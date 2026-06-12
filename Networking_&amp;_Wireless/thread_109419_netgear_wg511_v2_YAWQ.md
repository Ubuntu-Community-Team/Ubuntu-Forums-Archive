---
title: "netgear wg511 v2 YAWQ"
date: 2005-12-28
forum: Networking &amp; Wireless
---

### Post by glug101 on 2005-12-28
Greetings and thank you to all in advanced for the wonderful and friendly help that I have come to expect from this community:)

I am a long time linux user who loves this whole UNIX-like thing that is going on seemingly everywhere.  I haven't posted to ubuntu forums in awhile because I've been spending most of my time on my powermac.  Recently I've gotten back my sweet ruggedized thinkpad and I am working on getting ubuntu squeezed onto it.  Unfortunately, my network card that I bought for it isn't working correctly.

The network card is a Netgear wg511 v2 that was made in China.  After following ndiswrapper instructions, I have gotten the drivers from the install disc onto the laptop, and [HTML]</i>ndiswrapper -l</i>[/HTML] shows that the drivers are installed.  Heck, I even have a happy green light on the card.

However, when trying to get the networking setup, the card can't be seen.  wlan0 does not exist, despite the correct drivers being installed the computer being told to look for one.  Anybody have any ideas for this confused unix fan?

---

### Post by Lambert on 2005-12-28
if you run iwconfig and there's no wlan0 (or interface name for the device if it's different then wlan0) then the driver is not working properly.

1. if you do not have these in the same folder as the .inf file you will need the .sys and if there's a .bin file

2. you might be able to find more help at the ndiswrapper wiki page.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page")

---

### Post by glug101 on 2005-12-28
Thanx for the quick response Lambert.

Is there a special place to put the .inf and .sys files? (there is no .bin file)  I had all of the files copied to the harddrive and in the same folder when I ran the ndiswrapper.  I've also seen the wiki page.  I haven't given up on it yet, but what I've read seems to show that I have everything setup correctly.  The only thing that I can think of is to try a native driver (I think there is one for this card) or compile an up to date version of ndis.  However, the latest version requires gcc 3.4 (4.0 doesn't seem to cut it) and I don't have a working network connection to install 3.4 :(

Seriously considering returning this card for one that will work out of the box...

---

### Post by Lambert on 2005-12-28
No, there's no special place to put the files. 

There is no native driver for that card that I know of (I show it being a marvel chipset and I do not know of a native driver for that chipset)

I don't like to recommend buying a new card but it's what I did and sometimes what's called "the real cost of gnu/linux". I had a card with a broadcom chipset and after a couple days of struggling bought a card with an atheros chipset. Best $40 I spent.

The only thing I can say at this point is remove the driver you used and look around and try another driver. (driver for 2in2k or one off the manufacture website if you used the cd rom) Sometimes updates to drivers are done which change things and might make ndiswrapper not work with the driver properly. 

If you lean towards buying a new card here are some links to do research.

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
[https://wiki.ubuntu.com/WirelessNetworkCards](https://wiki.ubuntu.com/WirelessNetworkCards)

Have you searched the forums with wg511v2? you might find a post with somebody succesful and tips on making work.

---

### Post by glug101 on 2005-12-28
Thanx again for the swift reply lambert!  

I have searched the forums, and that's how I've gotten as far as I have.  Unfortunately, there are a lot of other people with many different problems with the same card :(  The solutions seem to be irradic and none I've found so far have worked for me.

On the plus side, I just bought the card yesterday from best buy.  As long as I return everything intact, I can get a full refund for store credit and get one that works! :) (might be the best option, eh?)

Thanx again for the help:)

---

### Post by Vetto on 2005-12-28
Netgear WG511 has an anthros chip (at least all the ones sold in the US do).  as does the 511T which I have.

Your card should work in linux with the shipped madwifi drivers, you shouldnt need ndiswrapper...if it doesnt, see [this post]("http://www.ubuntuforums.org/showthread.php?t=105437")

---

### Post by Lambert on 2005-12-28
netgear uses multiple chipsets in their 511 series

[LIST=1]
[*]Card: Netgear WG511 v3 (Made in China)[LIST]
[*]Chipset: Intersil Corp.3890 PRISM GT 802.11g
[*]Driver: SMC2802W driver used; available at [http://www.smc.com/files/AV%5CDR_2802wV.2_WHQL.zip]("http://www.smc.com/files/AV%5CDR_2802wV.2_WHQL.zip") (from above)
[*]Other:Mandrake 10.1, Linux 2.6.8.1-24mdk, ndiswrapper 1.1, WEP Note: Mandrake automatically loaded the prism54 module, but it didn't work that well. I unloaded that and used ndiswrapper. Works great.[/LIST] 
[*]Card: Netgear WG511 v2 54Mbps Cardbus adapter[LIST]
[*]Chipset: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
[*]pciid: 11ab:1faa[/LIST][/LIST]

---

### Post by glug101 on 2005-12-28
[QUOTE=Vetto]Netgear WG511 has an anthros chip (at least all the ones sold in the US do).  as does the 511T which I have.

Your card should work in linux with the shipped madwifi drivers, you shouldnt need ndiswrapper...if it doesnt, see [this post]("http://www.ubuntuforums.org/showthread.php?t=105437")[/QUOTE]

the wg511 v2 made in china DOES NOT have the anthros chip in it.  (however, any future wireless cards that I buy will ;) ).  I believe that the 511T does, but I'm quite sure that mine does not. (I think the ones made in taiwan 'just work' with ubuntu)

