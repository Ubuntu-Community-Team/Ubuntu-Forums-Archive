---
title: "help w/ codecs please!"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by texastoned@gmail.com on 2007-05-13
[SIZE="3"]I have a ton of media from my pc backed up on an external harddrive.  the hard drive is NTSF which i understand is a pain, but most of the media is .mp3 or .wma(&i'm not happy i ripped into that format).  When I try to access the media both in RythmBox or in XMMS it tells me that the filetype is not an audio stream or somesuch.  In my reading i've gathered i need codecs; most specifically gstreamer.10-ffmpeg, gstreamer.10-plugins, & gstreamer.10-plugins-multiverse but my Synaptic Package Manager dosent find anything like that,  Any tips?  I just took the leap to Ubuntu from PC after a wicked crash a week ago and I've only had Ubuntu runnin well for two days so forgive my ignorance.  thanks![/SIZE]

---

### Post by texastoned@gmail.com on 2007-05-13
never mind, i figured it out...for the moment...im confident y'all be hearing from me quite a bit in the future. thanks guys!

---

### Post by floke on 2007-05-15
Why don't you post how you figured it out in case it helps others with a similar problem?
Oh, and welcome to Ubuntu :)

---

### Post by The Afterdark on 2007-06-16
> **Steve.K said:**
> Why don't you post how you figured it out in case it helps others with a similar problem?
Oh, and welcome to Ubuntu :)

Yah... ditto.  Cause I just got Ubuntu myself and don't know how to get the codecs. :(
Help anyone?

---

### Post by Gremlinzzz on 2007-06-16
these work for me wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb  just pasted in terminil

---

### Post by The Afterdark on 2007-06-16
> **Gremlinzzz said:**
> these work for me wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb  just pasted in terminil

wget -c [http://www.debian-multimedia.org/poo...2-0.0_i386.deb](http://www.debian-multimedia.org/poo...2-0.0_i386.deb)
gave me the following:

> 
$ wget -c [http://www.debian-multimedia.org/poo...2-0.0_i386.deb](http://www.debian-multimedia.org/poo...2-0.0_i386.deb)
--15:36:59--  [http://www.debian-multimedia.org/poo...2-0.0_i386.deb](http://www.debian-multimedia.org/poo...2-0.0_i386.deb)
           => `poo...2-0.0_i386.deb'
Resolving [www.debian-multimedia.org](www.debian-multimedia.org)... 213.186.33.17
Connecting to www.debian-multimedia.org|213.186.33.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...2-0.0_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...2-0.0_i386.deb) [following]
--15:37:00--  [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...2-0.0_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...2-0.0_i386.deb)
           => `poo...2-0.0_i386.deb'
Resolving ftp.sunet.se... 194.71.11.69, 2001:6b0:19::64
Connecting to ftp.sunet.se|194.71.11.69|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:37:00 ERROR 404: Not Found.


I'm using Ubuntu 6.06 LTS.  Do I have to have 7.04 to get this working?

---

### Post by wolfen69 on 2007-06-16
type in terminal:

sudo su -c 'echo deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free >> /etc/apt/sources.list'
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

every codec or what not should be available through synaptic now. or just click on media file and it will ask you if you would like to download the proper codecs.

---

### Post by Gremlinzzz on 2007-06-16
OK this is the site i go too youll see the commands just paste [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by merlockmagus on 2007-06-17
Everytime I use wget to download the key, I get the following message:
gpg: no valid OpenPGP data found.


Any idea why that is? Is the site down or something?

---

