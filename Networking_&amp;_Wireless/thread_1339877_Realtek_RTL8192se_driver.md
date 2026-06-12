---
title: "Realtek RTL8192se driver"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by pcrofts on 2009-11-28
I have a new toshiba p505 laptop. I've installed the 64bit version of Ubuntu 9.10 on it but I just can't get the Realtek RTL8192se wireless card to work. I gave up on the Ndiswrapper and got the linux driver from Realtek. I've attached the driver here as a zip file. I removed the supplied wpa_supplicant archive included with the driver as one already is installed on my ubuntu and I needed to reduce the file size to post.

I have tried following the info in the readme but I can't get it to work with my wpa protected network. If anybody else is trying to get this adapter to work and can try this driver I'd be so grateful if you can tell me if you get it to work.

---

### Post by tubby12 on 2009-11-29
save the driver to Desktop
Open the terminal
cd Desktop
unzip \*.zip
cd rtl8192se_linux_2.6.0010.1116.2009
make
sudo su
enter password
make
make install
exit

---

### Post by pcrofts on 2009-12-01
Thanks for the post.

I see you are suggesting calling make twice once as my user and once as root. I didn't do that I called make as root and then again as root for make install. Do you think that would make the difference.

I tried it again with no security settings on my wireless router to see if I could get a connection without them. I couldn't. What I find interesting is that if I use ifconfig I see the physical/mac address as different to the actual mac of the card. That can't be good.

I'm busy refreshing the install of ubuntu and will try the way you suggested when it is done.

---

### Post by chellrose on 2009-12-01
I'm having problems setting up Realtek wireless too.  I have a new laptop which came preloaded with Windows 7.  I shrunk the Windows partition and installed Kubuntu 9.10 using the live CD, so that my system is now dual boot.

I'm a total newbie at this and have no idea how to set up net connections.  I tried using the attached driver and following the steps suggested by tubby12, but got an error message when I typed make:

```
make: *** /lib/modules/2.6.31-14-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
```What should I do?  I can't get it to recognize a wired connection either, so I have no way of downloading any needed packages.

Thanks.

In case it helps, here is some more information:

Output of lspci:

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

```Output of ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:26:9e:87:35:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 

eth0:avahi Link encap:Ethernet  HWaddr 00:26:9e:87:35:23  
          inet addr:169.254.5.123  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```Output of iwconfig:

```

lo         no wireless extensions.

eth0    no wireless extensions.

```

I should add that wireless works just fine under Windoze, so there apparently isn't a problem with the card.

---

### Post by pcrofts on 2009-12-02
I did try the suggestion provided here. But it doesn't work. Calling make twice causes problems in the make install.
 
I seem to reliably be able to get the driver to install if I start from a fresh install of Ubuntu then call make as root followed by make install as per the readme instructions.
 
(
sudo make
sudo make install
reboot
)
 
After the reboot the interface is not up. The instructions refer to NetworkManager which seems to be different in 9.10. Also the wpa_supplicant seems to already be running with a different settings. It makes me think the new NetworkManager behaves differently.
If I do a ifconfig wlanX up it will bring up the interface but I have to use the NetworkManager to click and enable wireless. At this point I can try and connect to a network. It will connect to my router but the mac address associate with the card is not the correct one. I'm going to set up another wireless router with zero security to confirm if I can get a connection.
 
I am also unable to see any of the 10 or so wirless networks that are within range.
 
I am going to invite the person from Realtek to review this thread. I really hope he will be able to do so and perhaps offer some advice. But as you can imagine this is asking a lot.

---

### Post by pcrofts on 2009-12-03
Another piece of information. A troubleshooting guide suggest that I should see the same driver in lshw and lsmod but in my system the names are differnt. Does this matter?

  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan3
       version: 10
       serial: 00:e0:4c:81:92:dd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=V 1.1 firmware=49 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:b6100000-b6103fff


root@tosh-unix:/home/paul/rtl8192se_linux_2.6.0010.1116.2009# lsmod | grep 8192
r8192se_pci           453768  0

---

