---
title: "Lenovo T61 &amp; 9.10 - some sounds, but none in Emacs"
date: 2010-01-10
forum: Multimedia Software
---

### Post by Joe Casadonte on 2010-01-10
Hi,

I've installed Ubuntu 9.10 on a Lenovo T61.  I get some sounds, but not all of them.  For example, I get sound when I startup the machine, sound when I login, sound from RhythmBox.  I can't get some sounds out of Emacs, though -- hitting C-g gives me no sound, but running:

```
 (play-sound-file "/home/me/foo.wav")
```*does* play a sound.

I've reinstalled all alsa sub-components, pulse audio and run through all of the trouble-shooting guides I can find on the net.

Does anyone have any ideas?  Thanks!


joe

---

### Post by Joe Casadonte on 2010-01-11
I knew there was another example of my problems besides Emacs, but I couldn't remember it.  Thunderbird has a setting to play the default system sound when new mail comes in.  That does nothing on my system.  If I set it to a specific wav file, though, that gets played as expected.

I can go into System > Preferences > Sound > Sound Effects and choose an alert sound (which is what I would expect Emacs and T-Bird to be using).  When I select a new sound, I do hear it play.  However, outside of this preference dialog box, I've never heard it.

So possibly this is tied up in the "system alert sound" somehow?  Thanks for the help!

---

### Post by Joe Casadonte on 2010-01-18
Evidently in 9.10 the PC speaker is disabled by default:

[https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/77010](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/77010)

Why they "solved" this issue by disabling the speaker is beyond me; like many others, I feel the real solution is to let Gnome deal with the sound. That would be a way better default behavior, IMHO.

So, to get the behavior I desired (turn on the beep but replace it with a gentler sound) I did the following:

Edit the /etc/pulse/default.pa file and add the following lines at the bottom of the file:

```
load-sample drip-ogg /usr/share/sounds/gnome/default/alerts/drip.ogg
load-module module-x11-bell sample=drip-ogg
```Then add the following lines to my ~/.bashrc file:

```
xset b on
pactl load-module module-x11-bell sample=drip-ogg >/dev/null
```The result is a pleasing system alert sound that's available pre-login, and the same pleasing system sound available post-login, but only after I've brought up a terminal window (which I nearly always do first thing anyway).

The "xset b on" turns the alert sound back on, and the "pactl" line replaces it with a more pleasing sound.  I haven't yet figured out how to do the "xset" bit globally (putting it in /etc/X11/xinit/xinitrc didn't work for me), nor have I figured out a way to do without it (simply commenting out the "pcspkr" line in /etc/modprobe.d/blacklist.conf didn't do it).

Occasionally I get both the system beep and my more pleasing sound both happening at once; when it does happen, simply re-running the "pactl" line fixes the issue (which I can do by opening up another terminal window).  It's not an ideal solution, but it works well enough for me.  I hope this helps someone else!

---

### Post by rifter on 2010-03-02
> **Joe Casadonte said:**
> Evidently in 9.10 the PC speaker is disabled by default:

[https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/77010](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/77010)

Why they "solved" this issue by disabling the speaker is beyond me; like many others, I feel the real solution is to let Gnome deal with the sound. That would be a way better default behavior, IMHO.

So, to get the behavior I desired (turn on the beep but replace it with a gentler sound) I did the following:

Edit the /etc/pulse/default.pa file and add the following lines at the bottom of the file:

```
load-sample drip-ogg /usr/share/sounds/gnome/default/alerts/drip.ogg
load-module module-x11-bell sample=drip-ogg
```Then add the following lines to my ~/.bashrc file:

```
xset b on
pactl load-module module-x11-bell sample=drip-ogg >/dev/null
```The result is a pleasing system alert sound that's available pre-login, and the same pleasing system sound available post-login, but only after I've brought up a terminal window (which I nearly always do first thing anyway).

The "xset b on" turns the alert sound back on, and the "pactl" line replaces it with a more pleasing sound.  I haven't yet figured out how to do the "xset" bit globally (putting it in /etc/X11/xinit/xinitrc didn't work for me), nor have I figured out a way to do without it (simply commenting out the "pcspkr" line in /etc/modprobe.d/blacklist.conf didn't do it).

Occasionally I get both the system beep and my more pleasing sound both happening at once; when it does happen, simply re-running the "pactl" line fixes the issue (which I can do by opening up another terminal window).  It's not an ideal solution, but it works well enough for me.  I hope this helps someone else!

Thank you for your helpful post. It did indeed help me with fixing the bell.  You might also refer to _[color=blue][this bug](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154)[/color]_ which directly attempts to address at least some of the issues.  _[color=blue][this comment](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/486154/comments/50)[/color]_ gives some instructions that might be helpful as well, and [thread=1331186]this thread[/thread] gives some further enlightenment.

I like what you did in changing the bell's sound, and I think I will tackle that once I am sure I have the bell on everywhere I can find it. Unfortunately there are more places to look, and as the post in the bug indicates, the game is yet afoot in that regard.

I am concerned about the statements that say that xset b is still not setting the volume.  I don't know if that is fixed or not.  I do an 

xset b 100

everytime after having done all this other stuff, and the bell comes back, at least within the gui. It concerns me that there may yet be more places to look, and alerts I may be missing because the bell is neutered in so many places.

Anyway thanks for having an informative thread.  I hope that people who have this problem find this information.  It was not easy to find a thread on turning *on* the system bell, and these threads and the bug info were the most helpful.

---

### Post by Joe Casadonte on 2010-06-14
And....as an FYI to folks, it's broke again in 10.04 -- it's enough to make me find another distro.

---

