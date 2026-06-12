---
title: "Sansa View FFMpeg Conversion Help"
date: 2010-11-25
forum: Multimedia Software
---

### Post by SoraDonaldGoofy on 2010-11-25
Hi guys, this is my first post! I have a Sansa View, and I want to be able to watch videos on it. GUI suggestions from Ubuntu Software Center appreciated, but I have been using a command line program called pacpl so far.
Once I got my mp4 videos, I thought I was all set, but the View said "Unsupported Media Format". I found out that the pixel rate wasn't in increments of 16.
Finally, I started using FFMpeg. My first command went as follows:

     ffmpeg -i 'input' -r 29.97 -vcodec libxvid -b 256k -acodec libfaac -ab 96k -bufsize 4M -qmax 51 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -ar 44100 -g 300 -s 320xInfinity -padtop -Infinity -padbottom -Infinity -ac 2 -f mp4 -y 'output'

I got this error message:

    Seems stream 1 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/stephan/Videos/Music Videos/Kiss The Rain With Lyrics.mp4':
  Duration: 00:04:17.72, start: 0.000000, bitrate: 382 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 25 tbr, 25 tbn, 50 tbc
Unable to parse option value "trell": undefined constant or missing (
Invalid value '+4mv+trell' for option 'flags'

I found out again that this command format was for older versions, and thus tried this:

    ffmpeg -i 'input' -acodec aac -ab 128k -vcodec mpeg4 -b 1200k -mbd 2 -flags +mv4+aic -trellis 1 -cmp 2 -subcmp 2 -s 320x180 -metadata title=X 'output'

This gave me this error message:

    Seems stream 1 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/stephan/Videos/Music Videos//Kiss The Rain With Lyrics.mp4':
  Duration: 00:04:17.72, start: 0.000000, bitrate: 382 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 25 tbr, 25 tbn, 50 tbc
Unknown encoder 'aac'

Then I read that you have to write libfaac instead of aac, but it still wouldn't work!

Finally I tried a different script that I found:

    ffmpeg -i 'input' -r 29.97 -vcodec libxvid -b 700k -acodec libfaac -ab 128k -bufsize 4M -qmax 51 -mbd 2 -flags +mv4+aic -trellis 1 -cmp 2 -subcmp 2 -s 320x180 -metadata title=X /'output'

This told me again that it didn't recognize "libfaac"

The reply to the thread I got this from reported it to be successful, I have no idea why it didn't work. HELP!

---

### Post by andrew.46 on 2010-11-26
Hi Sora,

[Looks like]("http://kb.sandisk.com/app/answers/detail/a_id/37") this device supports h.264 and aac in an mp4 container so this might be your best bet. Have a look at this guide which should get you started:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Andrew

---

### Post by SoraDonaldGoofy on 2010-11-26
[QUOTE=andrew.46;10164777]Hi Sora,

[Looks like]("http://kb.sandisk.com/app/answers/detail/a_id/37") this device supports h.264 and aac in an mp4 container so this might be your best bet. Have a look at this guide which should get you started:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Okay I'll try that

---

### Post by SoraDonaldGoofy on 2010-11-28
I got ffmpeg to work! Okay, so first I enabled the medibuntu repositories:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

Then I updated the ffmpeg codecs:

sudo apt-get install ffmpeg libavcodec-extra-52

Lastly I changed aac to libfaac, and it worked!

---

### Post by SoraDonaldGoofy on 2010-11-28
One more question, though. I ran this script:

me@eeepc:~$ ffmpeg -i ~/example.flv -acodec libfaac -ab 128k -vcodec mpeg4 -b 1200k -mbd 2 -flags +mv4+aic -trellis 1 -cmp 2 -subcmp 2 -s 320x180 -metadata title=X ~/example.mp4

I tried playing the mp4 on my sansa view, and got the unsupported "media format" message. I know it gave me this message because of properties like resolution, pixel rate, bit rate, etc., that it couldn't read/adjust. Can anyone give me the correct properties to set for the video? that would be helpful

---

