---
title: "[SOLVED] Problem with webcam and w3cam"
date: 2009-01-02
forum: Multimedia Software
---

### Post by Theo Molenaar on 2009-01-02
Hi,

I have a webcam which is connected to Ubuntu 8.04 server (up to date) and which is used in conjunction with the program 'motion' ([http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)). The webcam is a Philips PCVC740K ToUcam Pro [pwc] and it works fine under 'motion'. 

I also want to have a live video stream on my webpage. Here is where the problem starts. I have installed program 'w3cam'. Testing the cgi is done via the following command: [http://localhost/cgi-bin/w3cam.cgi?help](http://localhost/cgi-bin/w3cam.cgi?help). This works fine and gives the following output:

[FONT="Courier New"]W3Cam, Version 0.7.2

Usage: w3cam.cgi
CGI parameters (GET or POST):
 help                                    show this page
 size=#x#                                geometry of picture [default = 240x180]
 color={0|1}                             color or grey mode [default = 1]
 input={tv|composite|composite2|s-video} define input source
 quality={1-100}                         jpeg quality [default = 65]
 format={ppm|png|jpeg}                   output format
 freq=#                                  define frequenzy for TV
 usleep=#                                sleep # micro secs before cap. [default = 20000]
 mode=[gui|html]                         build a page with panel or plain html
 refresh=#.#                             time in sec to refresh gui
 norm={pal|ntsc|secam}                   tv norm
 bgr={1|0}                               swap RGB to BGR (default: no)

Compiled in features:
 PNG file format
 JPEG file format
 TTF/TimeStamp[/FONT]

Testing the video stream is done as follows: [http://localhost/cgi-bin/w3cam.cgi](http://localhost/cgi-bin/w3cam.cgi). This should give 1 image of the webcam. Instead of this I get the following error:

Can't open device /dev/video0: Permission denied

The webcam is running on /dev/video0 and has the following permissions:
crw-rw----+ 1 root video 81, 0 2009-01-02 14:56 /dev/video0

Thanks for any help!

Rgrds, Theo

---

### Post by Theo Molenaar on 2009-01-06
Update: the problem is with w3cam.cgi. For unknown reasons this program does not work properly with 'motion'. 

On the 'motion' webpage a link can be found to another piece of software called mjpeg-proxygrab ([http://www.lavrsen.dk/twiki/bin/view/Motion/MjpegProxyGrab](http://www.lavrsen.dk/twiki/bin/view/Motion/MjpegProxyGrab)) which can either grab an image or proxy the mjpeg stream from a Motion webcam. Now it works like a charm. 

Thanks, Theo

---

