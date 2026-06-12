---
title: "shn music codec installation"
date: 2009-02-20
forum: Multimedia Software
---

### Post by cozmicharlie on 2009-02-20
This tutorial is an update to the tutorial I wrote for Hardy ([http://ubuntuforums.org/showthread.php?t=739658](http://ubuntuforums.org/showthread.php?t=739658)).  It simplifies the steps and utilizes more command line than the previous tutorial.  If you are new to Linux, I know the thought of using the command line can be daunting - as they say in the HitchHikers Guide to the Galaxy - "Don't Panic!".  Using the command line greatly simplifies the installation process.

Some background on the shn codec.  It is a lossless codec and one of the early codecs used for trading lossless music.  It has largely fallen out of favor because of the lack of development and has been supplanted by better lossless codecs such as flac (better in the sense that you can do more with flac such as tagging - not better quality).  However, it is still used extensively in the lossless trading community.  Unfortunately, not many players in Linux support shn.  One of the few is XMMS (see this tutorial ([http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)).  Also, the newer version of ffmpeg does support shn (a search of the forum will reveal tutorials using ffmpeg).  You have a couple options for converting shn to other formats such as PACPL and SoundKonverter ([http://ubuntuforums.org/showthread.php?t=712064](http://ubuntuforums.org/showthread.php?t=712064)).  All rely on having the shn codec installed.

For this tutorial we are using the shn codec available from etree. The steps are simple:

Open a terminal
Type or copy and paste the following commands at the prompt
[LIST=1]
[*]Download the shn codec file from etree.  This will download to your home folder.  If you want to download to another folder then you will need to change the commands.
```
$ wget http://www.etree.org/shnutils/shorten/dist/src/shorten-3.6.1.tar.gz
```
[*]untar the downloaded folder
```
$ tar xvf /home/yourhomefolder/shorten-3.6.1.tar.gz
```
[*]Change directories to the untarred folder
```
$ cd /home/yourhomefolder/shorten-3.6.1
```
[*]Install the shn codec
```
$ ./configure
```
```
$ make
```
```
$ sudo make install
```
[/LIST]

That's it - fairly painless.

Enjoy!

---

### Post by ytowndan on 2009-11-19
Thanks for these guides!  I'm still fairly new to Ubuntu, so this will make it much easier for me (although, I'm sure I'll still need about 20 google tabs open ;)).  

I have a couple TB of Phish and GD (many of the older sources are shn).  I've been running foobar under crossover, so I can have shn playback, but I'd like to go native if possible.  As I mentioned above, I'm still pretty new to Ubuntu, and before I attempt this I have one question.  Will XMMS give me gapless playback with shn?  As I'm sure you know, there's no bigger annoyance than a big old gap ruining a segue.  

Thanks,
-Dan

---

