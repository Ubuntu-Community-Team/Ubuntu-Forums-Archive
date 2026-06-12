---
title: "Projector or exteral monitor on a Laptop with Nvidia card"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by MarilenCorciovei on 2007-03-18
After trying several solutions for using an external monitor on my laptop with nvidia card I finally came to this one ([original article here]("http://www.len.ro/work/tools/external-monitor-on-linux-laptop-nvidia/")).

Hope it helps
[Len]("http://www.len.ro")


Goal
The goal of this effort was to use an external monitor or projector on a Linux based laptop (running Ubuntu Linux) equipped with a Nvidia video card:

    * should not require laptop restart
    * should not require X restart
    * should be simple enough


Hardware

    * Dell Inspiron 8600 and Dell Latitude D820 with Nvidia graphics card running at 1680x1050
    * External LCD monitor capable of 1680x1050 (this might not be always the case but surely the solution can be adapted)


First try
My first try was to just plug the monitor and press the Fn + F8 (CRT/LCD) button. Nothing happen even if this is how it should have worked. BUH! I don't have windows on my laptops but I found a similary laptop with Windows and this worked. Well, probably now it's a question of drivers. After searching the forums for a while and still nothing I came upon a solution which was supposed to work but it required the external device to be connected on when X started, not good.

The solution
Using the idea which I found on the forums I created a second configuration file /etc/X11/xorg.conf.external with the following device configuration:

```
Section "Device"
    Identifier     "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Driver         "nvidia"
    Option         "NvAgp"      "1"
    Option "TwinView" "Yes"
    Option "TwinViewOrientation" "Clone"
    Option "MetaModes" "1680x1050,1680x1050"
EndSection
```


Then I realized I can start a new X server on :2

```
Xorg :2 -ac -config /etc/X11/xorg.conf.external
```


And then in a new terminal start a window manager (I used WindowMaker as you cannot start gnome twice)

```
export DISPLAY=localhost:2 (here is where the -ac is used)
wmaker
```


I then switch to the new X with CTRL-ALT-F8 do my work and then finally when not needed anymore I close it without affecting my running X. In fact I found this method even handier as it's a sandbox for all the applications I want to show and I will not get disturbed during the presentation by an incoming mail or message.

---

