---
title: "Broadcom 4318, ndiswrapper, not even getting powered on."
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by Slicedbread on 2006-06-07
So I have a dreaded Broadcom 4318 wireless chipset which has been nothing but a pain. I tried the bcm43xx driver first and when I did get it to work (3 times out of many fresh installs), it was way too flaky- I managed to break it by just going into the default network manager or starting as a different session; So I have given up with that and I am now trying ndiswrapper. I have had no success with it either, I cant even get the wifi button to light up. 

It seems to me that the device is not being powered on or initiated because it will not retrieve any scan results. *iwconfig* and ubuntu strangely enough still detect the card even if I disable it in the bios. I have followed the guides thoroughly and have even compiled ndiswrapper to see if that would work, it doesnt. Ndiswrapper says that the *driver installed, hardware present* but there is no way to activate it, every post that I have seen at least was able to see wireless networks but I cant, so Im trying to see if anyone else has any suggestions.

TIA, I hope to be having problems getting to connect with WPA soon! Either that or try a different distro.

---

### Post by MarkSheely on 2006-06-08
I have the same card.  The instructions at the following post worked for me:

[http://ubuntuforums.org/showpost.php?p=1085392&postcount=55](http://ubuntuforums.org/showpost.php?p=1085392&postcount=55) 

Let me know if you encounter any problems, I'll do my best to help out.

--Mark

---

### Post by Slicedbread on 2006-06-08
Heh thats funny, you linked to a solution posted by myself. The default bcm43xx driver is flaky at best, I already solved the problem, it was the /etc/network/interfaces file and its alias.

Originally Posted by crag277
First of all, thanks to all the posts on these forums I'm posting from a wireless connection, and I have a Broadcom 4318 "AirForce One 54g".

Here's how I did it, maybe it'll help someone. You don't even need an internet connection.

The drivers I used are attached to the message. To follow this guide to a T downlad them and place in a folder bcm43xx on your desktop.

I've tried the procedure in this HowTo several times, on different versions of Dapper, with different drivers and it would never work. I had to use ndiswrapper to get it working.

I'm running Ubuntu i386 Dapper, Turion 64, ATI Radeon XPRESS 200M.

1) Blacklist bcm43xx driver
Open a Terminal window
Type "sudo gedit etc/modprobe.d/blacklist"
At the bottom add the lines
# get rid of the default kernel drivers
blacklist bcm43xx

2) Make sure network interfaces file is correct
Type "sudo gedit /etc/network/interfaces"
Remove all comments ('#') that you see so that all devices arehandled by the default network manager.
I would reboot here and make sure the wireless light goes out

3) Install ndiswrapper
Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.You could also type "sudo apt-get install ndiswrapper-utils

4) Conigure ndiswrapper
Open termianl and navigate the folder where your drivers are."cd Desktop/bcm43xx"
Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit. If it worked, you should be able to click the Network Manager icon in the top right. It will probably show a disconnected ennection becuase the computer is not plugged in.
Left click it and select eth1 from the drop down menu.
Click Configure
Click Wireless Connection, then Properties. Here just enter your network information. If you're using an unprotected network you should only have to type yout SSID.

Click OK and you should now be connected! If a green signal meter and connected network icon appear in the upper right you'll know it worked.

Hope this helps!

---

### Post by MetalMusicAddict on 2006-06-13
Slicedbread. If you were here I would kiss you. Ive been ](*,) for weeks now. I actually got the native driver working but it wouldnt work at boot. I would always have to got to the prefs of the wireless card and then it would connect. Very weird. Just wouldnt work at boot. Thanx man.

---

### Post by xxrealmsxx on 2006-06-14
[QUOTE=Slicedbread]Heh thats funny, you linked to a solution posted by myself. The default bcm43xx driver is flaky at best, I already solved the problem, it was the /etc/network/interfaces file and its alias.

Originally Posted by crag277
First of all, thanks to all the posts on these forums I'm posting from a wireless connection, and I have a Broadcom 4318 "AirForce One 54g".

Here's how I did it, maybe it'll help someone. You don't even need an internet connection.

