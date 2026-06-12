---
title: "ffmpeg problems with UTube Ripper"
date: 2009-02-11
forum: Multimedia Software
---

### Post by ArtF10 on 2009-02-11
Ubuntu 8.10 (32 bit)

I'm using UTube Ripper and have converted a youtube video file to .flv using this guide:
[http://www.ubuntugeek.com/downloadextract-audio-from-youtube-videos-using-utube-ripper-in-ubuntu.html](http://www.ubuntugeek.com/downloadextract-audio-from-youtube-videos-using-utube-ripper-in-ubuntu.html)

When I select "Convert" to convert the .flv file to a .mp3 file, a message comes up in the Console box saying "Have you installed ffmpeg?"  It won't perform the conversion.

So, I installed ffmpeg through Synaptic, restarted and tried to convert again.  No luck.  The same "Have you installed ffmpeg?" message shows up.

Any ideas where I am going wrong?

---

### Post by FakeOutdoorsman on 2009-02-11
You can usually directly copy the audio stream from a video file with FFmpeg alone if UTube Ripper sucks.  First find out the audio format of the flv:
```
ffmpeg -i input.flv
```
FFmpeg will output a good amount of information, but the most important indicates the audio details:
```
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
```
The above example uses MP3 audio.  Now just copy the stream:
```
ffmpeg -i input.flv -acodec copy output.mp3
```
The important option is "acodec copy".  This tells FFmpeg to just copy the stream instead of re-encoding to MP3.  This preserves the quality.  If you need to encode  from one format to a restricted format such as MP3 you will need to install the **libavcodec-unstripped-51** package.  You shouldn't need this package if you are straight copying the stream like my example above (going from MP3 input to MP3 output).

I usually just watch the YouTube video and then check the /tmp folder for a Flash**** file while the page is still open.  Then I use FFmpeg.  No need for UTube Ripper, youtube-dl, or other scripts.

---

### Post by ArtF10 on 2009-02-12
Yeah, I dug deeper and found out that Youtube Ripper works for 3 attempts and then stops working.

Ok, so I'm going to try out your procedure.  I waited for the full video to load, minimized the browser and copied the .flv file to the desktop, from the /tmp folder.  I've got ffmpeg installed.  Your first command includes input.flv.  

Do I need to rename the flash file input.flv?  
Also, does it need to be stored in a specific location?i.e. not on the desktop....home folder maybe...or is the desktop fine?

---

### Post by FakeOutdoorsman on 2009-02-12
I'm not familiar with Youtube/UTube Ripper, so I can't comment on that.  You don't need to rename your file to "input.flv".  That was just an example.  It will take any name.  It also doesn't need to be stored in any specific location.  You just need to specify it.  For example, if it in a folder called "earthquake_ham" in your home folder:
```
ffmpeg -i ~/earthquake_ham/yourvideofile.flv -acodec copy output.mp3
```

---

### Post by ArtF10 on 2009-02-12
ok thanks, will give it a try tomorrow.  I need to first clean up some packages I've installed.

---

### Post by ArtF10 on 2009-02-12
ok i'm trying it and having problems.  I've saved the .flv file to the desktop(assume it is named yourvideofile.flv).  Here's what I've typed:

- Open terminal

- Enter the ffmpeg command
```
art@computer:~$ ffmpeg -i /desktop/yourvideofile.flv -acodec copy output.mp3
```

It produces a bunch of text, but the last line says no such file or directory.

---

### Post by mc4man on 2009-02-12
```
ffmpeg -i  ~/Desktop/yourvideofile.flv -acodec copy [COLOR="Red"]output[/COLOR].mp3
```

Your free to name the red anything you like (no spaces or use '' around name and ext.

If you wanted to save to desktop
ffmpeg -i  ~/Desktop/yourvideofile.flv -acodec copy ~/Desktop/output.mp3

---

### Post by ArtF10 on 2009-02-12
when you say "~/Desktop" what does that ~ mean?

I have only typed /desktop/yourvideofile.flv ...........

I'm not too familiar with the command line.  Do I need to install "acodec"?

EDIT:  Would this be my full command?:
```
art@computer:$ ffmpeg -i /home/art/Desktop/yourvideofile.flv -acodec copy /home/art/Desktop/output.mp3
```

I tried the above command and it STILL says No such file or directory.  The .flv file is saved on the desktop.  I'm completely lost here.....

---

### Post by mc4man on 2009-02-12
> I'm completely lost here..... 

no problem
> (assume it is named yourvideofile.flv).
I missed the key word there "assume"

In the orig. suggested command
> ...............yourvideofile.flv ...... the **yourvideofile** was just meaning 'the actual name of the .flv" you copied.

The reason your command is failing is that's obviously not the name of the .flv

do this to get the idea

Right click on the .flv on your desktop -> rename

You'll notice only the name will be highlighted which is good.

Type in foo and click anywhere to save the new name (foo.flv)

Now in the terminal run this (Copy and paste exactly

```
ffmpeg -i ~/Desktop/foo.flv -acodec copy ~/Desktop/foo.mp3
```

(~ just replaces the need to go /home/art

Edit:
The output.mp3 was just suggesting that the word "output" could be whatever you want the file to be named.

So you could also do this

```
ffmpeg -i  ~/Desktop/foo.flv -acodec copy output.mp3
```

and the name of the mp3 would be output

---

### Post by ArtF10 on 2009-02-13
Sorry for the confusion...that's actually what I've done.  I just used the name yourvideofile.flv here but when I entered the command in the terminal, I used the name of my .flv file.  Anyways, still no luck.

The only thing I can think of is that I have not navigated to the right directory in the terminal.  Presumably I would have to navigate to the desktop directory since that is where the file is located...right?  I don't know how to do this.

---

### Post by mc4man on 2009-02-13
> Presumably I would have to navigate to the desktop directory since that is where the file is located...right?
Not necessary but why not

open a terminal type this and press the enter key
cd Desktop

Then run the command without any path for the input file or output file (replace red with the actual name 
as in 
ffmpeg -i [COLOR="Red"]whatever the name of the file[/COLOR].flv -acodec copy [COLOR="Red"]whatever the name of the file[/COLOR].mp3

I'll give you an example 
There is a file on my desktop named  "song.flv
> doug@doug-desktop:~$ cd Desktop
doug@doug-desktop:~/Desktop$ ffmpeg -i song.flv -acodec copy song.mp3

Now if the song name has spaces you'll put ' around it
Ex. (i'll give you a complete to show how it works
I have a file 10-cold cold ground.flv on the desktop
> 
doug@doug-desktop:~$ cd Desktop
doug@doug-desktop:~/Desktop$ ffmpeg -i  '10-cold cold ground.flv' -acodec copy '10-cold cold ground.mp3'
FFmpeg version SVN-r16844, Copyright (c) 2000-2009 Fabrice Bellard, et al.

  libavutil     49.14. 0 / 49.14. 0
  libavcodec    52.11. 0 / 52.11. 0
  libavformat   52.25. 0 / 52.25. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 3. 0 /  0. 3. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 28 2009 15:22:30, gcc: 4.3.3
Input #0, mp3, from '10-cold cold ground.flv':
  Duration: 00:04:20.88, start: 0.000000, bitrate: 320 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 320 kb/s
Output #0, mp3, to '10-cold cold ground.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, stereo, s16, 320 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   10191kB time=260.88 bitrate= 320.0kbits/s    
video:0kB audio:10191kB global headers:0kB muxing overhead 0.000307%
doug@doug-desktop:~/Desktop$


If the file was in your home folder to begin with then you would not go cd Desktop, just run the command after opening a terminal
as in 

> ffmpeg -i [COLOR="Red"]whatever the name of the file[/COLOR].flv -acodec copy [COLOR="Red"]whatever the name of the file[/COLOR].mp3


If still a no go then post the exact name of your file and me or someone else will give you the exact command

---

### Post by ArtF10 on 2009-02-13
Thanks, I'll give it ago tonight and see what happens.

---

### Post by ArtF10 on 2009-02-16
Here's my output:

```
art@asus:~$ cd Desktop
art@asus:~/Desktop$ ffmpeg -i FlashUYKYR4.flv -acodec copy outpute.mp3FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
FlashUYKYR4.flv: no such file or directory
art@asus:~/Desktop$ cd ..
art@asus:~$ ffmpeg -i FlashUYKYR4.flv -acodec copy outpute.mp3
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
FlashUYKYR4.flv: no such file or directory
art@asus:~$
```

I've attached a screenshot of my desktop to show that the flash file is infact there.

---

### Post by ArtF10 on 2009-02-17
Any help would be greatly appreciated.

---

### Post by FakeOutdoorsman on 2009-02-17
It looks like the file on your Desktop doesn't have .flv in the name, but your command did.  First navigate to your Desktop:
```
cd Desktop
```
Then paste this (shift + ctrl + v in the terminal):
```
ffmpeg -i FlashUYKYR4 -acodec copy output.mp3
```
Alternatively, you can use tab completion.  Tab completion will type the file name for you.  Navigate to the desktop, type "ffmpeg -i F" (without the quotes) and then hit tab.  The name should appear in the terminal typed for you.

---

