---
title: "ip cam viewer"
date: 2012-07-07
forum: Multimedia Software
---

### Post by tock on 2012-07-07
I haven't been able to get anything to come up on google for a ip -cam view software.  

I can't use a web browser, do to the webserver software on the ip-cam dvr requires activex.  How ironic since it is based on a linux kernel.  Anyway there are other options beside http, like the media port or the mobile port.  Using either of these does not require activex and is designed for phones and ipads.  I have it working on my android phone using "IP cam viewer lite"but I cannot find similiar software for ubuntu.  

Using the http port does allow me to make changes to the firmware on the dvr but I would be happy to just be able to view the camera's the same way I am able to on a android or ipad.  

I tried using mplayer and telling it to use the media port but no luck.
Any ideas on software that will get this working for me?  The cam system is zmodo.

---

### Post by DorianX on 2012-07-13
You've gotten farther than I have. Even on the http port, all I get is a blank screen with the ZModo Logo, even running IE under wine.

I was able to find this: [http://www.zoneminder.com/forums/viewtopic.php?f=9&t=18137](http://www.zoneminder.com/forums/viewtopic.php?f=9&t=18137) Which links to a small C program that will stream the raw data from the cameras, but it's error prone. When I tried it in mplayer, I just got a gray distortion. Ffmpeg was better, showing me an image from thee camera, but it would freeze frequently and the channel was so noisy that you didn't really get video so much as a series of still frames (I think it was receiving all the frames, but ffmpeg did not recognize all of them and therefore dropped most of them as broken)

I'd rather like to be able to control the DVR from other machines on my network, but like you, I also want to be able to view live video from the cameras.

---

### Post by jarek.k on 2012-09-24
Hi,

Did any of you have any luck finding ip cam viewer for ubuntu?

I'm more less where tock stucked. ip cam viewer on android is working fine, but can't find desktop app for ubuntu.

i've also tried *cameraip*/ipcam/video/mjpg.cgi - i get image, but no live feed.

---

### Post by hollywoodpete on 2013-03-09
I have the same issue with a different DVR. Vonnics. I can log in to the Webserver of the DVR but can't get into the video stream. It works fine on my wife's Mac and my Android phones but Linux is a real problem. I have one windows computer left on my network for my son's gaming habit but would love to be able to check the monitors from Linux desktops

---

