---
title: "Rhythmbox Ripping to MP3"
date: 2014-01-26
forum: Multimedia Software
---

### Post by Prime624 on 2014-01-26
I tried to use Rhythmbox to rip a CD to MP3 files, but it says I need the correct encoding files (or whatever it's called). I had already installed the MP3 encoding library (lame I believe) earlier to rip a CD with Asunder. Regardless, I hit the install button when Rhythmbox asked if I wanted to install the encoder. It said that the plugin could not be found. I then installed the Restricted Extras package from the Ubuntu Software Center, and tried again. It again said that I needed the correct encoder and when I hit install, it again said that it could not be found. I restarted my computer a few times throughout this process.

How can I fix this?

---

### Post by Yellow Pasque on 2014-01-26
First, install these packages:

```
sudo apt-get install gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-tools
```

Now, you should have lame encoder plugin:
```
$ gst-inspect-1.0 lame
Plugin Details:
  Name                     lame
  Description              Encode MP3s with LAME
  Filename                 /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstlame.so
  Version                  1.2.2
  License                  LGPL
  Source module            gst-plugins-ugly
  Source release date      2013-12-26
  Binary package           GStreamer Ugly Plugins (Debian)
  Origin URL               http://packages.qa.debian.org/gst-plugins-ugly1.0

  lamemp3enc: L.A.M.E. mp3 encoder

  1 features:
  +-- 1 elements
```

---

### Post by Prime624 on 2014-01-26
It lists each of those four and says it is already the latest version.

---

### Post by Yellow Pasque on 2014-01-26
What version of Ubuntu are you using?

---

### Post by Prime624 on 2014-01-26
13.10

---

### Post by Yellow Pasque on 2014-01-26
Well, I'm stumped. If you have the gstreamer1.0-plugins-ugly package installed, it should work.

Hopefully, someone who actually uses rhythmbox can help..

---

### Post by monkeybrain20122 on 2014-01-27
I don't know that Rhythmbox can be used to rip CD (I don't use it), so not able to help you there. But I know sound juicer would work (for gnome)

---

### Post by mc4man on 2014-01-27
You don't need to install anything more, the message is erroneous & can be ignored.
If you want it to go away just change the "Format Setting" to something else, ie. any of the options other than "Default"
restart Rb & no message see screens, 1st before restart, 2nd after

(note that the same is seen with vorbis

---

### Post by Prime624 on 2014-01-27
Wonderful. Thank you.

---

