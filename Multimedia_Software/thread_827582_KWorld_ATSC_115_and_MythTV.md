---
title: "KWorld ATSC 115 and MythTV"
date: 2008-06-12
forum: Multimedia Software
---

### Post by mastermindg on 2008-06-12
I have purchased 2 KWorld ATSC 115 cards specifically because of their compatibility. They are great cards and I look forward to putting them to work.

I am able to scan channels on the 1st card (/dev/video0) but not the second, but I can deal with that later. I have configured the 1st card for V4L, setup the card, the source, the inputs, and the channels. However, when I pull up the frontend it is showing that both cards are unavailable.

When I look at the backend log it says:

ERROR: no valid capture cards are defined in the database.

Obviously, 1 of the cards must be somewhat valid or it wouldn't have been able to scan channels in the first place.

Can somebody please explain what I am missing?

---

### Post by mastermindg on 2008-06-15
I have removed one of the cards and now have one remaining.

I am running MythTV on Hardy with 1 K-World ATSC 115 card. I am able to set the card up in the backend, INCLUDING scanning channels. When I open up the frontend, it is still showing Tuner not available.

I am able to watch TV with tvtime. All modules have been loaded. This seems to be an issue with MythTV.

---

### Post by mastermindg on 2008-06-22
Thanks for everybody jumping up at once on this.

This is a rather stupid issue, since other applications are able to access video devices without direct permission.

MythTV needs permission to access /dev/video...(0,1,...)

Add MythTV user to video group and
chown root:video /dev/video(0,1,...)

---

### Post by GhettoYhetti on 2008-06-22
mastermindg . . . was the Kworld card autodetected and really that easy?

---

### Post by kwisher on 2008-07-22
Hello All,

I am in desperate need of advise and guidance.

I am currently building my first MythTv system. I have successfully installed Mythbuntu 8.04.1 and have Myth partially working with my two Kworld-115 cards. I live in North Central Indiana and have Comcast cable. I receive analog channels 2 through 68 and also subscribe to the very basic digital stations to receive a discount on cable internet. The digital channels require a set-top-box. I don't believe I receive any HD channels for free and I'm not really interested in HD at the moment because I don't have a full HD TV. The STB has two Firewire ports.

My goal is to be able to use my Myth system to replace my current dual tuner DVR set-top-box.

From my cable wall outlet I have a 4-way splitter. From the splitter I have one feed directly to the top port (farthest from motherboard) of one tuner card. One feed to the input on STB. From STB output I feed the other tuner card to the top port of the second tuner card. With this setup I can view my analog channels and have channel listings and program guide info from Schedules Direct. Is this the correct routing for analog & digital cable?

My problem seems to be with the way the two tuner cards are setup in Myth. I cannot add the cards as a DVB device for the digital channels. Can someone please provide instructions on how I can get all four tuners working so that I can watch & record at the same time?

TIA,

kwisher

---

### Post by kwisher on 2008-07-27
Bump

---

