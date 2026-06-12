---
title: "Problem with Smplayer"
date: 2012-02-27
forum: Multimedia Software
---

### Post by blueshead on 2012-02-27
Mplayer has finished unexpectedly. Exit code :127

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo x11 -ao pulse -zoom -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 33554774 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/shack/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -contrast 7 -brightness 12 -volume 54 -cache 36 -osdlevel 0 -idx -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=8.8:6.4:7.3:7.6:5.9:6.4:3.8:6.1:8.5:5.9 -softvol -softvol-max 110 /home/shack/Videos/GANGS OF NEW YORK REMASTERED/Gangs of New York 2002 Remastered.m2ts

/usr/bin/mplayer: relocation error: /usr/bin/mplayer: symbol ff_codec_bmp_tags, version LIBAVFORMAT_53 not defined in file libavformat.so.53 with link time reference
```

" version LIBAVFORMAT_53 not defined in file libavformat.so.53 with link time reference" ?

---

### Post by raja.genupula on 2012-02-27
Hi i have got this for you .
[http://ubuntuforums.org/showthread.php?t=1560374](http://ubuntuforums.org/showthread.php?t=1560374)

hope that help you a bit

---

### Post by SeijiSensei on 2012-02-27
I'd remove mplayer and install mplayer2 using [this method]("http://www.ubuntugeek.com/install-mplayer2-on-ubuntu-using-ppa.html").

You can even leave the existing mplayer alone.  Once you add the "ripps" PPA and run "sudo apt-get update" running "sudo apt-get install mplayer" will overwrite your existing version with the one found in mplayer2.

Mplayer has been one of those programs whose development has happened "too fast" for distros to keep up with it.  The pace of development has slowed in the past couple of years, but it's pretty common to find fairly out-of-date mplayer builds in Linux repositories.  Nowadays I either use the ripps' version of mplayer2 or build my own from the [source code](http://www.mplayer2.org/).

---

