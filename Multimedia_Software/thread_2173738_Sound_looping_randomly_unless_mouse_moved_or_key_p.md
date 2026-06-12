---
title: "Sound looping randomly unless mouse moved or key pressed.  Ubuntu 12.04 LTS"
date: 2013-09-11
forum: Multimedia Software
---

### Post by zombienerd1 on 2013-09-11
Hardware:  Toshiba NB-205 Netbook, HDA Intel sound, Codec: Realtek 272.

Issue:  While playing media from any source (Nightingale, VLC, Chromium, etc) random loops occur of about .25 seconds until the mouse is moved or a key is pressed (same .25sec sound bit played over and over in a loop).  It will sometimes go 20 minutes without doing it, and other times will do it every 10 seconds.

I am relatively new to Ubuntu, and Linux in general.  

I have scoured the web, and have read a few posts that have people describing similar problems, with some solutions mentioned;  I have tried most, but none have worked, and I've reverted the changes back to the original configurations.

One poster said to another user "[COLOR=#333333][FONT=Ubuntu Mono]the workaound is to reduce the fragment time (period size) less than rewind safeguard[/FONT][/COLOR]"  I have no idea how to do this, and no idea if it would help my issue at all.

Any help or suggestions would be appreciated.  All the "Sound issues" troubleshooters seem to deal with "No sound" conditions, and besides teaching me how to pull hardware info, were not helpful to me.


Thanks for any help.

---

### Post by zombienerd1 on 2013-09-12
Anyone?  This is annoying on the machine that is supposed to be my music box.  Maybe I'll try upgrading to 13.04 to see if the problem disappears or stays.  I won't have an internet connection for that box until next month though...

---

### Post by zombienerd1 on 2013-09-15
Update:

To see what happens, I put a few songs in VLC, set it to repeat, and left it alone for the night with the volume off.

Bingo, I got an error message sometime throughout the night.

---------------
Potential PulseAudio version problem:
PulseAudio is streaming with an excessive latency.  Sound may be lost or quality degraded.
to address that issue, upgrade the PulseAudio daemon to version 3.0, or disable the alternate sampling rate in its configuration.
---------------

Being I'm new to Linux, could anyone point me at which config file would contain the alternate sampling rate?  I'll also do some searching myself here shortly.

---

### Post by QIII on 2013-09-15
Hello!

The configuration for pulse is in /etc/pulse/daemon.conf -- and there may be a similar file in your /home directory.

Don't change anything yet, but could you tell me if you see a couple of lines as follows in those files:

```
; default-sample-rate = 44100
; alternate-sample-rate = 48000
```

---

### Post by zombienerd1 on 2013-09-15
> **QIII said:**
> Hello!

The configuration for pulse is in /etc/pulse/daemon.conf -- and there may be a similar file in your /home directory.

Don't change anything yet, but could you tell me if you see a couple of lines as follows in those files:

```
; default-sample-rate = 44100
; alternate-sample-rate = 48000
```

In /etc/pulse/daemon.conf  The default-sample-rate is commented out; there is no line for alternate-sample-rate.  

I don't appear to have a daemon.conf in my home folder.  I have a .pulse directory, but it only has a few .tdb files and the default-sink and default-source files.  There is also a .pulse-cookie file in my home dir.

I was hoping that was the problem, looks like my digging needs to go deeper.

---

### Post by zombienerd1 on 2013-10-15
Ok, I've upgraded to 13.04, and installed all updates.

The problem still occurs.  I'm darn near my wits end.  This is my primary machine for listening to music, and I can't leave it playing if I walk away, as it will start skipping and it annoys the heck out of anyone else around.

I think it's about time to find a new distro and see if the same problem occurs.

---

### Post by zombienerd1 on 2013-10-16
Probable Solution found.  2 hours without a skip yet.  I'll report again if it skips in the future.

Searching for others with the NB204, I came across a post from 2010 referring to 10.10, applied the recommended change, and so far it's good to go!

>sudo gedit /etc/default/grub

Find the line:
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/COLOR]
Change it to:
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer clocksource=jiffies"
[/COLOR]
Save file, exit gEdit.
then:
>sudo update-grub
>sudo reboot


From: [http://ubuntuforums.org/showthread.php?t=1619219&highlight=NB205](http://ubuntuforums.org/showthread.php?t=1619219&highlight=NB205)

> [COLOR=#000000]try adding "clocksource=jiffies nolapic_timers" to the kernel command line[/COLOR]
[COLOR=#000000]parameter.[/COLOR]

[COLOR=#000000]sudo pico /etc/default/grub[/COLOR]

[COLOR=#000000]change[/COLOR]

[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]

[COLOR=#000000]to[/COLOR]

[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapci_timer clocksource=jiffies"[/COLOR]

[COLOR=#000000]save changes[/COLOR]

[COLOR=#000000]sudo update-grub[/COLOR]

[COLOR=#000000]reboot[/COLOR]


[COLOR=#000000]sfranzyshen[/COLOR]

---

### Post by Mario_Quesada on 2014-02-09
I did find the file and replaced the line but could not save the changes. Should I save it with another file name?
It is not clear, you say sudo update-grub but I couldn't save the changes with the same file name.
Please explain, I'm new to Ubuntu
Thank you

---

### Post by trackp200 on 2014-05-28
> **Mario_Quesada said:**
> I did find the file and replaced the line but could not save the changes. Should I save it with another file name? It is not clear, you say sudo update-grub but I couldn't save the changes with the same file name. Please explain, I'm new to Ubuntu Thank you  Did you use:  ```
 sudo gedit /etc/default/grub
``` OR: ```
 sudo nano /etc/default/grub
``` OR: ```
 sudo pico /etc/default/grub
```

---

