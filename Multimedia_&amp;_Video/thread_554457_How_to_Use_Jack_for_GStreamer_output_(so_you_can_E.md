---
title: "How to: Use Jack for GStreamer output (so you can EQ banshee/rhythmbox w/Jack-Rack!)"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by hotspoons on 2007-09-19
This is a lot easier than trying to get it to work through PulseAudio, as I did before, and works much more reliably. Gstreamer includes a jackaudiosink plugin in the gstreamer-plugins-bad package, though it won't show up in sound properties without a little hacking. 

First you need some stuff. Before that disable 'esd software mixing' in the Sounds tab of gnome-sound-properties (system->preferences->sound). Get some ladspa plugins, jack-rack, jack.plumbing, the bad plugins, patchage to see that everything works, and of course jackd (make sure you have universe/multiverse enabled):

```

sudo apt-get install gstreamer0.10-plugins-bad jackd jack-rack ubuntustudio-audio-plugins jack-tools patchage

```

Now you have more plugins than a $50,000 Protools rig, and all you're going to use them for is making your MP3's sound better. Here's how.

Open gconf-editor (alt-F2, type 'gconf-editor'), navigate to  
/system/gstreamer/0.10/default/. In the 'audiosink', 'chataudiosink', and 'musicsink' keys, enter the following:
```

jackaudiosink connect=none

```

If you leave off the 'connect=none', the sink will automatically connect to the outputs of your soundcard in Jack. You may want this for default audio and chat (just remove 'connect=none'), but not for music if you want EQ, dynamics, etc. processing on it. You may want to change the description of the sinks as well...otherwise it just shows up as 'ALSA custom' in gnome-sound-properties.

Next, we make a rule for jack.plumbing. In the version of jackaudiosink that ships with Feisty, the outputs are by default named 'GStreamer:out_x'; In Gutsy, they are named by the program, so for Banshee, they would be 'Banshee:out_x'.

Here's mine using Feisty. Save this in your home directory as '~/.jack.plumbing':

```

(connect "GStreamer:out_1" "jack_rack:in_1")
(connect "GStreamer:out_2" "jack_rack:in_2")
(connect "jack_rack:out_1" "alsa_pcm:playback_1")
(connect "jack_rack:out_2" "alsa_pcm:playback_2")

```

You may need to modify that depending on your version of GStreamer and programs you are using. You can also enter more rules in there...after you get up and running (below), open patchage for a very nice graphical representation of what is happening, and it will also show you the proper names of your ports if they vary from mine.

Now you need a script to automate it. Put this in a script (again, you may need to modify the jackd command to suit your set up, depending on what your primary soundcard is labeled as in ALSA, and if you have -RT kernel, running jack with '-R' will give you better performance), save it in your home folder, 'chmod +x' it, and add it as a start up item in your session:

```

#!/bin/bash
jackd -dalsa -dhw:0 &
sleep 2
jack.plumbing &
sleep 1
jack-rack -n &

```

Now you're set. Try running that script, and if everything works, jack-rack should pop up (and on every boot). If it doesn't, jackd didn't start correctly. If you save a jack-rack file, you can tell jack-rack to load it in the script above by just adding the path to the file after the '-n'. If jack-rack popping up on every boot annoys you, get alltray (sudo apt-get install alltray) and run jack-rack like so: "alltray jack-rack -n &", and it will dock in your system tray.

Now run your favorite gstreamer audio application (exaile, banshee, rythymbox, etc.) and see if you have any sound when you hit play. If not, open patchage and manually connect the output pins from your sound application to the input pins of jack-rack (just drag and drop). Jack rack's output should already be connected to the outputs of your soundcard. 

If one or both of the above things didn't happen automatically, check the names in patchage for the pins, and edit your ~/.jack.plumbing file and change the names to reflect the proper pins. .jack.plumbing should automatically see you updated the file when you close and reopen your sound program.

That should do it. Let me know if this works for anybody else. Thanks,

-Rich

---

### Post by battles33 on 2007-12-07
since finally getting serious about linux (with ubuntu) about two months ago, i've been looking the whole time how to do this. thanks so much. i don't really get that script part, but the auto connect for me is perfect.

thanks so much for this post

---

### Post by AudioGarf on 2007-12-14
Great job!

Very teachfull script, exactly that I was searching! and it works quite perfecly!

Problems: 
- plumbing rules doesn't work at everyboot.
- starting jack-rack with alltray doesn't change anything: jack-rack pops-up at everyboot. I've tested alltray in click mode: it works with jack-rack. I don't understand.

---

### Post by AudioGarf on 2007-12-15
Ok, I can use jack.plumbing properly now: you REALLY have to start patchage after all connections have been done.

It seems that patchage makes some mess in jack.plumbing rules.

I cannot use jack-rack with alltray: a splash screen issue according to alltray manual.

Do you have compiled jack-rack without splash?

---

