---
title: "Audio profiles unavailable in Sound Juicer &amp; Recorder"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by ahaslam on 2007-05-05
Hi, got a weird problem in Feisty that didn't exist under Dapper.
Some of my audio profiles aren't available in Sound Juicer & Sound Recorder.

If I try & edit/add profiles from the Sound Juicer preferences it freezes & wont allow me to add/amend anything. Using 'gnome-audio-profiles-properties' allows the amendments but they're not available from within my applications.

The attached screenshot should illustrate better:
[ATTACH]31871[/ATTACH]

Any thoughts would be appreciated ;)

---

### Post by ahaslam on 2007-05-06
All of the profiles are active, I don't understand what's wrong, even a couple of default options aren't available :-k

---

### Post by Astenorh on 2007-05-07
You are using the old gstreamer. To update  use 

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gl gstreamer0.10-pitfdll gstreamer0.10-sdl gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse mpg321
```

---

### Post by ahaslam on 2007-05-07
0.10 here, as default in Fiesty.

---

### Post by pkid on 2007-12-25
I have exactly the same issue!  I have the latest version of GStreamer.  Just to be sure I tried to install the packages listed in one of the above posts but the problem continues.  I am running Ubuntu 7.10

---

### Post by TwoFlightsDown on 2007-12-25
I'm new to Ubuntu, but I'm trying to learn.  When I tried to install the packages in your post, I got this message and I'm not sure what it means:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.10-plugins-bad: Depends: libgsm1 (>= 1.0.10) but it is not installable
                             Depends: libmpcdec3 but it is not installable
  gstreamer0.10-plugins-bad-multiverse: Depends: libmjpegtools0c2a (>= 1:1.8.0) but it is not going to be installed
  gstreamer0.10-plugins-ugly: Depends: libid3tag0 (>= 0.15.1b) but it is not installable
                              Depends: libmad0 (>= 0.15.1b) but it is not installable
  mpg321: Depends: libid3tag0 (>= 0.15.0b) but it is not installable
          Depends: libmad0 (>= 0.15.1b) but it is not installable
E: Broken packages


I'm don't know what this means or how to go about fixing it.  I get this message for a lot of programs and things I try to add.  Am I doing something wrong or have I installed something incorrectly?  

Any help or insight would be greatly appreciated.

---

### Post by TwoFlightsDown on 2007-12-25
Oh, I got it now.  My repositories weren't all enabled.  That's why I kept getting that message.

---

