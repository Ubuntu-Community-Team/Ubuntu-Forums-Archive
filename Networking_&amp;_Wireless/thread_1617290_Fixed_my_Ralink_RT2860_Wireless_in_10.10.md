---
title: "Fixed my Ralink RT2860 Wireless in 10.10"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by TBABill on 2010-11-09
I searched the forums for answers and finally came across the fix for my wireless. It works perfectly in 10.04 and cannot connect to a network in 10.10. The card is a Ralink RT2860 and normally works out of the box with any distro, but here's what I found on the forums that fixed mine (so others can search and find an answer easily):
 
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
 
Add the following lines to the end of blacklist.conf:
> blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb


---

### Post by uhappo on 2010-11-10
I have
```
03:00.0 Network controller: RaLink RT2860
```wireless card and it worked flawlessly on 10.04.

Your tip worked, thanks alot!

---

### Post by TBABill on 2010-11-10
Very welcome. Glad it has helped save someone else some trouble. Enjoy!

---

### Post by castor_fou on 2010-11-13
indeed it works but here it failed to resume after suspend.
In log file I have something as(wlan0): link timed out.

---

### Post by not_a_phd on 2010-11-13
Tip works fine for me (eeePc 901) on a WPA network, but not a WEP encrypted network. I am presently running a kludged system where I blacklist the rt2860sta driver by default (for my WEP network). When I am at a WPA hotspot, I rmmod the generic rt2800 and rt2x00 drivers, and insert the rt2860sta one, which works well except for suspend. 

When I add the SUSPEND_MODULE=rt2860sta to my /etc/pm/config.d/config file, my system hangs upon wake up.

All is not well in wireless Ubuntuland.

---

### Post by frenkel on 2010-11-13
When I blacklist the modules listed in by the TS and reboot, my suspend works just fine (make sure the other modules where not loaded before).

---

### Post by not_a_phd on 2010-11-13
> **frenkel said:**
> When I blacklist the modules listed in by the TS and reboot, my suspend works just fine (make sure the other modules where not loaded before).

Dude, suspend is the least of my worries. I am quite aware of which modules are loaded, and which are not. The problem that I am having is that no single module configurations works on both types of networks to which I connect - WPA Open and WEP. 

I have gone so far as to compile RaLink drivers, but they do not play with network-manager. 

So, I continue to operate with a kludged system. I stand by my statement that all is not well in wireless Ubuntu-land. 

If anyone out there in ubuntu-land is successfully operating an eeepc 901 with the RaLink 2860 driver on Maverick, I would ***love*** to hear how they are doing it.

---

### Post by frenkel on 2010-11-14
> **not_a_phd said:**
> Dude, suspend is the least of my worries. I am quite aware of which modules are loaded, and which are not. The problem that I am having is that no single module configurations works on both types of networks to which I connect - WPA Open and WEP. 

I have gone so far as to compile RaLink drivers, but they do not play with network-manager. 

So, I continue to operate with a kludged system. I stand by my statement that all is not well in wireless Ubuntu-land. 

If anyone out there in ubuntu-land is successfully operating an eeepc 901 with the RaLink 2860 driver on Maverick, I would ***love*** to hear how they are doing it.

Well I'm sorry, but I was under the impression you where complaining mostly about the fact that your machine would hang after resume.
Did everything work fine in 10.04? For me it did, so you might want to try and compile that staging driver if that's possible.

---

