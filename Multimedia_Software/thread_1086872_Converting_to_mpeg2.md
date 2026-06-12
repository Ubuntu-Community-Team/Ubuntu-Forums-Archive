---
title: "Converting to mpeg2"
date: 2009-03-04
forum: Multimedia Software
---

### Post by Geffers on 2009-03-04
I need to convert some .mov files to mpeg2 to play on a specific device.

I have tried mencoder but this appears to convert to mpeg4 by default and I am unsure how to choose mpeg2, if indeed this is an option.

Any advice would be appreciated ;)

Geffers

---

### Post by Fire_Chief on 2009-03-04
You could try tovid for this. It uses ffmpeg or mpeg2enc to perform the conversions. I'd also recommend Handbrake. Both are available in the repositories.

-Cheers!

---

### Post by Geffers on 2009-03-04
> **Fire_Chief said:**
> You could try tovid for this. It uses ffmpeg or mpeg2enc to perform the conversions. I'd also recommend Handbrake. Both are available in the repositories.

-Cheers!

Thanks, I'll give one or the other a try.

Geffers

---

### Post by andrew.46 on 2009-03-04
Hi,

There are some very keen FFmpeg users on these forums so if you have a go with FFmpeg you should get plenty of support. If you are using Intrepid:

```
sudo apt-get install ffmpeg libavcodec-unstripped-51
```

will get what you need. Then find one of your files and examine it with FFmpeg:

```
ffmpeg -i myfile.mov
```

This will demonstrate the exact makeup of the file and from there it is a simple matter to convert. You could always post the results here and I am sure some skilled person can guide you from there :-).

All the best,

Andrew

---

### Post by Geffers on 2009-03-05
> **andrew.46 said:**
> Hi,

There are some very keen FFmpeg users on these forums so if you have a go with FFmpeg you should get plenty of support. If you are using Intrepid:

```
ffmpeg -i myfile.mov
```

You could always post the results here and I am sure some skilled person can guide you from there :-).

Andrew

Andrew,

This is my output from file QE2.mov

geoff@Columbia:~/Desktop$ ffmpeg -i QE2.mov
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'QE2.mov':
  Duration: 00:58:10.2, start: 0.000000, bitrate: 520 kb/s
  Stream #0.0(eng): Video: h264, yuv420p, 480x272, 25.00 fps(r)
  Stream #0.1(eng): Audio: mp4a / 0x6134706D, 48000 Hz, stereo
Must supply at least one output file
geoff@Columbia:~/Desktop$ 

It appears to have been coded using h264 but I am unsure how to change it.

Geffers



Geffers

---

### Post by andrew.46 on 2009-03-05
Hi,

I am still an FFmpeg n00b so the following syntax may be corrected by others:

```
ffmpeg -i QE2.mov -vcodec mpeg2video -sameq  -ab 128k outfile.mpg
```

At the very least this should provide a start :-).

Andrew

---

### Post by Geffers on 2009-03-06
> **andrew.46 said:**
> Hi,

I am still an FFmpeg n00b so the following syntax may be corrected by others:

```
ffmpeg -i QE2.mov -vcodec mpeg2video -sameq  -ab 128k outfile.mpg
```

At the very least this should provide a start :-).

Andrew

Probably close but got this error;

Output #0, mpeg, to 'outfile.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 480x272, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: mp2, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86018 ) for input stream #0.1


Looks like the audio is a problem.

Geffers

---

