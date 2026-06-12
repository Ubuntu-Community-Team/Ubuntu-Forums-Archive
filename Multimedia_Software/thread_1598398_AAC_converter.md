---
title: "AAC converter"
date: 2010-10-16
forum: Multimedia Software
---

### Post by quisnox on 2010-10-16
I'm looking for good AAC converter with comfortable GUI to convert some of my FLAC music collection files to use in Nokia mobile phone.

I've heard about 'magic' Nero AAC codec...maybe it's possible to use it in Linux with GUI?

WinFF, Arista - checked already and they haven't any options for AAC. Gnome Soundconverter don't have any options for HE-AAC (aka (e)AAC+ & etc)

Previously used Winamp with built-in AAC+ converter...but it was in Windows

---

### Post by quisnox on 2010-10-17
bump!

---

### Post by lazyworkhorse on 2010-10-17
[http://ubuntuforums.org/showpost.php?p=4380982&postcount=17](http://ubuntuforums.org/showpost.php?p=4380982&postcount=17)

---

### Post by ztomic on 2010-10-17
[http://ubuntuforums.org/showthread.php?t=1150510&highlight=convert+aac](http://ubuntuforums.org/showthread.php?t=1150510&highlight=convert+aac)

You need nautilus-script-manager installed before doing this.

---

### Post by andrew.46 on 2010-10-20
Hi quisnox,

> **quisnox said:**
> I've heard about 'magic' Nero AAC codec...maybe it's possible to use it in Linux with GUI?

As far as I know NeroAacEnc does not have a gui but the commandline is pretty straightforward. Are you aware that the input file needs to be wav?

> WinFF, Arista - checked already and they haven't any options for AAC.

WinFF will do it for you but you will need to get a copy of FFmpeg equipped for aac encoding, this has been stripped by the Ubuntu developers. Perhaps the easiest way is to enable the Medibuntu repository:

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

```

and then add the extra libavcodec library + FFmpeg:

```

sudo apt-get install ffmpeg libavcodec-extra-52

```

Then if you like you can import the WinFF preset that I have attached to this post and you should be right :).

Andrew

---

### Post by shantiq on 2010-10-20
> **quisnox said:**
> I'm looking for good AAC converter with comfortable GUI to convert some of my FLAC music collection files to use in Nokia mobile phone.

I've heard about 'magic' Nero AAC codec...maybe it's possible to use it in Linux with GUI?

WinFF, Arista - checked already and they haven't any options for AAC. Gnome Soundconverter don't have any options for HE-AAC (aka (e)AAC+ & etc)

Previously used Winamp with built-in AAC+ converter...but it was in Windows

[B]quick answer
========
[/B] 
easiest tool for this task is **soundconverter** in your synaptic

install it/go applications/sound and video


when on your desktop click on edit/preferences set to aac


easy to use and fast

=======================================




**long answer (with nero)**
========================================
you mention nero   it is there for linux too but not with gui thaT i know of

if you want to try it you will have to already have your flacs decompressed to wav not hard to do cd to your folder

```
  flac -d *

```

[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]Download the package NeroAACCodec-1.5.1.zip from here:-[http://www.nero.com/eng/downloads-ne...-aac-codec.php]("http://www.nero.com/eng/downloads-nerodigital-nero-aac-codec.php")


Unzip it and look in the linux folder inside the NeroAACCodec-1.5.1 folder.  unzip the linux folder into your home folder

3 files    neroAacDec, neroAacEnc and neroAacTag.

Install at least  [/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=Verdana]neroAacEnc and neroAacTag for your needs here[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]
Make them executable and put  in /usr/bin folder.

[/FONT][/FONT][/COLOR]```
[COLOR=#000000]sudo mv neroAacEnc /usr/bin  [/COLOR]
```[COLOR=#000000]

then [/COLOR]```
cd  /usr/bin
```[COLOR=#000000]
and  [/COLOR]```
sudo chmod +x neroAacEnc
```[COLOR=#000000] 


do same 3 steps again with neroAacTag for tagging


[/COLOR][COLOR=#000000]

[/COLOR]```
[COLOR=#000000]sudo mv neroAacTag /usr/bin [/COLOR]
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana] 
[/FONT][/FONT][/COLOR][COLOR=#000000]then [/COLOR]```
cd  /usr/bin
```[COLOR=#000000]
and  [/COLOR]```
sudo chmod +x neroAacTag
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]


Then test it using [/FONT][/FONT][/COLOR][COLOR=#000000]**neroAacEnc -help**[/COLOR]
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana][B]neroAacTag -help   and find OUT ALL THE OPTIONS

[/B]IF YOU want a 320kbps  with 2 passes for more reliable encoding use

[/FONT][/FONT][/COLOR]```
neroAacEnc -2pass -br 320000 -if nameoffile.wav -of nameoffile.aac
```
if you want the absolute highest kbps available code in


```
neroAacEnc -q 1 -if nameoffile.wav -of nameoffile.aac
```
**THIS is a little more involved but fun:)**




[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]

[/FONT][/FONT][/COLOR]

---