### Post by castor_fou on 2010-11-14
I made some progress and now everything work fine: wep or wpa, toggling off/on wifi, suspend/resume.
What I did since previous post was just a BIOS update to the last version available (from ASUS website). I followed some blog post at [http://blog.lmartin.fr/dc2/index.php/post/2008/09/22/Mise-a-jour-du-BIOS-EeePC-via-une-cle-USB](http://blog.lmartin.fr/dc2/index.php/post/2008/09/22/Mise-a-jour-du-BIOS-EeePC-via-une-cle-USB), this is in French but can be translated via Google translate.

---

### Post by not_a_phd on 2010-11-14
> **frenkel said:**
> Well I'm sorry, but I was under the impression you where complaining mostly about the fact that your machine would hang after resume.
Did everything work fine in 10.04? For me it did, so you might want to try and compile that staging driver if that's possible.

No need to be sorry - you were trying to help, and I ***greatly*** appreciate it. I fear that my frustration is shining through right now.... 

I had been running 9.10 Karmic, and felt it time to upgrade before it expired. Everything "just worked" under Karmic, and I did not do the necessary homework beyond trying out the live USB version (which also worked). While things worked just fine in the "try it out on USB" mode, they did not after reboot into the newly installed system. 

If I had done my homework, I would have found that Ubuntu had broken wireless on the eeepc 901 in 10.04, and had not yet fixed it in 10.10. 

I have been actively working this problem for the past 3-weeks now, with little progress to show for it. I have compiled and installed vendor staging-drivers on my machine, but was worse off for it. In that case, my wpa_supplicant would disconnect me every 5-seconds on my WEP network. I have traced source code to see where this is happening in the code, but ran into a dead end in the debug process because of the way wpa_supplicant initialization arguments are hard-coded into the network manager.   

I have recently begun looking at ways of taking network-manager out of the loop and seeing if I can do better by reverting to manual configuration. I don't think I can do worse....

---

### Post by not_a_phd on 2010-11-14
> **castor_fou said:**
> I made some progress and now everything work fine: wep or wpa, toggling off/on wifi, suspend/resume.
What I did since previous post was just a BIOS update to the last version available (from ASUS website). I followed some blog post at [http://blog.lmartin.fr/dc2/index.php/post/2008/09/22/Mise-a-jour-du-BIOS-EeePC-via-une-cle-USB](http://blog.lmartin.fr/dc2/index.php/post/2008/09/22/Mise-a-jour-du-BIOS-EeePC-via-une-cle-USB), this is in French but can be translated via Google translate.

This seemed to be the best advice I have seen in 3+ weeks of scrubbing through the forums on this topic. The latest BIOS on the referenced page was BIOS-1703. I see that asus is up to BIOS-2103 for the eeePC901 on another site.

I notice significant wifi improvement upon installation of BIOS-1703. Things are not perfect. But, they are better. Once I get a connection for more than 5-minutes, it stays stable and survives a suspend. However, it takes several association attempts to get a stable connection. Most times, I have to help it along with a command line entry of my ssid and wep key using the iwconfig command. 

Which bios did you install? I am almost afraid to try a newer one, but I am willing to do so if it will help...

---

### Post by castor_fou on 2010-11-15
> **not_a_phd said:**
> 
Which bios did you install? I am almost afraid to try a newer one, but I am willing to do so if it will help...

I have installed the very last version 2103. And because this is reversible, it is not that frightening. I have a 901/XP flavour of eeepc. 

After 2 days, I experience some issues when resuming after suspend (One time on 5 I would say). And doing Fn-F2, Fn-F2 (Fn-F2 is the command to desactivate/activate wifi) solves it. Not perfect world but still easier than to reboot ;)

---

### Post by not_a_phd on 2010-11-15
> **castor_fou said:**
> I have installed the very last version 2103. And because this is reversible, it is not that frightening. I have a 901/XP flavour of eeepc. 

After 2 days, I experience some issues when resuming after suspend (One time on 5 I would say). And doing Fn-F2, Fn-F2 (Fn-F2 is the command to desactivate/activate wifi) solves it. Not perfect world but still easier than to reboot ;)

I will give 2103 a try then. Do you know if there are hardware differences between the the 901/XP and the 901/Linux?

---

### Post by castor_fou on 2010-11-16
> **not_a_phd said:**
> Do you know if there are hardware differences between the the 901/XP and the 901/Linux?

except for ssd hard drives capacity (from memory 20 Gb for linux, 12+4 Gb for windows but faster ones) I don't know.

---

### Post by azdavef on 2010-11-18
My pci card with this chipset works occassionally with network manager and all the time with wicd.  Worked fine with network manager since Hoary.  I used wicd with Feisty and Gutsy, and I am back with it.  I don't tug on Superman's cape, either.

---

### Post by not_a_phd on 2010-11-18
> **azdavef said:**
> My pci card with this chipset works occassionally with network manager and all the time with wicd.  Worked fine with network manager since Hoary.  I used wicd with Feisty and Gutsy, and I am back with it.  I don't tug on Superman's cape, either.

Any recommendations on a good tutorial on how to uninstall network manager, and install wicd? I had a rough time of it when I attempted this before.

