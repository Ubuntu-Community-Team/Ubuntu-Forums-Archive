---
title: "config ideas for MythBE/NAS + Myth/XBMC/Boxee FE"
date: 2010-01-23
forum: Multimedia Software
---

### Post by jalyst on 2010-01-23
_Myth Back-end  +  NAS_ (already own the parts; cept 3x 1/1.5TB HDD)
This machine will do all video capturing/transcoding. 
It will also be the Backup Server/NAS....

1x  **_Old_** Lian-Li midi-Tower or Chen Mei FT
1x  Gigabyte 8600GTS .................................... [take transcoding load off CPU w/VDPAU or is this def. not doable?]
1x  Hauppauge HVR-2200 .................................. [may eventually add a 2nd one]  
1x  GA-P35-DQ6 (ATX form-factor)
1x  TWIN2X4096-8500C5DF ................................. [2x2GB DDR2 1066; 4GB enough?]
1x  Core2Duo (conroe) E6420 2.13Ghz ..................... [may underclock/volt slightly?]
1x  Antec True Power 3.0 650W ........................... [Less wattage possible?]
Storage Sub-sys:
1x  1TB WD Black ........................................ [video capture disk, can it handle 4 simultaneous HD streams?]
1x  150GB 10k RPM Raptor ................................. [boot/system volume?]
3x  1/1.5TB 7.2k RPM HDD ....................... [For content storage & BU, may not bother w/RAID till get hw controller?]

********************************************
_Myth/XBMC Front-end_ (don't have the parts; cept where mentioned)
This will be the media player & MAME PC...
Later (6mth) I'll buy a top-end GPU that'll be swapped-in sometimes for gaming.

1x mATX H57 or Q57 mobo. ......... [make/model?]
1x Intel Core i3 530
2x DDR3 1GB ...................... [make/model?]
1x 30GB SSD or USB Flash*? + 74GB 10k RPM Raptor? (for local storage; already own) 
**_OR_**
1x 1TB WD Black or Samsung F3? [innermost sectors -20GB?- for OS, outermost for local storage]
1x Xonar Essence ST (PCI; already own)
1x H6 (Essence daughterboard; already own)
1x PSU ................................ [perhaps BE PSU is best here if I intend to use strong GPU sometimes; make/model?] 
1x Case ............................... [make/model?]
1x nV GT220 ....................... [only if IGP+CPU not enough; make/model?]

For the back-end I was thinking of doing a minimal Ubuntu install & only adding what is needed.
For the front-end I was thinking of starting the same way and gradually adding MythTVFE, XBMC, and maybe a lightweight DE like crunchbang etc.
Interested in peoples thoughts on what I'm missing hardware or software wise or just some general advice.
Thanks!
________
discarded:
********
74GB 10k RPM Raptor ....................... [very old -not used much- slightly damaged connector so connection always a bit loose]
*4GB USB flash ................................ [aside from the fact that 4GB is too small, is USB flash too much of a poor alt to SSD?]
80GB 7.2k HDD, make/model YTBD.

---

### Post by jalyst on 2010-01-23
anyone?

---

### Post by jalyst on 2010-01-24
Come on, anyone? I've updated my OP.
Thanks....

---

### Post by jalyst on 2010-01-24
Also would ya'll agree with this? ...
[http://forums.overclockers.com.au/showthread.php?p=11370174#post11370174](http://forums.overclockers.com.au/showthread.php?p=11370174#post11370174)

As much as I'd like a shiny new Clarkdale-based FE   :lol: 
I'm starting to think it might make more sense to do an AIO?

---

### Post by jalyst on 2010-01-25
I think I'm going with an AIO, but with the FE I outlined as the platform base. 

So that means I'll sell most of the parts outlined for my proposed back-end.
This will give me a little cash towards the new build, whilst allowing me to move to the newer/sexier Intel platform :)

It'd be cheaper to go with the BE as the base for an AIO (& it'd be plenty of horsepower), but I prefer this approach.
I'll outline the new machine I have in mind soon....

