---
title: "About instalation of other programs"
date: 2008-08-06
forum: Mythbuntu
---

### Post by jlvc on 2008-08-06
I'm building an htpc, i'm not sure at all about what to choose mce 2005 or linux with mythtv, i think i'll take linux, but, if i choose mythbuntu, can i install another software, for example azureus or transmission?
My favourite distribution is fedora, but as i saw your distribution good and easy , i will take mythbuntu, if mythbuntu doesn't let me do that i think i'll take ubuntu and do the post-install using ubuntu (in spain is easy to get free tv using ubuntu).

Thanks, Jay.

---

### Post by nickrout on 2008-08-06
yes you can install other software. However a lot of other software doesn't sit well with mythtv if you are intending to use it like you do myth, ie from the sofa with a remote control.

For bittorrent I use rtorrent, a console client (and a very good one too). I can sit on the sofa with my remote for the mythtv functions and log into rtorrent with ssh from the laptop.

---

### Post by jlvc on 2008-08-07
Thanks, very useful info, I'll see if i what i need is compatible or if i need to install it over ubuntu.
I'd like to ask something about hardware, i don't know if I should do a new thread, anyway I'm gonna do it here.

To play 1080p what do i need? is enough 512 mb graphic card (I've heard that resolution depends of memory of the graphic card), is an nvidia 6200 LE TC 512? and a nvidia 8400 GS 512mb?
If i buy graphic card with hdmi, does the hdmi "move" (sorry English is not my best) sound? if does, do i just have to connect the card to the pcie or do i need to connect sound there
If the card comes without fan and only with the rest of cooler (i mean the metallic part) is it dangerous if i don't do anything with 3d (just to use it as media center to play movies and music).

Is AMD Athlon64 X2 4000+ enough , p4 3.0 ghz is more expensive, is it better?


Edit: i found a motherboard with video and sound integrated 1080p :D

AMD Athlon64 X2 4000+
Asus M2N-VM HDMI
Buffalo DIMM 1 GB DDR2-800 (i know there's no need of 800 frecuency, but difference is 1&#8364;)
Samsung HD501LJ (500 GB HD sata)
167&#8364; - 255.932 USD i think it's a good price, maybe in usa is cheaper... no case no tv card yet.

Edit 2:
Wifi card Abit AirPace WLP-01 + 12&#8364;
Is this the recommended remote in the websitte? [http://www.alternate.es/html/productDetails.html?artno=EZFM01](http://www.alternate.es/html/productDetails.html?artno=EZFM01) +24 it's in spanish but i supose it isn't hard to see if is this one.

---

### Post by Lindsay.Mathieson on 2008-08-07
The Asus M2N-VM HDMI is an excellent board, I have the Asus M2N-VM DVI which works well. The onboard Nvidia 7050 works with XvMC and the Audio - ALC883 supports 5.1 surround sound on linux.

I'd recommend a Athlon 5000+ and 2Gb ram if you can afford it.

Excellent choice of remote the Microsoft MCE - its ergonomic and plug&play under Linux/MythTV.

Dunno about the wifi card - alawys tricky under linux, I'd research that one carefully.

Re other apps - not a big issue. I run a mailserver, subversion server and wine on my MythBox, never been a problem.

One thing - if you do go with Windows, I'd try GBPVR ([http://gbpvr.com](http://gbpvr.com)) rather than MCE 2005. Personally I think its much better (on windows).

But I'd still go with myth.

---

### Post by jlvc on 2008-08-07
Thanks for the fast response, the price is quite similar so i think i'm gonna buy that cpu, the giga of ram i think i'm gonna see with one, and if i need more i'll buy, later :)

What really worries me is the tv tunner, i need now DVB-T and they're easy to find, but in a not very long while, i'm gonna need **DVB-S** probably and they're hard to find, at least **1080p** (i don't know if all the countries have the same protocol, sorry)

The wireless card is recommended by this page: [http://linux-wless.passys.nl/?lang=english](http://linux-wless.passys.nl/?lang=english) , but, can you tell me please your experience with your wireless card? i want something which the computer recognises in the install with 54 MBit/s (11g) support, i don't mind the price, i mean, this can be 10 &#8364; more or less expensive, and i want this to be ok for years, better if is pci, it's not very important because my router is approximately 1 meter, i want it to do adhoc.

Note: I'm sure i'll finally pick mythbuntu, it has everything done, and my father wants a linux-based system too.

Edit: Does mythbuntu have any **problem** with **screens in chases**?i've seen one cheap and bewatiful but it has a screen, does mythbuntu have any problem with them?

---

### Post by Lindsay.Mathieson on 2008-08-08
I don't use DVB-S (Satelite?) but I presume its similar to DVB-T, just different sources. As far as I know the max res is 1080p so you're unlikely to go higher than that :) Also I don't think the res is a function of the card - it merely streams the signal for us. What you can do with it is a function of your CPU, video card and TV.


The wireless looks good, I would expect it to work OOB on mythbuntu + updates.


<i>Does mythbuntu have any problem with screens in chases</i>

Whats a "screens in chases"? Do you mean a built in VFD/LCD on the PC case?

Support varies, we'll need more detail but it can be done. At the worst it would just not drive it, but it shouldn't stop myth itself working.

---

### Post by jlvc on 2008-08-08
Thanks for the fast response again :)
Some responses.
> **Lindsay.Mathieson said:**
> As far as I know the max res is 1080p
Right, i said at least because if it is higher I don't mind

> **Lindsay.Mathieson said:**
> 
Whats a "screens in chases"? Do you mean a built in VFD/LCD on the PC case?

Yes, that's what i meant, sorry , my English could be better.

I Will finally pick a dvb-t.
I have my last questions:
1st:how can i change the title of my thread? i wen to my first message and edited the title but it didn't change

I want to do a pvr to watch one thing and record one at the same time (even better i had a time machine of 5 or 6 minutes but it's too much hehe...) Well to do that, i've heard i need 2 cards or one double, is it right?

Is 264&#8364; WITHOUT tv tunner for

Asus M2N-VM HDMI (motherboard sound and video included, hdmi 47&#8364;)
AMD Athlon64 X2 5000+ (cpu 2x 2600 69&#8364;)
A-DATA DIMM 1 GB DDR2-800 (1 gb ram ddr2 800)
Samsung HD501LJ (hd sata2 7200 rpm 500 gb 54&#8364;)
Abit AirPace WLP-01 (wifi receptor atheros chipset no problems with linux checked 12&#8364; does what i need)
Barebone NOX CUBE - Black (without window 39&#8364; ) (i prefer nox media but it's too big)
LC Power LC380M V2.2 - 380W Micro (feedign font? 380W 25&#8364;)

I think i won't can get it cheaper.
1&#8364;=1.5$

---

