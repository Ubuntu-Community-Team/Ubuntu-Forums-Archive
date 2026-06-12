---
title: "Howto: Samsung YP-T10 MTP and the svi video codec"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by sornen on 2007-12-28
[SIZE="5"]Howto: Samsung YP-T10 MTP and the SVI video codec[/SIZE]

[COLOR="DarkRed"][SIZE="5"]UPDATE[/SIZE]

There is now a hacked firmware version which will turn the player into a UMS device, but possibly also brick the device:

[http://www.anythingbutipod.com/forum/showthread.php?t=21463](http://www.anythingbutipod.com/forum/showthread.php?t=21463)

Foxx has added packages for libmtp 0.2.4 rhythmbox 0.11.4 and gnomad2 at his site.  Scrolldown to read about it.

If you scroll down there is also a howto for downloading youtube videos.
[/COLOR]

On an urge I bought the YP-T10 without realising that it was an MTP device and not a UMS device.   Fortunately you can get it working with linux.  The first part explains &#8220;howto" get MTP working and the second part &#8220;howto"  create svi video files.

[SIZE="5"]MTP[/SIZE]

First off you need libmtp 2.4 version.  Although this is not available for Gutsy it will be available with the next Ubuntu release, Hardy.  In the meantime the source for the Hardy release can be used and compiled in Gutsy.

Grab the source libmtp7 and install in a directory such as ~/tmp/libmtp7 :

* [Description file]("http://archive.ubuntu.com/ubuntu/pool/main/libm/libmtp/libmtp_0.2.4-1ubuntu3.dsc")
* [Source file]("http://archive.ubuntu.com/ubuntu/pool/main/libm/libmtp/libmtp_0.2.4.orig.tar.gz")
* [Diff]("http://archive.ubuntu.com/ubuntu/pool/main/libm/libmtp/libmtp_0.2.4-1ubuntu3.diff.gz")

You will need to check that these additional (Gutsy) packages are installed

1) dpkg-dev 
2) fakeroot 
3) libusb-dev
4) doxygen 
5) debhelper 
6) cdbs 
7) docbook-xsl

Compile and install as follow
```

dpkg-source -x libmtp_0.2.4-1ubuntu3.dsc
cd libmtp-0.2.4
fakeroot dpkg-buildpackage -b

```
Then install the deb files:
```

cd..
sudo dpkg -i libmtp7_0.2.4-1ubuntu3_i386.deb libmtp-dev_0.2.4-1ubuntu3_i386.deb libmtp-doc_0.2.4-1ubuntu3_all.deb mtp-tools_0.2.4-1ubuntu3_i386.deb

```

Hook up the YP-T10 to the usb port and test that mtp is working with this command:

```

mtp-detect

```

Programs such as gnomad, amorak or rythmbox wont be able to use libmtp7 without recompiling.  [Rythmbox+mtp]("http://ubuntuforums.org/showthread.php?t=385371&highlight=rhythmbox+mtp")

However, mtpfs is a program that will allow you to mount MTP device and use it  like an UMS device.  This will allow for copying and deleting of files on the YP-T10.

These additional (Gutsy) packages need to be installed:

1) libfuse2
2) libfuse-dev
3) libglib2.0


Grab the source for [mtpfs]("http://www.adebenham.com/mtpfs/") then extract and compile:

```

tar xzf mtpts-0.7.tar.gz
cd mtpts-0.7.orig
./configure
make
sudo make install

```

I created a directory in my home called T10 to mount the YP-T10 file system on.
```

mkdir ~/T10

```

To mount issue this command replacing <username> with your home directory name.
```

mtpfs /home/<username>/T10

```

To unmount the system type
```

fusermount -u /home/<username>/T10

```

I found it convenient to create 2 launchers on my gnome panel so that a mouse click is all that is required to mount and umount the T10 filesystem.  So add two custom application laucher to the gnome panel each containing one of the commands as above.

