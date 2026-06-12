---
title: "Rip CD to MP3 with K3b"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by TroutStalker on 2007-05-16
I'm a new ubuntu user (trying to switch from SUSE) and I'm having trouble with k3b.  I want to rip a CD to MP3 files.  At first I got an error msg when k3b started saying I didn't have mp3 support.  After browsing the forum I found I had to install libk3b2-mp3.  I've also installed other mp3 files - lame and libmad.  I no longer get the error msg but still can't rip.  When I click 'start ripping' in k3b I'm presented with a pulldown menu that has ogg-vorbis and Wave.  Looking at the k3b settings-plugins screen I see AudioDecoder k3b MAD which purports to be an MP3 decoder.

I can rip to mp3 using grip so I assume I have the proper libraries installed for ripping to MP3.

I'd really appreciate some help on this; I'm at a loss as to how to proceed.

---

### Post by TroutStalker on 2007-05-16
Well it took me a while but I found the source of my problem.  I was missing the plugin library for MP3 encoding, libkd3lameencoder.  I thoght it would be in libk3b2-mp3 but it's not there.  I copied the lib from my SUSE system to /usr/lib/kde3/lib and I can rip CDs to mp3.

If anyone knows what package contains libkd3lameencoder I'd like to know.

---

### Post by NewJack on 2007-05-19
I had the same problem as you when I saw your post.  Did a search for "Lame" in Synaptic and a bunch of files came up.  If you scroll down a bit, you will see LAME ver. 3.96.  Just mark it for installation and you won't get the error message anymore.  Hope that helped.

Joe  :guitar:

---

### Post by ageilers on 2007-05-19
I had the same problem. Installed Lame and libk3b2-mp3 from Adept Manager, worked fine. Then I discovered that in Kubuntu, I can rip CDs right from Konqueror into MP3, FLAC, Ogg Vorbis, WAV, and CDA fromats. It ripped at a bitrate over 200 kbps compared to K3b at 128 kbps.

[http://docs.kde.org/userguide/audio-cd.html]("http://docs.kde.org/userguide/audio-cd.html")

The deeper I dig into (K)Ubuntu, it keeps getting better. Someday I will realize just how good it is.

---

### Post by wolframarnold on 2007-10-29
K3b doesn't seem to be configured by default for MP3 ripping.

Install the following packages (via Synaptic, Adept, or apt-get):
lame
liblame0
libk3b2 (decode only)
libk3b2-mp3 (decode only)

The packages marked with (decode only) I don't think are needed for ripping to MP3, which is encoding.  Lame is the MP3 encoder.

After you have these packages, you'll have to configure K3B to use them:

[LIST]
[*]Go to Settings -> Configure K3b -> Plugins.
[*]You should see an entry "K3b External Audio Encoder".  Select that and click "Configure"
[*]Click on "Add" and enter:
[LIST]
[*]Name: MP3 (lame)
[*]Filename extension: mp3
[*]Command: /usr/bin/lame -h -m j --abr 128 --tt %t --ta %ta --tl %m --ty %y --tn %n --tc %c - %f
[/LIST]
[/LIST]

You should then be able to see the MP3 options in the drop down list of target formats when you click on ripping.

---

### Post by xXJT-JaredXx on 2008-01-07
thx wolframarnold i had the same kinda problem n i'm running gutsy, i already had an mp3 pluggin but the command line was different to the 1 u provided so i added urs and it seems to work now

---

