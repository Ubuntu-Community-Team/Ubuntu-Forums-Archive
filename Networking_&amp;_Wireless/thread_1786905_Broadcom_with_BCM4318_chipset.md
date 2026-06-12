---
title: "Broadcom with BCM4318 chipset"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by SeePU on 2011-06-20
Does ANYONE know how to configure a laptop that has this wifi chipset?!?

Laptop:
Acer Aspire 5002WLMi

wifi chipet:  BCM4318

ID:
$ lspci -nn | grep 14e4
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

Also, I don't want outdated instructions... there is something going on, imho, and this driver is no longer working... it looks like

This is the main page I'm using:

[http://wiki.debian.org/bcm43xx](http://wiki.debian.org/bcm43xx)

But, if you know of some method or some step that isn't being done and recognize it, please explain! 

I don't know what else to try and I guess I'm getting close to giving up and using that POS laptop as a Windoze machine... 

I've tried Ubuntu, Xubuntu, Lubuntu and variations of Debian flavors.  

The same laptop's wireless works in Windows XP.  

I'm typing this on another laptop in Linux but the wifi card in that machine is an Intel ipw2200 so the wifi card works in the Acer and my wireless configuration seems to be set up correctly.

Anyone have any idea of what to try now?  It would be nice to get this laptop working.   Regardless, I'll NEVER buy anything with a Broadcom card in it!!! 

Can anyone help????!? :(

---

### Post by riggzy01 on 2011-06-20
Yes, just go to synaptic package manager, type in b43 in search box, install "b43 installer" and "b43 firmware." You have to do all this while on ethernet.  You should then be good to go.

---

### Post by riggzy01 on 2011-06-20
That's for Ubuntu btw.

---

### Post by SeePU on 2011-06-20
> **riggzy01 said:**
> Yes, just go to synaptic package manager, type in b43 in search box, install "b43 installer" and "b43 firmware." You have to do all this while on ethernet.  You should then be good to go.I've done that and lost count how many times I've tried this.

It's good when my usb stick works for trying distros or I would have created a lot of Live CDs/DVDs by now.

the b43-cutter package (whatever it's called) is already installed so I have to install the b43-installer.  I assume the b43 cutter package is now open and the installer is closed (proprietary).

But, after that is done, my wifi hardware is still not working and I can't scan networks (no wireless networks found is the message in wicd).

---

### Post by riggzy01 on 2011-06-20
Sorry about that, I've spent my fair share of time installing and uninstalling those as well.  Hmmm...you should try "$ sudo lshw -C network"  this will show if the wireless card is soft blocked or hard blocked if you haven't already.

---

### Post by SeePU on 2011-06-20
$ modprobe b43
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ubuntu@ubuntu:~$ 


What does that indicate?   My hardware isn't detected?!?  OR the firmware is not installed or what?

Dmesg shows:
the firmware not found but that's before I installed it?

---

### Post by riggzy01 on 2011-06-20
Try "wlan0 up"

---

### Post by riggzy01 on 2011-06-20
I take that back, this means your wireless card is not yet configured. 

This seems to show you how to install firmware for this card:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by SeePU on 2011-06-20
> **riggzy01 said:**
> I take that back, this means your wireless card is not yet configured. 

This seems to show you how to install firmware for this card:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Interesting page but those instructions are useless.

> Step 2.

Under the desktop menu System > Administration > Hardware/Additional Drivers, the b43 drivers can be activated for use.

Note: A computer restart may be required before using the wifi card.Is that author KIDDING?!?   I've never NEVER NEVER EVER read of instructions to choose 'Additional Drivers' for this b43 driver install.   Is this new for Natty 11.04?   Anyway, when I try, I am not disappointed... nothing is shown!  Lucky me!

"No proprietary drivers are in use on this system...."

It's good Mr. 'Antonio' really checked and tested his instructions out or I wouldn't be able to laugh and cry at another set of instructions not working! :-(

---

### Post by riggzy01 on 2011-06-20
This seems like it will take a little bit more work but it worked for the other posters so... 

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/) 

Let me know if it helps!

---

### Post by SeePU on 2011-06-20
> **riggzy01 said:**
> This seems like it will take a little bit more work but it worked for the other posters so... 

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/) 

Let me know if it helps!Well, that looks like a very old 'solution' but first, I am going to try an actual install and the other idea I had is that the 'wl' "stuff" is causing a problem/conflict?

So, in that effect, the blacklisting of the 'wl' is interesting but I'm hoping having the OS actually installed will help.  Probably not but then I can at least note what is working (nothing so far) and what doesn't.

I'm trying Lubuntu 11.04 first.

I'll look at the other 'solutions' after if this (likely) doesn't help.

---

### Post by SeePU on 2011-06-20
Update:  installing doesn't help.   I could have kept using the Live ver. via the usb stick.

However, I have something showing now for dmesg regarding the firmware.   Hopefully, someone can decipher and maybe suggest an idea from it?

```
$ dmesg | grep b43
[    1.959375] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.565358] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   21.658242] Registered led device: b43-phy0::tx
[   21.658271] Registered led device: b43-phy0::rx
[   21.658303] Registered led device: b43-phy0::radio
[   22.444039] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   22.520209] b43-phy0: Radio hardware status changed to DISABLED
```

---

### Post by bkratz on 2011-06-20
How about the output of 

rfkill list

There may not be an output if this is not loaded.  You can always get it with

sudo apt-get install rfkill

rfkill will show if anything is hard or soft blocked

---

### Post by walt.smith1960 on 2011-06-20
Excuse me if you've already done this but if you're using Network Manager, when you left-click the icon are the two boxes "Enable Networking" and "Enable Wireless" checked?  These seem to get spontaneously unchecked.  Ask me how I know #-o.

---

### Post by nm_geo on 2011-06-20
> **SeePU said:**
> Well, that looks like a very old 'solution' but first, I am going to try an actual install and the other idea I had is that the 'wl' "stuff" is causing a problem/conflict?

So, in that effect, the blacklisting of the 'wl' is interesting but I'm hoping having the OS actually installed will help.  Probably not but then I can at least note what is working (nothing so far) and what doesn't.

I'm trying Lubuntu 11.04 first.

I'll look at the other 'solutions' after if this (likely) doesn't help.

You may just be on to something with the "wl" stuff causing a problem/conflict.

When you figure out the driver and modules in Lubuntu are the same maybe you will want to try to see why your wireless tries and then gets disabled.

May i suggest you do the rfkill list all that was pointed out ..
and if you want to see if the b43 or ssb module are blacklisted by the old 'wl' install run this too.

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl
```'

That line of code will tell you if any of the above are listed in your blacklist files

---

### Post by josephmills on 2011-06-20
could we also see a ```
rfkill list all 
``` thanks

---

### Post by zander1013 on 2011-06-20
hi,

i had similar frustration myself.

the correct solution was given on a link my last post in the sticky thread about the broadcom problem above...


[http://ubuntuforums.org/showthread.php?p=10962081#post10962081](http://ubuntuforums.org/showthread.php?p=10962081#post10962081)


the problem is that b43xx has been blacklisted. the solution on the link in the thread i have given describes how to remove it from the blacklist.

my speculation is the blacklisting of the b43xx stuff is why none of the original solutions given in that sticky thread are working for peeps using newer .iso images for install.

---

### Post by nm_geo on 2011-06-20
> **zander1013 said:**
> hi,

i had similar frustration myself.

the correct solution was given on a link my last post in the sticky thread about the broadcom problem above...


[http://ubuntuforums.org/showthread.php?p=10962081#post10962081](http://ubuntuforums.org/showthread.php?p=10962081#post10962081)


the problem is that b43xx has been blacklisted. the solution on the link in the thread i have given describes how to remove it from the blacklist.

my speculation is the blacklisting of the b43xx stuff is why none of the original solutions given in that sticky thread are working for peeps using newer .iso images for install.
  I am very familiar with that link and process  :lolflag:

---

### Post by zander1013 on 2011-06-20
hhh!!

just make sure your not confusing it with the broken one i posted by mistake here is the one that works..
[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

:P

EDIT: i can tell your not confused. my bad.

---

### Post by SeePU on 2011-06-20
> **zander1013 said:**
> hi,

i had similar frustration myself.

the correct solution was given on a link my last post in the sticky thread about the broadcom problem above...


[http://ubuntuforums.org/showthread.php?p=10962081#post10962081](http://ubuntuforums.org/showthread.php?p=10962081#post10962081)


the problem is that b43xx has been blacklisted. the solution on the link in the thread i have given describes how to remove it from the blacklist.

my speculation is the blacklisting of the b43xx stuff is why none of the original solutions given in that sticky thread are working for peeps using newer .iso images for install.

I replied already in that other thread!  But, I want to thank you and the rest for replying to the thread and trying to help me!

I really appreciate it!!!! ;)

My wifi card is currently working (knock on wood) but I don't know for how long it will be.  ;-)   At least, now, I have a few things to try.

I will be saving this thread and that other one plus bookmarking that web page with the instructions for the solution.  

However, I didn't use any of those steps.  As I mentioned in that thread, my wireless worked seemingly after a reboot.  But, I booted up my XP Pro partition and wireless worked when XP Pro fully booted up.  I 'restarted the computer' and then booted up into Lubuntu.  I wasn't expecting anything (just confirming that the wifi card actually worked - was going crazy with all sorts of tests and various steps to no avail) but when Lubuntu booted up, wireless was enabled.  I just chose my wifi connection and entered the info (password etc.) as the scanning worked.  

I don't know if this is just a coincidence but I have no explanation for it.  I didn't edit any blacklist file.     NOTE:  I don't consider my wireless currently working as solved.  I am assuming it's only temporary since there was no apparent 'solution' done.  

Any theories?  I'm at a loss but it was very peculiar.  I would not be surprised if the wireless stops working later on sometime but at least I have your ideas and possible solutions to try out.  

Thanks again!  

At any rate, I feel as that the Broadcom drivers are very poorly written.  I guess that is insulting to the Broadcom developers but sorry, 'can't help thinking that.

---

