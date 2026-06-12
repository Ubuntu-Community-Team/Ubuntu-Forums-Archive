---
title: "No sound when creating new user"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by namnam on 2008-01-17
Hello there!

I've been letting my desktop user (the one created during install) run a [Music Player Daemon]("http://musicpd.org/") process for a while and it has worked great.

The other day I wanted to create a new user who would have all my media files and also run the MPD. I log into this computer remotely and add the new user with the adduser command:

```

sudo adduser media

```

I guess it was setup with all default values.

I log in with this new user and run the MPD. The probem is that I'm not getting any sound and the error messages makes me think it's not getting access to the sound card:

```

ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default

```

Have I set up this user wrongly?

Thanks in advance!

---

### Post by lswest on 2008-01-17
if the sound card is in use by the original account i don't believe that the sound card can be used in any other account (sounds silly, but it's true, like trying to play music in xmms while watching a flash video or so) supposedly, it should be solved by changing sound architecture in hardy.  the error states that it can't find the card, so either it's in use, or the alsa drivers for the sound card aren't working right in that user account.

---

### Post by namnam on 2008-01-17
Thanks for the reply!

I plugged in a keyboard, rebooted and at the GDM prompt I logged in as this new media user - still no sound even though there shouldn't be any other user occupying the sound card :(

And when I run sudo with this new user it doesn't seem to work eigher; just nothing happends. It doesn't say that I'm not in the sudoers file or anything. Just nothing. Which is strange, can these issues be related?

Yes, PulseAudio for Hardy looks interesting, although it doesn't change how things work at the low level does it?

---

### Post by sisco311 on 2008-01-17
ensure that user added properly to group audio:
```
id **username**
```if not add it:
```
sudo usermod -a -G audio **username**
```to use sudo add it to admin group:
```
sudo usermod -a -G admin **username**
```

---

### Post by namnam on 2008-01-17
Yup sisco311 you nailed it! I added a few other groups such as video as well and also had to reboot.

Thank you!

---

