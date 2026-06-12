---
title: "looking for good webcam video capture program"
date: 2012-02-22
forum: Multimedia Software
---

### Post by RememberWhenItRained on 2012-02-22
Hello community: I am looking for a good webcam video capture program to record with. Have tried Cheese - crashed in Unity - choppy/laggy (basically useless) in Gnome.
also tried camorama and guvcviewer. No go. Also tried vlc and open a capture, with Video Linux 2 (think i got the name wrong) but didn't see a record button. Picked up video. Didn't see a record button or any sign there was output recorded. Only displayed my video from webcam currently but did not appear to record.

Any recommendations for a better/working one? Seem?s i've tried most popular programs, but it's almost certain i'm missing some...

If i got really desperate, i could use something like vlc and use a screen capture program to record the portion that was displaying my webcam pickup, but i'd have to have it sync audio as well. tried RecordMyDesktop a while back and things came out really choppy.
Also would like to get a screen recording app as well, preferably a semi feature-rich one (zoom & annotation perhaps?) That exists, right?

Suggestions?

CLIFFS:
*Need to find program to record webcam video. Tried most with poor results
*Cheese crashed and was laggy, others crashed
*Also looking for screen/desktop recording app


Thank you

---

### Post by roelforg on 2012-02-22
Install ffmpeg,
assuming linux made a symlink for your cam, this will make a video:
```

ffmpeg -i /dev/video0 myvid.mp4

```
Hit CTRL-C when done.

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> Install ffmpeg,
assuming linux made a symlink for your cam, this will make a video:
```

ffmpeg -i /dev/video0 myvid.mp4

```Hit CTRL-C when done.

thank you for your quick response. Did as requested. A lot of output on terminal, but this was the final portion:
```
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
/dev/video0: Operation not permitted
```

where did i go amiss?

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> thank you for your quick response. Did as requested. A lot of output on terminal, but this was the final portion:
```
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
/dev/video0: Operation not permitted
```where did i go amiss?
Try:
```

sudo ffmpeg -i /dev/video0 myvid.mp4

```

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> Try:
```

sudo ffmpeg -i /dev/video0 myvid.mp4

```

same output, and oddly doesn't ask for sudo password

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> same output, and oddly doesn't ask for sudo password
Would you run this:
```

sudo ls /dev/video*

```

Also, if you've used sudo in the last 15-20 min it won't ask for your password.

---

