---
title: "Juicer Track Number Tag Missing"
date: 2009-12-26
forum: Multimedia Software
---

### Post by andypi on 2009-12-26
I'm trying to rip a CD to AAC format using sound juicer. It's so I can use the tracks in iTunes (which I've got running on a WinXP virtual machine).

The tracks rip fine, and will play in iTunes, and the metadata is almost fine, but it's missing the track numbers. Is there any way I can get Juicer to include the track numbers with the metadata so that they'll show up in iTunes?

Thanks,

Andy

---

### Post by ajgreeny on 2009-12-26
In Sound Juicer preferences you can set the file name to show number if that is what you want.  Or you can for mp3s, perhaps it's different for AACs, I never use them, so have no idea.

---

### Post by andypi on 2009-12-26
Thanks, but that's not quite the problem I'm having. The track numbers are written into the *filenames* of the ripped files. However, the track numbers are not written into each track's *metadata*, which is why they're not showing up in my media player.

---

### Post by ajgreeny on 2009-12-27
OK, I see what you mean, but I have no solution, other than using easytag or tagtool to add them manually. I have used both, but find that tagtool is a bit better for tagging with ID3 v2 tags, which I can't get easytag to do for me, and my mp3 player needs v2.

Have a look at both and try them out to see if they do what you want.  Sorry I can't help with juicer.

---

### Post by andypi on 2009-12-27
Yeah, I did think of using a tagger, but I do think juicer should be able to do it. Interestingly it does work fine when ripping to MP3 (which is what I've done, for now).

Looking at the (default) gstreamer pipeline for the MP3 profile within Juicer, you can see the id3v2 bit. However, copying this into the AAC profile results in files which iTunes won't play.

These are the two profiles:

AAC: audio/x-raw-int,rate=44100,channels=2 ! faac profile=2 ! ffmux_mp4
MP3: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

Anyone know how the AAC pipeline should be changed in order to correctly tag the files? Alternatively, is some update to gstreamer required (though I believe I have the most recent version with the relevant codec).

Thanks.

---

