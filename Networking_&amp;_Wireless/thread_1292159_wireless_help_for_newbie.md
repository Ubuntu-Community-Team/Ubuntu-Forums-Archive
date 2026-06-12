---
title: "wireless help for newbie"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by mcbean7 on 2009-10-15
Hello,
I am new to ubuntu. I just installed 9.04 and cannot connect to the internet. It says networking disabled. I tried to enable it but no connection. I have a dell latitude d600. Where do I start diagnosing this connection problem?
Thanks in advance.

---

### Post by t0mppa on 2009-10-15
Open up a terminal session (Application / Accessories / Terminal), run **lshw -C network** and post back with the results. That'll show what wireless chip your card has, what (if any) drivers it's using and if it's disabled or enabled.

---

### Post by mcbean7 on 2009-10-15
I hope I did this right. Does this help?
 
 
 
To run a command as administrator (user "root"), use "sudo <command>".


See "man sudo_root" for details.






ubuntu@ubuntu:~$ ifconfig


eth0 Link encap:Ethernet HWaddr 00:0d:56:dc:46:55 


UP BROADCAST MULTICAST MTU:1500 Metric:1


RX packets:0 errors:0 dropped:0 overruns:0 frame:0


TX packets:0 errors:0 dropped:0 overruns:0 carrier:0


collisions:0 txqueuelen:1000 


RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


Interrupt:11 






lo Link encap:Local Loopback 


inet addr:127.0.0.1 Mask:255.0.0.0


inet6 addr: ::1/128 Scope:Host


UP LOOPBACK RUNNING MTU:16436 Metric:1


RX packets:76 errors:0 dropped:0 overruns:0 frame:0


TX packets:76 errors:0 dropped:0 overruns:0 carrier:0


collisions:0 txqueuelen:0 


RX bytes:5940 (5.9 KB) TX bytes:5940 (5.9 KB)






ubuntu@ubuntu:~$ iwconfig


lo no wireless extensions.






eth0 no wireless extensions.






vboxnet0 no wireless extensions.






pan0 no wireless extensions.






wmaster0 no wireless extensions.






wlan0 IEEE 802.11bg ESSID:"" 


Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated 


Tx-Power=20 dBm 


Retry min limit:7 RTS thr:off Fragment thr=2352 B 


Power Management:off


Link Quality:0 Signal level:0 Noise level:0


Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0


Tx excessive retries:0 Invalid misc:0 Missed beacon:0






ubuntu@ubuntu:~$ lshw-c network


bash: lshw-c: command not found


ubuntu@ubuntu:~$ lshw -c network


WARNING: you should run this program as super-user.


*-network:0 


description: Ethernet interface


product: NetXtreme BCM5702X Gigabit Ethernet


vendor: Broadcom Corporation


physical id: 0


bus info: pci@0000:02:00.0


logical name: eth0


version: 02


serial: 00:0d:56:dc:46:55


width: 64 bits


clock: 66MHz


capabilities: bus_master cap_list ethernet physical


configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5702-v2.25 latency=64 mingnt=64 module=tg3 multicast=yes


*-network:1


description: Network controller


product: BCM4306 802.11b/g Wireless LAN Controller


vendor: Broadcom Corporation


physical id: 3


bus info: pci@0000:02:03.0


version: 02


width: 32 bits


clock: 33MHz


capabilities: bus_master cap_list


configuration: driver=b43-pci-bridge latency=32 module=ssb


*-network:0 DISABLED


description: Ethernet interface


physical id: 1


logical name: vboxnet0


serial: 0a:00:27:00:00:00


capabilities: ethernet physical


configuration: broadcast=yes multicast=yes


*-network:1 DISABLED


description: Ethernet interface


physical id: 2


logical name: pan0


serial: 32:e1:a0:28:e6:c7


capabilities: ethernet physical


configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


*-network:2 DISABLED


description: Wireless interface


physical id: 3


logical name: wlan0


serial: 00:90:4b:69:40:e1


capabilities: ethernet physical wireless


configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


ubuntu@ubuntu:~$

---

