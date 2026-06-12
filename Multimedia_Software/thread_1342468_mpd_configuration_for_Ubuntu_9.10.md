---
title: "mpd configuration for Ubuntu 9.10"
date: 2009-11-30
forum: Multimedia Software
---

### Post by jzacsh on 2009-11-30
Firstly, I apologize if I've done a poor job searching for this first.
I was using this post, along with the man pages to try and set up mpd for myself:
[http://ubuntuforums.org/showthread.php?t=664334](http://ubuntuforums.org/showthread.php?t=664334)

This isn't relevant, since it doesn't happen anymore, but oddly I have no idea how I got this error to stop:
```
listen: Failed to listen on mpdhost (line 69): Cannot assign requested address
Aborted

```

But, I keep getting this error:
```
$ mpc ls /multidrive/media/music/library/Sufjan\ Stevens/* | mpc add sufjan
error: ACK [50@0] {lsinfo} directory not found
adding: sufjan
error: ACK [50@0] {add} directory or file not found

```

.. is that "ACK" as in ... *TCP* ACK*nowledgement packet*? if so.. I have no idea where to start.. any help would be awesome!

---

### Post by jzacsh on 2009-12-01
Actually I think the problem now is just this:

```

*$ mpc play*
Pallas Athena - Minute
[playing] #91/138   0:00/1:37 (0%)
volume: n/a   repeat: off   random: off   single: off   consume: off

*$ mpc volume +10*
**error: ACK [52@0] {volume} problems setting volume**

```

---

### Post by jzacsh on 2009-12-07
anybody?

---

### Post by falconindy on 2009-12-07
Post your /etc/mpd.conf. Am I right in assuming that you get no sound at all? MPD is likely using the wrong mixer channel.

---

### Post by jzacsh on 2009-12-07
> **falconindy said:**
> Post your /etc/mpd.conf. Am I right in assuming that you get no sound at all? MPD is likely using the wrong mixer channel.

Thanks for the reply :)
correct, no sound plays. I attached my config file (as .txt, so this forum would accept it). *Notice everything is in /multidrive/media/music/mpd/ because I keep my music (library/)and playlists under /multidrive/media/music/.*

---

### Post by henriquemaia on 2009-12-07
I have the same problem (no sound) and can't seem to get it to work. I'm using pulse as sink, but mpd doesn't show on the sound properties. Any ideas?

---

### Post by falconindy on 2009-12-07
Comment out the ALSA section entirely. MPD should be smart enough to pick up the default local output device (which in your case should be Pulse). Here's a couple resources if you're finding yourself still stuck:

[http://www.pulseaudio.org/wiki/PerfectSetup#MPD](http://www.pulseaudio.org/wiki/PerfectSetup#MPD)
[http://mpd.wikia.com/wiki/PulseAudio](http://mpd.wikia.com/wiki/PulseAudio)

---

### Post by henriquemaia on 2009-12-07
I found a way that worked in my case. It was taken from [here]("https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/192735/comments/8").

> running mpd as user mpd (what is default in ubuntu) you need to make pulse a bit more easy on permissions
Edit /etc/pulse/default.pa and add
load-module module-native-protocol-tcp auth-anonymous=1
this gives permission to everybody to use pulse.

so, open a terminal and run:
sudo gedit /etc/pulse/default.pa

add to the end of the file:
load-module module-native-protocol-tcp auth-anonymous=1

save the file, close gedit and then run:
killall pulseaudio

followed by:
sudo /etc/init.d/mpd restart

Hope this helps.

---

### Post by jzacsh on 2009-12-08
> **falconindy said:**
> Comment out the ALSA section entirely. MPD should be smart enough to pick up the default local output device (which in your case should be Pulse). Here's a couple resources if you're finding yourself still stuck:

[http://www.pulseaudio.org/wiki/PerfectSetup#MPD](http://www.pulseaudio.org/wiki/PerfectSetup#MPD)
[http://mpd.wikia.com/wiki/PulseAudio](http://mpd.wikia.com/wiki/PulseAudio)

wow, so thanks a bajillion for finding that for me. I have no idea what happened, but I cam home and typed `ncmpcpp` again and it started playing music.

Have no idea what happened. :) thanks again!

---

### Post by jzacsh on 2009-12-08
> **jzacsh said:**
> wow, so thanks a bajillion for finding that for me. I have no idea what happened, but I cam home and typed `ncmpcpp` again and it started playing music.

Have no idea what happened. :) thanks again!

actually, ncmpcpp isn't working on my box any more. now music just pauses immediately after starting to play. this happen to anyone?

*also, I've commented out the alsa section* - though the music plays no (*or when it did before this above problem started*) it still couldn't increase/decrease volume.

---

### Post by InkyDinky on 2009-12-11
I kept getting that setvol error until I uncommented out the "mixer_type  software" line.

---

