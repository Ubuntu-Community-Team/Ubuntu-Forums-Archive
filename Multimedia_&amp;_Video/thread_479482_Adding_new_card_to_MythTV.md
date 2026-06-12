---
title: "Adding new card to MythTV"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by cdersham on 2007-06-20
Ok, i have a fresh install of ubuntu 7 and mythTV.. i followed the instructions from this site....
My problem is when i run the Backend setup, i can't seem to get my card added.  

I have a Hauppauge WinTV PVR-150
I make sure i select all the correct settings....acording to the instructions... and when i click finish i do not see a card.

Should i?

As i continue the install when i get to input connections i don't see anything. its blank.

I know my card is working cause when i run mplayer /dev/video0 i can see live tv

I am stumped.... any suggestions or ideas?  should i see the capture card listed under capture cards, after
i add the card??

I am sure it is something simple

Thanks

Chris

---

### Post by cdersham on 2007-06-20
bump

---

### Post by bla2000 on 2007-07-14
I have the same problem.  I've just installed a 7.04 and followed [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop) but when I try to add my 2 cards they do not appear.  The 2 cards are a pvr150 and pvr250.  In the "Capture Card Setup" I set the card type to "Mpeg 2 encoder card (pvr-x50, pvr500) and the "Probed info:" displays the correct card name which is either "Haupauge WinTV PVR-150 [ivtv]" or "Haupauge WinTV PVR-250 [ivtv]" depending on which "Video device:" I select.

---

### Post by bla2000 on 2007-07-14
I noticed that nothing else was being saving.  So I'm going to try to recreate the mythconverg database following the instruction in the section "Mythbackend setup not saving settings" on [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting).

---

### Post by bla2000 on 2007-07-14
Re-installing the mythconverg database worked.  Mythtv is fine now.

---