### Post by Niko Johnson on 2009-10-15
you have to run sudo before you type in the command, thats why you got the "not the super user" error. if you dont know your root  password you should change it beacuse you are going to have to log in as root more then once. just type in this command ```
 sudo passwd root 
``` then type in your password and then the new root password, then you log in as root just hit ```
 su root
or 
su - 
``` then you should see ubuntu@ubuntu:# instead of a $

---

### Post by mcbean7 on 2009-10-15
Let's try this again.
 
 
 
ubuntu@ubuntu:~$ su root


Password: 


root@ubuntu:/home/ubuntu# lshw -C network


*-network:0 


description: Ethernet interface


product: NetXtreme BCM5702X Gigabit Ethernet


vendor: Broadcom Corporation


physical id: 0


bus info: pci@0000:02:00.0


logical name: eth0


version: 02


serial: 00:0d:56:dc:46:55


capacity: 1GB/s


width: 64 bits


clock: 66MHz


capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation


configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5702-v2.25 latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair


*-network:1


description: Network controller


product: BCM4306 802.11b/g Wireless LAN Controller


vendor: Broadcom Corporation


physical id: 3


bus info: pci@0000:02:03.0


version: 02


width: 32 bits


clock: 33MHz


capabilities: pm bus_master cap_list


configuration: driver=b43-pci-bridge latency=32 module=ssb


*-network:0 DISABLED


description: Ethernet interface


physical id: 2


logical name: vboxnet0


serial: 0a:00:27:00:00:00


capabilities: ethernet physical


configuration: broadcast=yes multicast=yes


*-network:1 DISABLED


description: Ethernet interface


physical id: 3


logical name: pan0


serial: 32:e1:a0:28:e6:c7


capabilities: ethernet physical


configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


*-network:2 DISABLED


description: Wireless interface


physical id: 4


logical name: wlan0


serial: 00:90:4b:69:40:e1


capabilities: ethernet physical wireless


configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


root@ubuntu:/home/ubuntu#

---

### Post by t0mppa on 2009-10-15
> **Niko Johnson said:**
> you have to run sudo before you type in the command, thats why you got the "not the super user" error.

It was a warning, not an error. Running *lshw* with sudo only gives some info that is not relevant to cases such as these, so it's simpler to run it normally. And sudo was put in for a reason, you shouldn't run commands as root unless absolutely necessary and when you know what they're doing. You can't cause serious harm with the normal user privileges, but running a few shady commands as root could end up screwing up the whole system. And it's especially dangerous for new people who have no idea what the commands do.

> **mcbean7 said:**
> I hope I did this right. Does this help?

Yeah, you got it right. The BCM4306 is a bit older chip, but it is still supported by the b43-legacy driver. You have to install the firmware for it to work though. Do you have a working Internet connection (though wired) on your computer?

P.S. You can put pastes inside [ code] and [ /code] tags (without the space), so they're easier to read through.

---

### Post by mcbean7 on 2009-10-15
oops...sorry about that. Thanks.
The computer with Ubuntu does not have internet connection. Wired is not an option because of my location at work. Do I have any other options?

---

### Post by t0mppa on 2009-10-15
It just means you'll have to do the downloads on another computer and then copy the files over via some removable media, a USB stick for instance.

And on a second thought, there's one more piece of information that is required, as there are different revisions of the 4306 chip and the files you need depend on which one you have, so can you post the output of **lspci -vnn | grep BCM4306** as well?

---

### Post by mcbean7 on 2009-10-15
root@ubuntu:/home/ubuntu# lspci -vnn | grep BCM4306


02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)


[EMAIL="root@ubuntu:/home/ubuntu"]root@ubuntu:/home/ubuntu[/EMAIL]# 
 
 
I do have a USB thumb drive. Where do i go to download the files needed? Thx.

---

### Post by t0mppa on 2009-10-15
You can get the b43-fwcutter that will extract the firmware from [here]("http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2"). And then you can grab the firmware from [here]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o").

Copy them both to your Ubuntu box, open up a terminal, navigate to the directory where you copied the two files into and run the following commands:

