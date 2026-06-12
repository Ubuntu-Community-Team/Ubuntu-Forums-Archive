---
title: "GNOME Mplayer choppy video and audio"
date: 2009-09-12
forum: Multimedia Software
---

### Post by virgoboy on 2009-09-12
HI!  So, ever since i installed Firefox 3.5.2, video as a whole has been not so crystal clear.  However, when watching a website like NASA TV, the video is very choppy, usually not in sync with the audio and the audio is barely audible and poppy.  I am using the gecko-mediaplayer 0.6.0 plug-in and have uninstalled the Totem plugins as they were acting worse!  All embedded media streams going through MPlayer are pretty bad quality-wise.

I feel like i have looked into every forum for help, including this one, and have gotten no where.  Hope some one here can help.  Thanks!

---

### Post by purgatori on 2009-09-12
Does video files play ok in gnome/mplayer outside of Firefox?

---

### Post by virgoboy on 2009-09-12
Yes.  The problem only seems to be video embedded in Firefox.

---

### Post by purgatori on 2009-09-12
Ok, then try running firefox with the --verbose flag from the terminal and see what output you get while accessing embedded video.

---

### Post by virgoboy on 2009-09-12
Wow, i am a bit new to all of this so, exactly what should i enter into the terminal (sorry).

---

### Post by purgatori on 2009-09-12
```
firefox --verbose
```

---

### Post by virgoboy on 2009-09-12
Thanks... no difference :confused:

---

### Post by purgatori on 2009-09-12
> **virgoboy said:**
> Thanks... no difference :confused:

Difference? Compared to what?

---

### Post by virgoboy on 2009-09-12
I entered the code into the terminal.  It opened a new FF browser window.  I went to the website in question ([http://www.nasa.gov/multimedia/nasatv/index.html](http://www.nasa.gov/multimedia/nasatv/index.html)) and there was no difference in the video between the two FF browser windows... hope this makes sense:(.

---

### Post by purgatori on 2009-09-12
> **virgoboy said:**
> I entered the code into the terminal.  It opened a new FF browser window.  I went to the website in question ([http://www.nasa.gov/multimedia/nasatv/index.html](http://www.nasa.gov/multimedia/nasatv/index.html)) and there was no difference in the video between the two FF browser windows... hope this makes sense:(.

It does, but the idea was to examine the output in the terminal when visiting said site.

---

### Post by virgoboy on 2009-09-12
I hope you are a patient soul... there is nothing happening in the terminal when i try to play an embedded video on the website in question and Now, nothing is playing there at all.  It loads, stops then nothing...

---

### Post by purgatori on 2009-09-12
Ok... well, since I can't provide a specific diagnosis of the problem, make sure that you uninstall the mozilla-totem plugin, and any other media playback plugins you may have installed besides gecko-media-player, then try the following:

In the terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install w32codecs
```

Close all open instances of Firefox, and enter:

```
killall firefox
```

Then open Firefox and try the site again.

---

### Post by virgoboy on 2009-09-12
OK.  I believe the terminal said something about "Firefox No process killed".  It cleared the result before i had a chance to copy it!  There is no difference in the website and now there are updates so, i'm gonna reboot and see what happens...

---

### Post by virgoboy on 2009-09-12
Thanks for your time with this but, i am a Hopeless cause.  I appreciate your help!!!!:D  Anything else you (or anyone) could pass on to me would be greatly appreciated.  I'm sure at some point, it will all work normally again without any explanation.

---

### Post by purgatori on 2009-09-12
> **virgoboy said:**
> Thanks for your time with this but, i am a Hopeless cause.  I appreciate your help!!!!:D  Anything else you (or anyone) could pass on to me would be greatly appreciated.  I'm sure at some point, it will all work normally again without any explanation.

I'm sorry that I haven't been able to help you so far, but see what difference makes, if any.

From the terminal, type:

```
nano .mplayer/config
```

Look for the entry that says: [gnome-mplayer] -- and change:

```
ao=(whatever it currently is)
```

to

```
ao=esd
```

... save the file, and then restart Firefox and see if you still experience problems.

---

### Post by virgoboy on 2009-09-13
Here is what i get:

  GNU nano 2.0.7            File: .mplayer/config                               

# Write your default config options here!


[gnome-mplayer]
vo=xv
vf=eq2
ao=oss
alang=English,eng,en
slang=English,eng,en










                                [ Read 9 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

It won't let me change anything or save anything.

---

