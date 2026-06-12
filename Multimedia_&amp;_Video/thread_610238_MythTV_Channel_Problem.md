---
title: "MythTV Channel Problem"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by 3givor on 2007-11-11
I have been using MythTV for about seven months now and am very happy with it, except for one thing. Ever since rebuilding my box to use the 0.20.2 release under Feisty I can't change to any channels above 13. I thought maybe the packages for Gutsy would fix things, so yesterday I rebuilt the system on Gutsy and installed MythTV from packages (I did not use the Mythbuntu CD), but the problem persists. If it wasn't for this and the blank screen after ten minutes the system would be a far better option than any other PVR out there. Can someone help me, please?

---

### Post by Fire_Chief on 2007-11-11
I'm experiencing the same issue with a new Mythbuntu installation. Everything is working fine except for the channel changing. All channels above 13 display snow on the screen.

---

### Post by 3givor on 2007-11-12
I should have mentioned that I am running MythTV on an AMD athlon 64 with an ASUS P1-AH1 PC and that my tuner is a PVR-150 with grey remote. I installed the AMD64 alternate CD as my base system, and have nothing else running on the box.

---

### Post by JasonF on 2007-11-12
Re-run mythtv-setup and make sure to use the correct frequency ranges for your region. It sounds like you have selected us-broadcast instead of us-cable (assuming you are in the US).

---

### Post by barney_1 on 2007-11-12
Just to clarify, when you start the backend setup program go to:

3. Video Sources --> Channel Frequency Table:

Set that to US-cable as JasonF said.

---

### Post by 3givor on 2007-11-14
Finally had a chance to run setup again and change the frequency table. This worked like a champ. Thanks for everyone's help.

---