### Post by FakeOutdoorsman on 2009-03-06
Looks like you're using Hardy (8.04).  I don't think FFmpeg from the Ubuntu repository can decode AAC audio.  You can remove FFmpeg, enable the [Medibuntu](http://medibuntu.org/) repository, and then install FFmpeg from that repository.  It should be able to decode AAC.

---

### Post by andrew.46 on 2009-03-06
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> Looks like you're using Hardy (8.04).  I don't think FFmpeg from the Ubuntu repository can decode AAC audio.  You can remove FFmpeg, enable the [Medibuntu](http://medibuntu.org/) repository, and then install FFmpeg from that repository.  It should be able to decode AAC.

I am amazed as always by your intimate knowledge of the limitations of the stock FFmpeg in various Ubuntu versions! Do you run them *all* on VirtualBox or you have just encountered these problems many times?

All the best,

Andrew

---

### Post by FakeOutdoorsman on 2009-03-06
> **andrew.46 said:**
> Hi FakeOutdoorsman,



I am amazed as always by your intimate knowledge of the limitations of the stock FFmpeg in various Ubuntu versions! Do you run them *all* on VirtualBox or you have just encountered these problems many times?

All the best,

Andrew
Hi Andrew,

I cheat.  For each Ubuntu release I save the output of:
```
ffmpeg -formats > ffmpegformats.txt 2>&1
```
and
```
ffmpeg -h > ffmpegh.txt 2>&1
```
I also have vanilla Hardy and Intrepid virtual machines in VirtualBox to monkey around with.  Attached are some "ffmpeg -formats" for Hardy, Medibuntu Hardy, Intrepid, and Intrepid unstripped (I've been meaning to upload these for myself when not using my usual computer).

---

### Post by Geffers on 2009-03-08
> **FakeOutdoorsman said:**
> Looks like you're using Hardy (8.04).  I don't think FFmpeg from the Ubuntu repository can decode AAC audio.  You can remove FFmpeg, enable the [Medibuntu](http://medibuntu.org/) repository, and then install FFmpeg from that repository.  It should be able to decode AAC.

That's interesting, didn't realise there would be different versions (If that is the correct description) for different installations.

I'll give that a try and report back.

Thanks,

Geffers

---

### Post by Geffers on 2009-03-09
> **FakeOutdoorsman said:**
> Looks like you're using Hardy (8.04).  I don't think FFmpeg from the Ubuntu repository can decode AAC audio.  You can remove FFmpeg, enable the [Medibuntu](http://medibuntu.org/) repository, and then install FFmpeg from that repository.  It should be able to decode AAC.

Followed those instructions, rebooted to make sure and got exactly the same error message referring to the audio;

Stream #0.1: Audio: mp2, 48000 Hz, stereo, 128 kb/s
Stream mapping:
Stream #0.0 -> #0.0
Stream #0.1 -> #0.1
Unsupported codec (id=86018 ) for input stream #0.1

Geffers :(

---

### Post by FakeOutdoorsman on 2009-03-09
> **Geffers said:**
> Followed those instructions, rebooted to make sure and got exactly the same error message referring to the audio;
Can you paste the complete FFmpeg output?  Is this video available for download for testing?

---

### Post by Geffers on 2009-03-09
> **Fire_Chief said:**
> You could try tovid for this. It uses ffmpeg or mpeg2enc to perform the conversions. I'd also recommend Handbrake. Both are available in the repositories.

-Cheers!

Tried tovid and got the same error message about the audio stream, but then as it uses ffmpeg then I suppose it would.

Geffers

---

### Post by Geffers on 2009-03-09
> **FakeOutdoorsman said:**
> Can you paste the complete FFmpeg output?  Is this video available for download for testing?

Bit big at 215MB.

Bit of history about the file, it is a download from the BBC site of the timewatch program about the QE2 using the Linux program get_iplayer which enables the program to be downloaded and played at a later time.

I have an older TV STB that actually plays mpeg2 files on my TV via it's own USB socket; hence the need to convert it.

It downloads as a mov file with the video codec shown as H.264 / AVC and the audio as MPEG-4 AAC audio.

On my windows machine I used the free video conversion software 'super' and it converted fine. For future use I would prefer to use my Linux machine for the conversions resulting in my enquiry.

Geffers

---

### Post by Fire_Chief on 2009-03-10
While tovid can use Mpeg2enc instead of FFmpeg, at this point I would suggest using Handbrake instead. It can handle AAC audio and H.264 video just fine.

-Cheers!

---

### Post by FakeOutdoorsman on 2009-03-10
> **Geffers said:**
> Bit big at 215MB.

Bit of history about the file, it is a download from the BBC site of the timewatch program about the QE2 using the Linux program get_iplayer which enables the program to be downloaded and played at a later time.

Perhaps a small section of the audio can be cut out:
```
ffmpeg -i QE2.mov -acodec copy -t 5 output.aac
```
or if that doesn't work:
```
ffmpeg -i QE2.mov -acodec copy -t 5 -vn output.mp4
```

---

### Post by Geffers on 2009-03-10
> **Fire_Chief said:**
> While tovid can use Mpeg2enc instead of FFmpeg, at this point I would suggest using Handbrake instead. It can handle AAC audio and H.264 video just fine.

-Cheers!

Couldn't find it in synaptic and on the Handbrake site it appears it is only supported in v8.10, I am still on v8.04 due to a wifi problem with v8.10

I suppose though it would work OK.

Geffers

---

### Post by Geffers on 2009-03-10
> **FakeOutdoorsman said:**
> Perhaps a small section of the audio can be cut out:
```
ffmpeg -i QE2.mov -acodec copy -t 5 output.aac
```
or if that doesn't work:
```
ffmpeg -i QE2.mov -acodec copy -t 5 -vn output.mp4
```

Right, I will do that but am busy for the next couple of days, I am not on my Linux machine at the moment so may not be able to do this till Friday.

Geffers

---

### Post by Geffers on 2009-03-10
> **FakeOutdoorsman said:**
> Perhaps a small section of the audio can be cut out:
```
ffmpeg -i QE2.mov -acodec copy -t 5 output.aac
```
or if that doesn't work:
```
ffmpeg -i QE2.mov -acodec copy -t 5 -vn output.mp4
```

Managed to try it and got the following error message for both options;

Unable for find a suitable output format for 'pipe:'

Geffers

---

### Post by Geffers on 2009-03-10
> **Fire_Chief said:**
> While tovid can use Mpeg2enc instead of FFmpeg, at this point I would suggest using Handbrake instead. It can handle AAC audio and H.264 video just fine.

-Cheers!

Just downloaded Handbrake to read the installation notes and saw the following;

A program to rip and encode DVDs and other sources to MPEG-4

I need conversion to mpeg2 for the movie to play on a specific device that cannot be upgraded.

Geffers

---

### Post by FakeOutdoorsman on 2009-03-11
> **Geffers said:**
> Managed to try it and got the following error message for both options;

Unable for find a suitable output format for 'pipe:'

Geffers
How odd.  Perhaps a recent version of FFmpeg will be able to decode this audio unlike the ancient FFmpeg from the Ubuntu repository:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

---

### Post by Geffers on 2009-03-19
> **FakeOutdoorsman said:**
> How odd.  Perhaps a recent version of FFmpeg will be able to decode this audio unlike the ancient FFmpeg from the Ubuntu repository:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

Sorry for delay in getting back, the link looks interesting and I'll give it a try over the weekend.

Geffers

---

### Post by Geffers on 2009-03-22
> **FakeOutdoorsman said:**
> How odd.  Perhaps a recent version of FFmpeg will be able to decode this audio unlike the ancient FFmpeg from the Ubuntu repository:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

Those instructions were spot on UNTIL Step Five (5) when I got the following error message :(

geoff@Columbia:~/x264/ffmpeg$ ./configure --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
FAAD test failed.
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

Tried to run ffmpeg but I get /usr/bin/ffmpeg: No such file or directory.

The config.err file has so much info I haven't a clue what to look for.

Geffers

---

### Post by FakeOutdoorsman on 2009-03-22
You made me realize there was an omission in the guide: there was a missing "cd" in step 5, but it shouldn't have caused your error.  Can you include config.err?  Wrap it with the code tag: [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG]

I'm guessing that your error was one of three things:
1. The SVN code of FFmpeg is currently not working.  Sometimes this happens because it is bleeding-edge code, but the compile problems are usually fixed within a day.  I should test the same revision as you.  Show the output of:
```
svn info ~/x264/ffmpeg/ | grep Revision
```

2. Maybe you forgot to install the libfaad-dev package.  Show the output of:
```
dpkg --get-selections | grep libfaad-dev
```

3. The omission of "cd" may have caused a problem, but I doubt that it would.

---

### Post by Geffers on 2009-03-23
> **FakeOutdoorsman said:**
>   Can you include config.err?  Wrap it with the code tag: 


Sorry, not sure what the code tag is so am (hopefully) adding it as an attachment. It is named config.err.txt

I definitely browsed for and uploaded a file associated with this message but can't find anything. I will upload it to a URL but unfortunately need to go on my windows machine to do so - ftp addresses in my address book :)

> **FakeOutdoorsman said:**
> 
  Show the output of:
```
svn info ~/x264/ffmpeg/ | grep Revision
```



Before reading your message I followed the instructions to 'Reverting Changes Made by This Tutorial' so wont get an output.

I'll reinstal and try again.

Geffers

---

### Post by Geffers on 2009-03-24
> **Geffers said:**
> 

I definitely browsed for and uploaded a file associated with this message but can't find anything. I will upload it to a URL but unfortunately need to go on my windows machine to do so - ftp addresses in my address book :)


Geffers

I know why it didn't upload, it exceeded to size limit.

Anyway, here it is, [HTML]http://www.3lanes.eclipse.co.uk/temp/config.err.txt[/HTML]

Geffers

---

### Post by Geffers on 2009-03-24
> **FakeOutdoorsman said:**
> You made me realize there was an omission in the guide: there was a missing "cd" in step 5, but it shouldn't have caused your error.  Can you include config.err?  Wrap it with the code tag: [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG]

I'm guessing that your error was one of three things:
1. The SVN code of FFmpeg is currently not working.  Sometimes this happens because it is bleeding-edge code, but the compile problems are usually fixed within a day.  I should test the same revision as you.  Show the output of:
```
svn info ~/x264/ffmpeg/ | grep Revision
```

2. Maybe you forgot to install the libfaad-dev package.  Show the output of:
```
dpkg --get-selections | grep libfaad-dev
```

3. The omission of "cd" may have caused a problem, but I doubt that it would.

Ran through the installation process again and got the same error.

As you requested here is the output from the two commands you asked for;

geoff@Columbia:~/ffmpeg$ svn info ~/x264/ffmpeg/ | grep Revision
svn: '/home/geoff/x264' is not a working copy
svn: Can't open file '/home/geoff/x264/.svn/entries': No such file or directory
geoff@Columbia:~/ffmpeg$ dpkg --get-selections | grep libfaad-dev
geoff@Columbia:~/ffmpeg$ 

Geffers

---

### Post by FakeOutdoorsman on 2009-03-24
Looks like you're missing libfaad-dev:
```
sudo apt-get install libfaad-dev
```
Now continue with the installation starting with this line:
```
./configure --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
```
The other command I asked you to run didn't work because your source directory has moved.  Try this:
```
svn info ~/ffmpeg | grep Revision
```

---

### Post by Geffers on 2009-03-25
> **FakeOutdoorsman said:**
> Looks like you're missing libfaad-dev:
```
sudo apt-get install libfaad-dev
```
Now continue with the installation starting with this line:
```
./configure --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
```
The other command I asked you to run didn't work because your source directory has moved.  Try this:
```
svn info ~/ffmpeg | grep Revision
```

I'm getting a wee bit confused with the directory location.

Following instructions on the web page Reverting Changes Made by This Tutorial I ran the command as follows;

```
geoff@Columbia:~$ sudo apt-get purge x264 ffmpeg build-essential yasm subversion git-core checkinstall texi2html libfaac-dev libfaad-dev liblame-dev libtheora-dev libxvidcore4-dev ibsdl1.2-dev zlib1g-dev libfaad-dev libfaac-dev libmp3lame-dev libtheora-dev libvorbis-dev libxvidcore4-dev libschroedinger-dev libspeex-dev libgsm1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package x264 is not installed, so not removed
Package ffmpeg is not installed, so not removed
Package build-essential is not installed, so not removed
Package yasm is not installed, so not removed
Package checkinstall is not installed, so not removed
Package texi2html is not installed, so not removed
Package libfaac-dev is not installed, so not removed
Package libfaad-dev is not installed, so not removed
Package liblame-dev is not installed, so not removed
Package libtheora-dev is not installed, so not removed
Package libxvidcore4-dev is not installed, so not removed
E: Couldn't find package ibsdl1.2-dev

```

Why is it telling me that x264 and ffmpeg are not installed, both are in my home directory along with yasm and still are after running the purge command.

Geffers

---

### Post by Geffers on 2009-03-25
> **FakeOutdoorsman said:**
> Looks like you're missing libfaad-dev:
```
sudo apt-get install libfaad-dev
```


I hope I am not getting this wrong but on the installation instructions there is a section > Intrepid Ibex 8.10 and Hardy Heron 8.04: Optional Dependencies

I have copied all on the end of the previous Hardy command ```
sudo apt-get install build-essential subversion git-core checkinstall texi2html libfaac-dev libfaad-dev liblame-dev libtheora-dev libxvidcore4-dev
```

so I think I did have libfaad-dev installed as that is the first listed on the third line.

Sorry if this is getting complicated but thanks very much for the help :popcorn:

Geffers

---

### Post by mc4man on 2009-03-25
As far as your dependencies for Hardy, you cannot take the first hardy dep. line and add the packages listed in "optional dependencies" verbatim  to it, If you do that then *nothing* is going to be installed. 
*(libmp3lame-dev is not available for hardy*

You should probably do them separately, though if you want them *all* for hardy in one command use this (blue are the available additional 'optional', red are 'optional' from orig. install line
```

sudo apt-get install build-essential subversion git-core checkinstall texi2html [COLOR="Red"]libfaac-dev libfaad-dev[/COLOR] liblame-dev [COLOR="Red"]libtheora-dev libxvidcore4-dev[/COLOR] [COLOR="Blue"]libsdl1.2-dev zlib1g-dev libvorbis-dev libschroedinger-dev libspeex-dev libgsm1-dev[/COLOR]

```

As far as x264 and yasm, go into your respective build folders and see if you created a .deb package, if so d. click on to install or if not then maybe start those over and follow instr. exactly.  (I can't see how you could have built them without the the build dep's installed

---

### Post by Geffers on 2009-04-05
> **mc4man said:**
> As far as your dependencies for Hardy, you cannot take the first hardy dep. line and add the packages listed in "optional dependencies" verbatim  to it, If you do that then *nothing* is going to be installed. 
*(libmp3lame-dev is not available for hardy*

You should probably do them separately, though if you want them *all* for hardy in one command use this (blue are the available additional 'optional', red are 'optional' from orig. install line
```

sudo apt-get install build-essential subversion git-core checkinstall texi2html [COLOR="Red"]libfaac-dev libfaad-dev[/COLOR] liblame-dev [COLOR="Red"]libtheora-dev libxvidcore4-dev[/COLOR] [COLOR="Blue"]libsdl1.2-dev zlib1g-dev libvorbis-dev libschroedinger-dev libspeex-dev libgsm1-dev[/COLOR]

```

As far as x264 and yasm, go into your respective build folders and see if you created a .deb package, if so d. click on to install or if not then maybe start those over and follow instr. exactly.  (I can't see how you could have built them without the the build dep's installed

Apologies for delay in replying, been a wee bit tied up the last week so I will give your instructions another go.

Geffers

---

### Post by Geffers on 2009-04-07
> **mc4man said:**
> As far as your dependencies for Hardy, you cannot take the first hardy dep. line and add the packages listed in "optional dependencies" verbatim  to it, If you do that then *nothing* is going to be installed. 
*(libmp3lame-dev is not available for hardy*

You should probably do them separately, though if you want them *all* for hardy in one command use this (blue are the available additional 'optional', red are 'optional' from orig. install line
```

sudo apt-get install build-essential subversion git-core checkinstall texi2html [COLOR="Red"]libfaac-dev libfaad-dev[/COLOR] liblame-dev [COLOR="Red"]libtheora-dev libxvidcore4-dev[/COLOR] [COLOR="Blue"]libsdl1.2-dev zlib1g-dev libvorbis-dev libschroedinger-dev libspeex-dev libgsm1-dev[/COLOR]

```

As far as x264 and yasm, go into your respective build folders and see if you created a .deb package, if so d. click on to install or if not then maybe start those over and follow instr. exactly.  (I can't see how you could have built them without the the build dep's installed

This is looking promising, followed your 'coloured' suggestions above then reinstalled. All appeared to go OK, ffmpeg took nearly 30 minutes to install.

I am now in the process of converting a .mov file to mpeg but not sure at this stage if it is mpeg2 or not. Will have to wait until conversion is finished.

I'll let you know the outcome.

Geffers

---

### Post by Geffers on 2009-04-08
> **Geffers said:**
> This is looking promising, followed your 'coloured' suggestions above then reinstalled. All appeared to go OK, ffmpeg took nearly 30 minutes to install.

I am now in the process of converting a .mov file to mpeg but not sure at this stage if it is mpeg2 or not. Will have to wait until conversion is finished.

I'll let you know the outcome.

Geffers

It worked :guitar:  converted to mpeg1.

Thanks for excellent instructions, now I'll have to get used to ffmpeg's various features.

Geffers

---

