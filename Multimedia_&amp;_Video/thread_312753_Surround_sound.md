---
title: "Surround sound"
date: 2006-12-04
forum: Multimedia &amp; Video
---

### Post by c2483 on 2006-12-04
I found this at ubuntu guide
 How to setup the surround speakers (5.1 and others) with ALSA
* Read #General Notes 
* Edit the ~/.asoundrc file, create it if it doesn't exist: 
gedit ~/.asoundrc
* Enter the following section: 
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

    * This will allow to play the surround output and duplicate the stereo output to all 6 channels (not only front ones). 

My question is will this work with 8 channel.
I'm using the BlueGears HDA Digital X-Mystique 7.1 with creative 7.1 speakers

Another question
Can I send audio to each speaker individually to check everything is connected correctly

---

