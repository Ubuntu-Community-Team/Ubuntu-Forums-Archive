---
title: "HOWTO: Get mpd and pulseaudio to work at startup on xubuntu ibex"
date: 2008-12-12
forum: Multimedia Software
---

### Post by glurgle on 2008-12-12
*** IMPORTANT ***
This is NOT the recommended way to run pulseaudio, in most cases it makes more sense to run it as a per-user daemon. That said, one of the primary purposes of this computer is to run a Music Player Daemon for me and my girlfriend to use. While there is often nobody logged into the machine, that's not always the case, and so I can't afford to have mpd always hogging my alsa device directly. So this is what I did:

1. Install mpd, pulseaudio, pulseaudio-utils and an MPD client (I use xfmpc because it's nice and simple.

2. Edit /etc/default/pulseaudio and change the options PULSEAUDIO_SYSTEM_START and DISALLOW_MODULE_LOADING to 1

3. Edit /etc/pulse/default.pa and comment out the line that loads the x11-bell module:
```

#load-module module-x11-bell sample=x11-bell
```

4. Edit /etc/mpd.conf and add an audio output section like so:
```

audio_output {
  type "pulse"
  name "Music Player Daemon"
}
```

* While editing mpd.conf, you will also want to tell it where to look for your musi. You might also want to comment out the line that specifies bind_to_address, as this can cause issues with some remote clients not resolving the hostname properly.


5. Reboot. Or kill any existing pulseaudio processes. Stop mpd, and bring up pulseaudio and restart mpd like so:

```
killall pulseaudio
sudo /etc/init.d/mpd stop
sudo /etc/init.d/pulseaudio start
sudo /etc/init.d/mpd start
```

And that should get everything going.

---

