---
title: "Onboard 7.1 card with analogue 5.1 system - hardly any subwoofer usage?"
date: 2010-04-15
forum: Multimedia Software
---

### Post by The Bright Side on 2010-04-15
Hey guys!

I'm getting confused about this: I am using my onboard 7.1 sound card and an analogue 5.1 sound system, and when I watch movies in stereo, I get really strong bass. However, when I switch to 5.1, the sound becomes tinny and weak (even though it's correct Surround).

When I watch e.g. Rambo (2008) or Matrix, the subwoofer hardly does anything even in the big action scenes. What throws me off is that it is not completely silent, there is _some_ bass - but it's next to nothing in comparison. It becomes painfully obvious when I switch back and forth between stereo and 5.1 in VLC's menus. All the main sound seems to come from the 5 other speakers. I can still get more bass by just manually turning up the sub (on my sound system), but e.g. Pandemonium by the Pet Shop boys does not seem to use the sub _at all_ when I view it in 5.1.

Mike Oldfield's 2009 remix of Tubular Bells, on the other hand, uses the subwoofer magnificently, and I have a little 5.1 test vid that shows that all speakers are addressed correctly; it runs through all kinds of frequencies on the sub and works splendidly.

This is the first time I'm using 5.1, but I can't believe that most DVDs are mixed so badly in surround. I unfortunately don't have any friends who have 5.1, so I can't compare... Does anybody have any idea what may be wrong, or are many DVDs just mixed that way in 5.1?

I'm using VLC media player and manually selecting 5.1 as input device there; system-wide, my sound profile is set to Analog Stereo Duplex.

---

### Post by The Bright Side on 2010-04-15
One more thing I noticed: if I select any audio profile other than the Stereo Duplex one in my system-wide sound preferences, say Analog Surround 5.1 Output, and then open e.g. Audacious to play music, the sound is tinny with little to no subwoofer. If I then bring up the sound hardware dialog again and select any other audio profile, the Subwoofer gets heavily involved.

It's only prominent in the mix right away if I have Stereo Duplex selected, with any other profile, I have to start the playback app and then switch sound profiles around in the Sound Preferences to "switch on" the subwoofer usage.

VLC seems to manage sound independently... When I have it open, it does not show up in my Sound Preferences as a currently running software (in the tab to the far right).

---

### Post by Yellow Pasque on 2010-04-15
You may need to install the vlc-plugin-pulse package to get VLC to route through pulseaudio. Also, this link may help: [http://gwos.org/udsf/doku.php/hardware:pulseaudio:surround](http://gwos.org/udsf/doku.php/hardware:pulseaudio:surround)

I guess it could also be an ALSA driver issue that could be fixed with an ALSA update, but that should be a last resort: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by The Bright Side on 2010-04-15
Thanks! I tried going through pulse, but the only setup that even allows me to select 5.1 is ALSA with a fixed output device. With all others, the "Audio Devices" dialog is greyed out in VLC.

I just spent another hour tinkering around with all the other settings I could find in VLC or Ubuntu, but to no avail. Most movies I have will sound pretty darn good if I manually turn up the sub, but there are quite a few DVDs that have no bass at all. Mostly Region 2 DVDs, actually.

Thanks anyway!

---

