---
title: "DVD does not play"
date: 2008-05-10
forum: Multimedia Software
---

### Post by fogelfink on 2008-05-10
I have looke through these forums for two days now to find a solution for my dvd playing problem.  First of all I have to say I am new to linux and am just trying to get my new laptop (no dual boot) to work on Ubuntu.  
And I can't get it to play dvds - I tried lots of things:
followed this sticky: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and went through all steps, so I should have all the relevant stuff. 

I tried that thread: [http://ubuntuforums.org/showthread.php?t=747326](http://ubuntuforums.org/showthread.php?t=747326)

But to no avail!  This is the message I get on my terminal:


```
abraxas@abraxasmobile:~$ vlc dvd://dev/scd0
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat dev/scd0
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000294] dvdread demuxer error: DVDRead cannot open source: dev/scd0
[00000292] main input error: no suitable access module for `dvd://dev/scd0'
[00000283] main playlist: nothing to play

```

And when I load a dvd, vlc tries to open it, but crashes in 3 out of 5 cases, or it simply does nothing.

Can anyone help me with that - I am a complete beginner.
Cheers

---

### Post by ajaychebbi on 2008-09-26
I am getting the exact same error. No luck so far. The drive just wont mount DVDs. Works fine in Windows XP.

---

### Post by silkstone on 2008-09-26
Have you installed libdvdcss2?  You need that to play videos.

Make sure you have the Medibuntu repos enabled...

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then...

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot
```

then:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

or, if you get an error with that command:

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

Making VLC the default player for DVDs involves a couple of extra steps...

```
gksudo gedit /etc/gnome/defaults.list
```

Scroll down to the "x-content/video" entries and change "totem.desktop" to "vlc.desktop". Save and close.

Next, right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right.

Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties" and change the launch command from "vlc %U" to:

vlc %m

Close the VLC properties dialog and exit the menu editor. Finally, navigate to Nautilus > Edit > Preferences > Media > DVD Video and select VLC.

---

### Post by lkraemer on 2011-10-29
silkstone,
Great Post....I updated it for Ubuntu 10.04.3 as follows:


Make sure you have the Medibuntu repos enabled...

```

sudo wget http://www.medibuntu.org/sources.list.d/lucid.list -O /etc/apt/sources.list.d/medibuntu.list

```

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Then...

```

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot

```
then:

```

sudo /usr/share/doc/libdvdread4/install-css.sh

```
or, if you get an error with that command:

```

sudo updatedb
locate install-css.sh

```
Then change the following command accordingly for the correct path ...
```

sudo /usr/share/doc/libdvdread4/examples/install-css.sh

```

```

sudo apt-get install w32codecs

```

Now you can Install non-free-codecs
```

sudo apt-get install non-free-codecs

```

This will enable your system to support for MP3 and various other audio formats, unrar. Java runtime environment, Flash plugin, Microsoft fonts, w32codecs etc!
You can install more codecs and DVD Support by using:

```

sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine mencoder

```

Making VLC the default player for DVDs involves a couple of extra steps...

```

gksudo gedit /etc/gnome/defaults.list

```

Scroll down to the "x-content/video" entries and change "totem.desktop" to "vlc.desktop". Save and close.

Next, right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right.

Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties" and change the launch command from "vlc %U" to:

vlc %m

Close the VLC properties dialog and exit the menu editor. Finally, navigate to Nautilus > Edit > Preferences > Media > DVD Video and select VLC.

Thanks.

lk

REF:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://ubuntuforums.org/showpost.php?p=5861353&postcount=3](http://ubuntuforums.org/showpost.php?p=5861353&postcount=3)
[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

---

