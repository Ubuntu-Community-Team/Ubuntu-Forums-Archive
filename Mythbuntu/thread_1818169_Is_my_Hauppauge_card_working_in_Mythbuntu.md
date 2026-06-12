---
title: "Is my Hauppauge card working in Mythbuntu?"
date: 2011-08-04
forum: Mythbuntu
---

### Post by DoricMan on 2011-08-04
Having a trying time getting Mythbuntu connecting to Freesat in spite of searching this forum and other documentation.
 
I have checked my Hauppauge WinTV-NOVA-HD-S2 card in an adjacent XP system, using the known working Freesat video connection. The card performs correctly in XP. 

The file Freesat.xmltv seems to be configured correctly.

I get the following messages:
Card1 (typeDVBInput) is set to start on Channel Please add, which does not exist.
Card2 (typeDVBInput) is set to start on Channel Please add, which does not exist.
I have not found a way of curing this or even knowing whether the Hauppauge card is even working as it should.

Can anyone suggest ways out of this 3 week dillema?

My hardware is as follows.

 Mythbuntu 
  Release 11.04 (natty)
  Kernal Linux 2.6.38-10-generic
  GNOME 2..32.1

 Hardware
  Memory 2.0 GiB
  Processors O, 1, 2: AMD Phenom 8650 Triple-Core Processor
  Motherboard ASUS M2AN68-AM PLUS
  Graphics card ASUS EN210 GeForce 210 512M DDR2
 
 Hauppauge WinTV-NOVA-HD-S2 Model 229 Digital Sattelite Card     

 Many thanks.

 DM.

---

### Post by thatguruguy on 2011-08-05
> **DoricMan said:**
> Having a trying time getting Mythbuntu connecting to Freesat in spite of searching this forum and other documentation.
 
I have checked my Hauppauge WinTV-NOVA-HD-S2 card in an adjacent XP system, using the known working Freesat video connection. The card performs correctly in XP. 

The file Freesat.xmltv seems to be configured correctly.

I get the following messages:
Card1 (typeDVBInput) is set to start on Channel Please add, which does not exist.
Card2 (typeDVBInput) is set to start on Channel Please add, which does not exist.
I have not found a way of curing this or even knowing whether the Hauppauge card is even working as it should.

Can anyone suggest ways out of this 3 week dillema?

My hardware is as follows.

 Mythbuntu 
  Release 11.04 (natty)
  Kernal Linux 2.6.38-10-generic
  GNOME 2..32.1

 Hardware
  Memory 2.0 GiB
  Processors O, 1, 2: AMD Phenom 8650 Triple-Core Processor
  Motherboard ASUS M2AN68-AM PLUS
  Graphics card ASUS EN210 GeForce 210 512M DDR2
 
 Hauppauge WinTV-NOVA-HD-S2 Model 229 Digital Sattelite Card     

 Many thanks.

 DM.

Have you scanned for channels?

---

### Post by ian dobson on 2011-08-05
Hi,

Scan for channels then setect the start channel.

If you haven't setup mythtv then you need to run mythtv-setup then define a video source,cards and input connections then scan for channels.

Maybe have a look here:- [http://www.mythtv.org/docs/mythtv-HOWTO-9.html#ss9.1](http://www.mythtv.org/docs/mythtv-HOWTO-9.html#ss9.1)

Regards
Ian Dobson

---

### Post by DoricMan on 2011-08-06
> **thatguruguy said:**
> Have you scanned for channels?Yes frequently, but cannot get any channels.

---

### Post by ian dobson on 2011-08-06
Hi,

What messages do you see in the system log (type dmesg|more for the terminal).

Also have a look here:- [http://parker1.co.uk/mythtv_freesat.php](http://parker1.co.uk/mythtv_freesat.php) there are afew tips on how to setup mythtv with your card. It could well be that the mythtv scanner isn't doing the job.

Regards
Ian Dobson

---

### Post by DoricMan on 2011-08-11
> **ian dobson said:**
> Hi,

What messages do you see in the system log (type dmesg|more for the terminal).

Also have a look here:- [http://parker1.co.uk/mythtv_freesat.php](http://parker1.co.uk/mythtv_freesat.php) there are afew tips on how to setup mythtv with your card. It could well be that the mythtv scanner isn't doing the job.

Regards
Ian DobsonThanks Ian and all the above for your help. I'm a bit laid up with an old complaint, hence my lateness in coming back. 
I have now just discovered that my Mythbuntu set-up has somehow lost its ability to write into the various pages, and scripts are not being acted on. Perhaps this explains my problem. I am now doing diagnostic work on the box and so far everything looks OK. Then I will re-format and install Mythbuntu from scratch. 
Living in hope, Thanks everyone.
DM

---