---

### Post by pdc on 2010-11-19
:p [http://lmgtfy.com/?q=tutorial+remove+network-manager+install+wicd](http://lmgtfy.com/?q=tutorial+remove+network-manager+install+wicd) :p

---

### Post by not_a_phd on 2010-11-20
> **pdc said:**
> :p [http://lmgtfy.com/?q=tutorial+remove+network-manager+install+wicd](http://lmgtfy.com/?q=tutorial+remove+network-manager+install+wicd) :p


Ouch. That was harsh dude! =] (Though, I certainly appreciate the {good natured?} humor.)

In seriousness, perhaps I should have been a bit more specific. Can anyone reading these posts point me toward a tried and true tutorial for stripping network manager and adding wicd that they personnally know will work. The last time I attempted this, while following a tutorial that I found via Google, I ended up with a system where network-manager was still *partially* installed alongside wicd, and when I attempted to uninstall wicd, I was left with an unusable system that I had to reinstall from scratch.

---

### Post by azdavef on 2010-11-20
I have switched back and forth between them so often that I just do it.  I really prefer to use network manager because it is integrated into Ubuntu more than wicd.  I just can't do without a peaceful wireless connection.  Bluetooth works better with network manager and wicd doesn't do vpn (at least I haven't been able to figure it out).  I don't really need either so it's no big deal to me.  The past has taught me that network manager will work at some point.  This chipset is popular and current.  My pci card is dual band b/g/n and it really rocks on that other OS we don't talk about.  Briefly, you need a working internet connection to install wicd.  There are four packages to install with the Package Manager.  wicd, wicd-daemon, python-wicd, and wicd-gtk.  Apply and when you restart, both network manager and wicd should be running and you should have a "new" icon in your panel.  Left click on the new icon and check to see if wicd can see your router.  You should be able to click on the Properties of your router and the setup is pretty self explanatory.  Go back to the Package Manager and in the search box enter network-manager.  I don't remember exactly which ones were installed, but I do remember that there were 4 of them.  Mark them for removal and apply.  When you restart, network-manager should be gone.  You may need to enter the Properties of the router you need to connect again as above.  And, by the way, there are no sure things (solutions) in the Ubuntu community.  Just a lot of people trying to help by telling you what worked for them (as you probably already know).  I can heartily advise to put your home directory on a separate partition whenever you get a chance to do it.  It makes fresh installs real easy, especially if you backup regularly (Back In Time is awesome). Good Luck...

---

### Post by rhy7s on 2010-11-22
> **castor_fou said:**
>  And doing Fn-F2, Fn-F2 (Fn-F2 is the command to desactivate/activate wifi) solves it. Not perfect world but still easier than to reboot ;)
That's what I've been doing as well, the drop in the first place is still quite disruptive though.

---

### Post by introspectif on 2010-11-30
Thanks, this solved the problem I was facing. 

For the benefit of those who might be facing the same problem, it was not that I could not connect to my wireless network, but that it was extremely unstable and would alternate between connected and disconnected. Of course, this was completely unacceptable. I suppose something's wrong with those modules running together.

---

### Post by Luca79 on 2010-12-29
Hallo everybody, I am a new forum user. I have a problem with Ralink RT2860 on Ubuntu 10.10 64 bit. The PC is HP-020it. The OS recognize the wifi card and find the wifi network, ask me for network password over and over but never get connected. Does anybody have advice?

Thx a lot in advance.

---

### Post by Ethyrdude on 2011-04-02
I'd like to thank TBABill for his initial post for this fix, it worked great for fixing my router connection problem, I had a connection already with Ubuntu 10.10 32 bit but I decided to go to the 64 bit version and this was such an easy fix to implement.  I did do a reboot after and as soon as I logged back in I had and instant connection.

My problem was the same as what most of you mentioned, I could see the card, my computer recognized it, I could see the various networks but I just couldn't connect to any network and it kept asking over and over for my wpa2 password even tho I had provided it.  By adding those 5 lines to the blacklist, I got it up and connected, yay!!

---

### Post by asavage on 2011-10-14
If you have done this when you upgrade to 11.10 your wireless might not work (or at least mine didn't).  Commenting out the lines added to /etc/modprobe.d/blacklist.conf will fix it.

---

