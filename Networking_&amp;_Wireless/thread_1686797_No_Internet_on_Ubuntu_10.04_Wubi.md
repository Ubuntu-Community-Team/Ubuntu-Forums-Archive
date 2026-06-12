---
title: "No Internet on Ubuntu 10.04 Wubi?"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by Okaithx on 2011-02-12
Hello, I am a new user and would like to find out why I have no internet coming in from my wireless router/modem in my install of Wubi 10.04. I had heard that there were wireless problems with 10.10 which is why I decided to go with sourceforge.net's download of 10.04.01. Now, here's my problem.

I set up my SSID and WEP key in a new Wireless connection entry in the Wireless tab of the window that appears when "Configure VPN" is clicked from the right-click menu of the Network Manager icon. However, when left-clicking the Network Manager icon after I had applied this wireless entry, it said "Device not ready" or something like that. My wireless receiving function on my Dell Inspiron 1545 was turned on during this, and so was my router/modem.

Also, the sudo lshw -C network code Terminal thing said that my wireless was "DISABLED" and the help file says to see if everything is turned on. Since everything WAS, I don't have a clue on what to do next.

I am able to do the following if suggested:

-Install 10.10 instead
-Retry the connection with everything turned on 100%
-Switch my wireless on/off
-Uninstall Ubuntu and not use it (really don't want to do this, Ubuntu is AWESOME and I would like to get connected!)

I do not have an ethernet cable in which to plug in a wired connection. Also, connecting with Windows 7 automatically detected my router and only required the WEP key, so that really wasn't hard, which is why this advanced connecting stuff is confusing to me.

Also sometimes it tells me that wireless is disabled and it greys out the option to enable it, almost like it wants me to not connect!

Please help ASAP! Thanks!

-Okaithx :D

---

### Post by Okaithx on 2011-02-13
Can no one really help me on this?

---

### Post by Okaithx on 2011-02-13
Need some help over here...

I have a Broadcom Corp. BCM 4312 which is supposed to work if you install the drivers but I don't know how to do that on Wubi. I can't connect to the internet on linux so i can't access the drivers there either.

---

### Post by nl4m on 2011-02-13
On the top panel, right hand side, you'll an icon with 2 computers and a red "X" on them. Click that icon, you'll get a drop down menu with the list of all the available wireless networks in the area. Click on yours and a "Password" window will pop up. Enter your password and see if it connects... I've been using wubi Ubuntu since 8.04, now using 10.10, and never had a problem with the wireless.

---

### Post by Okaithx on 2011-02-13
Do not see two computers and a red x, nor do I see 2 computers or a red x separate. All I see is the Shutdown options button, the clock, the chat button, the email envelope button, and the network manager button which, when pressed, will reveal that I have no wired connection (obviously if I'm trying to get wireless) and that under wireless it says "Device not ready."

Is there perhaps more help on this matter that you or someone you know could provide?

---

### Post by nl4m on 2011-02-13
^ Yes, the network manager. Try to right click it and see if it gives you the option of "Enable Wireless". If that option is not there you should connect the computer through the ethernet cable and update it. 

On my other computer I've had the same problem where my wireless card was not working. I found some drivers on online for it and installed them. It worked perfectly fine after that. When I upgraded the distro it worked without the need to install the drivers.

---

### Post by Okaithx on 2011-02-13
Yes, the option is there, but not when the wireless is turned off via computer switch. However when wireless is on via switch, the Wireless Connection says "device not ready."

---

### Post by nl4m on 2011-02-13
Turn the wireless switch "ON" (on the computer, itself) then shutdown and reboot. If the daemon is asleep rebooting should solve it. If that does not work get to the error message and hit the button "Print Screen" or "PrtSc", take a picture of the error and post it.

---

### Post by Okaithx on 2011-02-13
I don't know what having the daemon asleep means, nevertheless I tried what you said and it did nothing. Maybe it's because the wireless is automatically turned off during shutdown? Anyway I tried to take a screenshot while having the panel menu open but it wouldn't let me so here's the problem in text form:

After clicking the Network Manager icon, I get this menu:

---------------------------
| [COLOR=Black]**Wired Network**[/COLOR]      |
|   [COLOR=Gray]disconnected[/COLOR]          |
|                               |
| **Wireless Network**  |
|  [COLOR=Gray]device not ready[/COLOR]     |
---------------------------
| VPN Connections...   |
---------------------------

The right border is a little messed up in text form but if you've seen this drop-down menu you know what I'm talking about.

---

### Post by nl4m on 2011-02-13
According to this website it is a driver issue:
[http://www.hamrobrt.com/solved-wireless-wifi-in-ubuntu-9-10-10-04/](http://www.hamrobrt.com/solved-wireless-wifi-in-ubuntu-9-10-10-04/)

What you should do is press "ALT+F2" at the same time. This will bring up a window. In it type, in small letters "GNOME-TERMINAL". When the terminal pops up type in:
```
sudo lshw | grep -i "network"
```

Push in your password and wait for the output. Once done look for "product:". What ever is listed after that it is the name of your wireless card. Mine is "PRO/Wireless 2915ABG". Take the name of your wireless card and type in google search "(wireless card name) driver linux". Once you find the drivers I'll walk you through the rest (installing them).

An easier way would be just to do an update. If that does not work try upgrading the distro to 10.10. If you have something important, backup the whole "Ubuntu" folder. Or copy the files to the windows partition.

---

### Post by Okaithx on 2011-02-14
> **nl4m said:**
> According to this website it is a driver issue:
[http://www.hamrobrt.com/solved-wireless-wifi-in-ubuntu-9-10-10-04/](http://www.hamrobrt.com/solved-wireless-wifi-in-ubuntu-9-10-10-04/)

What you should do is press "ALT+F2" at the same time. This will bring up a window. In it type, in small letters "GNOME-TERMINAL". When the terminal pops up type in:
```
sudo lshw | grep -i "network"
```Push in your password and wait for the output. Once done look for "product:". What ever is listed after that it is the name of your wireless card. Mine is "PRO/Wireless 2915ABG". Take the name of your wireless card and type in google search "(wireless card name) driver linux". Once you find the drivers I'll walk you through the rest (installing them).

An easier way would be just to do an update. If that does not work try upgrading the distro to 10.10. If you have something important, backup the whole "Ubuntu" folder. Or copy the files to the windows partition.

I might try the hard way with the drivers, but what do mean by an easier is to just do an update? What is "an update"? That is a little vague. And I actually did try 10.10 Wubi, but the problem was there as well.

My wireless card is a Broadcom BCM4312. I found that out yesterday.

---

### Post by femi.aiyeku on 2011-02-14
i m using dual boot on my HP laptop,windows 7 and ubuntu 10.10,whenever i boot in my ubuntu 10.10,my internet connection keeps timing out and i have to restart my system to reconnect and after about 10-15 mins ,the internet times out agains, pls i need your assistance.......reply

---

### Post by jermanbdogg on 2011-02-14
I am having the same issues. I managed to get a new driver. But I am stuck at not having a wireless but now have just ethernet. Maybe our postings can collaborate?  :p

[http://ubuntuforums.org/showthread.php?t=1687914](http://ubuntuforums.org/showthread.php?t=1687914)

---

### Post by PRC09 on 2011-02-14
For Broadcom cards see the link below.However I am only assuming that the instructions work in wubi as I have never used it........


[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by nl4m on 2011-02-14
> **Okaithx said:**
> I might try the hard way with the drivers, but what do mean by an easier is to just do an update? What is "an update"? That is a little vague. And I actually did try 10.10 Wubi, but the problem was there as well.

My wireless card is a Broadcom BCM4312. I found that out yesterday.


All the software that you run, no matter the Operating System, need to be updated. For example, you have Flash player 10, tomorrow Flash player 11 comes out and you have to update to the newest version. You have Windows media player 8, 9 comes  out so you update. The Linux kernel is a monolithic one. What that means is that all the drivers are built into the kernel. In another words, every time a new kernel is released it has new drivers in it. I thought that if you do an update of the kernel, not the distro, that it might have the latest drivers. To do an update for programs/kernel/security/distro go to the top panel, click on "System", "Administration", "Update Manager". When the window pops up click on "Check" and then "Install", if there is an update.

I *think* this maybe the driver you need. Once again before doing anything please back your files up. I don't want to be held accountable for any errors or lost files. 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

If your computer is a 32-bit system, here is a direct link:
[http://www.broadcom.com/docs/linux_sta/hybrid-portsrc_x86_32-v5_100_82_38.tar.gz](http://www.broadcom.com/docs/linux_sta/hybrid-portsrc_x86_32-v5_100_82_38.tar.gz)

Save the download to your desktop folder. That's /home/(username)/Desktop. Once saved launch the terminal, the whole "ATL+F2", "gnome-terminal". In the terminal type in:
```
cd /home/$(whoami)/Desktop
``` 

Then type in:
```
tar zxf hybrid-portsrc_x86_32-v5_100_82_38.tar.gz
```

Then enter:
```
./configure
```

Followed by:
```
make
```

And lastly:
```
make install
```

Now just restart your PC with the wireless switch "ON". It *should* work.  If you have any questions or if my explanation was not clear enough let me know.

---

### Post by nl4m on 2011-02-14
@[PRC09]("http://ubuntuforums.org/member.php?u=774899") - Wubi, at it's core, is a bootloader designed to boot Linux filesystems from with in Windows' NTFS. Once booted everything is the same.

@femi.aiyeku - It sounds like it might be a router/modem problem. How is the internet connect in windows 7? Does it drop the connect as well?

---

### Post by jermanbdogg on 2011-02-14
I tried this one before too and it didn't work for me, but it might for others. I just tried it again too and I am still at the same spot as before. Got ethernet but no wireless.

---

### Post by Okaithx on 2011-02-15
> **nl4m said:**
> All the software that you run, no matter the Operating System, need to be updated. For example, you have Flash player 10, tomorrow Flash player 11 comes out and you have to update to the newest version. You have Windows media player 8, 9 comes  out so you update. The Linux kernel is a monolithic one. What that means is that all the drivers are built into the kernel. In another words, every time a new kernel is released it has new drivers in it. I thought that if you do an update of the kernel, not the distro, that it might have the latest drivers. To do an update for programs/kernel/security/distro go to the top panel, click on "System", "Administration", "Update Manager". When the window pops up click on "Check" and then "Install", if there is an update.

I *think* this maybe the driver you need. Once again before doing anything please back your files up. I don't want to be held accountable for any errors or lost files. 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

If your computer is a 32-bit system, here is a direct link:
[http://www.broadcom.com/docs/linux_sta/hybrid-portsrc_x86_32-v5_100_82_38.tar.gz](http://www.broadcom.com/docs/linux_sta/hybrid-portsrc_x86_32-v5_100_82_38.tar.gz)

Save the download to your desktop folder. That's /home/(username)/Desktop. Once saved launch the terminal, the whole "ATL+F2", "gnome-terminal". In the terminal type in:
```
cd /home/$(whoami)/Desktop
```Then type in:
```
tar zxf hybrid-portsrc_x86_32-v5_100_82_38.tar.gz
```Then enter:
```
./configure
```Followed by:
```
make
```And lastly:
```
make install
```Now just restart your PC with the wireless switch "ON". It *should* work.  If you have any questions or if my explanation was not clear enough let me know.

Okay I get ya. But, two things.

1. Do I need to place the driver on, say, an SD Card to save it to the Linux desktop, or is this going to take it from my Windows desktop?

2. If the wireless switch turns off between every reboot automatically, how can it stay on? Or does it just need to be on until the PC is restarted?

---

### Post by nl4m on 2011-02-16
> **Okaithx said:**
> Okay I get ya. But, two things.

1. Do I need to place the driver on, say, an SD Card to save it to the Linux desktop, or is this going to take it from my Windows desktop?

2. If the wireless switch turns off between every reboot automatically, how can it stay on? Or does it just need to be on until the PC is restarted?

If you plan on downloading the driver from your Linux partition, after you launch firefox (or whatever your browser is) choose "Desktop" as the place/destination to save it. If you plan on downloading the driver from with in your windows partition you might need a form of an external storage device (SD, Flash, external HDD...). Reboot into Linux Ubuntu, plug your external device in, and drag and drop the downloaded package to your desktop and follow the codes. 

The wireless switch will remain "ON" for as long as the computer is turned on itself, and the switch is in the "ON" position.  If you turn off the computer, there is no power flowing through the PC so the wireless card is turned off, too. Once you turn the PC on again-- if the wireless switch is on the "ON" position-- it will turn itself on along with the rest of the computer. It is always best to leave the wireless switch "ON", unless you need to conserve power. 


@jermanbdogg - Please tell me more about the problem. What is the error message? what is the name of your wireless card? Did you try to update? Also can you post the output of these commands:
```
uname -r
```

```
sudo lshw
```

```
ifconfig
```

```
cat /etc/network/interfaces
```

---

### Post by jermanbdogg on 2011-02-16
I managed to get mine up and running. It turns out that I have the LP-PHY version of the Broadcom 4312 chip. It required that I compile a specific version of the driver from source. I marked my posting as solved. Everyone here should take a look as I have my entire ordeal documented and might help solve this one as well.

[http://ubuntuforums.org/showthread.php?t=1687914](http://ubuntuforums.org/showthread.php?t=1687914)

---

