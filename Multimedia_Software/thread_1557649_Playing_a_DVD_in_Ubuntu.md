---
title: "Playing a DVD in Ubuntu"
date: 2010-08-21
forum: Multimedia Software
---

### Post by cwklinuxguy on 2010-08-21
Hi am I using Ubuntu Karmic Koala on an EEE PC Netbook and I'm wondering if anyone knows how I can play a DVD. I have tried it but I just get an error message from Movie Player. Any way to do it on Ubuntu?

---

### Post by Rinzwind on 2010-08-21
- WHAT error message?

- Have you checked the official wiki page on playing dvd's:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

It has some packages that need to be installed.

---

### Post by prshah on 2010-08-21
> **cwklinuxguy said:**
> get an error message from Movie Player. 

Personally I use only VLC for all my video playback needs. I suggest you install VLC from the repositories and use that to play DVDs (and other video formats).

You will also need to install restricted extras.

A quick way to do this is to open the terminal and give the command```
sudo apt-get install vlc ubuntu-restricted-extras
```

---

### Post by Nick_Jinn on 2010-08-21
> **cwklinuxguy said:**
> Hi am I using Ubuntu Karmic Koala on an EEE PC Netbook and I'm wondering if anyone knows how I can play a DVD. I have tried it but I just get an error message from Movie Player. Any way to do it on Ubuntu?


You have to install Medibuntu. I dont think the restricted extras are enough.

You can watch unencrypted dvds with restricted extras, but if you want to watch a commercial DVD you have better get Medibuntu instead.

---

### Post by cwklinuxguy on 2010-08-21
Are said "restricted extras" legal in the United States?

---

### Post by Nick_Jinn on 2010-08-21
Its pretty much a non-issue for end users. Those extras would have come with the hardware you purchased if it originally had windows. No cop is going to pull you over for web surfing with restricted extras, even if they confiscated your PC.


It is however an issue for software producers. Cononical could get in trouble (maybe, but unlikely) if they were selling PCs without paying a small royalty, but thats something the software developers and PC vendors have to worry about. Its not something you or I need to worry about.

---

### Post by shantiq on 2010-08-21
a short answer is this


you need ubuntu-restricted extras from your synaptic


system/admin/synaptic


see attached image

---

### Post by sauravpidit on 2010-08-22
> **cwklinuxguy said:**
> Hi am I using Ubuntu Karmic Koala on an EEE PC Netbook and I'm wondering if anyone knows how I can play a DVD. I have tried it but I just get an error message from Movie Player. Any way to do it on Ubuntu?
I am very sorry but I am having the same problem and I really need some help. 
I even put the code into the terminal, like they asked me to but the DVD still doesn't play. I have tried about half a dozen dvd software including Kaffine, KMPlayer, Mplayer, Gnome Mplayer, Xfmedia but I have had no luck. Any other input would be greately appriciated.

---

### Post by mc4man on 2010-08-22
> I am very sorry but I am having the same problem 
you probably just need libdvdcss2 installed
Go to the link provided in post 2

---

### Post by Nick_Jinn on 2010-08-22
You will also need the 32 or 64 bit codecs. By far the easiest way is to install the entire medibuntu repository. Restricted extras isnt enough. Not for commercial DVDs anyway.

---

### Post by mc4man on 2010-08-23
> You will also need the 32 or 64 bit codecs. By far the easiest way is to install the entire medibuntu repository. Restricted extras isnt enough. Not for commercial DVDs anyway.

The only thing in medibuntu that relates to dvd playback (as in encrypted "commercial DVDs" ) is libdvdcss2

---

### Post by Nick_Jinn on 2010-08-23
You could be right. What are the w32 and w64 codecs for then?

---

### Post by andrew.46 on 2010-08-28
Hi Nick,

> **Nick_Jinn said:**
> What are the w32 and w64 codecs for then?

These are the debian names for a collection of mostly Windows codecs and dlls put together by the MPlayer developers. The actual codecs are here:

