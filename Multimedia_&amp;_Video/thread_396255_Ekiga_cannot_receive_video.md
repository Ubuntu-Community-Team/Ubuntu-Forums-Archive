---
title: "Ekiga cannot receive video"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by Jonam on 2007-03-29
I have tried to get Ekiga (Ubuntu PC) working with Netmeeting (Windows PC) within my home network using H323. I can send video from Ekiga to Netmeeting but cannot see the remote camera at the Netmeeting end. Ekiga does not appear to start the H261 codec for reception. 

I have checked that I have all the necessary libraries, enabled video support in Ekiga and also looked at the Ekiga website but could not find any solution to this problem.

The output of Ekiga's log is:

23:09:15 Connected with Home_PC using Microsoft® NetMeeting®	3.0	181/21324
23:09:16 Opened codec H261 for transmission
23:09:16 Opened SBLive! Value [CT4832] for playing with plugin ALSA
23:09:16 Opened codec PCMU for reception

Would appreciate any suggestions on how to fix this.

Jonam

---

### Post by drpaul on 2007-03-29
Does the video work if you connect to another Ekiga user through the Ekiga server?

Paul

---

### Post by Jonam on 2007-04-03
Haven't tried that yet. I'll give it a go and post back.

Jonam

---

### Post by Jonam on 2007-04-06
Tried a video conference  via the Ekiga server and it worked (mostly). Receiving audio was fine but I was unable to send even though the mic was working properly through ALSA mixer. Video worked both ways. However, it still does not work with Netmeeting on my home LAN.

Jonam

---

### Post by balak on 2008-01-02
Jonam, Did you ever get this working? I am in the same situation (can't see remote desktop in netmeeting)

any help or pointers will be much appreciated!

thanks!

---

