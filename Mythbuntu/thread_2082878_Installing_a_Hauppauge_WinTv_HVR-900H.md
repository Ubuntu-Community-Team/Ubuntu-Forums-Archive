---
title: "Installing a Hauppauge WinTv HVR-900H"
date: 2012-11-10
forum: Mythbuntu
---

### Post by langner on 2012-11-10
Hi All, 

I'm trying to install the HVR-900H (usb) into MythTV v0.25 - ubuntu 12.04. I have put the  'xc3028L-v36.f' in the firmware folder, as listed on linustv.org, but the back end says it fails to start. 

I have used lsusb and it has found it and dmesg (but I don't know what I'm looking at with this one).  

If anyone knows a good step by step help file it would be very appreciated. 

Thanks in advance 

Matthew

---

### Post by nickrout on 2012-11-11
> **langner said:**
> Hi All, 

I'm trying to install the HVR-900H (usb) into MythTV v0.25 - ubuntu 12.04. I have put the  'xc3028L-v36.f' in the firmware folder, as listed on linustv.org, but the back end says it fails to start. 

I have used lsusb and it has found it and dmesg (but I don't know what I'm looking at with this one).  

If anyone knows a good step by step help file it would be very appreciated. 

Thanks in advance 

MatthewHave you set up mythtv with mythtv-setup? Until you do, the backen won't start.

---

### Post by langner on 2012-11-11
Hi,

The backend has been set up (along with the frontend, same machine) as I have two freesat (UK) cards working fine. 

I have found some sites saying that I have to install the usb stick for it to work but it is unclear to me how this is done. Or do I need to install it at all? 


Matthew

---

### Post by langner on 2012-11-11
Oh, more info.

This is a dedicated machince - mythbuntu 12.04

---

### Post by langner on 2012-11-11
> **langner said:**
> ......but the back end says it fails to start.

It say this in the capture card section of the backend when you try to add a new one. You know the place where you can choose v4l and dvb. 

I'm selecting v4l or is this not right? 

Ps all options at this point, card/usb/mpeg2, says it  fails to start.

---

### Post by jksj on 2012-11-11
Select dvb not v4l.
High mixing freesat and freeview is none trivial.
The best guide I found was [http://www.gavsworld.net/?page=The%20Server/MythTV%20Backend%20Setup.]("http://www.gavsworld.net/?page=The%20Server/MythTV%20Backend%20Setup")

Even though my freesat card is PCI and freeview USB I had to use UDEV rules to fix the IDs at boot. Otherwise the identities of the cards were likely to switch at each boot. You will also probably end up using guide data from XMLTV as the system will probably be unreliable with live EIT data. As it is bound to conflict between the two sources as they update at different times.
Having said all that the combination works fine once you put in the effort, follow the above guide.

---

