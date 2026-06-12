---
title: "[SOLVED] Installation of Mapivi 0.9.7 in Ubuntu 8.10 Intrepid Ibex"
date: 2008-11-11
forum: Multimedia Software
---

### Post by daucourt on 2008-11-11
Hi,

For previous release of Ubuntu 8.10 Intrepid Ibex, the following guidelines were usable [http://ubuntuforums.org/showthread.php?t=130912](http://ubuntuforums.org/showthread.php?t=130912)

For Intrepid, here are the guidelines:

1. Open a terminal through menu Applications/Accessories/Terminal
2. Then type the following commands

```
cd
wget http://heanet.dl.sourceforge.net/sourceforge/mapivi/mapivi097.tar.gz
tar xvfz mapivi097.tar.gz
```

3. then apply the full list of commands

```
sudo aptitude install jpegpixi libimage-exiftool-perl jhead libjpeg-progs ncftp lynx perl-tk libimage-info-perl  libimage-metadata-jpeg-perl libproc-processtable-perl
mkdir -p ~/.maprogs/mapivi/trash
cp ~/mapivi097/pics/EmptyThumb.jpg ~/.maprogs/mapivi/EmptyThumb.jpg
cp -r ~/mapivi097/icons ~/.maprogs/mapivi/

```

4. Then enjoy program launching

```
perl ~/mapivi097/mapivi
```

Thierry

PS : You can also install mapivi via synaptic/aptitude, but it is version 0.9.1 (not 0.9.7)

---

### Post by Martin-Herrmann on 2009-11-06
Mapivi 0.9.7 is now also available in the Ubuntu repositories, see [http://packages.ubuntu.com/search?keywords=mapivi]("http://packages.ubuntu.com/search?keywords=mapivi").

The new version 1.0 :KS is available here [http://mapivi.sourceforge.net/mapivi.shtml]("http://mapivi.sourceforge.net/mapivi.shtml").
Mapivi 1.0 is quite stable, but not yet recommended for productive usage. Anyhow I would be happy to receive some feedback.

Regards
      Martin

---

