---
title: "sm player not working"
date: 2011-03-10
forum: Multimedia Software
---

### Post by suresnjain on 2011-03-10
SM player is not working -it shows "M Player has finished unexpectedly.Error Code:127"                                              and log shows"/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 62914903 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/suresnjain/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 1 -subpos 100 -volume 51 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/suresnjain/Desktop/factsgbl_pkumar_04mar.flv

/usr/bin/mplayer: relocation error: /usr/bin/mplayer: symbol rgb24toyv12, version LIBSWSCALE_0 not defined in file libswscale.so.0 with link time reference
 please help. My system is Ubuntu 10.04 LTS and VLC player and Movie Player  both are working fine.

---

### Post by no2498 on 2011-03-10
you do this yet

sudo apt-get install ubuntu-restricted-extras

---

### Post by andrew.46 on 2011-03-11
Hi suresnjain,

Have you used a PPA that has replaced some of the libraries associated with FFmpeg?

Andrew

---

