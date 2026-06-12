---
title: "RTL8188CE realtex wireless, new in 12.04"
date: 2012-08-19
forum: Networking &amp; Wireless
---

### Post by PhilLord on 2012-08-19
I am having significant problems with the internal wireless in my notebook, which is a Toshiba. The card in question is an RTL8188CE. The network connects, but then after a while hangs with no connectivity, although NM claims that there is connection. 

The error appears to occur shortly after syslog reports a WPA rekey

WPA: Group rekeying completed with...

although "after" appears to be 1 or 2 minutes. 

It's quite a pain. I have found no fix yet, other than unloading and loading the kernel module. Existing connections generally get broken in this process. 10 minute connectivitiy at a time is quite an issue. 

This is new in 12.04, as far as I can tell. The network appeared to be okay before I upgraded from 11.10, although, of course, I cannot repeat this experiment. 

Any help gratefully recieved. 

Phil

---

### Post by metalllama on 2012-10-21
I'm looking for a solution to the same problem. It seems like this is a pretty common. I just bought a new Toshiba C855 for school and I haven't been able to really use my ubuntu partition since I got it because I need the internet when I'm on my pc. If I come across anything I will let you know.

---

### Post by kurt18947 on 2012-10-21
You might give this a try:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Download the RTL8188CE package, extract it to an account with SUDO privileges and a  location you can find again ;). Open a terminal, navigate to the extracted files and look for installer.sh or similar.  Type "sudo bash (installer name)" e.g. sudo bash installer.sh.  I've had pretty good luck with an RTL-8188Cus device using this procedure.

---

### Post by SunnyDaze on 2012-10-22
I am having major problems with the Toshiba PA3839U-1MPC radio device that came with my Toshiba Laptop model C855D-S5203.  The Wireless freezes my laptop when it is on and connected.

I ran:
sudo lshw -C network

And it said my device was the Realtek RTL8188CE 802.11b/g/n WiFi Adapter, which must be the chip the Toshiba PA3839U-1MPC is using.

Both Ubuntu 12.04 and Linux Mint 13 (Maya) will set up the hardware automatically, but if I have the wireless turned on and connected, it works fine for a few minutes, and then both Ubuntu and/or Mint will completely freeze.  Everything stops working. . . mouse, keyboard, etc.  I can't even get the "REISUB" SysRq key sequence to do anything. At this point I have to press and hold the power button, too shut the system down.

If I turn off the WiFi in the network manager, the computer will run just fine.  This of course means I have no Wireless network.  This isn't an option, since it's a laptop, and WiFi is a must.

:(

I will let you know if I figure anything out.

---

### Post by SunnyDaze on 2012-10-22
> **kurt18947 said:**
> You might give this a try:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Download the RTL8188CE package, extract it to an account with SUDO privileges and a  location you can find again ;). Open a terminal, navigate to the extracted files and look for installer.sh or similar.  Type "sudo bash (installer name)" e.g. sudo bash installer.sh.  I've had pretty good luck with an RTL-8188Cus device using this procedure.

Before I tried to compile this, I installed the "build-essential" package.

Then I tried to compile, but the RTL8188CE driver won't compile.  Get an "Error 2" message while trying to compile.

---

### Post by kurt18947 on 2012-10-23
> **SunnyDaze said:**
> Before I tried to compile this, I installed the "build-essential" package.

Then I tried to compile, but the RTL8188CE driver won't compile.  Get an "Error 2" message while trying to compile.

Oh dear, that is not like the downloads I've gotten from that site.  I did download the RTL8188CE  and looked at it.   I'm no guru and I don't have an 8188CE device to try installing.  I did open the download, clicked on the 'compat' folder and one of the folders within is labeled 'script'.   Click 'script' and the contents include several shell scripts, one of which is "compat-install.sh".  I'm not sure if that would install the correct driver or not.  Perhaps try emailing support at RealTek?  

