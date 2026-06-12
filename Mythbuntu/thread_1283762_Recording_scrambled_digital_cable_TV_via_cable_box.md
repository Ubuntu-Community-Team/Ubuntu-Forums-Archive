---
title: "Recording scrambled digital cable TV via cable box?"
date: 2009-10-05
forum: Mythbuntu
---

### Post by cat2005 on 2009-10-05
_Contender for dumb questions of the year_:

I am certain my cable (Time Warner) encrypts each digital channel except the local channels.  If I were to watch those encrypted digital channels, then I would need to rent their stupid cable box.  

1)  Is it possible to route that digital signal, after being unscrambled, to my TV tuner?  
2)  If yes, then I should be able to both watch and record the unscrambled digital cable TV signal, correct?

Thank you.

---

### Post by tgm4883 on 2009-10-05
> **cat2005 said:**
> _Contender for dumb questions of the year_:

I am certain my cable (Time Warner) encrypts each digital channel except the local channels.  If I were to watch those encrypted digital channels, then I would need to rent their stupid cable box.  

1)  Is it possible to route that digital signal, after being unscrambled, to my TV tuner?  
2)  If yes, then I should be able to both watch and record the unscrambled digital cable TV signal, correct?

Thank you.

Yes you need the box. You can route it to your analog tuner card, alternatively you can connect the cable box via firewire.

---

### Post by xinix on 2009-10-06
You'll probably want an IR blaster if you don't go with the firewire option.  With this mythtv will be able to change channels on the cable box.

---

### Post by JMcFly on 2009-10-06
What's the best analog way to connect to the cable box? Svideo and audio cable? Composite cables? 
 
What firewire speed do you need for capture? I think my mobo is limited to 50mbps on the firewire port (its much slower than using USB2.0 to move files to my external drive) due to its age.

---

### Post by blackoper on 2009-10-06
best analog way is an hdpvr with component capture and optical in.
If you use something like a pvr-150 then svideo and rca audio

---

### Post by cat2005 on 2009-10-06
> **xinix said:**
> You'll probably want an IR blaster if you don't go with the firewire option.  With this mythtv will be able to change channels on the cable box.


I am looking at my mobo manual and can not find anything related to "firewire".  It is an ASUS p4s800.  Could it be differently named?

---

### Post by xinix on 2009-10-06
It has a couple other names but Firewire is the one that seems to have stuck thanks to Apple.  The standard is "IEEE 1394", Sony uses "i.LINK", Texas Instruments calls it "Lynx".

---

### Post by cat2005 on 2009-10-07
> **tgm4883 said:**
> Yes you need the box. You can route it to your analog tuner card, alternatively you can connect the cable box via firewire.



tgm4883,

I just thought of something.  Suppose I have the cable go into my box, then route it to my analog card tuner.  Thus the output is analog.  What if my analog card tuner lacks encoding capability?  Would I only be able to watch, but not record?

---

### Post by tgm4883 on 2009-10-07
> **cat2005 said:**
> tgm4883,

I just thought of something.  Suppose I have the cable go into my box, then route it to my analog card tuner.  Thus the output is analog.  What if my analog card tuner lacks encoding capability?  Would I only be able to watch, but not record?

The encoding would happen in software, and it would use your CPU to do that. It would be recommended to get at least a hardware encoder. IMO, software encoders are more trouble than they are worth.

Digital tuners don't have hardware encoders, as the signal is already encoded when it comes in.

---

