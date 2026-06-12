---
title: "Audio device: Intel Corporation 82801G (ICH7 Family)"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by gui_love on 2007-10-04
In hope that's help 

lenovo 3000 c200

Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


1	(K)ubuntu users download and install first alsa-utils-1.0.14 because alsaconf does not exist by default (feisty).
After installation try "sudo alsaconf" to be sure that's ok.
2	Download realtek-linux-audiopack-4.07a.tar.bz2 
    [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false)

3	Extract and install (automatic by sudo ./install) and follow the indications on the screen for alsaconf.
4	Restart and enjoy.


PS when i restart a insane microphone effect has start,be sure you have a headphone jack to mute the speakers and slow down the microphone on the mixer or mute it.

---

### Post by u_kraze on 2007-10-26
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
./install: 100: alsaconf: not found


That is my output does it work if i restart right away??:confused:


NEVER MIND i got it working ...

---

### Post by TiMaxime on 2007-12-30
HI everyone, yeah first message.. too much trouble to make my sound work!!
ive got the same sound card as one said before, and alsa is installed but when i go in terminal i get that
> timaxime@timaxime:~$ sudo alsaconf
sudo: alsaconf: command not found


so yeah, ive looked on like 10forums to find something and thats the first one with the exactly same problem as me, and have got two mates who have the same problem as well (speaker not working)
so if someone can help me, that would be really appreciate :guitar:

cya soonn
and thanks again

---

