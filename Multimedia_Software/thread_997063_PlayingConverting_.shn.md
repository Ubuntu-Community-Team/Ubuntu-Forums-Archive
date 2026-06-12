---
title: "Playing/Converting .shn?"
date: 2008-11-29
forum: Multimedia Software
---

### Post by think13 on 2008-11-29
I have found a concert recording encoded in shorten (.shn).

I have problems playing these files; every media player I try has a fatal error after a little over a minute in playback.  I want to convert these to FLAC.

shntool gives me this error when I try to convert:
```
david@david-laptop:~/Desktop$ ls
mermen98-03-20d1t02.shn
david@david-laptop:~/Desktop$ sudo shntool conv -o flac *.shn
[sudo] password for david: 
shntool [conv]: warning: failed to read data from input file using format: [shn]
shntool [conv]:          + you may not have permission to read file: [mermen98-03-20d1t02.shn]
shntool [conv]:          + arguments may be incorrect for decoder: [shorten]
shntool [conv]:          + verify that the decoder is installed and in your PATH
shntool [conv]:          + this file may be unsupported, truncated or corrupt
```

Sound converter does create files, but they are only about a minute and a half in length - I believe they should be longer, but I'm not sure.

Any hints?

---

### Post by cozmicharlie on 2008-12-01
You can play shn using xmms.  Unfortunatley, it is no longer in the repos but thier are a number of good How To,s on the forums.  Follow these instructions to get xmms to play shn.  This will also give you shn support for converters.  If you scroll to the end of the post you will see the method for installing the shn codec.  You don't need xmms if all you need to do is convert.
[http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)
(Also, you may want to look for a deb package for isntalling xmms - do a search in the forum).

