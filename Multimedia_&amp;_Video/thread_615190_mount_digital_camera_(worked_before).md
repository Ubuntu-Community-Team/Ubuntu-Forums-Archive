---
title: "mount digital camera (worked before)"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by prezbedard on 2007-11-16
ok when I was using 6.06 I ran into this issue

[http://www.computechgroup.com/?p=334](http://www.computechgroup.com/?p=334)

however before that my computer would mount the camera so I could browse it like a drive.

I upgraded to Feisty within the past week and good news is my camera works but it only will launch for me to import the images and not actually mount the camera. I read that this is because it it using a ptp (spelling?) protocol to transfer the images. Isn't there a way to mount it if it did work like that at one point?

its a canon powershot sd110

Thanks,

---

### Post by MrFSL on 2007-11-16
Odds are there is a setting on the camera to change the way it connects to the computer.

...at least that is how it works on my Canon, Kodak, and Nikon cameras.

---

### Post by prezbedard on 2007-11-16
I did check that but couldn't really find anything that related except video setting. Also I haven't changed any kind of setting so I don't see how it could be an issue if there is a setting.

---

### Post by MrFSL on 2007-11-16
> **prezbedard said:**
> I did check that but couldn't really find anything that related except video setting. Also I haven't changed any kind of setting so I don't see how it could be an issue if there is a setting.

The settings change for me once after a battery change.

---

### Post by prezbedard on 2007-11-16
I can't seem to find any kind of setting that would do this.

---

### Post by fyo on 2008-01-10
I can confirm the behavior reported by the OP.

Earlier versions of Ubuntu (6.06) would mount the camera. That no longer happens (automatically, anyway) with feisty and gutsy.

**This is not a camera issue!**

The package gphotofs can restore the functionality, but I've found it a real hassle to use.

EDIT: Note that some cameras use the USB mass storage device class and are thus mounted regardless of Ubuntu version, cameras (like all the Canons I've come across) that use the PTP protocol are no longer mounted.

---

### Post by prezbedard on 2008-01-10
> **fyo said:**
> I can confirm the behavior reported by the OP.

Earlier versions of Ubuntu (6.06) would mount the camera. That no longer happens (automatically, anyway) with feisty and gutsy.

**This is not a camera issue!**

The package gphotofs can restore the functionality, but I've found it a real hassle to use.

EDIT: Note that some cameras use the USB mass storage device class and are thus mounted regardless of Ubuntu version, cameras (like all the Canons I've come across) that use the PTP protocol are no longer mounted.

Any reason behind changing the way it worked? I find it much simpler to browse my camera to copy and paste photos I want then have to be restricted by an app to do it.

---

### Post by phaed on 2008-04-13
I have a Canon PowerShot SD 870 IS.  A few weeks ago, I could plug it in and it would be detected, mounted, and displayed in Nautilus.  Now it doesn't do that.  I see with dmesg that it is being recognized, but not mounted.

However, I found that I can import my photos using F-Spot (/usr/bin/f-spot-import).

You might try that.

---

### Post by prezbedard on 2008-04-13
> **phaed said:**
> I have a Canon PowerShot SD 870 IS.  A few weeks ago, I could plug it in and it would be detected, mounted, and displayed in Nautilus.  Now it doesn't do that.  I see with dmesg that it is being recognized, but not mounted.

However, I found that I can import my photos using F-Spot (/usr/bin/f-spot-import).

You might try that.

ya thats what I do now. Though it kind of sucks. I liked it better when I could just browse the camera and do a copy and paste. I'm one, like many I would think,  who doesn't need an app to do it for me

---

