---
title: "TBS 6981 PCI-E DVB S2 DUAL Anyone?"
date: 2010-11-03
forum: Mythbuntu
---

### Post by byronmyth on 2010-11-03
Anyone have one of these dual cards up and running with Myth? I need to add a second Sat card and I only have a PCI-E slot available, they claim MythTv in their adverts but as it's an expensive card.....

---

### Post by LowSky on 2010-11-03
it should work fine, they even have the Linux driver on their website 

[http://www.tbsdtv.com/english/Download.html](http://www.tbsdtv.com/english/Download.html)

They mention Ubuntu 10.10 and Linux Kernel 2.6.35 so the driver is so far up to date

---

### Post by felipesms on 2011-01-29
I have the same problem
 I can not run the card in mythtv even with the module in memory.
I need step by step

---

### Post by sami8519 on 2011-01-29
I have the TBS6980 which uses same driver as the TBS6981 and it is working fine in mythtv as well as VDR.

Regards
Sami

---

### Post by simonnev on 2011-01-29
I have that card and have no problems with it running .24
use the drivers from the web site.

going to get another one for a slave backend.

Simon

---

### Post by simonnev on 2011-01-29
Oh

got mine for 75gbp

---

### Post by felipesms on 2011-03-07
> **felipesms said:**
> I have the same problem
 I can not run the card in mythtv even with the module in memory.
I need step by step



Ok Thank you all,
 The driver installation for ubuntu that I was failing.
 

 And it worked ...

---

### Post by Billsputters on 2011-07-30
Well, thinking of going the whole hog and trying a quad one! [TBS 6984 quad tuner all on one card]("http://www.tbsdtv.com/english/product/6984.html"). 

I imagine this would work, question is, would it be too much for the bus to handle 4 streams coming from the one card, or would 2 dual ones, splitting the load be a better option.

---

### Post by MickSulley on 2011-10-30
I have a TBS6981 and I have spent ages trying to get it to work.  I have managed to install the drivers following their instructions.  I have done what I guess is correct in the setup but I just get 'Failed to find any new channels!'.

On the Scan Config screen I have
Scan type: Full Scan (Tuned)
Frequency:  11597
Polarity:  Vertical
Symbol Rate:  22000000
Mod Sys:  DVB-S
FEC:  Auto
Modulation:  QPSK
Inversion:  Auto
Roll-off:  0.35

I am in UK, Midlands using the dish from my Sky system.  I am running Ubuntu 11.10

Can anyone give me some pointers on how to get this working? 

Thanks
Mick

---

### Post by nickrout on 2011-10-30
> **MickSulley said:**
> I have a TBS6981 and I have spent ages trying to get it to work.  I have managed to install the drivers following their instructions.  I have done what I guess is correct in the setup but I just get 'Failed to find any new channels!'.

On the Scan Config screen I have
Scan type: Full Scan (Tuned)
Frequency:  11597
Polarity:  Vertical
Symbol Rate:  22000000
Mod Sys:  DVB-S
FEC:  Auto
Modulation:  QPSK
Inversion:  Auto
Roll-off:  0.35

I am in UK, Midlands using the dish from my Sky system.  I am running Ubuntu 11.10

Can anyone give me some pointers on how to get this working? 

Thanks
Mick

have you set up your diseqc options? And ensured that the stick? (mythtv-setup has a nasty habit of these settings not sticking for some reason)

---

### Post by MickSulley on 2011-10-31
> have you set up your diseqc options? And ensured that the stick? (mythtv-setup has a nasty habit of these settings not sticking for some reason)
I had missed that, but it is still not working.

I have taken details from my Sky box and set up as follows -
diseqc set to LNB
LNB Preset:  Universal(Europe)
LNB Type:  Universal (Voltage & Tone)
LNB LOF Switch:  11700
LNB LOF Low:  9750
LNB LOF High:  10600

I have come out and gone back in to confirm that it has saved that info.

and in Scan Config
Scan Type:  Full Scan (Tuned)
Frequency:  11778
Polarity:  Vertical
Symbol Rate:  27500000
Mod Sys:  DVB-S     I have tried DVB-S2 as well
FEC:  Auto
Modulation:  QPSK
Inversion:  Auto
Roll-off:  0.35

When I press Next it flashes something and then says 'Failed to find any channels'

I have noticed that if I go out of this option completely and then go back in it has not remembered any of the Scan Config settings, is that normal?

What am I doing wrong here?  This is driving me nuts.

---

### Post by shad0w_walker on 2011-10-31
If that is what you are putting in frequency, try this instead:

11778000

---

### Post by trippy21 on 2011-10-31
> **MickSulley said:**
> I had missed that, but it is still not working.

I have taken details from my Sky box and set up as follows -
diseqc set to LNB
LNB Preset:  Universal(Europe)
LNB Type:  Universal (Voltage & Tone)
LNB LOF Switch:  11700
LNB LOF Low:  9750
LNB LOF High:  10600

I have come out and gone back in to confirm that it has saved that info.

and in Scan Config
Scan Type:  Full Scan (Tuned)
Frequency:  11778
Polarity:  Vertical
Symbol Rate:  27500000
Mod Sys:  DVB-S     I have tried DVB-S2 as well
FEC:  Auto
Modulation:  QPSK
Inversion:  Auto
Roll-off:  0.35

When I press Next it flashes something and then says 'Failed to find any channels'

I have noticed that if I go out of this option completely and then go back in it has not remembered any of the Scan Config settings, is that normal?

What am I doing wrong here?  This is driving me nuts.

I think the polarisation should be horizontal, i used the settings here [http://iwtf.net/2010/01/05/freesat-hd-mythtv-0-22-linux-pvr-with-ubuntu-howto-%e2%80%93-part-3/](http://iwtf.net/2010/01/05/freesat-hd-mythtv-0-22-linux-pvr-with-ubuntu-howto-%e2%80%93-part-3/)
for my HVR4000 card, which picks up ITV1 HD.
Also my firmware wasn't being loaded at startup so installed the latest drivers from the website, which resolved the main problem

---

### Post by nickrout on 2011-10-31
> **trippy21 said:**
> I think the polarisation should be horizontal, i used the settings here [http://iwtf.net/2010/01/05/freesat-hd-mythtv-0-22-linux-pvr-with-ubuntu-howto-%e2%80%93-part-3/](http://iwtf.net/2010/01/05/freesat-hd-mythtv-0-22-linux-pvr-with-ubuntu-howto-%e2%80%93-part-3/)
for my HVR4000 card, which picks up ITV1 HD.
Also my firmware wasn't being loaded at startup so installed the latest drivers from the website, which resolved the main problem

You assume he wants to acess the same satellite and the same transponder?

---

### Post by krazykev on 2011-12-06
I cannot get this card to work in Ubuntu 11.10 either. I downloaded the drivers from TBS and installed as per their instructions.  i can see the device in Myth Setup but scanning always fails.

I have even tried using the API tools provided (szap-s2), but this freezes.  This is worrying.  Sadly I am new to Linux/Ubuntu so any guidance as to what logs/traces would be prudent to look at would be most appreciated.  I am using Kernel V3 on an X86_64 build. Thanks

---

### Post by MickSulley on 2011-12-06
I had a lot of trouble getting mine to work (see earlier posts in this thread).  At first I could get the driver to work, sounds like you have past that stage, but then I scanned and found nothing.  Initially I looked at all of the settings on my Sky box, same dish so must be the same settings.  Wrong! There are lots I don't understand on this subject, but this link (again from a post earlier in this thread) gave me a start.  I assume the satellite setting depend upon which part of the world you live in, this is for UK.

 [http://iwtf.net/2010/01/05/freesat-hd-mythtv-0-22-linux-pvr-with-ubuntu-howto-%e2%80%93-part-3/](http://iwtf.net/2010/01/05/freesat-hd-mythtv-0-22-linux-pvr-with-ubuntu-howto-%e2%80%93-part-3/)

Hope that helps a little

---

### Post by nickrout on 2011-12-06
Details for most satellite settings can be found on [http://www.lyngsat.com](http://www.lyngsat.com)

---

