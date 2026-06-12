---
title: "Slight stuttering in any opengl program if using compiz"
date: 2010-11-15
forum: Multimedia Software
---

### Post by a-user on 2010-11-15
Now, i'm using currently ubuntu 10.10. Having a nvidia gt220 with the proprietary drivers.
i used compiz for a while. it works quite well, with vsync on and so on. but one thing bothers me all the time:
in any opengl programm (like a game or the unigen benchmarks) or on video playback (no matter if its the default video player, xbmc or what ever) i see some kind of stutter.
about every second or so it jumps one frame forward and then two back. till the next second it plays fluid. to be able to observe this easily you need a video (or a opengl scene) where the whole screen scrolls in a medium speed but smooth. than you can observ how it "jumps" every second.

if the scrolling is too slow you wont observe it.

now, if i turn composite off this disapears. all play fluid. ofcourse i get tearing as long as i do not also disable the composite extension in the xorg.conf, but this is another story.

now, the question is, is there a possibility to fix this stuttering with compiz active? cause i use this pc to watch movies quite often so this would render compiz unusable.

---

### Post by s3MA00RRNY on 2010-11-15
Here is some extra garbage you can put in /etc/X11/xorg.conf:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "RandRRotation" "true"
    Option         "Coolbits" "1"
    Option         "TwinView" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "RenderAccel" "true"
EndSection

Section "Extensions"
    Option "Composite" "Enable"
    Option "RENDER" "Enable"
EndSection
```

Don't copy/paste this. Take the Option lines and put them in the right section in the file. The Extensions section may or may not exist. Create it if necessary.

RandRRotation allows you to rotate the screen.
Coolbits lets you change the throttling mode on the GPU.
TwinView allows you to use two different resolutions on a cloned desktop.
AllowGLXWithComposite allows you to have compositing programs (Compiz) running with games or other stuff. Technically this should already be enabled.
RenderAccel acclerates 2D rendering.
Composite enables compositing acceleration.
RENDER enables rendering accleration.

---

### Post by a-user on 2010-11-15
thx for your reply. i tried all but one of your options. the only one i didn't tried is the render extension, which according to nvidia info is not needed to explicitly enable in xorg.conf. but i will try it.

beside of that i don't have a performance problem. my frame rate is quite high. it is only this light stuttering every second or so.

i experimented a bit with slider in the compiz settings that set the vertical refresh rate to sync with. it seems to inluence how strong this stuttering is. i have 60hz refresh rate. and i had it at 60 with detect refresh rate off. now i could improve the behaviour a bit setting it to 59. go more under or over 60 only increases the problem.

but even with 59 it's still there. it is somewhat better, and occurs less often (now there are some seconds where you don't observ the mentioned problem) but it is not solved.

it seems as if the vsync of compiz does not perfectly match the refreshrate of the screen, at least not continuesly. but i may be wrong.

what also helped a bit is disabling triplebffer.

btw. the framerate of e.g. the opengl benchmark unigine tropical or any other program is more or less the same with and without compiz.

---

### Post by a-user on 2010-11-16
as i thought, the render extension is already loaded, even without explicit calling in xorg.conf.

any other suggestion?

btw. did this anybodyelse observed? cause i have this issue with **all** pc i tested this. it seems as if compiz vsync is somewhat buggy. there is no tearing but this every second jump.

---

