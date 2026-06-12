---
title: "Cant Make Flac Audio Cd's...but they will play!"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by jacc1234 on 2007-03-04
I am trying to make an audio cd from flac files. I have the gstreamer.08-flac plugin and most of the gstreamer .10 packages. I am able to listen to my flac files in Totem and Rythembox. I have tried to burn the files using serpentine and gnomebaker an k3b. I have an issue with my sata cd drive and k3b so for now im just trying to work on gnome baker which burns everything else. When I try to burn a flac file this is the error I get:

Could not decode stream.gstflacdec.c(586): gst_flac_dec_error_callback (): /gnomebaker-convert-to-wav-pipeline/decoder/flacdec3:
CRC mismatch (2)

any help would be great.

Thanks,
Jacc1234

---

### Post by jacc1234 on 2007-03-05
Ok here is an update. I am able to use some flac files to make audio cd's. I dont know why but for some reason they just work. If anyone can give me a way to check how the files were encoded and what version of flac was used it might be helpful.

Thanks,
Jacc1234

---

### Post by m.musashi on 2007-05-29
I have the same issue with flac playing but not burning. Does no one know what's up with this?

---

### Post by yabbadabbadont on 2007-05-29
The original wav files that were encoded into flac had to be 16bit/44.1kHz or it won't work.  At least that is what I have seen others report around the net.

---

### Post by m.musashi on 2007-05-29
Is there a way to know how they were encoded? And if they were not encoded properly is there a way to burn them?

---

### Post by yabbadabbadont on 2007-05-29
```
/media/music/Flac/4_Non_Blondes/Bigger_Better_Faster_More $ file 06_Spaceman.flac 
06_Spaceman.flac: FLAC audio bitstream data, 16 bit, stereo, 44.1 kHz, 9706116 samples
```
If it isn't correct, you could try decoding it to a wav file using the flac command line tool and then try converting the wav with sox.

---

### Post by m.musashi on 2007-05-29
Thanks for the help.

Okay, I got this for one of the files:
```
10. To the Pirates' Cave!.flac: FLAC audio bitstream data, 16 bit, stereo, 44.1 kHz, 9290880 samples
```
That's the same as yours (other than the samples part) so it looks like it's the right format. When I try to add a file to gnomebaker it tells me it's an unsupported file type. I don't get it. I thought flac support was built in.

EDIT: actually gnomebaker says "the plugin to handle a file of type (null) is not installed."

---

### Post by yabbadabbadont on 2007-05-29
[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-flacdec.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-flacdec.html)

Is the only thing that looks like it might apply here...  I don't use Gnome or gstreamer, so I'm a bit limited in the help I can provide here.  :(

Isn't there a command line command you can run to re-register all the gstreamer plugins?

---

### Post by m.musashi on 2007-05-29
Actually, I don't know. I've never had a problem with flac before. It's always "just worked".

---

### Post by m.musashi on 2007-05-29
D'oh! Okay, I managed to solve this but I can't say it makes sense. The files I wanted to burn were on my desktop. I was connecting to it from my laptop over ssh (using nautilus). I was trying to drop them from nautilus to gnomebaker and kept getting the error. On a hunch I copied the files to the laptop and then it worked fine.

I just don't get why I have to copy them first. Kind of defeats the purpose of having remote storage and networks and such.

---

### Post by yabbadabbadont on 2007-05-29
Edit: Too late.  :D

---

### Post by m.musashi on 2007-05-29
Did you have another thought? My fix only seems a workaround for what I'd call a bug.

---

### Post by yabbadabbadont on 2007-05-29
I've got plenty of them...  ;)  Just none that apply to the current situation.  :D

I would say that the bug is in either the network layer or the "drag and drop" implementation (OLE in winblows).  It isn't gstreamer or gnomebaker since it worked with the files copied locally.  Something to consider if you open a bug on launchpad.

---

### Post by m.musashi on 2007-05-29
lol

Okay, I filed this as a bug (my first bug report). I did file it as related to gnomebaker because I wasn't sure what other package to attach it to. I know it's not just all drag and drrop since I can drag and drop the files elsewhere.

Oh, well. I managed to do what I needed. Thanks for the help.

---

