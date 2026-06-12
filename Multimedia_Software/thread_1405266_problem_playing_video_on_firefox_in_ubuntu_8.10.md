---
title: "problem playing video on firefox in ubuntu 8.10"
date: 2010-02-12
forum: Multimedia Software
---

### Post by ilovethislinuxstuff on 2010-02-12
hi everyone, 
i'm brand new to linux, and a computer dummy. i'm having a problem. i want to see the video in this website, [http://www.clubframeco.com/sm_video_introduction.html](http://www.clubframeco.com/sm_video_introduction.html), and can't make it work. when i clicked it, i was asked in a dialog box to search for the right codec or something, so i did. it asked me to download gstreamer. so i did. but i just get a blank box on the video when i click it. so i looked around in google for advice and decided to download the ubuntu-restricted-extras, and i did. and that's where i stand. can you all help me to play this video? thank you.
dj

---

### Post by ghostborg on 2010-02-12
I went to the page and right clicked on the video and selected about and the about box said:

Totem Browser Plugin 2.28.2
Browser Plugin using GStreamer 0.10.25

so I would think you should fire-up synaptic package manager System=>Addministration=>Synaptic Package Manager and type in "totem" in the seach box.

On my system I have installed:
totem
totem-plugins
totem-common
totem-mozilla
libtotem-plparser12

my guess is you are missing totem-plugins and/or totem mozilla.

Another useful thing for you to do is follow the instructions
for mediabuntu:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

cut and paste the command line instructions in a terminal window.

1. add the medibuntu repository and key
Adding the Repository

The following bash command adds Medibuntu's repository to Ubuntu. It also adds Medibuntu's GPG key to your keyring, which is needed to authenticate the Medibuntu packages.

    *

      This command should be run in the Terminal (Applications &#8594; Accessories &#8594; Terminal):

      sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


2. install using entire library :
playing encrypted dvd's

sudo apt-get install libdvdcss2

3. Playing Non-Native Media Formats

With the entire Medibuntu repository

If you have added the entire Medibuntu repository, install the package using APT.
Choose which ubuntu versino you installed 32bit or 64bit?
    *

      For i386, the package is called w32codecs:

      sudo apt-get install w32codecs

    *

      For amd64, the package is called w64codecs:

      sudo apt-get install w64codecs

---

### Post by ilovethislinuxstuff on 2010-02-13
thank you for your reply. it seems as though i can't get this. i'll give you the response from the terminal window. after i downloaded the first string of commands to get mediabuntu from the repository, here's what i got at the end: Reading package lists...
then when i tried to install, i got this: Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
what should i do? thank you.
dj

edit: by the way, i just looked at the synaptics package manager and all of the totem things that you have are already installed on my ubuntu...i wonder why that site video is not coming up for me?...

---

### Post by HappyFeet on 2010-02-13
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Copy and paste the complete string above into a terminal. Try again for w32codecs. But doing ```
sudo apt-get install non-free-codecs
```  will give you everything you need.

Also you might want to get mozilla-mplayer for firefox. Always works great for me. You don't have to remove totem-mozilla first.

---

### Post by ilovethislinuxstuff on 2010-02-13
thank you for the reply. youu guys are fantastic at replying. for a newbie it helps. now on to the bad news, i entered all of that info into the terminal, closed out, went back to the site i was having problems seeing (link is above in the original post) and i still only see a white box when i click the play button. was i supposed to do something else? is there a way for me to check to see if i have the right stuff downloaded and installed? if so, i would be glad to look and report back. let me know. thanks!

---

### Post by ilovethislinuxstuff on 2010-02-26
just wanted to let you guys know that i decided to upgrade to the newest ubuntu in order to see if it was easier for me to watch videos online. it seems to be. so, thanks for the help anyway!

---

