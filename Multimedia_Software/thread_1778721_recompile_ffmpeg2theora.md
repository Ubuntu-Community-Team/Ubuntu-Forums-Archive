---
title: "recompile ffmpeg2theora?"
date: 2011-06-09
forum: Multimedia Software
---

### Post by lelandnielsen on 2011-06-09
Total noob question:
I'm trying to add subtitles to an ogg video using ffmpeg2theora.  I receive an error message stating that I need to install the -libkate packages and recompile.  So I get the packages from Synaptic, but I can't figure out how to recompile ffmpeg2theora.  
Help?
Thanks!

---

### Post by Yellow Pasque on 2011-06-10
You may need to enable source code repositories and get some packages if you haven't already:
```
gksu software-properties-gtk
sudo apt-get update
sudo apt-get install devscripts debhelper libkate-dev liboggkate-dev
cd ~
sudo apt-get build-dep ffmpeg2theora
apt-get source ffmpeg2theora
cd ffmpeg2theora-0.24 (version number may be different if you're not using natty)
dch -i #bumps version, edit changelog and save file
debuild -B -us -uc
cd ..
sudo dkpg -i ffmpeg2theora_0.24-2ubuntu2*.deb
```

---

