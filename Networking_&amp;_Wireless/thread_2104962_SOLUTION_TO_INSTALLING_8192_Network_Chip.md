---
title: "SOLUTION TO INSTALLING 8192 Network Chip"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by Andrew F in Australia on 2013-01-14
HI All

A simple guide to installing the Ralink  8192 chipset drivers used in the ASUSN13 usb network adapter.

I'd made a simple mistake then overlooked the error message about 4 days ago - have been fighting with the computer ever since.

Many sincere thanks to Steeldriver and Ahallubuntu.  This is their knowledge, I'm merely standing on the shoulders of giants here.

------------
(1) Download Current Driver from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

(if above link broken, look to [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/) for the rtl8192cu chipset drivers)

(2) Extract the driver to a directory in your home directory [BR}**ABSOLUTELY CRITICAL: The directory MUST have no spaces in its name**
(to do this, use either the graphical archive manager or a terminal with the command unzip (filename)

(3) Follow ahallubuntu's instructions here:
[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

the chmod 755 command is key as it enables all users to use the module also.```
 **Re: ubuntu 12.04 rtl8192cu connects with bad ip**             

Download the latest driver from Realtek from here:
[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Open a terminal, then assuming you downloaded it to the Downloads directory in your home directory:[code]:
cd ~/Downloads 
unzip (ZIPFILENAME) 
cd (NEWDIRECTORY_CREATED) 
chmod 755 ./install.sh
sudo ./install.sh 

```You may need to blacklist your existing driver by adding these three  items to the end of the file /etc/modprobe.d/blacklist.conf 
```

blacklist rtl8192cu 
blacklist rtl8192c_common 
blacklist rtlwifi 

```and add the name of the new module "8192cu" to the end of the file /etc/modules so it will be automatically loaded at each boot.

You may need to re-build this each time your kernel is updated by Ubuntu.

*ast edited by ahallubuntu; October 27th, 2012 at 01:18 PM..                                                           *             
[/code]To blacklist the modules, type the following into a terminal window:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```To append 8192 to the end of the /etc/modules file, use

```
gksudo gedit /etc/modules
```Cheers,

AF
(original hassles documented [here]("http://ubuntuforums.org/showthread.php?t=2102362"):)

---

### Post by ahallubuntu on 2013-01-14
You're welcome!

---

### Post by ahallubuntu on 2013-01-14
It's a shame we can't convince Realtek to release Debian/Ubuntu packages instead of source code you have to build in a terminal!  I wonder how many countless hours of time users have wasted on this over the last year or two...

---

### Post by kurt18947 on 2013-01-14
> **ahallubuntu said:**
> It's a shame we can't convince Realtek to release Debian/Ubuntu packages instead of source code you have to build in a terminal!  I wonder how many countless hours of time users have wasted on this over the last year or two...

True, but RealTek is still better than most.  At least the script is pretty simple to run and has been reliable for me.  I think I understand the reason for sticking with bash scripts;  they work in most if not all distros with little or no tweaking.

---

### Post by ahallubuntu on 2013-01-14
Yes, the Realtek drivers have been easy for me to build, too.  But I have been writing scripts for years.  I can type terminal commands in my sleep.  It's quite intimidating for users who aren't used to typing commands, and it helps re-enforce the idea that Linux is only for hackers and requires typing a lot of commands.

It amazes me that Canonical has such awful support for wireless cards even in recent versions of Ubuntu.  Yes, they aren't responsible for kernel modules, but they could at least provide an easy-to-use tool to help figure out how to get your wireless card working if it's not supported automatically.  Laptops must be near the bottom on their priority list.

---

### Post by chili555 on 2013-01-14
I hear good things about linux-backports-modules-cw which needn't be compiled from source and automagically gets updated without recompiling. Anybody tried it?

---

