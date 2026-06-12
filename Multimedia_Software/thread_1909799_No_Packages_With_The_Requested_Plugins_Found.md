---
title: "No Packages With The Requested Plugins Found"
date: 2012-01-16
forum: Multimedia Software
---

### Post by davethewave83 on 2012-01-16
How do I fix this?

I am using "SoundConverter" to convert music to Ogg, some of my music is mp4
I think that's what it's hanging on. 

The mp3 convert with no problems.

I installed FFmpeg as it says here 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

but it did not help

I have all sources checked, as well as canonical partner in the other tab.

---

### Post by carl4926 on 2012-01-16
Do you have the the Good, the Bad and the Ugly range in Gstreamer?

---

### Post by davethewave83 on 2012-01-16
> **carl4926 said:**
> Do you have the the Good, the Bad and the Ugly range in Gstreamer?

I have main, universe, restricted and multiverse checked, as well as canonical.

---

### Post by davethewave83 on 2012-01-16
no i am on Lucid Lynx, 10.04. I have gstreamer nice, good, bad and ugly.

---

### Post by bluexrider on 2012-01-16
[B]For 11.10

Medibuntu[/B] repository provides all the playback and  encoding capabilities that most Windows and Mac systems contain, but  which Ubuntu&#8217;s creators decline to include by default in their systems,  due to licensing restrictions and a lack of open-source code for those  features. If you just want to get AAC playback, copyright DVDs playing,  and newer versions of all the audio, video, and font files, load  Medibuntu into your system. (Required)
 Open your Terminal, copy and paste:

 ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update sudo apt-get -y update && sudo apt-get -y upgrade sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
``` If you are running a 32-bit version of Ubuntu, copy and paste in Terminal:
 ```
sudo apt-get install w32codecs libdvdcss2
``` If you are running a 64-bit version of Ubuntu, copy and paste in Terminal:
 ```
sudo apt-get install w64codecs libdvdcss2
```
REF: [HERE]("http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")

---

### Post by davethewave83 on 2012-01-16
> **bluexrider said:**
> [B]For 11.10

Medibuntu[/B] repository provides all the playback and  encoding capabilities that most Windows and Mac systems contain, but  which Ubuntu’s creators decline to include by default in their systems,  due to licensing restrictions and a lack of open-source code for those  features. If you just want to get AAC playback, copyright DVDs playing,  and newer versions of all the audio, video, and font files, load  Medibuntu into your system. (Required)
 Open your Terminal, copy and paste:

 ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update sudo apt-get -y update && sudo apt-get -y upgrade sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
``` If you are running a 32-bit version of Ubuntu, copy and paste in Terminal:
 ```
sudo apt-get install w32codecs libdvdcss2
``` If you are running a 64-bit version of Ubuntu, copy and paste in Terminal:
 ```
sudo apt-get install w64codecs libdvdcss2
```
REF: [HERE]("http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")

thanks that fixed it. 

that's the reason I am converting to Ogg though, it's so I don't have to download all this, kind of a paradox I guess. Have to download it, in order to avoid downloading it ;)

are there any open source video codecs, for the mp4 files? Some are music videos, I'd like to keep video if possible. I'll check around while waiting for a reply. Thanks again

---

### Post by bluexrider on 2012-01-16
well, your profile said 11.10....

This option is available for **Ubuntu Lucid Lynx 10.04**, **Ubuntu Karmic Koala 9.10** and **Ubuntu Hardy Heron 8.04**.  [Medibuntu]("http://medibuntu.org/")  is a third-party repository that contains packages that are unable to   be included in the official Ubuntu repositories.  To install FFmpeg from   Medibuntu open Terminal (Applications -> Accessories ->  Terminal)  and run the following:  Code:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update 

```**Ubuntu Lucid Lynx 10.04 & Ubuntu Karmic Koala 9.10**
  Code:
```
sudo apt-get install ffmpeg libavcodec-extra-52 

```REF: [HERE]("http://www.doyourself.org/ffmpeg/587-howto-easily-enable-mp3-mpeg4-aac-and-other-restricted-encoders-in-ffmpeg/")

---

### Post by davethewave83 on 2012-01-16
> **bluexrider said:**
> well, your profile said 11.10....

This option is available for **Ubuntu Lucid Lynx 10.04**, **Ubuntu Karmic Koala 9.10** and **Ubuntu Hardy Heron 8.04**.  [Medibuntu]("http://medibuntu.org/")  is a third-party repository that contains packages that are unable to   be included in the official Ubuntu repositories.  To install FFmpeg from   Medibuntu open Terminal (Applications -> Accessories ->  Terminal)  and run the following:  Code:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update 

```**Ubuntu Lucid Lynx 10.04 & Ubuntu Karmic Koala 9.10**
  Code:
```
sudo apt-get install ffmpeg libavcodec-extra-52 

```REF: [HERE]("http://www.doyourself.org/ffmpeg/587-howto-easily-enable-mp3-mpeg4-aac-and-other-restricted-encoders-in-ffmpeg/")

The instructions you posted for 11.10 worked on my 10.04 

I use both versions, I really like 10.04, I can't stand the new gnome3 or Unity, I think they're ruining things but, many people like it so maybe it's just me. So I need something to remember the good times with, so I use 10.04 also. 

Thanks for the support

---

### Post by bluexrider on 2012-01-16
Glad we got you fixed up. Enjoy

---

