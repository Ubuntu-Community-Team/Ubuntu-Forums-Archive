---
title: "Shutting off screensaver and other powersave?"
date: 2008-07-02
forum: Mythbuntu
---

### Post by zoiks on 2008-07-02
Mythbuntu 8.04, updated
Gigabyte P35-DS3L mobo w/ Intel E8400
nVidia Quadro NVS 285 w/ DVI out (DVI -> HDMI cable)
latest proprietary nVidia driver
Sharp Aquos HDTV LC-52D64U
KSI IR keyboard, PS/2 (with Sony RM-VL900 learning remote)
HDHomeRun + PVR500

First off, I'd like to make the claim that the screensaver (screen blanker) or some part of the power saving features seems to be messing up some of my hardware, in the following ways:

1) When the screensaver comes on for a period, and I bring the system back to life, the keyboard system tends to become flaky or sometimes unresponsive. This is characterized by poor reception from the learning remote (or the keyboard), sometimes getting a "stuck key" which repeats at a high rate (because the receiver hasn't properly registered that I have lifted the key) or otherwise just misses most of my key presses. This only happens when it comes back from power save mode. (Note: it is not going to standby or hibernation.) On a fresh boot, I don't have these issues with the keyboard response.

2) It's possible the power-saving state is also messing up the dedicated ethernet link to the HDHR. (There's a second Ethernet port using a PCI slot that I've set up for this purpose.) I have DHCP set to give it a particular IP address et al, and it always works when I reboot the HDHR and the mythbox, but sometimes when it comes back from screensaver mode I don't get any response from the HDHR and the second-from-left green LED on the HDHR just blinks. I'm not 100% positive it's the screensaver/powersaver at fault, but I think so. I'm not sure exactly the mechanism, either.

So, what I'd really like to know is:

How do I shut off the screensaver and the other powersave features completely? As far as screen blanking is concerned, this feature is somewhat useless for me, as it doesn't reduce power consumption on the Sharp TV, it just turns the screen black. I suppose it could prevent burn-in on the LCD, but my wife and I are pretty good about turning the TV off when it's not in use. I really just want to kill the screensaver and any other power saving features (except perhaps CPU scaling, which should be fine) to prevent problems.

I've tried 2 things so far:

1) I used gnome-screensaver-settings to turn off the screensaver. It took the settings, but the screen blanking still continues after 10 minutes.

2) Based on the advice of another thread, I've tried the following lines at the end of xorg.conf

```
Section "ServerFlags"
       Option "BlankTime" "0"
       Option "StandbyTime" "0"
       Option "SuspendTime" "0"
       Option "OffTime" "0"
       Option "ScreenBlank" "0"
EndSection

```

When these lines are used, the nvidia driver fails to load and I get some low-res default screen when it boots up, so it doesn't work at all.

Any help would be much appreciated.

---

### Post by zoiks on 2008-07-04
Bump.

No help? I just want to know how to shut off the screensaver, and would like to shut off any other power saving stuff except for CPU scaling.

---

### Post by db260179 on 2008-07-04
Install the gnome-powermanager, then in a terminal, run gnome-powermanager (because it doesnt create a shortcut)

This should turn off the powermanagement etc.

> **zoiks said:**
> Bump.

No help? I just want to know how to shut off the screensaver, and would like to shut off any other power saving stuff except for CPU scaling.

---

### Post by zoiks on 2008-07-05
> **db260179 said:**
> Install the gnome-powermanager, then in a terminal, run gnome-powermanager (because it doesnt create a shortcut)

This should turn off the powermanagement etc.

OK, so this is what I did:

```

sudo apt-get install gnome-power-manager
gnome-power-manager

```

Running gnome-power-manager just runs and then returns to the command prompt. Then I rebooted. Seems to be working, now the screensaver doesn't come on. Hopefully this solves the other problems I had.

Thanks!

---

### Post by zoiks on 2008-07-05
Well, crud, I spoke too soon. The screensaver (screen blank) still activates, only it takes 45 minutes instead of 10.

I have no idea who is even blanking it. Is it the nvidia driver? Some other gnome background thingy like gnome power manager? Is it XFCE? Is it xscreensaver? Is it myth? How do I find out?

At least my tests so far indicate however that it's not screwing up the IR keyboard receiver like it used to.

For those who care, the screensaver/blanker is kind of useless for us. The power consumption on our TV (a Sharp LCD TV) is not reduced when the screen goes blank. The backlighting is still turned on. If anything, it wastes power because it isn't as obvious that the TV is still on when myth blanks the screen, thus it backfires in a green sense. At most it might save some burn-in on the TV, but I'm not worried about burn-in.

So, any suggestions where to check/modify this new level of screensaver that's bugging me?

---

### Post by zoiks on 2008-07-06
Bump. No other help for this? How do I even find out who's blanking the screen? (It's not the TV itself, as the behavior is the same even if the TV's been off.)

---

### Post by jlagrone on 2008-07-06
you might try running gnome-power-preferences and making sure everything is set as you desire.  I believe it is installed with the power manager described above, but I could be wrong.

---

### Post by s3a on 2008-07-06
Why not just go to System-->Preferences-->Screensaver?

You should be able to turn off screensaver and change other things as well.

Hope that helps!

***Edit:** 
Sry, I didn't read all: "1) I used gnome-screensaver-settings to turn off the screensaver. It took the settings, but the screen blanking still continues after 10 minutes."*

---

### Post by zoiks on 2008-07-08
> **jlagrone said:**
> you might try running gnome-power-preferences and making sure everything is set as you desire.  I believe it is installed with the power manager described above, but I could be wrong.

Well, it looks like that may have done it. I ran gnome-power-preferences (didn't even know this existed!) and it had "Put Display to Sleep in: 40 minutes". Changed it to Never.

Many thanks! (Well, let's hope it actually works this time - I thought I had it licked last time. :) )

---

