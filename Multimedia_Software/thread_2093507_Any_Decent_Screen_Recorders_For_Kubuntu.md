---
title: "Any Decent Screen Recorders For Kubuntu?"
date: 2012-12-10
forum: Multimedia Software
---

### Post by jlacroix on 2012-12-10
Hello everyone. I've spent the entirety of my night trying to record a Linux tutorial video to put up on Youtube. To say this night has been an epic fail would be an understatement.

I normally use qt-recordmydesktop with most Linux distributions, but for some reason it isn't available for Kubuntu so I installed gtk-recordmydesktop instead.

gtk-recordmydesktop crashes every time I move my mouse cursor outside of the frame, which I do constantly on accident. So basically I have to make sure I _do_not_ touch my mouse, or goodbye screenrecorder and everything I've recorded so far.

Is there a decent screen recorder for Kubuntu? recordmydesktop is a joke.

---

### Post by cybrsaylr on 2012-12-11
I've had great luck with Kazam. It works great.

---

### Post by dannyboy79 on 2012-12-11
i use ffmpeg/avconv myself. there's many scripts out there but this is one I use to stream to justin.tv or twitch.tv but you can just change the output from streaming to justin.tv to just save it to a file. Interesting also as it can capture your desktop sounds and also a microphone if you want it to using pulseaudio loopbacks.

[http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html](http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html)

---

### Post by monkeybrain2012 on 2012-12-11
kazam is the best and easy to use.

Add the ppa
[https://launchpad.net/~kazam-team/+archive/unstable-series](https://launchpad.net/~kazam-team/+archive/unstable-series)

---

### Post by FakeOutdoorsman on 2012-12-11
A good ffmpeg screencasting guide is on these forums:

[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719)

---

### Post by jlacroix on 2012-12-11
Thanks for the responses everyone. I'm not interested in a script, I'd rather have a quick and dirty GUI solution. Kazam seemed like it would be a good option, but unfortunately, it doesn't work for me. When I run it in a terminal, I get this:

```
ERROR Kazam - Could not find any typelib for Wnck
Traceback (most recent call last):
  File "/usr/bin/kazam", line 134, in <module>
    from kazam.app import KazamApp
  File "/usr/lib/python3/dist-packages/kazam/app.py", line 39, in <module>
    from kazam.frontend.window_area import AreaWindow
  File "/usr/lib/python3/dist-packages/kazam/frontend/window_area.py", line 29, in <module>
    from gi.repository import Gtk, GObject, Gdk, Wnck, GdkX11
ImportError: cannot import name Wnck

```

---

### Post by dannyboy79 on 2012-12-11
finding a quick and dirty GUI solution will prove to be very irritating, give in to the command line and the script and it just works!

---

### Post by jlacroix on 2012-12-11
Is it possible to record a specific window with the commandline? I didn't see that part.

---

### Post by deadflowr on 2012-12-12
Did you try RecorditNow. It works with recordmydesktop but its built for KDE. 
It's in the repos.
Agreed though, gtk-recordmydesktop is utter garbage in Kubuntu.

---

### Post by FakeOutdoorsman on 2012-12-12
> **jlacroix said:**
> Is it possible to record a specific window with the commandline? I didn't see that part.

Yes, there are several methods described in the [screencasting guide](http://ubuntuforums.org/showthread.php?p=8746719#post8746719) mentioned in my previous post. See the FAQ, specifically:
[list]
[*]Q: How do I get the exact size and coordinates of a specific window I want to capture?
[*]Q: I want to select an area of the screen with my mouse and get ffmpeg to record it. Is it possible?
[/list]

FFcast is worth mentioning. It allows you to click the window(s) you want to record or draw the recording area with the mouse (basically the methods as shown in the FAQ but maybe more convenient). I doubt it is in the repos, so you'd have to compile it. I wrote a [mini-guide](http://ubuntuforums.org/showpost.php?p=9902784&postcount=79) a few years ago to do just that--it is outdated but I can't easily edit my own post due to some questionable new forum policy, and the forum overlords killed the Tutorials & Tips section anyway.

---

### Post by jlacroix on 2012-12-12
> **deadflowr said:**
> Did you try RecorditNow. It works with recordmydesktop but its built for KDE. 
It's in the repos.
Agreed though, gtk-recordmydesktop is utter garbage in Kubuntu.
Looks like a great solution! I'll go ahead and mark this solved. Thank you!

---

