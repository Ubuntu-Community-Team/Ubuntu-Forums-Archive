---
title: "playing sound on a server"
date: 2008-12-30
forum: Multimedia Software
---

### Post by DoppyNL on 2008-12-30
Hi people,

I've installed Ubuntu-server on an old machine and want to use this (among other things) to play mp3's.
The server is connectect to my audio-system using a simple audio-cable.
I've installed mpd as the player and currently Sonata as a client on another computer.

This all seems to work nicely, as Sonate reports a song is being played, except that I don't hear a thing!

How can I configure Ubuntu in such a way it will play sound to the (onboard) soundboard?
How can I configure mpd in such a way it will send the output to the soundboard?

tnx!

---

### Post by d8a on 2008-12-30
I'm not sure which packages are default on an ubuntu server edition install.

Please post the output of 

```
cat /proc/asound/cards
```

---

### Post by DoppyNL on 2008-12-30
```
doppynl@someweirdnameoverhere:~$ cat /proc/asound/cards
 0 [nForce2        ]: NFORCE - NVidia nForce2
                      NVidia nForce2 with ALC650E at irq 21
```
I'm no linux wizz, but that looks like it is installed... or at least it is recognised!

---

### Post by d8a on 2008-12-30
Yes, that looks good. Make sure your sound card isn't muted:

```
alsamixer
```

"OO" under a channel is good, "MM" means it's muted. You can mute or unmute a channel by pressing "M"

---

### Post by DoppyNL on 2008-12-30
when I started alsamixer I got a message it wasn't installed, so I installed it:
```
sudo apt-get install alsa-utils
```

Now I get this:
```
doppynl@someweirdnameoverhere:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
```

Remember that this all is on a server without X running...
Also, I'm unable to test for actual audio at the moment, I only have remote access ;).

---

### Post by d8a on 2008-12-30
A possible reason for this is that your user is not a member of the group **audio**

Edit /etc/group

---

### Post by DoppyNL on 2008-12-30
Brilliant!```
$sudo alsamixer
```And I get the mixer in front of me!

I can see that Master is set to mute, so that probably causes the problem of no sound.
Since I'm not near my server at the moment I can't test if it is actually working.

I will post back in about 6 hours about the result.

tnx!

---

### Post by DoppyNL on 2008-12-30
After some minor changes on the configuration of mpd, I'm now getting sound from my server.
So, in short: IT WORKS! 

:D

tnx!

Now to get a slightly longer cable to connect my server to my audio-set... I'm 2 meters short :|

---

### Post by jamesisin on 2008-12-30
Maybe some folks will benefit from more details about your configuration of mpd?

---

### Post by DoppyNL on 2008-12-31
The configuration of mpd is working out of the box.
The only changes I made were to point mpd to a different dir to work in, as I didn't want to use the default dirs.

I had to make some changes again to the config file of mpd after I installed asamixer to set the sound settings back to the defaults. I changed those settings earlyer to see if I could get any sound. I only set them back to default (wich is "let mpd figure out how to output sound").

I short:
- default settings of mpd worked for me
- I only changed dir-settings so my library is in a different location.
- asamixer didn't require any further configuration (just put yourself in the audio group or use sudo).

---

