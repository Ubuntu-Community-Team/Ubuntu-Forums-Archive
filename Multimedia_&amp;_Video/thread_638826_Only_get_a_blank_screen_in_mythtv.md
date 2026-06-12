---
title: "Only get a blank screen in mythtv"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-12-12
Hi,

I am trying to setup mythtv in my ubuntu.
* mythtv 0.20
* ubuntu 7.10
* Hauppage 950 WinTV HVR
* ATI card 


I think I have all the drivers for my tv-tunner setup correctly since I am able to watch TV with another program (TVTime).  

And I think mythtv can talk to my tv-tuner too. Since when I tried to scan channels, it does find some channels.

However, when I go to mythtv-frontend and watch live-tv, I only get a blank screen.

Can you please tell me how can I trouble shoot my problem?

---

### Post by Mizzou_Engineer on 2008-01-02
I get that also. I was thinking that it might have been related to Xvideo as Totem had a similar type of problem with Xvideo until I installed the latest ATi drivers (8.433.1-1) rather than the old 8.37 ones that are in the normal repos. That fixed Totem and VLC and anything else that uses Xvideo, but it did not seem to help MythTV. 

Here are my specs:

Ubuntu 7.10 amd64
MythTV 0.20.2-0ubuntu10.1
Hauppauge WinTV PVR-150 (ivtv driver loads according to dmesg, scanning for channels worked)
ATi x1900GT GPU (AMD fglrx 8.433.1-1 driver)

EDIT: The solution is to select "MPEG encoder: PVR-x50" as the card type in mythtv-setup. The default is "Analog V4L card" and this does not work with Hauppauge MPEG-2 encoder cards like the PVR-150/350 series and probably your 850 series as well.

---

