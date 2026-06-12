---
title: "Tutorial: simple (but cool) TV recording script!"
date: 2008-09-21
forum: Multimedia Software
---

### Post by lovinglinux on 2008-09-21
This is a byproduct of my tutorial "[[COLOR="Dark_Red"]**Firefox Media Center**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=913671")". I decided to create a new thread because some people might not be interested in the other stuff from the Firefox tutorial, so here you will just learn how to create a simple tv recorder script, with recording preset time and panel notification/stop icon.

[COLOR="Red"]**Requirements:**[/COLOR] You need a tv card already working with TVTime.

To create our recorder we first need to install transcode, ffmpeg and zenity. Type the following command on a terminal:

```
sudo apt-get install transcode ffmpeg zenity
```

After installing the required applications, we need to create a shell script for starting the recorder.

Open the text editor and add the following text 

For NTSC cards

```
#!/bin/bash

killall zenity
killall tvtime
killall transcode
amixer -q set "Line" 100% unmute
amixer -q set "Analog Mix" 100% unmute
tvtime
amixer -q set "Line" 0% mute

REC=$(zenity --list --text "Choose a recording time" --radiolist  --column "Pick" --column "Recording time" 00:15:00 '00:15:00' 00:30:00 '00:30:00' 00:45:00 '00:45:00' 01:00:00 '01:00:00' 01:15:00 '01:15:00' 01:30:00 '01:30:00' 01:45:00 '01:45:00' 02:00:00 '02:00:00' 02:15:00 '02:15:00' 02:30:00 '02:30:00' 02:45:00 '02:45:00' 03:00:00 '03:00:00' 03:15:00 '03:15:00' 03:30:00 '03:30:00' 03:45:00 '03:45:00' 04:00:00 '04:00:00' 06:00:00 '06:00:00' 12:00:00 '12:00:00')
NAME=$(zenity --title "Name Selector" --entry --text "Select a file name (without extension or spaces)")
TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

transcode -x v4l2,v4l2 \
	-M 2 \
	-i [COLOR="Red"]/dev/video0 [/COLOR]\
	-p [COLOR="Red"]/dev/dsp2 [/COLOR]\
	-y ffmpeg \
	-F mpeg4 \
	-c ${REC} \
	-g 720x480 \
	-f 0,4 \
	-I 1 \
	-u 100 \
	-Q 3 \
	-Z 360x240,fast \
	-E 48000,16,2 \
	--lame_preset medium \
	-o ~/[COLOR="Red"]**Desktop**[/COLOR]/${NAME}.avi & zenity --text "Recording ${NAME}.avi started at ${NOW} with ${REC} preset time" --notification

killall zenity
killall transcode 
amixer -q set "Line" 0% mute

``` 

You will probably have to tweak this code and replace devices/player (in red) with your own. You can also choose another directory for saving the files. 

If you have a PAL-M TV card then use this code instead:

```
#!/bin/bash

killall zenity
killall tvtime
killall transcode
amixer -q set "Line" 100% unmute
amixer -q set "Analog Mix" 100% unmute
tvtime
amixer -q set "Line" 0% mute

REC=$(zenity --list --text "Choose a recording time" --radiolist  --column "Pick" --column "Recording time" 00:15:00 '00:15:00' 00:30:00 '00:30:00' 00:45:00 '00:45:00' 01:00:00 '01:00:00' 01:15:00 '01:15:00' 01:30:00 '01:30:00' 01:45:00 '01:45:00' 02:00:00 '02:00:00' 02:15:00 '02:15:00' 02:30:00 '02:30:00' 02:45:00 '02:45:00' 03:00:00 '03:00:00' 03:15:00 '03:15:00' 03:30:00 '03:30:00' 03:45:00 '03:45:00' 04:00:00 '04:00:00' 06:00:00 '06:00:00' 12:00:00 '12:00:00')
NAME=$(zenity --title "Name Selector" --entry --text "Select a file name (without extension or spaces)")
TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

transcode -x v4l2=resync_margin=1:resync_interval=250,v4l2 \
        -g 640x480 \
        -i [COLOR="Red"]**/dev/video0**[/COLOR] \
        -p [COLOR="Red"]**/dev/dsp2**[/COLOR] \
        -e 32000,16,2 \
        -N 0x1 \
        -J resample,levels,smartyuv \
        -w 4000 \
        -y ffmpeg \
        -F mjpeg \
	-c ${REC} \
        -o ~/[COLOR="Red"]**Desktop**[/COLOR]/${NAME}.avi & zenity --text "Recording ${NAME}.avi started at ${NOW} with ${REC} preset time" --notification

killall zenity
killall transcode 
amixer -q set "Line" 0% mute
```

For more command options visit [[COLOR="DarkRed"]**Transcode**[/COLOR]]("http://www.transcoding.org/cgi-bin/transcode?Transcode_Command_Line_Options") web site.


If you want to automatically play the recorded file when you stop the recording, add the following command to the end of the previous script. In this case I'm using [COLOR="Red"]**smplayer**[/COLOR], but you can modify this line to use any player you want.

```
[COLOR="Red"]**smplayer**[/COLOR] ~/[COLOR="Red"]**Desktop**[/COLOR]/${NAME}.avi
```