### Post by RememberWhenItRained on 2012-02-22
same output (path? what's the term?) that you had specified in your earlier command,
```
/dev/video0
```

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> same output (path? what's the term?) that you had specified in your earlier command,
```
/dev/video0
```
N'ah it's fine, same path as mine so no problems.
Try using this:
```

sudo ffmpeg -f video4linux2 -i /dev/video0 myvid.mp4

```

---

### Post by roelforg on 2012-02-22
FYI:
```

sudo ffmpeg -f x11grab -i :0.0 out.mp4

```Will record your screen.

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> N'ah it's fine, same path as mine so no problems.
Try using this:
```

sudo ffmpeg -f video4linux2 -i /dev/video0 myvid.mp4

```
great! seems to have worked. is output .mp4 store in /home?


wait - no audio output
too bad can't see output/what's going on. Thanks! a

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> great! seems to have worked. is output .mp4 store in /home?


wait - no audio output
too bad can't see output/what's going on. Thanks! a
The file should be in the dir where you started ffmpeg (home dir i'd guess).

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> The file should be in the dir where you started ffmpeg (home dir i'd guess).
thanks. what do i do about the lack of audio?

You've been so helpful. appreciate it.

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> thanks. what do i do about the lack of audio?

You've been so helpful. appreciate it.
Is there a mic on your pc,
the command i gave only records the webcam stream, which is just video.

Please run:
```

sudo ls /dev/audio*
sudo ls /dev/dsp*
sudo lshw -C sound

```
Note: that last one may take some time.

I'll see if i can update the command for you.

---

### Post by RememberWhenItRained on 2012-02-22
yes, mic is coupled with the webcam. There a  way to record simultaneously?

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> yes, mic is coupled with the webcam. There a  way to record simultaneously?
Would you run those commands i just gave you?
They'll tell me how you access the mic.

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> Is there a mic on your pc,
the command i gave only records the webcam stream, which is just video.

Please run:
```

sudo ls /dev/audio*
sudo ls /dev/dsp*
sudo lshw -C sound

```Note: that last one may take some time.

I'll see if i can update the command for you.
output as follows, consecutively:
```
ls: cannot access /dev/audio*: No such file or directory
ls: cannot access /dev/dsp*: No such file or directory
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:47 memory:f6afc000-f6afffff

```

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> output as follows, consecutively:
```
ls: cannot access /dev/audio*: No such file or directory
ls: cannot access /dev/dsp*: No such file or directory
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:47 memory:f6afc000-f6afffff

```

Try this command:
```

sudo ffmpeg -f alsa -ac 2  -ab 128k  -i hw:0,0 -f video4linux2 -i /dev/video0 myvid.mp4

```

If it doesn't give sound, try using alsamixer to increase the MIC and PCM volumes.

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> Try this command:
```

sudo ffmpeg -f alsa -ac 2  -ab 128k  -i hw:0,0 -f video4linux2 -i /dev/video0 myvid.mp4

```If it doesn't give sound, try using alsamixer to increase the MIC and PCM volumes.


you sir, are a genius.

now my next question - is there a way i can assign a shorter terminal input to that command (such as "webcam-capture") or will i just have to make a shortcut on the desktop with that command?

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> you sir, are a genius.

now my next question - is there a way i can assign a shorter terminal input to that command (such as "webcam-capture") or will i just have to make a shortcut on the desktop with that command?
Sure:
Issue this (as your normal user):
```

nano ~/.bashrc

```
Insert the following at the end of the file (copy/past is the safest way):
```

alias webcam-capture='sudo ffmpeg -f alsa -ac 2  -ab 128k  -i hw:0,0 -f video4linux2 -i /dev/video0'

```
Hit CTRL-O
Hit enter
Hit CTRL-X

Reboot

Open a terminal; type webcam-capture myvid.mp4 ; hit CTRL-C when done; view.

Syntax:
```

webcam-capture [extra ffmpeg options you might need one day, just ignore for now] <filename of video>

```

BTW. Thanks for the complement.

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> Sure:
Issue this (as your normal user):
```

nano ~/.bashrc

```Insert the following at the end of the file (copy/past is the safest way):
```

alias webcam-capture='sudo ffmpeg -f alsa -ac 2  -ab 128k  -i hw:0,0 -f video4linux2 -i /dev/video0'

```Hit CTRL-O
Hit enter
Hit CTRL-X

Reboot

Open a terminal; type webcam-capture myvid.mp4 ; hit CTRL-C when done; view.

Syntax:
```

webcam-capture [extra ffmpeg options you might need one day, just ignore for now] <filename of video>

```BTW. Thanks for the complement.

good to know,. Thanks, sir.

For now i just created a desktop launcher which brings up a new terminal, still have to enter the sudo password (to be expected) and works like a charm. Now i'm wondering how hard it would be to code/script a simple app that is a GUI for ffmpeg where you can see what you are recording. I'm not a programmer though. oh well.

Thanks again!

(Why did Canonical do away with the right click to create a launcher in Ocelot?)

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> good to know,. Thanks, sir.

For now i just created a desktop launcher which brings up a new terminal, still have to enter the sudo password (to be expected) and works like a charm. Now i'm wondering how hard it would be to code/script a simple app that is a GUI for ffmpeg where you can see what you are recording. I'm not a programmer though. oh well.

Thanks again!

(Why did Canonical do away with the right click to create a launcher in Ocelot?)

I'm a programmer myself; i'm just saying: a gui isn't needed in this case. Whats to display that the terminal can't?

Also, (you've gotta google this) it's possible to grant exceptions for certain programs to allow sudo access w/o entering passwords. If you need help with this, please open a new thread.

---

### Post by RememberWhenItRained on 2012-02-22
was simply thinking a GUI would be nice to see the actual video you are recording, real-time, as opposed to terminal output. (Been using ubuntu for two years, still getting used to terminal stuff.) Not that it matters a whole lot, as long as you have the camera where you want it.

I'll look up about sudo exceptions, thanks.

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> was simply thinking a GUI would be nice to see the actual video you are recording, real-time, as opposed to terminal output. (Been using ubuntu for two years, still getting used to terminal stuff.) Not that it matters a whole lot, as long as you have the camera where you want it.

I'll look up about sudo exceptions, thanks.
Sure, and hey, it records!
You might try running:
```

sudo ffplay -f video4linux2 /dev/video0

```
in a different terminal whilst recording

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> Sure, and hey, it records!
You might try running:
```

sudo ffplay -f video4linux2 /dev/video0

```in a different terminal whilst recording
running this should show what the user is recording at that moment, no? Which begs the question, is it possible to use two different commands and summon two separate terminals using the same launcher?

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> running this should show what the user is recording at that moment, no? Which begs the question, is it possible to use two different commands and summon two separate terminals using the same launcher?
The command will display the webcam feed; execute the record command in the other terminal and you've got both.
If it works; i'll post an updated version of the webcam-capture.

---

### Post by RememberWhenItRained on 2012-02-22
```
 libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[video4linux2 @ 0x9dc1ac0] Cannot find a proper format for codec_id 0, pix_fmt -1.
/dev/video0: Input/output error
```

cannot find proper codec...

see attached  screencap

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> ```
 libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[video4linux2 @ 0x9dc1ac0] Cannot find a proper format for codec_id 0, pix_fmt -1.
/dev/video0: Input/output error
```cannot find proper codec...

see attached  screencap
Try:
```
[FONT=monospace]
[/FONT]sudo ffplay -f video4linux2 -i /dev/video0

```

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> Try:
```
[FONT=monospace]
[/FONT]sudo ffplay -f video4linux2 -i /dev/video0

```
no-go.

same output. cannot find proper codec format and /dev/video0: Input/output error

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> no-go.

same output. cannot find proper codec format and /dev/video0: Input/output error
I'm out of ideas.

At least recording works.

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> I'm out of ideas.

At least recording works.
indeed. Thank you very much!

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> indeed. Thank you very much!
You're welcome.

---

### Post by RememberWhenItRained on 2012-02-22
> **roelforg said:**
> I'm out of ideas.

At least recording works.
@roelforg
 It is interesting to note: was playing around with it: without starting the Webcam-Capture launcher, and running ```
sudo ffplay -f video4linux2 -i /dev/video0
``` by itself, it worked.

Is there a way to have that single launcher to start this first, then the ffmpeg recording?

ETA: which seemed to consolidate both processes to one terminal,, but upon keying CNTRL + C and searching /home for the .mp4, it "contained no playable streams"

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> @roelforg
 It is interesting to note: was playing around with it: without starting the Webcam-Capture launcher, and running ```
sudo ffplay -f video4linux2 -i /dev/video0
``` by itself, it worked.

Is there a way to have that single launcher to start this first, then the ffmpeg recording?

ETA: which seemed to consolidate both processes to one terminal,, but upon keying CNTRL + C and searching /home for the .mp4, it "contained no playable streams"
Oh well.  Maybe you'll find a proper solution one day.

---

### Post by RememberWhenItRained on 2012-02-22
sorry to keep bugging you.

I'm seeing about a 3-4 second lag between audio and video - audio is delayed. Any suggestions/solutions?

---

### Post by roelforg on 2012-02-22
> **RememberWhenItRained said:**
> sorry to keep bugging you.

I'm seeing about a 3-4 second lag between audio and video - audio is delayed. Any suggestions/solutions?
Look up in the man page of ffmpeg on how to adjust the delays between the 2 input's.
It's because your pc is processing 1 of the 2 streames faster than the other.

---

### Post by BrianSnapp on 2012-03-03
Interesting forum, as I have been trying for quite a long time, to get webcam recording to work (I have the same problems with CHEESE. Choppy, lagging, etc).

Here is the output I get, when I run the terminal commands...

-----------------------------------------------------------------
brian@brian-jolicloud:~$ sudo ffmpeg -f alsa -ac 2  -ab 128k  -i hw:0,0 -f video4linux2 -i /dev/video0 myvid.mp4
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
Input #0, alsa, from 'hw:0,0':
  Duration: N/A, start: 26488.257006, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
[video4linux2 @ 0x93ed370]Wrong size (0x0)
/dev/video0: Error while opening file
-----------------------------------------------------------------
Perhaps, it is because I am using Jolicloud? I know it's based off of Ubuntu, and I have yet to find a program that works in Ubuntu, not working in Jolicloud.

Any ideas?
Thank you in advance

~Brian Snapp

---

### Post by RememberWhenItRained on 2012-03-03
> **BrianSnapp said:**
> Interesting forum, as I have been trying for quite a long time, to get webcam recording to work (I have the same problems with CHEESE. Choppy, lagging, etc).

Here is the output I get, when I run the terminal commands...

-----------------------------------------------------------------
brian@brian-jolicloud:~$ sudo ffmpeg -f alsa -ac 2  -ab 128k  -i hw:0,0 -f video4linux2 -i /dev/video0 myvid.mp4
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
Input #0, alsa, from 'hw:0,0':
  Duration: N/A, start: 26488.257006, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
[video4linux2 @ 0x93ed370]Wrong size (0x0)
/dev/video0: Error while opening file
-----------------------------------------------------------------
Perhaps, it is because I am using Jolicloud? I know it's based off of Ubuntu, and I have yet to find a program that works in Ubuntu, not working in Jolicloud.

Any ideas?
Thank you in advance

~Brian Snapp

hey Brian,

 I don't think Jolicloud should be an issues as it is a derivative of Ubuntu Netbook distro.

what does running ```

sudo ls /dev/video*
```
give you?

---

### Post by billmnfl on 2012-12-29
Hello roelforg and RememberWhenItRained.
I have to stop in to thank you for your discussion on this topic.
I have been searching for days to try to get an old vhs tape copied over to my computer so that I can burn it to DVD.  
After reading through this thread, and adjusting some settings, finally, I was able to record a video with sound that I am sure I will be able to burn to DVD.
I have loaded the file into Openshot and it displays beautifully.
I am ranting and raving because it has taken me over a week to find your thread.
Thank you, Thank you, Thank you.  ):P

My system:
Linux GA-MA785GM 
3.2.0-35-generic #55-Ubuntu SMP 
Wed Dec 5 17:42:16 UTC 2012 
x86_64 x86_64 x86_64 GNU/Linux

Billmnfl

---

