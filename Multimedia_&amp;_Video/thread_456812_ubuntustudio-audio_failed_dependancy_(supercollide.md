---
title: "ubuntustudio-audio failed dependancy (supercollider -&gt; libjack)"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by c0ntax on 2007-05-28
It seems that trying to install the audio side of Ubuntu studio doesn't work on my AMD64 hardware. I'm running x86_64 on Feisty Fawn and every time I try to run:

```
sudo aptitude install aubuntustudio-audio
```

I get:

```
The following packages have unmet dependencies:
  supercollider: Depends: libjack0.80.0-0 (>= 0.98.1) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
galan [Not Installed]
supercollider [Not Installed]
ubuntustudio-audio [Not Installed]
```

I have libjack0.100.0-0 install but I  guess it specifically needs 0.80? If anyone could help I'd really appreciate it.

I also get similar dependancy problems when trying to install ubuntustudio-video (but I'm less bothered about video stuff):

```
The following packages have unmet dependencies:
  cinepaint: Depends: cinepaint-data (= 0.21-2-0ubuntu4) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
cinepaint [Not Installed]
ubuntustudio-video [Not Installed]
```

---

### Post by kiwidoc66 on 2007-05-28
Are you installing from the Ubuntustudio repo? If not the website gives instructions for adding it at [http://www.ubuntustudio.org/downloads](http://www.ubuntustudio.org/downloads)

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

Have you installed the  ubuntustudio-desktop meta-package first?

If you have and it still isn't working, it's gone beyond me sorry...

---

### Post by c0ntax on 2007-05-30
I tried that but got the following error when apt-get update was ran:

```
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
```

:-(

---

