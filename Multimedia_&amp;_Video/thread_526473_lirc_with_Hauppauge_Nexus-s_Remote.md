---
title: "lirc with Hauppauge Nexus-s Remote"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by jenetik on 2007-08-15
Does anyone have a HOWTO/Guide for configuring lirc with a Hauppauge Nexus-s remote control?  I have tried a few ubuntu forums and can't seem to get communication established between the devices.  I have tried using 'evtest' and '/usr/sbin/lircd -H dev/input -d /dev/input/eventx -n' and neither respond to the buttons being pressed on the remote.  I am trying to follow these guides:

[http://www.hauppauge.co.uk/board/archive/index.php?t-8336.html]("http://www.hauppauge.co.uk/board/archive/index.php?t-8336.html")
[https://help.ubuntu.com/community/Install_Lirc_Feisty]("https://help.ubuntu.com/community/Install_Lirc_Feisty")

I have built the i2c driver module and am not sure if it's working; do I need to configure any other modules for the Nexus besides lirc_i2c?  I believe these are loaded OK because they show up in the logs below as registered.  Any help would be appreciated, thanks.  

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="DVB on-card IR receiver"
P: Phys=
S: Sysfs=/class/input/input182
H: Handlers=kbd event4
B: EV=100003
B: KEY=fc812 a052041 0 0 0 0 0 4000 40002800 1e1680 0 0 ffc

[ 1908.202032] DVB: registering new adapter (Technotrend/Hauppauge WinTV Nexus-S rev2.3)
[ 2055.965138] input: DVB on-card IR receiver as /class/input/input182

---

