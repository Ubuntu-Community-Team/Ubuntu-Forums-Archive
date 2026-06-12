---
title: "WITHOUT A SONG second tryee"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by jackmccaskill on 2007-12-27
Greetings,

     I probably have no business in this forum!  I have tried "absolute beginners talk", meaning I do not know by elbow from my backside.  All replys have been cryptic at best, many of them being one word answers with no explanations or asking about file types I know nothing about.  Please help.

      I have installed xubuntu 6.06.  I have copied my music which is all in files with the extention 
'WMA".  I have installed fxmedia and rhythmbox Music player as well as XMMS Music player usuing the synaptic package manager to install

     None of those programs will play my *.wma files!

     Are there any programs [packages] that will?  If so how do I obatain them AND how do I Iinstall them?  If not please also let me know.

---

### Post by Yellow Pasque on 2007-12-27
What happens when you run:
```
sudo apt-get install xmms-wma
```
Does magic happen when you try to play your wma files in xmms now?

---

### Post by Yellow Pasque on 2007-12-28
For rhythmbox, make sure you have gstreamer0.10-ffmpeg, i.e.
```
sudo apt-get install gstreamer0.10-ffmpeg
```
and to make sure you have all the plugins you need for other formats:
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by jackmccaskill on 2007-12-30
Would someone, please, tell me, in**_ plain English_**, will or will not  ubuntu  play music files with the extention .WMA!

If not, is there a conversion program to convert my music files to a format that ubuntu **wil**l play?

I have read both "ubuntu for dummies" and Linus Bible and can find no reference to this problem.

To date, the replies to this and my my post [same name] to "absolute beginers talk have only helped to compound my frustration

---

### Post by Yellow Pasque on 2007-12-30
> Would someone, please, tell me, in plain English, will or will not ubuntu play music files with the extention .WMA!

It's dependent on what application you're using. Clear as mud? Good.

---

### Post by Steveway on 2007-12-30
Ubuntu can play these files. But!
But WMA files often come encrypted with DRM (Look up Wikipedia for more information on it).
DRM-infected files can't be played on Linux.
You'll have to somehow convert them on Windows to another filetype like mp3 or Ogg-theora.
Then you'll be able to play your music on Linux.
Where did you get tha music from?

---

### Post by Yellow Pasque on 2007-12-30
> You'll have to somehow convert them on Windows to another filetype like mp3 or Ogg-theora.
Sound quality takes a hit when you do this and I would recommend re-ripping the sources to ogg (preferably FLAC if you have space for it).

---

### Post by Zimmer on 2007-12-30
> **jackmccaskill said:**
> Would someone, please, tell me, in**_ plain English_**, will or will not  ubuntu  play music files with the extention .WMA!

If not, is there a conversion program to convert my music files to a format that ubuntu **wil**l play?

I have read both "ubuntu for dummies" and Linus Bible and can find no reference to this problem.

To date, the replies to this and my my post [same name] to "absolute beginers talk have only helped to compound my frustration

Mplayer or Movie player plays them on my Ubuntu setup....

Does that help?

I will run away now and find out WHY it plays them as I installed all sorts 12 months ago to get things to work.. :)

OK, find #1  nautilus-script-audio-convert   is in the Synaptic package manager and it reckons that can convert WMA files
find #2  w32codecs   also in Synaptic, this enables many of the Windows format stuff to be played etc.

If you cannot find them in your Synaptic Package manager then you will have to update your sources list to include the source for these ...

#3  MPlayer  [https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

It is in the Multiverse repository  and supports WMA  , so it would seem that #3 would be the best place to start..enable the Multiverse repository and  install Mplayer..

---

### Post by lemurian on 2008-01-04
> **Zimmer said:**
> Mplayer or Movie player plays them on my Ubuntu setup....

Does that help?

I will run away now and find out WHY it plays them as I installed all sorts 12 months ago to get things to work.. :)

OK, find #1  nautilus-script-audio-convert   is in the Synaptic package manager and it reckons that can convert WMA files
find #2  w32codecs   also in Synaptic, this enables many of the Windows format stuff to be played etc.

If you cannot find them in your Synaptic Package manager then you will have to update your sources list to include the source for these ...

#3  MPlayer  [https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

It is in the Multiverse repository  and supports WMA  , so it would seem that #3 would be the best place to start..enable the Multiverse repository and  install Mplayer..
As steveway noted, the fact is that there are multiple kinds of WMA files.  Some of them have no DRM.  They are playable everywhere.  Some of them are infected with DRM.  They can be played only on some devices.

Of the 3 proposals, I have #2 and #3 installed on my machine.  If Rhythmbox refuses to play a WMA file wihle reporting "This file is encrypted and cannot be played", then the w32codecs don't help at all and mplayer also cannot play the file.  I have not looked into #1 because converting the file is not an acceptable solution to me.  (And I think it would not work anyway because of the fscking DRM.)

If anyone knows of a solution to deal with DRM-infected files, please post it.

---

### Post by Steveway on 2008-01-04
> **lemurian said:**
> As steveway noted, the fact is that there are multiple kinds of WMA files.  Some of them have no DRM.  They are playable everywhere.  Some of them are infected with DRM.  They can be played only on some devices.

Of the 3 proposals, I have #2 and #3 installed on my machine.  If Rhythmbox refuses to play a WMA file wihle reporting "This file is encrypted and cannot be played", then the w32codecs don't help at all and mplayer also cannot play the file.  I have not looked into #1 because converting the file is not an acceptable solution to me.  (And I think it would not work anyway because of the fscking DRM.)

If anyone knows of a solution to deal with DRM-infected files, please post it.

Delete them.

And if your not concerned of the legal risks then download the infected titles in another format through a p2p app. The legal status of this depends on your countrys laws.

---

