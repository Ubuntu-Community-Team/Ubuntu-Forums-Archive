---
title: "Router too far away??"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by krockroc on 2010-05-03
Hi,

frustrated newbie here....

Dual boot Vista Basic and Ubuntu 10.04 on low spec PC.

Issue:
I can connect to the wireless when I am next to it. I move to the room where the computer is normally used and I lose connection. I can still see it but it fails to establish a connection. 
Okay, sounds like it's just too far way but when I re-boot and use Vista, it works fine (1 or 2 bars, but it works). 

Is this a driver issue?

Anything I can do apart from move my wireless router?

Thanks.

---

### Post by P4man on 2010-05-03
Yes, quite possibly a less than stellar driver.
What wifi card do you have? Can you post the output of this command:

```
lspci
```

---

### Post by krockroc on 2010-05-03
Hi P4man,

Output of lspci is at the end.
My issue has sligthly changed since the last post.
Still no conection 'far' away but when I connect close I actually have no web access. 100% connection but no internet. A direct cable allows access to the web.

No security on the router.
I think the wifi card is a Realtek 8187b ('I think' because that's what it says, but when I googled it, it's called a USB modem - my card is internal...not USB).

          00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX  
 00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)  
 00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)  
 00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)  
 00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)  
 00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)  
 00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller  
 00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)  
 00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)  
 00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller  
 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)  
 
Thanks.

---

### Post by P4man on 2010-05-03
looks like its an internal USB card, well connected to usb internally. Guessing its a HP laptop?

anyway, show us the output of

```
lsusb
```

---

### Post by kelvin spratt on 2010-05-03
You may need to change the wireless channel in your router from 0-1 to 8. i had the same problem with win7 and that cured it.

---

### Post by krockroc on 2010-05-03
Not a hp. An e.system (???) laptop... It was cheapo a few years back. 

Bank holiday here in ireland so out right now. I will get the output later. 

I will try changing the channel too. 

Thanks both.

---

### Post by krockroc on 2010-05-03
OK...

changing the channel to 8 worked a treat. Thanks Kelvin.

Wifi access is funny. I did some tests..... 
Inside the room - okay.
Just outside the room - okay
1 metre away from door - okay
1.5 metres away from door - not working
Back to 1 metre - works
1.5 metres - not working.

The room where we normally use the pc's is a further 10 metres way and works with Vista (only thing that works well, as the pc is such a low spec). 

output of lsusb:

          Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device  
 Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 
Thanks

---

### Post by P4man on 2010-05-03
Im confused now. Are you saying there is still a tangible difference between ubuntu and vista (on the same machine using the same wifi card!) or not?

If not, consider buying a high gain antenna for the access point. They really do help. moving to 802.11n instead of b/g makes an ever bigger difference but (probably) requires a new access point and wifi card.

also, dont understand this line:
> works with Vista (only thing that works well, as the pc is such a low spec). 

If it runs vista, it can run any OS. Ubuntu or XP or windows 7 or any linux. There is no bigger resource hog than vista!

---

### Post by krockroc on 2010-05-04
> **P4man said:**
> Im confused now. Are you saying there is still a tangible difference between ubuntu and vista (on the same machine using the same wifi card!) or not?

If not, consider buying a high gain antenna for the access point. They really do help. moving to 802.11n instead of b/g makes an ever bigger difference but (probably) requires a new access point and wifi card.

also, dont understand this line:


If it runs vista, it can run any OS. Ubuntu or XP or windows 7 or any linux. There is no bigger resource hog than vista!

Sorry, I was sure I replied to this already. When I said "*works with Vista (only thing that works well, as the pc is such a low  spec).*"...I mean the wireless router is the only thing that works beeter on Vista. Everything else is nearly unusable because it is so slow.

So, same card, same router but Ubuntu doesn't let me go further than 5 to 6 metres. Vista allows about 20 metres through the house.

Everything else on Ubuntu works perefectly.
Wireless printer (in the room), email, internet.....and fast (well as fast as you can expect 512MB ram). In fact, I tried to install the Lexmark printer on Vista before and it told me that there was not enough memory...no complaints with Ubuntu.

So, overall, I think I am a convert to Linux...if I can just get the wireless at a distance to work **(any other suggestions?)**. A little bit of a chore to get everything working but, it's free and faster and I hope less 'Windows type updates to download" (none, preferably).

Thanks.

---

### Post by P4man on 2010-05-04
Try the windows drivers. This only works for wifi drivers btw.
Here is how to:

[http://ubuntuforums.org/showthread.php?t=1444096&page=3](http://ubuntuforums.org/showthread.php?t=1444096&page=3)

posts 23 and 24.

---

### Post by krockroc on 2010-05-05
Hi P4man,

I am away with work until Friday so will try that on the pc when I get home on Friday (Volcano-permitting).

Thanks.

---

### Post by krockroc on 2010-05-07
P4man,

woohoo!!! That did it.

Everything now works and of course much, much faster than Vista was.
Looking back, the only thing that didn't work and took most of my time was the network connection and most of that was because I was too far away for the original driver. Once I moved, I got connection and then using the link you gave me, I got steady connection from everywhere.

Excellent.

Thanks again.

---

