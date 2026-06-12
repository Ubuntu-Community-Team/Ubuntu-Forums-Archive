---
title: "How do I play/burn a .wv file?"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by m.musashi on 2007-05-30
I downloaded an audio file that has the extension .wv. As far as I can tell, this is not a wav file. Based on what I've learned searching the web it may have been created using a program call "exact audio copy" but I have no idea how to play the file or burn it to a CD - preferably in ubuntu.

Anyone know what to do with these? Or should I avoid downloading them? Of course, it was the only thing I could find that promised good audio quality.

Thanks.

---

### Post by ryanVickers on 2007-05-30
If your in ubuntu/linux, you might notice that the file extensions don't matter - you can totally remove them if you want, so I would say you just don't have a program for opening them.  I've seen in various places that it's a microsoft format, probably "microsoft video" (wma/wmv is windows media audio/video).  Make sure you have every plugin you can get your hands on:

all "gstreamer" (about 5), "xine" (1 or 2) and there is one "ubuntu extras" or something like that

---

### Post by m.musashi on 2007-05-30
Thanks for the quick reply. I don't think it's a microsoft format but probably a format that is designed to be used in windows. From what I've found it's from a program called exact audio copy. I found one thread here about getting it to run in wine but I don't want to use it. I just want to extract the audio files and burn them. I wanted a flac file but couldn't find one.

---

### Post by shirilover on 2007-05-31
The file in question is a WavPack lossless audio file.
Playing the file will depend on what audio player you use.
Burning to CD as CD audio may require the wavpack package.

---

### Post by m.musashi on 2007-05-31
Is playing or burning an option in ubuntu (not using wine) or would I need to use windows?

---

### Post by WarLocke on 2007-05-31
a .wv file is basically a compressed .wav file.  What I would recommend you do is convert it to a .wav and then burn it from there.  To convert it, you can use a program called [Media Coder]("http://mediacoder.sourceforge.net/").  It is an awesome program, but it is Windows only, so you will have to use wine unless you have a Windows box around.  btw, you can turn .wv files into anything you want, even MP3 with that program.  

As far as burning, I use K3B.  You can also use Gnomebaker (I think thats what its called) and they both run on Ubuntu.  

good luck

---

### Post by Jose Catre-Vandis on 2007-05-31
I think XMMS has a wavpack plugin. Once you have playback, you can use the Out-lame plugin to export the file to a wav format for burning to CD

---

### Post by m.musashi on 2007-05-31
Hmmm. I couldn't find a wavpack plugin for xmms but I did find one for audacious. I can now play the file. However, it is one long file with no track breaks for anything. It did come with a cue file that is supposed be used to extract the original tracks in order but I don't know how to use it.

Any idea how I can get regular wav files out?

Thanks.

---

### Post by m.musashi on 2007-05-31
Holy crap. I got it to work. I installed something simply called wavpack. It's a command line tool but it extracted the file into a plain wav file. It's still just one long file but I'm working on figuring that out.

Thanks for the help. Knowing it was called a wavpack file made all the difference in solving my mystery.

---

### Post by Jose Catre-Vandis on 2007-06-01
> **m.musashi said:**
> Hmmm. I couldn't find a wavpack plugin for xmms but I did find one for audacious. I can now play the file. However, it is one long file with no track breaks for anything. It did come with a cue file that is supposed be used to extract the original tracks in order but I don't know how to use it.

Any idea how I can get regular wav files out?

Thanks.

Not one to be told I'm wrong :)

Try this:[http://www.wavpack.com/files/xmms-wavpack.tar.gz](http://www.wavpack.com/files/xmms-wavpack.tar.gz)

and then this: [http://savannah.nongnu.org/projects/out-lame/](http://savannah.nongnu.org/projects/out-lame/)

---

### Post by mihai.ile on 2008-01-15
the post is very old but I'll just answer anyway so it will be usefull for others...

For burning an audio CD:
When you have the cue file and the corresponding wav file, open the cue with a text editor and make sure that in the file, more or less at the begining there is a line that starts with FILE.
Make sure that it points to the wav file and after this, the word WAVE.
For example if the cue and wav in the same directory:
FILE "CDImage.wav" WAVE

Save the file and just do 2nd click -> write to CD in nautilus file manager or use any other application to burn the .cue image file.

---

