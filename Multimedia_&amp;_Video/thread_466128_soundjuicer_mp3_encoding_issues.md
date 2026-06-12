---
title: "soundjuicer mp3 encoding issues"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by fopdoodledavid on 2007-06-06
Hi! I'm trying to get soundjuicer to rip my cds in mp3 form, but it's not working out so well. I read the little help manual and went to preferences and made a new GNOME audio Profile for mp3s, and used this mess "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux" in the little GStreamer pipeline box. I clicked the little active box and closed out and the mp3 profile I made doesn't appear. I've restarted soundjuicer and my computer with no luck. Any helpful ideas? Thank you for your help!

---

### Post by steeleyuk on 2007-06-06
As far as I know the Sound Juicer profile thing is broke. You'll need to edit the profiles this way:

Go to the terminal and enter:

gconf-editor

Follow the path in gconf-editor to:

/system/gstreamer/0.10/audio

From there you should be able to add, delete and edit the profiles. (The above assumes you have gstreamer0.10 installed)

PS. I've not tried this personally so can't guarantee it will work...

---

### Post by fopdoodledavid on 2007-06-09
Hey, thanks for the suggestion. I followed your path and I found the mp3 profile I'd made with all of specifications I wanted. Unfortunately, it still doesn't appear as an option in the main preferences window. I can choose from FLAC, Ogg, WAV and an unknown one. Any tips for how to get it to pop up in the interface? Thanks again.

---

### Post by Circus-Killer on 2007-06-12
yeah, having the same problem. can add the profile, just cant select it in the popup menu in soundjuicer. it seems to be a common bug yet i cant find a solution.

---

### Post by fopdoodledavid on 2007-06-13
Is there some way to, like, manually set the encoder soundjuicer uses? Like... some secret terminal code thing that sets the preferences without using the windows etc.? I have no technical knowhow, so I have no idea how to do stuff like that. *sigh* I just really want to be able to rip my cds as mp3s.

---

### Post by kongwak on 2007-06-13
Just a silly question, but when you created the profile, did you tick the "make active" box?

kongwak

---

### Post by Major_Kong on 2007-06-14
> **fopdoodledavid said:**
> Is there some way to, like, manually set the encoder soundjuicer uses? Like... some secret terminal code thing that sets the preferences without using the windows etc.? I have no technical knowhow, so I have no idea how to do stuff like that. *sigh* I just really want to be able to rip my cds as mp3s.

Use the following command:

```
gst-inspect-0.10 lame
```

It will show you the syntax options.


Gstreamer pipeline examples:

```
audio/x-raw-int,rate=44100,channels=2 ! lame quality=0 vbr=4 vbr-quality=3 ! id3v2mux
```

The result is a ~175 kBps VBR MP3 using the "new VBR algorithm".

---

### Post by jcoles on 2007-07-11
The simplest method is to just use cdparanoia and lame directly from the command line. You can even create scripts so that your preferred options are always set.

SoundJuicer doesn't offer mp3 as an option. It's only the most popular format! 

soundKonverter looks promising, but it just doesn't work. The CD spins, the display says "Ripping...", but the counter stays at 0%. It's a pity. 

Fortunately, there is nothing wrong with the underlying non-GUI programs that do the work. 

I have used command line programs for ripping, encoding, and CD writing the same way over several years and distributions of Linux. Each distribution has different GUI-based programs. But, many are poorly designed and puzzling to use. And sometimes they just don't work.

I could go into more detail if you like.

---

### Post by bennyj on 2007-07-12
> **jcoles said:**
> The simplest method is to just use cdparanoia and lame directly from the command line. You can even create scripts so that your preferred options are always set.

SoundJuicer doesn't offer mp3 as an option. It's only the most popular format! 

soundKonverter looks promising, but it just doesn't work. The CD spins, the display says "Ripping...", but the counter stays at 0%. It's a pity. 

Fortunately, there is nothing wrong with the underlying non-GUI programs that do the work. 

I have used command line programs for ripping, encoding, and CD writing the same way over several years and distributions of Linux. Each distribution has different GUI-based programs. But, many are poorly designed and puzzling to use. And sometimes they just don't work.

I could go into more detail if you like.

That would be great! some command line examples?

---

### Post by fopdoodledavid on 2007-07-13
Yeah, just running it from terminal sounds awesome. Some examples of how to rip cds/burn cds would be awesome. Thanks!

---

### Post by stchman on 2007-07-13
> **fopdoodledavid said:**
> Hi! I'm trying to get soundjuicer to rip my cds in mp3 form, but it's not working out so well. I read the little help manual and went to preferences and made a new GNOME audio Profile for mp3s, and used this mess "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux" in the little GStreamer pipeline box. I clicked the little active box and closed out and the mp3 profile I made doesn't appear. I've restarted soundjuicer and my computer with no luck. Any helpful ideas? Thank you for your help!

