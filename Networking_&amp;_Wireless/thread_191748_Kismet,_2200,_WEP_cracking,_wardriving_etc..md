---
title: "Kismet, 2200, WEP cracking, wardriving etc."
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by scottylans on 2006-06-07
Hi guys,

I'd really like to have a good discussion here and work out (once and for all) what the deal is with wardriving and WEP / kismet on the 2200 under ubuntu (or linux in general)

I've heard stories that the ipw2200 does support monitor mode, then it was removed, then back etc.

Can you do EVERYTHING under ipw2200 or is the card limited? 
Can you inject packets with a 2200?
Is there support for all cracking and wardriving tools for the 2200 or is the card holding me back?

Anyone here with any good experience care to comment?



EDIT: and if we DO establish the card is perfectly fine for it, what are the best tools and are they available for ubuntu?

---

### Post by scottylans on 2006-06-08
No interest? - no knowledge - any comments at all?

---

### Post by cinephy on 2006-06-09
The 2200 does support a rfmon mode but only in Linux. Kismet has worked flawlessly for me with this card. Just apt-get it and setup the /etc/kismet/kismet.conf file. The source line should read:

[INDENT]source=ipw2200,eth1,ATHEROS[/INDENT]

Change eth1 to whatever points at your card. After that you should be up and running. WEP keys have been cracked with weak packet capture and aircrack.

---

### Post by jslatton on 2006-06-09
ipw2200 b/g does NOT support packet injection.  if you can get it to work, you'd make about 10,000 people instantly happy.

this means you cannot inject ARP packets to increase weak IVs (which is what is needed to crack wep).

