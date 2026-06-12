---
title: "Transcode/encode video for Samsung YP-Q2"
date: 2009-12-05
forum: Multimedia Software
---

### Post by garryknight on 2009-12-05
This is a short tutorial on how to encode video for playback on the Samsung YP-Q2 personal media player. Normally you have to reboot into Windows and run Samsung's EmoDio program to encode video and transfer it to the device. This tutorial uses the ffmpeg program under Linux, thus avoiding a reboot. You need to know how to access a command line, for example by using KDE's Konsole. There are plenty of starter tutorials on the net that show you how to do this with your particular desktop.

**DISCLAIMER:** You use any of the commands in this tutorial at your own risk. I'm not yet all that familiar with ffmpeg so there might be better ways of achieving the same results; if so, I'd welcome feedback on this. Also, my method produces videos of a particular quality; how that relates to the three available quality settings output by EmoDio, I've no idea. Maybe someone who knows ffmpeg better than I do could comment on this.

EmoDio produces a file with a .svi extension that is a 320 x 240 pixel MPEG-4 video stream coded at 15 frames per second together with a 44100 Hz, 128 Kbit per second stereo MP3 stream. These are the parameters that need to be fed to ffmpeg to produce something that the Q2 will recognise as playable. It's possible that the video produced might also be playable on other Samsung devices such as the Q1. If you have one of these devices, by all means try this method and let me know the results.

Here's how we convert the file:

```
ffmpeg -i input.mov -acodec libmp3lame -ar 44100 -ab 128k -ac 2 -vcodec mpeg4 -b 1024k -r 15 -s qvga -f avi output.svi

```Here's an explanation of the parameters I used in that command:
```

-i input.mov        this is the input file
-acodec libmp3lame    we encode the audio using the MP3 codec
-ar 44100        we want to output 44100 Hz audio
-ab 128k        output audio at 128 kbits per second
-ac 2            output stereo audio
-vcodec mpeg4        we encode the video using the MPEG-4 codec
-b 1024k        maximum bitrate of 1024 kbits per second
-r 15            frame rate of 15
-s qvga            screen size 320 x 240 pixels (QVGA size)
-f avi            force the output format to AVI
output.svi        the output file name

```I should also point out that you don't have to tell ffmpeg what the format of the input video is in as it will know by inspecting the file itself. So you can start your command with
    ffmpeg -i input.mov ...
    ffmpeg -i input.flv ...
    ffmpeg -i input.wmv ...
and so on.


**Making it simpler**

Here's a bash script so you don't have to remember all of those parameters. If you save it as, say, "q2video" then make it executable with the command "chmod +x q2video", you can use it as, for example, "q2video inputfile.mov". It will create a Q2-compatible output file called inputfile.svi.

```

#!/bin/bash

# function to show program usage
function usage
{
    echo Usage: q2video inputfile
    echo e.g.   q2video myvideo.mov
    echo Converts video inputfile to inputfile.svi
    echo in a format suitable for the Samsung Yp-Q2 PMP
    exit
}

# ensure the input file exists
if [ ! -e $1 ]; then
  echo "Filename $1 doesn't exist"
  usage
fi

# get output filename from $1
OUTFILE=${1%.???}.svi

# Tell the user what we're doing
echo -n "Converting $1 to Q2 video file $OUTFILE using ffmpeg "
ffmpeg -i $1 -acodec libmp3lame -ar 44100 -ab 128k -ac 2 -vcodec mpeg4 -b 1024k -r 15 -s qvga -f avi $OUTFILE

```
**Transferring the completed video to the player**

Now you know how to convert your videos, here's some more good news: you don't have to reboot into Windows in order to get the video onto the Q2. If you go into the Q2's Settings and look in the System submenu at the PC Connection setting, you'll see 2 options: MTP and MSC. The first option is used when you want the Q2 to be treated as a media device and is the normal setting for using the Q2 with EmoDio or Windows Media Player. The second option is used when you want the Q2 to be treated as a removable storage device, i.e. a removable flash drive. The good news is that you can set it to MSC and leave it that way and the Q2 should work perfectly with EmoDio and WMP, and will work perfectly with Linux too.

So, having set the PC Connection setting to MSC, just plug your Q2 into a USB port and it will be available as a mounted drive. If, like me, you're running KDE 4, a notification will pop up at the bottom-right of the screen and you can click the Q2 entry then select Open with File Manager. You can then navigate to the Videos folder on the Q2 and then drag and drop your video file there. If you're using anything other than KDE4, you might have to manually mount the device. I only know KDE so I can't help you with this but there will be plenty of tutorials available on the net.



