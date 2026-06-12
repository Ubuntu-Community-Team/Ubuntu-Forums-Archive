---
title: "My volume controls appear to be possessed!"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by SAndresen on 2007-12-06
Hello, this is my first post in these forums, so I hope I am able to present my issue in adequate form.

I am currently using a Dell Inspiron 9300 notebook computer that initially came with Windows XP. Recently I had formatted the entire harddrive and installed Ubuntu 7.04 ("Feisty") over it. The soundcard on my system no longer works, so I am using a USB Creative X-Fi XMod external soundcard. I have ensured it is the default sound card.

The system worked great for me, except that I was unable to hear sounds from Flash (using Firefox). It turned out that as well, I could not hear system sounds - like the sounds Ubuntu makes when it starts up, shuts down, and the system sounds under the Sounds tab in System > Preferences > Sound. That being said, I could still hear the annoying beep under the Devices tab and music/sounds from music players, etc. I spent days trying to get this to work but no avail, until just tonight, I decided to try upating until Ubuntu 7.10 ("Gusty"), which is where things turned for the worse.

After "upgrading" the OS, my volume controls have seemingly become possessed by some ghost in the machine. The single-click on the icon (that brings up what I'm guessing is the master control) is simple enough, but when I try to scroll up, sometimes it will bump down upon reaching different "elevations" on the GUI dial. Additionally, the speaker has itself set to mute in the top right, and trying to uncheck the mute option does nothing to remedy this. This mute appears to have no effect on the sound itself though.

Double Clicking on the icon to get the PCM specific controls is where it gets really weird. By itself, moving the right PCM channel is quite normal, however, the oddities exist when trying to change the left PCM. Unless the right PCM is set to the very bottom, the left PCM will, after manually adjustment, automatically drop to the bottom - that is, unless I put it to the maximum, then it will stay there. If the mute in the top right hand corner is not showing, then it appears if I try ever to turn any volume dial I have access to.

Trying to change the volume using  the notebook controls or the soundcard dial (both of which would change the master volume perfectly before) now changes the PCM volume dials at complete random. The dials bounce around at random while I hold the volume up button, while pressing the volume down button once leads to the sound of the left one going completely to the bottom and the right now being just slightly above the left. Pressing the mute button twice gets rid of the mute setting on the master volume (and in fact seems to be the only way to do so, not that it does anything), but by pressing volume down, it comes back right away.

Now you're thinking I should try linking the left and right channels. Any attempt to change the volume unlinks them immediately - even changing the master volume up and down shifts the PCM volume dials around randomly.

I've spent the last 2 and a half days going through various forums and Google and what I am left with is the following:
 - The original issue I had persists.
 - I can hear music, however, my ears are at the mercy of the ghost of my machine, as to how loud each headphone speaker is (the left-channel is the left-ear phone and the right the right-ear phone).

I have given up on trying to listen to sounds from Flash via Firefox and now I would like very much to just be able some sounds on my computer. Your input is very much appreciated.

---

### Post by SAndresen on 2007-12-06
Nobody's ever heard of this before or has any idea what's causing it?

:(

---

### Post by ThrashJazzAssassin on 2007-12-06
Is the problem still there when you boot from the Gutsy live CD?

---

### Post by SAndresen on 2007-12-06
I didn't upgrade to Gutsy with a CD. The CD I have is Feisty and I upgraded via the upgrade/update manager. I will try booting from that now.

---

### Post by SAndresen on 2007-12-06
I am currently running off the Feisty disc, and the volume controls are behaving as they should. Still, the original problem persists (no system sounds, no sounds in Firefox, but sounds everywhere else).

---

### Post by ThrashJazzAssassin on 2007-12-06
You already said the mixer works in Feisty.

This is a bug and has been reported [https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/158590]("https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/158590")

---

### Post by SAndresen on 2007-12-06
Ah, not once did I ever find that bug. Sorry and thank you.

---

### Post by SAndresen on 2007-12-06
Except trying to access the alsamixer gets me this:

> amshaun@shaun-laptop:~$ amixer
amixer: Mixer attach default error: No such device
shaun@shaun-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

---