but, this is hardly the place to discuss this.  it has been talked about at length over at [http://www.remote-exploit.org](http://www.remote-exploit.org).  Back|track is the best security/pentest distro out there.

---

### Post by piracyrocks on 2006-06-10
i installed kismet but i do not know how to run it.....it did not place an icon to click on in the "Applications" menu.  what do i do?

---

### Post by scottylans on 2006-06-12
[QUOTE=jslatton]ipw2200 b/g does NOT support packet injection.  if you can get it to work, you'd make about 10,000 people instantly happy.

this means you cannot inject ARP packets to increase weak IVs (which is what is needed to crack wep).

but, this is hardly the place to discuss this.  it has been talked about at length over at [http://www.remote-exploit.org](http://www.remote-exploit.org).  Back|track is the best security/pentest distro out there.[/QUOTE]


jslatton: really REALLY appreciate the response, good to finally have an answer!
is it a limitation of the hardware or the drivers?

Essentially, what you're telling me, is if I'm trying to crack a lan which has very low activity, I'm screwed?

---

### Post by cinephy on 2006-06-12
Sounds that way to me... BUT

While searching through the Back|track forums I did come across something which may be of interest to you

[http://www.netstumbler.org/showthread.php?t=19792]("http://www.netstumbler.org/showthread.php?t=19792")

(the link came from a B|t forum post. I realize this directs to a different forum.)
This seems to be hinting at some sort of packet injection but the more I dugg around it still seems as if it is still crippled in some fashion. Let me know if this helps at all.

---

### Post by scottylans on 2006-06-12
jslatton:

Another thing, if my 2200 is useless, can you perhaps suggest another card for me?

What is out there in USB or PCMCIA with excellent linux support for capturing / sniffing packets and injecting packets to boot??
I remember looking around and having problems finding a NEW PCMCIA card which can do this, since most new cards seem to be 802.11g which rarely seemed to have decent wardriving support? (well bad chipsets for wardriving)

---

### Post by endokrin on 2006-06-12
Are you saying you want a card that you can crack WEP more easily with?

---

### Post by scottylans on 2006-06-13
Essentially yes, specifically cracking wep rather than finding.

So I don't care about a highly sensitive card with good range, more a card which has full support for the cracking side like packet injection etc.

---

### Post by scottylans on 2006-06-13
I'm specifically after a PCMCIA card with good injection support, I got my rt2500 PCI card working on my desktop last night but couldn't get a SINGLE weak packet from the WAP I was trying to get into - I think it's a range issue.

---

### Post by chili555 on 2006-06-13
[QUOTE=piracyrocks]i installed kismet but i do not know how to run it.....it did not place an icon to click on in the "Applications" menu.  what do i do?[/QUOTE]

Open a terminal and type sudo iwconfig ethX mode monitor and then sudo kismet.

Be sure you have /etc/kismet/kismet.conf correctly configured first. Read /usr/share/doc/kismet/README.gz for lots of direction.

---

### Post by scottylans on 2006-06-14
Hey guys!

I got my rt2500 card to work, following a .SWF howto on how to crack wep in 10 minutes.

It was pretty straight forward, unfortunately without injection support on the ipw2200 it's pretty bloody hard so really kinda pointless even using kismet on an intel 2200.

I've ordered a dlink usb card using the RT2570 chipset which apparently has very good support thanks to the serialmonkey drivers (google it)

I couldn't capture enough IV's using my gigabyte RT2500 chipset due to aerial problems though - so I'm looking to upgrade that too.

Anyhow, ipw2200 and wardriving is mostly pointless unless you figure out packet injection which apparently CAN be done but it's not very good and kind of a workaround method, I'm sure if the firmware is ever patched or the driver or whatever needs fixing, we'll all know, but until then aireplay and ipw = useless unless the target network is extremely busy.


Next on the agenda is to find a really really good pcmcia card with long range and injection support (incase the rt2570 has bad range or not enough volts over usb or something to really give it some "oomph")

---

### Post by wildseven on 2006-07-16
> **cinephy said:**
> The 2200 does support a rfmon mode but only in Linux. Kismet has worked flawlessly for me with this card. Just apt-get it and setup the /etc/kismet/kismet.conf file. The source line should read:

[INDENT]source=ipw2200,eth1,ATHEROS[/INDENT]

Change eth1 to whatever points at your card. After that you should be up and running. WEP keys have been cracked with weak packet capture and aircrack.


i just got kismet, but for the source line i put

source=ipw2200,etho0,ipw2200

and it works, is there a difference?

---

### Post by wildseven on 2006-07-16
> **scottylans said:**
> Hey guys!

I got my rt2500 card to work, following a .SWF howto on how to crack wep in 10 minutes.

It was pretty straight forward, unfortunately without injection support on the ipw2200 it's pretty bloody hard so really kinda pointless even using kismet on an intel 2200.

I've ordered a dlink usb card using the RT2570 chipset which apparently has very good support thanks to the serialmonkey drivers (google it)

I couldn't capture enough IV's using my gigabyte RT2500 chipset due to aerial problems though - so I'm looking to upgrade that too.

Anyhow, ipw2200 and wardriving is mostly pointless unless you figure out packet injection which apparently CAN be done but it's not very good and kind of a workaround method, I'm sure if the firmware is ever patched or the driver or whatever needs fixing, we'll all know, but until then aireplay and ipw = useless unless the target network is extremely busy.


Next on the agenda is to find a really really good pcmcia card with long range and injection support (incase the rt2570 has bad range or not enough volts over usb or something to really give it some "oomph")


for packet injection and WEP cracking, cant you just use kismet to find the WAP and then use airsnort to capture IV's and airplay to send repeated packets to the system to speed up the process?

---

### Post by Xhosa on 2006-08-03
For a list of cards suitable for WEP cracking using aireplay - see:

[http://tinyshell.be/aircrackng/wiki/index.php?title=FAQ#Which_is_the_best_card_to_buy_.3F](http://tinyshell.be/aircrackng/wiki/index.php?title=FAQ#Which_is_the_best_card_to_buy_.3F)

and

[http://tinyshell.be/aircrackng/wiki/index.php?title=Compatibility](http://tinyshell.be/aircrackng/wiki/index.php?title=Compatibility)

In reponse to the earlier queries about using aireplay - unless your card has support for this in its firmware, it will just drop the packets (this is what the ipw2200 does).  

Se this thread:

[http://tinyshell.be/aircrackng/forum/index.php?topic=25.0](http://tinyshell.be/aircrackng/forum/index.php?topic=25.0)

For more details on the ipw2200 and injecting.

---

### Post by Supersaiyan.IV on 2006-12-11
> 
Another thing, if my 2200 is useless, can you perhaps suggest another card for me?

What is out there in USB or PCMCIA with excellent linux support for capturing / sniffing packets and injecting packets to boot??
I remember looking around and having problems finding a NEW PCMCIA card which can do this, since most new cards seem to be 802.11g which rarely seemed to have decent wardriving support? (well bad chipsets for wardriving)


To me ipw2200 is far from useless.

WEP CRACKING _IS_ SUPPORTED BY [COLOR="Red"]IPW2200[/COLOR] after applying a packet injection patch.  
Compatibility proven-> [http://www.aircrack-ng.org/doku.php?id=compatibility]("http://www.aircrack-ng.org/doku.php?id=compatibility")

Here's a full how-to description: [http://tinyshell.be/aircrackng/forum/index.php?topic=400.105]("http://tinyshell.be/aircrackng/forum/index.php?topic=400.105")

Just as a note that it actually works I can say that i'm sending this post  
from my [COLOR="Red"]neighbour's[/COLOR] 128bit wep encrypted wifi network.

The patch works for ipw2200-1.2.0 and 1.1.4 (simply rename folders). Enables ARP replies, however rest of the 'active' attacks supported by Atheros and other better cards don't work.
However it's good enough. 1,2million IV's per hour is what my ipw2200 gets at a poor signal. 

With trial and error everything works ;) Good Luck and have fun ;)

---

### Post by gunbladeiv on 2007-06-12
how about broadcom???
any suggestion on how to crack WEP??
im using kismet on bcm43xx driver but dont know how to crack wep...
any suggestion?

---

### Post by Hero_boy on 2007-11-07
> I got my rt2500 card to work, following a .SWF howto on how to crack wep in 10 minutes. - scottylans

Would you have a URL to this .SWF scottylans?

> 
how about broadcom???
any suggestion on how to crack WEP??
im using kismet on bcm43xx driver but dont know how to crack wep...
any suggestion?
- gunbladeiv


I have a similar issue. I have a Cnet CWP-854 wireless PCI card (H/W ver B - RT2500 chipset). Ubuntu 7.10 automatically installed the bcm43xx driver which works fine.

So I installed Kismet and edit the following line:

**source=RT2500,wlan0,wireless**

Now when I try to start Kismet it give me the following error:
[B]
FATAL: Failed to set monitor mode: Device or resource busy.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README[/B].

Do I simply need to do what it says & put my card in 'monitor' mode somehow? Or do I need to upgrade my drivers from the automatically installed bcm43xx ones to some RT2500 drivers?

Thanks in advance!

---

### Post by KamakazieX on 2007-11-12
I am at the same dead-end with the RT2500. Device/resource busy. same with iwconfig..

1. What is the name of the service taking control of the device? Been trying to grep it, no luck.

2. Could it be a driver issue? (It is a 10$ wireless card)

---

### Post by mahousaru on 2007-12-08
Sorry for the late post but here is how I solved the issue with the standard rt2500 driver that comes with gutsy

First right click disable wireless in the Gnome network manager

```

sudo ifconfig wmaster0 down
sudo iwconfig wlan0 mode monitor
sudo kismet

```

To reconnect to you network afterwards do

```

sudo ifconfig wmaster0 down
sudo iwconfig wlan0 mode managed

```

---

### Post by icheyne on 2008-01-10
Here's the fix to the Gutsy RT2500 and Kismet problem:

[http://ubuntuforums.org/showthread.php?t=662994](http://ubuntuforums.org/showthread.php?t=662994)

---

