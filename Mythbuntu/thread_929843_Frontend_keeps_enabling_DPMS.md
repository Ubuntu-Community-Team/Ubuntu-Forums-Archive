---
title: "Frontend keeps enabling DPMS"
date: 2008-09-25
forum: Mythbuntu
---

### Post by NTolerance on 2008-09-25
I've got my combined backend/frontend connected to an LCD HDTV via a VGA cable.  I'm using onboard Intel X3100 graphics.  I need to completely disable any kind of screensaver or monitor power save features.  

Here's what I have tried in addition to disabling all GNOME power and screensaver options:

"Option" "DPMS" "false" in Device and Monitor sections of xorg.conf.

This:

```
Section "ServerFlags"
        Option          "Blank Time" "0"
        Option          "Standby Time" "0"
        Option          "Suspend Time" "0"
        Option          "Off Time" "0"
        Option          "NoPM" "1"
EndSection

```

and finally, this in .xsessionrc:

```
xset s noblank
xset s off
xset -dpms
```

I have MythTV frontend set to start automatically with GNOME.  I am running xset q to check the current DPMS status.  The .xsessionrc actually got DPMS disabled for a brief moment after an X restart, but it seems like when the frontend loads DPMS gets turned back on again.

My TV gets into a real funk when DPMS is on.  You can't change inputs or really do anything when it happens.  This leads to low WAF.  :(

---

### Post by NTolerance on 2008-09-26
bump

---

### Post by NTolerance on 2008-09-29
Here are the relevant parts of xset q when this problem occurs:

```
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0

DPMS (Energy Star):
  Standby: 1800    Suspend: 1800    Off: 3600
  DPMS is Enabled
  Monitor is Off

```

---

### Post by NTolerance on 2008-10-01
bump

---

### Post by NTolerance on 2008-10-06
Anyone got their myth box hooked up to an HDTV?

---

### Post by anonymousdog on 2008-10-06
In my searches, I keep seeing ```
Option "DPMS" "false"
``` and this bug [https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/200665](https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/200665)

---

### Post by NTolerance on 2008-10-07
> **anonymousdog said:**
> In my searches, I keep seeing ```
Option "DPMS" "false"
``` and this bug [https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/200665](https://bugs.launchpad.net/ubuntu/+source/xfce-mcs-plugins/+bug/200665)

In my case I'm using a Ubuntu + Mythbuntu setup.  Mythbuntu depends on XFCE4, so I had no choice but to install it via Synaptic.  I don't use XFCE4, so it would be nice to uninstall it and avoid any potential problems but I don't think there is a way to do this due to the dependency issue I mentioned.

Thanks for responding to my post.  

Does DPMS have any effect when using HDMI connections?  Maybe Mythbuntu users are using HDMI and they don't run into this problem.  My 40" Samsung HDTV has a well supported VGA input which I'm using.  It's supported so well that the TV responds to DPMS and goes into some sort of sleep mode when you switch to the VGA input via the remote control.  When it's in sleep mode the LED on the front of the TV starts blinking and it won't allow you to change to other inputs, essentially it's "dead in the water" from an end-user perspective.

---

### Post by newlinux on 2008-10-07
I have a frontend connected to a TV via HDMI and another one via VGA. Both work fine with DPMS for me. Only have a little bug on one of my TVs where if I press in the second the screensaver is just starting up, the screen will go black and won't return (all I see is a mouse). But waking up from a sleeping monitor or when teh screensaver is on is not a problem on either TV, neither is switching inputs.

---

### Post by NTolerance on 2008-10-07
> **newlinux said:**
> I have a frontend connected to a TV via HDMI and another one via VGA. Both work fine with DPMS for me. Only have a little bug on one of my TVs where if I press in the second the screensaver is just starting up, the screen will go black and won't return (all I see is a mouse). But waking up from a sleeping monitor or when teh screensaver is on is not a problem on either TV, neither is switching inputs.

So you're using DPMS and don't have the desire to disable it as in my case?  If so, how do you deal with the TV turning off when you switch to the HDMI/VGA input?

---

### Post by newlinux on 2008-10-07
My TV doesn't turn off when I switch. It just indicates there is no signal (which there isn't because the computer disabled the output), and as soon as I use the remote the computer reenables output and the signal is displayed as it should be. Of course if i switch when there is a signal (the output has not been put to sleep yet) then it just displays the signal (screensaver or desktop depending on the idle time).

DPMS works perfectly for me (with the exception of what i mentioned earlier) - goes to screensaver and turns off monitor if I idle to long, and wakes up the monitor as soon as I am no longer idle.

---

### Post by anonymousdog on 2008-10-08
BTW, a frontend log will record when DPMS gets enabled and disabled.

---

### Post by NTolerance on 2008-10-08
> **anonymousdog said:**
> BTW, a frontend log will record when DPMS gets enabled and disabled.

Provocative.

