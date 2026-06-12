---
title: "No Sound On Kubuntu 11.10 AGAIN"
date: 2012-01-01
forum: Multimedia Software
---

### Post by Maleificus on 2012-01-01
Okay, here we go again, I just don't get it.

Okay so I have spent the past week in my dual booted Windows 7 so I could play Fable III, I come back to Kubuntu to find that my sound is not working on it, I opened PulseAudio and found that all the levels were set to where they needed to be, this is not HDMI this is just a regular vt1720 envy 24pt. Can anyone help with this?

---

### Post by inobe on 2012-01-01
are you the one with the broken audio port?

---

### Post by Maleificus on 2012-01-01
I had a broken audio port at one point but I bought a new sound card to replace the on board a while ago.

---

### Post by inobe on 2012-01-01
sounds like your audio controller gets switched somehow.

have you disabled the native sound device in the system bios?

---

### Post by Maleificus on 2012-01-01
Okay, I re-started to make sure that the on-board peripheral was disabled and it was but when Kubuntu booted back up I had sound again, I have tried re-booting three times to fix the problem and made no changes to anything on this re-start, what is up with that, and should I mark the thread solved yet?

---

### Post by inobe on 2012-01-01
no, don't mark as solved.

someone may see this.

if you go over to launchpad and report this as a bug, you may get help.

---

### Post by Maleificus on 2012-01-01
Okay thanks.

---

### Post by inobe on 2012-01-01
[https://bugs.launchpad.net/bugs](https://bugs.launchpad.net/bugs)

---

### Post by MoreOrLess on 2012-01-01
So you disabled your onboard audio chip and got sound? That's not a bug; you just needed to make the discrete card the default one.

---

### Post by inobe on 2012-01-01
> **MoreOrLess said:**
> So you disabled your onboard audio chip and got sound? That's not a bug; you just needed to make the discrete card the default one.

please read again!

> Okay, **I re-started to make sure that the on-board peripheral was disabled and it was** but when Kubuntu booted back up I had sound again, I have tried re-booting three times to fix the problem and made no changes to anything on this re-start, what is up with that, and should I mark the thread solved yet?

please don't hijack threads with useless, meaningless information, it only causes confusion:p

---

### Post by 4Orbs on 2012-01-02
Here's how I fixed the problem of disappearing sound on versions of Ubu/Xubu/Kubuntu that I've used.. 11.04 and 11.10. Look at post #3 [on THIS THREAD.]("http://ubuntuforums.org/showthread.php?p=11426771#post11426771") Be sure to open the file to be edited with the Kubuntu text editor, Kate rather than gedit (unless you already have gedit installed). NOTE: That thread relates to a vlc problem, but the fix also fixed disappearing sound (no sound after logging out then logging in again; sound returns after reboot). Seems like you have the same problem as I had.

---

### Post by Maleificus on 2012-01-02
Okay, I tried your method, rebooted and now I have no sound again.

---

### Post by 4Orbs on 2012-01-02
You have disabled your onboard sound in BIOS, but you also need to disable it in the Kubuntu sound settings by selecting "Off" from the dropdown menu for the unwanted device, and also make sure your new soundcard is enabled in the settings. You might try selecting pulseaudio as the default output device and if that doesn't work select instead the generic duplex option.

---

### Post by Maleificus on 2012-01-02
Yes, that was the first thing I did when I installed Kubuntu was to disable the on-board sound card, and I re-checked it and the profile is still set to off. As far as setting pulseaudio as the default sound output I can't find any setting that will let me do that. After several more restarts and removing your extra line I have sound again, I don't know how long that will last though.

---

### Post by 4Orbs on 2012-01-02
Just for clarification, you say you removed the extra line in the pulseaudio default.pa file. The only thing you should have removed (or previously added) was the "tsched=0" at the end of the line.

---

### Post by Maleificus on 2012-01-02
That's correct, sorry I mistyped. I removed the amendment that you specified.

---

### Post by 4Orbs on 2012-01-02
While your sound is working; Does it continue to work if you logout then log in again (not reboot)? Or logout and switch to another user account, then logout and log back in to your account?

---

### Post by Maleificus on 2012-01-02
Yes, yes it does.

---

### Post by 4Orbs on 2012-01-02
Is your Kubuntu 11.10 a new installation or was it an upgrade from a previous version? Is it installed on its own partition as a real dual-boot, or did you install it inside Windows using Wubi?

I have never used upgrades or Wubi, but from what I've seen from other posts both methods have caused headaches for some users. Last year I was using Kubuntu exclusively for a few months and it worked nearly perfectly after the workarounds were applied that I described previously. So, I am at a loss for any other helpful suggestions. I will add that I also had the Xfce desktop installed as a separate session with Kubuntu, but don't know if that had any influence on the successful usage of Kubuntu. I feel that it may have helped, but can't offer that as a possible fix for your problem.

Hopefully someone will come along and suggest a different fix that will really work for you. If I come up with any new ideas, I'll be back.

---

### Post by Maleificus on 2012-01-02
Yeah, it is installed on it's own partition.

---

### Post by 4Orbs on 2012-01-02
When the sound stops working, was it working for a while then suddenly stopped... all during the same login session or does it only happen between reboots/logins?

---

### Post by Maleificus on 2012-01-02
It happens in between reboots and logins.

---

### Post by 4Orbs on 2012-01-02
I'm not going to recommend or suggest this, but it is what I would try if I were in your shoes.

Open the Muon package manager and install the Pulseaudio volume control package (pavucontrol) and use it instead of Phonon to configure the sound settings.

Under the "Output Devices" tab, select the "Analog Output" port. Under the "Configuration" tab turn-off the internal audio device and under the dropdown for your discreet card select either "Analog Stereo" or "Analog Stereo Duplex" output.

The pavucontrol is a gtk application, so it may want to pull in a bunch of dependencies if you install it. So you are the one to decide if you want all the extra junk or not. I don't know if it will even fix your problem. But, as I said, it's what I would try.

If you install pavucontrol, it should show up in your multimedia menu.

---

### Post by Maleificus on 2012-01-02
Yeah, I already have that package installed, that is what I have been using to make sure the volume levels are correct and nothing is muted.

---

### Post by 4Orbs on 2012-01-02
O.K. Then have you checked in the kde settings manager that all the audio settings agree with the pavucontrol settings (no conflicting settings between the two)?

---

### Post by francoj11 on 2012-04-29
Did you solved your problem? I have the same problem, except that I suddenly lost the sound and never returned again, not even between reboots (in kubuntu 11.10, an then happened the same in a fresh install of kubuntu 12.04).

---

