---
title: "How to play 3gp files on Gutsy Gibbon"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by tenmoi on 2008-03-06
Hi everyone!

I had been trying for 2 days getting mplayer and vlc to play 3gp files with sound without success untill I found this thread [http://ubuntuforums.org/showthread.php?t=178455](http://ubuntuforums.org/showthread.php?t=178455). The thread was a great help. So all that is going to follow here is just a summary of all the posts there. I just add my words to save time so pls do not accuse me of plaigarism.
I did exactly as following.  

#This is not the definitive how to, but a reasonable bodge that should work quite easily. #This particular version of ffmpeg, ffplay & ffserver will be installed in /usr/local/bin, and #will not overwrite theversion of ffmpeg. ffplay & ffserver installed via synaptic or apt-get.


First of all open a shell.

Next use this command to get the source for ffmpeg:

svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg

Next get the codec you need for the audio by typing this into the shell

wget [http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-510.zip](http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-510.zip)

or go to: [http://www.penguin.cz/~utx/amr](http://www.penguin.cz/~utx/amr)

and download the newest version. (I downloaded both libamrnb and libamrwb)

Extract the libamrn(w)b wrappers and go to the source directories. Configure, build and install them.

Code:

./configure --prefix=/pathto/my/home/folder/libamrnb

Code:

make && sudo make install

then for libamrwb:

Code:

./configure --prefix=/pathto/my/home/folder/libamrwb

Code:

make && sudo make install



The file, "26.104/26104-510.zip", needs to be unzipped anywhere you like. A folder inside ~/ffmpeg/libavcodec called "amr_float" needs to be created. Next the file within it called "26104-510_ANSI_C_source_code.zip" needs to be unzipped, and the contents placed in "~/ffmpeg/libavcodec/amr_float/".



Now that all this has been done, you need to follow 2 , supposing that you have all the libaries and lib*-dev development files installed. Else you follow 1:

1. code:

cd ~/ffmpeg

./configure --prefix=/pathto/my/home/folder/ffmpeg-svn --enable-libamr-nb --enable-nonfree --enable-gpl --enable-libamr-wb  --extra-cflags=-I/pathto/my/home/folder/libamrnb/include --extra-ldflags=-L/pathto/my/home/folde/libamrnb/lib --extra-cflags=-I/pathto/my/home/folde/libamrwb/include --extra-ldflags=-L/pathto/my/home/folde/libamrwb/lib


2.Code:
cd ~/ffmpeg

./configure --prefix=/pathto/my/home/folder/ffmpeg-svn --enable-libamr-nb --enable-libvorbis --enable-libxvid --enable-libmp3lame --enable-libx264 --enable-nonfree --enable-gpl --enable-libamr-wb --enable-libtheora --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-pthreads --extra-cflags=-I/pathto/my/home/folder/libamrnb/include --extra-ldflags=-L/pathto/my/home/folde/libamrnb/lib --extra-cflags=-I/pathto/my/home/folde/libamrwb/include --extra-ldflags=-L/pathto/my/home/folde/libamrwb/lib

then

make

sudo make install

Now do this:

Add this line of code

# libamrnb
/home/nam/libamrnb/lib

to /etc/ld.so.conf.d/libamrnb.conf. Create this file if it doesn't exist. Then run

Code:

sudo ldconfig

then add this line of code:

# libamrwb
/opt/libamrwb/lib

to /etc/ld.so.conf.d/libamrwb.conf. Then run

Code:

sudo ldconfig

Now you should be able to play 3gp movies by typing the following:

/usr/local/bin/ffplay <full-path-to-3gp-file>

This particular version of ffmpeg, ffplay & ffserver will be installed in /usr/local/bin, and will not overwrite theversion of ffmpeg. ffplay & ffserver installed via synaptic or apt-get.:guitar:

Do hope that you'll share my luck.

---

### Post by andrew.46 on 2008-03-08
Hi,

 There may be slightly clearer directions for mplayer both here:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

which describes how to install the svn mplayer and here:

[http://ubuntuforums.org/showpost.php?p=4378414&postcount=195](http://ubuntuforums.org/showpost.php?p=4378414&postcount=195)

which describes how to add the amr wide and narrow band software.

     Andrew

---

### Post by stooshbunutu on 2008-03-11
you can always convert using mobile media converter

[http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

---

