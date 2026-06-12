---
title: "No sound after alsa-driver upgrade"
date: 2010-07-17
forum: Multimedia Software
---

### Post by Pulsar5271 on 2010-07-17
After following Alpho2K's guide on monespaceperso.org for upgrading the  ALSA driver to 1.0.23, my sound was taken out.  I've tried it twice;  once with 10.04 LTS, then with Studio 10.04 which I am posting from now.

I  have two sound devices in my machine: a Creative SB Audigy SE, and the  motherboard's onboard sound.  Both are being detected.  I've checked  alsamixer, pavucontrol, alsaconf.  I have surfed for answers high and  low, checked the Comprehensive Sound Problems Guide and others like it,  with little success.  I don't really care about the onboard sound; I  mainly want the Creative card to work.

The only reason I upgraded  from the stock versions of ALSA was because I had a problem while  playing WoW in Wine.  Just playing MP3s would do it too; the sound would  cut out after a while using it, and wouldn't come back unless I  rebooted.

I was able to get it to work under LTS somehow by  disabling my onboard sound in the BIOS just to see what happened.  It  seemed like after the onboard sound was no longer available as a device,  it had no choice but to send the sound to the Creative card, which  worked.  At the time I performed the alsa-driver upgrade under LTS, the  machine was detecting both sound devices.

After that I decided to  try Ubuntu Studio (for the preempt kernel), and the exact same thing is  happening.  This time, when I performed the upgrade, the onboard sound  was disabled, so the Creative card was the only audio device installed.   So currently, I have no audio whatsoever, even though everything SAYS I  do.

My audio applet is muted by default when I log in (that's  probably a red flag), so I raise the volume to 100%.  Alsamixer shows  that all the levels are around 81, which should be loud.  Pavucontrol  shows that the CA0106 device is the one marked for output, and since I  have the system sounds turned on, I can see that the system THINKS it's  making sound when I make it beep (hitting backspace on an empty terminal  line, or something like that).

I even tried re-enabling and  re-disabling my onboard sound, just to have something for Pavucontrol to  switch back and forth to, for troubleshooting.  I'm thinking of going  back to the 10.04 LTS, just because I know how to make it work.  But I  thought I'd prostrate myself before the community before I spend another  night on that.

My best guess?  When the alsa-driver upgrade is  taking place, it's mapping audio to a device one increment away from the  one it should be sending it to.  It would explain why, the first time I  tried it, it had two devices to send the audio out to, and disabling  one of them got it to default to the correct one.  The time I tried it  under Studio, there was only one device available at upgrade time, so  maybe it transparently mapped my audio into the void.  I don't even know  if that's the way it works, or if I'm way off base.  It's just a  theory.  It might also be some configuration that I don't fully  understand with audio processing under the realtime kernel.

I've  stayed up all night for 2 nights in a row now trying to get my WoW Linux  box to run right.  I'd be very happy if someone out there could provide  some insight into this.

---

### Post by lidex on 2010-07-17
I have no experience with ubuntu-studio, but there is a forum focused on that you may want to search/post to:
[http://ubuntuforums.org/forumdisplay.php?f=335]("http://ubuntuforums.org/forumdisplay.php?f=335")

---

### Post by Pulsar5271 on 2010-07-17
Thanks for the response.  I have looked there, but since this seems to be an Ubuntu-wide problem with the alsa-driver upgrade, not specific to Studio, I decided to post here.

A new day is worth a new look, though.  Thanks again.

---

### Post by Pulsar5271 on 2010-07-17
I've discovered something interesting.

When I run alsamixer, and hit F6 to "Select sound card", it shows two devices:

*******Sound Card****
* - (default)
* 0 CA0106
* (enter device name)
********************

Since my onboard sound is disabled, the CA0106 should be the only one available, and it's listed as device 0.  What's got me intrigued is the presence of the "negative" one at the top that it's defaulting to, like it's -1, which would come before 0, and which obviously is useless.

This seems to lend some credibility to my theory of the system sending all my sound output into the ether, behind the scenes.

I have tried specifying the CA0106 in that menu, and rebooting.  My sound still does not work, despite the audio applet and pavucontrol reporting that it does.  Perhaps there are some deeper configurations I'm not seeing, that are still set to send my sound output to "device -1".

Are my Lamb of God MP3s playing in the Minus World from Super Mario?

---

### Post by lidex on 2010-07-18
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

Per *markbuntu*:
> Audigy
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.

---

### Post by Pulsar5271 on 2010-07-18
Thanks, but I've already run out of patience.

I formatted my partition and went back to Ubuntu 10.04 LTS with the generic kernel.

I wish I had noticed your sig before, though.  I just used that upgrade script, and it went painlessly, even with the onboard sound enabled.  I guess that'll be handy if I want to plug other things in there, eventually.

Thanks for the help!

---

