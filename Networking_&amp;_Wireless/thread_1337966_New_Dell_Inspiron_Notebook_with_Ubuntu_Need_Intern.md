---
title: "New Dell Inspiron Notebook with Ubuntu: Need Internet!"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by justyellowboy on 2009-11-25
So, my dad bought me that new Dell Inspiron 15 laptop with Windows 7. Inside is a wireless minicard that Windows did a great job of setting internet connection with. The very first thing I did with this fabulous computer was exclaim, "OH GEE, MAYBE I'LL GO PUT ANOTHER OPERATING SYSTEM ON IT!" and with the naitivity of a teenager's impulse, placed a plump, 15-GB, 64-bit Ubuntu on Dual-Boot with GRUB (that right there has me worried; shouldn't wubi make a *back-up* of the old loader, since people might switch back?)
 
I want to make the relationship work. I've set up a connection with all of the details from the Windows connection I could provide for Ubuntu, including SSID, MAC, and I should report that you can't type in the % sign when configuring IPv6, so that was a no-go. However, I don't think there is a real connection *to* this minicard. You must forgive me, I don't understand the processes behind wireless networking. What I mean is that I'm providing the details but the OS hasn't recognized the Wireless driver.
 
My question then is "**How do I get Ubuntu to use my Wireless WLAN Utility and the drive**?" The Utility, for one thing, would probably have to be made in support of Linux distros, since just copying the Windows program folder to Ubuntu via flash drive like an idiot didn't work out (lol). I crossed my fingers and tried to compare it to the list of supported drivers, but I could determine how to exactly check (in other words, **how do I know if my driver is supported?**)
 
It's probably likely that even if the driver were supported, the possibly unsupported utility would render the laptop's connectivity unexecutable (get it? A little play on words about putting Windows EXEs on Ubuntu desktops? Nevermind). If anybody is out there with their knives sharpened for some classic au contraire, please serve me on a platter (in other words, add 2 cents, please!)
 
Thanks in advance to all of you! I understand how hard you folks work on this and these new questions don't get much more complicated than simple variants.) I desire to be a Computer Science major, and the educational software on here has me excited.

---

### Post by Nburnes on 2009-11-25
You have hooked it up through LAN and downloaded all the updates correct? Then checked to see if Ubuntu has hardware drivers for it?

---

### Post by Mahngiel on 2009-11-25
Alot of connectivity issues arise when enabling wifi cards due to proprietary drivers.  First thing you'll need to do is figure out which card you have:  

Open the command line terminal and type:

```
lspci

```Towards the end, you'll find something like "Network Controller" etc.

Hit up:
```
lspci -nn | grep 'insert network controller name here'
```From there you will know what kind of card you have and can find out what to do from there by looking at the stickied thread [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by JBAlaska on 2009-11-26
Although Dell is not very forthcoming in posting which chipset is in this lappy, I have determined that it is a broadcom one.

1- Go to System, administration, software sources. and check the "installable from CD-ROM/DVD checkbox, insert the LiveCD, close the software sources window.

2- Run this in a terminal:
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
3- Reboot
4- Go to System, administration, hardware drivers and enable the "Broadcom STA wireless driver.
5- left click on network manager icon on the upper left of your panel and choose your wireless network.
6- enter your wifi password and encryption type (WEP or hopefully WPA personal)

---

### Post by justyellowboy on 2009-11-26
This got me the right result. I'm happy to say that I'm mostly (hopefully completely) compatible with Ubuntu! <333 Thanks, Mahngiel!
 
JBAlaska called it quite nicely tonight. Hopefully I have such a CD, can fix the problem in the morning, and you can have my cookie of the day.

---

### Post by justyellowboy on 2009-11-26
I dearly apologize for the double-post. I wanted to give an update here that has me perplexed, but with a theory. I don't have a CD for the Wifi, which means that it came pre-installed. I have read other Ubu discussions about how OS recovery discs are actually built into the machine, based on that, I thought "maybe that applies for the utility," so I'm thinking about how I can use Windows to "install" an Ubuntutized version of the Utility to place into Ubuntu? This definitely sounds like hard work that I'm not familiar with.
 
Gosh, if only I knew how to code up a separate utility and stop dealing with this mess! : D
 
I also have a friend that is suggesting some code to me, but it's on the tip of his tongue. He's suggested
```
sudo service networking restart
```
and
```
sudo -s
service networking restart
```
while I attempted an extra sudo on the second line of that last one, as well. All three variations have resulted in returning "Unknown Instance." I'm not sure what this means. Can someone explain what it means, and possibly infer what line(s) of code he's hinting at?
 
Thanks for all your help, guys. :3 You're doing awesome!

---

### Post by justyellowboy on 2009-11-26
STOP STOP STOP STOP!!!

I just found another discussion that is on the *exact* same page as me, posted on the same day. Please close this topic while I transfer my little theory over there. C:

---

