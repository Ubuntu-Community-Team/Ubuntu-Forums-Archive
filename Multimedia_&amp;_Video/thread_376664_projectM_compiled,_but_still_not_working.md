---
title: "projectM compiled, but still not working"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by tbraun on 2007-03-05
Hello!

I managed to get projectM (the MilkDrop-like visualization plugin for xmms) properly compiled and installed. However, it still does not want to work. Enabling the plugin has absolutely no effect. No error message is shown.

When I start xmms from the command line, I can see the following messages:

```

Message: device: default
projectM plugin: Initializing
projectM plugin: Playback starting
reading ~/.projectM/config 
Video mode set failed: Couldn't find matching GLX visual
loading preset from '/usr/local/share/projectM/presets/Unchained & Rovastar - Luckless.milk'
pre init_display()
post init_display()
post CreaterenderTarget
mesh: 32 24
maxsamples: 2048
exiting projectM_init()
loading preset from '/usr/local/share/projectM/presets/EvilJim - Follow the ball.milk'
loading preset from '/usr/local/share/projectM/presets/shifter - snow.milk'
loading preset from '/usr/local/share/projectM/presets/Krash & Illusion - Spiral Movement.milk'

```

The music plays, but nothing displays. Right after it prints that it is reading the config file, it reports that it "Couldn't find matching GLX visual". I looked into the config file, and it appears the only thing I need to adjust is the screen resolution. I did that, but still the same error.

For what it's worth, I'm running 6.10 on a Dell Inspiron 9300 with 1920x1200 screen resolution and nVidia GeForce Go 6800.

Any help is greatly appreciated.

Thank you very much...

Tom

---

