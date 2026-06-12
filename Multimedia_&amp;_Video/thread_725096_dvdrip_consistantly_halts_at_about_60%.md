---
title: "dvd::rip consistantly halts at about 60%"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by slacker9876 on 2008-03-15
Since my dogs decided to eat about 30 of my movies I acquired a 1TB disk to add to the system so I could archive all of them just in case they get hungry again. I know I could ISO the discs but I would rather have them ripped so I can also enjoy diskless playback through Front Row on my mac.

I have used dvd:rip in the past successfully on this computer, but I just rebuilt it as I wanted to eliminate the Windows side of the system. I added the needed repos and installed the ubuntu-restricted-extras and dvd::rip and find it odd that it is freezing up on **any** DVD at the same spot.

I am going to try acidrip, but would like to know if anyone has seen this same issue as occasionally it is nice to transcode for iPod, etc.

---

### Post by xc3RnbFO8P on 2008-03-15
Try this:
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by slacker9876 on 2008-03-16
Thanks man, it still stops, but it does completely extract the VOB files and I just finished encoding Full Metal Jacket and playback was fine all the way through the credits. Not sure what I missed as I used this before I freshly rebuilt the system as x86_64. So I am working and now I can begin this daunting task.

---

### Post by xc3RnbFO8P on 2008-03-16
You could install again:

> sudo apt-get install w64codecs

> wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb

And reinstall DVD::RIP

---

