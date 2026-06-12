---
title: "HOWTO: Get mpd running with pulseaudio"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by aquaherd on 2008-02-15
>>what?

I tried for ages to get mpd working with single-user pulseaudio to the level of compiling mpd and pulseaudio myself to no avail; then I finally found this out:

a) Let user mpd be member of pulse* groups.
b) Let mpd have access to your X11 session (if you want to keep package pulseaudio-module-x11 and have an X11 bell).

>>how?

do
  sudo usermod -a -G pulse-access mpd
  sudo usermod -a -G pulse mpd
  sudo usermod -a -G pulse-rt mpd
in a console

append:

  xhost +local:mpd

to your .bashrc or startup script of choice.

>>why?

Since pulseaudio access to the desktop is delayed until the first try to play, mpd can happily boot and be idle until you log in. I guess you can have it much easier when you do
   sudo apt-get remove pulseaudio-module-x11
and I can express my hope that this will be addressed when hardy hits the shelf.

hth,

herd

---

### Post by K.Mandla on 2008-02-19
Moved to Multimedia and Video.

---

### Post by Emblem Parade on 2008-03-28
I'm running Hardy Heron beta, and this was enough for me:

```
sudo aptitude install paprefs
paprefs
```

In PulseAudio Preferences, make sure these two options are enabled:

* Enable network access to local sound devices
* Don't require authentication

Then, to your /etc/mpd.conf add this:

```
audio_output {
	type    "pulse"
	name    "My MPD PulseAudio Output"
}
```

Don't add any other options to this! Let MPD just use PulseAudio's defaults. Now, restart MPD:

```
sudo /etc/init.d/mpd restart

```

Worked for me! (After hours of fiddling around...)

---

### Post by nitio on 2008-03-30
> **Emblem Parade said:**
> I'm running Hardy Heron beta, and this was enough for me:

```
sudo aptitude install paprefs
paprefs
```

In PulseAudio Preferences, make sure these two options are enabled:

* Enable network access to local sound devices
* Don't require authentication

Then, to your /etc/mpd.conf add this:

```
audio_output {
	type    "pulse"
	name    "My MPD PulseAudio Output"
}
```

Don't add any other options to this! Let MPD just use PulseAudio's defaults. Now, restart MPD:

```
sudo /etc/init.d/mpd restart

```

Worked for me! (After hours of fiddling around...)


Thank you very much! I did not know that pulseaudio was the default in Hardy Heron and so I've decided to give it a shot in Hardy but was a pain not having mpd working with it. Thank you!

---

### Post by bongo on 2008-04-09
Hi, can you circumvent that PulseAudio shuts down with the X server or when switching consoles? For me the whole point of having a music deamon was to be able to play music whatever happened to the system.

If not, is it still able to run ALSA in Hardy?
Edit: Alsa works perfectly, just uninstall all pulseaudio related stuff (except the libraries)

---

### Post by grugnog on 2008-04-16
For reference paprefs worked well for me (although I had previously applied the first post suggestions, so it is possible it is a combination).

The one thing worth remembering is that paprefs itself needs to be run as your regular user, not as root ;)

---

### Post by Hubi17 on 2008-04-27
> **Emblem Parade said:**
> I'm running Hardy Heron beta, and this was enough for me:

```
sudo aptitude install paprefs
paprefs
```

In PulseAudio Preferences, make sure these two options are enabled:

* Enable network access to local sound devices
* Don't require authentication

Then, to your /etc/mpd.conf add this:

```
audio_output {
	type    "pulse"
	name    "My MPD PulseAudio Output"
}
```

Don't add any other options to this! Let MPD just use PulseAudio's defaults. Now, restart MPD:

```
sudo /etc/init.d/mpd restart

```

Worked for me! (After hours of fiddling around...)

Thanks! Your my savior. I been trying to get this fixed for 2 days and now it works!

-Hubi

---

### Post by firmit on 2008-05-06
For those using ALSA, there is a Tweak/fix. Add this to your /etc/mdp.conf
> audio_output {
type                    &#8220;alsa&#8221;
name                    &#8220;My ALSA Device&#8221;
device                  &#8220;hw:0,0&#8243;     # optional
format                  &#8220;44100:16:2&#8243; # optional
}

audio_output_format             &#8220;44100:16:2&#8243;

They have a bug reported on the issue here:
[http://www.musicpd.org/mantis/view.php?id=1661](http://www.musicpd.org/mantis/view.php?id=1661)

---

