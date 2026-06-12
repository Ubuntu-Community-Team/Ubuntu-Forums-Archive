---
title: "Squeezecenter has APE and FLAC greyed out"
date: 2009-03-13
forum: Multimedia Software
---

### Post by jpgoossen on 2009-03-13
Hi,

Got myself a Squeezebox Classic (GF didn't want all my CD's in the living room when shacking up) and am really happy with it. Am digitizing (well converting digital Audio CD to MP3 and such) my collection and all works well.

I have my Squeezecenter server 7.3.2 running on a Ubuntu 8.10 notebook. Music is on a USB connected portable drive. It connects, plays MP3, M4a, Wav et cetera.
Except that whenever I try AAC or Monkey Audio (APE) it will not play. In the settings (Advanced, File Types) those formats are greyed out.

I looked at the Slimserver Forum but found nothing relating to this issue. 
According to all information I read there, APE should be supported out of the box. I also tried to install any APE or AAC codec I could find in the package manager, but with no result.

Since according to that Forum, there is no specific Linux issue that would stop my box from playing those files, is there any Ubuntu specific issue on this matter?

Any advice one way or the other?

Thanks in advance,

Patrick

---

### Post by listener on 2009-03-13
I'm not knowledgable about the system you're using, but I have no idea why FLAC would not be available.  It should easily be installed from the repos if it isn't already there.  Monkey's Audio may be more difficult, as I don't think you can get it from the repos.  You can locate it and compile it yourself fairly easily though.  The Etree wiki has a webpage dedicated to lossless audio tools, and an entire section for Linux, it is a really good resource.  

I'd prefer FLAC, however.

Good Luck

---

### Post by mc4man on 2009-03-13
Don't know if you mean 'flac' or 'aac'
For flac - flac, libflac8
For aac - faad, libfaad0
For ape a .deb is available here (says jaunty, doesn't matter in this case

[https://launchpad.net/~quintasan/+archive/ppa/](https://launchpad.net/~quintasan/+archive/ppa/)

Don't add his repo, just expand the mac listing and scroll down to the "package files" listing and  click to dl and install. Most likely the mac_3.99-u4-b5-1_i386.deb (for 32 bit ubuntu install

Or you can get a .deb here (libmac2 ( same thing
[http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libmac2.php](http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libmac2.php)

---

### Post by jpgoossen on 2009-03-16
Mc4Man,

Thanks for your reply. I was unclear in my original question, I guess. I managed to install MAC from source, so Ape is now supported. FLAC seems to work, but I remember getting a message "cannot play file" or similar a while back on a FLAC file. Might be different sound-resolution from what is supported. Will have to look into that. LibFAAD I will look at, but if it not installed yet, I will see if I can add either some repository or compile from source. That should solve the last of my issues, and if some of them are bps related, I will do some batch converting, I guess.

Thanks!

Patrick

---

