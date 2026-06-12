---
title: "Enabling Multimedia in Feisty (HOW-TO)"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by Adamant1988 on 2007-04-19
Video/audio codec, flash, mp3, dvd playback, and win32 Codec install for Feisty Fawn for beginners. If your a new user, copy and paste commands into the terminal, should be relatively easy from that point forward. 

**_ For mp3, etc. _**
Open up Add/Remove programs from your Application bar. 

Go to Sound&Video and Find and Check all of the packages below (easily done by searching for gstreamer)
[list]
[*]"GStreamer ffmpeg video plugin"
[*]"GStreamer extra plugins"
[*]"GStreamer plugins for aac, xvid, mpeg2, faad"
[*]"GStreamer plugins for mms, wavpack, quicktime, musepack"
[/list]

Then go to Other subsection of Add/Remove and find
[list]
[*]"Ubuntu restricted extras"
[/list]
**_For Flash support_**

While under the "Other" section enable
[LIST]
[*]"Macromedia Flash plugin"
[/LIST]


**_For DVD Playback and Win32 Codecs _**

Edit the file /etc/apt/sources.list using either of the following commands in a terminal:
```

$gksudo gedit /etc/apt/sources.list

```
to open it in the GUI text editor

or

```
$sudo vim /etc/apt/sources.list
``` 
to open it in the Vim command line text editor

Add the following lines to add the Medibuntu repository to the file:

[quote]## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Now update the local list of packages to get the list of packages from the newly added Medibuntu repository:

In a terminal execute the following command:

```
sudo apt-get update
```

Now you can install libdvdcss2 and w32codecs using the following command:
```

sudo apt-get install libdvdcss2 w32codecs
```

[Medibuntu doc page]("https://help.ubuntu.com/community/Medibuntu")

---

