---
title: "Totem _never_ works"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by krussell on 2007-03-29
Hello All :-)
I have just installed Ubuntu Edgy, and it is just fantastic!
However, i am having some problems with movie player.
The default movie player is Totem, which never seem to work. I had to go for mplayer instead.
Totem launches whenever a dvd/cd is inserted, but it can never play the thing saying "CDROM not found" or "No codec to handle the format". 
Is it about gstreamer 0.8 ? 
And another thing, can i copy/paste AVSEQ.DAT and *.VOB files from VCD/DVD like in Windows?

Kind regards

---

### Post by kevinlyfellow on 2007-03-29
I've been having severe problems with totem-gstreamer with edgy also, I decided that totem-xine is still a better solution

---

### Post by smartbei on 2007-03-29
use Synaptic to get totem-xine as the above poster suggested. It works.

---

### Post by Platinum89 on 2007-03-29
> **smartbei said:**
> use Synaptic to get totem-xine as the above poster suggested. It works.

Followed your suggestion, but unfortunately I get the below error when trying to watch the broadcast at cbc.ca   Any suggestions? :)

Totem could not play 'mms://a1987.v87520.c8752.g.vm.akamaistream.net/7/1987/8752/1175174786000/origin.media.cbc.ca/windows/hourly/hourlynewscast.wmv'.

Video codec 'MS WMV 9 (win32)' is not handled. You might need to install additional plugins to be able to play some types of movies

---

### Post by Luggy on 2007-03-29
I take it you guys are new. Not that that's a problem, it's just that a common problem for new users is that they think the porprietary codecs ( such as .mp3 and .wav ) they were used to in Windows should work for linux.

The easiest way to get these codecs is to run automatix.

run this command to install automatix if you use x86
```

sudo deb http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.32-6.10edgy_i386.deb

```

Once it's installed navigate to the multimedia section and install the multimedia codecs.

For more help check out [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Platinum89 on 2007-03-29
Yes, I'm new, but learning :redface: 

Opened the Terminal and pasted your command and then my password. Received the following notification.

sudo: deb: command not found

Am I missing something?:oops: :-k

---

### Post by jackrobinson on 2007-03-29
download this file:
[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.32-6.10edgy_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.32-6.10edgy_i386.deb)
and double click on it to install it. Then you will find it installed in applications --> system tools. run it. Its called automatix.

---

### Post by compiledkernel on 2007-03-29
> **jackrobinson said:**
> download this file:
[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.32-6.10edgy_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.32-6.10edgy_i386.deb)
and double click on it to install it. Then you will find it installed in applications --> system tools. run it. Its called automatix.

Automatix is unsupported software. It will likely break your system. And honestly it isnt supported by these forums. I caution any user in its use.

---

### Post by siepo on 2007-03-29
Activate the medibuntu repositories (google for details) and then install the w32codecs using synaptic, apt-get, aptitude or whatever.

---

### Post by kevinlyfellow on 2007-03-29
```
 sudo apt-get install libxine-extracodecs
```

or you can use synaptic to install  libxine-extracodecs.  Automatix just for this is a bit overkill and lots of people swear that its dangerous, but I don't know about the truth of that.  Last I used it it just made my system a bit messy, but I was able to clean it up.

Edit: Oh sorry, that doesn't provide wmv support (still do it though!).  yeah, your going to either use automatix/easy ubuntu or put in new repositories.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

