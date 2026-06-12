---
title: "DVD playback - no picture in Kaffeine, Totem crashes"
date: 2008-04-26
forum: Multimedia Software
---

### Post by dangoeslinux on 2008-04-26
I have no idea what I am doing wrong, but I can't get my laptop to play DVDs. I read all sorts of threats, installed all sorts of stuff but the DVDs won't play. Please help!!!!

I am running 7.10. Totem starts if a DVD is inserted but crashes immediately. The DVD will play in Kaffeine but there is no picture. The sound and the DVD navigation seems to work fine.

I am thankful for any suggestions.  :confused:

---

### Post by rumli on 2008-04-26
Did you try the instructions found here:
[http://www.funnestra.org/ubuntu/hardy/#totem-xine]("http://www.funnestra.org/ubuntu/hardy/#totem-xine")?

Install Totem-xine with codecs and DVD support:
```

sudo apt-get install totem-xine
wget -c -P /tmp/ http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.0_i386.deb
wget -c -P /tmp/ http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb
sudo dpkg -i /tmp/w32codecs_20071007-0.0_i386.deb /tmp/libdvdcss2_1.2.9-0.0_i386.deb

```

Change the default Totem alternative to Totem-xine: 
```

sudo update-alternatives --config totem

```
and enter the number corresponding to /usr/bin/totem-xine.

---

### Post by dangoeslinux on 2008-04-28
I tried your suggestions, but there is no change. Totem still crashes and Kaffeine plays but no picture. I installed the xine backend, w32 codecs and the libdvdcss2_1.2.9-0.0 in the past. Synaptic confirms that all these packages are installed and that I have the latest versions. There are also some gstreamer packages installed.

The last suggested command line gives me the following output:

laptop:~$ sudo update-alternatives --config totem
No alternatives for totem.
laptop:~$ sudo update-alternatives --config gnome-video-thumbnailer

There is only 1 program which provides gnome-video-thumbnailer
(/usr/bin/totem-video-thumbnailer). Nothing to configure.


:confused: More ideas? :confused:

---

### Post by dangoeslinux on 2008-04-28
I installed gxine but it's the same problem - no picture. DVD navigation and audio works.

PLEASE HELP!

---

### Post by ubuntu-freak on 2008-04-28
Have you not tried VLC? Did you run the install-css.sh command at all? You don't need to remove Gstreamer to watch DVDs, give my [how-to](http://ubuntuforums.org/showthread.php?t=766683) a try and use VLC. You can also make it launch by default and at fullscreen when a DVD is inserted.
 
Hope that helps,
 
Nathan
 
P.S. Try disabling effects in System>Preferences>Appearance>Effects if you still have problems.

---

