---
title: "Duplicate Tuners"
date: 2009-09-08
forum: Mythbuntu
---

### Post by Barry_IA on 2009-09-08
Hi Folks!

Have two tuners physically installed in my BackEnd: a HVR-1600 (dual tuner with digital and analog halves) plus a HVR-2250 (dual digital tuner).  All are working correctly.  The problem is both tuners of the HVR-2250 are listed twice, both Live TV and in Information.  When in Live TV the Switch Input option will list a second HVR-2250_A as 'available' while I'm watching the real HVR-2250_A.  Same with the HVR-2250_B (other half).

Information is also showing me as having six tuners installed when I only have three.  The identification numbers are also starting at 9 (!).  

.   Tuner    09 ... HVR-1600 Digital      .... (Correct)                                            .................... Records
       .   Tuner 10 ... HVR-1600 Analog               ... (Correct)                                            .................... Records
       .   Tuner 11      ... HVR-2250_A                               .......... (Correct)                                            ................... Records
       .   Tuner 12      ... HVR-2250_A                               .......... (Duplicate of above)
.   Tuner 13      ... HVR-2250_B                               .......... (Correct) ...................                                            Records
       .   Tuner 14      ... HVR-2250_B .......... (Duplicate of above)

So, #12 and 14 are the 'ghost' tuners.  How do I get rid of the duplicate listing?  (I'd prefer not to do another re-install.)

I think I got the 'ghost' tuners when I 'lost' the HVR-2250's: one day they weren't there -- not being listed.  Tried re-installing Steve Toth's files -- didn't find the tuners again.  Went through the BackEnd Install (menu with General, Tuners, etc.), finally went though each sub-menu also and this time it found the HVR-2250 tuners.

No idea how things got started with Tuner #9 -- at one time I did have Tuner #1.  

I'm not concerned about stating with Tuner #9, but would like to get rid of the 'ghost' tuners.

TIA!

---

### Post by ian dobson on 2009-09-08
Hi,

Your "ghost" tuners are actually there to allow you to record 2 programs from the same tuner at the same time (if both channels are on the same multipex). This function is called multirec and was introduced into mythtv in 0.21.

see [http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex](http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex)

You can configure the number of "ghost" tuners in myth-setup under tuners.

Regards
Ian Dobson

---

### Post by newlinux on 2009-09-09
also, your tuners will never start over at 1 unless you delete them all and then re-add them (or change their number directly in the DB). Otherwise if you delete and re-add tuners while others exist it will keep increasing the tuner number.

---

### Post by Barry_IA on 2009-09-14
<quote> Your "ghost" tuners are actually there to allow you to record 2 programs from the same tuner at the same time (if both channels are on the same multipex). This function is called multirec and was introduced into mythtv in 0.21.
<end quote>



Thanks, Ian!  Guess it makes sense though seems odd when have two "A's" and two "B's" to represent the two tuners on the single card.  Guess I'll just :go with the flow". <g>

---

### Post by Barry_IA on 2009-09-14
> **newlinux said:**
> also, your tuners will never start over at 1 unless you delete them all and then re-add them (or change their number directly in the DB). Otherwise if you delete and re-add tuners while others exist it will keep increasing the tuner number.

Thanks, NewLinux!  Makes sense.

As a follow-up to the other issue, I had to reboot the 12th and 13th to get the HVR-2250 (both halves, A and B, or A, A, B and B as it's displaying) to be visible/work again.  ...Just checked [morning of the 14th]: working fine, so not an overnight problem.

---

