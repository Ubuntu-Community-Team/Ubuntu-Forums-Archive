---
title: "Possible to delay audio output?"
date: 2009-06-16
forum: Multimedia Software
---

### Post by Mike Gats on 2009-06-16
What I would like to accomplish is to synchronize the radio broadcast of a sporting event to the television. Right now my radio is about 8 seconds ahead of the TV.  I have a Sansa clip mp3 player that has an FM radio which I would connect to the &quot;audio-in&quot; port on my laptop. Is there a program that could record this input, allow me to configure a delay and then send the delayed signal to the audio out port?  I am running Ubuntu 9.04.  Please let me know if more information is needed  Thanks Mike

---

### Post by tokland on 2010-01-24
> **Mike Gats said:**
> What I would like to accomplish is to synchronize the radio broadcast of a sporting event to the television. Right now my radio is about 8 seconds ahead of the TV.  I have a Sansa clip mp3 player that has an FM radio which I would connect to the &quot;audio-in&quot; port on my laptop. Is there a program that could record this input, allow me to configure a delay and then send the delayed signal to the audio out port?  I am running Ubuntu 9.04.  Please let me know if more information is needed  Thanks Mike

I needed something similar and I came up with this:

[http://code.google.com/p/tokland/wiki/RealTimeLADSPAPlugins](http://code.google.com/p/tokland/wiki/RealTimeLADSPAPlugins)

Certainly not very user-friendly but doable. I am pretty sure there are a whole bunch of alternatives (Pulseaudio?) though.

---

### Post by d53richar on 2010-10-18
SOLVED.
I too required something to delay radio audio. After looking around all I found was something for windows but nothing for linux (vlc seems possible but i could not get that to work) so I decided to create something using Python and GStreamer.
This was tested on Ubuntu 10.04 with Alsa and GStreamer.
First of all go to System/Preferences/Sound and select the Input Tab, if you have more that one one device listed then select the device (card) that you wish to use, make sure that 'Line In' is selected from the drop down menu. Connect an audio source to the Line In on your sound card and check that the VU Meter (Input Level) is indicating that sound is being received.
This application is command line only, I am too lazy to put a GUI front end on it. 
Save the following code to a file (I used radiodelay.py) and make that file executable.
To use it, in a terminal type ./radiodelay.py 3.5 for a 3.5 second delay, if you do not supply a number then the delay is set to Zero (actually there will always be a  slight delay).
OK without further 'delay' here is the Python code.

#!/usr/bin/python

import pygst
pygst.require("0.10")
import gst
import pygtk
import gtk
import sys

class Main:
    def __init__(self):
    #this just reads the command line args
    try:
        DELAY = float(sys.argv[1])
        DELAY = long(DELAY * 1000000000)
        print DELAY 
    except IndexError:
        DELAY = 0

    self.delay_pipeline = gst.Pipeline("mypipeline")
    #ALSA
    self.audiosrc = gst.element_factory_make("alsasrc", "audio")
    self.audiosrc.set_property("device","default")
    self.delay_pipeline.add(self.audiosrc)
    #Queue
    self.audioqueue = gst.element_factory_make("queue","queue1")
    self.audioqueue.set_property("max-size-time",0)
    self.audioqueue.set_property("max-size-buffers",0)
    self.audioqueue.set_property("max-size-bytes",0)
    self.audioqueue.set_property("min-threshold-time",DELAY)
    self.audioqueue.set_property("leaky","no")
    self.delay_pipeline.add(self.audioqueue)
    #Audio Output
    self.sink = gst.element_factory_make("autoaudiosink", "sink")
    self.delay_pipeline.add(self.sink)
    #Link the elements
    self.audiosrc.link(self.audioqueue)
    self.audioqueue.link(self.sink)
    #Begin Playing
    self.delay_pipeline.set_state(gst.STATE_PLAYING)

start=Main()
gtk.main()


Save the above code and begin to enjoy listening to your favorite radio commentators whilst watching live sports on tv.

Regards
David

---

### Post by d53richar on 2010-10-18
MAJOR OOPS
The python indentation did not come out in the code so I am attaching the code as radiodelay.py

Regards
David

---

