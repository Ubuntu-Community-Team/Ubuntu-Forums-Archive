---
title: "Problem playing mp3's.  ID3 tag demuxer"
date: 2009-10-03
forum: Multimedia Software
---

### Post by abulluck on 2009-10-03
Ok, this problem is driving me crazy.  I have searched everywhere to no avail.  

Whenever I try to play any mp3's in any program (totem, rhythmbox, etc) I get a "search for codecs" which results in a "missing id3 tag demuxer".

When I run rythmbox in a terminal here is the error it returns:

[COLOR="Navy"]Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|ID3 tag demuxer|decoder-application/x-id3
/usr/lib/python2.6/dist-packages/GnomeCodecInstall/Main.py:102: GtkWarning: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
  res = dlg.run()[/COLOR]

I have all of the Gstreamer packages installed.

Please someone help on this one. 

Thanks
Andy

---

### Post by abulluck on 2009-10-04
Someone has to have solved this before.  I cannot do anything with mp3's in any program.  They all want to look for plugins "id3 tag demuxer" and it returns nothing.

This is frustrating the hell out of me as there are no solutions out there.

If someone doesn't have a solution to fix it, then what do I need to re-install to make this work.  I just recently did a reinstall of 9.04, but I have a seperate /home partition that I kept intact when I reinstalled.

Please, I need some help here.

Thanks

---

### Post by xterm on 2009-10-20
I have the exact same problem!

I did a re-install of 9.04 and installed all gstreamer packs I could find threw synaptic. And installed ubuntu-restricted-extras ... 

No luck in playing MP3 files in any program

---

### Post by abulluck on 2009-10-20
Sorry, I should have followed up my post but I found the problem or I fixed it without knowing which step fixed it.

My problem was the mp3 files I was trying to play were bad.

I know how frustrating it is cause there is not a  lot of info out there.  Before you pull anymore hair out, try creating a fresh mp3 file from an audio cd and playing that.

---

