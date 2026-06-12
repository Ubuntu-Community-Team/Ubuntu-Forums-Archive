---
title: "VLC stopped working"
date: 2012-03-02
forum: Multimedia Software
---

### Post by girishk_007 on 2012-03-02
Hello

I am a ubuntu neophyte, currently using Ubuntu 11.10. I upgraded VLC player yesterday to VLC 2.1.0 and now no video plays. All I get is the audio stream with no video. I have installed the restricted extras and still nothing happens. What could be the problem and how do I fixed it


cheers

Girish

---

### Post by winh8r on 2012-03-02
Did you install it following these instructions?:

[http://www.videolan.org/vlc/download-ubuntu.html]("http://www.videolan.org/vlc/download-ubuntu.html")

---

### Post by girishk_007 on 2012-03-02
Initially I installed VLC using synaptic. But VLC stopped working properly after I updated VLC. Also libavcodec-extra-52 is not present using synaptic, libavcodec-extra-53 is. What is the difference between these two libraries


cheers

Girish

---

### Post by andrew.46 on 2012-03-02
> **girishk_007 said:**
> I am a ubuntu neophyte, currently using Ubuntu 11.10. I upgraded VLC player yesterday to VLC 2.1.0 and now no video plays. 

Seems a little odd as official release is still 2.0.0, where did you get your version of vlc from?

---

### Post by rojaasensei on 2012-03-02
I'm using 2.0.0-6 vlc

It could be you got an incomplete update.

Try sudo apt-get update from the command line.  When done see if your update manager has some vlc updates.  

This has happened to me in the past.

---

### Post by girishk_007 on 2012-03-03
I used this link for a daily build of VLC:
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

I tried the update - did not fix the problem
Now I also removed the daily build repository and unistalled VLC and re-installed it using just the universe repository. Does not fix the problem though. I keep getting these error messages

"VLC does not support the audio or video format "mp4v". Unfortunately there is no way for you to fix this."

or 

"VLC does not support the audio or video format "h264". Unfortunately there is no way for you to fix this."

The video stream does not work but the audio stream is fine


cheers

Girish

---

### Post by girishk_007 on 2012-03-03
The current VLC version (from the universe repository) is 1.1.12


cheers

Girish

---

### Post by rojaasensei on 2012-03-03
> **girishk_007 said:**
> I used this link for a daily build of VLC:
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

I tried the update - did not fix the problem
Now I also removed the daily build repository and unistalled VLC and re-installed it using just the universe repository. Does not fix the problem though. I keep getting these error messages

"VLC does not support the audio or video format "mp4v". Unfortunately there is no way for you to fix this."

or 

"VLC does not support the audio or video format "h264". Unfortunately there is no way for you to fix this."

The video stream does not work but the audio stream is fine


cheers

Girish

The ppa deb [http://ppa.launchpad.net/n-muench/vlc/ubuntu](http://ppa.launchpad.net/n-muench/vlc/ubuntu) oneiric main updates about once a week, it is stable

---

### Post by girishk_007 on 2012-03-03
Hi
I updated the VLC from the PPA but still does not work.
I checked thge other video players too -  the movie player that comes with ubuntu does not work, but banshee and xine works ok. When I use WinFF that uses ffmpeg to convert video files I get the following error:
Error while opening encoder for output stream #0.0

It seems that it might be a problem with video encoder!How do I debug what the problem is and how do I fix it.


cheers

Girish

---

### Post by P-I H on 2012-03-04
I haven't installed VLC 2.0 on 11.10, but I am using it on my 12.04 test system.
The new VLC behaves differently when playing HD media compared to the older version. With the old version I was able to start play from the folder, but in the the version I have to select the 00000.m2ts file.

---

