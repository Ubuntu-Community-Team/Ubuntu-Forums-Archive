---
title: "How do I capture real audio streamed output?"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by khelms on 2007-02-19
I've been reading web pages for a couple of days and trying various applications, but I can't get this to work 100%.  I want to capture a real audio stream and write it to my hard drive as a wav file.

I've tried using mplayer which can't handle a .smil url, so I had to manually pull one of the .ra files out of the .smil page and stick it in a file.  Example:
mplayer -playlist playlist.txt -ao pcm:file=cartalk.wav -vc dummy -vo null

That works for a while, but always dies at the exact same point in the file with
rtsp: read error.

I've tried using vsound which doesn't work much better.  Example:
vsound -f cartalk.wav -d realplay [http://www.cartalk.com/Radio/Show/show.smil](http://www.cartalk.com/Radio/Show/show.smil)

For some reason vsound causes a burst of static to appear in the sound at what appears to be random points, but seems to happen at the same place each time I play the stream.  Vsound doesn't handle multiple .ra files in a .smil.  Each new .ra play overwrites the previous audio.  Vsound also misbehaves if I don't run it under sudo as root.

Is there some other set of options I can try or some other application?  Should I be using the "real" realplayer instead of realplay?  Realplay seems to play the audio fine with no static bursts when invoked outside of vsound.

I'm trying hard to migrate all my "use cases" from Windows to Ubuntu, but I really miss Total Recorder here!

Keith

---

### Post by ron999 on 2007-11-10
Hi
Change this command:-
vsound -f cartalk.wav -d realplay [http://www.cartalk.com/Radio/Show/show.smil](http://www.cartalk.com/Radio/Show/show.smil)

Into this one:-
vsound -t -d -f  cartalk.wav  realplay [http://www.cartalk.com/Radio/Show/show.smil](http://www.cartalk.com/Radio/Show/show.smil)

During the recording you will build up a file in your home folder (similar to) **vsound28427.au**
When you've finished and you shut down realplay the file will change into **cartalk.wav**
:)

---

### Post by mdwy62 on 2008-06-01
Thanks for this info. I've installed realplay, vsound and sox, but I don't think vsound is working. I'm using the command:

vsound -t -d -f heiress.wav realplay 20080531_latw.ram

Realplay is playing the stream fine. I don't see a file .au being created, either in the folder in which I ran the command, or in my home folder. Further regardless of whether I use the -d option, I get audio output.  I get the following terminal output from the vsound command above:

About to start the application. The output will not be available
until the application exits.
Warning: LD_PRELOAD="/usr/lib/vsound/libvsound.so"
Opening ALSA PCM device default
Opening ALSA PCM device default
Opening ALSA PCM device default

When I stop the stream and close realplay, I get the following:
/usr/bin/realplay: line 54: 23288 Segmentation fault      (core dumped) $HELIX_LIBS/realplay.bin "$@"
Missing file ./vsound23281.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from 
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to 
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.

Thanks for any suggestions!

---

### Post by logos34 on 2008-06-01
> **ron999 said:**
> Hi
Change this command:-
vsound -f cartalk.wav -d realplay [http://www.cartalk.com/Radio/Show/show.smil](http://www.cartalk.com/Radio/Show/show.smil)

Into this one:-
vsound -t -d -f  cartalk.wav  realplay [http://www.cartalk.com/Radio/Show/show.smil](http://www.cartalk.com/Radio/Show/show.smil)

During the recording you will build up a file in your home folder (similar to) **vsound28427.au**
When you've finished and you shut down realplay the file will change into **cartalk.wav**
:)

Only problem with that is you end up with a HUGE wav file that you need to transcode to lossy format

Use mplayer--it will save directly as .ram...it's the best way, IMO:
[B]
mplayer -playlist "URL" -dumpstream -dumpfile filename.ram[/B]

---

### Post by ron999 on 2008-06-01
@mdwy62
What is the stream that you're trying to capture?

---