```
tar xjf b43-fwcutter-012.tar.bz2
cd b43-fwcutter-012
make
cd ..
sudo ./b43-fwcutter-012/b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
```

P.S. You can use tab in the middle of typing those long file and directory names and if there's only possibility left, it will be automatically filled in for you, so you don't have to worry about typos.

---

### Post by mcbean7 on 2009-10-15
I copied the files to my USB thumb drive and have transferred it to the desktop of Ubuntu. Now, I don't know how to navigate to this file location.

---

### Post by t0mppa on 2009-10-15
Ok. The desktop folder is actually a subdirectory inside your home directory.

Terminal shows a prompt of **<user_name>@<host_name>:<path>$** and opens by default at ~, which refers to your home directory, so you can get to the desktop by typing **cd Desktop**, then with **ls -la** you can see a list of files inside the directory to make sure it's the right one.

Looking at the above posts, apparently your username is *ubuntu*, so your home directory will be located at */home/ubuntu* and thus the Desktop for same user at */home/ubuntu/Desktop*. You can also get there from any path on the file system by running **cd /home/ubuntu/Desktop**

---

### Post by mcbean7 on 2009-10-15
OK. I followed these directions along with post #10 directions and see a list of files extracting...
Am I done or do i need to install any files?

---

### Post by t0mppa on 2009-10-15
Assuming the make or the last command invoking the firmware didn't end with any errors, you should be good to go. Try running **sudo iwlist scanning** to see if your card can detect any networks now.

---

### Post by tranduyninh on 2009-10-15
hm. i'm trying all of way, but my wireless card ( broadcom ) also get problem ?

---

### Post by t0mppa on 2009-10-15
> **tranduyninh said:**
> hm. i'm trying all of way, but my wireless card ( broadcom ) also get problem ?

Unless you have exactly the same chip, I suggest you create your own thread. You'll get better feedback that way and it will be a lot less confusing with only one problem per thread.

---

### Post by mcbean7 on 2009-10-15
hmmm...running the sudo iwlist scanning gives me a Interface doesn't support scanning for lo, eth0, vboxnet0, pan0, wmaster0, wlan0.

---

### Post by t0mppa on 2009-10-15
*sigh* That's not good news then. What also bugs me is the fact that there's the other wireless interface showing up on *lshw* and that it's disabled. You only have one wireless card, right?

One thing you could check is **dmesg | grep -e b43 -e wlan0** to see if it gives any hints towards what's wrong. If b43 refuses to work, then there's always NDISwrapper and using Windows driver through it. However, when I tried it with my similar card, it would only work with open networks or WEP encryption, but not WPA. So, I don't have much experience about playing around with it.

---

### Post by mcbean7 on 2009-10-15
Yes I only have one wireless card. I'll run dmesg as recommended and will post what I find. Thank you for your help. Damn this is frustrating. I thought it would be much easier than this!!

---

### Post by mcbean7 on 2009-10-15
I hope this can answer some questions as to why this wireless is not working. Thanks
 
 
ubuntu@ubuntu:~$ dmesg | grep -e b43 -e wlan0


[ 3.772464] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5


[ 166.866007] b43legacy-phy0: Broadcom 4306 WLAN found


[ 166.888045] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1


[ 166.888068] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2


[ 166.912037] b43legacy-phy0 debug: Radio initialized


[ 197.514623] input: b43legacy-phy0 as /devices/virtual/input/input9


[ 197.784045] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw


[ 199.545011] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.


[ 199.545021] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).


[ 199.583506] input: b43legacy-phy0 as /devices/virtual/input/input10


[ 199.952040] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw


[ 199.954650] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.


[ 199.954659] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).


[ 1371.791205] b43legacy-phy1: Broadcom 4306 WLAN found


[ 1371.816047] b43legacy-phy1 debug: Found PHY: Analog 1, Type 2, Revision 1


[ 1371.816070] b43legacy-phy1 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2


[ 1371.840232] b43legacy-phy1 debug: Radio initialized


[ 1376.687988] input: b43legacy-phy1 as /devices/virtual/input/input11


[ 1376.964254] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw


