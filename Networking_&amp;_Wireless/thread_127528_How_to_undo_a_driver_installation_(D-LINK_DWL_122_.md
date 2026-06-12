---
title: "How to undo a driver installation (D-LINK DWL 122  - RT2570)"
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by rama on 2006-02-09
Hello
I bought a D-Link DWL 122 USB stick and followed the instructions in this thread to make it work.
[http://www.ubuntuforums.org/showthread.php?t=106846](http://www.ubuntuforums.org/showthread.php?t=106846)
When I reached this step: 

sudo /etc/init.d/networking restart

My computer hanged. I rebooted the system and it always hangs at a point. 
I searched the forum and found out that I can skip the setp where it hangs by pressing Ctrl+C and log in to the system. Another way would be to boot from a Live CD.
My question is what can I do to undo all the steps from the How-To and try something else? Is there a configuration file I can alter so that I can remove the rt2570.ko driver from loading? Or can I log in by pressing Ctrl+C and then do a:
sudo rmmod /lib/modules/`uname -r`/drivers/rt2570.ko

I am guessing that there is a list of modules/drivers somewhere that the system reads and activates during initialization (boot). Which file is that?

PS: Yes I am a noob... :rolleyes:

EDIT: I currently **dont** have another wifi device in the house so naturally I wont be able to connect to anything should the driver work. I m expecting a wifi router to be delivered shortly though...

---

### Post by rama on 2006-02-09
OK so I managed to boot the computer (taking the sub stick off was enough) and then I commented out everything I added in /etc/network/interfaces.

I tryied the linux-wlan-ng driver and it works. Iwconfig shows the device, I ran wifi radar (only to find that no network is available). I dont know about WEP and WPA yet. The problem now is using gnome network manager ("networking"). I can see the wifi card detected, but it says that it si not configured. So I press configure and the system nearly hangs. It does respond but it is extremly slow ... eg it's been almost 15 minutes now that I typed "sudo reboot" and its still shutting down deamons...

EDIT: I was wrong about tha rt2570 driver. It works! linux-wlan-ng had nothing to do with the device being recognized... Anyway I 'd still like to know why gnome network manager ("networking") crashes my computer.

---

