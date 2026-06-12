---
title: "Which USB Wireless Adapters work out-of-the-box with 13.04?"
date: 2013-08-10
forum: Networking &amp; Wireless
---

### Post by dccmgb on 2013-08-10
Please let me know if you have a USB Wireless Adaptor that has worked out-of-the-box with Ubuntu 13.04 (manufacturer and model #).  

I currently have an ASUS USB N-13 Adapter (ASUS supported with Linux) and have created the following post ([http://ubuntuforums.org/showthread.php?t=2166114](http://ubuntuforums.org/showthread.php?t=2166114)) for help but as of now have not received any replies.  So the next best option is to purchase an adapter that works with 13.04 without requiring any code modification.  

I'm frustrated that it has taken this much time to get a connection (my ASUS adapter works fine with XP) under 13.04 but still hanging in there with Ubuntu (not yet ready for the faint of heart).  Your information and help will be greatly appreciated.  dc

---

### Post by kurt18947 on 2013-08-10
I haven't used any dual frequency (2.4/5 ghz.) adapters but I have a small collection of N150 adapters with a couple that have been plug'n' play since at least 12.04.  One is Netgear WNA1100 using an Atheros 9271(I think) chipset.  The other is Trendnet TEW-649UB using a Realtek 8192SU chipset.  I can plug either of these in and they 'just work'.  There are a couple others that are great for notebooks/netbooks but come with some cautions.  I have a generic Ralink/Mediatek RT5370 -$5 from Ebay - which I believe gained 'OOB' support in 12.10.  It should be okay with 13.04.  I had problems with the RT5370 having weaker reception/slower throughput than other adapters.  I got a new wireless router and installed 13.10 at about the same time.  The RT5370 is now working much better but I'm not certain if it's the new router, new O.S. or some combination.  I have another great performer but it's not strictly plug'n'play.  Edimax EW7811Un using a Realtek RTL-8188CUs chip has great reception and throughput but it requires a tuned driver, it doesn't work out of the box.

I have one caveat with the above.  The adapters I mentioned do work out of the box.  Manufacturers sometimes change chipsets without changing model #, they just add some sort of suffix.  Dlink seems to have a fondness for that.  I have and used to recommend Dlink DWA-131, it's a twin the Trendnet TEW-649UB.  Dlink changed chipsets and called the new chipset DWA-131 ver.B.  There was no way to determine if an adapter is the original which did work out of the box or ver. B which did not work - at all - without buying the adapter, opening the box and reading the label on the adapter.  I don't know of a way around buying & checking the version, I don't think it's on the packaging.  There are other choices - Tenda is one - but I have no experience with them.

---

### Post by beaucoder2 on 2013-08-11
Hi Kurt,

I am testing 13.04 64 bit on an MSI 970A G46 Motherboard with an AMD FX-4130 processor, 4 GB DDR3 1333 RAM. 
The NetGear WNA1100 works fine on it. Just install, 13.04 finds it and off we go. 

I would like to know some other newer, faster brands and models. 

It is almost impossible to get advance information. Does Ubuntu have a "installed & working" page for wireless adapters for 12.04, 1304 (32bit and 64bit)?

This is very frustrating. No one knows for sure. Anyway, you can also quote me on ubuntu 13.04 64-bit:  WNA1100 works like a champ. 

HTH,

Ken Wagner, Sugar Creek, MO

---

### Post by kurt18947 on 2013-08-12
This is one of the shortcomings of community maintained pages.  They may start up gangbusters but soon are outdated.  Plus new models come out so frequently.  The single best source I've found is wikidevi.  If you know the chipset being used instead of the manufacturer/model, you can better assess the probability of it working 'out of the box'.

---

### Post by lucas4 on 2013-08-12
currently I have [Linksys WUSBN600v2]("http://support.linksys.com/en-eu/support/adapters/WUSB600N"). Worked in 12.04, works also with 13.xx. Didn't really have to do anything - just plug in and vuoila!

---

### Post by beaucoder2 on 2013-08-12
Thanks, Kurt, for the wikidevi link. ([http://wikidevi.com/wiki/Main_Page](http://wikidevi.com/wiki/Main_Page)). Very, very helpful.

Question for lucas4:  Is your 13.04 32-bit or 64-bit?   

Thanks, 

Ken

---

### Post by dccmgb on 2013-08-12
Selecting a USB Wireless Adapter based on chipset versus Mfg/model# makes sense.  Is there a list of the Ubuntu supported/proven chipsets?

---

### Post by kurt18947 on 2013-08-12
> **lucas4 said:**
> currently I have [Linksys WUSBN600v2]("http://support.linksys.com/en-eu/support/adapters/WUSB600N"). Worked in 12.04, works also with 13.xx. Didn't really have to do anything - just plug in and vuoila!

That's good to know.  Do both frequencies work?  No issues with WPA/WPA2?  These are functions that can cause problems with some adapters.  For instance, some Intel wifi devices work perfectly at G speeds (2.4 ghz., 54 mb./sec) but are not happy at N speeds/ >54 mb./sec no matter what the specs say.

---

### Post by dccmgb on 2013-08-14
I have confirmed that the Tenda W311M wireless adapter is definitely plug-n-play with Ubuntu 13.04,  No modification needed as it uses the Ralink RT5370 chip, which is already proven (see #2 above).  Bought it yesterday at a MicroComputer Center store for $9.99.  Supports 150Mbps and is working great.

For $3 more, I could have bought another Tenda that supports 300Mbps but it has a different chipset that according to searches on this site would require some modification - so it was of no interest to me after dealing with previous wireless adapter issues with Ubuntu.

Does someone know if there is a way and place to create a list of supported wireless adapters by specific Ubuntu releases so to make it easier for the next person.  I believe there are 4-5 proven wireless adapters with 13.04 just within this tread.

---

### Post by beaucoder2 on 2013-08-29
Thanks, Guys.

This is a great start. Did not know the Tenda W311M works with 13.04. Tried it with some older releases but only had grief. Nice to know.

Ken Wagner

---

### Post by afortner03 on 2013-12-16
Hi Kurt, I am new to Ubuntu and love it I am working on building a desktop and would like to know if the Trendnet  TEW-649UB works on Ubuntu 13.10

---

### Post by kurt18947 on 2013-12-17
> **afortner03 said:**
> Hi Kurt, I am new to Ubuntu and love it I am working on building a desktop and would like to know if the Trendnet  TEW-649UB works on Ubuntu 13.10

Yes, I believe it should.  The reason it may not is if TrendNet has changed the chipset in the adapter.  The TEW-649UB I have uses a RealTek8192SU chipset and is plug 'n' play.  Once you have a functioning Ubuntu system, you can plug the adapter in and it should come alive with no further action.  If not, you can run the terminal command "lsusb" and see if there's a line that has 'Realtek 8192SU'  in it.   The only flaw I've seen with my 8192SU devices is they will not connect after being suspended.  A way to check if your system has this problem is to suspend,  resume from suspend and notice the wifi adapter appears to not be powered.  Unplug the adapter, wait a second and plug it back in.  If it then works, you need to create a simple file to suspend the adapter before suspending the system.  Resume should then work properly.   If you need help with this, feel free to contact me and I'll find the info.  Good luck with your build.

---

### Post by cazub on 2013-12-18
For 13.10 i can confirm the d-link 131 and Asus n-13 do NOT work out of the box. Haven't tried rolling back to 13.04. Same for netgear WNDA3100v2. Basically every dongle , even the 'linux compatible ones' and ones listed as 'the most compatible out of the box wifi cards for linux!' require

downloading the driver from the manufacturer website (no internet connection so how can i do this?) 
untaring the tar file 
issuing a MAKE command (again no internet connection so i can't install MAKE, it wasn't included by default on cd)
some combination of modprobing 

OR if you're real lucky like with the WNDA3100v2 you'll get to use ndiswrapper which again requires an internet connection to get. 

Lets say the drivers get installed correctly. Is the device working? WHo knows! Maybe? Network-manager doesn't really do anything, i can't issue an init.d/networking restart anymore because i'm supposed to use the service command. More good news, the service command barely works! 

Now i'm 60 bucks in on wifi dongles that "Absolutely for sure work out of the box!" , anyone want to buy one? They make great paperweights with ubuntu.

---

### Post by kurt18947 on 2013-12-18
> **cazub said:**
> For 13.10 i can confirm the d-link 131 and Asus n-13 do NOT work out of the box. Haven't tried rolling back to 13.04. Same for netgear WNDA3100v2. Basically every dongle , even the 'linux compatible ones' and ones listed as 'the most compatible out of the box wifi cards for linux!' require

downloading the driver from the manufacturer website (no internet connection so how can i do this?) 
untaring the tar file 
issuing a MAKE command (again no internet connection so i can't install MAKE, it wasn't included by default on cd)
some combination of modprobing 

OR if you're real lucky like with the WNDA3100v2 you'll get to use ndiswrapper which again requires an internet connection to get. 

Lets say the drivers get installed correctly. Is the device working? WHo knows! Maybe? Network-manager doesn't really do anything, i can't issue an init.d/networking restart anymore because i'm supposed to use the service command. More good news, the service command barely works! 

Now i'm 60 bucks in on wifi dongles that "Absolutely for sure work out of the box!" , anyone want to buy one? They make great paperweights with ubuntu.

I'm sorry to hear about your bad luck.  The Dlink DWA-131 did work 'out of the box' initially, it used a Realtek RTL8192SU chipset.  Dlink changed chipset to what I don't know but it was no longer plug 'n' play.  The Netgear WDNA3100V2 has been a problem child from the get-go.  Ask Chili555 about that one.  The only success with the WDNA3100V2 was with NDISwrapper and that seemed pretty hit-and-miss.  I'm not certain but I seem to remember the Netgear WDNA3100 (not the 3100V2) had a better chance of working but was still not easy or certain.  I'd say wifi is the biggest PITA with linux hardware.

---

### Post by manishbhoola on 2014-03-31
For ubuntu 14.04 beta, I can confirm that D-Link N 150 adapter works out of the box. Worth the upgrade to this latest LTS.

---

### Post by kurt18947 on 2014-04-02
> **manishbhoola said:**
> For ubuntu 14.04 beta, I can confirm that D-Link N 150 adapter works out of the box. Worth the upgrade to this latest LTS.

It appears your D-Link N150 uses the Mediatek/Ralink RT5370 chip which does have good compatibility.  How are your signal strength & speed?  I've never gotten over 72 MB./Sec. indicated in iwconfig and signal strength shows as lower than other adapters.  I've not had any disconnect problems with it though.  A good choice for plug 'n' play.

---

