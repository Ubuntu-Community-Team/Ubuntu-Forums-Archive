---
title: "Is there a motion activated webcam application?"
date: 2011-05-11
forum: Multimedia Software
---

### Post by Maheriano on 2011-05-11
I want to set up a webcam to point out my window and watch the back patio but only record when there's movement. Anything available?

the motion detection would be easy, just take an image snapshot every second, store it, take another and compare the checksum on both to see if the image changed. If so, start recording.

---

### Post by Maheriano on 2011-05-12
I installed Zoneminder from the repositories, how do I get it to work? How do I open it?

---

### Post by jamesjenner on 2011-05-12
It's not a 'gui' application it's a web based application. And as such it does require a little bit of configuration before you can use it.

I suggest you go to the zoneminder web site and read the documentation, which has now been moved to a wiki.

To make it easy for you you can use the following link:

[http://www.zoneminder.com/wiki/index.php/Documentation]("http://www.zoneminder.com/wiki/index.php/Documentation")

I would review the notes on installing from a deb and then look at the tutorial links are:

[http://www.zoneminder.com/wiki/index.php/Documentation#Installation_from_a_.deb]("http://www.zoneminder.com/wiki/index.php/Documentation#Installation_from_a_.deb")
 
and

[http://www.zoneminder.com/wiki/index.php/Documentation#Tutorial]("http://www.zoneminder.com/wiki/index.php/Documentation#Tutorial")

The second one tells you how to run it right at the start, but just installing via the Ubuntu Software Centre isn't enough.

Cheers,

James

---

### Post by no2498 on 2011-05-12
is a program called motion 
it saves its pics in your home folder
you start and stop in in a terminal
it must be off before you use any other webcam app like skype cheese

---

### Post by wkulecz on 2011-05-12
> just take an image snapshot every second, store it, take another and compare the checksum on both to see if the image changed. If so, start recording

In your dreams!  There is a lot more to it than that!  Changes in light level as clouds go by, motion you don't want to record -- insects, small anaimals, incidental motion from the wind, all make the "obvious" solutions generally fail.

Motion is probably a better choice if you are only using a single camera.  I'm using zoneminder, but in my tests motion had far superior immunity to changing light levels.

I've found Zoneminder to be unstable when changing settings during installation, but once I got it setup its been very reliable -- more reliable than the power company.

I have it Email short video clips of motion triggers, still has issues with false messages due to ambiant light changes, but most days it is false alarm free since I've tweaked settings.  Provides great peice of mind while we are away.

---

### Post by Maheriano on 2011-05-13
> **wkulecz said:**
> In your dreams!  There is a lot more to it than that!  Changes in light level as clouds go by, motion you don't want to record -- insects, small anaimals, incidental motion from the wind, all make the "obvious" solutions generally fail.

Motion is probably a better choice if you are only using a single camera.  I'm using zoneminder, but in my tests motion had far superior immunity to changing light levels.

I've found Zoneminder to be unstable when changing settings during installation, but once I got it setup its been very reliable -- more reliable than the power company.

I have it Email short video clips of motion triggers, still has issues with false messages due to ambiant light changes, but most days it is false alarm free since I've tweaked settings.  Provides great peice of mind while we are away.

So allow for a larger checksum change before recording.....easy. If there's a major change like a body entering the frame, it'll trigger. If it's a simple light change or insect, no recording. I've already written this application with a speed overlay from the NMEA string from my GPS receiver, it worked great.

---

### Post by Maheriano on 2011-05-13
Do Zoneminder and Motion require Apache servers on the box?

---

### Post by Cyked on 2011-07-20
> **wkulecz said:**
> 

I have it Email short video clips of motion triggers, still has issues with false messages due to ambiant light changes, but most days it is false alarm free since I've tweaked settings.  Provides great peice of mind while we are away.


How did you accomplish this?  I use motion and want an email sent when motion is detected and it starts saving files (I have no need to send files).

---

### Post by wkulecz on 2011-07-20
I'm using Zoneminder to do this,  I've played with Motion a bit, I think when it triggers you have to have its script run a command (or other script) to send the Email.

Perhaps this will get you started:

[http://www.lavrsen.dk/foswiki/bin/view/Motion/ExternalCommands](http://www.lavrsen.dk/foswiki/bin/view/Motion/ExternalCommands)



> Do Zoneminder and Motion require Apache servers on the box?
Zoneminder entire user interface is web based so it needs a local server, but it can be configured to only accept local (loopback) connections.

I don't think Motion requires a web server.

---

### Post by Cyked on 2011-07-20
I'll take a look, thanks.

Motion doesn't require it, but if you want to review on the web...
For me Motion is configed to drop the output files in a dir and I view in Apache (any computer, phone, whatever).

---

### Post by Cyked on 2011-07-20
Not trying to thread jack, but anyone know how to address this?  I'm not finding anything on google re: how/where to change this.  From what I AM finding I am seeing something on /usr/lib/libv4l/v4l2convert... or changing the v4l2_palette.  Beyond that I'm not sure if this is supposed to go in motion.conf or what (I see nothing in the manpage for motion)

syslog entries when starting motion in daemon mode.
```

motion: [1] Config palette index 8 (YU12) doesn't work.
motion: [1] Supported palettes:
motion: [1] 0: MJPG (MJPEG)
motion: [1] 1: YUYV (YUV 4:2:2 (YUYV))
motion: [1] Selected palette YUYV

```

---

