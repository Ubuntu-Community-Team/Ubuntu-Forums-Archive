---
title: "ASUS Eee PC 1015 - Broadcom 4727 Wireless Problem"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by JLGreen on 2010-09-02
Hello,

I just got an ASUS Netbook and was thoroughly disappointed with the Windows 7 starter that came preloaded on it.  A long time ago I installed Ubuntu on a laptop of mine and I was quite impressed, so I found a download for Ubuntu Netbook Remix 10.04.  I installed it and everything seems to be working great except I am having a problem getting my wireless adapter to work.  When I type the command "lspci | grep Broadcom" I get the following output...

"02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)"

Any help would be greatly appreciated, having a netbook without wireless isn't fun.

Cheers

---

### Post by JLGreen on 2010-09-03
Update:

So I think I have make some progress...

I found a link to the driver that I think I need from the Broadcom website.  Using the command "lspci -n | grep 14e4" I determined that I have the Broadcom 4313 2.4Ghz card.  So following the instructions in the readme file I built the driver and got an out of a wl.ko file.  Before trying to install this module I verified that none of the other wireless modules were installed using "lsmod | grep "b43\|ssb\|wl" this command executed with no output.  The next part is where I ran into trouble, using the command "modprobe lib80211" I got the following output:

"WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."

Then after that I tried "insmod wl.ko" and I got the following output:

"insmod: error inserting 'wl.ko': -1 Unknown symbol in module"

Any light that can be shed on this issues would be greatly appreciated.  The procedure that I was following can be found here:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

---

### Post by bkratz on 2010-09-03
> **JLGreen said:**
> Update:

So I think I have make some progress...

I found a link to the driver that I think I need from the Broadcom website.  Using the command "lspci -n | grep 14e4" I determined that I have the Broadcom 4313 2.4Ghz card.  So following the instructions in the readme file I built the driver and got an out of a wl.ko file.  Before trying to install this module I verified that none of the other wireless modules were installed using "lsmod | grep "b43\|ssb\|wl" this command executed with no output.  The next part is where I ran into trouble, using the command "modprobe lib80211" I got the following output:

"WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."

Then after that I tried "insmod wl.ko" and I got the following output:

"insmod: error inserting 'wl.ko': -1 Unknown symbol in module"

Any light that can be shed on this issues would be greatly appreciated.  The procedure that I was following can be found here:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)




Look under "common issues" in the readme at this location.
It describes what you are seeing.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)


Just noticed your link!  Look under "common issues"!

---

### Post by JLGreen on 2010-09-03
I had read through the common issues section, the problem is whenever I try the modprobe command whether its "modprobe lib80211" or "modprobe ieee80211_crypt_tkip" I end up getting the same output...

"WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."

I don't know what it means but its preventing it from working.

---

### Post by bkratz on 2010-09-03
> **JLGreen said:**
> I had read through the common issues section, the problem is whenever I try the modprobe command whether its "modprobe lib80211" or "modprobe ieee80211_crypt_tkip" I end up getting the same output...

"WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."

I don't know what it means but its preventing it from working.

you should be able to ignore it, it is just a warning, but I thought the modprobe command needed a "sudo" in front of it. I will google for that and be back.

---

### Post by bkratz on 2010-09-03
Nothing definitive yet. But were you still in the hybrid_wl directory when you did the modprobes and insmod commands?  Looking at the first post of this thread it looks like that is where the user was when he/she did it.

