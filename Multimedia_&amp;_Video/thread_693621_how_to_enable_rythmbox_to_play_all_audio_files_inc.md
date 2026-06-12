---
title: "how to enable rythmbox to play all audio files including cds etc ?"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by tavati on 2008-02-11
how can i enable rythmbox to play all audio files etc including cd

---

### Post by cozmicharlie on 2008-02-11
You first need to install the encoders/decoders.  There are a number of packages you need to download. I am assuming you are running Gutsy but if not then look on the Medibuntu page for the instructions for whatever version of Ubuntu you are using.

Start by enabling the medibuntu repository (see [HTML]https://help.ubuntu.com/community/Medibuntu:[/HTML]

Open a terminal and type or cut ands paste the following (1 line at a time).
```
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

Make sure you have all your repsoitories open in Synaptic. Go to settings>repositories and you have tabs for "Ubuntu Software" and Third PArty Software" - make sure they are all checked. If not check and run update.

Open Add/remove programs under the Applications menu. Select "All", scroll down to the "Ubuntu Restricted Extras" and install these. It will ask you if you want to install packages and give you warnings. These packages all work fine in Ubuntu, it is just they have restricted licenses that you have to agree to.  Close Add/Remove, open Synaptic and search for "gstreamer". These should be installed when you install the Ubuntu Restricted Extras but double check and install any gstreamer-10 plug ins (good, bad, ugly) if they are not already installed.  I also install Lame for mp3. You can do this through Synaptic also. Search Lame and install the packages.

If you follow the above instructions you should have most audio codecs installed.  Go to Rythmbox, add your music files and that should do it.

---

### Post by cozmicharlie on 2008-02-11
This link will help also:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

