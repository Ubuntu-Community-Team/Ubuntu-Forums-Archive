---
title: "I've failed and need assistance..."
date: 2009-02-05
forum: Mythbuntu
---

### Post by nicoloks on 2009-02-05
I can feel the beginnings of real frustration seeping in. I have two weeks holiday and in I was hoping to have three Antec Fusion Remote based HTPC's for a few mates and myself setup on Mythbuntu 8.10 before the end of week one. Doesn't look like that is going to happen now as I am still stuck on HTPC No.1 at the end of week one with no end in sight.

To summarise, my problems are;

1. Two of the three HTPC's are based on the Asus M3N78-VM mATX board which has both HDMI and optical S/PDIF outputs. One of my mates has an older receiver that only has optical/coaxial S/PDIF inputs (no HDMI) and I need to be able to configure the on board soundcard to act as a digital pass through. While I think I have managed to get this to work over HDMI (I don't have a HDMI receiver either), I just can't get anything to come out of the S/PDIF interface. Even with the BIOS set to push the HD audio out the S/PDIF interface it still seems to only come through the HDMI. I've found nobody with this exact board who has manged to get the S/PDIF working, so I moved on.

2. All three HTPC's are being built in a Antec Fusion Remote case which have the Soundgraph iMon IR/LCD (15c2, 0x0038). There is no doubt there is plenty of information about getting this case to work, however it is all appears so cut and paste like (at least to a new Linux user) with link reference to instruction here and there with updates on the 57 post of a 10 page forum thread and changing versions of Mythbuntu, patches and associated libraries that I honestly have no idea what I am meant to do. Following [this guide]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html") I did manage to get the RM200 remote that came with the Antec cases working, sort of. The d-pad worked, along with most of the buttons that surround it, and each of the numerical keys worked. I say worked because in my wisdom I thought the non working keys where because I missed a step and went through each of them again and now nothing works (I have no lcd* or lirc* in /dev).

3. Similar to above, I haven't been able to get the LCD or volume knob working. I thought I was almost there as I managed to get LCDproc loaded and I got a message saying "Thanks for using LCDproc & Linux!" on the LCD. I don't seem to be able to get either of these items fullly working though.

Very long story short I promised my mates I'd have their HTPC's ready for the weekend, which just isn't going to happen without some help which I am now begging the knowledgeable MythBuntu community for. If it gives incentive at all I might be able to arrange a small paypal payment for anyone willing to log into the first system and "fix" the above problems. From there (hopefully) I should be able to see the error of my ways and get the others working. I really, really, really want to use Mythbuntu, however if I can't get this sorted by next week I'll have no choice but to format and load up Windows MCE. It might be made by the devil, but at least I don't have to go through hell and back to get it to work (stupid hardware vendors not giving linux the time of day :( , apart from Nvidia, they rock :) ).

---

### Post by tgm4883 on 2009-02-05
> **nicoloks said:**
> I can feel the beginnings of real frustration seeping in. I have two weeks holiday and in I was hoping to have three Antec Fusion Remote based HTPC's for a few mates and myself setup on Mythbuntu 8.10 before the end of week one. Doesn't look like that is going to happen now as I am still stuck on HTPC No.1 at the end of week one with no end in sight.

To summarise, my problems are;

1. Two of the three HTPC's are based on the Asus M3N78-VM mATX board which has both HDMI and optical S/PDIF outputs. One of my mates has an older receiver that only has optical/coaxial S/PDIF inputs (no HDMI) and I need to be able to configure the on board soundcard to act as a digital pass through. While I think I have managed to get this to work over HDMI (I don't have a HDMI receiver either), I just can't get anything to come out of the S/PDIF interface. Even with the BIOS set to push the HD audio out the S/PDIF interface it still seems to only come through the HDMI. I've found nobody with this exact board who has manged to get the S/PDIF working, so I moved on.

2. All three HTPC's are being built in a Antec Fusion Remote case which have the Soundgraph iMon IR/LCD (15c2, 0x0038). There is no doubt there is plenty of information about getting this case to work, however it is all appears so cut and paste like (at least to a new Linux user) with link reference to instruction here and there with updates on the 57 post of a 10 page forum thread and changing versions of Mythbuntu, patches and associated libraries that I honestly have no idea what I am meant to do. Following [this guide]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html") I did manage to get the RM200 remote that came with the Antec cases working, sort of. The d-pad worked, along with most of the buttons that surround it, and each of the numerical keys worked. I say worked because in my wisdom I thought the non working keys where because I missed a step and went through each of them again and now nothing works (I have no lcd* or lirc* in /dev).

3. Similar to above, I haven't been able to get the LCD or volume knob working. I thought I was almost there as I managed to get LCDproc loaded and I got a message saying "Thanks for using LCDproc & Linux!" on the LCD. I don't seem to be able to get either of these items fullly working though.

Very long story short I promised my mates I'd have their HTPC's ready for the weekend, which just isn't going to happen without some help which I am now begging the knowledgeable MythBuntu community for. If it gives incentive at all I might be able to arrange a small paypal payment for anyone willing to log into the first system and "fix" the above problems. From there (hopefully) I should be able to see the error of my ways and get the others working. I really, really, really want to use Mythbuntu, however if I can't get this sorted by next week I'll have no choice but to format and load up Windows MCE. It might be made by the devil, but at least I don't have to go through hell and back to get it to work (stupid hardware vendors not giving linux the time of day :( , apart from Nvidia, they rock :) ).

For the antec case, try this link.  I used it on mine and it worked fine for 8.10   [http://wiki.foxmediasystems.com/index.php/Antec_Fusion_v2_Black_LCD](http://wiki.foxmediasystems.com/index.php/Antec_Fusion_v2_Black_LCD)

---

### Post by nicoloks on 2009-02-06
Thanks for the reply TGM. Seems most of the guides out there are targeted towards this 15c2:ffdc model. I think my issue is I have the 15c2:0038 model, and the guide I linked to is the only one I've found that mentions my model. A lot of the contents of the guide you linked to look very familiar, but at least it is all in one spot! I'll give it a go and see how I get on. Cheers.

---

### Post by nicoloks on 2009-02-06
No cigar unfortunately, and after 6 hours on this today I think I'm done for the day. I think I start with a fresh install of 8.10 next week as god knows what is what on this sytem now, and if that doesn't work I'll reluctantly be headed back to the Windows camp.

---

