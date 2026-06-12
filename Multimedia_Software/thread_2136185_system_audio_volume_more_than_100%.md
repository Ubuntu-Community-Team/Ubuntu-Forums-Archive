---
title: "system audio volume more than 100%"
date: 2013-04-16
forum: Multimedia Software
---

### Post by alokmahor on 2013-04-16
Hi all,

in Ubuntu(unity/Gnome desktop) we can increase system audio volume more than 100%. how does that work?

how can I enable increasing system volume more than 100% in KDE or other desktop?


thank you

---

### Post by Feathers McGraw on 2013-04-17
I'm also interested in a solution to this.

As it is, I'm getting by using VLC with the volume at 200%, although I'm getting quite a lot of distortion.

Also, I had noticed that the default setup in Kubuntu had the keyboardvolume controls changing the wrong volume (for me there are two: "Built-in Audio Analogue Stereo"; "Cedar HDMI Audio [Radeon HD 5400/6300 Series] digital Stereo (HDMI)")...increasing the volume using the keyboard was showing that the volume was 100%, but the one I actually wanted was at about 50% and not affected by the keyboard controls. Changing the default sorted it out.

Feathers

---

### Post by hainen on 2013-04-17
If you use veromix as mixer plasmoid it can go past 100% volume. 
Another alternative is the official pulse audio volume control.

---

### Post by Aide9aic on 2013-04-21
I've used the Veromox Plasmoid for some time now, works well. If you choose this, be sure to disable KMix. Open the file **~/.kde/share/config/kmixrc**, find the line that begins with **AutoStart**, and change the value to **false**.

---

### Post by Feathers McGraw on 2013-04-21
Thanks guys, works like a dream!

For those that don't know, veromix is a widget that can be added by right clicking on the desktop.

I also had to assign my keyboard volume controls from kmix to veromix in veromix's settings.

Feathers

---

### Post by chuckiv on 2013-10-17
> **alokmahor said:**
> Hi all,

in Ubuntu(unity/Gnome desktop) we can increase system audio volume more than 100%. how does that work?

how can I enable increasing system volume more than 100% in KDE or other desktop?


thank you

find your kmixrc file

find / -name kmixrc

for me it is in /home/myname/.kde4/share/config/kmixrc

don't forget the dot "." before .kde4 or .kde because it is a hidden file

to edit file: sudo vi /home/myname/.kde4/share/config/kmixrc

press "i" to insert and add this line at the top under [Global]

VolumeOverdrive=true

now restart kmix or just restart your computer

while the onscreen volume still shows 100%, it is actually going to 153%, you should be able to notice that it's louder

if you need proof you can install pavucontrol with sudo apt-get install pavucontrol and that volume slider will show the 153%, but this step isn't needed. Kmix is going to 153% also. I promise ;p

---

