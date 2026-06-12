---
title: "HOW TO: Antec Veris Basic IR Receiver, Ubuntu 9.10 Karmic, Harmony or MCE Remote XBMC"
date: 2010-01-27
forum: Multimedia Software
---

### Post by stpfarms on 2010-01-27
I created the following tutorial for users of Ubuntu/Mythbuntu 9.10 Karmic. None of the tutorials/posts I found worked properly all the way through so I created a step by step guide:

Prerequisites:
Antec Veris Basic installed
Ubuntu 9.10 Karmic
XBMC 9.11
MCE Remote or any Harmony Remote programmed as a MCE Remote

1. The first thing to do is ensure the Antec Veris Basic is recognized by the OS. Type in "lsusb" at the terminal. Take note of the characters following ID for SoundGraph Inc., in this case 15c2:0043:[INDENT]**lsusb**
[/INDENT]Output:[INDENT] [B]Bus 003 Device 003: ID 15c2:0043 SoundGraph Inc.
Bus 003 Device 002: ID 045e:0719 Microsoft Corp.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/B]
[/INDENT]2. We now want to add a UDEV rule to prevent the USBHID driver from loading and taking over the Antec Veris device. We accomplish this by creating a rule in /etc/udev/rules.d/. You can download my rule here:<b>[INDENT]**sudo wget -q [http://www.stpit.com/public/99-lirc.rules](http://www.stpit.com/public/99-lirc.rules) -O /etc/udev/rules.d/99-lirc.rules**[/INDENT]In order to edit the file to ensure the proper Product ID type the following:[INDENT]**sudo nano /etc/udev/rules.d/99-lirc.rules**[/INDENT]Check the following:[INDENT]    [B]#Prevent the USBHID driver from loading for the Antec Veris
SYSFS{idVendor}=="15c2", SYSFS{idProduct}=="0043", MODE="0666", PROGRAM="/bin/sh -c 'echo -n $id:1.0 >/sys/bus/usb/drivers/usbhid/unbind;\
    echo -n $id:1.1 >/sys/bus/usb/drivers/usbhid/unbind'"[/B][/INDENT]*note - the idVendor and idProduct is pulled from Step One. In my case the idProduct was 0043 but yours may be different depending on the revision of the Antec Veris you purchased.

3. Reboot your machine:[INDENT] **sudo reboot**
[/INDENT]4. *Optional - We can now check to see if the Antec Veris is loaded without a driver associated with it. This step is optional.[INDENT] [B]sudo mount -t usbfs none /proc/bus/usb
sudo cat /proc/bus/usb/devices[/B]
[/INDENT]Output:[INDENT] [B]T:  Bus=03 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0043 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms[/B]
[/INDENT]5 Now it is time to install LIRC. Since you are using Ubuntu 9.10 Karmic, the software repository includes the latest 0.8.6 version of LIRC.[INDENT] **sudo apt-get install lirc**
[/INDENT]6. You will be presented with a choice for remote control, simply choose "**Soundgraph iMON Antec Veris**" and for IR Transmitter choose "**None**". This will set up your /etc/lirc/hardware.conf file to load the lirc_imon driver for the Antec Virus.

7. *Optional - We can now check to see if the Antec Veris is loaded with the lirc_imon driver. This step is optional.[INDENT] [B]sudo mount -t usbfs none /proc/bus/usb
sudo cat /proc/bus/usb/devices[/B]
[/INDENT]Output:[INDENT][B]T:  Bus=03 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0043 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=(lirc_imon)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(lirc_imon)
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
[/B][/INDENT]8. We will now tell the lirc_imon driver to use the MCE codes instead of the RMA100 codes. You can download my conf file by using the following:<b>[INDENT]**sudo wget -q [http://www.stpit.com/public/lirc_imon.conf](http://www.stpit.com/public/lirc_imon.conf) -O /etc/modprobe.d/lirc_imon.conf**[/INDENT]You can view the lirc_imon.conf file:[INDENT]**cat /etc/modprobe.d/lirc_imon.conf**[/INDENT]Output:[INDENT]**options lirc_imon ir_protocol=1**
[/INDENT]9. We now want to change the driver to load the MCE compatible configuration. We will do this by changing a line in /etc/lirc/hardware.conf and /etc/lirc/lircd.conf. You will want to change "lircd.conf.imon-antec-veris" with "lircd.conf.imon-mceusb" You can do this by typing in the following in terminal:[INDENT] **sudo nano /etc/lirc/hardware.conf**
[/INDENT]Change: **  REMOTE_LIRCD_CONF="imon/lircd.conf.imon-antec-veris" **     to       **REMOTE_LIRCD_CONF="imon/lircd.conf.imon-mceusb"**[INDENT] **sudo nano /etc/lirc/lircd.conf**
[/INDENT]Change:**  include "/usr/share/lirc/remotes/imon/lircd.conf.imon-antec-veris"      **to[B]       include "/usr/share/lirc/remotes/imon/lircd.conf.imon-mceusb"
[/B] 
*note: we could also simply overwrite the lircd.conf.imon-antec-veris with lircd.conf.imon-mceusb but you may want to use the imon-antec-veris settings at a later time.

10. We now want to restart LIRC:[INDENT] **sudo /etc/init.d/lirc restart**
[/INDENT]11. Now we can test the MCE remote control to ensure the system is recognizing your remote control commands. We will load IRW and press buttons on our MCE remote. The terminal should output the buttons that you press.[INDENT] **sudo irw**
[/INDENT]Output:[INDENT] [B]0200005100000000 00 KEY_DOWN MCE_via_iMON
0200005100000000 01 KEY_DOWN MCE_via_iMON
0200004f00000000 00 KEY_RIGHT MCE_via_iMON
0200004f00000000 01 KEY_RIGHT MCE_via_iMON
0200005000000000 00 KEY_LEFT MCE_via_iMON
0200005000000000 01 KEY_LEFT MCE_via_iMON
0200002800000000 00 #KEY_OK MCE_via_iMON
0200002800000000 01 #KEY_OK MCE_via_iMON[/B]
[/INDENT]12. Now that the MCE remote is working properly we need to have XBMC pick up these commands. We accomplish by creating a Lircmap.xml file in ~/xbmc/userdata. I have created a Lircmap.xml file that you can use. Type the following at the terminal:[INDENT] [B]sudo wget -q [http://www.stpit.com/public/Lircmap.xml](http://www.stpit.com/public/Lircmap.xml) -O ~/.xbmc/userdata/Lircmap.xml
[/B][/INDENT]13. Start XBMC and you should be able to remote control XBMC with your Harmony or MCE remote. Currently for some reason on my system I have to issue a **sudo /etc/init.d/lirc restart** on a fresh boot before XBMC starts or the remote will not work. I am trying to track this issue down under this link here: [http://ubuntuforums.org/showthread.php?t=1387992](http://ubuntuforums.org/showthread.php?t=1387992)

---

### Post by highflyr on 2011-03-13
Thanks for posting stp! Have you tried/gotten this to work on 10.10 maverick? Looks like it works for 10.04 lucid [http://blog.unixguru.se/?p=7](http://blog.unixguru.se/?p=7) "-Microsoft Remote-
This is how I made my MCE work with Ubuntu 10.04.1 and XBMC (doesn&#8217;t work with 10.10)"

---

