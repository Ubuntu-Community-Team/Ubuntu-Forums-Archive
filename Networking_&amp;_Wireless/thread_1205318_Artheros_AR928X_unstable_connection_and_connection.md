---
title: "Artheros AR928X unstable connection and connection drop"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by chenxiaolong on 2009-07-05
First of all, I'm running Ubuntu 9.04 Jaunty with kernel: 2.6.28-13-generic. I have an Artheros AR928X wireless card on a HP G60-247CL laptop. It frequently drops the connection no matter what access point I'm connected to (TP-Link Wireless N router, Netgear Wireless G router, and Linksys Wireless G router). I'm using Wicd right now because with Network-Manager, it always came up password dialog even if its right (with WPA and WPA2). After about 10 tries with NM, it would connect. Wicd connects on the first try. Both lose the connection and reconnect frequently. 

I'm not using a custom kernel; I'm just using the default kernel or updated one installed from updates. I'm still very new to linux, so if there are any commands I need to run in the terminal, it would be nice if you explained the commands, or typed the exact package name (like linux-backport-modules-jaunty rather than kernel backports). If there are any log files, config files, etc. that you need me to post, I would be happy to do so. I'll compile packages/kernel from source if I need to.

BTW1, I'm using the default ATH9X driver. If I need to use ndiswrapper or some other driver, could you provide clear instructions.

BTW2, Please don't post any comments telling me to look in the forum. I spent a lot of time looking through all the threads and posts on the driver and wireless card and even the Launchpad Bugzilla. Most of the things didn't work or I didn't understand them.

P.S. Sorry about my English and the long post.

---

### Post by Crafty Kisses on 2009-07-06
Hey there my friend! Your English is just fine. ;-) First I want to see some logs. So go into a Terminal and type the following:
```
tail -f /var/log/syslog
```
Post the results here on the forums. Now you mentioned you're using the default Atheros drivers, well that's fine for now but I want you to try a couple of different things before I hunt down a driver for you, and if it comes to that, don't worry I'll walk you through it step by step. So anyway, try connecting through the Terminal and see if you get any different results:
```
iwconfig wlan0 essid *youressid*
```
Now obviously where *youressid* is you would put your ESSID. I'd also like to see your routing table, you can view that by running the following:
```
route
```
Once I've seen those logs, I can help you further.

---

### Post by chenxiaolong on 2009-07-06
Thanks!!!

Here are the results of tail -f /var/log/syslog :

```
chenxiaolong@CXL-2CE90587MV:~$ tail -f /var/log/syslog
Jul  6 11:29:26 CXL-2CE90587MV ntfs-3g[11496]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8 
Jul  6 11:29:26 CXL-2CE90587MV ntfs-3g[11496]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096 
Jul  6 11:29:26 CXL-2CE90587MV hald: mounted /dev/sda2 on behalf of uid 1000
Jul  6 11:30:02 CXL-2CE90587MV /USR/SBIN/CRON[11547]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul  6 11:38:04 CXL-2CE90587MV kernel: [ 7501.928200] wlan0: beacon loss from AP f679c6b8 - sending probe request
Jul  6 11:40:01 CXL-2CE90587MV /USR/SBIN/CRON[12254]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul  6 11:42:44 CXL-2CE90587MV anacron[12596]: Anacron 2.3 started on 2009-07-06
Jul  6 11:42:44 CXL-2CE90587MV anacron[12596]: Normal exit (0 jobs run)
Jul  6 11:42:44 CXL-2CE90587MV anacron[12604]: Anacron 2.3 started on 2009-07-06
Jul  6 11:42:44 CXL-2CE90587MV anacron[12604]: Normal exit (0 jobs run)
Jul  6 11:44:11 CXL-2CE90587MV kernel: [ 7868.968329] wlan0: beacon loss from AP f679c6b8 - sending probe request
Jul  6 11:44:15 CXL-2CE90587MV kernel: [ 7872.972397] wlan0: beacon loss from AP f679c6b8 - sending probe request
Jul  6 11:44:38 CXL-2CE90587MV kernel: [ 7895.713753] wlan0: beacon loss from AP f679c6b8 - sending probe request
Jul  6 11:45:34 CXL-2CE90587MV kernel: [ 7951.240212] wlan0: authenticate with AP f679c6b8
Jul  6 11:45:34 CXL-2CE90587MV kernel: [ 7951.242905] wlan0: authenticated
Jul  6 11:45:34 CXL-2CE90587MV kernel: [ 7951.242918] wlan0: associate with AP f679c6b8
Jul  6 11:45:34 CXL-2CE90587MV kernel: [ 7951.247302] wlan0: RX ReassocResp from efad608a (capab=0x431 status=0 aid=1)
Jul  6 11:45:34 CXL-2CE90587MV kernel: [ 7951.247314] wlan0: associated
Jul  6 11:46:04 CXL-2CE90587MV kernel: [ 7981.661197] wlan0: beacon loss from AP f679c6b8 - sending probe request
Jul  6 11:46:12 CXL-2CE90587MV kernel: [ 7989.442970] wlan0: beacon loss from AP f679c6b8 - sending probe request

```

Here are the results of iwconfig wlan0 essid "LL-Wireless N" (My N router)

```

chenxiaolong@CXL-2CE90587MV:~$ iwconfig wlan0 essid "LL-Wireless N"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
chenxiaolong@CXL-2CE90587MV:~$ sudo iwconfig wlan0 essid "LL-Wireless N"
[sudo] password for chenxiaolong: 
chenxiaolong@CXL-2CE90587MV:~$ 

```

Here are the results of iwconfig wlan0 essid "LL-Wireless G" (My G router) after rebooting

