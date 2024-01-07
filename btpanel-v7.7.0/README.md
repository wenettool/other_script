# btpanel-v7.7.0
btpanel-v7.7.0-backup  官方原版v7.7.0版本面板备份

**Centos/Ubuntu/Debian安装命令 独立运行环境（py3.7）：**

```Bash
curl -sSO https://raw.githubusercontent.com/wenettool/btpanel-v7.7.0/main/install/install_panel.sh && bash install_panel.sh
```

跳过登录框，以及破解插件等请自行搜索

&nbsp;

**如果遇到重启后宝塔乱码 请DD最新版Debian系统然后修改语言区域：**


```Bash
localectl set-locale LANG=en_US.UTF-8
nano /etc/default/locale
```

```Bash
LANG="en_US.UTF-8"
LC_ALL="en_US.UTF-8"
```

修改后保存文件，重启VPS即可。

# btpanel-v7.7.0
btpanel-v7.7.0-backup  官方原版v7.7.0版本面板备份

**Centos/Ubuntu/Debian安装命令 独立运行环境（py3.7）**

```Bash
curl -sSO https://raw.githubusercontent.com/8838/btpanel-v7.7.0/main/install/install_panel.sh && bash install_panel.sh
```

**备用安装链接，适用于不能访问GitHub的服务器。**

```
curl -sSO https://slink.ltd/https://raw.githubusercontent.com/wenettool/other_script/master/btpanel-v7.7.0/install/install_panel_proxy.sh && bash install_panel_proxy.sh
```

# 手动破解：

1，屏蔽手机号

```
sed -i "s|bind_user == 'True'|bind_user == 'XXXX'|" /www/server/panel/BTPanel/static/js/index.js
```

2，删除强制绑定手机js文件

```
rm -f /www/server/panel/data/bind.pl
```

3，手动解锁宝塔所有付费插件为永不过期

文件路径：`/www/server/panel/data/plugin.json`

搜索字符串：`"endtime": -1`全部替换为`"endtime": 999999999999`

4，给plugin.json文件上锁防止自动修复为免费版

```
chattr +i /www/server/panel/data/plugin.json
```

============================

！！如需取消屏蔽手机号

```
sed -i "s|if (bind_user == 'REMOVED') {|if (bind_user == 'True') {|g" /www/server/panel/BTPanel/static/js/index.js
```