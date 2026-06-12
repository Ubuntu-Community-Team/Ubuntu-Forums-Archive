---
title: "Gapless CD burning"
date: 2010-02-01
forum: Multimedia Software
---

### Post by redhuxley on 2010-02-01
I'm sure I'm jumping the gun in asking this, but I've at least done a search of the forums and didn't find anything super helpful.  I've used the GnomeBaker CD burner (Brasero would not work at all for some reason) but there doesn't seem to be an option to go gapless on a burn.  Is there a CD burning app that has that option?  Is there a way for a total linux/ubuntu newb to configure GnomeBaker to do it?

Thanks/

---

### Post by hemimaniac on 2010-02-01
Hit up the repos and give k3b a try, it has the most/simplest options crammed into a neat little package that is easy to use. When creating the audio cd in k3b it will give you options about pauses, breaks, or cross fading. give it a try ;)

---

### Post by redhuxley on 2010-02-01
> **hemimaniac said:**
> Hit up the repos and give k3b a try, it has the most/simplest options crammed into a neat little package that is easy to use. When creating the audio cd in k3b it will give you options about pauses, breaks, or cross fading. give it a try ;)

Done and done.  Thanks.  I'm gonna give this a try now...

edit:  yikes...three crashes is the span of like 5 minutes...

---

### Post by VertexPusher on 2010-02-02
Gnome CD Master (sudo apt-get install gcdmaster) is what you are looking for. It's a GUI front end for the cdrdao tool which will burn audio CDs in gapless (disc-at-once) mode. Unlike most other CD authoring tools it will show you a graphical representation of the audio waveform, and you'll be able to place track markers anywhere you want (ideal to divide gapless live recordings).

---

### Post by redhuxley on 2010-02-02
But that's only wave burning, yeah?  That might be nice for creating CDs from .toc and .cues but to just burn an mp3 CD w/o gaps?

---

### Post by VertexPusher on 2010-02-02
There is no such thing as an MP3 CD without gaps. Some media players support gapless playback of specially crafted MP3 files, but this is entirely beyond the scope of CD authoring/burning.

---

### Post by redhuxley on 2010-02-02
> **VertexPusher said:**
> There is no such thing as an MP3 CD without gaps. Some media players support gapless playback of specially crafted MP3 files, but this is entirely beyond the scope of CD authoring/burning.


You might be technically correct, but many windows burners have a feature to burn gapless mp3 cds(perhaps the gaps just become so short to make them practically inaudible) and I have used them often and easily before in another OS, and the burned CD had no audible gaps, so...



I got the gap very short in k3b, but I still hear a short gap.  I'll continue tweaking and see what's up.

---

### Post by VertexPusher on 2010-02-03
> **redhuxley said:**
> many windows burners have a feature to burn gapless mp3 cds
No, they don't, because it is technically impossible. You are confusing gapless burning (i.e. disc-at-once mode) with gapless playback of MP3 files.

MP3 streams consist of frames. The size of each frame depends on the bitrate and the sample rate. Since recordings rarely end at frame boundaries, the MP3 encoder needs to add some blank samples at the end to fill the last frame. This causes the gap.

Some MP3 encoders store the sample-accurate duration of the original recording as metadata inside the MP3 file. Some media players are able to use that information to perform gapless playback. However, this has absolutely nothing to do with the way these MP3 files are burned to a CD.

Gapless playback is a feature shared by MP3 encoders and MP3 players. The CD burning software can't do anything about it. Your MP3 files either contain the necessary metadata or they don't. You cannot retroactively add it to existing MP3 files without knowing the duration of the original recordings.

---

### Post by redhuxley on 2010-02-03
> **VertexPusher said:**
> No, they don't, because it is technically impossible. You are confusing gapless burning (i.e. disc-at-once mode) with gapless playback of MP3 files.

MP3 streams consist of frames. The size of each frame depends on the bitrate and the sample rate. Since recordings rarely end at frame boundaries, the MP3 encoder needs to add some blank samples at the end to fill the last frame. This causes the gap.

Some MP3 encoders store the sample-accurate duration of the original recording as metadata inside the MP3 file. Some media players are able to use that information to perform gapless playback. However, this has absolutely nothing to do with the way these MP3 files are burned to a CD.

Gapless playback is a feature shared by MP3 encoders and MP3 players. The CD burning software can't do anything about it. Your MP3 files either contain the necessary metadata or they don't. You cannot retroactively add it to existing MP3 files without knowing the duration of the original recordings.

I'm not confusing burning with playback.  I don't even care about playback on my machine(tho appreciated is gapless playback on my Zen player...), I only want to eliminate the seemingly default 2 second gaps that most burners add to the process.  I get what you are saying(I think), but I'm pretty sure the encoder would have made use of it's gapless feature for the particular album I have in mind, so then wouldn't the data be there?  Again, I have to say that I've burned several live mp3 albums from archive.org that had no audible gaps between tracks.  I've also backed up things like Dark Side of the Moon, and classical albums into mp3 using Exact Audio Copy and heard no gaps on burned playback.  Now, if I have your thrust right there probably is a gap, it's just not two freaking seconds long!

