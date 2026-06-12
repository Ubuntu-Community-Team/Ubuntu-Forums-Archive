---
title: "Problem with Codecs"
date: 2010-03-29
forum: Multimedia Software
---

### Post by Disco Soup on 2010-03-29
So I'm having trouble finding and installing DivX codecs. I have audio on my vids but no video.

---

### Post by derekeverett on 2010-03-29
I'm no expert here but did you install the ubuntu-restricted-extras package?

---

### Post by Disco Soup on 2010-03-29
I believe so. First thing.

---

### Post by mick222 on 2010-03-29
Make sure multiverse is enabled in your software sources also install ffmpeg from mediabuntu repos toenable them copy command  into terminal.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update                                              
```
Vlc installs a lot of codecs so it is worth installing as well.

---

### Post by derekeverett on 2010-03-29
I found this thread

[http://ubuntuforums.org/showthread.php?t=1440210&highlight=divx](http://ubuntuforums.org/showthread.php?t=1440210&highlight=divx)

It basically points to ubuntu-restricted-extras and VLC, which would have been my answer.

Hope that helps..

---

### Post by Disco Soup on 2010-03-29
Still wonky. Hmm.

---

### Post by Disco Soup on 2010-03-29
Could the problem be that I am using a tv instead of a regular computer monitor? The TV has an option for PC input. I can watch flash videos and sites like Youtube and Hulu work fine.

---

### Post by andrew.46 on 2010-03-29
Hi Disco,

> **Disco Soup said:**
> I have audio on my vids but no video.

If you are using Karmic Koala perhaps you could install the program mediainfo? The following is a single command:

```

sudo add-apt-repository ppa:shiki/mediainfo && \
sudo apt-get update && \
sudo apt-get install mediainfo mediainfo-gui

```

and then interrogate the problem file in the following manner:

```
mediainfo -f **[COLOR="Red"]my_file[/COLOR]**
```

and of course substituting *my_file* with the actual name of your file. This should fully identify the problem file. Are you running 32 bit or 64 bit Ubuntu?

All the best,

Andrew

---

### Post by Nisal on 2010-03-29
USE VLC other than 3gp all formats working fine in VLC

---

### Post by andrew.46 on 2010-03-29
Hi Nisal,

> **Nisal said:**
> USE VLC other than 3gp all formats working fine in VLC

To tell the truth if vlc has been compiled against a libavcodec with amr support it will play 3gp files as well... Unfortunately this is not the case with the Ubuntu version.

Andrew

---

### Post by Disco Soup on 2010-03-29
I'm using Hardy Heron.

---

### Post by andrew.46 on 2010-03-29
Hi Disco,

> **Disco Soup said:**
> I'm using Hardy Heron.

Instructions for *manually* adding the PPA for Hardy can be seen here:

Official PPA for MediaInfo 
[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)

All the best,

Andrew

---

### Post by Disco Soup on 2010-03-30
Hmm, maybe I'll just install Winamp with Wine.

---

### Post by yetiman64 on 2010-03-30
> **Disco Soup said:**
> Hmm, maybe I'll just install Winamp with Wine.

I've got Winamp running under Wine and have never had any luck with video, but great on sound and 1 visualization (Milkdrop).

---

### Post by andrew.46 on 2010-03-30
Hi Disco,

> **Disco Soup said:**
> Hmm, maybe I'll just install Winamp with Wine.

Can you perhaps post a link to one of the videos that are giving you trouble?

Andrew

---

### Post by Disco Soup on 2010-03-30
It's every video on my hard drive (currently 1, The End of Time Part 2) and anytime I click to open video files with Firefox. That said, youtube and hulu work perfectly.

---

