---
title: "fresh 14.04.1 install, Nanostick 290e"
date: 2015-04-29
forum: Mythbuntu
---

### Post by mattshaw on 2015-04-29
Hi guys

I have a fresh install of 14.04.1, with all updates to 14.04.2. I have 3 x DVB-T2 nanostick 290e tuners, which dont appear to be working too well.

I am getting eit lookups in the epg, but cannot get a picture when i try LiveTV on the frontend. Its not an issue with VDPAU, i also have 2 x dvb s2
tuners, and LiveTV (sd and hd) and recording is fine on them.

I have done a lot of google on this, and it appears that the USB Nanostick 290e's are ok immediately after a reboot, but then start to have problems
after unsure durations.

I have also seen posts that say later kernels are good, ie. 3.15/3.16. My current latest kernel after the 14.04.2 updates is 3.13.0.49. I have read
that it is a good idea to update to the latest "hardware entitlement stack". I also see that 14.04.10 and later *buntus are available.

How do I update my system so I can get this Hardware entitlement stack, and get a later kernel or dist-release ???

Matt

---

### Post by novellahub on 2015-04-29
Here is a wiki explanation on enabling the Enablement Stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by mattshaw on 2015-04-29
Thanks for that novellahub, had a read through, but dont really get it. With Mythbuntu am I running desktop or server ubuntu,
and which set of commands should I enter, dont really understand all this stuff.....



> **novellahub said:**
> Here is a wiki explanation on enabling the Enablement Stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by novellahub on 2015-04-29
You are running desktop with Mythbuntu. 

```
sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic
```

---

### Post by mattshaw on 2015-06-11
I am yet to try this, real life gets in the way. But I am interested in communicating with any nanostick 290e users. Can you please comment on this ???

Thanx

---

### Post by roburk on 2015-06-18
290e user here and happy to help if I can.
   
  Sounds a bit like the USB power down (sleeping) issue, I had a similar problem with an old Hauppauge PCI / USB card quite a while back.

   

  It would be good if we could see your dmesg output at a point where the problem has already occurred.
   
  I take it the problem effects all three 290es? How are they attached? USB2 /USB3? Mixed? Are you Going through a USB hub? (is it externally powered?)

   
  Rob

---

### Post by mattshaw on 2015-06-22
I haven't had time to investigate further, I might have time for a play tonight, but can answer your questions :

I only have one 290e connected at the moment, until I am confident that it works 100%, I will then connect the others.

The one I am using is directly connected to the usb port on the desktop case, no hub etc....I think the ports are usb 2

---

### Post by mattshaw on 2015-10-20
Havent had time to look at this till last night, been getting by with my 2 x freesatHD cards. Anyway, shut down and restarted my mythtv server, after a couple of weeks upgrades. Anyway, thought I would try LiveTV on the 290e, and VOILA it works !!!! I then scheduled a couple of recordings....all worked fine. I will leave it alone for  a while, and schedule a few recordings over the next week or so, and report back. Then on to try the other two 290e's, and if all is good, I will delete all capture cards, and add them in one at a time, to get nice Tuner numbers. Another issue, when adding tuners it always presumes that you want a virtual tuner, and allocates the next tuner number. As I have 5 capture cards I dont really need the virtual tuners, but mythtv is reserving the next tuner number. As I said I would like a nice clean setup and tuner numbers, does anyone know how to stop this behaviour ?????

---

### Post by tobiz on 2015-10-22
I'm about to do a fresh install of mythbuntu 14.04.2 as a way of upgrading my 12.10 version which has 2x290e usb tuners. The old 12.10 system worked ok but a mythweb problem has resulted in it being totally trashed hence decision to go fresh install.  I'm interested to hear how you get on. I will let you know how I get on but my past experience of fresh installs (since my trusty still running 8.10 system) is it takes ~2wks to get everything to how it was, so may be some time before I report back. Just to illustrate the sort of curved ball problems you get: I tried to download the 14.04.2 torrent but all I get is "Stalled. Unable to contact tracker". Yes I could (and will) go for the straight iso download but this is only step 1! (BTW the signature is spec of old still working 8.10 system)

---

