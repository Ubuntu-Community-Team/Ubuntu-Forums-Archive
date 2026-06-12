---
title: "Sound is choppy since last update (12.04)"
date: 2012-06-29
forum: Multimedia Software
---

### Post by Seine on 2012-06-29
This is a [cross-post from askubuntu]("http://askubuntu.com/questions/157554/choppy-stuttery-sped-up-sound-after-update"), as my question seems to be getting very little attention.

My audio has always worked perfectly on this hardware and 12.04. Yesterday I received an update, including a kernel update. Today the sound is periodically stuffed. In youtube, mkv files via VLC and embedded audio in web pages (memrise.com) the sound can become stuttery, sped up or stopped mid play-back.

Edit: The behaviour is MKV files stutter every 10 seconds or so, youtube videos play about 10 seconds worth of video & audio in 1 second then play normally but slightly out of sync, embedded files in memrise.com are sometimes shortened (perhaps sped up?) to about a 10th of their normal duration.

Where can I go to find if this is a known problem, or report it if it is not? Also, can I find a log that will tell me what packages were updated on my machine yesterday?

---

### Post by MickM on 2012-06-29
I have the exact same problem and everything was OK last week.

---

### Post by p_squared on 2012-06-30
Same here, also happens with mp3 and flac files in rhythmbox.

---

### Post by MickM on 2012-06-30
Hi,
mine has been fixed. I did an ubuntu update (Update Manager) and one of the update was a Google Chrome update, after re booting and trying Youtube and other streaming videos all worked OK.
It seems that Google have fixed the problem.

---

### Post by Seine on 2012-06-30
Ah, I am happy for you. I got the Chrome update but the problem persists even after reboot.

---

### Post by Seine on 2012-06-30
I think the sped up youtube and the sound problem were different. Youtube speeds are now normal, but the audio problem persists.

I have raised this as [bug #1019693]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1019693").

---

### Post by Seine on 2012-07-01
For those of you having problems with this, I suggest trying:

[LIST=1]
[*][Turning off PulseAudio timer scheduling]("https://wiki.ubuntu.com/Audio/PositionReporting") as a workaround
[*]Going to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1008177") and clicking "this bug affects me too"
[/LIST]

---

### Post by jdsampayo on 2012-07-07
For me it dissapeared disabling automute
alsamixer => disable auto mute

Found the solution in this video:
[http://www.youtube.com/watch?v=Wrhl8iaDzFI](http://www.youtube.com/watch?v=Wrhl8iaDzFI)

---

