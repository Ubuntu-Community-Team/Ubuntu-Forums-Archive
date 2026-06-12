---
title: "Black screen on lcd after no usage (only on dvi out)"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by Sean R on 2007-11-01
Hello!

I'm experiencing an issue where after not using my computer for about half an hour, the screen goes black. The only way to recover the desktop is by control-alt-backspacing to restart the xserver.

Hardware involved is: ATI 9500pro with fglrx 8.42.3 (latest version). My tv is a 42" Toshiba Regza and it is connected via a dvi-hdmi cable. This issue only seems to happen while using the dvi-hdmi to the tv @ 1920x1080. If I'm using a vga-vga cable between the pc and the tv and running at 1024x768 there is no problem.

I have already tried disabling the screensaver, stopping acpid, and stopping apmd... non of which produced any change.

I understand that I'm using restricted drivers, but I thought I'd post my problem to see if anyone has any ideas for a fix. Thanks in advance!

Sean R

---

### Post by Light- on 2007-11-01
This seems to be related to the "DPMS" thingy that turns your monitor off after a while (power saving).

Try this:
type "sudo gedit /etc/X11/xorg.conf" (without the quotes into a terminal), and browse to the monitor section of the file. Put a # before "Option	"DPMS"" to comment out the line, and restart your computer. The monitor should now not turn off automatically.

Problem is, it will always be going, unless you use the power button to turn it off and on (this doesnt work for me, if i use the power button to turn it off, it goes off and gives me "no signal" when it comes back on) but it might work for you.

---

### Post by Sean R on 2007-11-01
Thanks for your input, I appreciate it.

Unfortunately, that did not solve the issue. When I rebooted I had no video coming through to the tv. After hitting Control-Alt-Backspace to restart the xserver, it worked again.

The issue is rather strange... you would think that whatever happens when the xserver restarts (with Control-Alt-Backspace) would be similar to what happens on an entire system bootup. There must be something happening when restarting the xserver that doesnt happen on a system boot... or perhaps there is a synchronization issue between the tv and the pc.

Anybody else have an idea?

Thanks!

Sean R

---

### Post by Sean R on 2007-11-02
Disabling DPMS did fix the issue. When I boot I have to control-alt-backspace to restart the x server, but after that everything works fine. After the pc being for the night, no more black screen.

Thanks for the help!

Sean

---

### Post by Sean R on 2007-11-09
Okay, the issue is back now. DPMS is still disabled. It doesn't seem to matter what resolution I'm using, I get a black screen after the pc has not been used for approximately 30 minutes. Still, the issue is only while using DVI-HDMI. VGA has no problems.

Any ideas?

Thanks!

---

### Post by Sean R on 2007-11-13
Finally figured out what the problem was. I noticed a lot of people have viewed this thread so I thought I'd give anyone else experiencing the same issue the fix.

Open /etc/default/acpi-support as root and find the line:
# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

Change true to false. Save and close.

Sean

---

### Post by dell500 on 2008-03-24
I was wondering what your xorg.conf file has for getting the Toshiba Regza TV to work under unbuntu.  I've got a GeForce 8800.

dell :ninja:

---

