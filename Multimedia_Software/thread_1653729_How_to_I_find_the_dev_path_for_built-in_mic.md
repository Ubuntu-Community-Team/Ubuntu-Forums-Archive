---
title: "How to I find the /dev path for built-in mic ?"
date: 2010-12-27
forum: Multimedia Software
---

### Post by KaYnemO on 2010-12-27
Hey all.
  tried to google this for a couple of days, but can't seem to figure it out. Here it is - I am using VLC to capture video from my webcam. So to set the video device I use /dev/video0 (built in webcam), but I need to specify the path to the built in mic and I can't find what that path is. If it help any, it seem my system is configured to use pulse audio instead of alsa. Is there any script to run to find where my mic is "pathed" at?
 arecord -l returns this:

$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

while ls /dev/audio* returns this:

~$ ls /dev/audio*
/dev/audio

Neither helps !! D'oh ! Please help !

---

### Post by KaYnemO on 2010-12-28
bump

---

### Post by lidex on 2010-12-29
Have you seen this:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
More:
[http://ubuntuforums.org/showthread.php?t=1446884](http://ubuntuforums.org/showthread.php?t=1446884)

---

### Post by KaYnemO on 2010-12-29
> **lidex said:**
> Have you seen this:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
More:
[http://ubuntuforums.org/showthread.php?t=1446884](http://ubuntuforums.org/showthread.php?t=1446884)

You know - these above links discuss the troubleshooting of mic for skype etc. My mic works, but I can figure out where (pathwise) it is located.

---

### Post by lidex on 2010-12-29
From first link above...
> 3.1. Configuring Webcam Software

In some cases your media player (VLC, mplayer, amongst others) will need to know the video and audio device files for your webcam. Before you plug in your webcam, try the following two command at a console:

UVC
ls /dev/video*
ls /dev/audio*

Make a note of the devices appearing. Now plug in your webcam, allow the system a few seconds to register the device, and run the two commands again. The new appearances should belong to your webcam (for instance, /dev/video0 and /dev/audio2). If nothing new appears, you may need to switch your webcam on. For a built-in webcam, you may have a function key to do so.

3.2. VLC

3.2.1. Using the GUI

In VLC, choose 'Open capture device' from the file menu and enter the video and audio device files (see above) in video device name and audio device name, respectively. If you just want a 'mirror' (to see what the webcam is showing), click 'OK' and you're done. If you wish to record, tick off 'Stream/save' in the 'Advanced options' section. Click the settings button right next to it. Tick 'File' off under 'Outputs' and enter a filename. Encapsulation method can be left at the default (MPEG TS). Under 'Transcoding options', tick 'Audio codec' and 'Video codec'. These can also safely be left the defaults (obviously greater compression results in lower file sizes, so experiment). Click 'OK' in the Settings screen and once again in the main webcam screen (Video4linux). If you want to have more control, you can access several settings, including resolution, by clicking the Advanced options button. 

That doesn't help?

---

### Post by KaYnemO on 2011-01-04
Nope 'cause

ls /dev/audio* returns this:

~$ ls /dev/audio*
/dev/audio

which helps me none :(

---

### Post by lidex on 2011-01-04
And you ran those commands before **and** after plugging in the webcam?

---

### Post by KaYnemO on 2011-01-06
> **lidex said:**
> And you ran those commands before **and** after plugging in the webcam?

Well, in my case it's irrelevant as the webcam is built in my notebook (an Orbicam) and has no mic, the mic, however, is also built-in and is nowhere near the cam, it is right next to the keyboard... Thanks for replying, btw, I appreciate it...

---

### Post by lidex on 2011-01-07
Gotcha.

---

### Post by st0kes on 2011-03-13
> **KaYnemO said:**
> Well, in my case it's irrelevant as the webcam is built in my notebook (an Orbicam) and has no mic, the mic, however, is also built-in and is nowhere near the cam, it is right next to the keyboard... Thanks for replying, btw, I appreciate it...

Did you solve this? I'm also trying to figure it out... 

I have a similar situation with a usb video capture card and 3.5m jack for audio in. Can't figure out what the mic device is called for vlc though.

---

### Post by KaYnemO on 2011-03-14
> **st0kes said:**
> Did you solve this? I'm also trying to figure it out... 

I have a similar situation with a usb video capture card and 3.5m jack for audio in. Can't figure out what the mic device is called for vlc though.


Nope... no one answers anymore...or any less :)

---

### Post by lidex on 2011-03-18
Apparently the vlc documentation is old. Seems ubuntu alsa changed the device schemes, probably when they dropped oss support. Try contacting someone over at vlc development or the ubuntu audio guys. I'm willing to bet someone knows the answer, it's just not documented.

---

### Post by Koalin on 2011-05-27
Hello,
I'm in the same situation. Trying to know the path of my mic to record video/audio with VLC. 
ls /dev/audio* returns no such file or directory

Anyone got it working?

Thanks.

---

### Post by skabople on 2012-01-04
video4Linux FTW... Ok now that I got that out...

path to audio devices:  /dev/snd

audio devices will look like this:
```

gvrv@thenet:/dev/snd$ ls -il
total 0
7644 drwxr-xr-x  2 root root      60 2012-01-04 09:11 by-path
7621 crw-rw----+ 1 root audio 116, 7 2012-01-04 09:11 controlC0
7620 crw-rw----+ 1 root audio 116, 6 2012-01-04 09:11 hwC0D0
7619 crw-rw----+ 1 root audio 116, 5 2012-01-04 10:36 pcmC0D0c
7618 crw-rw----+ 1 root audio 116, 4 2012-01-04 10:55 pcmC0D0p
6955 crw-rw----+ 1 root audio 116, 3 2012-01-04 09:11 seq
6895 crw-rw----+ 1 root audio 116, 2 2012-01-04 09:11 timer
gvrv@thenet:/dev/snd$ ls -il by-path
total 0
7645 lrwxrwxrwx 1 root root 12 2012-01-04 09:11 pci-0000:00:1b.0 -> ../controlC0

```Now, what to enter into VLC for the audio path I'm sorry but I can't help you...
Since the audio device sort of has multiple devices on it... left speaker, right speaker, mic, aux ports, and so forth.

I hope this helps...

--T}{E GvRv--

---

