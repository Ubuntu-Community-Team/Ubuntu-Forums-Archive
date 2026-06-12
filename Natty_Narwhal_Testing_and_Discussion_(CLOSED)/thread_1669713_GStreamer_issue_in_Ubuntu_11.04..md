---
title: "GStreamer issue in Ubuntu 11.04."
date: 2011-01-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by moma on 2011-01-18
Hello,

I'm worried that GStreamer has problems in Natty. I have an audio-recording program where GStreamer simply blocks and freezes the application.

This statement causes the blocking.
gst_element_set_state(g_pipeline, GST_STATE_PAUSED);

Everything works fine in Ubuntu 10.10.

Ok, I made a simple test program. Download it from 
[http://www.futuredesktop.com/tmp/t11.c](http://www.futuredesktop.com/tmp/t11.c) 

And compile it:
[COLOR="DarkGreen"]gcc t11.c -Wall $(pkg-config --cflags --libs gtk+-2.0 gdk-2.0 gstreamer-0.10 gstreamer-interfaces-0.10) -lm -o t11[/COLOR]

Compilation should now work right (thanks to @mc4man)

Then run it:
[COLOR="DarkGreen"]./t11[/COLOR]

It will show you a little GUI.
It also creates a simple audio-recorder pipeline for GStreamer, so play some audio, music, sound.

Press the buttons to Start, Pause and Continue the recording. In my case, pausing will block and freeze the program. I've tested this both in VirtualBox/Ubuntu 11.04 and on a real 64 bit Natty installation.

Compilation will need at least the dev packages:
[COLOR="Green"]sudo apt-get install build-essential libgtk2.0-dev  libglib2.0-dev  libgstreamer0.10-dev  libgstreamer-plugins-base0.10-dev [/COLOR]

Is this issue anything to be worried about?

Would you please test this and report back your findings.

BTW: The final product ([COLOR="Red"]if[/COLOR] and when ready) will be this
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

---

### Post by mc4man on 2011-01-18
While it's fine in 10.10 not so in 11.04 (gcc-4.5 SVN 20110117 (r168896)
(had to attach terminal out as a txt - this forum saw the quoted output as images, 110 of them

Edit: changed compile command a bit - works fine now (as far as building, opening, didn't test use

gcc t11.c -Wall $(pkg-config --cflags --libs gtk+-2.0 gdk-2.0 gstreamer-0.10 gstreamer-interfaces-0.10) -lm  -o t11

---

### Post by mc4man on 2011-01-18
It's getting hard to edit - may show up, may not^

Any way changed to command a bit - builds, opens fine
gcc t11.c -Wall $(pkg-config --cflags --libs gtk+-2.0 gdk-2.0 gstreamer-0.10 gstreamer-interfaces-0.10) -lm  -o t11

Edit: I get a freeze on pause and stop, using unity desktop. Doing a fresh install on another machine, worth checking there as you can't depend on the results of any one individual natty install at this point

---

### Post by moma on 2011-01-19
@mc4man: Thanks a lot for fixing the compilation command.

---

### Post by moma on 2011-01-19
@mc4man: Thanks a lot for fixing the compilation command.

---

### Post by moma on 2011-01-19
@mc4man: Thanks a lot for fixing the compilation command.

---

### Post by moma on 2011-01-19
@mc4man: Thanks a lot for fixing the compilation command.

---

### Post by moma on 2011-01-19
@mc4man: Thanks a lot for fixing the compilation command.

---

### Post by moma on 2011-01-19
@mc4man: Thanks a lot for fixing the compilation command.

---

### Post by moma on 2011-01-19
@mc4man: Thanks a lot for fixing the compilation command.

---

### Post by moma on 2011-01-19
@mc4man: Thanks a lot for fixing the compilation command.

---

### Post by mc4man on 2011-01-19
moma - 
see you got a bit of an intro to the current forum issue(s) - I find till resolved that once you click 'submit' the post will go thru no matter what. If your browser is  'spinning it's wheels' waiting for a response back I just close it or the tab out. The post will show up regardless

Anyway have a new install though atm haven't enabled unity so just logging in to the Classic > panel (trying to find some info on semi-random kernel panics I see on different hardware

The test prog is working much better on this install - opens fine
The start, pause, stop all work as expected - continue doesn't but now isn't totally locking - start will work after clicking continue (previously nothing worked after continue

Will probably enable/login to Desktop > unity later today...

Edit: for instance this post took almost 15 min to show... and this edit - who knows

---

### Post by cariboo on 2011-01-19
Please be patient, the new hardware is on the way. :)

---

### Post by mc4man on 2011-01-19
Enabled the unity login - all works fine 
Probably bit of a space out previously on the continue, that works fine also  - ie. pause > continue

---

### Post by moma on 2011-01-20
Very good news. I will also do a reinstallation of Ubuntu 11.04 (daily) and see what happens. I will let you know...

---

### Post by rburkartjo on 2011-01-20
mc i also just enabled the unity 2d login first time i could get unity to work so i can play around with

---

### Post by moma on 2011-01-20
Ok, the recorder now works right in Natty. Pausing and continuing work as expected. I had a very good test. I tested both the t11.c and the real Audio-Recorder ([https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)).

I found some issues with the toolbar icon (status icon) when running an ordinary GNOME 2.x Desktop.

I also found some widget-warnings in the win-settings.c when Skype is not present/not installed. Gonna fix that too.

Also the "auto start on login" feature needs love too.

---

