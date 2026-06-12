---
title: "Can someone help install FFmpeg + FFmpeg-PHP + Mplayer + Mencoder + flv2tool?"
date: 2009-02-05
forum: Multimedia Software
---

### Post by dmphotography on 2009-02-05
Hey there,

I've spent hours and hours trying to get these installed and so far I haven't had any luck.  I'm getting random errors during compiling them and I can't find a tutorial for Ubuntu 8.10.  Most of the tutorials I've found either refer to commands that aren't included with Ubuntu 8.10 or old packages for installing the above items that don't work.

I would be forever grateful to the first person that helps me get those installed, because I've wasted so many hours trying and only finding it unsuccessful yet again.

Thanks in advance.

---

### Post by amauk on 2009-02-05
any reason you're not using the ones in the repositories....?

---

### Post by redroad55 on 2009-02-05
this is the command line for what you want except the ffmpeg-php which I do not find in synaptic ..>   sudo apt-get install FFmpeg Mplayer Mencoder flv2tool  
if you have any questions post back ..Best to you

---

### Post by mozkill on 2009-02-05
Once you get a fresh linux system up and running, back it all up with Clonezilla  and then restart the system and then experiment with the command that the previous poster gives....  if it fails you can restore to the backup and try something else.

---

### Post by FakeOutdoorsman on 2009-02-06
> **redroad55 said:**
> this is the command line for what you want except the ffmpeg-php which I do not find in synaptic ..
ffmpeg-php is called php5-ffmpeg in the repository.  Also, flvtool is called flvtool2 in the repository.  Assuming you are using 8.10 (Intrepid) you will also need the libavcodec-unstripped-51 package if you want to enable restricted formats in ffmpeg.  So everything together will be:
```
sudo apt-get install ffmpeg libavcodec-unstripped-51 php5-ffmpeg mencoder mplayer flvtool2
```

More experienced users may want a recent and more customizable version of FFmpeg complete with the libx264 presets and other goodness not available in the ancient release of FFmpeg from the repository:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by dmphotography on 2009-02-06
> **amauk said:**
> any reason you're not using the ones in the repositories....?

Well do forgive me, because I'm really not very familar with Linux at all.  I'm just now starting to get comfortable with the permissions part and the use of console, which I haven't used anything like is since MS-DOS.  I've used nothing but Windows for the past serveral years, so it's taking me a little bit of time grasping how Linux works.  I still don't fully grasp how it all comes together on a lot of different topics, but I'm getting closer.


> **redroad55 said:**
> this is the command line for what you want except the ffmpeg-php which I do not find in synaptic ..
if you have any questions post back ..Best to you

And that's it?  I'm trying to install a video script like phpmotion on an XAMPP server to experiment with and I just don't understand how it works with Linux.  I wrote just about the only tutorial on the net explaining how to install all of those for Windows, but that was easy.  Haha.  Linux is a whole different nightmare.  If it weren't for so many different distro's of Linux with each of them having a slightly different way of doing things, then add in the out-dated documents, I might be able to figure this out a little easier.  But when you know nothing about Linux and everything you read differs from what you just finished reading, it's down right confusing as crap.

I'll try that and see if I can get it to work.  I don't think the ffmpeg-php is going to be a major issue, because theoretically it should be platform independent since it pertains to PHP and not the OS.

If I can do this successfully, it's going to be my personal quest to really learn this part and keep an updated resource online that'll hopefully spare people the headache I've gone through while trying to install it.

P.S.  I followed that tutorial you linked and successfully installed it, but that doesn't mention over half of the other things I need installed.  The problem is I don't know how they all tie together, so I'm a bit lost on that part.
I still need FFmpeg-PHP + Mplayer + Mencoder + flv2tool after that tutorial, which I know Mplayer and Mencoder are both executable files that are some what optional and are stand-alone apps and not dependent on anything but perhaps the codecs for the MPlayer.

---

### Post by FakeOutdoorsman on 2009-02-06
> **dmphotography said:**
> I still need FFmpeg-PHP + Mplayer + Mencoder + flv2tool after that tutorial, which I know Mplayer and Mencoder are both executable files that are some what optional and are stand-alone apps and not dependent on anything but perhaps the codecs for the MPlayer.
I gave you the command in my above post to install everything you requested from the repository.  No compiling needed.  I recommend using everything from the repository until you're more comfortable with Linux.

---

### Post by dmphotography on 2009-02-06
> **FakeOutdoorsman said:**
> I gave you the command in my above post to install everything you requested from the repository.  No compiling needed.  I recommend using everything from the repository until you're more comfortable with Linux.

You did and I apologize for that.  When I was posting my reply, I scrolled over your post on accident and proceeded to quote redroad55, completely overlooking your post.

It wouldn't be so difficult dealing with Linux if I knew where it puts stuff when you install it and had a little better understanding of the differences in builds and distros of Linux.  Also, how do you find where to get the packages you need, like the ones you posted above?  Is there some secret website that tells you that or what?  


I know the simple answer would be read a book on Linux, but that'd be like saying read a book on Windows and it just isn't going to happen.  I hate reading for one and secondly, I COULD live without Linux, which creates a lack of desire to invest an overwhelming amount of time and effort into extensively learning it.  

That sounds lazy, but I never have read any books on Windows and I can troubleshoot and do just about anything I need to in it and I have the same attitude towards other OSs as well.  Crap, all I ever read on MS-DOS was the commands I needed and skipped the boring stuff and managed just fine.  I honestly don't see why Linux is still so dependent on the command prompt and doesn't simplify things by making it secondary like Windows, or is that what makes Windows so vulnerable?

