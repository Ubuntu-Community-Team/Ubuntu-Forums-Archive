---
title: "Best Graphics Card:  Upgrade Old Dell"
date: 2010-10-25
forum: Multimedia Software
---

### Post by jbocean on 2010-10-25
I have an older Dell Inspiron 4550 w/ 2G memory and 38G HD. 
I believe I have GE440 graphics card. I am running 10.04, but the graphics are slower than I would like and when I tried to upgrade to 10.10, my card was not supported and I had to re-install 10.04.

QUESTION 1
Can anyone recommend a good graphics card to choose for an upgrade for this machine?

QUESTION 2
Is changing graphics cards pretty much the same as installing a memory chip, What is the best way to do the upgrade?

Thanks

---

### Post by cascade9 on 2010-10-25
You've probably got a Geforce 4 MX 440 (thats just a more exact version of what you put in). It would be an addon card, AFAIK 4550s didnt come with a standalone video card. 

[http://support.dell.com/support/edocs/systems/dim4550/specs.htm](http://support.dell.com/support/edocs/systems/dim4550/specs.htm)

Hard to find AGP cards these days. If you can find one, a 6XXX or 7XXX series nVidia AGP card would be you best bet. Look for a 6200, 6600, 6600GT, 7300GS, 7300GT, 7600GS or 7600GT. There are other AGP nVidia cards, like the 6800 and 7800GS but they are so power hungry that you would probably need to upgrade your power supply. 

A FX card (FX5200, FX5600, FX5700......dont get a FX5800/5900/5950, power again) would work, but I wouldnt be suprised if you have the same 'unsupported' issue when 11.04 or 11.10 comes out. 

Apart from removing the old drivers before you change video cards, yeah, its pretty much like changing RAM. Remove power cord, pop the case cover off, remove old video card, install the new card, case back on, power cord in, power up, install drivers (if you want).....done.

---

### Post by SeijiSensei on 2010-10-25
[Newegg]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709+600007850&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=") has 24 AGP cards, some of which are out of stock.  The best NVIDIA cards are running the 6200 chip; the ATIs are mostly Radeon 3450's and 4350's.

A 6xxx card might improve your desktop graphics performance, but it won't be much help if you're trying to watch video, particularly 720p or 1080p sources.  The VDPAU technology to handle video decoding in the GPU didn't arrive until the 8xxx series of NVIDIA adapters.  That means you're relying entirely on the CPU to decode video; your P4 is probably outclassed in that department as well.

---

### Post by jbocean on 2010-10-25
I checked (System >> Admin >> Nvidia X-Server Settings) I have ...

GeForce4M MX 420 w/ the 96.43.17 driver.

I went to Nvidia website found there is an updated driver ( 96.43.18 ) which I downloaded & saved to my Downloads folder & haven't touched it.

How do I update the driver ...

Do I need to extract the updated driver anywhere?
Do I need to dis-able compiz first?
Do I need to dis-able the current driver first?
How do I install the new driver (System >> Admin >> Hardware Drivers)?
Will I need to reboot?
What if I screw up - what do I need to do to recover?

Thanks!

---

### Post by Yellow Pasque on 2010-10-25
You can try an Nvidia PCI 8400GS as well. I've gotten mixed feedback on this suggestion. It depends on your mobo and how loaded your PCI bus is, etc

---

### Post by cascade9 on 2010-10-26
Opps, yeah Temüjin, I forgot to say that a PCI 8400GS is an option as well. 

If you play a lot of video it might be worth it, but if its just for desktop use a 6XXX nVidia AGP card will do the same job. 

> **jbocean said:**
> I checked (System >> Admin >> Nvidia X-Server Settings) I have ...

GeForce4M MX 420 w/ the 96.43.17 driver.

I went to Nvidia website found there is an updated driver ( 96.43.18 ) which I downloaded & saved to my Downloads folder & haven't touched it.

The reason why your card wasnt supported in 10.10 is because the 96.xx drivers needed for your card dont work with xorg 1.9. I dont think that the newer version of the 96.xx drivers do support xorg 1.9 yet, and when nVidia does get them going with 1.9 they should appear in the ubuntu repos very quickly afterwards.

---

### Post by jbocean on 2010-10-26
Thanks Cascade (& everyone who contributed) for the info about xorg 1.9 being the culprit.

One of the reasons I am so pleased w/ Ubuntu is it keeps older machines running longer. I am content & happy w/ 10.04 and have found a theme/icon set which works for me (Radiance & Faenza Cupertino Dark). So, rather than go the extra expense & trouble of installing a whole new graphics card - I will keep an eye on updated drivers (looking specifically for xorg 1.9 support) for my current card. Also, I have learned here that downloading & creating a live-cd and then doing a fresh install seems to work better than doing an upgrade. Then later on, I may have the graphics-power to Smoothly run Docky and gain a working knowledge of what a Mac-like Dock can do for me.

---

