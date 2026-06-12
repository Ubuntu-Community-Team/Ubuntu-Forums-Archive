---
title: "Where to find Windows Media Audio 9 decoder?"
date: 2010-04-04
forum: Multimedia Software
---

### Post by Darbre on 2010-04-04
I'm trying to play a wmv file in Karmic's Totem Movie Player. I get an error that "Windows Media Audio 9 decoder" is not installed. I let it search,but get no results. Where can I find this codec?

Thanks

Darbre

---

### Post by yochaigal on 2010-04-24
installing mplayer seems to work.

sudo aptitude install mplayer

---

### Post by Darbre on 2010-04-24
Thanks, but is this right? From the text below, it looks like I'm removing mplayer, not installing anything.

Darbre

======================================================


david@david-laptop:~$ sudo aptitude install mplayer
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  fastjar{u} gcj-4.4-base{u} gcj-4.4-jre-lib{u} libgcj-bc{u} libgcj10{u} 
  libgcj9-0-awt{u} libmikmod2{u} libmx4j-java{u} libqt3-mt{u} 
  libsdl-mixer1.2{u} libsmpeg0{u} linux-headers-2.6.31-14{u} 
  linux-headers-2.6.31-14-generic{u} 
0 packages upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 144MB will be freed.
Do you want to continue? [Y/n/?]


===========================================

---

### Post by andrew.46 on 2010-04-25
You can test your copy of MPlayer for playback of these files like this:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -ac help | grep wma[/COLOR]**

wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]
ffwmav1     ffmpeg    untested  DivX audio v1 (FFmpeg)  [wmav1]
ffwmav2     ffmpeg    untested  DivX audio v2 (FFmpeg)  [wmav2]
ffwmapro    ffmpeg    untested  WMA Pro audio (FFmpeg)  [wmapro]
ffwmavoice  ffmpeg    untested  WMA Voice audio (FFmpeg)  [wmavoice]

```

To complicate things a little wma comes in a few different forms: WMA Pro, WMA Lossless, WMA Voice and the 'original' WMA. The good news is that a well configured MPlayer on a 32bit system can easily play all of these.

Andrew

---

### Post by mick222 on 2010-04-25
you might have to install the medibuntu repositories to get the codecs.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```



[PHP]sudo apt-get install libdvdcss2 && sudo apt-get install w32codecs [/PHP]
That will install the medibuntu repo and the second command will install libdvdcss2 for dvd playback and the wma codecs. To read more about medibuntu see here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Or Vlc plays just about anything.

---

### Post by Darbre on 2010-04-25
Thanks for the help. I'm very familiar with VLC and installed that.

Darbre

---

### Post by andrew.46 on 2010-04-26
Hi Darbre,

> **Darbre said:**
> Thanks for the help. I'm very familiar with VLC and installed that.

This played your wmas? vlc has a bit of a weak spot with different types of wma files and depends heavily on a recent version of libavcodec to play some, the Ubuntu libavcodec has been pruned more than a little...

Andrew

---

### Post by Darbre on 2010-04-26
You're probably right, but I haven't found this weakness yet. I tested my installation of mplayer and even though it said all was well, it still won't play WMA9. VLC so far anyway, is fine. I have no clue what else to do with mplayer.

Darbre

---

### Post by andrew.46 on 2010-04-26
Hi Darbre,

> **Darbre said:**
> You're probably right, but I haven't found this weakness yet. I tested my installation of mplayer and even though it said all was well, it still won't play WMA9.

If you were interested in getting MPlayer running you could try running it from the commandline as follows:

```
mplayer -v my_file.wma
```

where you will need to substitute *my_file.wma* with the name of your own file of course. If you post the terminal output here there should be a few hints as to what is going wrong. Are you running 64 or 32 bit MPlayer?

Andrew

---

### Post by Darbre on 2010-05-03
Thanks, guys. The update to Lucid seems to have fixed my problem.

Darbre

---

### Post by alfh on 2010-05-26
Running 10.04, having similar problem. Some wma files causes Rhytmbox to start auto-search for windows media audio 9 codec (finding no suitable codec, of course).

Installed: ffmpeg, medibuntu repositories, w32codecs, g-streamer0.10-ffmpeg, mplayer

My main problem is getting streaming to work properly. I'd like to be able to scroll in radio programs which are working (like [http://nettradio.nrk.no/default.php?kanal=p2]("http://nettradio.nrk.no/default.php?kanal=p2")) and I want sound from [http://www.polskieradio.pl/sluchaj/play.aspx?p=r3]("http://www.polskieradio.pl/sluchaj/play.aspx?p=r3")

I'm trying to install smplayer to check if this will help, though I doubt it...

---

### Post by alfh on 2010-05-26
...and smplayer claims my mplayer is obsolete...

Synaptic says my version of mplayer is 2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1 which is the same version listed as the newest at [https://launchpad.net/ubuntu/lucid/i386/mplayer-gui]("https://launchpad.net/ubuntu/lucid/i386/mplayer-gui")

So if the newest available version is obsolete, then what next?

Thankful for any input here.

---

### Post by Rumpty on 2010-05-26
Apparently there is a newer version of mplayer available at
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Also smplayer at
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

---

### Post by shantiq on 2010-05-31
> **mick222 said:**
> you might have to install the medibuntu repositories to get the codecs.
[CODE]
Or Vlc plays just about anything.


[B][COLOR="Blue"]not happy with all formats though  

> No suitable decoder module:
VLC does not support the audio or video format "wmal". Unfortunately there is no way for you to fix this.


any idea how to convert those wma1 to say flac or wv?


shntool will not   or soundconverter or soundKonverter
[/COLOR][/B]

---

### Post by anticipator on 2010-06-28
1. Download the latest 'all-codecs-pack' from mplayer hq
[http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/)

2. Extract the files to a directory
tar -xvf all-********.tar.bz2 (replace '*' accordingly from filename :razz: )
This will extract the files into a directory 'all-********/' in the  current location

3. Copy all the extracted files to /usr/local/lib/codecs/ (If there is  no such directory, create it)
cp all-********/* /usr/local/lib/codecs/

4. Make sure the files have the required permissions
chmod 755 /usr/local/lib/codecs/*

5. Some players look in a the directory /usr/lib/win32/ for codecs. So  if you don't have that directory create it and copy the files there as  well.
cp /usr/local/lib/codecs/* /usr/lib/win32/

6. Now your media file should work fine in mplayer or smplayer...  

Good Luck!

---

### Post by Pollewoppetje on 2010-07-29
First of all, hello to everyone, since this is my first post here. 

I've tried everything you guys have posted here, including the codec-copying solution of Anticipator. However, when I play a wmv file of an HD movie, I still get prompted for an additional plugin. I find this weird because playing smaller/shorter WMV videos is no problem anymore.  

Many thanks in advance!

---

### Post by peter_parker on 2010-09-15
> **mick222 said:**
> you might have to install the medibuntu repositories to get the codecs.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```



[PHP]sudo apt-get install libdvdcss2 && sudo apt-get install w32codecs [/PHP]
That will install the medibuntu repo and the second command will install libdvdcss2 for dvd playback and the wma codecs. To read more about medibuntu see here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Or Vlc plays just about anything.

Hi,

This worked great for me.  

But i had one question.  Why does my video Only seem to play with audio when launched from the command line?:

mplayer /home/inawaz/Desktop/<media file>.wmv

If i try to double click or right click open with mplayer, video will play but no audio.  Same no suitable driver issue...

Just curious.

Thanks

---

