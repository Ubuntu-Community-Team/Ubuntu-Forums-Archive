---
title: "alsa sound not working with pulseaudio"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by shrift on 2007-05-15
I'm posting this because I finally solved my own problems with alsa and pulseaudio. I scoured these forums and the web in my search to fix this, but nobody seemed to have the answer. I hope this helps someone figure it out.

The specific problems I was having was when I would click the "test" button under Preferences>Sound, with alsa selected, I would get something like this.
```
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing."
```

Also, whenever I would attempt to use aplay on the commandline I would get an error about: ```
 /usr/lib/alsa-lib/libasound_module_ctl_pulse.so
``` being missing form the system.

If these symptoms fit your issues, then maybe you have the same problem I did. For me it turns out that the package ```
libasound2-plugins[/code[ needs to be installed in order for the file above to be installed. Unfortunately pulseaudio does not seem to depend on this package, which it should, in my opinion. I'll look into filing a bug report on that.

The other thing that needs to be set is the ~/.asoundrc file. I got this setup information from [http://www.pulseaudio.org/wiki/PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup")

In the commandline type
[code]gedit ~/.asoundrc
```

and then insert this text 

```

pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

I believe a reboot is necessary at this point. You can try just doing ```
sudo /etc/init.d/alsa-utils restart
```

If however that does not work, give rebooting a try. 

I hope this works for someone, let me know if I can help figure something out.

---