[http://ubuntuforums.org/showthread.php?t=1363867](http://ubuntuforums.org/showthread.php?t=1363867)

Even if not the reason, at least it is interesting reading. Still looking

---

### Post by JLGreen on 2010-09-04
I couldn't remember what directory I was in so I tried to rerun the last half of the procedure.  The procedure in the Readme.txt for the driver said to run the modprobe and insmod command from the /lib/modules/...  But I tried to run them from both there and the /hybrid_wl directory.  I got the same result both times.  Is it possible i'm barking up the wrong tree?  The reason I picked this driver was because when I do the lspci command my pci code was 14e4:4727, which the readme said was the Broadcom 4313.  Since my wireless didn't work out of the box, I figured this was the driver I needed.

Let me know if you have any other ideas, this is frustrating.

---

### Post by bkratz on 2010-09-04
Still looking, sounds like you and this op are doing the same thing,

[http://ubuntuforums.org/showthread.php?t=1568028](http://ubuntuforums.org/showthread.php?t=1568028)

---

### Post by JLGreen on 2010-09-04
I'm not sure if this helps but I read a little on the dmesg command, so I ran the following to see what problems my system was having on boot up.

"dmesg | grep wl"

Here was the output...

[   12.666481] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.668754] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   12.668761] wl: Unknown symbol lib80211_get_crypto_ops
[ 6641.408741] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 6641.408754] wl: Unknown symbol lib80211_get_crypto_ops
[ 6796.499264] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 6796.499278] wl: Unknown symbol lib80211_get_crypto_ops

Let me know if this helps, I'll be googling "lib80211_get_crypto_ops" to see what it does.

---

### Post by bkratz on 2010-09-04
Before this last info. here is a similar one that seems to be solved.

[http://ubuntuforums.org/archive/index.php/t-1052779.html](http://ubuntuforums.org/archive/index.php/t-1052779.html)


See the January 30th, 2009, 09:02 PM  posting, I think we will have to remove wl and put it back in like the posting.

---

### Post by JLGreen on 2010-09-04
So since my system is having problems at boot up regarding the wireless configuration.  I did an "lsmod" and it turns out that no modules are being loading for my wireless nic.  Since I also can't seem to load any modules it seems like i'm quite stuck.

---

### Post by chili555 on 2010-09-04
Do you have the ability to hook up an ethernet cable and get an internet connection? If so , please do:```
sudo apt-get install bcmwl-kernel-source
```Reboot and your wireless will likely be working.

---

### Post by JLGreen on 2010-09-04
When this command executed its output is:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


After the reboot there is no change. The wireless still does not work.  The following is the output from "dmesg | grep wl"...

> 
[   10.903345] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.906368] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   10.906376] wl: Unknown symbol lib80211_get_crypto_ops


ifconfig still shows no wireless device...

> 
eth0      Link encap:Ethernet  HWaddr 20:cf:30:20:28:0b  
          inet6 addr: fe80::22cf:30ff:fe20:280b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20979784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:6262 (6.2 KB)  TX bytes:5551 (5.5 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


---

### Post by bkratz on 2010-09-04
Dr. Chili555 here is a very similar thread you solved back in May in case it helps. Looks really similar, knowing you, you probably already remembered it!

[http://newyork.ubuntuforums.org/showthread.php?t=1480671](http://newyork.ubuntuforums.org/showthread.php?t=1480671)

---

### Post by JLGreen on 2010-09-04
SUCCESS!!!!

I am writing this post right now using my wireless internet!

Thanks to chili555 for the past wisdom!
Thanks to bkratz for those forum searching skills!

Here was the fix!
[http://newyork.ubuntuforums.org/show....php?t=1480671](http://newyork.ubuntuforums.org/show....php?t=1480671)

---

### Post by bkratz on 2010-09-04
Well congratulations!! Glad you got it.

Ready to mark as [solved] in the thread tools???

---

### Post by chili555 on 2010-09-05
Good work! I'm glad it's working.

---

### Post by dave.biagioni on 2010-10-10
I'm writing to confirm that this fix worked for my Asus 1015-PEM running Ubuntu 10.04 LTS Desktop Edition.  Thanks for taking the time to research and write this up!  :guitar:

---

### Post by bdaman80 on 2010-10-15
I was Having the same problem with the same hardware in an Acer D260 netbook w/ 10.04.  Tried everything, even other distros - Fedora 11-13, Debian506, opensuse, to no avail.  Clean install of 10.10, Works Fine

---

### Post by jannoke on 2011-02-14
Running HP Touchsmart TM2 laptop. Used the backported 2.6.35 kernel to get the vga_switcheroo wokring (to turn off onboard ATI and save power).

After that the automatic wifi activation did not work anymore. 
Using this guide got it fixed again. I don't think i needed the blacklisting or startup moves (but i did it anyways) since after module compile and modprobe the wifi worked right away, before even restarting.

Running 10.04.1

---