The other concern with this is that there is no mention of Ubuntu  11.xx or 12.xx  though the release notes were last modified on 08 Aug. 2012.  I wonder if this is the up-to-date driver for this chip set.

---

### Post by voodoomurphy on 2013-01-28
> **PhilLord said:**
> I am having significant problems with the internal wireless in my notebook, which is a Toshiba. The card in question is an RTL8188CE. The network connects, but then after a while hangs with no connectivity, although NM claims that there is connection. 

The error appears to occur shortly after syslog reports a WPA rekey

WPA: Group rekeying completed with...

although "after" appears to be 1 or 2 minutes. 

It's quite a pain. I have found no fix yet, other than unloading and loading the kernel module. Existing connections generally get broken in this process. 10 minute connectivitiy at a time is quite an issue. 

This is new in 12.04, as far as I can tell. The network appeared to be okay before I upgraded from 11.10, although, of course, I cannot repeat this experiment. 

Any help gratefully recieved. 

Phil

I'm having a similar issue in 12.10 with the same card. It doesn't lock up completely but it does hang for a second and network connectivity seems to drop frequently. I've tried installing the drivers from Realtek but not having any luck. I've also disabled IPv6 and changed my wifi encryption to WPA2.

---

### Post by SunnyDaze on 2013-03-28
I finally had time to sit down and tinker with this, and I think I got it to work.

I was having "error 2" issues whenever I tried to compile the driver.  I think this was due to the fact that I was trying to compile from a shared folder that was in a location other than my home path.  That folder probably did not have the proper permissions, but I'm not entirely sure.  It seems that back in the day I had to save code in my home path whenever I wanted to compile programs, but I haven't had to compiled Linux source much in the last 7 or 8 years, so I don't remember the details.

In the end I downloaded the driver from Realtek's website, and put it on my desktop.

Here are the steps:

1.  Make sure you have the developement code on you computer by typing **sudo apt-get install build-essential**
2.  Figure out what Linux kernel you have by typing **uname -a**
3.  Figure out what Realtek wireless chip you have by typing **sudo lshw -C network**
4.  Download the Realtek source code for your wireless chip & Linux kernel version from here:  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)
5.  Save the download to your desktop (If you save elsewhere, the directory might not have proper permissions.)
6.  Open a terminal, and type **sudo su**
7.  Change to the folder on your desktop that was created when you extracted the download.  **cd /home/YourUserNameGoesHere/Desktop/NameOfExtractedFolderGoesHere**
8.  Type **make install**.  There is no need to go into any of the sub-folders to compile the driver.
9.  When it is done compiling, type **reboot**
10.  Once rebooted, you should be able to find and connect to your network.

Here is a video explaining most of this procedure.  The video doesn't tell you how to find your kernel version, or your wireless chipset version.  You will need to watch this video in High Def, since he never zooms in on what he is doing.

[http://www.youtube.com/watch?v=QFh2EZhUKgs](http://www.youtube.com/watch?v=QFh2EZhUKgs)

---

### Post by SunnyDaze on 2013-04-18
> **SunnyDaze said:**
> 
Here are the steps:

1.  Make sure you have the developement code on you computer by typing **sudo apt-get install build-essential**
2.  Figure out what Linux kernel you have by typing **uname -a**
3.  Figure out what Realtek wireless chip you have by typing **sudo lshw -C network**
4.  Download the Realtek source code for your wireless chip & Linux kernel version from here:  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)
5.  Save the download to your desktop (If you save elsewhere, the directory might not have proper permissions.)
6.  Open a terminal, and type **sudo su**
7.  Change to the folder on your desktop that was created when you extracted the download.  **cd /home/YourUserNameGoesHere/Desktop/NameOfExtractedFolderGoesHere**
8.  Type **make install**.  There is no need to go into any of the sub-folders to compile the driver.
9.  When it is done compiling, type **reboot**
10.  Once rebooted, you should be able to find and connect to your network.


I have been used this newly compiled driver for a couple weeks now without any issues.

This solved my problem, hope it solves your issue as well.

---

