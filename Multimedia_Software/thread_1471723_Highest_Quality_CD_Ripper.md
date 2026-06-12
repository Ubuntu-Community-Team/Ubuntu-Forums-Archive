---
title: "Highest Quality CD Ripper"
date: 2010-05-03
forum: Multimedia Software
---

### Post by ttshivers on 2010-05-03
I was just wondering what is the highest quality CD ripper application.  Size does not matter, but quality does. Thanks in advance.

---

### Post by RavanH on 2010-05-03
You are asking about the SOUND quality and not the ripper program quality i suppose? generally the sound quality does not depend on the program being used but on the codec or 'format' the ripper is set to rip to...

Let's suppose you simply use the Rhythmbox that you most likely have on your install already and you choose to import the tracks from a freshly inserted CD. You will find you have the option to choose the format these tracks will be stored as. Choose FLAC for highest (lossless) audio conversion. The tracks will be large in file size but you will be enjoying the highest sound quality :) If you want to reduce the filesize but still have relatively good sound quality you might try OGG. It is said to be better than ancient MP3. But both are lossy audio formats which means you are losing some quality.

Other rippers will likely have these same options.

---

### Post by ttshivers on 2010-05-03
> **RavanH said:**
> You are asking about the SOUND quality and not the ripper program quality i suppose? generally the sound quality does not depend on the program being used but on the codec or 'format' the ripper is set to rip to...

Let's suppose you simply use the Rhythmbox that you most likely have on your install already and you choose to import the tracks from a freshly inserted CD. You will find you have the option to choose the format these tracks will be stored as. Choose FLAC for highest (lossless) audio conversion. The tracks will be large in file size but you will be enjoying the highest sound quality :) If you want to reduce the filesize but still have relatively good sound quality you might try OGG. It is said to be better than ancient MP3. But both are lossy audio formats which means you are losing some quality.

Other rippers will likely have these same options.

I want the sound quality to be high.  What about the WAV lossless codec.  Isn't that good?

---

### Post by gungrog on 2010-05-03
> **ttshivers said:**
> I want the sound quality to be high.  What about the WAV lossless codec.  Isn't that good?

WAV is good, but FLAC will give you the same quality but with a smaller filesize. 

Rubyripper is my ripper of choice at the moment, nice and simple, does what it says on the tin...:D

---

### Post by RavanH on 2010-05-09
Agreed... Although WAV is lossless too, I prefer FLAC when saving CD quality because of the smaller file size. In sound quality there is no difference, they are both formats that save without quality loss.

Only I use Sound Juicer. It uses the MusicBrainz database for automatic track data and it has a really nice orange icon in the Ubuntu menu :D

---