**Tips and tricks**

1. You can add -y before the output file name to allow ffmpeg to overwrite any existing file with the same name. I can't think why you might need to do this but if you do, the option is there:
```

ffmpeg -i input.mov -acodec libmp3lame -ar 44100 -ab 128k -ac 2 -vcodec mpeg4 -b 1024k -r 15 -s qvga -f avi -y output.svi

```2. It appears that some .flv files need to be converted to another format first (eg mpg). I don't know why this is; I just found it to be true with some files I downloaded from YouTube. If you have the same problem, just do the job in two passes:
```

ffmpeg -i input.flv ouput1.mpg
ffmpeg -i output1.mpg -acodec libmp3lame -ar 44100 -ab 128k -ac 2 -vcodec mpeg4 -b 1024k -r 15 -s qvga -f avi -y output2.svi

```3. Given the size limits that YouTube imposes, some "programmes" consist of more than one video. You can join them together before encoding them for the Q2 by converting each downloaded file into .mpg format first, then concatenating them, then converting the result:
```

ffmpeg -i input1.flv output1.mpg
ffmpeg -i input2.flv output2.mpg
ffmpeg -i input3.flv output3.mpg
cat output1.mpg output2.mpg output3.mpg >finalinput.mpg
ffmpeg -i finalinput.mpg -acodec libmp3lame -ar 44100 -ab 128k -ac 2 -vcodec mpeg4 -b 1024k -r 15 -s qvga -f avi -y finaloutput.svi

```4. Just as a matter of interest, here's how to encode a .svi for the Q2 using mencoder:
```

mencoder input.mov -o output.avi -ovc lavc -lavcopts vcodec=mpeg4 -vf scale=320:240,crop=320:240 -mf fps=25 -oac mp3lame -lameopts cbr:br=128
mv output.avi output.svi

```Note that the resulting filename has to have the .svi extension or the Q2 won't recognise it. Hence the rename.



**A few extra goodies**

The ffmpeg app is an excellent addition to any Linux installation as it can be used for quite a few different jobs. Here are four more for your enjoyment. Three of them are useful to Q2 owners, the fourth to YouTube fans.

1. Grab the soundtrack of a video as an MP3
  ffmpeg -i input.flv -vn -acodec libmp3lame -ar 44100 -ab 128 -ac2 output.mp3
This produces a stereo MP3 encoded at 44100 Hz, 128 kbits per second. Change the 44100 and 128 above to suit your preferences.


2. Convert a WAV to an MP3
  ffmpeg -i input.wav -acodec libmp3lame -ar 44100 -ab 128 -ac 2 output.mp3
This is useful if you've recorded something using a programme that outputs the result as a .wav file.


3. Create a screencast
  ffmpeg -f x11grab -s 1440x900 -r 25 -i :0.0 screencast.mpg
This particular form of the command assumes that your screen is 1440 x 900 pixels. You need to output the result to a .mpg format file so that you can press Ctrl+C to stop the recording and still leave a playable file. You can convert the resulting .mpg file into .svi format if you want to take your screencasts with you on your Q2.


4. Convert any video to an .flv file suitable for uploading to YouTube
  ffmpeg -i input.mpg -ar 22050 -acodec libmp3lame -ab 32K -r 25 -s 320x240 -vcodec flv output.flv


That's all, folks. Hope this all proves useful to someone. I'd welcome any feedback, particularly on how the I could tune the ffmpeg command I've show you here so that it produces smaller files without too much loss of quality. At the moment, some output files are twice as big as the input files and I'm not sure why.

---

### Post by knowmad on 2009-12-26
Nice post. I've tried to use the info to encode and copy files to a YP-S3 without any luck. I've converted my unit to the UMS firmware which is automounted in Ubuntu (Karmic). Music files copy fine. However when I copy converted video files to the device, I inevitably receive the error "This file is an unsupported type".

I've also tried re-encoding the svi files that come with the device and have the same error despite being able to view them in Gnome's movie player, totem.

---

### Post by garryknight on 2009-12-27
I think there's a Java app floating about that can convert some videos to the S3 format; I came across it while hunting for something for the Q2 but don't remember what it's called. I'm sure you could find it fairly easily, either through searching this forum or through Google.