The program I was using:

[http://cdburnerxp.se/](http://cdburnerxp.se/)

which features among other things:

[B][I]audio-CDs with or without gaps between tracks


[/I][/B]

---

### Post by VertexPusher on 2010-02-03
> **redhuxley said:**
> The program I was using:

[http://cdburnerxp.se/](http://cdburnerxp.se/)

which features among other things:

***audio-CDs with or without gaps between tracks***
Audio CDs are not MP3 CDs. I was talking about gapless audio CDs in post #4. In post #5 you said you wanted gapless MP3 CDs.

You need to make up your mind.

---

### Post by redhuxley on 2010-02-03
> **VertexPusher said:**
> Audio CDs are not MP3 CDs. I was talking about gapless audio CDs in post #4. In post #5 you said you wanted gapless MP3 CDs.

You need to make up your mind.


:neutral:

No doubt original post lacked specificity.  

from the cdburnerxp site:

***Create Audio Disc***

   *  An audio CD is the type common CD players use. You can create such a disc from audio files with the extension **.wav**, **.mp3**, **.ogg**, **.wma**, **.flac**, **.aiff**, **.bwf** and **.mp2**. Check [Audio Formats]("http://www.cdburnerxp.se/help/Audio/formats") for further information. You can also use **CUE** files. Just drag and drop a CUE file to the compilation, and CDBurnerXP will automatically split audio files according to the information in the CUE file and add them to the compilation. *
  [I] To create such a compilation select **Audio Disc**, from the startup screen. 
[/I]







But to clear up the original intent of my question:  I would like to burn audio cds (abums and live sets) from mp3 files that don't have gaps between the tracks. 


Maybe cdburnerxp and any other such programs that have the feature convert the files first?  


[http://www.hydrogenaudio.org/forums/lofiversion/index.php/t19366.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t19366.html)

---

### Post by VertexPusher on 2010-02-05
GnomeBaker has the ability to convert files. It should also have the ability to burn in disc-at-once mode since it depends on the cdrdao package whose sole purpose is DAO burning.

However, that still doesn't mean that a CD made from converted MP3 files ends up gapless. There are gaps inside the MP3 files, as I explained above. The only way to remove them is by loading all the MP3 files into an audio editor such as Audacity, then arranging them so that the result is a continuous stream of music. The resulting WAV file can be loaded into Gnome CD Master where you can set the track markers.

---

### Post by redhuxley on 2010-02-08
I'm an idiot, I'll confess but maybe this will help someone else out...  

GnomeBaker has a dao feature that you can choose from after you click the burn tab.  Somehow I completely missed on my first pass through.  GnomeBaker seems to be much more stable than K3B for me.

---

### Post by sachs on 2010-10-09
I  am new and would wish to friendly greet everyone. I choosed to get inside in this point because I see you very serious and sure in the field that brings me very unhappy. 
I am a classical music follower (I do not use the word "lover", because I do not know what does it really mean). I like very much, already, downolad complete works from wellknown stores. But..., but..., I like to burn CD's to listen them through my stereo system (no problems with recitals, symphonies, etc.). Then..., huge complete works, as operas, come fully tracked, generally  in MP3 files only. I know that Burrrn, Nero, Foobar, etc automatically convert MP3 to WAV. That's not my problem. The disgrace is that I get gapped music, intollerable to listen. Is there any method that is not editing file by file, that allows to get normal continuous music from those MP3 files? I have several complete downlowded operas and symphonic poems in my hard disk, that I cannot convert in CD; so they are lost. Many thanks and friendly cheers. Sorry for the lenght.
> **VertexPusher said:**
> Audio CDs are not MP3 CDs. I was talking about gapless audio CDs in post #4. In post #5 you said you wanted gapless MP3 CDs.

You need to make up your mind.

---

### Post by Marky-boy on 2010-12-22
Hi all - bit late in replying, I know, but will put this here in case anyone else stumbles on this thread, as i did.

Running Brasero 2.32.0 - which is the current version under ubuntu 10.10 standard repositories.

To burn a gapless CD from mp3s:
[LIST]
[*]add the tracks to an audio project in Brasero (or add them to a playlist in Rhythmbox and click the burn audio CD button)
[*]select all the tracks (Ctrl-A)
[*]right mouse click on any track
[*]choose Edit information from the menu
[*]under options choose Remove Silences
[*]burn
[/LIST]

Quick and easy.

Note: VertexPusher speaks the truth, mp3s do not lend themselves to gapless burning, for reasons he/she outlined. The method I've outlined will get you pretty close. I have burned some DJ mixes using this method, and while there is a tiny stutter as the CD changes tracks it is totally bearable. Some transitions will be smoother than others, depending on the exact length of the source file.

Have fun.

---

### Post by 5oak on 2012-01-05
Nero Linux gets the job done, at least with FLAC files. Don't know about mp3 since I never burn those. My experience with Brasero is that there will be a tiny though audible gap, even with FLAC files.

---

