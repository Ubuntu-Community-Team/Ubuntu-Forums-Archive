---
title: "Youtube vs Rhythmbox vs other not working together"
date: 2008-06-10
forum: Multimedia Software
---

### Post by earthpigg on 2008-06-10
This happened immediately upon my upgrade to Heron.

If i start a music player, i can play music just fine.
if i start a youtube video, i can watch/hear the video just fine.

but if i start a youtube video WHILE my music player is open, it does not work.

if i have a youtube video going and try to play something in rhythmbox, i get a box that says "couldn't stop playback - unknown playback error".

I have found references to this problem from other folks, but no solid solutions.

[http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/)

tried that, no effect.

I've tried playing around with the stuff in System -> Preferences -> Sound, but im not sure which options i should be trying, and if i need to restart each time.

Help, or pointing me in the right direction would be appreciated. No luck so far searching through threads on the forums.

edit: when i start rhythmox from a terminal so i can see what it tells me, this is what i get:

> Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing


---

### Post by sidran on 2008-06-10
I have seen this in a couple different distros of Linux over the past few years.  I have a feeling it's just a limitation in the way Linux shares access to the sound system.  If one process is using it, it's essentially locked to that process, and others cannot get access.

I haven't found any work-around for it. I just chalked it up as a quirk of Linux for now, though if anyone does have any suggestions, I'm all ears. :)

---

### Post by earthpigg on 2008-06-10
> **sidran said:**
> I haven't found any work-around for it. I just chalked it up as a quirk of Linux for now, though if anyone does have any suggestions, I'm all ears. :)

it wasn't happening back in Gutsy.

is it possible to go about using some gutsy mojo in heron? which mojo would i want to use?

---

### Post by sidran on 2008-06-10
> **earthpigg said:**
> it wasn't happening back in Gutsy.

is it possible to go about using some gutsy mojo in heron? which mojo would i want to use?

Now that you mention it, that is true.  Perhaps there was a regression of some sort, then?

---

### Post by kostkon on 2008-06-10
> **sidran said:**
> I have seen this in a couple different distros of Linux over the past few years.  I have a feeling it's just a limitation in the way Linux shares access to the sound system.  If one process is using it, it's essentially locked to that process, and others cannot get access.

I haven't found any work-around for it. I just chalked it up as a quirk of Linux for now, though if anyone does have any suggestions, I'm all ears. :)
No, it's not a limitation of *Linux*. It's a problem with *Flash* and *Pulseaudio*.

> **earthpigg said:**
> it wasn't happening back in Gutsy.

is it possible to go about using some gutsy mojo in heron? which mojo would i want to use?
Indeed it wasn't a problem in Gutsy since *Pulseaudio* was introduced in *Hardy*.
> **earthpigg said:**
> This happened immediately upon my upgrade to Heron.

If i start a music player, i can play music just fine.
if i start a youtube video, i can watch/hear the video just fine.

but if i start a youtube video WHILE my music player is open, it does not work.

if i have a youtube video going and try to play something in rhythmbox, i get a box that says "couldn't stop playback - unknown playback error".

I have found references to this problem from other folks, but no solid solutions.

[http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/)

tried that, no effect.

I've tried playing around with the stuff in System -> Preferences -> Sound, but im not sure which options i should be trying, and if i need to restart each time.

Help, or pointing me in the right direction would be appreciated. No luck so far searching through threads on the forums.

edit: when i start rhythmox from a terminal so i can see what it tells me, this is what i get:
For a solution, check [here]("http://tombuntu.com/index.php/2008/05/09/stop-flash-from-locking-system-audio/").

---

### Post by earthpigg on 2008-06-10
> 
For a solution, check [here]("http://tombuntu.com/index.php/2008/05/09/stop-flash-from-locking-system-audio/").

i already had libflashsupport installed... so i removed it using apt-get, reinstalled it, and restarted the system.

problem persists.

i *am* using 64 bit, i dont know if that could be a contributing factor to the problem. any way to remove PulseAudio or have it ignored or whatever without screwing other things up?

---

### Post by kostkon on 2008-06-10
> **earthpigg said:**
> i already had libflashsupport installed... so i removed it using apt-get, reinstalled it, and restarted the system.

problem persists.

i *am* using 64 bit, i dont know if that could be a contributing factor to the problem. any way to remove PulseAudio or have it ignored or whatever without screwing other things up?
I am not sure about this, but a solution would be to set your playback to use *Alsa* instead of *PulseAudio* by going to *System -> Preferences -> Sound* and changing the playback devices from *Autodetect* (i.e. *PulseAudio*) to *Alsa*.

---

### Post by earthpigg on 2008-06-10
> **kostkon said:**
> I am not sure about this, but a solution would be to set your playback to use *Alsa* instead of *PulseAudio* by going to *System -> Preferences -> Sound* and changing the playback devices from *Autodetect* (i.e. *PulseAudio*) to *Alsa*.

Did that, no effect :\

thank you for the advice folks, i appreciate it.

anyone know of anyone that has had this problem since the heron upgrade and managed to fix it some way other (or in addition to) than using the libflashsupport?

is there a way to verify that libflashsupport is not only installe - but being used?

---

### Post by Vivaldi Gloria on 2008-06-10
The following guide fixed all my problems:

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by earthpigg on 2008-06-10
YES! it worked vivaldi!

i skipped all of "2) Configure settings" because for some reason i didn't think they would be necessary... and apparently, they weren't for me :)

---

