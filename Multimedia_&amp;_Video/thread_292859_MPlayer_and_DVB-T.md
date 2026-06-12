---
title: "MPlayer and DVB-T"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by MikeMcKay on 2006-11-04
Hi,

I'm trying to get my DVB-T card working with either MPlayer or gxine in preparation for installing mythTV in accordance with the advice in [http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php).  

I think I've got the TV card outputting a sensible data stream to stdout but I get problems with both MPlayer and gxine when I try to get them to read from stdin. They appear to be different problems and I've taken the liberty of starting a separate thread for each.  This thread concerns MPlayer.

The tzap command seems to work and reports the following about every second:
    status 1f | signal c9c9 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK

The command I'm using to pipe the mpeg stream to MPlayer is:[INDENT]mike@polaris:~$ sudo -s -H
root@polaris:/home/mike# dvbstream -o -ps 201 202 -qam 16 -cr 3_4 | mplayer -v - 
[/INDENT]This seems to result in MPlayer crashing.

The output from dvbstream and MPlayer is attached.

Note that I don't have a joystick or IR Remote so I'm not concerned with the failures associated with the joystick and LIRC.

Note also that MPlayer appears to find a sensibly formatted stream on stdin.

Any suggestions would be welcome.

---

