---
title: "No xorg.conf"
date: 2010-05-21
forum: Multimedia Software
---

### Post by willix on 2010-05-21
Hy

I'm trying to setup an old desktop as a multimedia server. When I boot with a ordinary screen all is right. However when I boot it with my TV hooked up, I've get a message saying that "X server does not support size requested" and it sets itself with a 800x600 resolution and I can't increase it. However if I boot with my screen, and then switch the displays, I'm able to have a 1280x1024 resolution on my TV (much better).

Reading threw the forums, I understand and I need to edit my xorg.conf file but this is where all goes bizarre. I DO NOT have one!!! (at least not under /etc/X11)
[B]
What do I need to do for ubuntu to generate a xorg.conf file???
[/B]

I'm using Ubuntu 10.4 Lucid, have a simple Intel integrated graphic card and am not using any proprietary drivers.

---

### Post by Peter09 on 2010-05-21
Latest versions of Ubuntu do not use an xorg.conf file - although they will read it if you generate one.
 
Are you using an old monitor - what resolution are you hoping for?

---

### Post by willix on 2010-05-21
I'm trying to use a one-year old TV screen which I KNOW supports 1280x1024 but obviously is not detected by Ubuntu on start up.

As I said, if I boot the machine with an ordinary screen which supports 1280x1024, I am then able to disconnect the screen and connect the TV and use such resolution, but if I boot with the TV connected, the Display preference only offers 800x600 resolution. 

I was thus hopping to force X to use the desired resolution by hard coding it in xorg.conf but since their is no xorg.conf, how do I do this?

---

### Post by Peter09 on 2010-05-21
It looks like your TV is not providing any resolution details to you computer. Might be worth checking the set up of the TV.

---

### Post by Grenage on 2010-05-21
While it would be easy to configure one monitor in an xorg.conf, I'm not sure how to specify (and utilise) two.

As **Peter09** mentioned, it's likely an EDID issue.

---

### Post by willix on 2010-05-21
I am not trying to configure two monitors. I'm merly stating that my TV screen does support 1280x1024 but that when booting with it, I am not given the option to use that resolution.

---

### Post by Grenage on 2010-05-21
That's right, but Ubuntu isn't getting the correct information from the TV; this will be down to the cable or TV.

I agree that there should be an option to set any resolution, regardless of whether or not the computer thinks it can support it.

---

### Post by willix on 2010-05-21
I'm not sure what I can do about the cable or the setup. 

I've tried with a different computer (also running a freshly installed Ubuntu Lucid) which has an ATI video card  and although I dont have the option to set to 1280x1024, it does by default use 1360x768 which is acceptable. 

So in this second scenario, somehow, I am able to use a higher resolution and the only major difference is the video card/driver which kind of makes me think TV/cable have nothing wrong with them.

I know in old version of X, you could 'force' things in xorg.conf. Now that this file is lacking, is there a way of doing the same?
Is there a way to force X to generate a xorg.conf file (so that I can edit it) and them tell him to use it instead of whatever he does by default?

---

### Post by yota on 2010-05-21
As Peter09 already said X will read an xorg.conf file if you place one in /etc/X11.

There you can force anything to your desires, including resolution, refresh rates etc.

You'll find many howtos online, to get a base file based on your actual hardware as a quick start you can issue:
```

sudo Xorg -configure

```

Before jump on configuring, be sure to be able to remove the file from a VT (ctrl+alt+f1) in the case something went wrong and X is not starting.

Hope this helps!

p.s. probably 1360x768 is your native panel resolution (one display pixel matches exactly one panel pixel) which probably offers the best visual quality... maybe it's a "if ain't broke don't fix it" case?

---

### Post by Peter09 on 2010-05-21
I think there is an xorg.conf.default file, so if you copy that and name it xorg.conf you may be able to do something.

---

### Post by willix on 2010-05-21
Ok, did it :P

Thanks to all for your help!

The ```
sudo xorg -configure
``` did the trick. I was able to create a xorg.conf and it works as it with my TV screen.

The tricky thing was to actually kill X (the above instruction failing while X is running). It take me a while to remember to use ```
sudo service gdm stop
``` to stop the X server.

Anyway, thanks again to you all.

---