As **figrin** [mentioned]("http://forums.overclockers.com.au/showthread.php?p=11372726#post11372726") Core i3-xxx VA-API support for acceleration is getting there, but still pretty rough.
If I find it's not good enough after a few months, then I can always chuck in a GT220 to be used w/VDPAU.

I do have plans later this year to build a Core i7-based native VMM (baremetal hypervisor). 
So this could become the BE & "jack of all" server, and the AIO could revert to a FE/occasional gaming machine.

In the meantime I'll have my XBOX360 & soon a PS3 which can be used as FE's of sorts.
PS3 in particular, now that it's "apparently" been _fully_ [hacked]("http://www.engadget.com/2010/01/23/ps3-finally-properly-hacked")...

Any thoughts greatly appreciated!?!

---

### Post by jalyst on 2010-01-26
Here is the rough outline I have in mind...
_Underlined_ = I've decided on the part, **bold** = I own it.

1x _Intel Core i3-530_
1x mATX H57 or Q57 mobo?
2x 2GB DDR3?
**1x Asus Xonar Essence ST (PCI)**
**1x Asus H6 (Essence daughterboard)**
**1x Hauppauge HVR-2200**
**1x Antec True Power 3.0 650W**
Storage Sub-sys:
**1x 1TB WD Black** ..............................[capture disk, can it handle 4 simultaneous HD streams?]
3x 1/1.5TB 7.2k HDD? .........................[For content storage & BU, may not bother w/RAID]
_________
Low priority (won't buy this time round, but suggestions welcome!)
*********
1x [30GB OCZ Vertex SSD]("http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=159&bid=2&sid=38269")? ................... [approx $219]
1x nV GT220? .................................... [only if IGP+CPU proves to be not enough]
1x HTPC Case? ................................... [Have crappy old Lian-Li (PC-60?) mid-tower]

Make/model recommendations greatly appreciated!

---

### Post by jalyst on 2010-01-28
Alas there's no Q5x/H5x mATX mobo's with SATA6G & USB3.
So it come down to these three:

[GA-H57M-USB3]("http://www.gigabyte.com.tw/Products/Motherboard/Products_ComparisonSheet.aspx?ProductID=3307")		$174.0 [may be able to get for this price]
[P7H55D-M EVO]("http://www.asus.com/product.aspx?P_ID=LZtx6p7WKTP77rsk&templete=2")		$179.3 [definitely can get for this price]
[P7H57D-V EVO]("http://www.asus.com/product.aspx?P_ID=CadI5xNLwMYopFyJ&templete=2")		$292.6 [definitely can get for this price]

The last is ATX....
It does have SATA6G & USB3 but is substantially more than the other two.

I've realised that SATAII's "real world" limit is about 300MB/s anyway. 
I'm not aware of any 30-40GB SSD's that could reach that limit, even at sustained read speeds. 
So it's no big loss, when S6G does filter-down to H5x mATX boards, I can always sell & upgrade.

So these are my finalist parts (in AUD $):
************************************
approx $154 1x Intel Core i3-530
approx $179 1x [GA-H57M-USB3]("http://www.gigabyte.com.tw/Products/Motherboard/Products_ComparisonSheet.aspx?ProductID=3307") or [P7H55D-M EVO]("http://www.asus.com/product.aspx?P_ID=LZtx6p7WKTP77rsk&templete=2")
approx $145 [G.Skill]("http://www.umart.com.au/pro/products_review.phtml?id=10&bid=2&id2=153&sid=49311") 2x 2GB DDR3 1600Mhz (PC-12800)
Storage Sub-sys:
approx $312 3x 1TB Samsung F3? ........................... [content storage & BU, may not bother w/RAID]
___________
Total =  $790
---------------

Can I get some thoughts on this **_please_**!
Would you slot something different in?

---

### Post by jalyst on 2010-01-28
gee, what a great ****** community, adios...

---

