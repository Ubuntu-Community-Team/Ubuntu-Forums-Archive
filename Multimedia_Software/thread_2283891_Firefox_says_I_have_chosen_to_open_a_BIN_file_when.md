---
title: "Firefox says I have chosen to open a BIN file when using motion"
date: 2015-06-25
forum: Multimedia Software
---

### Post by scottbomb on 2015-06-25
I've been running the webcam software motion on a Xubuntu 14.04 box for several months now with no problems. I'm accessing it over the internet from a Kubuntu box. All of a sudden today, I keep getting this dialogue box popping up that says
```
You have chosen to open:

which is: BIN file
from: http://webcam.url.com

Would you like to save this file?
```

I click cancel but a couple of minutes later, another on pops up. And another. And another. What the hell is going on?

Googling this problem, all I can find are people saying that such errors are caused by the webmaster failing to declare the document type but this is not the case as the source code is:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">

<html>
<head>
<title>webcam</title>
<meta name="keywords" content="" />
<meta name="description" content="" />
<meta http-equiv="content-type" content="text/html; charset=UTF-8" />
</head>
<frameset rows="100%">
<frame src="http://scottbomb.dyndns.org:8891" title="webcam" frameborder="0" noresize="noresize"/>
<noframes>
<body>
<h1>webcam</h1>
<p><a href="http://scottbomb.dyndns.org:8891">http://webcam.scottbomb.com/</a></p>
</body>
</noframes>
</frameset>
</html>

```

I don't know where or how to change the html if I could.

My motion.conf:

```
webcam_port 8891
webcam_localhost off
output_normal off
target_dir /home/scottbomb/Dropbox/Webcam
threshold 1500
noise_level 32
daemon on
height 480
width 640

#required for video
framerate 30
webcam_maxrate 30
# webcam_quality 60

# Turn movie recorder on or off
ffmpeg_cap_new off

# Gap is the seconds of no motion detection that triggers the end of an event.
# An event is defined as a series of motion images taken within a short timeframe.
# gap is time for movement in the room to stop, telling motion to stop recording after these seconds
gap 20

jpeg_filename preview

# Ignore sudden massive light intensity changes given as a percentage of the picture area
# that changed intensity. Values are 0-100.
lightswitch 20

# The maximum length of an mpeg movie in seconds. Set this to zero for unlimited length.
# For security, keep this short. This way, a new movie is uploaded and/or saved every x seconds.
max_mpeg_time 10

# Picture frames must contain motion at least the specified number of frames
# in a row before they are detected as true motion. At the default of 1, all
# motion is detected. Valid range: 1 to thousands, recommended 1-5
minimum_motion_frames 90

############################################################
# HTTP Based Control
############################################################

# TCP/IP port for the http server to listen on (default: 0 = disabled)
# CHANGED
control_port 8892

# Restrict control connections to localhost only (default: on)
# CHANGED
control_localhost on

# Output for http server, select off to choose raw text plain (default: on)
control_html_output on

```

I get the same popup in Firefox on a Windows machine so I'm tempted to blame either motion or Firefox. The only difference between the two is the dialogue box in Windows says I'm trying to open application/octet-stream whereas Firefox on the Kubuntu client calls it a "BIN" file.

Any ideas on how to stop this annoying behavior?

---

