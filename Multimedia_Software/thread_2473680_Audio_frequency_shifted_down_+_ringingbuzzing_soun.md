---
title: "Audio frequency shifted down + ringing/buzzing sound during playback"
date: 2022-04-10
forum: Multimedia Software
---

### Post by daddingtonpalace on 2022-04-10
I gotta admit this is one of the stranger audio issues I've ever experienced. I believe this issue appeared after a system update in March as I first noticed the issue on March 25. I only noticed it when I joined a Zoom call where I noticed other participants sounded distorted (ringy, buzzy quality when they spoke). Then I noticed the frequency of a familiar person's voice was clearly shifted downward. Only after I wrapped up the call and I started playing some music on my system did I realize the issue was a local one, not some issue with Zoom.

So in summary. There the frequency of audio is 

Here be the deets.
[LIST=1]
[*]Ubuntu 21.10 x86_64 / 5.13.0-39-generic
[*]I have a setup with balanced lines to my speakers feed by a Scarlett 2i2 USB audio breakout box.
[*]Prior to the issue, the audio quality was just dandy.
[*]There are no issues with noise or ringing when there is no audio playing. The issue is present only during active playback.
[*]I can reproduce the issue in a newly create user account (having thought maybe it was a user configuration issue).
[*]I *cannot* reproduce the issue when booted to Windows.
[*]I previously installed some jack audio stuff when attempting to get lower latency audio. I removed all jack audio libs (which removed even rhythmbox and so on). At this point I had no audio. I reinstalled rhythmbox after which audio support returned, still with the ringing/distortion.
[/LIST]

At first I thought this was an issue with the DAC in my Scarlett or my machine, but after booting to Windows (and not reproducing the problem) it was clear this is a software-only issue.

I'm a little at a loss for how to approach the problem. Which system would be capable of downshifting the pitch of audio and introducing the ringing/distortion? Assuming there's some misconfiguration of this mystery system, how would I fix/reset it?

---

### Post by &amp;KyT$0P# on 2022-04-12
> **daddingtonpalace said:**
> I believe this issue appeared after a system update in March as I first noticed the issue on March 25.

What was updated in that system update?  Please check [FONT=Courier New]/var/log/apt/history.log[/FONT] (or one of the history.log.*.gz files, if history.log doesn't go back far enough) and post here the entry of the update that caused the problem.

---

### Post by daddingtonpalace on 2022-04-13
One issue here is I don't use this machine very often, and don't frequently play audio on it when I do login. So the issue could stretch a ways back in time.

Here's a link to the March update log. [https://docs.google.com/document/d/145iTLO09spalWBClUvYvPt4kpn0gtpZmL-2tGY4wMac](https://docs.google.com/document/d/145iTLO09spalWBClUvYvPt4kpn0gtpZmL-2tGY4wMac)

I don't honestly see much in the update that is related to audio related save an update to **alsa-ucm-conf:amd64** on March 3rd. There are a bunch of linux-modules-extra and headers and libc updates along the way that I suppose *could* somehow, handwavy, cause a regression in the audio system.

---

### Post by &amp;KyT$0P# on 2022-04-13
Do you still have the 5.13.0-35-generic kernel on your system?  Can you boot into 5.13.0-35-generic kernel and test if that fixes the issue?

---

### Post by daddingtonpalace on 2022-04-14
I only had the -37 kernel and the -39 kernels available. I tried booting back into the -37, but that didn't help.

Is there a way to install the older kernel using apt?

---

### Post by &amp;KyT$0P# on 2022-04-14
> **daddingtonpalace said:**
> Is there a way to install the older kernel using apt?

Try this, make sure it pulls in all 5 needed packages -
```
sudo apt-get install linux-{headers,modules-extra}-5.13.0-35-generic
```

---

### Post by daddingtonpalace on 2022-04-14
I should have been able to work through this on my own, but my linux-fu is rusty. So thank you for helping.

Good news, reverting to [COLOR=#000000][FONT=&quot]5.13.0-35-generic did the trick.[/FONT][/COLOR]

I noticed several usb-audio changes listed in [https://launchpad.net/ubuntu/+source/linux/5.13.0-37.42](https://launchpad.net/ubuntu/+source/linux/5.13.0-37.42). I'm using usb-audio, not the analog outs, maybe I can isolate the issue to usb-audio...see if the issue can be reproduced with the analog outs. I'll report back later, got run out now.

Thanks again!

---

### Post by daddingtonpalace on 2022-04-15
Confirmed that the behavior is specific to usb-audio only. The audio signal from the analog outs sounds totally normal.

---

### Post by daddingtonpalace on 2022-04-15
Found a fix!

There are several other reports of the same issue which is apparently caused by the default sample rate changing for external USB audio devices.

[https://askubuntu.com/questions/1399220/audio-crackling-after-update-in-usb-sound-card](https://askubuntu.com/questions/1399220/audio-crackling-after-update-in-usb-sound-card)
[https://askubuntu.com/questions/1398614/upgrading-to-5-13-0-37-generic-breaks-audio-with-external-audio-card](https://askubuntu.com/questions/1398614/upgrading-to-5-13-0-37-generic-breaks-audio-with-external-audio-card)

Oh, and there are a lot of me-toos on this reddit post.
[https://www.reddit.com/r/Ubuntu/comments/tkvjwu/this_is_why_i_love_linux_how_a_kernel_upgrade/](https://www.reddit.com/r/Ubuntu/comments/tkvjwu/this_is_why_i_love_linux_how_a_kernel_upgrade/)

The fix is to explicitly set default-sample-rate, which goes something like this:

$ sudo echo "default-sample-rate = 48000" >> /etc/pulse/daemon.conf

# then restart pulseaudio

$ (pulseaudio -k || sudo killall pulseaudio)

I'm not 100% clear what'll happen when I install Jammy, but hope this won't be an issue.

Thanks again halogen2 for the help.

---

