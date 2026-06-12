---
title: "delay backend boot?"
date: 2012-08-03
forum: Mythbuntu
---

### Post by Mad_Professor on 2012-08-03
Is there a simple way to delay the start up of the mythbackend?
I've got mythbuntu 10.04 with mythtv 0.23.1
I got two HVR-1950 and they take time to initialize.

Something simple since the tuner box is a backend only, no frontend.

---

### Post by klc5555 on 2012-08-04
> **Mad_Professor said:**
> Is there a simple way to delay the start up of the mythbackend?
I've got mythbuntu 10.04 with mythtv 0.23.1
I got two HVR-1950 and they take time to initialize.

Something simple since the tuner box is a backend only, no frontend.

Add a "sleep 5" statement (or sleep 10, or 30, or whatever delay you have discovered you need) to the beginning of mythbackend's startup script.

---

### Post by Mad_Professor on 2012-08-10
Well that worked somewhat..

The problem I am having now is that every 24 hours my inputs become scrambled. Video is all garbled, no errors reported in backend.log or syslog or any log and only a reboot fixes it, hence why I need to delay my backend until my usb tuners are up.

 But now the problem I am having is, I have to hit watch tv twice before it can display video. It does the same thing in mplayer, might have something to do with the kernellabs driver I compiled, located here:

[http://kernellabs.com/hg/~stoth/hvr1950-cc/]("http://kernellabs.com/hg/%7Estoth/hvr1950-cc/")

What I'm trying to do is setup a cron job to reboot the machine every 24 hours.

Is there a way to execute mplayer twice in a script, and then exit then proceed booting the backend?

EDIT:

Let me rephrase it, LIVETV doesn't start on the first attempt with the error "video frame buffer failed too many times." Second attempt successful and works thereafter. I need a way to tune and try to capture video acouple of times on boot before proceeding to start the backend.

---

### Post by klc5555 on 2012-08-13
No Linux distro, not even Ubuntu, needs to be rebooted every 24 hours in order to function if it's configured reasonably correctly on correctly functioning hardware. I suggest that effort might be better invested in debugging the 24-hr tuner "scrambling" issue.

Does it happen at the same time every 24 hours regardless of use? Or does it happen only after a lengthy period of disuse? Is hardware or software power management putting the machine into an uneeded suspended or hibernation state from which the USB bus is having a hard time recovering properly?

With regard to the livetv issue, is the implication that while a first livetv invocation after boot fails, a first scheduled recording succeeds? Does livetv work properly the first time if a scheduled recording has happened prior? Have you deselected the setting "use quick tune for live tv only" so that the backend will try to tune livetv just as slowly as when tuning for a scheduled recording, which may yield better results?

The trouble with trying to invoke a dvb card (as opposed to an analog card) as a capture card at boot, but before starting the mythbackend would appear to be actually tuning the card (as part of this script) to a known mpeg stream that it can capture when the card is invoked. 

If, however, after rebooting livetv works properly after the tuner has done a scheduled recording, then it would appear that if your cron script is rebooting the machine regularly when no one is watching at time "X", then a simpler approach would be to have a manually-scheduled 1 minute recording set always to happen at, say, time "X" + 5 minutes. Storage would be set to "save one episode". Then, when the machine has rebooted and mythbackend has started, the scheduled recording tunes up your tuner, if that is indeed what you need in this situation.

But of course this is all pretty bass-ackward. The better approach would be to debug and correct the configuration issue leading to the daily reboot in the first place.

---

