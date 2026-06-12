---
title: "TV output is back to black and white"
date: 2009-07-30
forum: Multimedia Software
---

### Post by Gustavo Narea on 2009-07-30
Hello, everyone.

I have a Dell Inspiron 6400 laptop powered by Ubuntu 9.04 and connected to my TV set via S-Video (through an S-Video to SCART converter).

Except for the black & white output in the beginning, it worked out-of-the-box. I managed to make it output in color after spending hours googling for a solution to this common issue; this was the solution:
[LIST=1]
[*]Add the following lines to */etc/X11/xorg.conf*:
```
Section "Device"
        Identifier      "Configured Video Device"
# The new lines are the following:
       Driver "intel"
       Option "TVOutFormat"    "COMPOSITE"
       Option "MonitorLayout"  "TV,LFP"
       Option "TVStandard"     "PAL"
       Option "ConnectedMonitor"       "TV"
EndSection
```
[*]Run the following commands when I wanted to use the TV set, since it's configured to output in NTSC-M by default:
```
xrandr --output TV --set TV_FORMAT PAL
xrandr --output TV --auto
```
[/LIST]

Right after the last command, the TV output started working and it did so with color.

After a couple of days working like a charm, with the screensaver disabled and without changing any configuration file, I was watching a video when the image suddenly turned to black and white again. Since then I have no been able to fix it again.

Does anyone know something I could try to make it work again?

Thanks in advance.

---

### Post by Gustavo Narea on 2009-07-30
I got it!

Try this workaround if you face this problem:
[LIST=1]
[*]Turn your TV set on, in a mode it can receive the input from your computer ("AV" in my TV).
[*]Turn your computer on.
[*]Plug the cable.
[*]Run the following command:
```
xrandr --output TV --set TV_FORMAT PAL
```
[*]Hit Fn+F8 (this may change from one computer to another).
[/LIST]

I don't know if it has something to do, but in my TV set I changed to SVCR mode (it was just VCR).

HTH.

---