Do you have the proper codecs installed?

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

---

### Post by bennyj on 2007-07-13
> **fopdoodledavid said:**
> Yeah, just running it from terminal sounds awesome. Some examples of how to rip cds/burn cds would be awesome. Thanks!

ffmpeg -i input.wav -acodec mp3 -ab 192kb -ac 2 output.mp3

There is all kinds of options using ffmpeg that will give you granular control.You just have to read up on it.

---

### Post by mjukr on 2007-07-15
From the Terminal:

sudo aptitude install gstreamer0.10-plugins-ugly-multiverse

Restart Sound Juicer. The MP3 ripping profile can now be set as the default. Note that you do *not* need to create that MP3 profile by hand from Feisty forward; it's already there.

---

### Post by capt scroggins on 2007-08-18
Thanks for this. I was trying to get mp3 ripping enabled for about 2 hours until I found this. I could create the mp3 profile in Soundjuicer but it wouldn't show up as an option until running this from terminal.

---

### Post by andrew.46 on 2007-08-24
Hi,

 I could not agree more with the following:

> **jcoles said:**
> The simplest method is to just use cdparanoia and lame directly from the command line. You can even create scripts so that your preferred options are always set..

 But there is a script that is readily available called abcde which does all of these things. In fact I have published a few details at:

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3)

 With another section below on ogg.

                  Andrew

---

### Post by BudaAlien on 2007-09-22
> **Major_Kong said:**
> Use the following command:

```
gst-inspect-0.10 lame
```

It will show you the syntax options.


Gstreamer pipeline examples:

```
audio/x-raw-int,rate=44100,channels=2 ! lame quality=0 vbr=4 vbr-quality=3 ! id3v2mux
```

The result is a ~175 kBps VBR MP3 using the "new VBR algorithm".

I have the Gstreamer plugins installed, through add/remove, on fiesty and this is my return:

$ gst-inspect-0.10 lame
No such element or plugin 'lame'

Could be one reason why I can't rip cd's either!

---

### Post by julian67 on 2007-09-22
There are several excellent alternatives to sound-juicer. For a GUI client [Asunder](http://littlesvr.ca/asunder/) is excellent. Like sound-juicer it will retrieve cddb info and write the tags. It will encode to Flac, Ogg or mp3, or all three at the same time if you like.

>     *  Can save audio tracks as WAV, MP3, Ogg Vorbis, and FLAC audio files
    * Uses CDDB to name and tag each track
    * Creates M3U playlists
    * Can encode to multiple formats in one session
    * Simultaneous rip and encode
    * Allows for each track to be by a different artist
    * Does not require a specific desktop environment


In the terminal the best i found is [Ripit]("http://www.suwald.com/ripit/ripit.html") 

> The program will do the following without user intervention:

  # gets the Audio CD Album/Artist/Tracks information from CDDB
  # rips the Audio CD Tracks
  # encodes to flac, mp3 or ogg
  # id3 tags encoded songs
  # Creates an playlist (m3u) file
  # Can generate a toc (cue) sheet for nice DAO burning
  # Can prepare and send a CDDB submission and save it locally
  # Can extract hidden songs and split ghost songs
  # May create md5sum files for all tracks
  # Run several encoder processes at the same time and same run


It supports mp3, Ogg, Faac, Flac, wav+toc. It can write the different formats to different folders which is very useful. I've been using the recent beta version and it's flawless. To rip a CD I just insert the CD into a drive and enter ripit in the terminal and soon after I have a folder of flacs+m3u and a folder of oggs+m3u, all tagged and named how I want. It's as close to a perfect CD ripper as I've found on any OS.

---

### Post by BudaAlien on 2007-09-22
I have got this fixed! For all who do not want to do everything in Term, here is how to have Sound Juicer encode to .mp3.

First you do need to install the Gstreamer 'ugly' plugin pack. But for whatever reason when you do this from the 'Add/Remove' panel it does not install the lame codec! (I think WTF aplies here!)

Goto System>Administration>Synaptic Package Manager. Search for and install gstreamer0.10-lame. It has the following dependencies:

libc6(>=2.3.6-6)
libglib2.0-0(>-=2.12.0)
libgstreamer0.10-0(>=0.10.10)
liblame0(>=3.97)
libxml2(>=2.6.27)

Happy ripping!  :guitar:

---

### Post by QwUo173Hy on 2007-09-24
> **mjukr said:**
> From the Terminal:

sudo aptitude install gstreamer0.10-plugins-ugly-multiverse

Restart Sound Juicer. The MP3 ripping profile can now be set as the default. Note that you do *not* need to create that MP3 profile by hand from Feisty forward; it's already there.

Thanks mjukr, that did it for me. I had installed the gstreamer0.8 lame package too as mentioned in the howto here
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)
but your post finished it for me.

Thanks again,
Jarlath

---

