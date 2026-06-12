---
title: "[SOLVED] Sound Juicer: Extracting MP3 - Massive file size (~50MB per song)"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by wieman01 on 2006-10-23
Whenever I am trying to convert a CD into a MP3 music files, each song grows to over 50 MB in size & won't play. I have not changed any settings & this definitely had been no issues until 2 weeks ago.

I attached a screenshot so as to show you my current settings. I am using Sound Juicer and until recently it never failed me. Any idea what's going on? Should I reinstall?

No problems reinstalling, but I'd love to know what's going on...

Cheers!

_**EDIT:**_
[COLOR="Red"]GStreamer Pipeline = audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=256 ! id3v2mux[/COLOR]

---

### Post by SteveF on 2006-10-23
I don't have a solution for you, but I have the same problem.  I tried reinstalling gstreamer-lame, but it did not help.

I ended up installing Grip and Lame and use that now to rip MP3s.

Steve

---

### Post by wieman01 on 2006-10-23
> **SteveF said:**
> I don't have a solution for you, but I have the same problem.  I tried reinstalling gstreamer-lame, but it did not help.

I ended up installing Grip and Lame and use that now to rip MP3s.

Steve
That's interesting... But it used to work until recently. Perhaps one of the updates is the culprit?

---

### Post by SteveF on 2006-10-23
I just saw another note which references this link:
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

It may be related to gstreamer10 does not have a gstreamer-lame plugin (as 8 did).  And that you may need to ugly plugins.

Steve

---

### Post by wieman01 on 2006-10-23
> **SteveF said:**
> I just saw another note which references this link:
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

It may be related to gstreamer10 does not have a gstreamer-lame plugin (as 8 did).  And that you may need to ugly plugins.

Steve
I know this guide & that's exactly what I have done. Like I've pointed out, it used to work well until 2 weeks ago or so. Must be something else.

---

### Post by CatKiller on 2006-10-23
I came across this yesterday: my other half was setting up MP3 ripping using the settings on the wiki, and was getting what I think are wav files (by the size) with ID3 tags stuck on (by the fact that they don't play).

I'd set mine up back on Breezy with settings from a different source, and mine still work OK. My settings are ```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=128 ! id3mux
``` So possibly yours, and anyone else that reads the same instructions you have, would benefit from adding in the vbr option? Mostly speculation based on the fact that mine works, and no one else's seems to.

Hope this helps.

---

### Post by wieman01 on 2006-10-23
My settings are: [COLOR="Red"]audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=256 ! id3v2mux[/COLOR]

I have not touched'em, and yet it stopped working all of a sudden.

I'll try the **vbr** option...

---

### Post by wieman01 on 2006-10-23
Nope, the **VBR option** did not help. Still the same problem.

---

### Post by CatKiller on 2006-10-23
> **wieman01 said:**
> My settings are: [COLOR="Red"]audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=256 ! id3v2mux[/COLOR]

I have not touched'em, and yet it stopped working all of a sudden.

I'll try the **vbr** option...

Maybe there's been a change in the lame syntax so that previously optional things are now mandatory? Just speculating.

I just tried having id3v2mux at the end, and that worked fine, so it must definitely be something in the middle section.

---

### Post by wieman01 on 2006-10-23
> **CatKiller said:**
> Maybe there's been a change in the lame syntax so that previously optional things are now mandatory? Just speculating.

I just tried having id3v2mux at the end, and that worked fine, so it must definitely be something in the middle section.
Copied your settings... does not work, either. Odd...

---

### Post by CatKiller on 2006-10-23
> **wieman01 said:**
> Copied your settings... does not work, either. Odd...

This is bizarre. I'll ask my other half to rip some stuff tonight and see if hers starts to work - this is on the same computer, so it must be a setting thing for us. I'll let you know if I discover anything interesting.

---

### Post by wieman01 on 2006-10-23
> **CatKiller said:**
> This is bizarre. I'll ask my other half to rip some stuff tonight and see if hers starts to work - this is on the same computer, so it must be a setting thing for us. I'll let you know if I discover anything interesting.
Appreciate it. :-)

Perhaps reinstalling does the job, but that's the last resort.

---

### Post by CatKiller on 2006-10-23
With the settings above (I copied and pasted from that post) it worked fine. Hmmm. I guess we might have been onto something if it hadn't worked, but we don't get as much information this way. I can't even say "ah yes, I installed such-and-such a package that made it miraculously work" since I installed all sorts of multimedia crap to attempt to get Cinelerra working. Sorry.

EDIT: Do you happen to know if it's possible to do this GStreamer pipeline stuff from the command line? You might get some error messages to explain why the middle stage is failing.

---

### Post by wieman01 on 2006-10-23
> **CatKiller said:**
> Do you happen to know if it's possible to do this GStreamer pipeline stuff from the command line? You might get some error messages to explain why the middle stage is failing.
Good point. I'll try that tonight. If there are no error messages whatsoever, I'll reinstall the packages & see if that resolves the problem. If it doesn't... well, let's not think about it now.

Thanks anyway.

_**EDIT:**_
Murakami's CatKiller? Weird book...

---

### Post by CatKiller on 2006-10-23
> **wieman01 said:**
> Murakami's CatKiller? Weird book...

No, it's an anagram of a Cornish name :biggrin:  Been meaning to read some Kafka, but maybe I should read Murakami first.

---

### Post by wieman01 on 2006-10-23
> **CatKiller said:**
> No, it's an anagram of a Cornish name :biggrin:  Been meaning to read some Kafka, but maybe I should read Murakami first.
Sidetracking... But read Kafka first. Honestly I hated "Kafka on the shore" (the book does make no sense at all - unbearable patchwork) but I am a great fan of Kafka the writer. :-)

Anyway, I'll report back tonight if I have been able to resolve the problem.

---

### Post by wieman01 on 2006-10-24
Thanks for your help. We will never know what caused this problem, because everything works fine after reinstalling "Sound Juicer" and "streamer0.10-plugins-ugly-multiverse". I don't like this kind of solution, but hey, it worked.

---

### Post by CatKiller on 2006-10-24
Ah well. Glad it's working for you now anyway.

---

### Post by wieman01 on 2006-10-25
I have finally found out why this problem had occurred in the first place... I am using a tool called GtkOrphan to remove orphaned packages, etc. The tool also shows "streamer0.10-plugins-ugly-multiverse" as one of the orphaned packages that I chose to remove. Well... Shouldn't have done that. :-)

---

### Post by CatKiller on 2006-10-25
> **wieman01 said:**
> Well... Shouldn't have done that.

:lol:

---

### Post by DoctorMO on 2006-10-28
Yep same problem here. we didn't have that gstremar ugly package and the results where wav files.

---

### Post by peterbakker on 2006-12-07
Same problem here. For some reason, this helped me out:

I installed the packages:
gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse 

and set the pipeline: 

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 ! id3mux
```

you can change the bitrate to your needs. 

Now i still have to find out how to enable the vbr settings](*,)  this week...

---

### Post by wieman01 on 2006-12-07
"vbr=true" would not do?
> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc **vbr=true** bitrate=192 ! id3mux

---

