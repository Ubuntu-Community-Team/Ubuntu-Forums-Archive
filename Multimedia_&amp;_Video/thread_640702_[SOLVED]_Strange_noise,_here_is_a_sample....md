---
title: "[SOLVED] Strange noise, here is a sample..."
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by Amazona aestiva on 2007-12-14
I have met this issue in games. There aren't any settings for audio, so I've no idea.

I attached a little of the creaking.

Thanks in advance!

---

### Post by swerner on 2007-12-14
Have you checked the volume of your inputs, like your line input or mic?  Or are some of the volumes set to 100%, it is best to set to 80% to avoid clipping (although this only occurs if you recorded the sound from your speakers).

---

### Post by Amazona aestiva on 2007-12-14
Yes I've check them and the noise is there with low volume too.

---

### Post by Amazona aestiva on 2007-12-14
I've just seen that sound(music) is a new feature in that game. Could it be a bug?

---

### Post by kajillin on 2007-12-14
could be your speakers? probly not but worth a check.

---

### Post by swerner on 2007-12-15
How was the sound recorded?  I did you put a mic up to your speakers? Or did you record using software only?

What happens to other music/sounds in your system, not in the game?  What game is it?

---

### Post by Amazona aestiva on 2007-12-15
Audacity recorded the line out, I didn't use mic.

We are speaking about[ this game]("http://www.getdeb.net/app.php?name=Snowballz").

The sound of other games and apps is all right.

My speakers are all right, the sound is clean when plays a video file.

---

### Post by weblordpepe on 2007-12-15
Hmmm yeah I've had specific apps that cause distortion like that. VLC does it if its own volume slider is above 50%. I assume it just calculated the maximum volume wrongly (bug in VLC).

Everything else is sweet though. I'd nail it down to the application aye.

---

### Post by Amazona aestiva on 2007-12-16
I've known about VLC's volume slider, but this app doesn't have one.

---

### Post by sdowney717 on 2007-12-16
wont work for me at all including older version in channel

scott@scott-desktop:~$ snowballz
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  136 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x87
  Serial number of failed request:  127
  Current serial number in output stream:  129

---

### Post by Amazona aestiva on 2007-12-16
> **sdowney717 said:**
> wont work for me at all including older version in channel

scott@scott-desktop:~$ snowballz
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  136 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x87
  Serial number of failed request:  127
  Current serial number in output stream:  129

Install the one from GetDeb, that works for me. The others in repo says that.

---

### Post by sdowney717 on 2007-12-17
tried them both and no go.
I have an ATI 9600 video card with the drivers properly installed.

perhaps it is another ATI video card problem.

---

### Post by weblordpepe on 2007-12-19
HmMmMMmMmmm. My laptop does make a quiet squealy noise when running Glxgears which becomes louder when I make the window **smaller**. Odd I know.

---

