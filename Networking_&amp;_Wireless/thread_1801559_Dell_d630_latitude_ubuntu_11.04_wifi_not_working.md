---
title: "Dell d630 latitude ubuntu 11.04 wifi not working"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by mkyweriga on 2011-07-10
[SIZE=3]Hello,
Newbie here. I just did a fresh wipe and install of Ubuntu 11.04 on my Dell D630 Latitude. I installed connected to the internet and ubuntu recognized I was missing firmware and I installed and rebooted. Now the "firmware missing" notice is gone but I don't know how to connect to my wifi. I can access internet with the ethernet cable.

This is the lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I feel like I just need to add the wifi network, but I don't know what info to put into the fields. Any help would be great.
Thanks :)
[/SIZE]

---

### Post by josephmills on 2011-07-10
could we see a ```
lspci -nn | grep 14e4 
``` thanks

---

### Post by josephmills on 2011-07-10
is it the firmware for the b43 or the wl ? could we also see a ```
rfkill list all 
``` and a ```
dmesg | grep b43 
 
``` thanks

---

### Post by mkyweriga on 2011-07-11
[SIZE=2]Hey everyone, I just saw a few responses to my first post. I thought I would be notified, but I guess I need to turn it on. I spent all day working on this problem and I just got my wifi to work. I heavily documented my progress and I post my solution here.
Most of the solving came from this post:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
It was super helpful.
Here are my notes of the steps I went through and how I got it to work :)
I also need to mark my original post as solved... I'll have to figure it out.

[/SIZE][COLOR=#000000][FONT=Ubuntu]Problem: Setting up wifi on this computer[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Status: Solved, 11Jul2011, 0002 Hrs :)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]This is a Dell Latitude D630 computer running Ubuntu 11.04 (Natty Narwhal )[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]10 July 2011[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Since I have tried a number of things I apparently need to wipe the cpu and retry the wifi stuff.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]I  will need to document what I do and what works, because I may need to  wipe this cpu for another reason and have to repeat this step. This is  why this documentation must remain online (google docs).[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So  now I will wipe and reinstall ubuntu. This time I selected the option  to automatically sign in without a password (I only use it at home and  my roommates are free to use it :)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Now  that I’ve re-installed ubuntu, it automatically knew I was missing the  wifi firmware, so I clicked the button to install it (very top of the  screen) and rebooted.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I am now hitting the basics here:[/FONT][/COLOR]
[[COLOR=#000099][FONT=Arial]_https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper_[/FONT][/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I will do this first (step 2.1.2):[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]calvcalvinst@calvinst-Latitude-D630:~$ sudo apt-get install ndisgtk[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Didn’t work because my account wasn’t an administrative one. I changed this and rebooted the machine.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Now it worked :)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]restarted machine[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]In step 3.1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I clicked on this link: [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_WifiDocs/Driver/bcm43xx_[/FONT][/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")[COLOR=#000000][FONT=Arial].[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I checked out the PCI slot info:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]calvinst@calvinst-Latitude-D630:~$ lspci[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Excerpt:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]calvinst@calvinst-Latitude-D630:~$ lspci -n: 0c:00.0 0280: 14e4:4311 (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thus, [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Card/model: BCM4311 [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]PCI ID: 14e4:4311[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The driver I need is STA or b43[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I just installed b43-fwcutter using synaptic.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Now I just installed [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**firmware-b43-installer **[/FONT][/COLOR][COLOR=#000000][FONT=Arial]which I maybe should have done instead of the previous step.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Now restart.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Since it still doesn’t work (all of the help in [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_WifiDocs/Driver/bcm43xx_[/FONT][/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")[COLOR=#000000][FONT=Arial].)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I will blacklist it (Back to Step 3.1)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]calvinst@calvinst-Latitude-D630:~$  echo -e "blacklist bcm43xx\nblacklist b43\nblacklist  b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Restart.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I already did step 3.2.1 in the [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_WifiDocs/Driver/bcm43xx_[/FONT][/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")[COLOR=#000000][FONT=Arial]. help file which is all above.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]In step 3.3.1 I downloaded: sp32156.exe from [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4311_[/FONT][/COLOR]]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4311")[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]And now I installed [/FONT][/COLOR][COLOR=#000000][FONT=Arial]*cabextract *[/FONT][/COLOR][COLOR=#000000][FONT=Arial]and [/FONT][/COLOR][COLOR=#000000][FONT=Arial]*unshield *[/FONT][/COLOR][COLOR=#000000][FONT=Arial]from synaptic.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Now I need to be in the correct directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]calvinst@calvinst-Latitude-D630:~$ cd Downloads[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and tried to unzip the file, that failed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I just did step 3.3.2: cabextract sp32156.exe, and that worked![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]calvinst@calvinst-Latitude-D630:~/Downloads$ cabextract sp32156.exe[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extracting cabinet: sp32156.exe[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting bcm1xsup.dll[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting bcm43xx.cat[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting bcmwl5.inf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting bcmwl5.sys[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting bcmwliss.dll[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting bcmwlnpf.sys[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting bcmwlpkt.dll[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting bcmwls.ini[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting bcmwls32.exe[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting bcmwlu00.exe[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting data1.cab[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting data1.hdr[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting data2.cab[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting ikernel.ex_[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting is.exe[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting launcher.ini[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting layout.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting setup.exe[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting Setup.ini[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting setup.inx[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting setup.iss[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  extracting sp32156.cva[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]All done, no errors.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I need to find the INF and SYS files, which are:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]bcmwl5.inf, bcmwl5.sys, bcmwlnpf.sys[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I made a driver directory in my home folder.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Home folder > drivers[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and copied and pasted everything there from the downloads folder.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I now went into Applications > System Settings > Windows Wireless Drivers[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I clicked “+ Install New Driver” and selected bcmwl5.inf [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I then did step 3.4.2:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]calvinst@calvinst-Latitude-D630:~/Downloads$ sudo ndiswrapper -i ~/drivers/bcmwl5.inf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]driver bcmwl5 is already installed[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Which was great [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I followed with step 3.4.2.1:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]calvinst@calvinst-Latitude-D630:~/Downloads$ ndiswrapper -l[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]bcmwl5 : driver installed[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    device (14E4:4311) present (alternate driver: ssb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Then  Ubuntu disconnected my ethernet cable and a little window popped up  asking me which wireless network I wanted to join. I unplugged the cable  and I was online. 
I HAVE WIFI [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]WOOT WOOT!!!![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OK, now to ensure this remains permanent.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Step 3.5:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo depmod -a
  sudo modprobe ndiswrapper[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]tail /var/log/messages[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I’m still getting that warning, but I think I can ignore it for now.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I ended with step 3.7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo ndiswrapper -m[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]But, the responses were that it was already OK. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I  rebooted and connected my wifi no problem. Man, what a day. I never  gave up. It was pretty tough, but I am a happy man on Ubuntu.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Now to get those Java plugins to work :)[/FONT][/COLOR]

---

### Post by linsteina on 2011-08-15
Thanks. All works now. Chun

---

### Post by aleska on 2011-09-11
For me, it was this and only this that solved the problem.  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Upon reboot, the network connection icon when clicked said something like, wireless disabled my manual hardware switch - or something like that.  

Excited I tried Fn + F2 and presto bammo wizzo wireless is working.
Rock on!
:D

---