Although you can drag and drop or delete files using Nautilus this seems to create a problem when doing the same with video files directly into the Video folder.   I think this may be to do with the preview facility in Nautilius.  Therefor avoid opening the Video folder, just drop files onto the Video folder in the T10 directory or copy or delete video files using terminal commands, eg:
```

cp /home/<username>/film/InMyMerr1932.svi /home/<username>/T10/Video

```

[SIZE="5"]SVI video file format[/SIZE]

To quote from the YP-T10 manual:

&#8220;What is SVI?
Samsung Audio Video interleaving(SVI) is a new video format developed and
controlled by Samsung."

This appears to be incorrect.  Let me quote [joco]("http://jocohp.hu/?o=user_post&id=58&l=1") who appears to be the first to blog about this:

&#8220;That's just hilarious! Here's the fact: it's just a simple AVI, with a few restrictions."

[joco]("http://jocohp.hu/?o=user_post&id=58&l=1") goes on to explain how you can use avidemux to encode video files into the svi format for the YP-P2.

This same encoding works also for the T10 but rather than use avidemux I prefer to use the command line and mencoder.  It is also possible to use ffmpeg but the ubuntu default does not have the xvid codec and would therefore require compiling from source.

To use mencoder it is best to use a profile to store the required options.  Copy this profile into say gedit and save as .mplayer/mencoder.conf in your home directory:
```

[svi]
fps=30
srate=44100
mc=0.1
oac=mp3lame=true
lameopts=cbr=true:br=128
ovc=xvid=true
xvidencopts=fixed_quant=4:max_bframes=0:quant_type=h263
profile-desc="fps=30 srate=44100 mc=0.1 oac=mp3lame=true lameopts=cbr=true:br=128 ovc=xvid=true xvidencopts=fixed_quant=4:max_bframes=0:quant_type=h263"


```

The meaning of the parameters can be looked up using the ubuntu help on mplayer or reading the joco blog.  The only unusual addition is the mc which is the maximum A-V (audio-video) sync correction per frame.  For some reason there seems to be a default value of about 0.065 for mencoder but I have found some videos require higher values.  Setting this to a higher value appear to remove the problem of the audio getting out of sync with the video.  It may require values higher than 0.1.

Finally convert a file to the svi format by a command such as this:
```

mencoder InMyMerr1932.avi -o InMyMerr1932.svi -profile svi -vf scale=320:240,harddup

```
The reason for not putting the -vf scale=320:240 in the profile is that the width or height can be less than 320 or 240 respectively and the T10 doesnt seem to mind.  This allows the aspect ratio to be preserved.  (Harddup is used to force duplicate frames to be encoded avoiding some A-V sync problems).

[SIZE="4"]Examples:[/SIZE]

With a video eg "InMyMerr1932.avi" that has a width of 500 and height of 200. To preserve the aspect ratio use:
```

mencoder InMyMerr1932.avi -o InMyMerr1932.svi -profile svi -vf scale=320:128,harddup

```
To keep the maximum resolution you could also crop the width.  This would keep the central part of the movie:
```

mencoder InMyMerr1932.avi -o InMyMerr1932.svi -profile svi -vf crop=320:200,scale=320:200,harddup

```
Finally if the movie was higher than wide it can be rotated counterclockwise by 90 degrees and viewed sideon:
```

mencoder InMyMerr1932.avi -o InMyMerr1932.svi -profile svi -vf rotate=2,scale=320:240,harddup

```

[SIZE="5"]Acknowledgements[/SIZE]

