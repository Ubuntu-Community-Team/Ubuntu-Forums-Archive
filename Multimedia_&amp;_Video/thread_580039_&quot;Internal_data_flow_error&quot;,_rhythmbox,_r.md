---
title: "&quot;Internal data flow error&quot;, rhythmbox, radio, Gutsy"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by yang on 2007-10-18
After letting one of the default radio stations (HBR) play in Rhythmbox for some time (anywhere from a few minutes to an hour), music stops playing. It does not abruptly stop, but seems to occur only when a track ends. The Play button is still depressed; releasing it and pressing it again gives me (after a second) the "Internal data flow error" message.

Trying to play other radio stations, gives the same error. Restarting Rhythmbox makes the issue go away.

This is on a fresh install of 7.10. My machine is a Dell XPS 410. I have not yet installed any of the codec packages.

I saw posts about this error message, but they seem to concern different issues.

---

### Post by barakaspeed on 2007-10-25
I am having the exact same issue with a fresh install.  I came across this result first and am still looking for a solution.  If I close and restart Rhythmbox and reconnect to radio and works again for another couple minutes.

---

### Post by redboar on 2007-10-27
Me three.  Same symptoms, and I can restart musicbox.  I get about 10-15 minutes of music each time on HBR1.  Any solution?

---

### Post by metasyntax on 2007-10-31
edit: never mind, my solution didn't do much.  Mark me down as having this on 2 separate gutsy machines, one was a fresh install, the other an upgrade from feisty.  I haven't found an exact reference to this in the bug database, but if I'm energetic I may open one tomorrow.

meta

---

### Post by SDL on 2007-11-03
I've got the same problem. I can only listen to half a song on Virgin Radio before it stops. I've got almost all of the G-streamer plugins installed from 'Add/Remove'.

---

### Post by Pulshion on 2007-11-07
install gstreamer instead of xine, worked for me

---

### Post by yang on 2007-11-07
huh? i don't think anyone mentioned xine on this thread so far.

---

### Post by Pulshion on 2007-11-08
I know no one mentioned but thats what happened with me. I had xine installed and it gave me the same error, i installed gstreamer and radio worked

---

### Post by SDL on 2007-11-10
Unfortunately, I'm already using the GStreamer version. Any other suggestions?

My problem isn't isolated to internet radio, either. When I'm listening to MP3's, after a while, Rhythmbox will freeze and require restarting.

Thanks for any help.

Stephen.

---

### Post by SDL on 2007-11-16
Hi. I think my problem is fixed. [This thread]("http://ubuntuforums.org/showthread.php?t=594069") gave me the idea to launch Rhythmbox from the Terminal. I then received the error:
```
sh: jackd: not found
```

I've installed jackd from the synaptic package manager and have been running Rhythmbox for quite some time with no problems.

:guitar:

---

### Post by zonum on 2007-11-17
I have written about this in another thread, and like others here, its not just on Internet radio.  Try pressing the Next button when playing an mp3 and/or when Internet radio is playing depress the Play button and then press the Play button again and see if it hangs (as it does for me).  The following is what I had reported:

I am running Gutsy and happened to notice today that when listening to mp3's under Rhythmbox that it would hang when it ended with a song and never went to the next song. I had to kill the rhythmbox process by hand, then tried again.

This tiime, I would start playing an mp3 (which plays just fine), then I would press the Next button and sure enough, the rhythmbox window would go gray, and just hang there - I have to kill the process "manualy".

This is becoming rather annoying, and, it is NOT just rhythmbox, banshee does the same exact thing, so in my opinion is some common underlying piece such as gstreamer, or something else along these lines.

zonum

---

### Post by dbarbour on 2008-01-27
Installed jackd. Problem resolved. Certainly it's not jackd itself that sorts te problem out, but rather a library or some subpart of jackd. **sudo apt-get install jackd**.

---

