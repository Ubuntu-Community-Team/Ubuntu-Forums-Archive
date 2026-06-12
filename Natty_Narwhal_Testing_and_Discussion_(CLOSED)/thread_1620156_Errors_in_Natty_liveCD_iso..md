---
title: "Errors in Natty liveCD iso."
date: 2010-11-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-11-12
Burning with Disk Creator gave me following error;-

mounting aufs on /root failed: No such device aufs mount failed

And Unetbooting:-

gconf-sanity-check-2 exited with status 256

I am using Nov-12 iso on dell inspiron E1505/6400

Thanks.

---

### Post by VMC on 2010-11-12
Read my [topic]("http://ubuntuforums.org/showpost.php?p=10108604&postcount=5") on the AUFS now being fixed. Use the latest ISO, from "12-Nov-2010 16:33". This ISO is the second one for 11/12. You must have downloaded the earlier one.

---

### Post by donniezazen on 2010-11-12
> **VMC said:**
> Read my [topic]("http://ubuntuforums.org/showpost.php?p=10108604&postcount=5") on the AUFS now being fixed. Use the latest ISO, from "12-Nov-2010 16:33". This ISO is the second one for 11/12. You must have downloaded the earlier one.

I had yesterdays image which i updated using zsync. Let me try a fresh Nov-12 16:33 image.

---

### Post by donniezazen on 2010-11-13
Tried the Nov-12.1 image ubuntu loads up to its blank wallpaper and nothing happens then.

---

### Post by VMC on 2010-11-13
Its not ready yet. It may not work correctly until alpha 1. 
I Just keep the iso zsynced along the way. If you follow the [Natty-changes]("https://lists.ubuntu.com/archives/natty-changes/") you can observe the progress.

---

### Post by cpatrick08 on 2010-11-15
the live nov 14 iso works great i am typing this message from inside the iso

---

### Post by oboedad55 on 2010-11-15
> **cpatrick08 said:**
> the live nov 14 iso works great i am typing this message from inside the iso

Ditto, I think I will install it just for laughs.

---

### Post by VMC on 2010-11-15
Those that find the ISO to work, what is your video card?

This is mine and it doesn't work:

 ```
VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
```

---

### Post by oboedad55 on 2010-11-15
Oh well, the installer crashes.

---

### Post by arpanaut on 2010-11-15
Live-CD boots to desktop albeit very slowly from usb. Throws errors on shutdown.
Will try to install later today when I have time to pay attention. 

```
VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
```

---

### Post by VMC on 2010-11-15
> **arpanaut said:**
> Live-CD boots to desktop albeit very slowly from usb. Throws errors on shutdown.
Will try to install later today when I have time to pay attention. 

```
VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
```

Thanks for the video id. I get to a desktop but nothing there, just a purple screen. No panels.

---

### Post by sparker256 on 2010-11-15
> **VMC said:**
> Thanks for the video id. I get to a desktop but nothing there, just a purple screen. No panels.

I got the same and then I did

Ctrl + Alt + F1

Then

sudo service gdm restart

Got the desktop at that point.

Bill

---

### Post by donniezazen on 2010-11-15
> **sparker256 said:**
> I got the same and then I did

Ctrl + Alt + F1

Then

sudo service gdm restart

Got the desktop at that point.

Bill

This helped me get the top panel but i still can't get bottom panel. Right click on the desktop is not working. And also there is no titlebar in any of applications or windows.

I have tried this on nov-15th ISO and dist-upgrading maverick to natty.

---

### Post by VMC on 2010-11-15
> **soham_1207 said:**
> This helped me get the top panel but i still can't get bottom panel. Right click on the desktop is not working. And also there is no titlebar in any of applications or windows.

I have tried this on nov-15th ISO and dist-upgrading maverick to natty.

That's funny. I got the bottom panel but not the top. I just created another panel, and moved it to the top.

 I had to add all the title bars along the way.

---

### Post by donniezazen on 2010-11-15
> **VMC said:**
> That's funny. I got the bottom panel but not the top. I just created another panel, and moved it to the top.

 I had to add all the title bars along the way.

Do you have a working desktop? Are you able to right click? Do you have icons on desktop?

---

### Post by VMC on 2010-11-15
> **soham_1207 said:**
> Do you have a working desktop? Are you able to right click? Do you have icons on desktop?

Yes, but entering "sudo service gdm restart", was a bit weird. I clicked Try Ubuntu, then from a VM entered the above message, only to have it come back to the two options, Try Ubuntu or Install Ubuntu. I then clicked  Try and at that point I had a bottom panel.

So its not right b a long shot. Maybe tomorrow will bring more updated files. 

The only reason I'm pushing this, is to find out if I can run Unity in all its glory.

---

### Post by donniezazen on 2010-11-16
**NOV 16th UPDATE**

I do get the top and bottom panel but i can't use the right click. None of the windows have titlebar.

---

