---
title: "time lapse with vlc"
date: 2011-06-15
forum: Multimedia Software
---

### Post by Rosscopico on 2011-06-15
Hi everyone,
I am still very new to Linux based systems, so pls be gentle!

I am trying to make a time lapse video currently with vlc. I have been doing lots of reading on this topic & have made many clumsy attempts, all of which have failed. 

So far I have the webcam working (as I can see myself) and can manually take snapshots in vlc & locate them in my Pictures directory..
But I am having a lot of difficulty automating the process.

The command line string I found to use is this
```
cvlc v4l2:// :v4l2-dev="/dev/video0" -V "image" --image-out-prefix img --image-out-format jpg --image-out-ratio 10 --v4l-fps 30
```So, do I name the webcam, or do I have to figure out the name issued to it by the system?

Very confused!:confused:

---

### Post by Rosscopico on 2011-06-16
So I've got the device name part sorted out. I can get the webcam to turn on, but the output to file is not working.
Here is the code and the output
```
ccvlc v4l2:// :v4l2-dev="/dev/video0" -V "image" --snapshot-path ~/home/ross/webcam/ 

VLC media player 1.1.9 The Luggage (revision exported) 
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS") 
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE") 
[0x9cca9c4] dummy interface: using the dummy interface module... 
[0x9cff6dc] main video output error: video output creation failed 
[0x9cce7fc] main decoder error: failed to create video output
```

Pls help!!

---

### Post by Rosscopico on 2011-06-17
Ok, so Ive learned that there is no video output module called image. So here is the new code, and its output.
```
vlc v4l2:// :v4l2-dev="/dev/video0" --vout ~/ross/Videos/webcam
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8e93914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1308058681)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:4250): Gtk-WARNING **: Locale not supported by C library.
   Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
[0x921f5ac] main video output error: video output creation failed
[0x920f494] main decoder error: failed to create video output

```
So, the webcam is turning on, VLC is opening, but its failing to create video output. Can anyone offer any suggestions as to why?:confused:

---

### Post by Rosscopico on 2011-06-17
So after playing around with some different commands, Im getting the webcam to switch on as before, vlc is opening & I can see myself in the webcam. However, it is not taking snapshots, as no files are being created in the specified directory , and I cant figure out how to get it to save an image every x frames, to be used for time lapse.
Here is the code and its output
```
cvlc v4l2:// :v4l2-dev="/dev/video0" mediadirs s video_dir --snapshot-path ~/ross/Videos/webcam --snapshot-prefix img --snapshot-format jpg
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x89c3784] dummy interface: using the dummy interface module...


```

---

### Post by Rosscopico on 2011-06-21
I got it working, the code I used was:-
```
cvlc v4l2:// :v4l2-dev="/dev/video0" --video-filter=scene --vout=dummy --aout=dummy --intf=dummy --scene-format=png --scene-ratio=50 --scene-prefix=snap --scene-path=/home/ross/Videos/Webcam/web4 v4l2:// vlc://quit
```

---

### Post by Rosscopico on 2012-12-16
I have found with Lubuntu & VLC 2.0.4 that the required terminal command is```
cvlc v4l2:// :v4l2-dev="/dev/video1" --video-filter=scene --vout=dummy --aout=dummy --intf=dummy --scene-format=jpg --scene-ratio=10 --scene-prefix=snap --scene-path=/home/ross/Videos/Webcam v4l2:// vlc://quit
```

---

### Post by overdrank on 2012-12-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

