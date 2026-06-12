---
title: "Any problems with my build?"
date: 2010-04-30
forum: Mythbuntu
---

### Post by Beastofomous on 2010-04-30
Alright guys so I'm juuuust about ready to pull the trigger on a BE/FE build. I've been trying to sort out the cheapest options for myself because I'm a new home owner, and I just thought I would get one last opinion on everything before I actually did it. So if you wouldn't mind looking at the hardware I selected and let me know if I'm going to have any issues right off the bat I would greatly appreciate it.

COOLER MASTER Elite 360 RC-360-KKN1-GP Black Steel / Plastic ATX Mini Tower Computer Case
Item #: N82E16811119195
Link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811119195](http://www.newegg.com/Product/Product.aspx?Item=N82E16811119195)
$29.99
	

HITACHI Deskstar 7K1000.C HDS721010CLA332 (0F10383) 1TB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive
Item #: N82E16822145304
Link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822145304](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145304)
$79.99
	

Open Box: MSI NF750-G55 AM3 NVIDIA nForce 750a SLI HDMI ATX AMD Motherboard
Item #: N82E16813130235R
Link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813130235R](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130235R)
$69.99
	

Hauppauge WinTV-HVR-2250 Media Center Kit Dual TV Tuner 1213 PCI-Express x1 Interface
Item #: N82E16815116036
Link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16815116036](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116036)
$123.99
	

Kingston ValueRAM 2GB (2 x 1GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10600) Dual Channel Kit Desktop Memory Model KVR1333D3N9K2/2G
Item #: N82E16820134637
Link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820134637](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134637)
$56.99
	

AMD Athlon II X2 240 Regor 2.8GHz Socket AM3 65W Dual-Core Processor Model ADX240OCGQBOX
Item #: N82E16819103688
Link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103688](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103688)
$59.99

Subtotal:	$420.9

---

### Post by colinnwn on 2010-05-02
Looks great. 

That motherboard's onboard video card supports VDPAU, which is awesome. Looks like you need to use Bob X2 deinterlacer to prevent audio stuttering 
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

The HVR-2250 is known as a great digital tuner card. Myth doesn't support using its onboard analog encoder, due to Hauppauge not releasing the technical specs, and not being willing to allow their one interested developer to work on it during company time. Also the onboard remote receiver is not supported in Myth for similar reasons. You'll have to get another type of remote and receiver.

Personally if there was no chance I'd ever use the card on Windows and want the analog tuner and onboard remote receiver, I'd choose a HDHomeRun instead. The dual tuner model has come down in price to where they can usually be found for $125 or a little more on Amazon. The single tuner version can be had for $80 or so I think, they're a steal.

---

### Post by goldshirt9 on 2010-05-02
don't buy a Hitachi deathstar sorry deskstar.
seagate / wd are far better.

---

### Post by colinnwn on 2010-05-02
Several years ago Hitachi richly deserved its Deathstar moniker. I still don't understand why they haven't changed their model name. Recently I believe they are much better. Shortly before this WD went through a period of lower reliability, and after the Deathstar problem Maxtor had some reliability issues that seemed to infect Seagate after they were purchased.

Hard drive tech advances so rapidly (though incrementally), that problems happen for all manufacturers, and get discovered and fixed in the next generation, even if customers with bum hard drives aren't always properly recognized for their trouble.

Right now I don't particularly know of a reason to steer clear of Deskstars. Though I haven't had a need to shop for a hard drive recently, so I am not up to date on current hard drives.

---

### Post by goldshirt9 on 2010-05-02
its a risk you take on any model i agree.
i wouldn't buy due to previously  said unreliability :(

saying that i have just bought a pc with a Samsung hdd and it seems great / fast / quiet.

would it be cheaper to buy a built pc ( without o/s) with most of the expensive items included and change the cheaper ones ?

---

### Post by soccergeek on 2010-05-16
I'm thinking of going with the same.  How did it work out for you?

---

### Post by fraterm on 2010-07-05
Specifically regarding the motherboard: *MSI NF750-G55 AM3 NVIDIA nForce 750a SLI HDMI ATX AMD Motherboard*

I purchased one of these recently, and am having trouble booting with APIC enabled in the BIOS.  Sadly with the APIC disabled it only sees one of my AMD Turion II cores.  Should be 2.  If I enable APIC in bios, the kernel panics/hangs, and I can't boot.

I was wondering if you had run into any of the same problems, and if there were any specific settings to enable that would enable the smooth operation of ubuntu on this particular motherboard.

---

### Post by ian dobson on 2010-07-05
Hi fraterm,

Check for a BIOS update, looks as if MSI have screwed up the APIC tables.

If there isn't an update available maybe try the noapic kernel command line parameter. See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards
Ian Dobson

---

### Post by nickrout on 2010-07-05
I would say that an nvidia 8200, while having the advantage of being built in, is at the very lower end of vdpau capability. If I had the money I would add a nvidia 220 or 240 PCIe card.

---

### Post by colinnwn on 2010-07-06
It is on the low end of VDPAU capability. I frequently buy a motherboard on a raging special, even if it doesn't have my preferred integrated peripherals. But all things equal, I'd rather have an integrated video card that I can use initially, and the option to upgrade to a discrete card later. Are there any other motherboards that have better NVIDA integrated video chipsets and support VDPAU?

Regarding the kernel panic, have you tried using the Ubuntu alternative install disk? In the past, I've found it more robust than the standard install disk. I don't know if they've scripted more workarounds in it for problematic hardware or what. Several years ago when I switched to Mythbuntu, the standard disk would freeze during install, but the alternative disk worked fine.

---

### Post by LowSky on 2010-07-06
You know its funny but the Intel Atom boards with ION technically have Nvidia Mobile version of the 9400. But buying a GT 220 is under $40 and Its a much better option.

---

### Post by nickrout on 2010-07-06
> **LowSky said:**
> You know its funny but the Intel Atom boards with ION technically have Nvidia Mobile version of the 9400. But buying a GT 220 is under $40 and Its a much better option.

ION is great, low power, can be done fanless, can be done with an external power brick, easily net booted, giving you a totally silent front end.

---

