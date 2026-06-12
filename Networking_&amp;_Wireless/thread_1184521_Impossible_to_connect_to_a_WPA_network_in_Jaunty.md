---
title: "Impossible to connect to a WPA network in Jaunty"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by Prium on 2009-06-11
Intrepid's wireless worked perfectly for me once I started using ndiswrapper. But in Jaunty, although it detects the available networks it simply will not connect. 

The network itself is working fine. It uses WPA encryption. A second PC running EasyPeasy (based on 8.04) manages to access it just fine via the network manager. 

I have tried using WICD. Aside from being awkward to use, it offered no advantages in terms of connectivity to my WPA network over the GNOME network manager. I also tried denying the keyring access to the WPA password (from a thread i read) but this did not allow the network manager to access my wireless network . 

I just wanted to ask if there is anything else I can try before deleting Jaunty and reinstalling Intrepid (as much as a headache as that will be). I'm not entirely convinced it is a driver issue as such - but I'm open to any suggestions. Cheers

---

### Post by idef1x on 2009-06-11
I would try to use the Network Manager itself from gnome.
What wireless card do you have? Does your system detect any wireless by itself (do you have a wlan0 interface or so?). Also check your /var/log/syslog and or /var/log/messages.
In mine it showed that i had to download a newer firmware for my card. After that is does work for me, so maybe also for you. I can't imagine that once working in intrepid (even via ndiswrapper) it wouldn't work anymore in jaunty...

---

### Post by Prium on 2009-06-11
Hmmm....what you say gives me hope. I was under the impression that Jaunty had a strange issue with wireless. 

Aside from this morning, I always run the network manager from GNOME. Unless I uncheck the wireless connection box, it will always show the available wireless and wired connections. 

The card is a Broadcom BCM4318 AirforceOne 54g. In 8.04 and 8.10 I had two options for getting it to work. One was to use a bcm4318-fwcutter tool (I had help with this), and the other was to use the windows driver with ndiswrapper. I found the latter to be the better option because with fwcutter I had to use an older driver, and so every time I ran system updates I got pestered to use a newer, albeit incompatible, driver version.

---

### Post by idef1x on 2009-06-11
Then it should work, cause i had to use the same tool for it! In my syslog i got the message to go to :
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) to download the latest.
Since you've a recent release of ubuntu, all you need to do (see the mentioned link) is to :

> 
in latest versions of Ubuntu (all flavors) and Debian just need to install the b43-fwcutter package: **sudo apt-get install b43-fwcutter** 
when you are asked "Fetch and install firmware?" answer "Yes" (just press "Enter) 


this installs AND uses the tool for you. Worked (and still does ;) )great with my wireless card!

---

### Post by Prium on 2009-06-12
thanks. i used 'sudo apt-get install b43-fwcutter' but it did not prompt for "fetch and install firmware". 

i guess this may still be present from 8.10 (because i updated to 9.04 rather than reinstalled)? in this case how can delete all the existing wireless drivers and start again?

---

### Post by idef1x on 2009-06-12
Hmmm strange...
You might try to uninstall it again with the --purge option, so :
sudo apt-get remove --purge **b43-fwcutter** and then remove the wireless drivers from /lib/firmware (make a backup first!) and then reinstall the b43-fwcutter again. Maybe it thinks the drivers are allready there[B].
[/B]Otherwise you have to do it manually I am afraid. Also after installing the drivers, reboot the machine so the wireless adapter will try to reinitialise (I have a PCMCIA adapter, so i just unplugged it and reinserted it for the same effect). If not working, taking a look in the /var/log/syslog (or /var/log/messages) might give a clue.

---

### Post by Prium on 2009-06-12
OK. That did actually get fwcutter to prompt for "fetch and install firmware". So now I guess it must be using the latest BCM4318 driver because now there is no wireless in network manager :(

I have seen this before. Ubuntu assumes I need the latest driver. But the one I need is an older version. A colleague from work figured this out and got it working for me. I'm struggling a bit to retrace his steps though....

---

### Post by idef1x on 2009-06-12
YOu need an older driver? Mostly you would say the newer the better ;)
Anyway there isn't something in your logfiles mentioning what it needs?

---

### Post by Prium on 2009-06-13
Jaunty is now gone. Intrepid takes its place. Wireless works perfectly using ndiswrapper and the current bcm4318 driver for XP. Hooray! And lesson learned: newer is not always better ;)

I appreciate your suggestions idef1x. Cheers

---

