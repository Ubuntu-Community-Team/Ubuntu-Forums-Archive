---
title: "DVD Ripper?"
date: 2009-03-18
forum: Multimedia Software
---

### Post by accooper on 2009-03-18
In Ubuntu is there such a thing as a good DVD ripper?  If so where can I get it and how do I install it?

TIA
Andrew

---

### Post by blue_shift on 2009-03-18
[http://www.google.co.uk/search?q=ubuntu+dvd+rip](http://www.google.co.uk/search?q=ubuntu+dvd+rip)

Also, run synaptic and search for dvd. There are plenty of programmes.

```
sudo synaptic
```

or for k9copy:

```
sudo apt-get install k9copy
```

---

### Post by stinger30au on 2009-03-18
dvdfab runs in wine, but k9copy all the way

---

### Post by bon_the_one on 2009-03-18
DVDRIP is in the multiverse repo, quite simple to use I think.

---

### Post by Bartender on 2009-03-18
Handbrake maybe?
I've got it running in Vista, with DVD43, and it seems to work better than the Linux version.  Hopefully that will change with time.

---

### Post by kidux on 2009-03-18
+1 for DVD:Rip.

---

### Post by Scubdup on 2009-03-18
I had a good at finding one and couldn't. Nothing I've seen on Linux matches DVD Shrink on Windows.

---

### Post by bon_the_one on 2009-03-18
> **Scubdup said:**
> I had a good at finding one and couldn't. Nothing I've seen on Linux matches DVD Shrink on Windows.

sudo apt-get install dvdrip

---

### Post by clancymf on 2009-03-18
If you want to rip to your harddrive - use handbrakecli
If you want to copy to dvd - k9copy + k3b

Make sure you have all the libs you need though in the medibuntu repository

---

### Post by jt_04 on 2009-03-18
-1 for DVD::RIP.  it's easy to use, but it consistently makes my audio/video stream to be completely out of sync.  I've tried using the -D # transcode option to correct the sync, but it is impossible to predict how much out of sync it will be in order to know how much to fix it.  

now I'm using Thoggen to rip my DVDs, and it seems to work great.  Then I use mencoder to convert them to AVIs and pull out clips as desired.  with thoggen and mencoder, I accomplished in under 2 hours what would take me 2 days with DVD::RIP

---

### Post by numbness05 on 2009-04-09
Its a matter of opinion but I would always go with Thoggen its nice peice of DVD ripping softeware but depends what you want to do with the file after as it rips in an ogg format so you would have to convert it after to burn it to DVD but as I only want them as backups on my hardrive this is fine for me.

Give it ago its in your Repo's 

Regards 
Numbness

---

### Post by blackgr on 2009-04-09
handbrake is one of the best. [http://handbrake.fr/](http://handbrake.fr/)

---

### Post by mudman00 on 2009-04-10
> **jt_04 said:**
> -1 for DVD::RIP.  it's easy to use, but it consistently makes my audio/video stream to be completely out of sync.  I've tried using the -D # transcode option to correct the sync, but it is impossible to predict how much out of sync it will be in order to know how much to fix it.  

now I'm using Thoggen to rip my DVDs, and it seems to work great.  Then I use mencoder to convert them to AVIs and pull out clips as desired.  with thoggen and mencoder, I accomplished in under 2 hours what would take me 2 days with DVD::RIP

I have just installed Thoggen and can't get it up and running. I am getting the following message in the titles to be ripped window

"Failed to retrieve DVD title details for some reason. Maybe you do not have libdvdcss2 installed?"

I would like to know what it is that I am doing from a conceptual basis as well as being able to download and install various applications and the codecs, etc...that are necessary to run them.

Questions....what is libdvdcss2 and do I need it for Thoggen to work? What does it do and how does it do it? Where is a safe place to get libdvdcss2 from, keeping in mind that I don't really know what I am doing with Ubuntu yet. I have only had this OS for three weeks now.

Thank you for any and all help

Craig

---

### Post by jt_04 on 2009-04-10
I'm fairly new at all this too, but I'll give it a shot...

Thoggen, like any program, needs different libraries to work.  One of those libraries is what decodes the DVD data.  That particular library is not yet installed on your machine (libdvdcss2).

a dvd cannot just be copied byte-for-byte into a movie because it is encrypted.  the libdvdcss2 library provides the encryption keys necessary to decrypt the dvd into viewable data, which can them be saved as a movie.

to search for the library in the package repositories on the internet, from the prompt, type:

```
sudo apt-cache search libdvdcss2
```

the output from that command will show all the packages that match the search term that can be installed.  the last line should be the libdvdcss2 package.  to install it, type:

```
sudo apt-get install libdvdcss2 
```


But in this case, libdvdcss2 is one of many packages included in the package "ubuntu-restricted-extras" that come in handy for many things ([read more here]("https://help.ubuntu.com/community/RestrictedFormats")), so you might as well install that whole package:

```
sudo apt-get install ubuntu-restricted-extras
```

and then Thoggen should work.


by the way, i finally reverted back to DVD::RIP.  the quality of the movies that Thoggen produced was too low for me, and I couldn't find a way to adjust it.

good luck

---

### Post by mudman00 on 2009-04-12
> **jt_04 said:**
> -1 for DVD::RIP.  it's easy to use, but it consistently makes my audio/video stream to be completely out of sync.  I've tried using the -D # transcode option to correct the sync, but it is impossible to predict how much out of sync it will be in order to know how much to fix it.  

now I'm using Thoggen to rip my DVDs, and it seems to work great.  Then I use mencoder to convert them to AVIs and pull out clips as desired.  with thoggen and mencoder, I accomplished in under 2 hours what would take me 2 days with DVD::RIP
I just began using Thoggen earlier today. It seems to be doing what it is supposed to do but is taking what seems like a very long time.....for example, when attemtpting to rip a copy of the kids Treasure Planet the programm indicated that it would take over four hours. Is this a normal speed or am I doing something wrong?

Thankyou for any and all help
Craig

---

### Post by donovan1983 on 2009-04-12
> **blackgr said:**
> handbrake is one of the best. [http://handbrake.fr/](http://handbrake.fr/)

I've been a big fan of HandBrake for a long time on any platform it runs on. On Ubuntu with libdvdcss installed it rips and encodes all in one shot, too. When encoding into H.263 format using the Classic preset (and forcing it to use a single thread) I get much better than real-time encoding, usually around 38FPS, on a modest 1.6GHz Atom. I just use the CLI version since it is simpler for me than using the GUI version.

---

### Post by steeleyuk on 2009-04-12
CLI version is quite a bit faster for me as well.

---

### Post by jocheem67 on 2009-04-30
NOFI here guys, but there's some mixing up going on here..

Ripping dvd's and encoding them are quite some different things.

For ripping and keeping them in the dvd-format, there's no real alternative for these two options:

k9copy ( it's kde, so it's quite ugly on gnome, but it is stable )
dvdfab and dvdshrink with wine ( windows-apps that do run well on ubuntu, with a little tweaking, I guess it's moderate level ubuntuknowledge ) 

Ripping and encoding them to a compressed format, well then there are quite some options:

ffmpeg, mencoder and transcode from the cli ( quite complicated, but very entertaining, and there's some threads about them on the forums and way more on google )
dvd::rip ( old but stable, only avi though )
acidrip ( stable, don't know it too well )
handbrake ( a bit new, seems like a good bet as it uses x264 )
avidemux ( doesn't rip, lots of options though )

If it comes to new dvd's , no re-encoding and newer protections like arcoss, the best choice would imho be wine with dvdfab and dvdshrink...one can end up with a nice iso, burn it to disc or just watch it from the HD ( vlc reads iso's just as I think totem )...

Personally I don't really see the need for encoding anymore ( harddrives are getting bigger and bigger, it consumes time, quality goes down, syncing and subs issues, alot of hassle )
Only when it comes to psp and iPhone stuff it should be a topic imho..

---

### Post by Melcar on 2009-04-30
Another encoder is OGMRip.  But yeah, for keeping the DVDs intact K9copy is the best.

---

### Post by spooner on 2009-04-30
> **jt_04 said:**
> -1 for DVD::RIP.  it's easy to use, but it consistently makes my audio/video stream to be completely out of sync.  I've tried using the -D # transcode option to correct the sync, but it is impossible to predict how much out of sync it will be in order to know how much to fix it.  

now I'm using Thoggen to rip my DVDs, and it seems to work great.  Then I use mencoder to convert them to AVIs and pull out clips as desired.  with thoggen and mencoder, I accomplished in under 2 hours what would take me 2 days with DVD::RIP

I was having this problem...
Was solved by passing the "-M *" option. But its trial and error to find the right demuxer for your source...

> 
-M mode
    demuxer PES AV sync modes (0-4) [1].

        Overview
            The demuxer takes care that the right video frames go together with the right audio frame. This can sometimes be a complex task and transcode tries to aid you as much as possible.
            WARNING: It does make a difference if you (the user) specifies a demuxer to use or if transcode resp. tcprobe(1) chooses the one which it thinks is right for your material.
            This is done on purpose to avoid mystic side-effects. So think twice, wether you specify a demuxer or let transcode choose one or you might end up with an off-sync result. 
        0
            Pass-through. Do not mess with the stream, switch off any synchronization/demuxing process. 
        1
            PTS only (default) Synchronize video and audio by inspecting PTS/DTS time stamps of audio and video. Preferred mode for PAL VOB streams and DVDs. 
        2
            NTSC VOB stream synchronization feature. This mode generates synchronization information for transcode by analyzing the frame display time. 
        3
            (like -M 1): sync AV at initial PTS, but invokes "-D/--av_fine_ms" options internally based on "tcprobe" PTS analysis. PTS stands for Presentation Time Stamp. 
        4
            (like -M 2): initial PTS / enforce frame rate, with additional frame rate enforcement (for NTSC). 


I'd +1 for handbrake... because of H.264 support and mkv containers!!

---

### Post by SuperSonic4 on 2009-04-30
+1 for k9copy, especially when it comes to creating a direct copy of a dvd into ISO format which can either be watched on vlc (it does handle video ISOs) or burned to a dvd to give a dvd quality copy

---

### Post by peterqb on 2009-04-30
> **jt_04 said:**
> -1 for DVD::RIP.  it's easy to use, but it consistently makes my audio/video stream to be completely out of sync.  I've tried using the -D # transcode option to correct the sync, but it is impossible to predict how much out of sync it will be in order to know how much to fix it.  

now I'm using Thoggen to rip my DVDs, and it seems to work great.  Then I use mencoder to convert them to AVIs and pull out clips as desired.  with thoggen and mencoder, I accomplished in under 2 hours what would take me 2 days with DVD::RIP

Neither Thoggen nor mencoder work in 9.04. I'm not sure what the problem is. Movie player won't work either, giving an error "can't read from source".

Any ideas? Thanks.

---

### Post by logos34 on 2009-04-30
> **jt_04 said:**
> -1 for DVD::RIP.  it's easy to use, but it consistently makes my audio/video stream to be completely out of sync.  I've tried using the -D # transcode option to correct the sync, but it is impossible to predict how much out of sync it will be in order to know how much to fix it.  

...with thoggen and mencoder, I accomplished in under 2 hours what would take me 2 days with DVD::RIP

anyone else notice the sync issue?  

don't do a lot of video ripping and encoding, but whenever I have I've used dvdrip.  lots of config options

---

### Post by diggity on 2009-04-30
Personally, I think DVDFab HD Decrypter is the best available.
You can rip the entire dvd or just the main movie without compression.
It runs very well under wine.
If you want compression, simply use handbrake after ripping with dvdfab.

---

