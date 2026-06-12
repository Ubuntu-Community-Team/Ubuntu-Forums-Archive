---
title: "WUSB54Gv4 troubleshooting"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by plefno on 2006-06-06
I upgraded to Dapper a few days ago and was surprised to see that Ubuntu actually recognized my new Linksys WUSB54G v.4 wireless usb adapter.  It's listed in the Network Settings as rausb0 but it's not activated.  If I try to configure it and connect to a network, my computer completely freezes up.  

I read somewhere that it may have to do with the particular driver that Ubuntu is trying to use.  How can I get Ubuntu to load a different driver.  I tried to use ndiswrapper, but I'm not sure if that will really work if I don't stop Ubuntu from trying to load the first driver.  I'm pretty new to Linux so I'm totally clueless about this.

I've read tons of posts in these forums as well as other places, but I haven't made any progress.  I think if I could just get Ubuntu not to use whatever driver it's trying to use by default, I could get ndiswrapper to get my adapter working correctly.  Any thoughts anyone?  Thanks.

---

### Post by e-lizza on 2006-06-06
Hi plefno,

You are right. There is a big problem with WUSB54Gv4.

You can read my post [here]("http://www.ubuntuforums.org/showthread.php?t=188573"), where I try to log my experience and where I am now.

After few days, I've spent in researching, I don't think that the problem is with driver. Finally, I managed my card to detect all (open, wep and wpa) wireless networks. Now the problem is that I cannot connect to any wireless network.

I did not reinstall driver. Driver for RT2500USB chipset is already included and it works.

I didn't have any success with ndiswrapper. 

Finally, I think that the problem is that data is encrypted twice - 1) by sw and 2) by the card. 

I've read post about ipw and how to turn it off for ipw. I tried to do it for rt2500usb but again this approach is not applicable - the most probably, rt2500usb and ipw have different command sets.

-- I would suggest - don't use network-admin, use network-manager + wpasupplicant. 
-- ndiswrapper doesn't work
-- I called linksys for support (there is a chat entry on their web site) and they rejected to support linux - crazzzy.

I would appreciate any ideas.

Regards,
Liz

---

### Post by plefno on 2006-06-06
Well after hours of spinning my wheels, I finally made some progress a few minutes ago.  After doing some searching, I found out how to blacklist driver modules.  Then I had to figure out what the driver module that Ubuntu was autoloading was called.  In my case it was the rt2570. So I blacklisted the rt2570 in /etc/modprobe.d/blacklist .  

When I rebooted Ubuntu, I was happy to see that my wireless adaptor didn't appear in the Network Settings.  So I loaded a driver with ndiswrapper and was able to connect to my access point!! Yay!  I couldn't get WEP to work, but I'm just going to try a couple other drivers and see if that fixes the problem.  

So I know I can at least connect to unprotected WAPs.  Don't know if this will help you, but it sure made me feel good to make some progress.

EDIT:  Ok, maybe I can't connect to any access points.  I might have still had my wired connection in, and I just thought it was connected.  Anyway, this is definitely progress.  I can see my network at least, and my computer isn't freezing up anymore.  I have to get up early, so I'm calling it quits for now, and I'll try to get it completely working tomorrow.

---

### Post by e-lizza on 2006-06-06
[QUOTE=plefno]So I blacklisted the rt2570 in /etc/modprobe.d/blacklist .[/QUOTE]
If I run 
> $ modprobe - l | grep rt25

there are 2 drivers rt2570 and rt2500. 

Did you blacklisted both of them?

---

### Post by plefno on 2006-06-06
I did initially blacklist both, and then I removed rt2500.  Maybe that's why it isn't connecting for me anymore.  But when I just blacklisted rt2570, Ubuntu didn't autodetect the card.  It might be best to blacklist both just to be sure.

---

### Post by plefno on 2006-06-06
Ok, I've definitely got it connecting again.  I know for sure it's my wireless connection because my wired connection is physically not connected.

**My current configuration:**
I have only rt2570 blacklisted in /etc/modprobe.d/blacklist .
I am using ndiswrapper and the windows driver off the install CD.
And I can at least connect to unsecured WAPs.
Right now I don't have ndiswrapper starting on Ubuntu startup, so I'm reinstalling the driver each time I boot.  I don't think I'll have to do this always.  I just don't have it configured to autostart yet.

And now I'm really going to bed.  Hope you make some progress.  I'll check this thread tomorrow.

---

### Post by e-lizza on 2006-06-06
[QUOTE=plefno]And now I'm really going to bed.  Hope you make some progress.[/QUOTE]

Good night, plefno!
I can check it only in the evening. I am in Europe. And it is about 9:15 a.m. only.

---

### Post by SUparJErk on 2006-07-04
Any further progress on getting this working? I'm trying to convince my girlfriend to switch to Ubuntu permanently, but if her network isn't functional, I don't have a very strong argument.

---

### Post by lmp on 2006-07-15
I have also got he wusb54gv4. I had no problem isntalling it under xubuntu and ubuntu. Just plugged in the device and it was recorgnised byt the system.
However ther is a trick !!! after connecting to the usb devise, change the properties but DONT connect!!. Save and restart. Than after restarting activate and everything will work (so without ndiswrapper).
On my desktop everything works fine. Only on my laptop I have a problem that the system disconnects after 5-10 minutes. This seems to be related to being a laptop. According to a windows magazine it should originate from the powermanagement of the wifi. The powermanagement of the wifi should be set to normal (in windows). I don't know how to do this under Xubuntu. Does anybody know????

---

### Post by Relic2K on 2006-08-11
Imp;
     Where/which program/files are you speaking of when you mention making changes ? You didn't mention how or where you are making the changes in your last post. Are using WPA or WEP ? I to would like to avoid using ndiswrappers if possible.
     Mine also works perfectly (was recognized) with ndiswrappers and no security. I just want to use WPA TKIP, but most of the programs so far don't give you any ability to set that up or use. Let me know soonest thanks :)

Relic

---

### Post by ruffEdgz on 2006-08-11
I am a noob when it comes to ubuntu so bare with me ;)

I also have this driver and have tried installing the drivers from this site:

[http://www.cicerosonline.com/WUSB54GC/](http://www.cicerosonline.com/WUSB54GC/)

I was wondering if anyone tried this? Is this the same USB wireless  driver that everyone else is using in this problem. 

I am going to try some new things like the blacklisting and the ndiswrapper but I thought I would ask some of those questions. 

Thanks for the help 

|2uff

---

