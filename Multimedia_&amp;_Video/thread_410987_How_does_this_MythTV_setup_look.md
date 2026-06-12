---
title: "How does this MythTV setup look?"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by jord1242 on 2007-04-16
OK, so made the splash from Windows to Ubuntu, NICE. So far my media center PC has Ubuntu Edgy on it. I am looking to install MythTV and play with it on my current media center PC, but decided instead of upgrading hardware on that box, I am going to slowly build a new sleeker looking one from the ground up.

I was wondering if some of you Mythtv users could take a look at what I propose to buy and build, and offer suggestions, etc. as I am a noob with Ubuntu and especially Mythtv, but not necessarily with hardware in general.

My setup. I have a DirectTV tivo that currently records my shows. I would like to run the Sat cables right into the computer, but I know that isn't possible, so I guess I would like to run from the set top box to the computer and record the shows within Mythtv. I need a dual tuner setup, as I like the ability to record 2 shows at once (it would be cool to run 3 tuners LOL).

[B]Case: ASUS Pundit (SiS chipset, slim barebones model)
PSU: Included
Motherboard: Included, ASUS P4S8L
CPU: Intel Celeron 2.0 GB, would like more, but not sure what the motherboard can handle
RAM: 2 GB DDR-333
Hard Drive: 500 GB Hard drive - would like the abiity to add more space as needed.
Optical: Sony DRU-500AX combo drive - a bit pricey, is there a cheaper option?
Video Card: NVidia Quadro FX540 PCIE 128MB DDR1 3D Graphics Card
Sound Card: Audigy
NIC: onboard
Video Capture Card: Hauppauge WinTV PVR-250 - would this work using my DirectTV DVR? Also, is this fully supported in Edgy (I see Feisty adds drivers to better support Hauppauge).[/B]

Let me knwo what you think, what I am missing, what doesn't look right, what you would add. I am adding slowly, so money isn't necessarily a problem, but I don't want to go overboard!

Thanks a lot,
JJ

---

### Post by superm1 on 2007-04-17
You've got a very capable starter setup here.  What you will need is an IR transmitter to control your cable box.  Also, i'd recommend you setup using feisty next week at release.  Lots of improvements to mythtv packaging, and it will save you a heck of a lot of hassle with stuff like mysql and ivtv.

Setup your drive with two partitions - one smaller one for data and such, and then a huge one that will be recordings.  If you setup the recordings partition as a LVM type, you can add other drives at a later time JBOD style.

---

### Post by jord1242 on 2007-04-17
Awesome info and thanks, yes, I will def need an IR transmitter, is there ones that work well with DirectTV that anyone has tested out? In the past, I have had issues with IR transmitters not working with DirectTV boxes. 

Other than that, this looks like a good setup? The IR Transmitter will obviuously change the channel on the DirectTV box when it is set to record. 

Does that look good then with a good IR Transmitter?

Thanks again for the help!

JJ

---

### Post by jord1242 on 2007-04-17
One other thing, what can I do to add an external hard drive to store all the recordings on, that will allow me to add more space if needed? I want to start with 500GB then add more as I need, without a lot of hassle. 

Thanks,
JJ

---

### Post by newlinux on 2007-04-17
You can setup your partition for storing recordings using LVM (logical volume manager) which allows you to add another hardrive that the OS sees as simply expanding your partition. I think, however, in myth .21 this will be unecessary (don't know when it will be available as a package in Ubuntu), as it will include a mechanism for distributing your recordings in different locations.

Your setup looks good to me. What about an IR receiver and remote? Do you have cable as well as DirecTV?

---

### Post by superm1 on 2007-04-17
> **newlinux said:**
> You can setup your partition for storing recordings using LVM (logical volume manager) which allows you to add another hardrive that the OS sees as simply expanding your partition. I think, however, in myth .21 this will be unecessary (don't know when it will be available as a package in Ubuntu), as it will include a mechanism for distributing your recordings in different locations.

Your setup looks good to me. What about an IR receiver and remote? Do you have cable as well as DirecTV?

Myth 0.21 is ages away yet.  There are ~900 tickets open, and the only time a new myth release happens is when that number comes down.  I'll have packages ready for it shortly after its released though.  For now, LVM is a better solution.

For IR transmitting, you have three options afaik.  Serial, mceusb2, or PVR-150.  I've got experience with serial and mceusb2.  I've never changed channels on a directv box, but i've had luck controlling tvs and receivers with the devices.  Should be the same basic concept.

---

### Post by jord1242 on 2007-04-17
> **newlinux said:**
> You can setup your partition for storing recordings using LVM (logical volume manager) which allows you to add another hardrive that the OS sees as simply expanding your partition. I think, however, in myth .21 this will be unecessary (don't know when it will be available as a package in Ubuntu), as it will include a mechanism for distributing your recordings in different locations.

Your setup looks good to me. What about an IR receiver and remote? Do you have cable as well as DirecTV?

I'll have to do research into LVM as this seems the option to go. Would this work with USB devices? I was thinking of adding external drives as needed, I could then some how mount them as one partition?

Thanks for the info. Also, if anyone has any success with remotes running on linux and MythTV, let me know what the best one would be to buy. I am researching out now the best IR receivers to change the channel.

Thanks,
JJ

---

### Post by jord1242 on 2007-04-17
> **superm1 said:**
> Myth 0.21 is ages away yet.  There are ~900 tickets open, and the only time a new myth release happens is when that number comes down.  I'll have packages ready for it shortly after its released though.  For now, LVM is a better solution.

For IR transmitting, you have three options afaik.  Serial, mceusb2, or PVR-150.  I've got experience with serial and mceusb2.  I've never changed channels on a directv box, but i've had luck controlling tvs and receivers with the devices.  Should be the same basic concept.]

LVM is fine for now, and to be honest, I probably won't be needing to use this for a while, as I plan on buying a 500GB external drive. Once I get to the point of maxing that out, I can then determine if MythTV supports it, or if LVM is the best way to go.

I have heard mention of PVR-150 directly controlling the DirectTV box ???? But I am not sure if that is the option for me to go. I wonder if anyone has had success using a DirectTV Tivo set top box with either Serial or mceusb2??

Thanks for the info!!!

JJ

---

