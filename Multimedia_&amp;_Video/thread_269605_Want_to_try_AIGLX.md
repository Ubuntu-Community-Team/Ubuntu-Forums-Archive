---
title: "Want to try AIGLX"
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by maniacmusician on 2006-10-02
...but I figure I should maybe troubleshoot my graphics first.

so heres the lowdown. I got some of my older problems sorted out. Now, with the open source "radeon" driver, i can actually enable compositing without everything being out of wack. This is great! BUT (yes, theres always a but), my computer is surprisingly slow with it on. This is to be expected, to a degree, but I always thought my graphics could at least be decent. I have this chipset ([http://www.ati.com/products/radeonxpress200Intel/specs.html](http://www.ati.com/products/radeonxpress200Intel/specs.html) ) that specs page says that my onboard card can handle directx 9, so i dont think composite should be a problem. My computer specs:

3.06 GHz processor,
1.5 GBs of RAM  --decent enough, i should think.

but...

```

maniacmusician@Alexis:~$ xdriinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Screen 0: not direct rendering capable.

```

```

maniacmusician@Alexis:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
259 frames in 5.1 seconds = 50.820 FPS
342 frames in 7.2 seconds = 47.193 FPS
342 frames in 7.3 seconds = 46.601 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```
with compositing disabled, I was getting about 189 fps...still not very good. so compositing has had a major impact on the computer's speed. I guess the problem seems to be that i dont have direct rendering. but i do have the "Section "DRI" Mode "0666" EndSection" in my xorg.conf.

So I really dont think my system is AIGLX ready yet, but i feel like it's some small setting or something that i'm overlooking. with my specs, i think i should be able to do this. 

so what can I do to fix this?

thanks.

ps: compositing only started working for me after I started using KDE. BUT, I can't find the option in KControl or wherever, that I used to turn on compositing. Can someone help me out and point that out to me? thanks.

---

### Post by pay on 2006-10-02
I would say wait for ATI's next driver release and use the FGLRX driver.

---

### Post by tseliot on 2006-10-02
If you want to try (i.e. test) the latest ATI (fglrx) driver (on Dapper) you can have a look at this page:
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

and post the feedback on this thread:
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

---

### Post by maniacmusician on 2006-10-02
[sigh] i'm not a big fan of the proprietary drivers. i get a higher resolution with radeon. But looks like I have no choice.

I guess this means XGL as well, instead of AIGLX...

---

### Post by maniacmusician on 2006-10-02
okay tried that, posted feedback. doesnt work any better than past versions. I can't get a higher resolution than 1280x1024, my fps with glxgears is around 123, and if I attempt to enable composite, the desktop wacks out on me. The radeon driver makes composite slow but at least it works a little. And i definitely cant have XGL if i cant even get composite.


can anyone tell me how I can get my computer to sanely run either AIGLX or XGL? by that i mean suggest the proper driver/config so that I can actually use the power of my graphics card. all the information is in the first post. let me know if anything else is needed.

---

### Post by maniacmusician on 2006-10-03
[cries]

is there no justice for an ATI user?

If only I had known before buying the chipset.

---

### Post by maniacmusician on 2006-10-04
....anyone?

---

### Post by maniacmusician on 2006-10-09
i'm thinking about rephrasing my question.

obviously, the problem is that my desktop is not capable of direct rendering with the open source "radeon" driver. The prop. drivers are pretty bad as well. Is there any way, that I can optimize my open source driver?

thanks.

---