["]Michael Simon]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1406219) for showing how to &#8220;retroport" libmtp.

[joco]("http://jocohp.hu/?o=user_post&id=58&l=1") for blogging about the Samsung &#8220;new" video format.

The folkes who contribute to the development of libmtp and mplayer.

---

### Post by 3calm on 2007-12-31
This is fantastic, thanks for posting this info!  What should I do with the diff file if anything?  I'm trying to get this to work with a YP-U3J.  I can view the contents of the player but can't read/write from/to the device.  Any help or advice is greatly appreciated. When I try to delete a file I get "Generic Error" with no other detail in the dialog.  I can happily provide more info if you need, just let me know where to look.

---

### Post by soviet911 on 2007-12-31
im trying to follow your derections and got stuck when putting in this command 
fakeroot dpkg-buildpackage -b
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is

i did the first two corectly, help plz

---

### Post by sornen on 2008-01-02
This message would be consistent with not being in the libmtp-0.2.4 directory after extracting the archive.

---

### Post by sornen on 2008-01-02
/etc/udev/libmtp7.rules list the UP-U3 so I would expect it should handle the same as the YP-T10.

Sorry unable to help much more as had nothing to do with either the libmtp package or mtpfs.

---

### Post by sornen on 2008-01-02
The Samsung T10 is ideal for playing youtube videos since both have a screen size of 320x240.  You can use [youtube-dl]("http://www.arrakis.es/~rggi3/youtube-dl/") to download youtube videos.

Put this script in your download directory.  To convert from flash to svi copy the following script to a text editor and save as flv2svi.sh.  Change the permission to execute and execute this command
```

chmod 755 flv2avi.sh
sh flv2svi.sh *.svi

```

This will convert any flv files that have not been converted into svi files.  There seems to be a A-V sync error after d/l the files of about 0.55 s which is compensated in mencoder with the -delay .55 parameter.

flv2svi.sh
```

#!/bin/sh     
MENC_OPTS="-delay .55 -profile svi -vf scale=320:240,harddup"
while [ "$1" ]; do
	echo "$1"
	SVI=`basename $1 .flv`.svi
	if test -e "$SVI"; then
		shift
		continue
	fi
	if file "$1" | grep -q "Macromedia Flash Video"; then
        mencoder "$1" $MENC_OPTS -o "`basename $1 .flv`.svi"
	else
		echo "$1 is not Flash Video. Skipping"
	fi
	shift	
done

```

Acknowledgements

[linux.com]("http://www.linux.com/articles/56642")

---

### Post by heidfirst on 2008-01-02
Thanks for the Howto, my  new T10 is working beautifully with ubuntu.

Gordon

---

### Post by 3calm on 2008-01-02
> **sornen said:**
> /etc/udev/libmtp7.rules list the UP-U3 so I would expect it should handle the same as the YP-T10.

Sorry unable to help much more as had nothing to do with either the libmtp package or mtpfs.

I appreciate the effort all the same.  At least it gives me some hope of getting it working.

---

### Post by foxx on 2008-01-02
In my PPA is libmtp 0.2.4 available and rhythmbox 0.11.4 and gnomad2 2.9.0 compiled against it too. Simply add my Repo and download the applications you need:

[http://ubuntu.jbbr.net/](http://ubuntu.jbbr.net/) (Repository overview with instructions)

foxx

---

### Post by jfrice on 2008-01-02
> **foxx said:**
> In my PPA is libmtp 0.2.4 available and rhythmbox 0.11.4 and gnomad2 2.9.0 compiled against it too. Simply add my Repo and download the applications you need:

[https://launchpad.net/~jbbr/+archive](https://launchpad.net/~jbbr/+archive) (PPA in Launchpad)
[http://blog.jbbr.net/ubuntu-pakete/](http://blog.jbbr.net/ubuntu-pakete/) (Overview about my packages - German!)

mtpfs will be available soon but some hours ago I found a hacked UMS-firmware for my MTP device so I'm unable to test it.

foxx

Just added your repo and updated rhythmbox - where does one find there mtp devices?

---

### Post by jfrice on 2008-01-02
Also ,

I have an yp-S5 as far as I can see its just a yp-T10 with speakers. Anyway i'm having the same issue as 3calm. I can mount the device & browse it. But I cant delete files, copy files or play them off the device. I just keep getting a "generic error".

I followed this guide line by line. Has anybody got a clue? I'm pulling my hair out.

Thanks.

J

---

### Post by foxx on 2008-01-03
> **jfrice said:**
> Just added your repo and updated rhythmbox - where does one find there mtp devices?

What is the output of "mtp-detect"? Did you activated the MTP Plugin in Rhythmbox? Have you tryed Gnomad2?

@ All:
In the following Thread you find a hacked Firmware which enables the T-10 to use UMS so you can access it like a memory stick:
[http://www.anythingbutipod.com/forum/showthread.php?t=21463](http://www.anythingbutipod.com/forum/showthread.php?t=21463)

You can use my german tutorial: [http://blog.jbbr.net/2008/01/03/umsmsc-fur-den-samsung-yp-t10/](http://blog.jbbr.net/2008/01/03/umsmsc-fur-den-samsung-yp-t10/)

---

### Post by jfrice on 2008-01-03
> **foxx said:**
> What is the output of "mtp-detect"? Did you activated the MTP Plugin in Rhythmbox? Have you tryed Gnomad2?

@ All:
In the following Thread you find a hacked Firmware which enables the T-10 to use UMS so you can access it like a memory stick:
[http://www.anythingbutipod.com/forum/showthread.php?t=21463](http://www.anythingbutipod.com/forum/showthread.php?t=21463)

You can use my german tutorial: [http://blog.jbbr.net/2008/01/03/umsmsc-fur-den-samsung-yp-t10/](http://blog.jbbr.net/2008/01/03/umsmsc-fur-den-samsung-yp-t10/)

mtp-detect gives a massive output seems to be working. I have activated the mtp plugin for Rhythmbox. I presume it would be obvious if it works. No luck with gnomad2 either.

I just installed amarok as we speak and it connects fine and I can send files and they play.

Thanks for the reply.

---

### Post by Dr.Suave on 2008-01-09
When I type ./configure to install mtpfs it starts to look like it's going well, but then gets to this:

```
checking for FUSE... configure: error: Package requirements (fuse >= 2.2                         glib-2.0 >= 2.6                         gthread-2.0 >= 1.2                         mad >= 0.15                         id3tag >= 0.15                         libmtp >= 0.0.9) were not met:

No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'mad' found
No package 'id3tag' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables FUSE_CFLAGS
and FUSE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

What can I do?

---

### Post by sornen on 2008-01-12
Install the packages that are missing.

---

### Post by Framp on 2008-01-14
Has anyone managed to get this howto working with an yp-t9?
I'm the owner of a yepp-t9 and I'm not able to convert anything on my pc.

Unsupported file.. ghhhhh damned samsung.

Can somebody show me a video file that's currently running on a t10? (maybe on mediafire or something similar)
I think t10 svi is far different than the t9 one :(
Thanks in advance

Regards
Framp

---

### Post by sornen on 2008-01-14
Firmware version 1.6 is supposed to make it a UMS device.

[http://www.anythingbutipod.com/forum/showthread.php?t=9337](http://www.anythingbutipod.com/forum/showthread.php?t=9337)

---

### Post by svit on 2008-01-16
I'm writing programm to convert video to svi format [svicoder]("http://sourceforge.net/projects/svicoder/") could you test it and [feedback]("http://sourceforge.net/tracker/?group_id=213426")?

---

### Post by foxx on 2008-01-16
> **sornen said:**
> Firmware version 1.6 is supposed to make it a UMS device.

[http://www.anythingbutipod.com/forum/showthread.php?t=9337](http://www.anythingbutipod.com/forum/showthread.php?t=9337)

Yes, but it's for the T-9...

[QUOTE=svit]I'm writing programm to convert video to svi format svicoder could you test it and feedback?[/QUOTE]

Thank you, I will try that

---

### Post by heidfirst on 2008-01-16
Hi Svit,

Have just tried your svicoder to re-encode some small mpg files that I have for my T10 and initial impressions are very good.  Many thanks for this.

Hopefully over the next few days I can convert some more files.

Gordon

---

### Post by sornen on 2008-01-17
> **foxx said:**
> Yes, but it's for the T-9...



Yes, but I was replying to the post above...

---

### Post by Framp on 2008-01-17
Thank you but i'm using another ums firmware on my yp-t9 (1.80)

I'm just wondering how I can convert some videos to make them run on my t9

svicoder doesn't work with t9 :(

---

### Post by whirlybird on 2008-01-17
I am still bit of a noob and really would like to get my Samung T10 to work without changing the Firmware.  So could someone please break this Howto down a bit more for me? Where do I get the libmtp 2.4 version from? then the libmtp7? For the first code section do I copy and paste the entire thing into terminal or just one line at a time? for the second code section (installing the deb files) the "cd.." what is this for? 

Thanks in advance!

---

### Post by foxx on 2008-01-18
1. Add my repo by executing the following in a terminal:
```
sudo wget http://ubuntu.jbbr.net/gutsy.list -O /etc/apt/sources.list.d/jbbr.list
wget -q http://ubuntu.jbbr.net/jbbr_ubuntu.asc -O- | sudo apt-key add - && sudo apt-get update
```

2. Do a upgrade with the update-manager or "sudo apt-get upgrade"
Rhythmbox will be updated and libmtp7 will be installed
Now you can see your device in rhythmbox and use it if you enable the MTP plugin

3. To sycronize videos etc. you need gnomad2. It's in my repository too. Simply install the packge "gnomad2".

---

### Post by foxx on 2008-01-18
Hello,

I added now mtpfs to my Ubuntu repository. It's not my own package - I used[ the package by Chris Lamb]("http://packages.debian.org/sid/mtpfs") from Debian. Thank you!
It's from SVN revision 11 which fixes a memory leak. It works very fine with my T10 (Bether than gnomad2).

Simply add my repository:

```
sudo wget http://ubuntu.jbbr.net/gutsy.list -O /etc/apt/sources.list.d/jbbr.list
wget -q http://ubuntu.jbbr.net/jbbr_ubuntu.asc -O- | sudo apt-key add - && sudo apt-get update
```

(More information on [http://ubuntu.jbbr.net/](http://ubuntu.jbbr.net/))

and install mtpfs:

```
sudo apt-get install mtpfs
```

You should also do a upgrade with the update-manager or with apt-get:

```
sudo apt-get upgrade
```

This should also upgrade rhythmbox to 0.11.4 compiled against libmtp 0.2.4. Gnomad2 is also available in repository.

Have fun!

News about the hacked UMS firmware: There is now also a hacked firmware available which switches from UMS/MSC to MTP. So you can try and revert if it does not work as expected. But it's still really something you do on your own risk.

* [Post with hacked firmware from MTP to UMS/MSC]("http://www.anythingbutipod.com/forum/showpost.php?p=199128&postcount=46")
* [Post with hacked firmware from UMS/MSC to MTP]("http://www.anythingbutipod.com/forum/showpost.php?p=202765&postcount=95")

foxx

---

### Post by whirlybird on 2008-01-18
foxx,

I added your repository (the newest one with mtpfs) and followed your steps but I get this when I do mtp-detect:

libmtp version: 0.2.4

Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device 1
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1561
Detect: There has been an error connecting. Exiting

What did I forget?

Thanks

---

### Post by foxx on 2008-01-19
It looks like "usb_claim_interface(): Device or resource busy" is the error. Did you had any other applications running which uses libmtp? I think when you mountet your device with mtpfs, mtp-detect will not work anymore. Try to close all applications like mtpfs, rhythmbox, gnomad2, disconnect your device and try again.
In another forum someone was only able to run mtp-detect with sudo. You could try this too.

foxx

---

### Post by svit on 2008-01-19
Hi, Framp.
> **Framp said:**
> svicoder doesn't work with t9 :(
try [svicoder v0.6]("http://sourceforge.net/project/showfiles.php?group_id=213426&package_id=257181&release_id=569725"). It should work with your player!

---

### Post by foxx on 2008-01-19
> **svit said:**
> Hi, Framp.

try [svicoder v0.6]("http://sourceforge.net/project/showfiles.php?group_id=213426&package_id=257181&release_id=569725"). It should work with your player!

Thank you, it also fixes my flv problem - but something else:

I would like to make a ubuntu package for svicoder. But there is one problem: The install script selects which resolution should be used. So I must create an own package for every player combination.... Not that good ;)
Maybe you could make one install script which allows selecting a prefix and simply installes the script and move the player selection to the script itself? I take a look at your script and try to write a patch but it would be nice to have this upstream.

foxx

EDIT: Sorry, I saw that it's already implemented in the script itselfs. So I only have to patch the install script.

---

### Post by foxx on 2008-01-19
Okay I build now a package for svicoder 0.6. It uses the default settings for YP-T8 / YP-T10 but you can change it by editing /etc/svicoder/default or appending "-p <1-8>" to svicoder.

1-8 must be changed like that:

> 1) yp-p2,ym-pd1     3) yp-s5,yp-t9      5) yp-t7f           7) yh-j50,sc-mx10
2) yp-t8,yp-t10     4) yp-t8,yp-d1      6) yh-j70           8) sdc-k65,sdc-k60

Like all the other packages you will find it in my repository [http://ubuntu.jbbr.net/](http://ubuntu.jbbr.net/) . There is also the source package available. The source is still the same but I wrote a patch which replaces the installer with a new one which makes it possible to use with debuild.

Link to deb: [http://ubuntu.jbbr.net/packages/dists/gutsy/main/binary-all/graphics/svicoder_0.6.0-1~jbbr1_all.deb](http://ubuntu.jbbr.net/packages/dists/gutsy/main/binary-all/graphics/svicoder_0.6.0-1~jbbr1_all.deb)

foxx

---

### Post by Framp on 2008-01-24
sorry to say that the yp-t9 svi format is not as the other;

Your svicoder doesn't work because svi has a slightly different container :(
Changing resolution doesn't do the trick

thanks for your work

regards

---

### Post by foxx on 2008-01-27
I update the svicoder package to 0.7.1

[http://ubuntu.jbbr.net/packages/dists/gutsy/main/binary-all/graphics/svicoder_0.7.1-1~jbbr1_all.deb](http://ubuntu.jbbr.net/packages/dists/gutsy/main/binary-all/graphics/svicoder_0.7.1-1~jbbr1_all.deb)

---

### Post by yahoo on 2008-02-17
Thanks foxx, installed and used your svicoder to convert video for my Samsung YP-T10.
Worked perfectly.

I had used this thread:
[http://www.anythingbutipod.com/forum/showthread.php?t=24737](http://www.anythingbutipod.com/forum/showthread.php?t=24737)
to mount hte YP-T10 and just copied the .svi video file to it without a problem.

Yahoo

---

### Post by svit on 2008-02-17
> **Framp said:**
> sorry to say that the yp-t9 svi format is not as the other;

Your svicoder doesn't work because svi has a slightly different container :(
Changing resolution doesn't do the trick

thanks for your work

regards

let's solve this problem together.  please open tracker item [here]("https://sourceforge.net/tracker/?group_id=213426"), and explain your problem, attach svicoder output.

---

### Post by svit on 2008-02-17
let's move svicoder-related discussions [here]("https://sourceforge.net/forum/?group_id=213426"), this thread has different topic

---

### Post by samiscooking on 2008-04-25
> **svit said:**
> I'm writing programm to convert video to svi format [svicoder]("http://sourceforge.net/projects/svicoder/") could you test it and [feedback]("http://sourceforge.net/tracker/?group_id=213426")?
Hi, I Tried jsvicoder and I post you a comment in the forum section of sourceforge. I retype here my problem: with your script or with jsvicoder I listen only noise after converting flv to svi. I hope someone can help me, bye

---

### Post by Kcrsh10 on 2008-04-27
I am following your instructions but keep on getting the following message:

:~$ dpkg-source -x libmtp_0.2.4-1ubuntu3.dsc
dpkg-source: error: cannot open .dsc file ./libmtp_0.2.4-1ubuntu3.dsc: No such file or directory
~$ cd libmtp-0.2.4
bash: cd: libmtp-0.2.4: No such file or directory
~$ fakeroot dpkg-buildpackage -b
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: failure: tail of debian/changelog gave error exit status 1

Any ideas as to why or how to rectifiy this? im using hardy and any help would be appreciated!

---

### Post by Headly B on 2008-04-28
Hi,

I'm pretty new to linux and had pretty much given up on getting my T10 to work (also have a Windoze machine so wasn't too bothered). However Since 8.04 released things are much simpler for noobies like me because the libmtp and mtpfs packages are already installed. So the very first message of this thread is now simplified as you can skip everything before the directions for mounting and unmounting the T10 ("I created a directory in my home called T10 to mount the YP-T10 file system on...")
However at this stage I did come across a problem. When I tried to mount the T10 using the directions supplied I got an error (premission denied...fuse..blah...blah). The solution is to make sure that your user is in the "fuse" group which wasn't obvious to me at the time. To do this:
system\administration\users and groups\manage groups. Make sure your user is ticked as a user in the "fuse" group. [COLOR="black"][COLOR="Black"]_then restart Ubuntu_[/COLOR][/COLOR]. If this doesn't work in a terminal write "sudo usermod -a -G fuse <username>"
Then: make sure tho reboot Ubuntu before you try again (that one got me for a while...)
Hey presto! It works!

Headly

---

### Post by Headly B on 2008-05-09
Hi,

Has anyone noticed a problem with using MTPFS since release of the Hardy Heron? Initially all worked well for me after upgrading to 8.04 but now, when I try to access the music or pictures folders on my T10 (using Nautilus) I get this error message:
"Couldn't display "/home/fintan/T10/Music".
Error: Error stating file '/home/fintan/T10/Music': Transport endpoint is not connected
Please select another viewer and try again." :confused:
However in the Terminal I can navigate into these directories and copy files to and from them.
It seems to have been caused by some updates since 8.04 was initially released.

Headly B

---

### Post by waynemcl on 2008-06-24
Hi,

Samsung T10:

I used to have mtp running on my old ubuntu 7.10. I blew away my system, installed 8.04, moved my homedir over.

I've installed mtp, Rhythmbox seems to be able to see the device.

When I shut off Rhythmbox, re-connect the device, try mtp-detect, I get a number of ok looking status messages, then:

[FONT="Fixedsys"]WMPInfo.xml Does not exist on this device
PTP: Closing session
inep: usb_get_endpoint_status(): Connection timed out
outep: usb_get_endpoint_status(): Connection timed out
usb_clear_halt() on IN endpoint: Connection timed out
usb_clear_halt() on OUT endpoint: Connection timed out
usb_clear_halt() on INTERRUPT endpoint: Connection timed out
OK.[/FONT]

I can't see desktop shortcuts or the device in Nautilus.

Then, Gnomad2 doesn't seem to see the device, but Rhythm box does, and is able to update playlists.

I's like to get a TopGear episode to the device. Any thoughts folks?

Cheers, Thanks, W

---

### Post by twomoons on 2008-06-25
Works a treat with 8.04.  didn't have to install everything listed as it was already installed.

Using it on my work laptop and am now even closer to moving my main pc rig at home from Windoze.

Thanks again

---

