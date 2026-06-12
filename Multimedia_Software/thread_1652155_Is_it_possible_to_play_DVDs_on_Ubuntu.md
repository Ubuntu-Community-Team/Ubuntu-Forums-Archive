---
title: "Is it possible to play DVDs on Ubuntu?"
date: 2010-12-24
forum: Multimedia Software
---

### Post by nrundy on 2010-12-24
I can't get any DVDs to play. I've tried MPlayer, VLC, Totem, KMPlayer.   The player puts out an error dialogue box or just tries to play the DVD forever. It's a "hollywood" DVD purchased from Best Buy.  I booted into Windows and played the DVD fine with Windows Media Player. No issues whatsoever. What the heck is wrong with Ubuntu?

---

### Post by mlentink on 2010-12-24
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ajgreeny on 2010-12-24
> **nrundy said:**
> I can't get any DVDs to play. I've tried MPlayer, VLC, Totem, KMPlayer.   The player puts out an error dialogue box or just tries to play the DVD forever. It's a "hollywood" DVD purchased from Best Buy.  I booted into Windows and played the DVD fine with Windows Media Player. No issues whatsoever. What the heck is wrong with Ubuntu?
Absolutely nothing is wrong with Ubuntu.  This is a problem related to the silly rules and regulations over software patents, and as such, to avoid possible legal problems, Ubuntu is not shipped with the codecs and decryption software needed to play commercial DVDs.

Follow mlentinks link and you will find all you need.  I use the [Medibuntu]("http://www.medibuntu.org/")  repositories, which also provide a number of other updated multimedia packages as well as the required libdvdcss2 for DVD playback.

---

### Post by io5cml4z on 2010-12-24
Try this:
> sudo /usr/share/doc/libdvdread3/install-css.sh
If that returns some sort of "not found" error try:
> sudo /usr/share/doc/libdvdread4/install-css.sh
:popcorn:

---

### Post by dnairb on 2010-12-24
IIRC you can run the following as a single command in terminal to add the Medibuntu repository, update the packages list and install libdvdcss2:


```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update && sudo apt-get install libdvdcss2
```

---

### Post by ricardisimo on 2010-12-30
I've got all of the codecs, backends and front ends installed. VLC plays ISO images just fine. It's just Totem that won't. It doesn't return an error, mind you... just black screen. Any ideas?

---

### Post by perspectoff on 2010-12-30
Commercial DVDs require libdvdcss from Medibuntu.

See Ubuntuguide.org for easy installation instructions:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Maverick#DVD_Playback_Capability)

or Kubuntuguide.org:

[http://kubuntuguide.org/Maverick#DVD_Playback_Capability](http://kubuntuguide.org/Maverick#DVD_Playback_Capability)

In brief, in a command-line terminal (Terminal or Konsole):

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb

---

### Post by ricardisimo on 2010-12-31
Like I said, I've got all of that installed. I wouldn't be able to play commercial DVDs with ***any*** program if I didn't have libdvdcss2 installed. The problem is playing them with Totem.

I can get around this by just playing everything in VLC, but...
[LIST=1]
[*]the default Ubuntu programs should work, in my opinion;
[*]I like having at least two working options for any given file or medium.
[/LIST]
So, once again, any ideas?

---

### Post by cchhrriiss121212 on 2010-12-31
> **ricardisimo said:**
> 
[LIST=1]
[*]the default Ubuntu programs should work, in my opinion;
[*]I like having at least two working options for any given file or medium.
[/LIST]
So, once again, any ideas?
1. Try opening totem from a terminal, that should provide sufficient error messages
2. Xine, Smplayer etc. there are plenty of other video players out there

---

### Post by io5cml4z on 2010-12-31
Try turning de-interlacing off. Although I didn't have your problem (for me the screen was just shaking), this solved it.

Edit > Preferences > Display > Toggle - "Disable deinterlacing of interlaced videos"
It's worth a try. Otherwise just use vlc, or mplayer.

---