If you want to automatically move the recorded file to another directory before playing it, use the following command instead (don't forget to change things in red accordingly):

```
mv ~/[COLOR="Red"]**Desktop**[/COLOR]/${NAME}.avi ~/[COLOR="Red"]**NewDirectory**[/COLOR]/${NAME}.avi

smplayer ~/[COLOR="Red"]**NewDirectory**[/COLOR]/${NAME}.avi
```

Now save this file as /home/[COLOR="Red"]**you**[/COLOR]/bin/startrec  (don't forget to replace you with your user name). 

Go to /home/[COLOR="Red"]**you**[/COLOR]/bin/, select the file and open it's properties. In the Permissions tab, make sure you tick "Allow executing file as program".

Now we need to create a button to start the recorder. You can right-click in the Desktop and select "Create launcher" or you can add a "Custom Application Launcher" to the gnome panel. Either way, you are going to use the following settings:

**Type:** Application
**Name:** TV Recorder
**Command:** /home/[COLOR="Red"]**you**[/COLOR]/bin/startrec

When you hit the new TV recorder button, TVTime will be launched, so you can choose the channel. You must close TVTime to start the recording process, then a window will pop up asking for recording time. Select an option from the list and click OK. 

A notification icon will show up in the panel notification area. Move the mouse over the notification icon and a tooltip will display the time the recording started and the recording time preset. The corresponding avi file should be created in the directory you have chosen for saving the recordings. 

You can stop the recording at any time by hitting the notification icon in the panel. It will remain on the panel if you do not touch it, even after the preset recording time ends (although the recording itself will stop automatically). If you chose to move the file after recording, then you must click the notification icon to continue. If you choose to start the recorded file automatically, the player of your choice will be launched and the recorded file will be displayed.

[COLOR="Red"]**Don't forget to replace things in red, including the player if you don't have smplayer.**[/COLOR]

You can also create buttons just to start TVTime, to record and stop recording as explained in [COLOR="Red"]**[Cresho's tutorial]("http://ubuntuforums.org/showthread.php?t=921233")**[/COLOR], from where I took some valuable information to create this tutorial myself.

---

### Post by vmosorio on 2008-10-17
Hello Lovinglinux!

Nice job!  I'm having problems recording though, everything starts as advertised but I don't get any file in the system...? 
There is one thing I did different from your guide: I have the startrec file in the bin folder but the one inside file system because I don't have a folder in that directory as in your tutorial:

Now save this file as /home/you/bin/startrec (don't forget to replace you with your user name). 

I'm using Hardy Heron and my systems records from dev/vbi0 instead of video0 so I changed that; the other problem is that when I try a command line capture it makes a file but when I try to play it, the player doesn't interpret the stream... any iadea?

Vic

---

### Post by lovinglinux on 2008-10-17
Thank you. I'm glad you liked it.

> **vmosorio said:**
> I'm having problems recording though, everything starts as advertised but I don't get any file in the system...? 

Please tell me where are you trying to save the video? did you changed the following path?

```
-o ~/Desktop/${TODAY}-${NOW}.avi
```

> **vmosorio said:**
> There is one thing I did different from your guide: I have the startrec file in the bin folder but the one inside file system because I don't have a folder in that directory as in your tutorial:

I don't think this would be an issue, because the script starts, but it doesn't hurt to create a bin on your user directory just for testing. Maybe the video files is not created due to writing permissions. When you run the script from the terminal do you see a frame counter?

> **vmosorio said:**
> I'm using Hardy Heron and my systems records from dev/vbi0 instead of video0 so I changed that; the other problem is that when I try a command line capture it makes a file but when I try to play it, the player doesn't interpret the stream... any iadea?

 I guess you should use device and not vbidevice for capture. So try dev/video1

---

### Post by vmosorio on 2008-10-18
Hello Lovinglinux and again thanks so much for your help.

>Please tell me where are you trying to save the video? did you changed the following path?<

Yes, I did. I'm saving to my home folder, I just replaced the word Desktop.

I didn't know I could run the script in the terminal, I just did and this is what I've got:


zenity: no process killed
tvtime: no process killed
transcode: no process killed
amixer: Unable to find simple control 'Analog Mix',0

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/victor/.tvtime/tvtime.xml
Thank you for using tvtime.
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] auto-probing source /dev/vbi0 (failed)
[transcode] V: import format    | unknown  (V=v4l2|A=v4l2)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x480  1.50:1  
[transcode] V: de-interlace     | (mode=1) interpolate scanlines (fast)
[transcode] V: fast resize      | Using -B 30,45,8 -X 0,0,8
[transcode] V: new aspect ratio | 360x240  1.50:1 (-B)
[transcode] V: bits/pixel       | 0.695
[transcode] V: decoding fps,frc | 29.970,4
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  128 kbps
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 6408 (6406.400000)
[transcode] A: adjustment       | -1600@1000
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 100 @ 720x480
[import_v4l2.so] v1.3.5 (2005-03-11) (video) v4l2 | (audio) pcm
[export_ffmpeg.so] v0.3.13 (2004-08-03) (video) Lavc1d.51.38.0 | (audio) MPEG/AC3/PCM
[import_v4l2.so]: v4l2 audio grabbing
[import_v4l2.so]: v4l2 video grabbing
[import_v4l2.so]: resync disabled
[import_v4l2.so]: video grabbing, driver = saa7134, card = Kworld/Tevion V-Stream Xpert TV
[import_v4l2.so]: Pixel format conversion: YVU420 [planar] -> YUV420 [planar] (no conversion)
[import_v4l2.so]: driver does not support setting parameters (ioctl(VIDIOC_S_PARM) returns "Invalid argument")
[import_v4l2.so]: checking colour & framerate standards: [NTSC] 
[import_v4l2.so]: receiving 30 frames / sec
[import_v4l2.so]: frame size: 720x480
[import_v4l2.so]: cropcap bounds: 704x480 +0+44
[import_v4l2.so]: cropcap defrect: 704x480 +0+46
[import_v4l2.so]: cropcap pixelaspect: 11/10
[import_v4l2.so]: capturing dimensions exceed maximum crop area: 704x480
video import module error: OPEN failed
[transcode] critical: failed to open input source

I think this is telling what the problem is but I just don't know what to do next.

Meanwhile I will try changing those dev parameters

Thanks

Vic

---

### Post by lovinglinux on 2008-10-18
> **vmosorio said:**
> [transcode] critical: failed to open input source

Try other devices and see if the output text still gives the error above.

---

### Post by vmosorio on 2008-10-18
I'm trying this:

zenity: no process killed
tvtime: no process killed
transcode: no process killed
amixer: Unable to find simple control 'Analog Mix',0

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/victor/.tvtime/tvtime.xml
Thank you for using tvtime.
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/dev/video1"

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/victor/.tvtime/tvtime.xml
Thank you for using tvtime.
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] auto-probing source /dev/video0 (failed)
[transcode] V: import format    | unknown  (V=v4l2|A=v4l2)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x480  1.50:1  
[transcode] V: de-interlace     | (mode=1) interpolate scanlines (fast)
[transcode] V: fast resize      | Using -B 30,45,8 -X 0,0,8
[transcode] V: new aspect ratio | 360x240  1.50:1 (-B)
[transcode] V: bits/pixel       | 0.695
[transcode] V: decoding fps,frc | 29.970,4
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  128 kbps
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 6408 (6406.400000)
[transcode] A: adjustment       | -1600@1000
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 100 @ 720x480
[import_v4l2.so] v1.3.5 (2005-03-11) (video) v4l2 | (audio) pcm
[export_ffmpeg.so] v0.3.13 (2004-08-03) (video) Lavc1d.51.38.0 | (audio) MPEG/AC3/PCM
[import_v4l2.so]: v4l2 audio grabbing
[import_v4l2.so]: v4l2 video grabbing
[import_v4l2.so]: resync disabled
[import_v4l2.so]: video grabbing, driver = saa7134, card = Kworld/Tevion V-Stream Xpert TV
[import_v4l2.so]: Pixel format conversion: YVU420 [planar] -> YUV420 [planar] (no conversion)
[import_v4l2.so]: driver does not support setting parameters (ioctl(VIDIOC_S_PARM) returns "Invalid argument")
[import_v4l2.so]: checking colour & framerate standards: [NTSC] 
[import_v4l2.so]: receiving 30 frames / sec
[import_v4l2.so]: frame size: 720x480
[import_v4l2.so]: cropcap bounds: 704x480 +0+44
[import_v4l2.so]: cropcap defrect: 704x480 +0+46
[import_v4l2.so]: cropcap pixelaspect: 11/10
[import_v4l2.so]: capturing dimensions exceed maximum crop area: 704x480
video import module error: OPEN failed
[transcode] critical: failed to open input source


Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/victor/.tvtime/tvtime.xml
Thank you for using tvtime.
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/dev/video"


As you see I have tried video video0 video1 with no luck.

tvtime works fine, I have audio and video, I have been able to record some video with motv but no audio, doing a cat /dev/videoo... gives me an access denied but if I try cat /dev/vbi0 > test.mpg it records and gives me a file but none of the players will play it saying that they couldn't determine the type of stream...


Thanks

---

### Post by lovinglinux on 2008-10-18
Keep /dev/vbi0 and change the audio device to /dev/dsp/...dsp1...dsp2.

How do you get the sound from your card, via mixer, line-in or what?

I'm sorry if I can't give you a quick solution. I'm a Linux newbie, so I'm trying to figure out what is wrong from your terminal output.

---

### Post by vmosorio on 2008-10-18
Now the message is this:

 Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/victor/.tvtime/tvtime.xml
Thank you for using tvtime.
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/dev/dsp2"

It looks like the problem is audio instead of video as before. I get the sound from the capture card into the sound card with a cable.

I have also tried dsp1 and just dsp

---

### Post by Merovius on 2008-10-18
I'm trying out this nice little script too. Seems to be doing exactly what you intended except I can't find a file it output. Not sure if it's not creating one or it's landing somewhere other then the desktop?

When does the .avi appear on the desktop? As soon as it starts recording or after it finishes?

---

### Post by lovinglinux on 2008-10-18
> **Merovius said:**
> I'm trying out this nice little script too. Seems to be doing exactly what you intended except I can't find a file it output. Not sure if it's not creating one or it's landing somewhere other then the desktop?

When does the .avi appear on the desktop? As soon as it starts recording or after it finishes?

As soon as it starts recording.

Run the script in the terminal and paste the output here. It would also help if you paste the script itself.

---

### Post by lovinglinux on 2008-10-18
> **vmosorio said:**
> Now the message is this:

 Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/victor/.tvtime/tvtime.xml
Thank you for using tvtime.
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/dev/dsp2"

It looks like the problem is audio instead of video as before. I get the sound from the capture card into the sound card with a cable.

I have also tried dsp1 and just dsp

post the output (each one separated) of:

```
ls -l /dev/video0
```

```
ls -l /dev/video1
```

```
ls -l /dev/video2
```

```
ls -l /dev/video3
```

```
ls -l /dev/dsp
```

```
ls -l /dev/dsp0
```

```
ls -l /dev/dsp1
```

```
ls -l /dev/dsp2
```

```
ls -l /dev/dsp3
```

```
cat /proc/asound/cards
```

---

### Post by Merovius on 2008-10-18
here's the output,

transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename or host "/dev/dsp2"

script,

#!/bin/bash

killall zenity
killall tvtime
killall transcode
amixer -q set "Line" 100% unmute
amixer -q set "Analog Mix" 100% unmute
tvtime
amixer -q set "Line" 0% mute

REC=$(zenity --list --text "Choose a recording time" --radiolist  --column "Pick" --column "Recording time" 00:15:00 '00:15:00' 00:30:00 '00:30:00' 00:45:00 '00:45:00' 01:00:00 '01:00:00' 01:15:00 '01:15:00' 01:30:00 '01:30:00' 01:45:00 '01:45:00' 02:00:00 '02:00:00' 02:15:00 '02:15:00' 02:30:00 '02:30:00' 02:45:00 '02:45:00' 03:00:00 '03:00:00' 03:15:00 '03:15:00' 03:30:00 '03:30:00' 03:45:00 '03:45:00' 04:00:00 '04:00:00' 06:00:00 '06:00:00' 12:00:00 '12:00:00')
TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

transcode -x v4l2,v4l2 \
	-M 2 \
	-i /dev/video0 \
	-p /dev/dsp2 \
	-y ffmpeg \
	-F mpeg4 \
	-c ${REC} \
	-g 720x480 \
	-f 0,4 \
	-I 1 \
	-u 100 \
	-Q 3 \
	-Z 360x240,fast \
	-E 48000,16,2 \
	--lame_preset medium \
	-o ~/Desktop/${TODAY}-${NOW}.avi & zenity --text "Recording started at ${NOW} with ${REC} preset time" --notification

killall zenity
killall transcode 
amixer -q set "Line" 0% mute

I believe I need to correct the line with -p /dev/dsp2 \?

---

### Post by lovinglinux on 2008-10-18
> **Merovius said:**
> I believe I need to correct the line with -p /dev/dsp2 \?

Yes. Run the commands from my previous post to find which devices respond properly and replace the device in the line above.

---

### Post by Merovius on 2008-10-18
Changed dsp2 to dsp and it went a bit further then this,

[import_v4l2.so]: v4l2 audio grabbing
[import_v4l2.so]: v4l2 video grabbing
[import_v4l2.so]: resync disabled
[import_v4l2.so]: video grabbing, driver = cx8800, card = ATI TV Wonder Pro
[import_v4l2.so]: VIDIOC_S_FMT: : Invalid argument
[import_v4l2.so]: VIDIOC_S_FMT: : Invalid argument
[import_v4l2.so]: Pixel format conversion: UYVY [packed] -> YUV420 [planar] (slow conversion) 
[import_v4l2.so]: driver does not support setting parameters (ioctl(VIDIOC_S_PARM) returns "Invalid argument")
[import_v4l2.so]: checking colour & framerate standards: [NTSC-M] 
[import_v4l2.so]: receiving 30 frames / sec
[import_v4l2.so]: driver does not support cropping (ioctl(VIDIOC_CROPCAP) returns "Invalid argument"), disabled
[import_v4l2.so]: 24 buffers available
[import_v4l2.so]: VIDIOC_STREAMON: Invalid argument
video import module error: OPEN failed
[transcode] critical: failed to open input source

---

### Post by vmosorio on 2008-10-19
Sorry I disappeared yesterday, but I'm here again...

This is what I've got from the terminal commands:


victor@victor-desktop:~$ ls -l /dev/video0
crw-rw----+ 1 root video 81, 0 2008-10-19 11:16 /dev/video0


victor@victor-desktop:~$ ls -l /dev/video1
ls: cannot access /dev/video1: No such file or directory

victor@victor-desktop:~$ ls -l /dev/video2
ls: cannot access /dev/video2: No such file or directory

victor@victor-desktop:~$ ls -l /dev/video3
ls: cannot access /dev/video3: No such file or directory

victor@victor-desktop:~$ ls -l /dev/dsp
crw-rw----+ 1 root audio 14, 3 2008-10-19 11:16 /dev/dsp


victor@victor-desktop:~$ ls -l /dev/dsp0
ls: cannot access /dev/dsp0: No such file or directory


victor@victor-desktop:~$ ls -l /dev/dsp1
ls: cannot access /dev/dsp1: No such file or directory


victor@victor-desktop:~$ ls -l /dev/dsp2
ls: cannot access /dev/dsp2: No such file or directory


victor@victor-desktop:~$ ls -l /dev/dsp3
ls: cannot access /dev/dsp3: No such file or directory

victor@victor-desktop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdf6f8000 irq 17

It looks like it should be ok using video0 and dsp but it doesn't work!

---

### Post by lovinglinux on 2008-10-20
> **vmosorio said:**
> Sorry I disappeared yesterday, but I'm here again..

I'm sorry for disappearing too. There was a storm here this weekend and an "energy pole" (don't know the exact name of this thing) went down, killing energy and phone cables. No computer and no Internet for a while.

> **vmosorio said:**
> It looks like it should be ok using video0 and dsp but it doesn't work!

I guess these are the correct settings. I have been googling your issue and found a few posts describing the same problem, but no solution. 

Have you tried the PAL-M script? Probably not the solution, but it doesn't hurt to try.

---

### Post by vmosorio on 2008-10-20
Glad to know you have power back... storms here also in Honduras, way too much rain these days.
 I call those "light poles" and that should be the name I guess...

I guess these are the correct settings. I have been googling your issue and found a few posts describing the same problem, but no solution.

Have you tried the PAL-M script? Probably not the solution, but it doesn't hurt to try.

Thanks so much for your help and I have been googling for over a week trying to get a video and audio recording since I have done video recording using "motv" but as I said without audio.

I have my tv card (Kworld/Tevion V-stream Xpert tv PVR7134) running ok with tvtime but I have to load the drivers using modprobe which after googling I found the way to change the defaults the systems loads at the beginning by adding the lines at the end of etc/modprobe.d/options file...

I have been able to capture using cat /dev/vbio > test.mpg it creates a file but none of the players will play it back... I wonder if we could convert it to a real mpg or avi (much better) and then play it back but I don't know how.

Cheers

Vic

---

### Post by vmosorio on 2008-10-20
I just tried the PAL-M script and it works!  BUT no audio ... :( 

Is this telling you something?

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/victor/.tvtime/tvtime.xml
Thank you for using tvtime.
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] auto-probing source /dev/video0 (failed)
[transcode] V: import format    | unknown  (V=v4l2|A=v4l2)
[transcode] V: import frame     | 640x480  1.33:1  
[transcode] V: bits/pixel       | 0.521
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [32000,16,2]
[transcode] A: export format    | 0x1     PCM          [32000,16,2] 1024 kbps
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 5120 (5120.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 10 @ 640x480
[import_v4l2.so] v1.3.5 (2005-03-11) (video) v4l2 | (audio) pcm
[filter_resample.so] v0.1.4 (2003-08-22) audio resampling filter plugin
[filter_resample.so] options=(null)
[filter_resample.so] Invalid settings
[transcode] warning : filter plugin 'resample' returned error - plugin skipped
[filter_levels.so]: v1.0.0 (2004-06-09) Luminosity level scaler #0
[filter_levels.so]: scaling 0-255 gamma 1.000000 to 0-255
[filter_levels.so]: post-processing filter
[filter_smartyuv.so] (MMX) 0.1.4 (2003-10-13) Motion-adaptive deinterlacing
[export_ffmpeg.so] v0.3.13 (2004-08-03) (video) Lavc1d.51.38.0 | (audio) MPEG/AC3/PCM
[import_v4l2.so]: v4l2 audio grabbing
[import_v4l2.so]: v4l2 video grabbing
[import_v4l2.so]: resync enabled, margin = 1 frames, interval = 250 frames, 
[import_v4l2.so]: video grabbing, driver = saa7134, card = Kworld/Tevion V-Stream Xpert TV
[import_v4l2.so]: Pixel format conversion: YVU420 [planar] -> YUV420 [planar] (no conversion)
[import_v4l2.so]: driver does not support setting parameters (ioctl(VIDIOC_S_PARM) returns "Invalid argument")
[import_v4l2.so]: checking colour & framerate standards: [NTSC] 
[import_v4l2.so]: receiving 30 frames / sec
[import_v4l2.so]: frame size: 640x480
[import_v4l2.so]: cropcap bounds: 704x480 +0+44
[import_v4l2.so]: cropcap defrect: 704x480 +0+46
[import_v4l2.so]: cropcap pixelaspect: 11/10
[import_v4l2.so]: default cropping: 704x480 +0+46
[import_v4l2.so]: 8 buffers available
[export_ffmpeg.so]: INFO: output is mjpeg or ljpeg, extending range from YUV420P to YUVJ420P (full range)
[filter.c] Filter "levels=input=16-240" with args (levels=input=16-240)
[filter.c] Filter "levels=input=16-240" is already loaded.
[export_ffmpeg.so] Using FFMPEG codec 'mjpeg' (FourCC 'MJPG', Motion JPEG).
[export_ffmpeg.so]: WARNING: Interlacing parameters unknown, use --encode_fields
[export_ffmpeg.so]: INFO: No profile selected
[export_ffmpeg.so] Neither './ffmpeg.cfg' nor '~/.transcode/ffmpeg.cfg'
[export_ffmpeg.so] found. Default settings will be used instead.
[export_ffmpeg.so]: INFO: Starting 1 thread(s)
[export_ffmpeg.so]: INFO: Set display aspect ratio to input
[mjpeg @ 0xb58f76e8]removing common factors from framerate


Hope it does...

---

### Post by lovinglinux on 2008-10-21
> **vmosorio said:**
> I just tried the PAL-M script and it works!  BUT no audio ... :( 

Is this telling you something?
...
Hope it does...

Nice. At least half of the problem is solved. I should have suggested this before, but I didn't know you live in Honduras. I guess your country also use PAL like here. Try changing TVTime settings (the program settings not the recording script) also to PAL-M and see if it works well. I still see NTSC as default in the output you posted, so I guess TVTime is still configured as NTSC.

Try this script:

```

#!/bin/bash

killall zenity
killall tvtime
killall transcode
amixer -q set "Line" 100% unmute
tvtime
amixer -q set "Line" 100% unmute

REC=$(zenity --list --text "Choose a recording time" --radiolist  --column "Pick" --column "Recording time" 00:00:40 '00:00:40' 00:15:00 '00:15:00' 00:30:00 '00:30:00' 00:45:00 '00:45:00' 01:00:00 '01:00:00' 01:15:00 '01:15:00' 01:30:00 '01:30:00' 01:45:00 '01:45:00' 02:00:00 '02:00:00' 02:15:00 '02:15:00' 02:30:00 '02:30:00' 02:45:00 '02:45:00' 03:00:00 '03:00:00' 03:15:00 '03:15:00' 03:30:00 '03:30:00' 03:45:00 '03:45:00' 04:00:00 '04:00:00' 06:00:00 '06:00:00' 12:00:00 '12:00:00')
TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

#transcode -x v4l2=resync_margin=1:resync_interval=250,v4l2 \
transcode -x v4l2,v4l2 \
        -g 640x480 \
        -i /dev/video0 \
        -p /dev/dsp \
        -e 32000,16,2 \
        -N 0x1 \
	-J resample,levels,smartyuv \
        -w 4000 \
        -y ffmpeg \
        -F mjpeg \
	-c ${REC} \
	-o ~/Desktop/${TODAY}-${NOW}.avi & zenity --text "Recording started at ${NOW} with ${REC} preset time" --notification

killall zenity
killall transcode 
```

Also try to install Audacity and record from device "OSS: /dev/dsp". If you don't see an OSS device option run the following command:

```
sudo apt-get install alsa-oss
```

See if you can get sound when recording with Audacity and then try the script again.

---

### Post by vmosorio on 2008-10-21
Hello Lovinglinux,

Nope, we don't use PAL here in Honduras we also use NTSC as it would be crazy with all the US TV products we buy. There is something wrong in my configuration then because I get a nice AVI file when I tried the PAL settings of your script.

There is an OSS mixer in the system:  Realtek ALC662 rev1 (OSS Mixer) I haven't tried recording audio yet but I will check as per your suggestion and tell you what happens.

Thanks again ...

Victor

---

### Post by vmosorio on 2008-10-21
Hello Lovinglinux,

Nope, we don't use PAL here in Honduras we also use NTSC as it would be crazy with all the US TV products we buy. There is something wrong in my configuration then because I get a nice AVI file when I tried the PAL settings of your script.

There is an OSS mixer in the system:  Realtek ALC662 rev1 (OSS Mixer) I haven't tried recording audio yet but I will check as per your suggestion and tell you what happens.

Thanks again ...

Victor

---

### Post by lovinglinux on 2008-10-21
> **vmosorio said:**
> Hello Lovinglinux,

Nope, we don't use PAL here in Honduras we also use NTSC as it would be crazy with all the US TV products we buy. There is something wrong in my configuration then because I get a nice AVI file when I tried the PAL settings of your script.

There is an OSS mixer in the system:  Realtek ALC662 rev1 (OSS Mixer) I haven't tried recording audio yet but I will check as per your suggestion and tell you what happens.

Thanks again ...

Victor

Here is the "clever people" behind the government who decide which TV system is used. I remember that, in the old days, we had to install PAL-M converters on almost every new VCR, because most equipment were imported from US. Go figure.

The government recently adopted a modified version of the Japanese system for free-to-air HDTV, which is still under implementation and generated a lot of criticism. I don't watch free-to-air anyway, because is just a lot of crap.

---

### Post by vmosorio on 2008-10-22
Hello again...

It is recording audio BUT from the soundcard MIC input not LINE as it should be so that produces a distorted audio. I tried changing the capture source in the volume recording control from mic to line but it doesn't work.
I installed the OSS mixer as you adviced too.

Well, with this distorted audio I tried recording anyways and I also noticed that the audio is not synced with video; I read somewhere in a post that when that problem occurs, de-interlaced has to be enabled, how do I do that in the script?

There is something curious to me and the terminal output from the PAL script says NTSC as the format...? or it's just me that don't understand the code. I post the output at the end. 

I think we're very close to fix the problem and I can start recording my tapes and then unto DVDs.  Thanks so much again you're of great help.




 zenity: no process killed
tvtime: no process killed
transcode: no process killed
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/victor/.tvtime/tvtime.xml
Thank you for using tvtime.
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] auto-probing source /dev/video0 (failed)
[transcode] V: import format    | unknown  (V=v4l2|A=v4l2)
[transcode] V: import frame     | 640x480  1.33:1  
[transcode] V: bits/pixel       | 0.521
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [32000,16,2]
[transcode] A: export format    | 0x1     PCM          [32000,16,2] 1024 kbps
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 5120 (5120.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 10 @ 640x480
[import_v4l2.so] v1.3.5 (2005-03-11) (video) v4l2 | (audio) pcm
[filter_resample.so] v0.1.4 (2003-08-22) audio resampling filter plugin
[filter_resample.so] options=(null)
[filter_resample.so] Invalid settings
[transcode] warning : filter plugin 'resample' returned error - plugin skipped
[filter_levels.so]: v1.0.0 (2004-06-09) Luminosity level scaler #0
[filter_levels.so]: scaling 0-255 gamma 1.000000 to 0-255
[filter_levels.so]: post-processing filter
[filter_smartyuv.so] (MMX) 0.1.4 (2003-10-13) Motion-adaptive deinterlacing
[export_ffmpeg.so] v0.3.13 (2004-08-03) (video) Lavc1d.51.38.0 | (audio) MPEG/AC3/PCM
[import_v4l2.so]: v4l2 audio grabbing
[import_v4l2.so]: v4l2 video grabbing
[import_v4l2.so]: resync disabled
[import_v4l2.so]: video grabbing, driver = saa7134, card = Kworld/Tevion V-Stream Xpert TV
[import_v4l2.so]: Pixel format conversion: YVU420 [planar] -> YUV420 [planar] (no conversion)
[import_v4l2.so]: driver does not support setting parameters (ioctl(VIDIOC_S_PARM) returns "Invalid argument")
[import_v4l2.so]: checking colour & framerate standards: [NTSC] 
[import_v4l2.so]: receiving 30 frames / sec
[import_v4l2.so]: frame size: 640x480
[import_v4l2.so]: cropcap bounds: 704x480 +0+44
[import_v4l2.so]: cropcap defrect: 704x480 +0+46
[import_v4l2.so]: cropcap pixelaspect: 11/10
[import_v4l2.so]: default cropping: 704x480 +0+46
[import_v4l2.so]: 8 buffers available
[export_ffmpeg.so]: INFO: output is mjpeg or ljpeg, extending range from YUV420P to YUVJ420P (full range)
[filter.c] Filter "levels=input=16-240" with args (levels=input=16-240)
[filter.c] Filter "levels=input=16-240" is already loaded.
[export_ffmpeg.so] Using FFMPEG codec 'mjpeg' (FourCC 'MJPG', Motion JPEG).
[export_ffmpeg.so]: WARNING: Interlacing parameters unknown, use --encode_fields
[export_ffmpeg.so]: INFO: No profile selected
[export_ffmpeg.so] Neither './ffmpeg.cfg' nor '~/.transcode/ffmpeg.cfg'
[export_ffmpeg.so] found. Default settings will be used instead.
[export_ffmpeg.so]: INFO: Starting 1 thread(s)
[export_ffmpeg.so]: INFO: Set display aspect ratio to input
[mjpeg @ 0xb58dc6e8]removing common factors from framerate


Vic

---

### Post by lovinglinux on 2008-10-22
> **vmosorio said:**
> It is recording audio BUT from the soundcard MIC input not LINE as it should be so that produces a distorted audio. 

Are you sure the sound cable from the TV card is connected to the "Line In" input in the sound card?

If it is connected to the MIC input it is normal to get distorted sound, because the volume is too high for MIC input. But it doesn't make sense to capture sound from MIC if the cable is properly connected to the "Line In input". Is not feasible. So check your cables.

> **vmosorio said:**
> I tried changing the capture source in the volume recording control from mic to line but it doesn't work. 

Those controls never work for me either. I guess they control the recording volume when using the soundcard mixer. 


> **vmosorio said:**
> Well, with this distorted audio I tried recording anyways and I also noticed that the audio is not synced with video; I read somewhere in a post that when that problem occurs, de-interlaced has to be enabled, how do I do that in the script? 

The problem is that when you transcode using PAL-M a lot of frames are dropped, so the program has difficulties to sync the audio. I don't remember exactly the technical stuff about this, but this is "normal". I also have sync problems. 

Try replacing the following line accordingly:

replace ```
transcode -x v4l2,v4l2 \
```

with ```
transcode -x v4l2=resync_margin=1:resync_interval=250,v4l2 \
```

It doesn't work for me, but this is what I have found in the Transcode web site.

I watch the videos using gnome-mplayer, so I can easily re-sync the audio on-the-fly. If I want to keep the recording on my video library, then I re-encode it using Avidemux, using the audio shift feature. Is not complicated, just time consuming. You could write a script to do this and add it to the recording script.

I don't know how to enable de-interlacing, but I guess it won't improve audio sync for the PAL-M script.

> **vmosorio said:**
> There is something curious to me and the terminal output from the PAL script says NTSC as the format...? or it's just me that don't understand the code. I post the output at the end. 

That's why I asked you a few posts back to change the format in the TVTime OSD menu. I'm not sure if it will have any impact on the recording.


> **vmosorio said:**
> I think we're very close to fix the problem and I can start recording my tapes and then unto DVDs.  Thanks so much again you're of great help. 

Yes, we are. 

You are welcome.

---

### Post by vmosorio on 2008-10-22
>Are you sure the sound cable from the TV card is connected to the "Line In" input in the sound card?
If it is connected to the MIC input it is normal to get distorted sound, because the volume is too high for MIC input. But it doesn't make sense to capture sound from MIC if the cable is properly connected to the "Line In input". Is not feasible. So check your cables.<

Changing the cable to the mic input is how I discovered that it was recording audio, pluging it back to line in gives me mute videos. I think there is something wrong with the audio configuratio: this morning I downloaded Audacity and it doesn't record from line in either, so we have an issue here.

>I watch the videos using gnome-mplayer, so I can easily re-sync the audio on-the-fly.<

How you do that? I have mplayer as well but it's just a player... I downloaded videmux as well but I can't load the videos recorded with the script, it says: "couldn't open file"  I guess there is something to tweak in the video, audio and format options but I don't know what.

I'm trying the changes you gave me for the code.

Vic

---

### Post by vmosorio on 2008-10-22
>Are you sure the sound cable from the TV card is connected to the "Line In" input in the sound card?
If it is connected to the MIC input it is normal to get distorted sound, because the volume is too high for MIC input. But it doesn't make sense to capture sound from MIC if the cable is properly connected to the "Line In input". Is not feasible. So check your cables.<

Changing the cable to the mic input is how I discovered that it was recording audio, pluging it back to line in gives me mute videos. I think there is something wrong with the audio configuratio: this morning I downloaded Audacity and it doesn't record from line in either, so we have an issue here.

>I watch the videos using gnome-mplayer, so I can easily re-sync the audio on-the-fly.<

How you do that? I have mplayer as well but it's just a player... I downloaded videmux as well but I can't load the videos recorded with the script, it says: "couldn't open file"  I guess there is something to tweak in the video, audio and format options but I don't know what.

I'm trying the changes you gave me for the code.

Vic

---

### Post by lovinglinux on 2008-10-22
> **vmosorio said:**
> >Changing the cable to the mic input is how I discovered that it was recording audio, pluging it back to line in gives me mute videos. I think there is something wrong with the audio configuratio: this morning I downloaded Audacity and it doesn't record from line in either, so we have an issue here.

Oops. Sorry. I didn't realized that you have changed the inputs just for testing.

What are the available input devices listed in Audacity?

> **vmosorio said:**
> How you do that? I have mplayer as well but it's just a player...

Gnome-mplayer is another frontend to mplayer. It is a very nice frontend, with simple but nice interface. Download gnome-mplayer version 0.8.0 from[ here]("http://www.getdeb.net/app/GNOME+MPlayer"). This is the best version I have found so far.

After installing it, run the command below:

```
gnome-mplayer
```

To re-sync the audio on the fly just use the "+" and "-" keys.

> **vmosorio said:**
> I downloaded videmux as well but I can't load the videos recorded with the script, it says: "couldn't open file"  I guess there is something to tweak in the video, audio and format options but I don't know what.

Strange. Can you upload the recorded video somewhere so I can test it here? Just upload something like 15 seconds of recording.

---

### Post by vmosorio on 2008-10-22
I have mplayer, but will try that you mention as it could be some different.

I found this regarding Pulse Audio and this could the cause of my audio problem...


[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

Looks like Audacity and other applications don't have support for pulse audio, Keep you posted.

Trying right now.

---

### Post by lovinglinux on 2008-10-22
> **vmosorio said:**
> I have mplayer, but will try that you mention as it could be some different.

Yes, it is different. I think gnome-mplayer is much better than the default mplayer GUI. You can also install gecko-mediaplayer plugin for Firefox, to use the embedded gnome-mplayer.

> **vmosorio said:**
> I found this regarding Pulse Audio and this could the cause of my audio problem...
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
Looks like Audacity and other applications don't have support for pulse audio, Keep you posted.

I have pulse audio installed, but my sound configuration is set to use ALSA.

---

### Post by vmosorio on 2008-10-23
I have to fix the line in audio problem... when I try to record in Audacity I have sound in the speakers coming from the line feed but the software doesn't seem to recognize this and the input meter doesn't show any activity. 
I have removed PulseAudio and did the other steps but no luck, do you know of any other way to deal with this issue?

The video is still out of sync with the audio, I'd like to try the deinterlacing business and see if that helps, also can we record directly to mpeg with your script?

---

### Post by lovinglinux on 2008-10-23
> **vmosorio said:**
> I have to fix the line in audio problem... when I try to record in Audacity I have sound in the speakers coming from the line feed but the software doesn't seem to recognize this and the input meter doesn't show any activity. 
I have removed PulseAudio and did the other steps but no luck, do you know of any other way to deal with this issue?

Try setting everything to ALSA in Applications >> Preferences >> Sound  and select the device accordingly like this:

[[IMG]http://img122.imageshack.us/img122/5385/screenshotsoundpreferenop7.th.png[/IMG]](http://img122.imageshack.us/img122/5385/screenshotsoundpreferenop7.png)

> **vmosorio said:**
> The video is still out of sync with the audio, I'd like to try the deinterlacing business and see if that helps, also can we record directly to mpeg with your script?

The portion of my script that provides the scheduling and saving functionality is in red in the code below. This portion is not related to the issues you have or to the output encoding. The rest of the script is just transcode commands, so you can change the code as you need, according to [[COLOR="DarkRed"]**transcode options**[/COLOR]]("http://www.transcoding.org/cgi-bin/transcode?Transcode_Command_Line_Options").

```
[COLOR="Red"]#!/bin/bash

killall zenity
killall tvtime
killall transcode
amixer -q set "Line" 100% unmute
amixer -q set "Analog Mix" 100% unmute
tvtime
amixer -q set "Line" 0% mute

REC=$(zenity --list --text "Choose a recording time" --radiolist  --column "Pick" --column "Recording time" 00:15:00 '00:15:00' 00:30:00 '00:30:00' 00:45:00 '00:45:00' 01:00:00 '01:00:00' 01:15:00 '01:15:00' 01:30:00 '01:30:00' 01:45:00 '01:45:00' 02:00:00 '02:00:00' 02:15:00 '02:15:00' 02:30:00 '02:30:00' 02:45:00 '02:45:00' 03:00:00 '03:00:00' 03:15:00 '03:15:00' 03:30:00 '03:30:00' 03:45:00 '03:45:00' 04:00:00 '04:00:00' 06:00:00 '06:00:00' 12:00:00 '12:00:00')
TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )[/COLOR]

transcode -x v4l2=resync_margin=1:resync_interval=250,v4l2 \
        -g 640x480 \
        -i /dev/video0 \
        -p /dev/dsp2 \
        -e 32000,16,2 \
        -N 0x1 \
        -J resample,levels,smartyuv \
        -w 4000 \
        -y ffmpeg \
        -F mjpeg \
	[COLOR="Red"]-c ${REC} \
        -o ~/[COLOR="Red"]**Desktop**[/COLOR]/${TODAY}-${NOW}.[COLOR="black"]**avi**[/COLOR] & zenity --text "Recording started at ${NOW} with ${REC} preset time" --notification

killall zenity
killall transcode 
amixer -q set "Line" 0% mute
```
[/COLOR]

To change the output format you might need to change the lines below and the output format:
```

        -y ffmpeg \
        -F mjpeg \
```

       ```
-o ~/Desktop/${TODAY}-${NOW}.[COLOR="Red"]**avi**[/COLOR]
```

---

### Post by lovinglinux on 2008-10-23
[COLOR="Red"]**UPDATE:**[/COLOR] I have updated the scripts in the first post to allow choosing a file name when recording.

---

### Post by vmosorio on 2008-10-24
I have the sound settings the same way in your picture, still no recording from line.
I think there could be a problem with the system not detecting the sound card correctly, these new HD cards have problem in WinXP systems and don't work unless you have service pack2 installed.

I removed pulseaudio and installed esound, I didn't see any change after that but today when I play a video I get this error message:

AO: [pulse] Failed to connect to server: Connection refused

What is that? (the video plays ok though)

I changed to mpg but just the filename, the -F option was already there in the script, I get the file with mpg extension but the filesize is about the same as an avi ... why?

I tried adding the de-interlacing option but the script didn't work after that, I tried:

-I 1
and
-I on

neither of the lines worked and the script didn't produce any file, I'm not good for this stuff my friend, hahaha!

More later...

---

### Post by lovinglinux on 2008-10-24
> **vmosorio said:**
> I have the sound settings the same way in your picture, still no recording from line.
I think there could be a problem with the system not detecting the sound card correctly, these new HD cards have problem in WinXP systems and don't work unless you have service pack2 installed.

I guess you are correct, since you can't record using Audacity either. If the problem was due to video transcoding, then you should at least be able to record using Audacity. I think you should open a new thread for sound card issues. I'm sorry I can't be more helpful.

> **vmosorio said:**
> I removed pulseaudio and installed esound, I didn't see any change after that but today when I play a video I get this error message:

AO: [pulse] Failed to connect to server: Connection refused

What is that? (the video plays ok though)

I have no idea. I saw that tutorial that explains how to remove pulse audio, but I didn't tried it. I was afraid something like this happens after removing pulse audio.

The tutorial also an explanation on how to get pulse audio back. I guess you should try that.

> **vmosorio said:**
> I changed to mpg but just the filename, the -F option was already there in the script, I get the file with mpg extension but the filesize is about the same as an avi ... why?

AVI and MPG are just containers. What really matters is the encoder used (the -F option), so if you didn't changed it, the file size should be similar. I don't know if transcode will save the file with a default container like avi, but if you save the file with another extension it will work anyway. Usually you can rename avi's, mpeg's, mkv's to whatever video extension you want. If you have a good player and all necessary codecs, the video will play, independently of it's file extension. 

Obviously that if you rename an avi file to mkv for example, you won't get all the extra mkv features, because the player will recognize it as avi, no matter which extension you use. Try renaming some of your avi files to mp4 or mkv and then play them to see how this works.

> **vmosorio said:**
> I tried adding the de-interlacing option but the script didn't work after that, I tried:

-I 1
and
-I on

neither of the lines worked and the script didn't produce any file, I'm not good for this stuff my friend, hahaha!

Hahahah. I'm not good either. I've lost a few nights of good sleep trying to record the sound properly with my card. In my case, the sound was not only out of sync, but with different FPS, so everyone sounded like Donald Duck. It was terrible. After a few days I realized I was using the NTSC script, while my card is PAL-M. :oops:

---

### Post by mocha on 2008-11-01
This is a really nice script!  Thanks!

I'm using it with an old Hauppauge NTSC analog capture card.  It works fine, audio is in sync and so forth.  The problem is that the recorded video "jumps" around a bit.  You can see in some of the frames like a horizontal bar of video from a different frame, and the audio makes a slight skip or "pop".  I think it has something to do with the transcode settings.  I will try playing with them.  Do you have any suggestions?

I attached a screenshot.

---

### Post by lovinglinux on 2008-11-01
> **mocha said:**
> This is a really nice script!  Thanks!

I'm using it with an old Hauppauge NTSC analog capture card.  It works fine, audio is in sync and so forth.  The problem is that the recorded video "jumps" around a bit.  You can see in some of the frames like a horizontal bar of video from a different frame, and the audio makes a slight skip or "pop".  I think it has something to do with the transcode settings.  I will try playing with them.  Do you have any suggestions?

Thank you. I'm glad it works for you.

Yep, you have to play around with transcoding settings until you find the best combination to your system. Try recording in xvid format. I don't remember the exact code, but the transcode site should have this.

I guess is something like this:
```

        -y ffmpeg \
        -F xvid \
```

---

### Post by mocha on 2008-11-02
Still no luck.  Actually the only way I could get xvid to work was "-y xvid" and delete the "-F" switch.  I've also been playing with bitrate using "-w", that helps to keep the file size down.  I'm also using "-I 5" for better deinterlacing.  I wonder if it has something to do with my TVtime settings?  I played with those and it's not making a difference.

---

### Post by lovinglinux on 2008-11-06
> **mocha said:**
> Still no luck.  Actually the only way I could get xvid to work was "-y xvid" and delete the "-F" switch.  I've also been playing with bitrate using "-w", that helps to keep the file size down.  I'm also using "-I 5" for better deinterlacing.  I wonder if it has something to do with my TVtime settings?  I played with those and it's not making a difference.

Unfortunately, I don't know what else you could do to fix this. Maybe someone with the same card can give us a solution.

---

