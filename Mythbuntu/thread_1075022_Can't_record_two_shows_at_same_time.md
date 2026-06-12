---
title: "Can't record two shows at same time"
date: 2009-02-19
forum: Mythbuntu
---

### Post by The Odometer on 2009-02-19
This seems to be a trivial issue to me--but I can't figure it out. I have a Pinnacle 800i tuner that I am using strictly for its ability to view ClearQAM. I also have an PVR-150 in my box. The PVR-150 will only view the channels that my cable provider broadcasts via analog (1-20). My Pinnacle card will view all of my channels.

The issue is that any time I try to record two shows at once, MythTV wants to use the Pinnacle card no matter what. Therefore, I can't get two shows to record at the same time, even if one is on the analog channels, while another is on the digital channels.

Any ideas as to what is going on? I'm new to using multiple tuners--but figured I'd use what I had on hand..and I'm fairly certain it can be done. I've tried to set up each show with a preferred input, but it just ignores it and does what it wants. I can view shows using the other tuner while one is recording, so I know it is possible. Thanks!

---

### Post by utar on 2009-02-20
I'm interested in this two as I have just bought a second tuner, although it not installed yet.

As a matter of interest have you set a different video source for both cards in the backend rather then using the same one?



Utar

---

### Post by klc5555 on 2009-02-20
> **The Odometer said:**
> This seems to be a trivial issue to me--but I can't figure it out. I have a Pinnacle 800i tuner that I am using strictly for its ability to view ClearQAM. I also have an PVR-150 in my box. The PVR-150 will only view the channels that my cable provider broadcasts via analog (1-20). My Pinnacle card will view all of my channels.

The issue is that any time I try to record two shows at once, MythTV wants to use the Pinnacle card no matter what. Therefore, I can't get two shows to record at the same time, even if one is on the analog channels, while another is on the digital channels.

Any ideas as to what is going on? I'm new to using multiple tuners--but figured I'd use what I had on hand..and I'm fairly certain it can be done. I've tried to set up each show with a preferred input, but it just ignores it and does what it wants. I can view shows using the other tuner while one is recording, so I know it is possible. Thanks!

I'm not sure I understand what the symptoms are. Is it that whenever you set up 2 shows to record simultaneously, Mythtv is trying to record both shows simultaneously through the Pinnacle, which can handle only one signal (analog or digital) at a time?

If so, first of all, go into the backend setup for the digital tuner on this card and change max recordings from "2" (default) to "1". Also be sure that "Open DVB card on demand" is checked. Now make a group for your Pinnacle card (other than "Generic" -- the Myth backend setup may offer you an option like "DVB0" for the group name) and put both the configured digital Pinnacle tuner and the configured analog Pinnacle tuner into this new non-Generic group, so that Mythtv will know that they are part of the same card, and won't schedule them on top of each other.

Now, configure two "Video Sources", call one, say, "digital" and call the second, say, "analog". The first will just be used by the digital tuner of the Pinnacle; the second will be used by both the analog half of the Pinnacle and the PVR 150. In "Input Connections", hook "Digital" up to the digital tuner of the Pinnacle and have it scan for QAM; hook the PVR 150 and the analog half of the Pinnacle up to "Analog" and have them scan for their analog channels. 

Now the digital half of the Pinnacle can only see (and attempt to tune to) the QAM stations; the other two tuners can only see (and attempt to tune to) analog stations. Myth will no longer try to tune a tuner to record on a type of station it can't see, nor will Myth try to tune the Pinnacle to two different QAM stations simultaneously, nor try to record from both the digital and analog halves of the Pinnacle simultaneously.

Cheers! :)

---

### Post by The Odometer on 2009-02-20
> **utar said:**
> I'm interested in this two as I have just bought a second tuner, although it not installed yet.

As a matter of interest have you set a different video source for both cards in the backend rather then using the same one?



Utar

Yes, each card has a different video source.

> 
I'm not sure I understand what the symptoms are. Is it that whenever you set up 2 shows to record simultaneously, Mythtv is trying to record both shows simultaneously through the Pinnacle, which can handle only one signal (analog or digital) at a time? 
Yes, that does seem to be the problem.

I've not even set up the Pinnacle as an analog tuner (there's no point in doing so, it will not give me any extra channels). However, I'll definitely try the set up you described--thanks for the help!

---