```
cat mythfrontend.log.1 | grep DPMS
2008-10-07 19:01:34.340 DPMS Deactivated
2008-10-07 19:03:10.230 DPMS Reactivated.
2008-10-07 19:06:14.023 DPMS Deactivated
2008-10-07 19:15:43.773 DPMS Reactivated.
2008-10-07 19:18:11.980 DPMS Deactivated
2008-10-07 19:34:48.507 DPMS Reactivated.
2008-10-07 19:34:49.861 DPMS Deactivated
2008-10-07 19:35:21.771 DPMS Reactivated.
2008-10-07 19:39:15.280 DPMS Deactivated
2008-10-07 19:41:40.603 DPMS Reactivated.
2008-10-07 19:42:36.950 DPMS Deactivated
2008-10-07 19:52:47.450 DPMS Reactivated.
2008-10-07 20:46:34.770 DPMS Deactivated
2008-10-07 20:47:16.010 DPMS Reactivated.
2008-10-07 20:47:51.237 DPMS Deactivated
2008-10-07 20:51:04.325 DPMS Reactivated.
2008-10-07 22:25:30.109 DPMS Deactivated
2008-10-07 22:51:23.239 DPMS Reactivated.
2008-10-07 22:54:17.509 DPMS Deactivated
2008-10-07 23:03:55.142 DPMS Reactivated.
2008-10-07 23:03:56.194 DPMS Deactivated
2008-10-07 23:21:10.907 DPMS Reactivated.
2008-10-07 23:21:12.964 DPMS Deactivated
2008-10-07 23:33:19.484 DPMS Reactivated.
2008-10-07 23:33:29.417 DPMS Deactivated
2008-10-07 23:53:03.952 DPMS Reactivated.
2008-10-07 23:59:20.309 DPMS Deactivated
2008-10-08 00:18:10.064 DPMS Reactivated.
2008-10-08 00:18:31.252 DPMS Deactivated
2008-10-08 00:35:58.567 DPMS Reactivated.
2008-10-08 00:42:34.276 DPMS Deactivated
2008-10-08 01:04:15.713 DPMS Reactivated.

```

I suspect that old versions of the frontend did nothing to alter DPMS settings, but a new feature was added recently that seems to want to enable DPMS regardless of overall system settings.  :(

---

### Post by newlinux on 2008-10-08
try moving those xset commands from ~/.xsessionrc to ~/.xsession and restarting your X server.

[http://www.gossamer-threads.com/lists/mythtv/users/349949?page=last](http://www.gossamer-threads.com/lists/mythtv/users/349949?page=last)

---

### Post by NTolerance on 2008-10-24
> **newlinux said:**
> try moving those xset commands from ~/.xsessionrc to ~/.xsession and restarting your X server.

[http://www.gossamer-threads.com/lists/mythtv/users/349949?page=last](http://www.gossamer-threads.com/lists/mythtv/users/349949?page=last)

.xsessionrc is still overridden by the frontend and .xsession causes X not to start.  Right now I've got my remote set up to run xset -dpms when I switch to my VGA input, but it only works half the time.  I guess the only thing I can do at this point is to put that in a cron job to run like every 10 minutes.

---

### Post by bmathis on 2008-10-24
> **newlinux said:**
> I have a frontend connected to a TV via HDMI and another one via VGA. Both work fine with DPMS for me. Only have a little bug on one of my TVs where if I press in the second the screensaver is just starting up, the screen will go black and won't return (all I see is a mouse). But waking up from a sleeping monitor or when teh screensaver is on is not a problem on either TV, neither is switching inputs.

Not to hijack the thread, but I was having the same issue. I know that if you wait the 5 minute timeout, or whatever it is, for the screen saver to kick in, wait until it goes full black, and then press a button on your remote or keyboard itll come back to life.

---

### Post by maniaq on 2010-02-28
hi this is a bump - anyone know how to solve this?

I'm not really having a problem per se but I just find it annoying when I turn on the tV in the morning and I'm greeted with a blank screen and I have to use the remote to get my picture back...

as per the previous log file, mine has a lot of:

> 2010-03-01 08:04:14.705 DPMS Deactivated
2010-03-01 08:21:09.626 DPMS Deactivated
2010-03-01 08:21:20.600 DPMS Deactivated
2010-03-01 08:35:38.244 DPMS Reactivated.
2010-03-01 08:35:47.574 DPMS Deactivated
2010-03-01 09:07:16.562 DPMS Deactivated
2010-03-01 09:14:30.553 DPMS Deactivated
2010-03-01 09:22:40.273 DPMS Reactivated.
2010-03-01 09:33:39.091 DPMS Deactivated
2010-03-01 09:33:58.716 DPMS Deactivated
2010-03-01 10:24:01.622 DPMS Reactivated.

...going on

why the hell would the myth-frontend want to enable previously deactivated DPMS settings anyway? Blank screens seems to me to be the complete **opposite **of what you want from your TV experience...

btw this doesn't affect playback - just the menu screens - is this to avoid burn-in of menus on CRTs? That's all good and well but the option to turn it off would be nice for the rest of us...

---

