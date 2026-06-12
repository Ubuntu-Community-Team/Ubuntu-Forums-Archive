---
title: "Importing Video Camera's Video"
date: 2008-05-10
forum: Multimedia Software
---

### Post by condawg on 2008-05-10
Hi there.
I'm wondering how I get video files from my video camera onto my computer.
When I plug it in, it asks if I want to import photos. I click "Yes," and the videos aren't in there (obviously), but I'd like to get them onto my computer.

They're stored on an SD card in my camera, but I unfortunately do not have an SD card slot on the computer I'm working with.
So I plug the camera in.

I have Kino, but can't figure out how to do it from there.

Keep in mind, I'm not trying to firewire in from a DV tape, I'm trying to get the digital video on there.

Thanks =]

---

### Post by condawg on 2008-05-10
Any takers?
I really need help with this.

Thanks =]

---

### Post by eldragon on 2008-05-10
if i got this right, you got a digital photo camera that can record video on a sd memory card...is this correct?

if thats so, then just browse your desktop for a newly mounted usb drive, navigate with nautilus and copy them manually.

thats they only way i know how to do it :D

---

### Post by condawg on 2008-05-10
> **eldragon said:**
> if i got this right, you got a digital photo camera that can record video on a sd memory card...is this correct?

if thats so, then just browse your desktop for a newly mounted usb drive, navigate with nautilus and copy them manually.

thats they only way i know how to do it :D

Well, no -- it's not a digital photo camera, it's a video camera. A camcorder.

And it doesn't show up on the desktop, but for some reason the videos showed up this time when I plugged it in. Eh.

EDIT: Okay, the videos actually do show up when I plug it in and hit "Import," but when I try and copy the files to my Video folder, it doesn't go.

It says "Copying File 0 Out of 7" and never goes.

EDIT 2: And, of course, 2 seconds after I post that, it goes. -_-

---

### Post by geoffreygrigg on 2009-01-21
Hi there...

I have a quite new Panasonic NV-GS120 Digital Video Camera given to me that records to tape only.

I need to import to Ubuntu. Do you have any idea what software I would use to import to my HDD?

The video camera system comes with disks to do that in Windows - but who want to use windows? Not me!

Will Kino do this? I cannot see how...

Thanks

---

### Post by cmebert on 2009-02-21
i have an older canon optura 40 that i just figured out how to import from.  first i had to use a firewire cable; usb will not allow dv export.  i installed kino and dvgrab as per this post:  [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire).  once i connected the camera and switched it to Play, i started kino with sudo.  in kino, i went to edit/preferences, and my camera showed up in the ieee1394 tab.  from my experience, as long as you have a firewire cable, and start kino with sudo, you shouldn't have any problems.

---

### Post by RedRat on 2009-02-21
> **geoffreygrigg said:**
> Hi there...

I have a quite new Panasonic NV-GS120 Digital Video Camera given to me that records to tape only.

I need to import to Ubuntu. Do you have any idea what software I would use to import to my HDD?

The video camera system comes with disks to do that in Windows - but who want to use windows? Not me!

Will Kino do this? I cannot see how...

Thanks

I am using 8.04 Gnome and the version of Kino that I have will not import HD files via the Firewire port. It will capture regular standard DV though. I guess the HD support will come later. The only way I found to get HD video is to capture it on a Windows machine and then transfer it over to my Linux machine. Kino will edit the HD video though.

---

### Post by DuncanNZ on 2009-02-23
Hi there, I've updated the instructions on [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) and would love it if you could take a look and let me know if you hit any problems. I'll try and help you in this thread.

---

### Post by RedRat on 2009-02-23
> **DuncanNZ said:**
> Hi there, I've updated the instructions on [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) and would love it if you could take a look and let me know if you hit any problems. I'll try and help you in this thread.

Thank you for the link. I downloaded the 1.30 Kino and installed it. I will see if it handles HD downloads. Your instruction look OK to me. Even under the older version of Kino, I could control the camera functions so I think I have most of the stuff in order. It appears that 8.10 is still a bit behind times. I think I will stick with 8.04 for a bit more time.

---

### Post by euriconeto on 2009-05-14
Hi There,
I have a related question, but not quite the same... Actually two:
1 - How do I edit vob files already in my computer using Kino (or similar app)?;
2 - How do I burn the files I saved in HD back into DVD?
Cheers!

---

### Post by RedRat on 2009-05-14
> **euriconeto said:**
> Hi There,
I have a related question, but not quite the same... Actually two:
1 - How do I edit vob files already in my computer using Kino (or similar app)?;
2 - How do I burn the files I saved in HD back into DVD?
Cheers!

As far as VOB files are concerned, they are mpg files. If you have to, just replace the vob extension with mpg and edit away. That is how I have done it. However, keep in mind that if you are attempting to edit a commercial DVD that you have "backed up" there are copyright concerns. No that we have that out of the way, you will find that some of these vob files are quite large, so you need a bit of horsepower in your computer.

In terms of Linux, your second question is a good one! I have no answer for that one since I don't have a Blue Ray burner (they are bit pricey still) and don't know what the structure of the BluRay DVD might be. Perhaps others here might enlighten us.

---

