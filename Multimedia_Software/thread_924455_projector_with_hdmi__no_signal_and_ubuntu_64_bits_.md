---
title: "projector with hdmi : no signal and ubuntu 64 bits crashed"
date: 2008-09-19
forum: Multimedia Software
---

### Post by ubick on 2008-09-19
Hello,

I'm not able to use panasonic projector PT-AX200E through hdmi using ubuntu 64bits hardy heron (with last updates).

Configuration :
- ubuntu 64 bits hardy (last updates)
- video card :  8800 GTS 320Meg, DVI-I, hdcp (2 dvi outs)
- hdmi with adaptator : hdmi / DVI

Test 1
------
Using projector hd ready sony vps aw 10 works very well.
All mode are working (twinview,..) on both my lcd (PC screen) and projector
Here is the spec of the projector
[http://www.lesnumeriques.com/article-232-2181-16.html](http://www.lesnumeriques.com/article-232-2181-16.html)

Test 2
------
Using projector hd ready Panasonic PT-AX200E :
Spec :
[http://www.lesnumeriques.com/article-232-2633-60.html](http://www.lesnumeriques.com/article-232-2633-60.html)

[1]- when setting up the projector through hdmi on ubuntu, my lcd display a black screen with "no signal" and ubuntu is freezed. keyboard is out, i have to do a hard reboot.
[2]- setting up the projector through vga on ubuntu works very well
[3]- setting up the projector through hdmi on windows works...
so cable and projector looks ok


More details on step [1]

- plug in the projector on the second output of the graphical card and turn the projector on
- as root, run nvidia-settings
- projector is automatically detected by the tool
- select twinview mode (I tried also duplicate screen)
- nvidia-settings set default resolution for projector to 1920x...
- clic on "apply" (or save xorg.conf, restart gdm)
-> nothing is displayed on projector
-> my lcd PC screen got a black screen "no signal" and ubuntu is hanging (keyboard is out)

- The projector documentation tells that the resolution is set to 1280x720.
So I restart my test using a fresh xorg.conf file (working with just my lcd PC screen) and I have the same error

- I tried to put projector cable instead of my lcp pc screen but nothing is displayed through the projector
- I tried to boot my PC and a live cd with only the projector plugged on my video card and nothing is displayed
- I tried with another hdmi cable but still the same issue

I really don't want to go back to windows, so any helps are welcomed

thanks

---

### Post by ubick on 2008-09-20
solution is here
[http://forum.tuxx-home.at/viewtopic.php?f=1&t=493&p=4450#p4450](http://forum.tuxx-home.at/viewtopic.php?f=1&t=493&p=4450#p4450)

---

