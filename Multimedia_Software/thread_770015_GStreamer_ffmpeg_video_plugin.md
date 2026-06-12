---
title: "GStreamer ffmpeg video plugin"
date: 2008-04-27
forum: Multimedia Software
---

### Post by YMS_1975 on 2008-04-27
Hey folks,

I'm running Ubuntu 8.04 (Hardy Heron) & I recently tried to play an ".flv" file.

I double click the file, and the "Totem Movie Player" application launches. It then presents me with a dialog box that says:

[SIZE="4"]Search for a suitable codec?[/SIZE]
[SIZE="3"]The required software to play this file is not installed. You need to install suitable codecs to play media files. Do you want to search for a codec that supports the selected file?

The search will also include software which is not officially supported.[/SIZE]

I then click "Search" and it looks for the suitable codecs. It pulls up 2 hits :

1) GStreamer ffmpeg video plugin
2) GStreamer plugins for mms,wavpack,quiti...

When I select option 1 it gives me this error : 

[B]W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.12-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.12-1_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-5ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-5ubuntu1_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.3-6_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.3-6_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)[/B]

Lil' help?:confused:

---

### Post by Wings.55555 on 2009-02-07
Hello, I am new to the beautifull world of Ubuntu. i too am facing the same problem above, but i know the reason for it. i do not have an internet connection right now. so it would be really very helpfull if somebody gives me details as to where i can download the codecs/plugins for both video and MP3 playback in my Ubuntu 8.10.

I will download them at my friend's house and instal them in my desktop.



PS:Though i am new to this, i am already spreading Ubuntu among my classmates and 6 people want to install it like me.

---

### Post by wolfen69 on 2009-02-07
do ```
gksudo nautilus
``` 
and navigate to /etc/apt/sources.list

then copy the sources.list to your home folder or whatever.
then delete your current sources.list and replace with this one:
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20080222)]/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse
```

this is a standard sources.list using repos from the US.
then
```
sudo apt-get update
```

---

### Post by xereniak on 2009-06-09
just use the link u posted in these forums (whoever posted the error message for the download) and it will download the codec. then you can tranfer it and stuff. then look at tthe next post for more instructions

---

### Post by xereniak on 2009-06-09
ya, i need help getting the rest of the files... there are six other files needed to install it without internet that i can't get from the site! 
Error Message: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.1_i386.deb) Could not resolve 'security.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.12-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.12-1_i386.deb) Could not resolve 'ca.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.1_i386.deb) Could not resolve 'security.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-5ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-5ubuntu1_i386.deb) Could not resolve 'ca.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.1_i386.deb) Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.1_i386.deb) Could not resolve 'security.ubuntu.com'
:confused:

---

### Post by Arup on 2009-06-10
Open up terminal, for Hardy copy paste 

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

after its done enter

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

You will be able to install all the codecs after this.

---

### Post by xereniak on 2009-06-10
Gstreamer audio plugin

hello, just posting some useful links for other plugins. may not work though, im posting these to test them. use these if you don't have internet on your ubuntu. otherwise, use the software from the software search. 
Error Message:
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-11ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-11ubuntu1_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-8ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-8ubuntu1_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/m/mpeg2dec/libmpeg2-4_0.4.1-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/m/mpeg2dec/libmpeg2-4_0.4.1-1_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'

---

### Post by xereniak on 2009-06-10
I don't have internet on my ubuntu.

---

### Post by xereniak on 2009-06-10
Video plugin 2 Error Message

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libi/libiptcdata/libiptcdata0_1.0.2-2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libi/libiptcdata/libiptcdata0_1.0.2-2_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.7-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.7-1_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.109.2-1ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.109.2-1ubuntu1_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-6_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-6_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.2ubuntu0.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.2ubuntu0.1_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wildmidi/libwildmidi0_0.2.2-2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/w/wildmidi/libwildmidi0_0.2.2-2_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.6-5ubuntu0.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.6-5ubuntu0.1_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'

---

### Post by Bill Nye on 2012-12-17
So I'm new to Ubuntu, and this is my first post. I'm probably wrong, but I think that you may need to add a third party repository to your list of software sources. Check out this page [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu).

---

