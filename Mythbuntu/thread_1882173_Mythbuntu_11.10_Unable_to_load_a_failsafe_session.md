---
title: "Mythbuntu 11.10: Unable to load a failsafe session"
date: 2011-11-16
forum: Mythbuntu
---

### Post by rmjohnson144 on 2011-11-16
I get this error when running mythbuntu live cd and it just doesn't startup at all:

```
Unable to load a failsafe session

Unable to determine failsafe session name.  Possible causes:  xfconfd isn't running (D-Bus setup problem); environment variable $XDG_CONFIG_DIRS is set incorrectly (must include "/etc", or xfce-session is installed incorrectly.
```

I searched for this error and all hits were for an upgrade of ubuntu and not from live cd.

I went ahead and installed Mythbuntu anyway and I don't have any mythbuntu interface at all.  It looks like a crippled regular Ubuntu install.  Very few options at all.

also, if I continue past the error I get a desktop with only two option in the upper right corner.  One is the power button symbol but it doesn't let me shutdown or restart.  The second button is a circle with a stick man in the center with options to change fonts.  Then there is a message on the backgraound anout installing Mythbuntu and a login screen covering the majority of the message.  I have to hit the power button to exit.

anyone know what is happening?
-=Mark=-

---

### Post by bobkat02 on 2012-01-10
Same behavior. Any suggestions?
 
Mythbuntu 11.10 64-bit
Gigabyte GA-M785GM-US2H / Athlon2 3000X2

---

### Post by rmjohnson144 on 2012-01-10
I gave up on 11.10.  I installed 10.04.3 LTS with great success.  I was able to get limited success on 11.04 and 11.10 didn't want to work at all.  I just gave up after getting 10.04 to work great.

wish you luck
-=Mark=-

---

### Post by bobkat02 on 2012-01-10
Mythbuntu 11.04 hasn't worked for me either, though it did get as far as the Partition Table before failing with other symtoms.  I was hoping that 11.10 would have overcome whatever problems 11.04 had.  I'm now downloading 10.10 to see if that works any better.  If not, I'll back off to 10.04 since it worked for you.
 
Since you got 10.04 to work have you tried installing upgrades toward 11.10?  If so, any luck, or are we stuck in history?  I realize that there are likely to be version mismatches between MythTV and Ubuntu that could pose challenges.
 
It is of some little comfort to know that I'm not alone in this.
==Bob

---

### Post by rmjohnson144 on 2012-01-10
I would definitely start with 10.04.3 LT.  It is the long term support. kind of like the stable release.

I forgot to ask what TV card are you using?  all cards work differently and some need special setup to get them to work at all.

you may want to search your specific card for help on setting it up.

Luck
-=Mark=-

---

### Post by asuastrophysics on 2012-03-06
> **rmjohnson144 said:**
> I get this error when running mythbuntu live cd and it just doesn't startup at all:

```
Unable to load a failsafe session

Unable to determine failsafe session name.  Possible causes:  xfconfd isn't running (D-Bus setup problem); environment variable $XDG_CONFIG_DIRS is set incorrectly (must include "/etc", or xfce-session is installed incorrectly.
```

I searched for this error and all hits were for an upgrade of ubuntu and not from live cd.

I went ahead and installed Mythbuntu anyway and I don't have any mythbuntu interface at all.  It looks like a crippled regular Ubuntu install.  Very few options at all.

also, if I continue past the error I get a desktop with only two option in the upper right corner.  One is the power button symbol but it doesn't let me shutdown or restart.  The second button is a circle with a stick man in the center with options to change fonts.  Then there is a message on the backgraound anout installing Mythbuntu and a login screen covering the majority of the message.  I have to hit the power button to exit.

anyone know what is happening?
-=Mark=-

Ubuntu 11.10 does not have an easy way to start a failsafe graphics session. What kind of video card do you have?

---

### Post by qyyy on 2012-04-12
I'm having the same problem running Mythbuntu 11.10 64-bit off a CD.

My graphics card is Nvidia 8800GT 512MB PCIe.

I'd guess the same problem results in my display running at a very low resolution. The locale selection window is way larger than what fits on the display. The display resolution is at 640x480, 800x600 or some such. It's a pain since you can't resize the window.

The full error message reads:
[QUOTE=Mythbuntu 11.10 64-bit CD Live session]Unable to load a failsafe session

Unable to determine failsafe session name.
Possible causes: xfconfd isn't running (D-
$XDG_CONFIG_DIRS is set incorrectly (must
include "/etc"), or xfce4-session is installed
incorrectly.[/QUOTE]

---

