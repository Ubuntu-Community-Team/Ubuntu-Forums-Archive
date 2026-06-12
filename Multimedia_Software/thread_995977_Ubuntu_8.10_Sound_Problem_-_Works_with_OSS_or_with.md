---
title: "Ubuntu 8.10 Sound Problem - Works with OSS or with PulseAudio at Startup Screen"
date: 2008-11-28
forum: Multimedia Software
---

### Post by GuitarStv on 2008-11-28
Please bear with me, as I'm a new Ubuntu user . . .

When I first loaded up Ubuntu 8.10, sound wasn't working with whatever the default options were so I went to System->Preferences->Sound and clicked on the only thing that seemed to make a sound upon pressing the play button (OSS).  This worked great for Rhythmbox music player, and for watching videos, but I couldn't seem to get audio from more than one source.  I couldn't get audio from youtube or any other flash players online.

That lead me to a post on the forums here.  I have followed all the instructions here ([http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")) to set up Pulse Audio, to no avail.  I ended up with no sound, but I could see items being added (and trying to play) in the PulseAudio->Volume Control->Playback Tab.

Even stranger . . . while there is no sound when I'm logged in, I hear a little drumbeat every time that I log out and the login screen comes up.  Anyone have any idea what I can do to get sound working properly?  At this point I'd really appreciate someone who could point me in the right direction!

---

### Post by Racer-X on 2008-11-28
I had issues with the PCM volume being down all the way.  What I thought was going to be an involved fix turned out to be very simple.

It was noted in the link you referenced under Appendix A, point c.  It's not really the most intuitive thing to find, though.

Right-click on your speaker icon in the tray, select preferences.  A window will pop up.  Select your Alsa mixer; mine is: HDA Intel (Alsa Mixer).  From there select PCM.  If you look back up at your speaker icon, it should not be zeroed out.  If it is, turn it up and you should have sound again.

---

### Post by GuitarStv on 2008-11-28
Nope, I already did that.  No volumes are muted on anything that I can tell.  I get sound occasionally through Pulseaudio (like when I go out to the login screen), but never while I'm actually using my computer.  If there's any additional information about my computer that might help with this problem, please just let me know and I'll get it to you.

---

### Post by Darrenor64 on 2008-11-29
I have a similar problem. Sounds work in GDM, but fail as soon as the gnome session start.

However, it was not a problem when I first installed the system, it started after a restart (possibly after the installation of several programs).

I first noticed it when Pidgin would hang during any sound event. I went to sound preferences, and changed all sound playback options to OSS, since it worked, and the problem was solved for most applications, but like the other user noted: not all programs were successful with sound.

Under Sound Preferences, when I test sound playback under "Auto-detect" or "Pulseaudio", an error popup says:

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample !
gconfaudiosink: Failed to connect stream: Invalid argument"

This popup refuses to close.

The error message for ALSA reads:

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample !
gconfaudiosink: Could not get/set settings from/on resource."

This second error message does close.

I am running Ubuntu 8.10, 64-bit.

Update:

I went to
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
Oddly enough, my user group set didn't include 'audio'. I added it, but it didn't solve the problem.

[http://www.alsa-project.org/db/?f=ba2aa9a2279cfb064b7592108157f0ffb9e85f29](http://www.alsa-project.org/db/?f=ba2aa9a2279cfb064b7592108157f0ffb9e85f29)

---

### Post by Darrenor64 on 2008-11-29
I started running 'pulseaudio' in the console, and now I am able to test the audio settings in 'autodetect'.

Now it seems I just need to find a way to make sure that pulse audio is always started. What's the best place for this?

---

### Post by Darrenor64 on 2008-11-29
$ pactl load-module module-x11-xsmp
Failure: Module initalization failed

I think this may be the root of my problem.

---

### Post by Darrenor64 on 2008-11-29
Anyway, the resulting solution that worked for me required me to do a 'complete removal' of pulseaudio (this also required a temporary removal of 'ubuntu-desktop' with synaptic.

I rebooted after this, and watched my system deal with a choppy alsa management of sound.
I reinstalled ubuntu-desktop (which also included 'pulseaudio'), and after another reboot, everything is working fine.
To enable surround sound, I had to add it to the mixer (through preferences), and put the volume up. Everything is working fine now.

---

### Post by Darrenor64 on 2008-11-29
And now it's disabled again.
Except this time instead of erroring out, it is mute.

---

### Post by markbuntu on 2008-11-29
I just posted a little guide for Intrepid for just that sort of problem. Give it a try and let me know how it works for you:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by GuitarStv on 2008-12-01
Thanks mark!  Your guide worked, and I now have functioning sound . . . I really appreciate it.

---

### Post by Darrenor64 on 2008-12-03
I was not successful with that guide.
However, it brought me to updated Creative XFI drivers, which I compiled and installed. Strangely enough now that sound card will work, but by other card isn't recognized by the pulseaudio system after I log into gnome, unless I run the following commands:

pulse_pid=(`ps -A | grep pulseaudio`);
kill ${pulse_pid[0]};
pulseaudio

For some reason pulseaudio needs to be restarted in order to detect the non-xfi sound card as an output device.
There is also a usb-input sound device connected to the computer.

---

### Post by markbuntu on 2008-12-03
I notice that you are not starting pulseaudio with the defaults so it is probably something in /etc/pulse/default.pa  or /etc/pulse/daemon.conf that is causing the problem. Did you edit these files?

---

### Post by Ozzyx09 on 2009-02-02
> **markbuntu said:**
> I just posted a little guide for Intrepid for just that sort of problem. Give it a try and let me know how it works for you:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

hey i've done all your steps up to the part where i have to choose Volume Control on the new icon and when i do it tells me Connection failed: Connection refused please help me on this i'm a new Ubuntu user thanks

---

### Post by markbuntu on 2009-02-02
OK,there is a very extensive troubleshooting guide here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Adventum on 2009-09-19
I had the same issue on 8.10. After a couple of hours in searching the forums for sound problem in Ubuntu I found very simple solution. When you go to Sound Preferences and at devices you have to choose different device at every dropdown, and do not let any of them on auto detect option.
To see if device is working for you just click the test button for the device.

---