---

### Post by glug101 on 2005-12-28
[QUOTE=Lambert]netgear uses multiple chipsets in their 511 series
[/QUOTE]

Yeah, apparently they think this is fun :)

---

### Post by Vetto on 2005-12-28
LOL...Lambert.  I refered your madwifi post here not realizing you were the author of it as well as the guy helping here!  Too bad about the various chips, nothing like making life easier.

---

### Post by jacrook on 2006-02-14
Just wanted to thank yall for posting all this help... I followed the various threads and got my wg511v2 to work on the first try. I love this distros community! Thanks again!:)

---

### Post by metasquier on 2006-02-14
you need to make sure that you go:

sudo modprobe ndiswrapper

Then use: 

dmesg | grep ndiswrapper

to make sure its going.  After that use:

wiconfig wlan0

and this should show up your device if its working, then it should also show up as wlan0 in your networking setup for ubuntu.

---

### Post by metasquier on 2006-02-14
Oh and to make sure that the module loads by itself on startup, you need to go:

sudo ndiswrapper -m

This adds the module to the module config file to auto load it.

---

### Post by Neffscape on 2006-10-22
Hi, unfortunately ndiswrapper seems to refuse every driver I found on netgear website (i cabextracted the .exe and i tried to install every .inf and .sys I found), so I'm currently unable to install my netgear wg511 v2 (made in China).
I'm a newbie so I don't know exactly how this ndiswrapper-thing should be applied, can you please help me by suggesting me a good and detailed howto?
I need the right drivers too (for the moment I tried [THESE]("http://kbserver.netgear.com/products/WG511v2.asp"),but ndiswrapper tell me that the driver is invalid:

here is the output of ndiswrapper -l:

[INDENT]wg511v2 invalid driver!
wg511v21        invalid driver!
wg511v22        invalid driver!
wg511v23        invalid driver!
wg511v24        invalid driver!
wg511v2.sys     invalid driver!
wg511v2xp.sys   invalid driver!
wg511v2xp.sys1  invalid driver![/INDENT]

As you can see I tried to install several drivers but no one is working!

Help me please! I don't know what to do

Thank you very much in advance!

Neff

---

### Post by wwood on 2006-11-06
Hi,

Just to let everyone here know that I got the wg511 v2 (made in china) working on Edgy. I used ndiswrapper-1.8, and followed the solution talked about at a launchpad location location I forget. The problem was that ndiswrapper-1.1 is the default, when 1.8 should be (that is the newest version right now).

But yeh, it works!

---

### Post by wwood on 2006-11-06
Neff,

I missed your post. I didn't have this problem. I used the INF file from the cd (Windows 2000 version), I've attached the driver I used. I've uploaded the sys file too, but I'

```
> ndiswrapper -l
Installed drivers:
wg511v2         driver installed, hardware present
```

Just to make sure we are on the same wavelength, 
```
 > lspci
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```

---

### Post by wwood on 2007-03-21
Perhaps mainly for myself, here's a history dump what I did from start to finish to enable my wireless card I talked about above

First I got all the other repositories running; ndiswrapper is in universe or multiverse I think.

Installed ndiswrapper-utils-1.8 using synaptic.

unpacked the tar.gz file in my post above into the folder t in my home directory.

<code>
    1  lspci
    2  uname -a
    3  cd t
    6  sudo ndiswrapper -i WG511v2.INF 
    7  ndiswrapper -l
   10  sudo depmod -a
   11  ifconfig
   13  sudo modprobe ndiswrapper
   14  dmesg |grep ndiswrapper
   15  ifconfig
</code>

I don't believe it will start up next time I start up, but that's ok for the moment.

---

### Post by rogdef on 2007-05-28
> **wwood said:**
> Perhaps mainly for myself, here's a history dump what I did from start to finish to enable my wireless card I talked about above

First I got all the other repositories running; ndiswrapper is in universe or multiverse I think.

Installed ndiswrapper-utils-1.8 using synaptic.

unpacked the tar.gz file in my post above into the folder t in my home directory.

<code>
    1  lspci
    2  uname -a
    3  cd t
    6  sudo ndiswrapper -i WG511v2.INF 
    7  ndiswrapper -l
   10  sudo depmod -a
   11  ifconfig
   13  sudo modprobe ndiswrapper
   14  dmesg |grep ndiswrapper
   15  ifconfig
</code>

I don't believe it will start up next time I start up, but that's ok for the moment.

This worked perfectly for me! Thank you!

---

### Post by mrbubbles on 2008-01-17
I got my 511v2 to work using the Netgear drivers, and there's just one problem: if I ever have to restart my system, I have to uninstall the drivers and reinstall them again to get the silly card to work. is there a reason I have to do this, or have I just missed something...

---

### Post by mrbubbles on 2008-01-22
bump

---

### Post by mrbubbles on 2008-01-23
bump

---

### Post by mrbubbles on 2008-01-23
hello?

---

### Post by mrbubbles on 2008-01-24
*sigh* bump

---