The drivers I used are attached to the message. To follow this guide to a T downlad them and place in a folder bcm43xx on your desktop.

I've tried the procedure in this HowTo several times, on different versions of Dapper, with different drivers and it would never work. I had to use ndiswrapper to get it working.

I'm running Ubuntu i386 Dapper, Turion 64, ATI Radeon XPRESS 200M.

1) Blacklist bcm43xx driver
Open a Terminal window
Type "sudo gedit etc/modprobe.d/blacklist"
At the bottom add the lines
# get rid of the default kernel drivers
blacklist bcm43xx

2) Make sure network interfaces file is correct
Type "sudo gedit /etc/network/interfaces"
Remove all comments ('#') that you see so that all devices arehandled by the default network manager.
I would reboot here and make sure the wireless light goes out

3) Install ndiswrapper
Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.You could also type "sudo apt-get install ndiswrapper-utils

4) Conigure ndiswrapper
Open termianl and navigate the folder where your drivers are."cd Desktop/bcm43xx"
Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit. If it worked, you should be able to click the Network Manager icon in the top right. It will probably show a disconnected ennection becuase the computer is not plugged in.
Left click it and select eth1 from the drop down menu.
Click Configure
Click Wireless Connection, then Properties. Here just enter your network information. If you're using an unprotected network you should only have to type yout SSID.

Click OK and you should now be connected! If a green signal meter and connected network icon appear in the upper right you'll know it worked.

Hope this helps![/QUOTE]

I want to try this method but before I go ahead and do so I just wanted to ask a quick question:

Is my modprobe.d/blacklist file supposed to be empty? Other than that I believe i'll give ndiswrapper a go, the other method is too buggy and keeps getting me disconnected on campus.

---

### Post by MetalMusicAddict on 2006-06-14
No it not supposed to be empty. Make sure you have the path to it right. Otherwise it will bring up (create) a blank file.

---

### Post by xxrealmsxx on 2006-06-14
[QUOTE=MetalMusicAddict]No it not supposed to be empty. Make sure you have the path to it right. Otherwise it will bring up (create) a blank file.[/QUOTE]

I found the correct file.

Thanks!

Now I just have to find the windows driver.

*edit*

nevermind!

---

### Post by xxrealmsxx on 2006-06-14
well that screwed my internet up

I successfully blacklisted the linux drivers

guess its time to reformat and try again -_-.

---

### Post by compwiz18 on 2006-06-16
If that doesn't work try [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) that post by me.  It has the drivers, and a script to automatically set it up.  Just download and run.

---

### Post by xxrealmsxx on 2006-06-16
[QUOTE=compwiz18]If that doesn't work try [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) that post by me.  It has the drivers, and a script to automatically set it up.  Just download and run.[/QUOTE]

I will try that later, i am currently having different problems highlighted here:

[http://www.ubuntuforums.org/showthread.php?p=1145227#post1145227](http://www.ubuntuforums.org/showthread.php?p=1145227#post1145227)

I believe one of my problems is i need a different driver due to my laptop not having bluetooth.

---

### Post by ????? on 2006-06-16
I have the same card, and ndis worked, but it does not want to work in the new kernel (got via Update Manager), but it works in the old kernel. In the new kernel it says hardware present.. have you tried the old kernel to see if it works?

---

### Post by xxrealmsxx on 2006-06-16
[QUOTE=?????]I have the same card, and ndis worked, but it does not want to work in the new kernel (got via Update Manager), but it works in the old kernel. In the new kernel it says hardware present.. have you tried the old kernel to see if it works?[/QUOTE]

how do i revert to the old kernel

also do i need to get the old linux-headers file?

---

### Post by noname101 on 2006-06-16
To get the old kernel back reboot and in the grub menu select the old kernel. The old kernel is Ubuntu, kernel 2.6.15-23-386 for me anyways.

---

### Post by trubblemaker on 2006-06-18
check the signature for some howto's not as simple as >  compwiz18
If that doesn't work try [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) that post by me. It has the drivers, and a script to automatically set it up. Just download and run. 
but gives some more understanding.

hope this helps

---