This tutorial will also help for installing the shn codec (it is the same as in the above post so if you follow the instructions for xmms you don't need to do this).  It says for Hardy but it works for Intrepid.  Note though that shn will not play in Rythmbox.  
[http://ubuntuforums.org/showthread.php?t=739658](http://ubuntuforums.org/showthread.php?t=739658)

If you simply want to convert then you have a few options. PACPL is good but it is command line.  SoundKonverter (yes with a k and it is a kde package but it works fine in gnome) both work.
To install Pacpl go here: [http://ubuntuforums.org/showthread.php?t=712064&highlight=shn](http://ubuntuforums.org/showthread.php?t=712064&highlight=shn)

SoundKonverter - simply install from Synaptic.

Also, the new ffmpeg from the Medibuntu repository does support shn so a very simple method is install ffmpeg from the medibuntu repository.  The only problem is though that the only player I found to work with this method is Totem Movie Player.  

This is another method but a bit more complicated.  I have not tried it but a number of people have posted that it works.
[http://ubuntuforums.org/showthread.php?t=925167&highlight=shn](http://ubuntuforums.org/showthread.php?t=925167&highlight=shn)

Post back if you need any help with installation

---

### Post by cozmicharlie on 2008-12-01
A link to xmms packages for Ubuntu
[http://ubuntuforums.org/showthread.php?t=999426](http://ubuntuforums.org/showthread.php?t=999426)

---

### Post by FakeOutdoorsman on 2008-12-02
You could try ffmpeg:
```
ffmpeg -i input.shn output.flac
```
However, when I tried this I got many "Multiple frames in a packet from stream 0" error, but the resulting file seemed fine.  It was a quick test and there may have been problems, but I didn't hear any.

---

### Post by cozmicharlie on 2008-12-02
> **FakeOutdoorsman said:**
> You could try ffmpeg:
```
ffmpeg -i input.shn output.flac
```
However, when I tried this I got many "Multiple frames in a packet from stream 0" error, but the resulting file seemed fine.  It was a quick test and there may have been problems, but I didn't hear any.

Yes, the newer ffmpeg is supposed to have shn support so it should work.  Did you use the ffmpeg from the medibuntu repository?  

In theory, players that use ffmpeg should all play shn but for some reason they don't.  The only one I found to play shn is Totem Movie Player.  Rythmbox supposedly uses ffmpeg but for some reason it will not play shn in Hardy or Intrepid though it did in Feisty.

---

### Post by FakeOutdoorsman on 2008-12-02
> **cozmicharlie said:**
> Yes, the newer ffmpeg is supposed to have shn support so it should work.  Did you use the ffmpeg from the medibuntu repository?  

In theory, players that use ffmpeg should all play shn but for some reason they don't.  The only one I found to play shn is Totem Movie Player.  Rythmbox supposedly uses ffmpeg but for some reason it will not play shn in Hardy or Intrepid though it did in Feisty.
I used ffmpeg from the Ubuntu repository on Intrepid.  There is no Medibuntu ffmpeg for Intrepid.  I did another test and this time no errors showed up.  I also was able to play the shn file with ffplay, which is part of the ffmpeg package.  ffplay uses the ffmpeg libraries and the SDL library.  I don't see any references to anything ffmpeg in the dependencies of Rhythmbox.  I get the following error if I try to play the shn with Rhythmbox:
```
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|Shorten Lossless decoder|decoder-audio/x-shorten
```
Does Rhythmbox play shn if gstreamer0.10-plugins-bad and/or gstreamer0.10-plugins-ugly are installed?  I'd test it, but I'm short on bandwidth.

---

### Post by cozmicharlie on 2008-12-02
No, I can't get Rythmbox to play shn with gstreamer or with the shn codecs installed.  It would up until Gutsy.    

I use xmms for playing shn.  Nice to know that ffplay is another option.  Ideally, any player that uses ffmpeg should play shn but Rythmbox doesn't in my system.

---

### Post by FakeOutdoorsman on 2008-12-02
> **cozmicharlie said:**
> 
...
It would up until Gutsy.
Might be some relevant bug reports:
[LIST]
[*][Bug #219627 in gst-plugins-good0.10 (Ubuntu): “shn files fail to play correctly in rhythmbox after upgrading to Hardy 8.04 rc”]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good0.10/+bug/219627")
[*][Bug #254747 in gstreamer0.10-ffmpeg (Ubuntu): “Rhythmbox crashes when playing shn files]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/254747")
[/LIST]

---

### Post by cozmicharlie on 2008-12-03
yep - looks like it.

---

### Post by shantiq on 2010-11-01
Two years on you have many more choices :KS


[SIZE="3"]to play
=======
[/SIZE]

1.  THE LATEST VERSION of qmmp 0.4.2  (standard issue in maverick) plays shorten now 



2. as does this git version of [**deadbeef**]("http://ubuntuforums.org/showpost.php?p=9731471&postcount=21")


3.   xmm2 will also play it with

xmms2-plugin-avcodec

through a gui like promoe or esperanza all of those in synaptic or do

```
sudo apt-get install xmms2 xmms2-plugin-avcodec promoe esperanza
```


many more gui [**here**]("http://xmms2.org/wiki/Clients")


4. and of course mplayer and smplayer also play shorten


5. and the trusted old[ xmms]("http://ubuntuforums.org/showthread.php?t=1525072") still goes on maverick and will play shorten too





[SIZE="3"]to convert
==========[/SIZE]


to flac```
shnconv -o nameoffile.flac  nameoffile.shn
```

from flac```
shnconv -o nameoffile.shn  nameoffile.flac

```

replace flac with the codec of your choice

run   ```
shntool -f 
```   to see which ones are available




[SIZE="3"]to batch-convert
================[/SIZE]

wav to shorten




```
for f in *.wav; do shorten "$f" "${f%.wav}.shn"; done

```

shorten to wav


```
for f in *.shn; do ffmpeg -i "$f" "${f%.shn}.wav"; done

```


to flac

```
for f in *.shn; do ffmpeg -i "$f" "${f%.shn}.flac"; done

```

from flac


```
shnconv -o shn *flac

```
more options [**here** ]("http://ubuntuforums.org/showthread.php?t=1609760") 




you can take the shntool or the script route for either

---