### Post by pcrofts on 2009-12-08
After lots of attempts with release 9.10 for AMD 64 I decided to roll back and try the older 9.04 AMD 64 version. The driver worked perfectly first time. So I guess that's the answer. For the time being if you have a Realtek rtl8191se card in your laptop stick with 9.04

---

### Post by rforsberg on 2009-12-10
duick question:  me in the same boat - koala 64 does not see realtek wireless.
when you rolled back to previous version - did ubuntu detect the hardware automatically or did you have to make the driver as described in the realtek package??
thank in advance.

---

### Post by pcrofts on 2009-12-10
I did a fresh install of 9.04 since it's a new laptop anyway. It's a Toshiba laptop. I had to make the drivers and install them. After reboot it recognized them prompted me there were wireless networks and it's been working great since then.

What is also interesting is that the Atheros ethernet interface did not work on 9.10 but it works perfectly in 9.04 without intervention.

---

### Post by rforsberg on 2009-12-11
Thnbaks for the advice....
So no probs with the make and install commands i.e bounds.c issue?  Just want to make sure that I don't blow away the 9.10 install and get the same make and install errors.
thanks again.

---

### Post by rforsberg on 2009-12-11
apologies for my atrocious spelling.......

---

### Post by pcrofts on 2009-12-12
I had no issues. There were a couple of compile warnings that I saw under 9.10 and under 9.04. But all i did was install 9.04 untar the driver and do
sudo su
make
make install

After rebooting it just worked like magic. I wish it would work with 9.10 but It's working great under 9.04 and trust me that's than the microsoft alternative.

---

### Post by LinuxFanBoi on 2009-12-13
> **pcrofts said:**
> I had no issues. There were a couple of compile warnings that I saw under 9.10 and under 9.04. But all i did was install 9.04 untar the driver and do
sudo su
make
make install

After rebooting it just worked like magic. I wish it would work with 9.10 but It's working great under 9.04 and trust me that's than the microsoft alternative.

Works with 9.10, but before you rolled back you used the following method;

sudo make
sudo make install

This was incorrect. I suggest that you upgrade to 9.10 then run these commands;

```
sudo su
make clean
make
make install
```

Reboot, enjoy!

---

### Post by tito_drum on 2010-01-16
> **pcrofts said:**
> I have a new toshiba p505 laptop. I've installed the 64bit version of Ubuntu 9.10 on it but I just can't get the Realtek RTL8192se wireless card to work. I gave up on the Ndiswrapper and got the linux driver from Realtek. I've attached the driver here as a zip file. I removed the supplied wpa_supplicant archive included with the driver as one already is installed on my ubuntu and I needed to reduce the file size to post.

I have tried following the info in the readme but I can't get it to work with my wpa protected network. If anybody else is trying to get this adapter to work and can try this driver I'd be so grateful if you can tell me if you get it to work.

You should try to find any open wireless and try what toby the second post did. I did it too and it worked for me and others although I downloaded a most recently [version ]("http://www.realtek.com.tw/downloads/RedirectFTPSite.aspx?SiteID=1&DownTypeID=3&DownID=872&PFid=48&Conn=4")from the driver using windows 7 that has no wireless problem of course. I red that driver version worked too.
Once you have the driver extract the files (in my case I create a folder call Realtek like appear in this post I can't find) in my ~/root/computer_name_folder (somehow it didn't work creating it in Desktop, although you can figured it out) 
An the write in the terminal

cd ~/Realtek/rtl8192se_linux_2.6.0010.1116.2009
sudo su
here is going to as your password
make
make install
reboot

and that's it

---

### Post by eburgos on 2010-01-26
> **LinuxFanBoi said:**
> Works with 9.10, but before you rolled back you used the following method;

sudo make
sudo make install

This was incorrect. I suggest that you upgrade to 9.10 then run these commands;

```
sudo su
make clean
make
make install
```Reboot, enjoy!

thanks so much for posting it!
I've been dealing almost a month getting this right on ubuntu 9.10 64 bit (Karmic Koala)
Also after installing the driver, the network would not appear (even after restarting) so I tried searching for wlan in synaptic and installed all missing packages related to network manager and then I didn't even had to reboot! Now it's working better than ever.
hope this can be of help to anyone else dealing with the same situation as me.

