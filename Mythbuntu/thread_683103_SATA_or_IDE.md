---
title: "SATA or IDE?"
date: 2008-01-30
forum: Mythbuntu
---

### Post by speedsixdave on 2008-01-30
Hi all,

Brand spanking new Mythbuntu user here. On the kitchen table now I have a:

Antec NSK 2480 case
AMD Athlon LE-1620 cpu
Biostar TF690g motherboard
1Gb ram
Lite-on IDE DVD writer
Hauppauge Nova-T TV card

which all seems to power up! Huzzah!

I was going to connect up an old 30Gb Maxtor IDE drive to start with but the IDE cable that came with the case is not long enough. That's ok - it's easy enough to get a longer cable. But obviously I will need a larger hard drive sooner rather than later. 

My question is: IDE or SATA? I ask because I read somewhere that KnoppMyth has issues with SATA drives ([knoppmyth wiki]("http://www.knoppmythwiki.org/index.php?page=PickingComponents")). Is there any problem with SATA drives in mythbuntu? SATA seems like the future but I don't want to burden myself with more problems yet. I've already got the ATI drivers to worry about...

Thanks, and looking forward to many wasted hours in front of the idiot box,

s.

---

### Post by ubnewbie2 on 2008-01-30
I don't think any modern system will have problems with SATA.  Mine runs perfectly. I have a 500GB drive, and I have a 250GB drive from another Ubuntu machine, which ran perfectly there too.

The only problem with SATA, that I had a few years ago was with an old motherboard, and the BIOS was the cause of the problems.

---

### Post by LaRoza on 2008-01-30
SATA is much better than PATA. It is faster and easier to use.

If your motherboard supports SATA, get it. You don't have to worry about master/slave or anything and usually you just plug it in (power and data cabled) and restart.

(I refuse to call PATA IDE)

---

### Post by twkisner on 2008-01-30
Mythbuntu does not have the the problems other distrobutions have had with SATA drives.

If your buying a new drive I would go with SATA.

---

### Post by ian dobson on 2008-01-31
Hi,

Go with SATA. Simpler wiring, Better performance (Usually), Future proof.

I have 4 00Gb SATA drives in my backend and no probems.

If your buying new drives go SATA but if you've got afew IDE drives lying about use them.

Regards
Ian Dobson

---

### Post by Whiffle on 2008-01-31
Depends.  If you can get PATA drives for cheaper and the performacne of them is good enough, use them.  If not, go with SATA.

---

### Post by speedsixdave on 2008-01-31
Thanks guys!

That seems fairly conclusive, SATA it is then. The cabling will be a lot easier to deal with too.

Many thanks, and I shall report back when I have the thing up and running.

s.

---

### Post by stdPikachu on 2008-01-31
> **LaRoza said:**
> If your motherboard supports SATA, get it. You don't have to worry about master/slave or anything and usually you just plug it in (power and data cabled) and restart.

Restart? Restarting is for wimps ;) In seriousness though, you shouldn't need to restart for a SATA drive to be recognised, it's a hot-swap tech from the get-go. Some chipsets don't yet support it under Linux though (but any Intel and nVidia ones should work).

> **LaRoza said:**
> (I refuse to call PATA IDE)

Quite right too. PATA and SATA are both IDE drives. For those who don't know IDE = Integrated Device Electronics, in other words that circuit board that lives under the spinny bits. Before IDE came about, you generally had to tell the BIOS the exact specs of your hard drive, with IDE all of the drive controller logic was moved onto the hard drive itself. It's an important difference, you people who never had to look up how many cylinders their drive had don't know you're born!</getoffmylawn>

I was going to say that, speed-wise, the different between PATA and SATA drives was negligible, but we've reached the stage now where all the new speedy tech is introduced in the SATA drives, and the PATA drives are generally stuck with older, slower tech. For instance, WD's Green Power drives (perfect for HTPC's by the way) don't come in PATA at all.

---

### Post by speedsixdave on 2008-01-31
Thanks stdPikachu and LaRoza. I was one who didn't know that. Have now had a read on wikipedia and even found out what the ATA stands for - go on go on go on...

Yep, Advanced Technology Attachment. I have now learned two things today, so my day at work was surely not entirely wasted.

s.

---

### Post by baudot on 2008-05-02
i've an old board which i used in the past with a ide harddisc successful, but the harddisc was very loud so i bought a new one. i took a sata and bought a sata to ide adapter and hooked this up to the board and installed mythbuntu. unfortunately after the installation (partitioning the disc, installing etc) mythbuntu does not boot. the kernel claims that there are errors with the disc. i reinstalled and everything did work very well.

has someone got idea idea what i could do with this?

---