[http://www.mplayerhq.hu/MPlayer/releases/codecs](http://www.mplayerhq.hu/MPlayer/releases/codecs)

Several programs, such as MPlayer and a correctly configured 32 bit vlc, can use these codecs to play some files for which native Linux playback is not yet possible. The importance and actual usefulness of these codecs is frequently overstated :).

Andrew

---

### Post by mc4man on 2010-08-28
> The importance and actual usefulness of these codecs is frequently overstated
That's certainly true, and in some cases where you'll have dual support thru both libavcodec and w32codecs the ffmpeg decoders can do a better job.

(some players will default to one or the other, mplayer, which defaults to dmo in some cases, remains the most flexible by allowing a specified -acodec and -vcodec
I keep w32codecs installed for the oodball codec and wmal, making adjustments in the players when needed ( or in the case of vlc in the source - removing some codecs from dmo

---

### Post by Nick_Jinn on 2010-08-28
> **andrew.46 said:**
> Hi Nick,



These are the debian names for a collection of mostly Windows codecs and dlls put together by the MPlayer developers. The actual codecs are here:

[http://www.mplayerhq.hu/MPlayer/releases/codecs](http://www.mplayerhq.hu/MPlayer/releases/codecs)

Several programs, such as MPlayer and a correctly configured 32 bit vlc, can use these codecs to play some files for which native Linux playback is not yet possible. The importance and actual usefulness of these codecs is frequently overstated :).

Andrew

But isnt lacking those codecs a possible explanation for watching some DVDs that are not playing?

---

### Post by andrew.46 on 2010-08-28
Hi Nick,

> **Nick_Jinn said:**
> But isnt lacking those codecs a possible explanation for watching some DVDs that are not playing?

For the most part commercial DVDs utilise some pretty unexciting codecs, you will usually see MPEG-2 video and AC-3 or MP2 sound. So extra codecs are usually not necessary, much more common are problems with copy protection...

Andrew

---

### Post by jmore9 on 2010-08-28
Go here :

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Which is the Comprehensive Multimedia & Video Howto in the Multimedia section.

Scroll down to part 4/5 which is the dvd playback section.

---

### Post by mc4man on 2010-08-28
> But isnt lacking those codecs a possible explanation for watching some DVDs that are not playing?
no 
I think sometimes it's useful to note that enabling dvd playback is different than the quality of that playback, (audio, video outputs used, video drivers intalled), or occasional access issues. (region setting on drive or lack of, region mismatch with matshita laptop drives, some structure protections on the disc, ect.

At it's very simplest dvd playback is enabled  with a couple of commands

Third party players like vlc, mplayer just need libdvdcss2, that's all.
Ex.
```
sudo apt-get install vlc && \
sudo /usr/share/doc/libdvdread4/install-css.sh
```

That's it, dvd playback is now enabled for vlc, if mplayer was installed it too.

Xine based players need 1 additional package - libxine1-ffmpeg

gstreamer players need a couple of plugins, so for instance on a fresh install ... 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly && \
sudo /usr/share/doc/libdvdread4/install-css.sh

```
That again is it - any other issues are not because of missing codecs, libs or plugins

---

### Post by gunthergloop on 2010-08-29
I'd just like to say thanks for this thread and all replies. Playback of my copyrighted DVDs still wasn't working for me up until the last post even though I tried everything else. (64-bit 10.04 Ubuntu FWIW)

It's all working now finally, so thanks again. :)

---

### Post by B-Mart on 2010-08-29
Either way, I would just be all like, YO! I GOT IT FROM THE INTERWEBS OFFICER! IT'S ALL FREE! I DIDN'T KNOW.

But yeah, a good thing to do is to also check and see if you have the proper codecs to play some movie formats, sometimes they don't get properly installed with movie player. :/

---

### Post by Old *ix Geek on 2010-09-09
> **Rinzwind said:**
> Have you checked the official wiki page on playing dvd's:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

It has some packages that need to be installed.Just wanted to thank you for this link--its info solved my problem beautifully. (I could view DVDs just fine...but with *NO* sound!)

---