If you have access to Windows and can run the Samsung video encoder, you should be able to find out what parameters you would need to feed to ffmpeg to code for the S3. As I said in my post above, I looked in EmoDio to find the parameters for the Q2 and after feeding them to ffmpeg, I was surprised first of all when I got the same message as you did, then I changed the filename extension to .svi and only then would the Q2 accept it.

If you don't have access to Windows, have a look in Totem to see if you can find out some information about the .svi encoding. Also, I know vlc can play .svi files but I'm not sure where you'd look to find out which audio and video stream parameters the S3 uses since I'm currently in a coffee bar on my netbook. But if you hunt around, I'm sure you'll come up with something.

And I don't think it's worth trying to re-encode the .svi files that came with the S3. Find a .wmv, .avi or .mp4 file and try it on that.

You might want to start off by searching these forums for something like "Samsung YP-S3 convert video". When I tried that, I got a few hits that were worth following up.

---

### Post by garryknight on 2009-12-27
Ok, I'm at home now and I've had a chance to check out one thing that I put in my previous post. If you run vlc and open a .svi file that has been encoded to run on your S3, you can look in the menu under Tools, Codec Details, then make a note of the video codec, x&y resolution, and frame rate, and the audio codec, sample rate, and bit rate. Then plug these into ffmpeg as shown in my first post.

I'd be interested to know if this works for you.

---

### Post by knowmad on 2009-12-27
Hi Garry,

Thanks for the feedback. This evening I was able to get one of my files converted using EmoDio. I found that all the settings I've been using with ffmpeg were correct. The only difference I see in the files is the INFOIST section in the head of the avi (looked at using the `strings` command).

I found a Java app called jSVIcoder which didn't support YP-S3 directly. I tried using it with the S5 settings but that failed. It appears to me that the firmware in the S3 is looking for more than just the .svi extension which is a bummer. I may try playing with a hex editor to see if I can have any luck getting the S3 to recognize my converted videos.

One interesting point is that the avi clip that I encoded with EmoDio was first encoded with mencoder. In fact, the mencoder converted clip worked better than the EmoDio converted original avi which was 160x120.


William

---

### Post by garryknight on 2009-12-28
> **knowmad said:**
> 
I found a Java app called jSVIcoder which didn't support YP-S3 directly.


That was the one I was referring to - couldn't remember its name. Sorry to hear it didn't work. If you know any Java, you could try playing with the source file.

> 
It appears to me that the firmware in the S3 is looking for more than just the .svi extension which is a bummer.
Yes. My Q2 needs to have everything exactly right. Not just the .svi extension but the codec, width, depth, frame rate, sample rate, everything. I even tried playing with the aspect ratio to see if I could get the picture to display at 16:9 on the 4:3 screen; no dice, it just came out with its perennial complaint: "This file is an unsupported type."

> 
I may try playing with a hex editor to see if I can have any luck getting the S3 to recognize my converted videos.
Good idea. And if you like, I can take a look at a .svi file that you **know** plays ok on your S3 and see if I can spot the difference between it and my Q2 vids.

> 
One interesting point is that the avi clip that I encoded with EmoDio was first encoded with mencoder. In fact, the mencoder converted clip worked better than the EmoDio converted original avi which was 160x120.
That *is* interesting. You said in your original reply to my post:

> **knowmad said:**
> Nice post. I've tried to use the info to encode and copy files to a YP-S3 without any luck.


Did you also try using mencoder on the original video, or just ffmpeg? In my post at the top of this thread I gave the parameters for use with the Q2:

```

mencoder input.mov -o output.avi -ovc lavc -lavcopts vcodec=mpeg4 -vf scale=320:240,crop=320:240 -mf fps=25 -oac mp3lame -lameopts cbr:br=128
mv output.avi output.svi

```My guess is that this is exactly what you were referring to when you said that the avi clip had first been encoded using mencoder.

> 
I've converted my unit to the UMS firmware which is automounted in Ubuntu (Karmic).
I wonder if this version of the firmware requires something in the .svi which the original firmware didn't. It seems very unlikely...

---

### Post by FakeOutdoorsman on 2009-12-28
> **garryknight said:**
> Good idea. And if you like, I can take a look at a .svi file that you **know** plays ok on your S3 and see if I can spot the difference between it and my Q2 vids.

Perhaps the S3 is looking for a specific video FourCC.  You can add a video FourCC with the *-vtag* option in FFmpeg.  Install [mediainfo](http://mediainfo.sourceforge.net/en/Download/Ubuntu) and post the output from a video created with the Samsung Video encoder or any other video that currently works with the device.

---

