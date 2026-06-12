---
title: "Writing song title, artist, etc. to files."
date: 2012-06-10
forum: Multimedia Software
---

### Post by Damascushead on 2012-06-10
So I have been searching high and low for a piece of software which will write the song title, artist, and album information to a .wav file.

Basically what I am trying to do is post some of my own music to a website which I am still creating. I am giving the music away for free, and I want people to be able to just click and download the music. It would be of great benefit if, when they download it, the song titles, artist name, and all track information is already on the files. Because there is nothing more annoying than manually entering in that information. I figure that burning software might do this properly. ( When I worked at a recording studio we used TOAST for this kind of thing.) Well since leaving the studio I have not been able to get my hands on software that will do this for less than 500 bucks. 

 No typical burning software that I have access to has done this properly (open source or otherwise). I have tried it through Windows Media player, Infra Recorder (both on windows) and on Brasero.  I even tried using TAGEditor (open sourced, also in spanish) to edit the ID3 tags on the wav files. I know I could use a different format, but I would like it to be a universally friendly format.  

Any help would be greatly appreciated!       :confused:

---

### Post by evilsoup on 2012-06-10
As far as I know, WAV files don't support metadata. Not ID3 tags at any rate, the WAV format predates ID3.
Encode it to MP3 or OGG (depending on your priorities); or, if you want lossless audio, use FLAC - which should sound identical to your WAV files, but at about half the filesize and with support for metadata tags.

Off the top of my head,

avconv -i input.wav -metadata title="track title" -metadata author="track artist" -metadata album="album name" -metadata track="track number" output.flac

should do the trick (assuming you have avconv installed, it's in the repositories). [This]("http://multimedia.cx/eggs/supplying-ffmpeg-with-metadata/") is slightly outdated (I think more things are supported in ffmpeg/avconv now), but it should give you an idea.

Hopefully someone else will be along shortly with a GUI solution.

EDIT: D'oh! I completely misread your post, sorry. Hopefully what I've written will be of use to someone (just tested it out and avconv can't put metadata onto WAV files, so it's no use to you I'm afraid).

---

### Post by d2btoo on 2012-06-10
Does EasyTAG(mp3 and such) counts?

*not sure abt WAV though!

---

### Post by evilsoup on 2012-06-10
Well, a [quick google search]("http://lmgtfy.com/?q=WAV+metadata") led me to this [audacity forum thread]("http://forum.audacityteam.org/viewtopic.php?f=18&t=63920"), which states that Audacity (which is in the repositories) can write some basic metadata to WAV files.

However, I've yet to come across any WAV file with metadata on it; at least, not that any software I've ever used - in Linux, Windows or OSX - has readily recognised. And that thread supports my gut instinct. Also, for delivery over the internet, WAV is not exactly an ideal format: it's too large.

Go with MP3 if you want near-universal support, or OGG if you particularly care about patents, or FLAC if you think people need the audio completely identical to what you have. All of these support metadata in well-documented and standardised ways.

---

### Post by nickrout on 2012-06-11
I am unsure whether wav supports tags, but flac is lossless and does! Also you will save a lot of bandwidth using compressed files.

---

### Post by shantiq on 2012-06-11
> **Damascushead said:**
> So I have been searching high and low for a piece of software which will write the song title, artist, and album information to a .wav file.

Basically what I am trying to do is post some of my own music to a website which I am still creating. I am giving the music away for free, and I want people to be able to just click and download the music. It would be of great benefit if, when they download it, the song titles, artist name, and all track information is already on the files. Because there is nothing more annoying than manually entering in that information. I figure that burning software might do this properly. ( When I worked at a recording studio we used TOAST for this kind of thing.) Well since leaving the studio I have not been able to get my hands on software that will do this for less than 500 bucks. 

 No typical burning software that I have access to has done this properly (open source or otherwise). I have tried it through Windows Media player, Infra Recorder (both on windows) and on Brasero.  I even tried using TAGEditor (open sourced, also in spanish) to edit the ID3 tags on the wav files. I know I could use a different format, but I would like it to be a universally friendly format.  

Any help would be greatly appreciated!       :confused:

a very simple way to do this is to upload them in a lossless format like flac which tags with no problems  [and is universal]   and the sound is excellent too


[B]
BUT
[/B] if wav is your target
there is one that will write tags to wav

it is **[dbpoweramp]("http://www.dbpoweramp.com/cd-ripper.htm")** which installs under wine and tags wav files   use the convert option for this from say a tagged flac version of your file  [tag that on with easytag first]  TAGS will be kept in the resulting wav   

see


> mediainfo *.wav
General
Complete name                            : 01 This world - Selah Sue.wav
Format                                   : Wave
File size                                : 48.1 MiB
Duration                                 : 4mn 45s
Overall bit rate mode                    : Constant
Overall bit rate                         : 1 412 Kbps
Album                                    : Selah Sue
Track name                               : This world
Track name/Position                      : 01
Performer                                : Selah Sue
Director                                 : Selah Sue
Genre                                    : Indie
Recorded date                            : 2011
Original source form/Name                : Selah Sue
Cover                                    : Yes
Cover type                               : Cover (front)
Cover MIME                               : image/jpeg
Comment                                  : Track 1
ITRK                                     : 01




then you still have the problem of    which players will pick up the wav info   [most expect none there]


deadbeef     xmms      winamp under Wine    do not      the only one that does perfectly on my system is vlc  [ATTACH]219516[/ATTACH]



i think  ** flac **   and better even   24-bit flac [96Khz]   is your best option

**universal    tagged and high audiophilic quality:KS**    and tagged with easytag a fully Linux solution

---

### Post by Damascushead on 2012-06-11
Thanks for all of the feedback.
 
**evilsoup, nickrout, shantiq**- It seems that converting to FLAC for lossless compression is a suitable option. I am glad there is a quick command line solution for the conversion and tagging as well. I was a little skeptical of having a compressed only version of my music. I am planning to have multiple formats available for download. But the more I think about it the more I think i will use FLAC and perhaps mp3 and ogg. 
 
It has always just driven me nuts though that .wav is so hard to tag properly. I will give these ideas a shot, particularly the avconv method.
 
I will let you know how it goes. Hopefully my music will be up soon.

---

### Post by FakeOutdoorsman on 2012-06-11
You could copy the WAV into the MKA container format:
```
ffmpeg -i input.wav -acodec copy -metadata title="track title" -metadata author="track artist" -metadata album="album name" -metadata track="track number" output.mka
```
Although I think FLAC is a better idea and I doubt the general public is familiar with the Matroska container format since their standard Windows apps will probably be useless (this is an uneducated guess).

---

### Post by Damascushead on 2012-06-12
Ok so I decided to go the flac route and all of the metadata wrote very easily and flawlessly with avconv. I didn't even know avconv existed, but I guess it comes standard with 12.04. 
 
Thanks for the help everyone, specially evilsoup.
 
Peace  :D

---

### Post by davidw1957 on 2012-12-31
Here are a couple of shell scripts to make editing/entering metadata a bit easier.
[http://www.davidreeves.com/.short/metadata1tarball](http://www.davidreeves.com/.short/metadata1tarball)
[http://www.davidreeves.com/.short/metadata2zip](http://www.davidreeves.com/.short/metadata2zip)

Both links are to the same files. just that one is a .tar.gz and the other is a .zip

---

