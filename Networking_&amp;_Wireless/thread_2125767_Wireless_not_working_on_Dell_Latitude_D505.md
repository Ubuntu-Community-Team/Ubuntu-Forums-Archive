---
title: "Wireless not working on Dell Latitude D505"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by rwwhite@eastex.net on 2013-03-15
I installed the latest version of Ubuntu (as of March 14, 2013) on my Dell Latitude D505 after reformatting the hard drive.  All available updates have been applied.  The system seems to work well.  It has internet access when wired to my router, but the wireless does not work.

The wireless did work with the router with Windows so the hardware is OK.  I find no hardware switch on the laptop.  There is bound to be some software step I need to find.

I know a little about DOS and Windows but am a newbie about Ubuntu.  I do not even know how to view the Ubuntu version number.  Where do I start to enable the wireless capability and then search for my LAN?

Help will be appreciated.  It is probably something simple.

Thanks.

R W White

---

### Post by varunendra on 2013-03-15
Welcome to the forums rwwhite, :)

For starters with the wireless, we'd need to look at the command output of-
```
lspci -nnk | grep -iA2 net
```

And to let us know of your Ubuntu version and kernel it is using -
```
uname -mr
lsb_release -d
```

Enter these commands in a terminal (Ctrl+Alt+T) and post back their outputs here.

Thanks!

---

### Post by buttonmasher2 on 2013-08-09
> **varunendra said:**
> Welcome to the forums rwwhite, :)

For starters with the wireless, we'd need to look at the command output of-
```
lspci -nnk | grep -iA2 net
```

And to let us know of your Ubuntu version and kernel it is using -
```
uname -mr
lsb_release -d
```

Enter these commands in a terminal (Ctrl+Alt+T) and post back their outputs here.

Thanks!

I'm sorry to dig up an old thread, but this is exactly the issue I'm having with my D505. 

I posted the question here on the linuxquestions subreddit and poked around the forums here a bit more and found this thread.
[http://www.reddit.com/r/linuxquestions/comments/1jztwu/lubuntu_12042_lts_dell_d505_laptop_wifi_problem/](http://www.reddit.com/r/linuxquestions/comments/1jztwu/lubuntu_12042_lts_dell_d505_laptop_wifi_problem/)

Here's what I wrote:
[COLOR=#000000][FONT=verdana]I've got Lubuntu installed and everything seems good to go aside from the wifi not working. I was very determined to get this up and running over a month ago and read/tried various things from the forums and nothing took. So I put it down for a while. But I'm back at it. I'm still new to Linux but I'm learning more all the time. I'm down to only using Windows at work. Here are a couple of the places I was using.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][http://ubuntuforums.org/showthread.php?t=1876860](http://ubuntuforums.org/showthread.php?t=1876860)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]running Additional Drivers finds[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Broadcom STA wireless driver[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]But when I try to install it, the progress bar will get to about 80% or so and this happens[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana][http://imgur.com/Efc8GDE](http://imgur.com/Efc8GDE)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Any help?[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Also, and I can only assume this is a long shot, there's an S-Video out on this laptop and having that work would be great. But I wouldn't even know where to begin.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Following what Varun said, I get this:

[/FONT][/COLOR]01:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridge
--
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 81)
    Subsystem: Dell Latitude D500 [1028:2002]
    Kernel driver in use: e100


And this:

3.2.0-48-generic i686
Description:    Ubuntu 12.04.2 LTS



Thank you for your time.

---

### Post by varunendra on 2013-08-09
> **buttonmasher2 said:**
> 01:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g **[14e4:4324]** (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridge

If you have a wired connection available, please do -
```
sudo apt-get install linux-firmware-nonfree
```

If you don't have any way to connect to internet, manually download the above package from here : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download) , then copy the package to your Ubuntu machine and double-click it to install.

Once it is installed, purge the sta driver if it is present -
```
sudo apt-get purge bcmwl-kernel-source
```

Then just reboot, or manually (re)load the correct driver as follows -
```
sudo modprobe -rfv b43
sudo modprobe -v b43
```

---

### Post by buttonmasher2 on 2013-08-09
> **varunendra said:**
> If you have a wired connection available, please do -
```
sudo apt-get install linux-firmware-nonfree
```

If you don't have any way to connect to internet, manually download the above package from here : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download) , then copy the package to your Ubuntu machine and double-click it to install.

Once it is installed, purge the sta driver if it is present -
```
sudo apt-get purge bcmwl-kernel-source
```

Then just reboot, or manually (re)load the correct driver as follows -
```
sudo modprobe -rfv b43
sudo modprobe -v b43
```


That's the stuff! Thank you, very much. I wish I could mark this problem as solved but it's not my thread. Good deal. 


Now, not to be too much of a pain in the butt... Any ideas on how to get the S-Video out to work? No sweat, if not. The wireless was the actual problem. Getting the video output to work would just be cool. 

Again, thanks.

---

### Post by chili555 on 2013-08-09
> **buttonmasher2 said:**
> That's the stuff! Thank you, very much. I wish I could mark this problem as solved but it's not my thread. Good deal. 


Now, not to be too much of a pain in the butt... Any ideas on how to get the S-Video out to work? No sweat, if not. The wireless was the actual problem. Getting the video output to work would just be cool. 

Again, thanks.The s-video guys are over here: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334) They don't let us fool with the fun stuff here in wireless jail.

---

### Post by buttonmasher2 on 2013-08-10
> **chili555 said:**
> The s-video guys are over here: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334) They don't let us fool with the fun stuff here in wireless jail.

Excellent. Thanks. 

And while it might feel like you're in wireless jail away from the fun, without you networking guys and your skills, we non-networky types wouldn't be able to even get to the party, let alone have fun there. So, thanks for sharing.

---

