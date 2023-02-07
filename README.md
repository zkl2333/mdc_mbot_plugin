# mdc_mbot_plugin
Yet another MovieBot plugin..

## Usage
### 基本使用
1. 在 [Release](https://github.com/mdc-ng/mdc_mbot_plugin/releases) 页面下载最新版本插件压缩包 mdc_mbot_plugin-${version}.zip
2. 解压缩并将插件文件夹重命名为 mdc_mbot_plugin，丢到容器的 plugins 目录
3. 重启容器
4. 初次加载插件会尝试自动下载核心库 libmdc_ng.so。如果容器不是全局代理，这一步失败报错是正常的，继续：
5. 进入 moviebot 的插件管理 - 我的插件页面，对 MDC 插件进行配置：
![image](https://user-images.githubusercontent.com/124132602/217214050-941124b0-99f2-41da-8f06-e147f79f7974.png)

    注意：如果配置了监控目录，需要在MR的应用设置 - 下载设置 - 媒体文件夹中添加该目录，只要保持“下载保存路径”一项与MDC监控目录中的配置一致即可，其余随意填写无影响

    ![image](https://user-images.githubusercontent.com/124132602/217214907-69b8a329-b4b9-4af2-b301-b113d5f77779.png)

6. 代理配好后，在插件管理 - 快捷功能中执行“更新MDC”，等待执行成功后重启容器
7. MR启动日志中若出现 “MDC基础库加载成功, 当前版本: xxx”：恭喜你，插件配置完成！
8. MDC的主要功能由核心库提供: https://github.com/mdc-ng/mdc-ng/releases
   
   请关注核心库的版本发布。可执行6~7步骤单独更新内核，以获得MDC的最新特性

### 作为基础库
```python
# 其他插件中对 MDC 的调用方式示例
def mdc_command(video, config_path):
    from ..mdc_mbot_plugin import mdc_main
    
    # video:        必填，视频的绝对路径，如 /nas/media/xxx.mp4
    # config_path:  可选，自定义配置文件的绝对路径。不传递则会使用默认config.ini
    mdc_main(video, config_path)
```
