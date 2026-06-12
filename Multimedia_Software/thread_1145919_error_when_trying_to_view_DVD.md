---
title: "error when trying to view DVD"
date: 2009-05-02
forum: Multimedia Software
---

### Post by madoldfart on 2009-05-02
when trying to watch a dvd

I load the DVD
then i get a dialogue box to choose what application to launch i select open movie player

Then i get the error:Could not open location; you might not have permission to open the file.

How can i fix - i am a newbie to ubuntu
Also how can i get it to auto load the DVD

---

### Post by xc3RnbFO8P on 2009-05-02
Here is a howto:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
and here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")
and install more codec, in Terminal:
> sudo apt-get install ubuntu-restricted-extras

---

### Post by madoldfart on 2009-05-02
i went to the links and installed as per the threads

i now have a new error Plugins

it asks me to search and when i search there are no suitable plugins

I just installed
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

and it now works problem solved. thanks for the help

---

### Post by MarcusA on 2009-05-02
It fixed it for me thankfully

---

### Post by xc3RnbFO8P on 2009-05-02
Did you do this:
> sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
> sudo apt-get install libdvdcss2
> sudo apt-get install w32codecs
>  sudo apt-get install libdvdread4
>  sudo /usr/share/doc/libdvdread4/install-css.sh
> sudo apt-get install ubuntu-restricted-extras

---

### Post by madoldfart on 2009-05-02
> **Ringi said:**
> Did you do this:
yes im sure i did all of that

---

### Post by AcelandineKestrel on 2009-05-02
I did every single thing here, installed all the necessary things....and it still tells me I don't have permission.

And, like I just said, I did EVERYTHING mentioned here. What the hell is going on??? Why won't it work???

---

### Post by trekkiencc74656 on 2009-05-04
I had the same problem. The problem still occurs with movie player however these steps did resolve the problem for vlc.

---

### Post by misplaced_ice on 2009-06-15
I'm also having the same problem.

I did all of the above but it's still not working - both with Totem and VLC.
Totem just disagrees that it's even there - it doesn't even give me any error messages - just ignores it.

VLC opens up a random window and will go to the menu but give me no control. The bar which normally has the playback stuff isn't there and I can't skip to other chapters - even by right clicking.
Some DVDs will just stop at the warning and not going any further.

:(

What am I doing wrong? 
Please help. It's driving me crazy. I may just have to turn to booze and drugs if I can't get it working ;)

---

