---
title: "Gutsy Sound Juicer wont rip to MP3"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by The Grum on 2007-10-19
Hi. Ive installed Gutsy and installed GStreamer plugins for MP3 playback (by launching an mp3).

Sound Juicer does not let me rip to MP3. The profile is there and the "Active" box is checked, but it does not appear in the list of profiles in Edit->Preferences.

I have to install the multiverse gstreamer plugins package for it to work.

Is this a bug in sound juicer or the gstreamer plugin?

---

### Post by The Grum on 2007-10-19
Never mind. Found the launchpad bug.

---

### Post by juan_suave on 2007-10-19
was there a fix?  can you link to the bug I can't find it.

---

### Post by froy02 on 2007-10-20
Not a bug but you have to install the restricted-manager and restricted manager-core for the gstream plugin to be available in the list of choices in sound Juicer preference.

---

### Post by carnar on 2007-10-30
solved !!! 
Only install ugly multiverse plugin for gstreamer :)
```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by shmengie on 2007-11-11
> **carnar said:**
> solved !!! 
Only install ugly multiverse plugin for gstreamer :)
```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```
worked like a champ, thx!!

p.s. do you know what bit rate that is? 128? 160? 192?

---

### Post by nossifer on 2008-01-16
stuff like this really makes me glad i run ubuntu.
works perfectly.  thanks for posting this.

---

### Post by Auximenes on 2008-01-20
What would I ever do without this forum? Thanks guys! :D

---

### Post by rosegarden78 on 2008-01-20
Yeah you need Medibuntu repositories.  You may consider installing Kaffeine and Audacity to compliment your audio suite.

---

### Post by Fruhwirth on 2008-01-25
Thanks!  

I have gstreamer0.10-plugins-ugly-multiverse and gstreamer0.10-plugins-ugly installed and all is working for me. 

I'm on Gutsy, AMD64.

my pipeline:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux

This post is the top hit for the google search string: gutsy "sound juicer" mp3

---

### Post by Sleestack on 2008-01-27
Same issue; I created the profile but it did not appear when I tried to set the mp3 output preference. Going to the Terminal and typing:

sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

...and it installed what I needed. Once I made sure the profile was marked as Active I was able to select the mp3 profile.

Thanks, everyone!

---

### Post by talen.quickblade on 2008-02-14
installing plug-ins did the trick. Had to restart sound juicer, and edit the profile to allow for my preference of 192 bit encoding.

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux

---

### Post by Scrik on 2008-02-25
post error

---

### Post by mike.oldfield on 2008-03-22
As others have already said, thanks! This worked perfectly for me on Hardy!

---

### Post by jISh on 2008-04-04
What a nice, perfect solution! Thanks so much! Ubuntu, and Linux as a whole, just gets better every day,

---

### Post by sa-mejia on 2008-04-06
I'm glad that I found this thread.

S.

---

### Post by SlappyPappy on 2008-04-10
Excellent thread thanks for posting.

Saved me a ton of time figuring this one out.  :popcorn:

---

### Post by Hooya on 2008-05-09
This doesn't seem to work in Hardy though.  I've got all the packages installed, but I still can't select mp3 encoding.  I've commented in the launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/124437](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/124437)

---

### Post by Paulo Calipari on 2008-05-17
This problem bothered me for some months, working with ubuntu 7.04 on AMD_64.
Not able to rip for my iPod.
This solution is quick and working fine.
"sudo apt-get install gstreamer0.10-plugins-ugly-multiverse"

---

### Post by abodsalas on 2008-06-16
Excelent. Worked right away. Only complain is:
Sound Juicer should have this on its help in a very visible place.
Probably 9 out of 10 people who want to extract CD's expect mp3 files.

Saludos,

Andres

---