### Post by Orange Kingdom on 2010-05-09
If you want an EXACT copy there is: [http://www.exactaudiocopy.de/](http://www.exactaudiocopy.de/)
Runs with Wine.

---

### Post by Yellow Pasque on 2010-05-09
> **Orange Kingdom said:**
> If you want an EXACT copy there is: [http://www.exactaudiocopy.de/](http://www.exactaudiocopy.de/)
Runs with Wine.
FLAC makes an exact copy, so there's no need for Windows software.

---

### Post by dumdidum on 2010-05-09
> **Temüjin said:**
> FLAC makes an exact copy, so there's no need for Windows software.

I think OP is asking about rippers, not encoders.

I recommend cdparanoia. Similar to Exact Audio Copy, it tries to make perfect rips (even if the CD is scratched etc.)

---

### Post by beanstalker on 2010-05-09
I'd add another plug for EAC. It is generally regarded as the best ripper available and it does run fine under wine. And if you want the highest quality available then go with uncompressed wav files. Flac is great too and does reduce the file size but some audiophiles seem to think that it produces a slightly flat soundstage. Personally I would say that the difference is inaudible even on extremely high-end HiFi installations. However I do still use wav as I'm not worried about file size and so I don't see any point in compressing the files. Other rippers such as cdparanoia are very good, but not as feature rich as EAC, and may is some very unusual circumstances produce bad rips.

Hope this is useful.

MacBookPro 5,3> High resolution Technologies Musicstreamer+ USB DAC> Rega Brio 3 Amp > Image Loudspeakers.

---

### Post by WinterRain on 2010-05-09
If you don't mind using Wine, [CDex]("http://cdexos.sourceforge.net/") is a great open source cd ripper. Been using it for years. Make sure to get the 1.5 version.

---

### Post by Yellow Pasque on 2010-05-09
> **dumdidum said:**
> I think OP is asking about rippers, not encoders.

I recommend cdparanoia. Similar to Exact Audio Copy, it tries to make perfect rips (even if the CD is scratched etc.)
Oh, right. I use the default GNOME audio extractor (sound-juicer), but if you want a nice front-end to cdparanoia, use k3b, You can install it like this without getting half of KDE:
```
sudo apt-get install --no-install-recommends k3b
```

---

### Post by jcottier on 2010-06-23
KDE4 has a new application called Audex (its in the 10.04 repo) which is the best ripper I have seen. It does not suffer from the bugs in Audio CD Extractor (Sound Juicer) and K3b where it wont go over 128Kbs (a gstreamer bug apparently), and it correctly handles track numbers order. It also gets the cover art automatically. Very neat, and supports flac and mp3 up to 320Kbs. Its a worthy replacement to KAudioCD creator which used to be my favourite.

---

### Post by kaligus on 2010-07-23
Audex is awesome as long as you are ripping to OGG

It crashes every time I try to add new profiles such as lame/mp3.

It often crashes if I try to use anything other than the default ogg extreme quality.

Kubuntu 10.04 is the OS with 6GB RAM (4GB of which is free)

---

### Post by shantiq on 2010-07-23
RIP FROM WODIM
===================


       To copy an audio CD in the most accurate way (rip copy from disc to disc), first run

```
           icedax dev=/dev/cdrom -vall cddb=0 -B -Owav

```
       and then to write run

```
           wodim dev=/dev/cdrw -v -dao -useinfo -text  *.wav
```


or

[  ===>  **Rubyripper** ]("http://ubuntuforums.org/showthread.php?t=799621&highlight=ruby+ripper")                  command and gui for a secure rip (as in EAC)

you can have [most of the lossless formats]("http://ubuntuforums.org/showthread.php?t=1533534&page=2") with rubyripper

Command-line   also **pacpl** is very good and in your synaptic    **ripit** is ok too also in your synaptic

---

### Post by cascade9 on 2010-07-23
+1 to rubyripper (linux) and EAC (windows/WINE). They wont create any higher quailty rips than other rippers, but the 2-stage ripping process that you can use in both of them does reduce the chance of any bad sectors/glitches/etc.. 

AFAIK, wodim only does single-pass rips.

---

### Post by shantiq on 2010-07-23
> **cascade9 said:**
> 

AFAIK, wodim only does single-pass rips.

absolutely right

but i put it there as it is fast and SILENT you cannot even hear any whirring as it is done    gentle on the hardware


always impressed me;):D:o


ps as regard the 2 pass programs i use them EAC and rubyripper

they make sure you have a copy that is as close to the original as possible although one could argue that it is a smidgeon retentive to insist on that to such a level but in the file-exchange community it is not seen as odd    personally a really good copy is fine but one can get overenthusiastic:KS:KS:KS:KS   anyway those are the best programs I know of

but if one wants accurate they are the state of the art i am told by people who understand those things

---

### Post by krapp on 2010-08-22
I'm a fan of Rubyripper howsoever slow it may be. The two trial ripping and subsequent analysis for mismatching chunks is a great idea. Loads quickly and the GUI is straightforward and simple enough to be pleasant unlike some of the abominations I've seen on Windows.  See posts 151 and 152 of **[http://ubuntuforums.org/showthread.php?t=799621&page=16](http://ubuntuforums.org/showthread.php?t=799621&page=16)** for installation instructions on 10.04.

---

