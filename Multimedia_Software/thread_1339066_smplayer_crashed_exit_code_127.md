---
title: "smplayer crashed: exit code 127"
date: 2009-11-27
forum: Multimedia Software
---

### Post by kboy on 2009-11-27
Hi, i've installed ubuntu 9.10 and with it smplayer. the problem is whenever i load a file in smplayer it crashes with an exit code 127.

any help will be appreciated.

---

### Post by rvm4000 on 2009-11-27
What does the mplayer log say? (Options->View logs)

---

### Post by kboy on 2009-11-27
here's the log of the exit code:

> /usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 69206031 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/fibo/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 100 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 500 /home/fibo/Videos/TV Shows/Seinfeld/Season 2/seinfeld.2x04.the_phone_message.dvdrip.avi

/usr/bin/mplayer: symbol lookup error: /usr/bin/mplayer: undefined symbol: codec_wav_tags


---

### Post by kboy on 2009-11-27
anyone?

---

### Post by rvm4000 on 2009-11-27
It seems mplayer was not compiled properly, or maybe a library is missing. I suggest to reinstall the mplayer package.

---

### Post by kboy on 2009-11-28
I've reinstalled several times, it didn't help.
the same error code continues every time

---

### Post by anonSam on 2009-11-28
Sometimes deleting the config files fixes problems like that for me. When you restart SMPlayer, the config files will automatically be re-generated. Of course, you'll have to reconfigure your personal SMPlayer settings again. 

The path on my system is:

/home/<USERNAME>/.config/smplayer

---

### Post by rvm4000 on 2009-11-28
You can also try to update mplayer:

[http://launchpad.net/~rvm/+archive/mplayer](http://launchpad.net/~rvm/+archive/mplayer)

BTW, it seems your problem is reported here:
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/461966](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/461966)

---

