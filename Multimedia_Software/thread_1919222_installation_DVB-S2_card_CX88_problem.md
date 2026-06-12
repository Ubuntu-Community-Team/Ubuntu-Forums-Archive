---
title: "installation DVB-S2 card CX88 problem"
date: 2012-02-02
forum: Multimedia Software
---

### Post by geforce430 on 2012-02-02
I install a DVB-S2 card CX88 but can not find the way to scan for channels due to some interface problem i can see it on firmware (in VLC or Kaffeine or VDR)  
code:
[COLOR=Teal]$ uname -a
Linux avi-desktop 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 i686 i386 GNU/Linux[/COLOR]
[COLOR=Teal]
[COLOR=Black]Code: [/COLOR]
$ lsmod
Module                  Size  Used by
cx88_vp3054_i2c        12840  0 
videobuf_dvb           13867  0 
dvb_core               94826  1  videobuf_dvb
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
vesafb                 13489  1 
nvidia              10390874  40 
snd_hda_codec_hdmi     31426  4 
tuner                  26836  1 
ppdev                  12849 
[COLOR=Green]
[/COLOR][/COLOR][COLOR=Green]$ dmesg | grep dvb
[  175.556848] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[  175.556856] cx88/2: registering cx8802 driver, type: dvb  access: shared[/COLOR]

---

### Post by geforce430 on 2012-02-03
Can anyone assist please ?
:(

---

### Post by maff on 2012-02-03
> **geforce430 said:**
> Can anyone assist please ?
:(

What are you using to scan?

in the uk i use this to build a channels.conf file:

scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf

This site is useful:
[http://parker1.co.uk/mythtv_about.php](http://parker1.co.uk/mythtv_about.php)

---

### Post by geforce430 on 2012-02-03
thanks
Well i didn't have the ability to scan in every software that i use (kafeine, VDR, MPlayer etc)
is it driver config problems ? how can i know ?
I got a CD with the card but no idea how to install it

---

### Post by geforce430 on 2012-02-03
i got on Code : scan Hotbird 13E | tee channels.conf: Permission denied 
scaning hotbird 13E using '/dev/dvb/adapter0/frontend and '/dev/dvb/adapter0/demux0'
main:2284: FATAL failed to open '/dev/dvb/adapter0/frontend0' : 2 no such file or directory
What should i do now ?

---

### Post by maff on 2012-02-03
> **geforce430 said:**
> i got on Code : scan Hotbird 13E | tee channels.conf: Permission denied 
scaning hotbird 13E using '/dev/dvb/adapter0/frontend and '/dev/dvb/adapter0/demux0'
main:2284: FATAL failed to open '/dev/dvb/adapter0/frontend0' : 2 no such file or directory
What should i do now ?

Check here to see if your card is supported
[http://www.linuxtv.org/wiki/index.php/DVB-S2_Devices](http://www.linuxtv.org/wiki/index.php/DVB-S2_Devices)

Hopefully it will point your in the right direction.

---

