---
title: "playing .wmv movies"
date: 2008-10-13
forum: Multimedia Software
---

### Post by tonymoloney on 2008-10-13
I'm having great problems playing a .wmv movie on Hardy Heron. The movie was made by my niece using the latest version of Windows Movie Maker.
I have followed all the advice given on the forums and Google and have /usr/lib/win32/essential-20071007.tar.bz2 unpacked and installed on my system, but still no joy.
Movie Player starts up but only the soundtrack plays, with visualizations taking the part of the video.
If it's any consolation, I have tried to play the movie on my friends WinXP computers and had no luck until I tried a friend who is running Vista (and presumably has all the latest codecs).
I haven't done it yet, but my next step will be to burn the file to a DVD and see if it will play on my DVD player.

---

### Post by pytheas22 on 2008-10-13
Ubuntu should be able to play .wmv files.  You can make sure that you have all the proprietary codecs installed by typing:
```

sudo apt-get install ubuntu-restricted-extras
```

You could also probably convert the file to raw video using Kino or VLC and then export it out again into a more Linux-friendly format, but this would take a long time and should not be necessary, unless this is some strange new kind of .wmv file.

---

### Post by tonymoloney on 2008-10-13
OK. I installed the restricted extras, but still no joy. I don't particularly want to go the other route that you suggested.

---

### Post by pytheas22 on 2008-10-13
If you open a command-line, cd to the location of the file and type:

```
file [filename]
```

what is the output?  Also, if the file's not too big or private, you could try putting it up somewhere where someone else could download it and see about getting it to work in Ubuntu.

---

### Post by tonymoloney on 2008-10-14
Sorry about the delay in answering - living in Western Australia has its difficulties when trying to keep up forum correspondence.
Anyway, I did what you said and the output after the file name was
: Microsoft ASF
Does that help?

And just to add to the confusion, I have just obtained a live cd of Elive. I was running this and noticed that it had Movie Player on it, so I decided to see what would happen if I tried to open my problem file with it.
You guessed it. The file played first time! So it would look like Elive has a more up-to-date version of Movie Player than Hardy Heron.

---

### Post by pytheas22 on 2008-10-14
Well, good to hear that it's definitely playable in Linux somehow.  I'm still not sure why it won't work in Ubuntu, however, because according [to this page]("https://help.ubuntu.com/community/RestrictedFormats"), if you install the 'ubuntu-restricted-extras' package (which you did yesterday if you followed my suggestion in post #2), .wmv should play.  But I do think that 'Microsoft ASF' is a newer version of .wmv that perhaps isn't supported yet in Ubuntu, so that could be the issue.

I think it might be worthwhile to try using a couple of different programs.  I am reading that mplayer (an alternative media player) might have better luck with ASF files.  You can install it with:
```

sudo apt-get install mplayer
```

Then launch it from the Applications>Sound and Video menu.  Can it handle your video (note that you have to right-click on the mplayer window in order to launch a menu where you can select which file to play...or you can right-click on the file itself and select 'open with Mplayer Movie Player' or whatever sounds closest to that)?

You may also want to give VLC a shot:
```

sudo apt-get install vlc
```

(or download the latest package from its [website]("http://www.videolan.org/vlc/")).

Please let me know if you have luck with these programs.

---

### Post by tonymoloney on 2008-10-15
I already have both those applications installed.
VLC behaves exactly the same as Movie Player i.e. sound but no video
When I run mplayer and select the file to play I get a message saying 

Cannot find the codec matching selected -vo and video format 0x32505657

and I agree - this video was made with the latest version of MS MovieMaker - on a Vista system, in fact. I have been able to get it to run on a friend's Vista system.

---

### Post by pytheas22 on 2008-10-15
You might try playing with the video driver settings in mplayer--right click and select preferences.  I can't guarantee that it will help, but it may.  Otherwise, I'm not sure what else to suggest because everything I'm reading says that ubuntu-restricted-extras should do the trick, although as we've discussed, it's possibly that this is a really new format not handled by the existing Ubuntu codecs.  It's also possible (though unlikely, because I don't think Elive has any money) that Elive paid to license a proprietary codec for this type of video that may not be available anywhere on Ubuntu, as it costs money.

---

### Post by frankleeee on 2008-10-15
All the codecs listed above a great, but if your using gstreamer I always add all of them as well, the gstreamer ffmpeg reads wmvs' in add remove. smplayer is a good media player as well.

---

### Post by rakris on 2008-10-15
```
sudo apt-get install w32codecs
```
```
mplayer blah.wmv
```


:popcorn::popcorn:

---

### Post by tonymoloney on 2008-10-15
rakris
when I followed your sudo apt-get install w32codecs
This is the output I got

Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by pytheas22 on 2008-10-15
Does it work if you run these commands:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
sudo apt-get install w32codecs
```

According to [this page]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html"), this works on Hardy.  I thought that w32codecs was part of the ubuntu-restricted-extras package, but maybe I was wrong.

---

### Post by tonymoloney on 2008-10-15
OK. Did all that without any problems but still no success.
Thanks for all your help. I'm getting frustrated with this and the video is not really that important to me, so I'll be happy to put it on the back-burner for now.

---

### Post by OttifantSir on 2008-10-16
If it's made with the latest Movie Maker (for Vista) and coded high enough with resolution above 512x586 and the bitrate is above 1000 Kbit/s, it might be that it has been encoded with Windows Media Video 9 Professional which is intended for HD-videos and professionals and not backwards compatible with any other WMV 9 codecs. (According to Wikipedia's article on WMV)

---

### Post by Bablefish on 2008-10-16
You always could check out Automatrix, it also allows you to play DVDs

---

### Post by rakris on 2008-10-20
after installing w32codecs.

use mplayer to play it.

check it in commandline. "mplayer file.wmv"

---

### Post by yelserpdog on 2008-10-21
I had the same problem. I eventually solved it but going to system>preferences, clicking on the visual effects tab and choosing "none". Videos now play without any problems

---

