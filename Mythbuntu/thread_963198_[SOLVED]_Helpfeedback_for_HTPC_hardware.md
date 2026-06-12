---
title: "[SOLVED] Help/feedback for HTPC hardware"
date: 2008-10-30
forum: Mythbuntu
---

### Post by laffinet on 2008-10-30
I'm planning on building a Mythbuntu based (cheap) HTPC and need some help/feedback regarding hardware.
Here's the planned configuration so far:

Motherboard:	Asus M2N-MX SE Plus
Processor:	AM2 LE-1600
Graphics:	NVIDIA GeForce6100 /nForce430 Chipset (onboard)
Hard drive: 	250G IDE (existing)
Memory:	        2G 667MHz
TV card:	        Leadtek DTV2000H
Network:	        D-Link DWA-510 wireless
Remote:	        Microsoft Remote
DVD:	        none (rip via Laptop if necessary and copy wireless to hard drive)
Case:	        Antec - Antec NSK2480B
Power supply:	incl.

hooked via VGA to LG LCD with HD tuner, so I only need a single tuner card to watch and record different programs.

I've tried to make this as cheap as possible. The main requirements are: play DVDs (or ripped), play mp3 collection, use as PVR (terrestrial DTV, Australia).

Few questions:
1. Is this setup powerful enough for HD content ?
2. Is everything compatible with Mythbuntu ?
3. The TV cards comes with a remote, what functions are possible with Mythbuntu ?
4. Is it possible to configure Mythbuntu with remote so that I can pause/play mp3s without having to fire up the Display (LCD TV) ?

Any feedback/recommendation welcome. Thanks for any help.

Cheers.

---

### Post by Valen00 on 2008-10-30
Whats that system come to in terms of $?

Core 2 CPU's are pretty cheap, try and get one of those into it if you can, it helps if you want to commercial flag and watch tv at the same time.

---

### Post by newlinux on 2008-10-30
1. It is probably powerful enough (I had an Athlon 64 3500 that did HD), but I agree, get a cheap dual core. Certainly powerful enough with XvMC
2. Looks good, I don't know much about non US tv cards, but I think I've seen that one used before
3. The remote buttons are completely configurable in myth. You can program any button to do any available myth function, and there are a lot of them
4. not sure...

---

### Post by laffinet on 2008-10-30
Thanks for your comments.

System so far came to approx. AU$500, which I had set myself as the limit/target.

I've changed a few things based on you recommendations:

Motherboard:	Asus M2N68-VM
Processor:	AMD AM2 x2 5000+
Graphics:	Nvidia® Geforce®7Series (onboard)	
Hard drive:	250G IDE (existing)
Memory:  	2G 667MHz
TV card:	Leadtek DTV2000H
Network:	D-Link DWA-510 wireless
Remote: 	Microsoft Remote
DVD: none (rip via Laptop if necessary and copy wireless to hard drive)
Case: Antec NSK2480B
Power supply: incl.

Which now comes to approx. AU$560. 

Judging from your comments I might be able to drop the extra remote and just use the one that comes with the TV card. Correct ? Will it be supported by Mythbuntu ?

If that's the case I might then throw in a DVD drive (only AU$25) or a new hard drive (AU&83 for 500G).

Any more thoughts/recommendations ? Thanks.

---

### Post by newlinux on 2008-10-30
You literally can use any IR remote (some already have sample configs floating around which make them easier to configure, but you can also create your own config with any remote using irrecord). The key is whether or not the IR receiver you plan on using (is there one that  comes with your tuner card - is that what you are planning on using) is supported. Even if it isn't you could build or buy one and use it with the remote that comes with your Tuner card.

Hopefully someone else knows more about that card, but a few searches might turn up the information too...

---

### Post by laffinet on 2008-10-31
I've read somewhere that there are issues with nvidia series7 and XvMC (mainly that XvMC is not possible with series7 chipsets). Does anyone know about any details ? Can this be overcome ?

---

### Post by newlinux on 2008-10-31
I think series 7 is okay, but not series 8 and higher (I haven't kept up with the latest driver updates so this may be outdated). But you should have no need for XvMC - your CPU (especially if you get the dual core) will have no problems decoding Mpeg-2 HD content without it, and I have found it to be a bit buggy for some. All of the CPUs in my sig (with the exception of the Celeron M) have no problems decoding Mpeg-2 HD content without XvMC

---

### Post by laffinet on 2008-11-17
For completeness sake, this is what I ended up building and the issues I had with it

Motherboard: Asus M2N68-VM
Processor: AMD AM2 x2 5000+
Graphics: Nvidia Geforce 7Series (onboard)
Hard drive: 320G SATA Western Digital
Memory: 2G 667MHz
TV card: Leadtek DTV2000H Rev. J
Network: D-Link DWA-510 wireless
Remote: Rock MCE Remote
DVD: some Samsung 20x DVD-RW SATA
Case: Antec NSK2480B
Power supply: incl.

Issues: 
- got tired trying to get the Leadtek remote to work so bought the ["Rock" MCE remote]("http://www.pcworld.idg.com.au/index.php/taxid;2136212606;pid;4896;pt;1"), worked out of the box
- ensure that HDMI is connected while installing Mythbuntu, hard to get working otherwise
- newest NVIDIA driver causes live TV to freeze, one version down (forgot number) works without problems
- had to modify xorg.conf to make sure correct resolution is selected

Other problem is that I can not get the wireless/router/wireless connection between my mythbox and my laptop to work. Got a thread [here ]("http://ubuntuforums.org/showthread.php?t=973638")but so far no solution.

Other: thinking about buying a Scythe Mini Ninja CPU cooler to reduce noise, not sure if it fits on the motherboard though.

---

