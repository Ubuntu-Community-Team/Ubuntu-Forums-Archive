---
title: "firmware-b43-installer error!!!"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by divyansh.sachdeva on 2011-09-11
Here's the problem: 

I'm new to Ubuntu and my wi-fi wasn't working, so I tried to install **firmware-b43-lpphy-installer** using Synaptic Package Manger. It didn't install and exited with error status 1. So I tried to uninstall the partial package and re-install the **firmware-b43-installer**, but it won't install now either. 

It tries to connect to a remote mirror and exits with error status 4 after multiple unsuccessful attempts at connecting. 

Also, now each time I boot up my system, a message window pops up saying that there's an error with the system files and points to firmware-b43-installer. 

Please help, and also tell if I really do need to install it????

Details:

Laptop: Toshiba L650
OS: Ubuntu 11.04(Natty)
Card: Broadcom BCM4313

Please help!!!

---

### Post by coffeecat on 2011-09-11
I've closed your other thread here:

[http://ubuntuforums.org/showthread.php?t=1841982](http://ubuntuforums.org/showthread.php?t=1841982)

Since you have complicated the situation with the firmware-b43-installer I haven't merged the two threads, but in future please do not create more than one thread on the same problem. It dilutes community effort.

But to your technical problem. The firmware-b43-installer package is not appropriate to your bcm4313 chipset. From your previous thread I see that there was evidence for both the open source driver and the proprietary STA driver being installed, and either of these should have worked, and you need to focus on those.

For now, post the complete and exact error that appears concerning the firmware-b43-installer. That may give a clue as to what needs to be done to purge it.

**EDIT**: also, I've moved the thread to Networking and Wireless. I can understand why you chose the Installation and Upgrade forum, but N&W is more appropriate and more likely to find you the help you need.

---

### Post by divyansh.sachdeva on 2011-09-11
Sorry for the hassle. I see your point.

After submitting an error report, after being prompted by the system, the error message on startup has vanished. 

The problem of connecting to Internet using wi-fi persists. On boot-up the hardware doesn't scan/show wireless connections despite their availability.

Right now there is no firmware-b43-installer or firmware-b43-lpphy-installer installed on the system. Apart from that I've blacklisted **brcm80211**.  


Can someone help me establish the connection from scratch? 

Help appreciated.

---

### Post by divyansh.sachdeva on 2011-09-11
The system generated error message related to firmware-b43-installer:

```

ProblemType: Package
DistroRelease: Ubuntu 11.04
Package: firmware-b43-installer (not installed)
ProcVersionSignature: Ubuntu 2.6.38-11.48-generic 2.6.38.8
Uname: Linux 2.6.38-11-generic i686
NonfreeKernelModules: wl
AptOrdering:
 firmware-b43-lpphy-installer: Remove
 firmware-b43-installer: Install
 firmware-b43-installer: Configure
Architecture: i386
Date: Sun Sep 11 16:24:43 2011
ErrorMessage: subprocess installed post-installation script returned error exit status 4
InstallationMedia: Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
SourcePackage: b43-fwcutter
Title: package firmware-b43-installer (not installed) failed to install/upgrade: subprocess installed post-installation script returned error exit status 4
UpgradeStatus: No upgrade log present (probably fresh install)

```

---

### Post by coffeecat on 2011-09-11
> **divyansh.sachdeva said:**
> Apart from that I've blacklisted **brcm80211**.  

I know that was suggested in the previous thread, but I'm not convinced that was a good idea. I have the bcm4313 wireless in a netbook and it works out of the box in Natty with the inbuilt brcm80211 driver. And I've recently helped someone install Natty on a different make netbook with the bcm4313 wireless, and that too worked out of the box.

I've got to go off-line for an hour or two now. When I get back I will read through your previous thread more closely and post back.

---

### Post by divyansh.sachdeva on 2011-09-11
Thanks. Really appreciate it. 

I understand that in some cases wireless connection doesn't give any trouble. Thing is I might've made some changes to my system unknowingly as I was trying various things to make the connection work. 

I'd appreciate it if you could check out my system's current configuration and then we might find a solution. Tell me the commands I need to execute to get the current status of the system.

---

### Post by coffeecat on 2011-09-11
OK, I've had a chance to read through your other thread. There were some side issues but the essence of it (if I read the thread correctly) is that:

1 - You had already installed the STA driver:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
Subsystem: Askey Computer Corp. Device [144f:7175]
Kernel driver in use: [COLOR="Red"]wl[/COLOR]
```

2 - You were not able to see wireless networks in Network Manager.

3 - When you blacklisted the brcm80211 driver, you were able to see wireless networks after the first reboot, but not after a second reboot.

Before we try to untangle all this, I suggest a simple experiment. Based on my experience of a HP netbook and a Samsung netbook, the bcm4313 card *should* just work out of the box with Natty. However, this is not necessarily so with your Toshiba, a make I have no experience of. Unfortunately, there can sometimes be all sorts of weird and wonderful conflicts between wireless drivers and hardware specifics. I remember a thread where (another) wireless chipset was disabled every time the OP used the screen brightness key combinations. I think that comes under the weird category. :)

Boot up with the live 11.04 CD or USB - whichever you used to install Ubuntu Natty. Choose "try Ubuntu" to get to the live desktop - you do not want the installer. Click on the network manager icon (near top right). Can you see any wireless networks? If you can see yours, can you connect to it? Don't worry about the issue you raised in the other thread about connecting to your ISP. There are two steps in the chain: connecting the modem-router to your ISP and connecting your computer wirelessly to the wireless router. Obviously you want to do both, but we need to see if you can connect the computer to the router wirelessly in the live session with the default brcm80211 driver.

Post back with what you find, and we'll take it from there.

---

### Post by wildmanne39 on 2011-09-11
Hi, please post the results of these commands:
```
rfkill list all
```
```
sudo lshw -C network 
```
```
iwconfig
```
```
lsmod
```
```
cat /etc/modprobe.d/blacklist.conf
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by coffeecat on 2011-09-11
> **wildmanne39 said:**
> Hi, please post the results of these commands:
```
cat /etc/modprobe.d/blacklist.conf
```

Hi there, wildmanne39. Good to see you joining in. I can help you with that one. If you look at the OP's previous thread (I've linked it in post #2) you'll see that they were asked to do this:

> Blacklist the following module:

```

echo "blacklist brcm80211" | sudo tee /etc/modprobe.d/blacklist-brcm80211.conf
```

Just for the record I've now had a chance to look in my Natty system installed in a machine with the same wireless chipset as the OP. It had previously run OK with the brcm80211 driver, but out of interest I installed the STA driver (which the OP had done) and the STA driver produced the file /etc/modprobe.d/blacklist-bcm43.conf which contains:

```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
```

Which means that the OP now has brcm80211 blacklisted twice over! And that's why I asked the OP to run 11.04 live to see how the brcm80211 driver behaves in a default system.

My blacklist.conf (which will almost certainly be the same as the OP's) only lists the bcm43xx out of the Broadcom set as blacklisted

---

### Post by wildmanne39 on 2011-09-11
Hi coffeecat, this is a card that I have only started to see recently and it has been problematic for me to get working, where as most broadcom cards are not. I appreciate all they help I can get.
Thank you

---

### Post by coffeecat on 2011-09-11
> **wildmanne39 said:**
> Hi coffeecat, this is a card that I have only started to see recently and it has been problematic for me to get working, where as most broadcom cards are not.

That's an interesting observation. As you can see from my earlier posts I've had hands-on experience with two machines with this card and it worked fine. However, like you I've seen threads where people with it are having problems. Perhaps I was just lucky with those two machines. I'll be intrigued to see what the OP reports from trying the live session.

---

### Post by divyansh.sachdeva on 2011-09-12
I booted up my system from the cd and ran a live session. During the live session I could see all the wireless networks available and could even connect to my wireless networks. 

Also, now the only problem that remains is of connecting to the wireless router without the live cd session. I've configured the router to connect to the internet automatically.

---

### Post by coffeecat on 2011-09-12
> **divyansh.sachdeva said:**
> I booted up my system from the cd and ran a live session. During the live session I could see all the wireless networks available and could even connect to my wireless networks. 

That is good news. It means that the bcm4313 card will work with the default brcm80211 driver. What you need to do is to get your permanent installation back to its default state with regard to the wireless. There are two things to consider. You had obviously installed the STA driver, but what I'm puzzled by is why you were having problems with it. On my HP netbook, the STA driver works just as well as, if not slightly better than, the default brcm80211 driver. Did you install the bcmwl-kernel-source package with Software Centre or Synaptic or did you use the Additional Drivers Utility? Or did you install it some other way?

The other thing which might be a problem is the attempt to install firmware-b43-installer. I'm not clear whether that has sorted itself out, or whether your package manager is in an inconsistent state and needs fixing, but you'll soon find out.

This is what I suggest you do:

1 - Open the Additional Drivers utility and see if it is telling you that the STA driver is enabled. If so, disable it and reboot. It's unlikely that the wireless card will be working yet because there are one or two steps to go through. If Additional Drivers was not telling you anything coherent, open Synaptic, search for bcmwl-kernel-source, mark for complete removal and "apply". Reboot. If Synaptic is telling you that bcml-kernel-source is not already installed (and Additional Drivers wasn't helping) stop there and post back with the answers to my questions above.

2 - If you've got this far, you need to check some of the files in /etc/modprobe.d to make sure brcm80211 is not still blacklisted. In the commands that follow you will be opening system files in a text editor with root privileges. Take care! Open a terminal, and:

```
gksudo gedit /etc/modprobe.d/blacklist-bcm43.conf 
```

If a blank file opens, simply close it without saving anything. If the file contains this line:

```
blacklist brcm80211
```

"Comment" it so that it looks like this:

```
#blacklist brcm80211
```

Save and close it. If the "blacklist brcm80211" line is not present, simply close the file. Now:

```
gksudo gedit /etc/modprobe.d/blacklist-brcm80211.conf
```

This is the file you were recommended to create in your previous thread. That will probably contain a single line "blacklist brcm80211". If so, simply comment it as before with a # at the beginning of the line, save the file and close it.

Lastly, it would be a good idea to check all the other files in /etc/modprobe.d to make sure none of them have the line "blacklist brcm80211". Browse to /etc/modprobe.d in a nautilus file browser window and double-click on each to open it in a read-only text editor window. Check that there are no "blacklist brcm80211" lines.

Now, in a terminal:

```
sudo modprobe brcm80211
```

Does the wireless now work? Whether it does or not, reboot. Don't do the modprobe command, but check the wireless. Does it work?

Lastly, let's see if the package manager is inconsistent. From a terminal:

```
sudo apt-get update
```

You will get output, but are there any errors?

---

### Post by divyansh.sachdeva on 2011-09-12
I opened my additional drivers and disabled the STA drivers. Secondly, I got  bcmwl-kernel-source package from the terminal window and also used the Synaptics. I've now removed this package using Synaptics(marked for complete removal). Finally, I commented the blacklisted brcm80211. 
Reeboot... And, whoa... The wireless is up and running!!!

Thanks a ton people!!! Special thanks to coffeecat. 

One last thing... Ubuntu is showing that I have some updates available. Should I update them or not? I'm kindda worried that I'll mess up my wireless again. Please suggest.

---

### Post by coffeecat on 2011-09-12
That's very good news, but does the wireless survive a second reboot? :)

I've updated my Natty system on the machine with the same wireless chipset - so far without problems. I'll keep my fingers crossed for you!

Good luck!

---

### Post by divyansh.sachdeva on 2011-09-12
So far it does!!!

Please advice about the updates!

---

### Post by coffeecat on 2011-09-12
> **divyansh.sachdeva said:**
> So far it does!!!

Please advice about the updates!

I'm 99.9% confident they'll be fine. However, if you're prepared to wait a little, I'll update one of my Natty systems on the HP netbook. I have two Natty systems there - one on its own partition using the STA driver and a wubi installation using the brcm80211 driver that you are now using. (Long story - don't ask! :p)

It's about time I updated the wubi one. I shall do so forthwith and let you know.

---

### Post by divyansh.sachdeva on 2011-09-12
Thanks a lot! But I think I'll take my chances! Whats life without a little risk! 
And thanks for all the help. Really appreciate it.
God Bless!

---

### Post by coffeecat on 2011-09-12
My system - and wireless - has survived an update and reboot. 

Good luck!

---

### Post by wildmanne39 on 2011-09-12
Hi coffecat, I see you got it working before I was able to get back.

I suspected that card would work with the livecd but I could not be sure of that.

In natty a lot of the broadcom cards do not work right away with the sta driver, they usually work easily with the b43 but not all so sometimes it take a little experimenting.

---

