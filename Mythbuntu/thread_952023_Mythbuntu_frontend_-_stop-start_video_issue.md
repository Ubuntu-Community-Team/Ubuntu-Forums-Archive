---
title: "Mythbuntu frontend - stop-start video issue"
date: 2008-10-18
forum: Mythbuntu
---

### Post by al_dente on 2008-10-18
I've successfully installed Mythbuntu on a PC - and it seems to be working fine. Spec as follows...
P4 2400 CPU
80 Gb hard drive
1Gb RAM
Onboard Intel 82845 graphics
Hauppauge Nova-T-USB2 DVB tuner
Dlink DWL-G122 USB wireless adapter

However, I thought I'd setup my desktop PC with MythTV frontend, so that I can watch TV on that too. I can connect to the backend successfully, but the video and audio output is stop-start, making it impossible to view anything. It plays a second, pauses a second, plays a second etc...

My desktop PC is a better spec than the backend PC - with a better graphics card too (AGP Nvidia 6200).
I'm using wifi to network the PCs (through my DD-WRT router). Is it possible that the bandwidth between the two PCs is not high enough?

I was wondering if my Dlink USB adapter is working at wireless b or g mode (it's supposed to support g). Does anyone suggest a good/easy way to test this?

Any other suggestions/comments?

Thanks

Al

---

### Post by ian dobson on 2008-10-19
Hi,

I wouldn't recommend using WiFi for your frontend. I imagine that's your problem. To stream video you need a constant bandwidth.

Try copying a large file (1-2Gb) from your backend to your frontend and time how long it takes, you can then work out what bandwidth you have.

You don't say what graphic card you have. Are you using the generic drivers or the ATI/NVIDIA drivers? If your using the NVIDIA rivers have you enabled xV on the mythtv frontend setup (This will enable Hardware decoding on you graphic card).

Regards
Ian Dobson

---

### Post by volkswagner on 2008-10-19
On the backend select "stream all from backend".  This will reduce bandwidth requirements. 
If it is not a bandwidth issue, you may try other playback profiles.

---

### Post by al_dente on 2008-10-19
Well I tried copying a file from the frontend to the backend and it only transferred at 12.5KB per second! This is amazingly slow - so I should think this is the cause of the issue.

I'll try the "stream all from backend" suggestion though and see if it helps - however, i think I'm going to have to resolve my networking issues first if I'm going to get anywhere I think.

Thanks for your comments.

Al

---

