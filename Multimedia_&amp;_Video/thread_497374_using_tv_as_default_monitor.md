---
title: "using tv as default monitor"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by bartkock on 2007-07-10
Hi
I have a question about my monitor settings.
I have an nvidia MX440 graphic card wit  1 VGA 1 SVideo and 1 DVI connector.
Now I'm trying to use de SVideo connector with a resolution op 720x576(PAL).
I was looking to some twinview options. And sometime's I had a second screen on my television for 1 sec. Then both sceens became black.
I can't find a good how to for my problem. All how to's are telling me differnt things.
Do i need nvidia-glx or not and where do I have to put the new option lines and so on.

Can someone help me with my problem

Kind regards 

Bart

---

### Post by bartkock on 2007-07-10
I solved the problem with the default monitor.
I disconnected my VGA device.
and in /etc/X11/xorg.conf I enabled the nvidia driver and disabled the 1024x768 resolution.

Now the default resolution is 800x600 and i actually want it to be 720x576 but when I add this. This resolution will be ignored.

Does someone know how to change this resolution?

---

### Post by bartkock on 2007-07-10
I found a solution here

[http://ubuntuforums.org/archive/index.php/t-401051.html](http://ubuntuforums.org/archive/index.php/t-401051.html)

---

### Post by frokki on 2007-07-30
> **bartkock said:**
> I solved the problem with the default monitor.
I disconnected my VGA device.
and in /etc/X11/xorg.conf I enabled the nvidia driver and disabled the 1024x768 resolution.

Now the default resolution is 800x600 and i actually want it to be 720x576 but when I add this. This resolution will be ignored.

Does someone know how to change this resolution?I fought with the same problem, but managed to fix it like this:

(At first you have to install nvidia-settings package from the repositories if you don't have it installed already)

I changed the bolded lines (under Section "Screen") in my xorg.conf like this:
```
Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    **Option         "metamodes" "TV: 720x576"**
    SubSection     "Display"
        Depth       24
    **    Modes      "720x576"**
    EndSubSection
EndSection
```
Then I logged out and restarted X by pressing ctrl+alt+backspace.
That didn't set the resolution straight away, but after logging in again I was able to select 720x576 resolution from Nvidia-Settings.

Hope it helps!

EDIT: SORRY, IT DID WORK UNTIL I REBOOTED :(
I'm as lost with this as you guys....

---

