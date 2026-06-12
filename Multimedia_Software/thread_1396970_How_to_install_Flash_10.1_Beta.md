---
title: "How to install Flash 10.1 Beta"
date: 2010-02-02
forum: Multimedia Software
---

### Post by spiritofelric on 2010-02-02
You can create an SH file and run "sh filename.sh" or just copy and paste the commands to your terminal.

```

#!/usr/bin/bash
echo We are going to start by remvoing the existing 'flashplugin-nonfree'
echo package if it is installed on your system. If you are asked, enter
echo your password.
sudo apt-get -mqy remove flashplugin-nonfree
echo Now we will setup Flash Player 10 beta...
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p2_linux_121709.tar.gz
tar xzvf flashplayer10_1_p2_linux_121709.tar.gz
mkdir -p ~/.mozilla/plugins
cp install_flash_player_10_linux/libflashplayer.so ~/.mozilla/plugins
cd ../../..
echo Cleaning up...
rm -rf flashplayer10_1_p2_linux_121709*
echo Flash Player 10 beta is now installed.
echo Restart your browser to begin using Flash Player 10 beta.

```

---

