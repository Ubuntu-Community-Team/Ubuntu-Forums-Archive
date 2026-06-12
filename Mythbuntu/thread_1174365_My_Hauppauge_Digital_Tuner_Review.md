---
title: "My Hauppauge Digital Tuner Review"
date: 2009-05-30
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2009-05-30
[FONT=&quot]ANTEC|THREE HUNDRED BK RT [/FONT]
    [FONT=&quot]GIGABYTE GA-EP43-UD3L 775 P43 R [/FONT]
    [FONT=&quot]2x TV TUNER HAUPPAUGE 1196 HVR-1250 RT  Top 2 PCIe slots[/FONT]
    [FONT=&quot]GIGABYTE GV-N95TD3-512I 9500GT[/FONT]
    [FONT=&quot]TV TUNER HAUPPAUGE|  HVR-2250 MC Model 1229 Bottom PCIe slot[/FONT]
    [FONT=&quot]TV TUNER HAUPPAUGE|1183 RT HVR-1600 Top PCI slot[/FONT]
    [FONT=&quot]PSU FSP|FSP350-60GLN(80) 350W[/FONT]
    [FONT=&quot]CPU INTEL|C2D E7400 2.8G [/FONT]
    [FONT=&quot]MEM 1Gx2|PNY MD2048KD2-800-X4 R [/FONT]
    [FONT=&quot]HD 1.5T Seagate ST31500341AS  32M [/FONT]
    [FONT=&quot]KB ADESSO|WKB-3000UB RT [/FONT]
    [FONT=&quot]DVD ROM LITE-ON|iHDP118-08 18X RTL[/FONT]
      [FONT=&quot]DVD BURN LG|GH22NS30 22X SATA[/FONT]
[FONT=&quot]
Antenna RCA ANT3020X NA CAW 03 [/FONT]
  [FONT=&quot]Mounted in the attic connected to my tuners via 30 foot double shielded RG-59 coax to cheep splitter an 6 foot unshielded RG-6 coax. No preamp or distribution amplifier.
All towers are within 4 degrees of each other and no more than 27 miles away.[/FONT]
   
    QAM 256 reception and tuning:
  HVR-1250 >>>>>>> HVR-1600 > HVR-2250

  DVB-T/OTA ATSC reception and tunning:
  HVR-1250 ~= HVR-2250 >~ HVR-1600
   
  The HVR-1250 is the only card I have that tunes QAM-256 reliably with my cable provider.  Both of the HVR-1250 have very sensitive tuners and can pick up channels that my Sony HDTV cannot.  As for the HVR-1600 it struggles to tune cable channels and play back of live tv and recordings has multiple artifacts.   The HVR-1600 digital tunner seems to work fine w/ OTA ATSC.  The HVR-2250 drivers are experimental (as of today 5-30-09) and work fine w/ OTA ATSC signals but It's QAM-256 reception is spotty at best (if the signal is too strong you get a black screen).

---

### Post by MythAaron on 2009-05-31
Thanks for the review.

My 1600 is the last bug I have in my system.  My analog cable records have low audio with hiss and wine.  My digital OTA reception is better than I thought it would be, but I'm in an apartment with an indoor antenna so I need a better tuner.

The [price]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380047&QksAutoSuggestion=&Configurator=&Subcategory=47&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=hvr-1250") for a 1250 is better than a 1600 too.

Edit:  Aww nuts...it is PCI-Express and it only has one tuner.  Good review, though.

---

### Post by LowSky on 2009-06-01
Im having no issue using my  HVR-2250 picking up QAM clear and perfect picture. May I suggest using a better splitter if you need one at all. Splitters come in different ratings so knowing what the cable company reccomends is a good start. Last time I needed one a stopped by my local cable company store and they gave me one free of charge.

---

### Post by dewmanstl on 2009-06-01
> **LowSky said:**
> Im having no issue using my  HVR-2250 picking up QAM clear and perfect picture. May I suggest using a better splitter if you need one at all. Splitters come in different ratings so knowing what the cable company reccomends is a good start. Last time I needed one a stopped by my local cable company store and they gave me one free of charge.

I noticed here ```
http://www.mythtv.org/wiki/Hauppauge_HVR-2250
``` that it is not supported. Are the drivers out now?

Thanks

---

### Post by LowSky on 2009-06-01
[http://ubuntuforums.org/showthread.php?t=942403](http://ubuntuforums.org/showthread.php?t=942403)

check this link, post number 10

I made a tutorial to get the card working

---

### Post by epi 1:10,000 on 2009-06-01
I tried it w/o any splitters, spliting it w/ 3.5 dB, 8 dB, and 12 dB reduction on my 2250, my Motorola DCT34xx DVR, and one of my 1250s.  The 1250 and the Motorola was able to receive signal and display w/o artifacts across all unencrypted channels. The 1250 did have artifacts when hooked straight up to the main line because the signal was to strong.  The HVR-2250 had trouble w/ QAM accros all signal strengths.

---

### Post by LowSky on 2009-06-01
well personally I'm going to blame your wiring, I would call you cable provider. Make sure the cable feed is grounded properly. Not being grounded while using a digital signal will result in possible signal issues.

Heck a fauly cable outside could be the reaosn you ar enot getting a decent signal. Most Cable companies will replace all out of the house wiring for free if your signal is an issue.

---

### Post by epi 1:10,000 on 2009-06-01
There are too many variables to track down. New line was run last year and grounded to a new 1/2inch 4 foot grounding rod courtesy of TimeWarnerCable. The OOG d04 INBAND STATUS measurement on all channels of the Motorola DCT are showing a s/n ratio between 20.2 to 22.1/GOOD and AGC between 14 and 16%/GOOD.  All my tv's, Motorola DVRs, and TiVo DVRs play nice w/ my cable. It could be problems w/ interference from the mobo, PSU, one of the many case fans, ect.  Other configurations may have different results.  LowSky could you post your config?

---

### Post by LowSky on 2009-06-02
Sure, also make sure the tuner isn't contacting the PCI slot of the case it could cause a distrubance. center the best you can.

AMD Phenom 9950 2.6Ghz
G. Skill DDR2-RAM 1066 2x2048MB (4GB or RAM)
GIGABYTE GA-MA78GM-US2H Motherboard
GIGABYTE GV-NX86T256D Nvidia 8600GT
Hauppauge WinTV-HVR-2250 - Retail box edition
LIAN LI PC-A16 Case.
Hanns·G HW-191DPB Monitor connected through DVI
Vizio VX37L 37" HDTV connected though VGA
COOLMAX CP-500T 500W Power Supply
Logitech MX518 
ENERMAX Aurora Keyboard


Also I have Cablevision for cable. I have the triple play, Phone/internet/TV I use a 4 way splitter. 2 to HDTVs with boxes, one to cable modem, one to HVR-2250 tuner.

A few weeks ago we had really bad internet connection with constant drops of service and horrible pixelation on the the TVs. Cable Co. stoped by checked the feed from the street and inside the house and had to rerun a new line from our house to the street corner. Since then no drops or bad picture.

---