Thanks again so much.

---

### Post by maluka on 2010-01-31
Your instructions worked! Thank you!

[IMG]http://i47.tinypic.com/2hnrvat.png[/IMG]

---

### Post by bek on 2010-02-15
Pls, need help, I could install wireless driver as it was said in previous posts, but I am facing another problem.  it is new Toshiba Satellite P505, so i had no problems with installation of 9.10, necessary drivers, but what happened since i have installed wifi, my laptop started to reboot itself, so I thought it is overheating problem, trying to find some solutions, but later on, right now, I am working without wifi, it is work smooth, no problems, and I do the same tasks I did with wifi. so it seems it is soft, right? any comments, how to make wifi work, and not cause problems?

thanks

---

### Post by racer7890 on 2010-02-18
I wrote a guide for people with the Realtek 8172 and 8192se. Hopefully someone will find it useful

[Installing the Realtek 8192se driver]("http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10")

---

### Post by jwaddell on 2010-02-21
> **tubby12 said:**
> save the driver to Desktop
Open the terminal
cd Desktop
unzip \*.zip
cd rtl8192se_linux_2.6.0010.1116.2009
make
sudo su
enter password
make
make install
exit

Thanks.  This worked fine for me on Ubuntu 9.10 on a brand new Toshiba Satellite L505D-ES5025.  I did modify the way I did it slightly [although I suspect it makes no difference].

Downloaded the rtl8192se_linux_2.6.0010.1116.2009.zip file using the wired eth0 connection which works fine.
open a terminal
sudo bash {enter password}

here are the relevant lines from my bash history
   61  cd /home/jeff/Downloads/
   63  unzip rtl8192se_linux_2.6.0010.1116.2009.zip 
   65  cd rtl8192se_linux_2.6.0010.1116.2009/
   67  make
   68  make install
   72  modprobe r8192se_pci
   73  iwconfig
---------
and now I'm typing this thank you message completely via wireless! Thanks again.  :D

---

### Post by u2rcrazy on 2010-03-05
> **tubby12 said:**
> save the driver to Desktop
Open the terminal
cd Desktop
unzip \*.zip
cd rtl8192se_linux_2.6.0010.1116.2009
make
sudo su
enter password
make
make install
exit
[tubby12]("http://swiss.ubuntuforums.org/member.php?u=967473"),

Thanks for your instructions on installing the realtek wireless driver (RTL8192se) on my Toshiba Laptop Model#: Satellite L555D-S7005.  It worked great.  By the way, do you know why Ubuntu doesn't use a GUI install program to install this driver.  This would make it so much easier.  Thanks again.:popcorn:

---

### Post by u2rcrazy on 2010-06-14
Does anybody have  trouble with intermitant connections with Ubuntu 10.045, **[B][[B]NetworkManager  Applet 8.0**]("http://ubuntuforums.org/showthread.php?t=1508501"), using this driver[/B][/B] (Realtek RTL8192se)?  Please See this thread:

**[[B]Ubuntu  10.45 & NetworkManager Applet 8.0:  Connects & Disconnects  Frequently**]("http://ubuntuforums.org/showthread.php?t=1508501")[/B]
[http://ubuntuforums.org/showthread.php?t=1508501](http://ubuntuforums.org/showthread.php?t=1508501)

Thanks,
Bobby

---

### Post by u2rcrazy on 2010-06-21
Please see this post below for more information and email correspondence with Realtek:

 				[[IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG] 				**How To:  Uninstall/Remove Old Wireless Driver to make way  for New Driver (RTL8191SE)?**]("http://ubuntuforums.org/showthread.php?t=1514883")


In this external post you'll see:
			

[LIST]
[*]Emails detailing how to uninstall the old driver and install the new driver
[*]pleading for interpretation on how to uninstall the old driver  (they didn't answer requests for more detailed uninstall information)
[*]emails detailing how to install the new driver
[*]and more
[/LIST]

---