Thanks again for your help!

---

### Post by redroad55 on 2009-02-06
The thing to do here is to be clear about what your comfortable with and in your posts take the time to point out whether you are comfortable with command line or you would be better served with a GUI .. The more specific you can be in your posts the easier it will be to help you .. That being said .. Most everything you have downloaded will show up in these places ..applications > system >
and or admin. or preferences .. Your terminal is located in Applications > accessories ... Don't be afraid to state what you don't know .. The general attitude of most on this forum is to be helpful and of course that secret desire to give it to microsoft ..Best to you

---

### Post by FakeOutdoorsman on 2009-02-06
> **dmphotography said:**
> It wouldn't be so difficult dealing with Linux if I knew where it puts stuff when you install it...
You can use the "whereis" command to find out where the binary was installed:
```
[frink@hedron ~]$ whereis ffmpeg
ffmpeg: /usr/local/bin/ffmpeg
```
System -> Administration -> Synaptic Package Manager can tell you where the files from an installed package are.  Right click on the package name -> Properties -> Installed Files.
> Also, how do you find where to get the packages you need, like the ones you posted above?  Is there some secret website that tells you that or what?
I wasn't running Ubuntu at the time when I replied so I used the [Ubuntu Packages Search](http://packages.ubuntu.com/) site.  I knew the names of most of the packages, but for php5-ffmpeg I just searched for ffmpeg because I didn't know the exact name.  You can have similar functionality in Synaptic Package Manager with the Quick Search.  Alternatively, you can go into the terminal and:
```
apt-cache search package_name
```
> That sounds lazy, but I never have read any books on Windows and I can troubleshoot and do just about anything I need to in it and I have the same attitude towards other OSs as well.  Crap, all I ever read on MS-DOS was the commands I needed and skipped the boring stuff and managed just fine.  I honestly don't see why Linux is still so dependent on the command prompt and doesn't simplify things by making it secondary like Windows, or is that what makes Windows so vulnerable?
You'll learn best by just using it and you can do must things without touching the command-line.  The forum is also one of the best places to learn.  The [Ubuntu Wiki](https://wiki.ubuntu.com/) and [Ubuntu Documentation](https://help.ubuntu.com/) may be useful.

---

### Post by dmphotography on 2009-02-06
You two both are awesome people!  Thank you very much for the help and feedback!

---

### Post by dmphotography on 2009-02-06
Ok, so here's the problem now.  the php5-ffmpeg doesn't install or create the ffmpeg-php that I need.  it should be a pre-compiled extension for PHP5, which the only thing I can find is one that must be compiled.  Here's two links explaining the method.

[http://ffmpeg-php.sourceforge.net/](http://ffmpeg-php.sourceforge.net/) 
This is the ffmpeg-php project.  If you scroll down, it mentions the steps to compile it, but I get an error about the ffmpeg headers missing or something like that.  

[http://escapegoat.org/2007/11/11/installing-ffmpeg-php-on-ubuntu-7-10](http://escapegoat.org/2007/11/11/installing-ffmpeg-php-on-ubuntu-7-10)
This one explains how to compile it, but it's out-dated.  There's two command lines that I've corrected here:

```
apt-get install libmp3lame-dev libfaad-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libx264-dev libdts-dev libgsm1-dev libvorbis-dev libdc1394-13-dev checkinstall build-essential gcc 
```
The new liblame-dev is libmp3lame-dev

```
./configure --enable-gpl --enable-pp --enable-libvorbis --enable-liba52 --enable-libdc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-pthreads --enable-libx264 --enable-shared --prefix=/usr
```

There were some missing the "lib" in the front of them.  The --enable-libogg option is no longer a valid option for the ./configure command.

I cannot successfully compile this, so if someone can either detail the method of how to compile this php extension or even better, upload/link it for me, I'd be forever grateful.  The result of this should be a file called ffmpeg_php and I don't know what the extension will be.  For Windows, it was ffmpeg_php.dll, but I think it's .so for Linux.

Anyways, that's for the help!

---

### Post by FakeOutdoorsman on 2009-02-06
I assumed you were using Ubuntu Intrepid 8.10.  What version are you using?

---

### Post by dmphotography on 2009-02-06
I am using Ubuntu 8.10.  I'm using XAMPP for my Apache, PHP, and MySQL install.  When I checked my phpinfo, there wasn't the ffmpeg-php listed there.  Did it create it somewhere else?  When I did the whereis php5-ffmpeg, it doesn't show a directory for it, which I assumes means it wasn't installed?

---

### Post by dmphotography on 2009-02-07
Ok, after spending a nice 10+ hours on this, I've got it figured out and I have a much better understanding now that I see how it all comes together.  I had to add the --enable-shared to step 5 of this guide [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) in order to compile the ffmpeg-php .  

There is a problem with ffmpeg-php that apparently others are having too. I believe it's an issue associated with the latest ffmpeg, but I'm not sure.  

I've posted my notes for my install and the final error at the bottom of it.
[http://www.myownserver.info/notes/index.php/2009/02/install-ffmpeg-ffmpeg-php-mplayer-mencod-10?blog=1](http://www.myownserver.info/notes/index.php/2009/02/install-ffmpeg-ffmpeg-php-mplayer-mencod-10?blog=1)

If anyone has any ideas or solutions, please let me know.

---