```

chenxiaolong@CXL-2CE90587MV:~$ sudo iwconfig wlan0 essid "LL-Wireless G"
[sudo] password for chenxiaolong: 
chenxiaolong@CXL-2CE90587MV:~$ 

```

Here are the results of iwconfig wlan0 essid "linksys" (My other G router) after rebooting again

```

chenxiaolong@CXL-2CE90587MV:~$ sudo iwconfig wlan0 essid "linksys"
[sudo] password for chenxiaolong: 
chenxiaolong@CXL-2CE90587MV:~$ 

```

And here's my routing table :

```

chenxiaolong@CXL-2CE90587MV:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.1.2     0.0.0.0         UG    0      0        0 wlan0
chenxiaolong@CXL-2CE90587MV:~$ 

```

After the commands, I couldn't connect any wireless network any more. I tried rebooting, but Wicd says it can't find any wireless networks.

---

### Post by Crafty Kisses on 2009-07-06
Once you have attempted to connect to your wireless network by running:
```
sudo iwconfig wlan0 essid "linksys"
```
Try to ping Google and see if you get a response. You can ping Google by running:
```
ping google.com
```

---

### Post by chenxiaolong on 2009-07-07
After running those commands, this is what I get:

```
chenxiaolong@CXL-2CE90587MV:~$ sudo iwconfig wlan0 essid "linksys"
[sudo] password for chenxiaolong: 
chenxiaolong@CXL-2CE90587MV:~$ ping google.com
ping: unknown host google.com
chenxiaolong@CXL-2CE90587MV:~$ 

```

---

### Post by terencelhl on 2009-07-08
Hi there,

My laptop, Dell Inspiron 1545 using same version, kernel as mentioned (chenxiaolong) and worse scenario that I'm having after I upgraded from previous kernel is, I'm unable to connect to my own wifi router except others.

It also able to connect to anything other than the one at home. Having exact symptons as mentioned by chenxiaolong.

FYI, I'm plugging an Aztech USB Wifi and everything seems to be work.

Could this be the kernel upgrade that caused incompatibility between Atheros 928X and my Linksys WRT310N? Just my two cents.

Regards,

Terence Loo

---

### Post by chenxiaolong on 2009-07-08
I just tested the Sabayon 4.2 Gnome live cd today and the wireless card worked fine. I don't know if this is a kernel problem or an Ubuntu-specific problem.

---

### Post by chenxiaolong on 2009-07-09
I starting to think that the problem is a kernel problem. The wireless card connects to all three of my networks in Fedora 11 and Foresight 2.1.1. I get a 100% signal within ten feet from my house, about 55% signal in the basement, and 30% signal outside the house (Wireless N).

---

### Post by kungfoofool on 2009-07-28
I'm [having the same issues](http://ubuntuforums.org/showthread.php?p=7693435#post7693435) with it being unstable, but this is on an ASUS laptop.

---

### Post by networkproblems on 2009-08-03
I found a fix for my HP G60-247CL that has the same AR928X card. I'm running 64-bit, but I assume it works on 32-bit as well. Now my laptop connects in less than 10 seconds to WPA or no security, and it doesn't drop the connection anymore.

For Jaunty:
```
sudo aptitude install linux-backports-modules-jaunty-generic
```For Intrepid:
```
sudo aptitude install linux-backports-modules-intrepid-generic
```Taken from [http://ubuntuforums.org/showthread.php?t=1030629](http://ubuntuforums.org/showthread.php?t=1030629) post #10. I only modified HuaiDan's code for it to work with jaunty.

---

### Post by chenxiaolong on 2009-08-03
I tried installing the backport modules before and it didn't work. Oh well. I already returned the HP because it had major overheating problems. My new laptop has a Broadcom card, which works fine in Linux.

---

### Post by andrew frank on 2009-08-22
I have a Fujitsu Lifebook P1630 and had the same unstable wifi connection with the Artheros AR928x. installing the backports (on jaunty) worked immediately. 
Thank you all for the hint!
andrew

unfortunately the signal is still weak:
Link Quality=26/70  Signal level=-84 dBm  
          
anybody a suggestion, how this could be improved? (another immediately next to this one has quality 72/100 and -56 dBm)

---

### Post by excogitation on 2009-08-27
Feel free to join in: [333730]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/333730").

---

### Post by aatyler on 2009-09-05
I have an Asus M50VM-B1 and the aetheros wireless card. I installed the backports modules as listed in this thread, so far so good, on the first reboot the wlan still had to be activated from the terminal, but it connected much faster and recognized the avail. networks quicker.

---

### Post by evilfishy1 on 2009-09-08
Wow, Thanks!
Fixed it for me (x64).

---

### Post by DevinMcElheran on 2009-10-12
Okay, so I've been at this problem for about a month and a half, at least. Now, apparently sudo aptitude install linux-backports-modules-jaunty-generic will fix all my problems. But my only connection is wireless, and my laptop, runs 32 bit, where my desktop, with the AR928x, is 64 bit. Is there any way to download this package with everything I'd need in the dependency tree for 64 bit froom 32 bit?

---

### Post by chenxiaolong on 2009-10-12
All the packages from the Ubuntu repository can be downloaded here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Strubbl on 2009-10-30
where can I delete this post? I put it in the worng thread

---

### Post by bronxbomberz41 on 2009-11-18
I have been having this problem since the Karmic upgrade to 9.10.  I'm not sure how to fix it at this point since all these posts seem to be for Jaunty.  Should I just switch to wicd?  I used that for a little while but while the connection always seemed to hold ok the gui manager itself often didnt' seem very stable and would turn grey on me.

---

