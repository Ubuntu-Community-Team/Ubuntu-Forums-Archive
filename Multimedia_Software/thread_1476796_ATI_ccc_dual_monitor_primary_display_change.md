---
title: "ATI ccc dual monitor primary display change"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Kilcaff on 2010-05-08
Hello,

In a nutshell I want to change my primary display on an ati card.  I've gone into more detail below.

Since putting ubuntu 10.04 on my new pc I've been having some monitor issues.

I have an ati 5770 with a dvi monitor in front of me and a HD tv plugged in to the hdmi port for watching films and videos etc.

The problem is that ubuntu always assumes that the hd tv is the primary display, probably due to the card making that assumption.  I had ccc installed (10.3) but I couldn't get it to make the monitor my primary display.  

I looked at the xconfig file but don't really know what I'm doing with it and all the other threads Ive found eventually talk about nvidia chips or don't seem to answer the problem.

Anybody got this set up and working, I'm sure I'm not the only one with this tv/monitor combo on an ati card?

I don't mind not using ccc so long as I can still get the hd resolutions on my tv but when I uninstalled ccc I get graphics glitches and a black screen when I reboot.  It works fine if the tv isn't plugged into the hdmi port though.

Any help, it's doing me nut!

---

### Post by Kilcaff on 2010-05-10
Anybody any clues?

---

### Post by justinmc on 2010-05-15
I have the exact same issue. Currently digging through aticonfig and xorg.conf options to figure it out.:popcorn:

---

### Post by Alpha_Cluster on 2010-05-15
I also am having that issue. Mine is a bit different. Did you know you cannot use LeftOf with the 5770 and the driver that comes with 10.04? I know its not working here. I had to switch my monitor ports to switch the primary display I agree it doesn't make sense.

Btw did you try putting the DVI in the other port? Just a thought.

---

### Post by ctsbc on 2010-05-15
See here: [http://ubuntuforums.org/showthread.php?p=9239483](http://ubuntuforums.org/showthread.php?p=9239483)

---

### Post by Kilcaff on 2010-06-02
Sorry, not had chance to get on here or Ubuntu for a while.
I tried swapping the dvi port but that made no difference.
I'll have a play later and see if I can find anything.

---

### Post by Kilcaff on 2010-06-02
Found this:
 
[http://devinvenable.blogspot.com/2010/04/switch-primary-monitor-in-ubuntu-104.html]("http://devinvenable.blogspot.com/2010/04/switch-primary-monitor-in-ubuntu-104.htmlNot")
 
Not sure if it works, and never set up a script before but will have a go later tonight when I'm back at home.

---

### Post by youngheart80 on 2010-06-13
Add me to the list of people looking for this answer.  No luck with the display toggle mentioned above.  Haven't tried out the script yet.

---

### Post by irvie on 2010-06-27
Anyone have any ideas on this?

I need to switch my primary monitor from my laptop display to my external monitor when it's plugged in...

---

### Post by sero on 2011-01-14
The following seems to have worked for me.

First, configure dual monitors using the ATI control center.

Then edit (as root) /etc/X11/xorg.conf

Check for a section like:

```
Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option      "Monitor-LVDS" "0-LVDS"
    Option      "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
EndSection
```

Notice how LVDS (the LCD) is set as the first option. Make it the second so that the section looks like:

```
Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option      "Monitor-CRT1" "0-CRT1"
    Option      "Monitor-LVDS" "0-LVDS"
    BusID       "PCI:1:0:0"
EndSection
```

Save the file, restart the computer, and the primary display should be set properly.

---

### Post by abreneliere on 2011-01-22
> **sero said:**
> 
Save the file, restart the computer, and the primary display should be set properly.

It didn't work for me, primary is still the bad monitor.

---

### Post by gewone on 2011-10-12
> **abreneliere said:**
> It didn't work for me, primary is still the bad monitor.

Didn't work for me neither.
Will now try the approach mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=1382165").

---

### Post by oldos2er on 2011-10-12
Closed, necromancy.

---

