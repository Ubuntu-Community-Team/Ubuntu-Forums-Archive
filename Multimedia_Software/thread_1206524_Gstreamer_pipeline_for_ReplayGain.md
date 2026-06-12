---
title: "Gstreamer pipeline for ReplayGain"
date: 2009-07-07
forum: Multimedia Software
---

### Post by CatKiller on 2009-07-07
Now that I've noticed that Amarok has support for ReplayGain, I'd quite like to be able to automatically add ReplayGain tags to files as I rip them using SoundJuicer. I'm aware that all of the tools to encode audio files (oggenc, flacenc and LAME at least) are able to analyse the files and generate the appropriate tags, but I know nothing about how GStreamer pipelines work to actually make this happen.

I'm sure it's pretty simple once you know how it's done, I just don't.

Ta.

---

### Post by CatKiller on 2009-07-08
So no one here knows hows GStreamer pipelines work?

---

### Post by hansdown on 2009-07-08
Hi CatKiller.

I'm by no means very good with this, but there are some links that will
hopefully help.

[http://noraisin.net/~jan/diary/?p=40](http://noraisin.net/~jan/diary/?p=40)

[http://osdir.com/ml/video.gstreamer.cvs/2003-04/msg00087.html](http://osdir.com/ml/video.gstreamer.cvs/2003-04/msg00087.html)

[http://linux.die.net/man/1/gst-launch-0.8](http://linux.die.net/man/1/gst-launch-0.8)

[http://www.jonobacon.org/2006/12/01/modifiying-gstreamer-pipelines-in-playing/](http://www.jonobacon.org/2006/12/01/modifiying-gstreamer-pipelines-in-playing/)

The only link that matches your specific question leads to this thread.

Sorry I can't be more helpful.

---

### Post by CatKiller on 2009-07-08
Thanks for the links. I'll see what I can figure out and post back. From having given those articles a quick skim, and from having looked at the pipelines that SoundJuicer already uses, it's possible that it's all much simpler than I initially feared, with all the connections being handled automagically.

Before I start playing, does anyone know of a tool that will read whatever ReplayGain is supposed to put in the file? Or would it be just another tag that I might see in EasyTAG? Just so that I don't have to rip tracks before and after modifying the pipeline and do a listening test to see if it worked.

---

### Post by CatKiller on 2009-07-09
OK. My first attempt didn't seem to work. I tried changing the pipeline to ```
audio/x-raw-int,rate=44100,channels=2 ! rganalysis ! flacenc name=enc
``` but it doesn't seem to have written any tags that I can see in any of EasyTAG, Ex Falso or metaflac. I haven't tried a listening test yet. It seems possible that the rganalysis part of the pipeline is calculating the levels and then either not telling flacenc its results or flacenc is just ignoring them.

I'm also slightly concerned by this statement

> Because the generated metadata tags become available at the end of streams, downstream muxer and encoder elements are normally unable to save them in their output since they generally save metadata in the file header. Therefore, it is often necessary that applications read the results in a bus event handler for the tag message. that I found in the [documentation for rganalysis]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-rganalysis.html"). Not that I really know how one might use a bus event handler.

If I fail to get rganalysis to do what I want, there's also the possibility of fiddling with the flacenc part of the pipeline. I know that flac can add ReplayGain tags through the --replay-gain option. It makes sense that the flacenc pipeline element should be able to do the same thing, but I don't know how to invoke this behaviour.

Unfortunately, the documentation seems to be largely focussed on developers writing applications that use GStreamer, and SoundJuicer's own documentation only has this to say on the subject, which isn't especially enlightening.
> 
Profiles are defined with GStreamer pipelines. GStreamer is the underlying multimedia library used by Sound Juicer and other multimedia applications. A full explanation of audio profiles is outside the scope of this document.I shall keep playing while I wait for the scales to fall from my eyes. Further insight, as always, will be very helpful.

---

### Post by CatKiller on 2009-07-09
OK. I can actually change the volume of the audio stream by following the rganalysis pipeline element with rgvolume. This will turn down all those loud modern records when I re-rip them. That's not what I'm after, though. Since any volume change of this type is necessarily lossy, what I'd like is to be able to just write whatever tags it is that Amarok reads with the appropriate values. That way I can just turn it off when I don't want it.

Will keep looking.

---

### Post by CatKiller on 2009-07-09
I am confused. What I've read so far suggests that rganalysis should put replaygain-track-gain, replaygain-track-peak and replaygain-reference-level tags into the stream. When there's a step that writes tags, like flacenc, it should write the tags from the stream to the file. In this case, that should be the artist, title and so on tags from MusicBrainz that SoundJuicer puts in the stream at the beginning as well as the replaygain-* tags that come from later in the pipeline. But it doesn't, and I don't know why. oggmux doesn't seem to, either.

---

### Post by CatKiller on 2009-07-09
OK. Metaflac does definitely show the tags if they're there (I made some with SoundKonverter). rganalysis is definitely generating the tags in the stream (I did a test run with gst-launch). Flacenc just isn't using those tags for some reason that I haven't figured out yet.

---

### Post by monraaf on 2009-07-09
Well you've given the answer yourself already:

> 
Because the generated metadata tags become available at the end of streams, downstream muxer and encoder elements are normally unable to save them in their output since they generally save metadata in the file header. Therefore, it is often necessary that applications read the results in a bus event handler for the tag message.


This means you'll have to use two passes.

[LIST=1]
[*]scan the file and capture the replaygain taglist
[*]apply the taglist to the flacencoder, and encode the file
[/LIST]

---

### Post by CatKiller on 2009-07-09
> **monraaf said:**
> This means you'll have to use two passes.

[LIST=1]
[*]scan the file and capture the replaygain taglist
[*]apply the taglist to the flacencoder, and encode the file
[/LIST]
 Great!

How?

I don't yet know enough about how to manipulate the stream in order to get flacenc to wait on rganalysis being finished before it writes the tags. Or, failing that, for something else to know that rganalysis is done so that it can add in the additional tags. Thinking aloud, I suppose I could use a tee in some fashion so that flacenc gets on with encoding the audio while rganalysis works out the gain, and then passes on that information to something that could write the extra tags in.

---

### Post by monraaf on 2009-07-09
I don't think you can do it with the gst-launch application. You'll have to do it with code. Just for fun I wrote a small python script to apply replaygain to an audiofile and encode it to flac. It's standalone and doesn't integrate with SoundJuicer though. I've added it as an attachment.

---

### Post by CatKiller on 2009-07-09
Wow, thanks! And you've used decodebin, so it takes an arbitrary audio file as its input. Neat.

> **monraaf said:**
> It's standalone and doesn't integrate with SoundJuicer though.

It might do, though. I don't think the individual GStreamer plugins are that complicated by themselves. If it's not already, it might be possible to make this script act as a GStreamer plugin; rather than get the outcome through a pipeline that uses the existing plugins, make a new plugin that does what I want.

---

