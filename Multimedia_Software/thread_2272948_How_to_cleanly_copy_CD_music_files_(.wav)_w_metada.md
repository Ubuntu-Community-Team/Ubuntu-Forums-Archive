---
title: "How to cleanly copy CD music files (.wav) w/ metadata ???"
date: 2015-04-09
forum: Multimedia Software
---

### Post by ozark_hillbilly on 2015-04-09
I am trying to find the cleanest way to copy CD music files (.wav) onto my hard drive so that the song/artist information is retained.
Currently I am simply copying the .wav files onto my /Music folder from the music CD, but they have no attached data regarding song/artist etc. The songs
are listed in the folder as Track 1.wav, Track 2.wav, etc. Under the Properties - General Tab no information is listed as well.

I then use FLAC, in Terminal mode, to convert the .wav files to a more manageable size while retaining sampling rate quality.

Is there a way to include the information about the artist/album/song title during the copy process? Rhythmbox shows the information but I
believe it retrieves this off the web and not the CD itself. Renaming songs manually by referencing the CD jacket material and transcribing it
has no future to me. It's cumbersome and time consuming. 
Any suggestions are welcome. Thanks.

---

### Post by Keith_Helms on 2015-04-09
CDs don't have any song/artist information on them.   They do have a  disc ID number on them which various player and ripper software packages  use to lookup that information from CDDB servers (CD database).   Wav  files also do not have any tag information on them other than just the file and directory names.  Your best bet is to  use a ripper that will invoke an MP3 or FLAC encoder and supply that  encoder with tag information about the album and songs.

You mentioned using  Rhythmbox, so take a look at this site.  It's an older post, but the  instructions might still be valid or might at least get you started:

[http://www.maketecheasier.com/rip-audio-cd-in-linux/](http://www.maketecheasier.com/rip-audio-cd-in-linux/)

---

### Post by oldfred on 2015-04-09
I have always use Sound Juicer/Gnome Audio CD extractor. But also have seen Asunder recommended. Both are in repository.
I change a few settings and rip to flac.

Several years ago when I converted to mp3 and copied to my mp3 player, it seemed slow copying. But when I converted and copied in one step with Sound Converter it seemed faster. So I do not have mp3s on my hard drive anymore.

---

### Post by ozark_hillbilly on 2015-04-10
Thanks folks! Asunder seems to fit the bill quite nicely.

---

### Post by andrew.46 on 2015-04-10
Just as point of interest: wav files actually can carry meta data:

[http://en.wikipedia.org/wiki/WAV#Metadata](http://en.wikipedia.org/wiki/WAV#Metadata)

but I have yet to find a method of doing this under Linux. And of course it is not really what the OP was after :).

---

### Post by Keith_Helms on 2015-04-11
> **andrew.46 said:**
> Just as point of interest: wav files actually can carry meta data:

[http://en.wikipedia.org/wiki/WAV#Metadata](http://en.wikipedia.org/wiki/WAV#Metadata)

but I have yet to find a method of doing this under Linux. And of course it is not really what the OP was after :).

Interesting.  Ya learn something every day!  Does abcde support wav metadata?

---

### Post by andrew.46 on 2015-04-11
> **Keith_Helms said:**
> Interesting.  Ya learn something every day!  Does abcde support wav metadata?

No, not at all. A linux application to add meta data to wav files would be great and tagging could be done post rip but as far as I am aware such a tagger does not yet exist for Linux...

---

### Post by mc4man on 2015-04-11
> **andrew.46 said:**
> No, not at all. A linux application to add meta data to wav files would be great and tagging could be done post rip but as far as I am aware such a tagger does not yet exist for Linux...
Possibly with [kid3]("http://kid3.sourceforge.net/") (kde or qt) though player recognition  could be sparse
(- dBpoweramp in wine tags wav but again only some players see.

---

### Post by mcduck on 2015-04-11
> **andrew.46 said:**
> Just as point of interest: wav files actually can carry meta data:

[http://en.wikipedia.org/wiki/WAV#Metadata](http://en.wikipedia.org/wiki/WAV#Metadata)

but I have yet to find a method of doing this under Linux. And of course it is not really what the OP was after :).

Of course that wouldn't help the OP since audio CD's don't actually contain WAV files, or any files at all (even though your file manager might be smart enough to visualize the disc's content as such to the user). ;)

---

### Post by mc4man on 2015-04-11
> **mcduck said:**
> Of course that wouldn't help the OP since audio CD's don't actually contain WAV files, or any files at all (even though your file manager might be smart enough to visualize the disc's content as such to the user). ;)
As soon as the track(s) are either directly copied via the file manager or ripped to .wav with an audio cd ripper then they are wave (pcm) files so don't get your point..
(- a direct  copied track can contain a bit of metadata, in gnome - 'gvfs-cdda using libcdio 0.83 x86_64-pc-linux-gnu' or similar

---

### Post by mcduck on 2015-04-11
My point was that the files one might see on the disc don't exist, and thus don't contain the metadata. So it's something that needs to be added to the files by the program you use to rip the CD, either by pulling the information from the Internet or from the disk itself it it happens to have CD-Text data on it.

So, if you happen to be able to open the CD in a file manager and view it as .wav files with no metadata on them, it's not worth trying to change the underlying system your file manager uses to display the CD to you that way to also include metadata on the .wav files,but instead just ignore the virtual .wav files completely and instead just rip the disc with a program that *does* add metadata to the files. While you are at it, you can also encode them directly to the desired format (which probably isn't .wav anyway).

So if the default ripper built in to the file manager doesn't give you features and format you want, might as well use a different tool (since you will need to rip the CD anyway as opposed to just copying already existing files from the disk like you could do with a data CD or DVD)

(It's of course a different question if the ripper built in the file manager actually *does* find all the metadata you want and allows you to directly run the virtual .wav files you see on the disc through an encoder since at that point you would actually be saving yourself from some extra work. But copying the .wav files to the hard drive and then encoding them would justa dd work compared to using a dedicated CD ripper/encoder to do both at the same time,)

---

### Post by andrew.46 on 2015-04-21
> **mc4man said:**
> Possibly with [kid3]("http://kid3.sourceforge.net/") (kde or qt) though player recognition  could be sparse

Just for the sake of completion I built a copy of kid3 and tagged this wav file:

```

wget http://www.andrews-corner.org/samples/luckynight.wav

```

Mediainfo shows the following:

```

andrew@ilium~/media/luckynight/test$ mediainfo luckynight.wav 
General
Complete name                            : luckynight.wav
Format                                   : Wave
File size                                : 10.2 MiB
Duration                                 : 1mn 0s
Overall bit rate mode                    : Constant
Overall bit rate                         : 1 411 Kbps
Album                                    : Treasure Quest Soundtrack
Track name                               : Lucky Night
Track name/Position                      : 9
Performer                                : Jody Marie Gnant
Genre                                    : Soundtrack
Recorded date                            : 1995
Comment                                  : 1-minute song sample demonstrating WAV tagging

Audio
Format                                   : PCM
Format settings, Endianness              : Little
Format settings, Sign                    : Signed
Codec ID                                 : 1
Duration                                 : 1mn 0s
Bit rate mode                            : Constant
Bit rate                                 : 1 411.2 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Stream size                              : 10.2 MiB (100%)

```

More of an academic exercise than anything I guess, although I note that vlc reads the meta tags...

---

