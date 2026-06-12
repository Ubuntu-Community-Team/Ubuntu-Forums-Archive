---
title: "missing avi codec?"
date: 2010-02-15
forum: Multimedia Software
---

### Post by nfelddav on 2010-02-15
I am trying to read an avi file into MATLAB using the MATLAB command mmreader.

The MATLAB documentation says it supports 
"Any format supported by your installed plug-ins for GStreamer 0.10 or above, as listed on [http://gstreamer.freedesktop.org/documentation/plugins.html](http://gstreamer.freedesktop.org/documentation/plugins.html), including AVI (.avi) and Ogg Theora (.ogg)."
for Linux.

When I try to invoke the command, it reports:

??? The file requires the following codec(s) to be installed on your
system:
video/x-avi-unknown


Error in ==> mmreader.mmreader>mmreader.init at 364
            obj.MMReaderImpl = audiovideo.mmreader(fullName);

Error in ==> mmreader.mmreader>mmreader.mmreader at 133
            obj.init(fileName);

---

### Post by Yellow Pasque on 2010-02-15
.avi is a container that will have video in another format inside. Make sure you have all the necessary gstreamer plugins packages installed (ffmpeg,good,bad,ugly,bad-multiverse,ugly-multiverse).

---

### Post by nfelddav on 2010-02-16
I checked, and I have all of the gstreamer plugins packages installed.

---

### Post by MRupe on 2010-02-16
Try installing VLC player. It has the codecs in it for most video formats that you will run into.

---

### Post by nfelddav on 2010-02-16
I have VLC, and it is capable of playing the video, but I would like to import it into MATLAB. Is this just impossible?

---

### Post by mcduck on 2010-02-16
> **nfelddav said:**
> I have VLC, and it is capable of playing the video, but I would like to import it into MATLAB. Is this just impossible?

If VLC can play it, then use VLC to check what format the video is compressed into. Without that information it's hard to say what codec you might need for the file to work...

(I'd place my bets on w32codecs and gstreamer0.10-pitfdll...)

---

### Post by nfelddav on 2010-02-16
> **mcduck said:**
> If VLC can play it, then use VLC to check what format the video is compressed into. Without that information it's hard to say what codec you might need for the file to work...

(I'd place my bets on w32codecs and gstreamer0.10-pitfdll...)
How would I do that? VLC says it is using Codec RV15, but I can't find anything that says what format the video is.

I have gstreamer0.10-pitfdll installed as well.

---

### Post by mcduck on 2010-02-16
> **nfelddav said:**
> How would I do that? VLC says it is using Codec RV15, but I can't find anything that says what format the video is.

I have gstreamer0.10-pitfdll installed as well.

I haven't got VLC installe don my Ubuntu machine right now, so I can't be sure how same the user interface is on Linux version, but on my mac the audio & video formats can be checked by opeing a file in VLC and then selecting Window->Media Information. Then just look at the Codec details-tab.

The pitfdll package is worthless on it's own, you also need the w32codecs (or w64codecs if you are running a 64-bit system). Pitfdll just allows gstreamer to use the dll files that Widbows codecs are using. You can getw32codecs from the Mediuntu repository.

edit : RV15 sounds like some version of the (non-free!) RealVideo codec. Nasty stuff, if you ask me, but getting the codecs from Medibuntu should do the trick...

---

