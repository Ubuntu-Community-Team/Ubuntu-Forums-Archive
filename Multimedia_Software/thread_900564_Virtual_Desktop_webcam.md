---
title: "Virtual Desktop webcam"
date: 2008-08-25
forum: Multimedia Software
---

### Post by Chocomochino on 2008-08-25
Hello, i want to use stickcam to show a part of my desktop,  i know this is possible in windows since a lot of people uses it on stickam. 
But i can't find a way to make it happen in Ubuntu 
*i just want to show it not record it. TIA!

Maybe it's just a configuration thing where i need the input of video to show as a device? :confused:

---

### Post by patrickballeux on 2008-08-26
Hi,

I just found yesterday a way to do this.  

I have to create a clean HOWTO but you can find the links on my blog : [http://blog.patrickballeux.com/2008/08/ubuntu-et-une-webcam-virtuelle.html](http://blog.patrickballeux.com/2008/08/ubuntu-et-une-webcam-virtuelle.html)

(in french...)

You will need recordMyDesktop and ffmpeg from the repository of Ubuntu.  Then you will have to download Flashcam and mjpegtools_yuv_to_v4l.

- Flashcam ([http://www.swift-tools.net/Flashcam](http://www.swift-tools.net/Flashcam))
- mjpegtools_yuv_to_v4l ([http://panteltje.com/panteltje/mcamip](http://panteltje.com/panteltje/mcamip))
- recordMyDesktop (gtk-recordMyDesktop can be used)
- ffmpeg 

You will need to compile Flashcam and mjpegtools_yuv_to_v4l and install them in your setup.  Normally done with "sudo make install".  Read the doc to compile and install...

Ok, we are almost there...

I created a small script that can automate the process into a single command line that you manually start in a console and stop using CTRL-C.  Not really fancy, but it works.

************Script*******************
mkfifo stream.ogg
sudo modprobe vloopback
echo "CTRL-C to stop the capture"
sleep 5
recordmydesktop -width 320 -height 240 -fps 15 --no-sound --on-the-fly-encoding --follow-mouse --overwrite -o stream.ogg & sleep 10 & ffmpeg -i stream.ogg -an -s 320x240 -r 15 -f yuv4mpegpipe - | mjpegtools_yuv_to_v4l /dev/video2
killall recordmydesktop
rm stream.ogg
*************************************

Copy this script into a bash file (mine is called caputre.sh), and create a folder where to invoke this script. 

What happens is
- A fifo file is created to pipe recordMyDesktop with ffmpeg
- The module vloopback is loaded and make sure that your "input" device is /dev/video2.  If not, you will have to modify the script to use the correct device.  If you already have a webcam on /dev/video0, you will have /dev/video1 as an output and /dev/video2 as an input.
- Then recordMyDestop is invoke and we use the fifo file to record the desktop.  That video file in the fifo file will be read by ffmpeg as an input, converted to yuv4mpeg format and the converted file will by piped to the mjpegtools_yuv_to_v4l onto the input device /dev/video2.
- To stop the screencast, simply hit CTRL-C.

[LIST]
[*]Make sure to start the script before opening you stickam viewer because Flash won't detect properly your new webcam "Vloopback".
[*]Sometimes, the Flash player crashes and stays zombie in memory.  It does not happen often, but when it does, it locks the video device and you have to reboot the computer to have access again to your webcam device.
[/LIST]

You will require a good CPU because the whole process is CPU demanding but not too much.

The script will capture a square of 400x300 that will be converted into a 320x240 image for the webcam.  This settings gives a good view of what you are doing with a good image quality without sacrificing all your CPU cycles.  Capture at 5 fps, more than that does not seem to help in any way for the webcam...

If you have any question, you can ask me...

Patrick Balleux
[http://blog.patrickballeux.com](http://blog.patrickballeux.com)

---

### Post by Chocomochino on 2008-08-26
> **patrickballeux said:**
> Hi,

I just found yesterday a way to do this.  



Merci Beaucoup!

i'll try this today!

---

