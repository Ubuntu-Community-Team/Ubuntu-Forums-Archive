---
title: "My sound card isn't detected."
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by Quillz on 2007-01-09
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```Are there any Linux supported drivers for this sound card?

---

### Post by Quillz on 2007-01-10
> **Quillz said:**
> ```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```Are there any Linux supported drivers for this sound card?
After a bit of research, I came across  alsaconf, which detected my sound card and claimed that it made all the proper configurations, but after a reboot, I'm still not hearing anything.

---

### Post by Absurd on 2007-01-10
Open up /etc/group and check to see that your username is in the audio portion. 

For example

```
audio:x:29:<your username>
```

If it's not, add it and reboot.

---

### Post by Quillz on 2007-01-10
> **Absurd said:**
> Open up /etc/group and check to see that your username is in the audio portion. 

For example

```
audio:x:29:<your username>
```

If it's not, add it and reboot.
```
audio:x:29:joseph
```
Yes, it's in there.

---

### Post by Absurd on 2007-01-10
Is it enabled in your BIOS?

If so, then I give up.

---

### Post by Quillz on 2007-01-10
> **Absurd said:**
> Is it enabled in your BIOS?

If so, then I give up.
How would I check this?

---

### Post by Absurd on 2007-01-10
When you restart or power up your machine, you should see a logo or pop up for a short period of time (before you are taken the grub menu). Often times, you hit F2 during that time in order to access the BIOS menu.

---

### Post by Quillz on 2007-01-10
> **Absurd said:**
> When you restart or power up your machine, you should see a logo or pop up for a short period of time (before you are taken the grub menu). Often times, you hit F2 during that time in order to access the BIOS menu.
Yes, I know, but what specifically in the BIOS am I looking for?

---

### Post by Absurd on 2007-01-10
To see if your onboard sound is enabled.

---

### Post by Quillz on 2007-01-10
Okay, thanks. Though it worked with Windows, so it probably is.

---

### Post by Absurd on 2007-01-10
I don't know what else it could be honestly. 

I take it that you've gone into the mixer and messed with the volume settings of different channels, right? I have the same type of onboard sound (that I do not use) and the Surround channel is the master channel (which can be controlled through the PCM as well).

---

### Post by Quillz on 2007-01-10
Actually, I've just been using the standard volume control. Where would I find such mixer?

---

### Post by Absurd on 2007-01-10
If you're using Gnome, then right click on the speaker icon (where you raise your volume) and choose to open up the mixer **or** just double click on the icon.

---

### Post by Quillz on 2007-01-10
> **Absurd said:**
> If you're using Gnome, then right click on the speaker icon (where you raise your volume) and choose to open up the mixer **or** just double click on the icon.
Yes, I've found that, and it's still not working. I don't know what else it could be.

---

### Post by Quillz on 2007-01-22
I finally got my sound card working! Turns out it was supported the whole time, I just needed to go into the advanced options and turn on surround sound.

---