[ 1376.969865] b43legacy-phy1 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.


[ 1376.969880] b43legacy-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).


[ 1377.017893] input: b43legacy-phy1 as /devices/virtual/input/input12


[ 1377.332220] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw


[ 1377.335911] b43legacy-phy1 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.


[ 1377.335919] b43legacy-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).


[ 1424.410178] b43legacy-phy2: Broadcom 4306 WLAN found


[ 1424.436334] b43legacy-phy2 debug: Found PHY: Analog 1, Type 2, Revision 1


[ 1424.436358] b43legacy-phy2 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2


[ 1424.460055] b43legacy-phy2 debug: Radio initialized


[ 1428.691080] input: b43legacy-phy2 as /devices/virtual/input/input13


[ 1428.968246] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw


[ 1428.973860] b43legacy-phy2 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.


[ 1428.973874] b43legacy-phy2 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).


[ 1429.022038] input: b43legacy-phy2 as /devices/virtual/input/input14


[ 1429.356241] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw


[ 1429.360779] b43legacy-phy2 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.


[ 1429.360794] b43legacy-phy2 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).


[ 1430.973963] b43legacy-phy3: Broadcom 4306 WLAN found


[ 1430.996060] b43legacy-phy3 debug: Found PHY: Analog 1, Type 2, Revision 1


[ 1430.996084] b43legacy-phy3 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2


[ 1431.020056] b43legacy-phy3 debug: Radio initialized


[ 1435.703150] input: b43legacy-phy3 as /devices/virtual/input/input15


[ 1435.984036] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw


[ 1435.987763] b43legacy-phy3 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.


[ 1435.987771] b43legacy-phy3 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).


[ 1436.019876] input: b43legacy-phy3 as /devices/virtual/input/input16


[ 1436.324275] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw


[ 1436.329900] b43legacy-phy3 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.


[ 1436.329915] b43legacy-phy3 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).


ubuntu@ubuntu:~$

---

### Post by t0mppa on 2009-10-15
Ok, the firmware obviously isn't working. The version it is requesting is exactly the one you downloaded though. So, perhaps the install didn't really work all the way through.

Try running **locate ucode** (or **locate ucode4.fw** if the former gives too many hits) to see if you can pick up something similar to the file it is failing to find or load.

[QUOTE=mcbean7]Damn this is frustrating. I thought it would be much easier than this!! [/QUOTE]

This is a bit doing it the hard way around. Ubuntu has some built-in features to make these things easier, but the fact that you can't use a wired connection complicates things, since they all rely on downloading the things automatically.

Anyway, I need to catch some sleep now, will check back tomorrow in case you're still stuck and haven't got anyone else to help you out.

---

### Post by mcbean7 on 2009-10-15
Thank you so much for your help so far. I'm going to play with it some more tonight to see if I can get it working. Will keep you posted.

---

### Post by zacharyr on 2010-05-16
I am in exactly the same spot with exactly the same computer (d600) and exactly the same network devices.

the only difference is that i'm on 10.4. in addition to wireless, i also can't get ethernet to work.

i just ran 'locate ucode' and got the following:

/lib/firmware/iwlwifi-1000-3.ucode
/lib/firmware/iwlwifi-3945-2.ucode
/lib/firmware/iwlwifi-4965-2.ucode
/lib/firmware/iwlwifi-5000-1.ucode
/lib/firmware/iwlwifi-5000-2.ucode
/lib/firmware/iwlwifi-5150-2.ucode
/lib/firmware/iwlwifi-6000-4.ucode
/lib/firmware/2.6.32-21-generic/e100/d101m_ucode.bin
/lib/firmware/2.6.32-21-generic/e100/d101s_ucode.bin
/lib/firmware/2.6.32-21-generic/e100/d101e_ucode.bin
/lib/firmware/e100/d101m_ucode.bin
/lib/firmware/e100/d101s_ucode.bin
/lib/firmware/e100/d102e_ucode.bin
/lib/firmware/slicoss/gbrcvucode.sys
/lib/firmware/slicoss/oasisrcvucode.sys

any ideas? thanks.

---

