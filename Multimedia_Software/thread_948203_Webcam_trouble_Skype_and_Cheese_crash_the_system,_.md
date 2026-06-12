---
title: "Webcam trouble: Skype and Cheese crash the system, camorama won't start."
date: 2008-10-15
forum: Multimedia Software
---

### Post by Hilko on 2008-10-15
I've got a build in webcam in a Thinkpad T500, running Ubuntu 8.04 64bit. It works fine with
aMSN and
Ekiga.

But I have the following problems:
[LIST=1]
[*]Skype 2.0.0.72 (for 64bit) crashes the complete system, whenever I go to Options -> Video Settings -> Test Webcam.
[*]starting Cheese crashes the complete system.
[*]Camorama cannot start. It gives an error: Could not connect to video device (/dev/video0). Please check connection.
[/LIST]

The first problem is my only priority, but i think the other problems are related. Does anyone know a solution or have some information on what the cause might be ?

Some info:
```
:~$ lsmod | grep video
uvcvideo               62084  0 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
video                  23444  0 
output                  5632  1 video
usbcore               169904  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd
```

```
:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 17ef:4807 ChipsBnk 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 1267:02f0 Logic3 / SpectraVideo plc 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

Skype gives this camera the name:
UVC Camera (17ef:4807) (/dev/video0)

Running skype from the command line and then clicking webcam test shows:
```
:~$skype
Skype V4L2: Failed to change capture framerate (15)
Starting the process...
Skype Xv: Xv ports available: 1
Skype XShm support enabled
Skype Xv: Using Xv port 85
```

Any help will be very much appreciated !

---

### Post by patrickballeux on 2008-10-15
Camorama won't work, it only support V4L device, not V4L2...
Cheese should not crash
Skype is also giving me problem on my AMD64 since it is a 32bits software on a UVC webcam

Could you have a look in your log files (kernel log probably).

It looks like you have a driver problem if the whole system is crashing...


Can you run this:

```

> gst-launch v4l2src ! ffmpegcolorspace ! ximagesink

```

You should see a view of your webcam live...

And have a look at the output of gst-launch...

Let me know!

---

### Post by Hilko on 2008-10-15
Thank you very much for your reply. > Camorama won't work, it only support V4L device, not V4L2...I don't really care about camorama, that's ok.
> Could you have a look in your log files (kernel log probably).
How do I do that ? Where do I find these log files ?

I tried running the command but it did not work: ```
:~$ > gst-launch v4l2src ! ffmpegcolorspace ! ximagesink
bash: v4l2src: command not found
```

So you think it's a driver problem ? What exactly does that mean ? (I'm no expert)

Thanks again for your reply.

---

### Post by patrickballeux on 2008-10-15
> **Hilko said:**
> Thank you very much for your reply. I don't really care about camorama, that's ok.
How do I do that ? Where do I find these log files ?

I tried running the command but it did not work: ```
:~$ > gst-launch v4l2src ! ffmpegcolorspace ! ximagesink
bash: v4l2src: command not found
```

So you think it's a driver problem ? What exactly does that mean ? (I'm no expert)

Thanks again for your reply.

For the logs: See in System - Administration - Log Viewer (or System Log Viewer?)  (Mine is in french...)

Hmmm, how did you end up with v4l2src: command not found...  Did you included gst-launch?
EDIT: Ok, I see, you included the ">"...  This was to simulate a prompt...

The whole line to execute is:

```
gst-launch v4l2src ! ffmpegcolorspace ! ximagesink
```

Careful, the is an exclamation point, not a pipe between the elements...

---

### Post by Hilko on 2008-10-16
Good. I found the logs, but i can only view 5 days back. And the logs are really long. I have no idea what i am seeing or what to look for. Do I need to use grep to find something ?

I had to install gst-launch, then I tried your command and it worked exactly as you predicted. It opened a large window, showing the output from my webcam and I could see my self ! The following showed in the terminal:
```
:~$ gst-launch v4l2src ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
ERROR: from element /pipeline0/ximagesink0: Output window was closed
Additional debug info:
ximagesink.c(1069): gst_ximagesink_handle_xevents (): /pipeline0/ximagesink0
Execution ended after 81155619544 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
FREEING pipeline ...

```

Hope this is of some help. What do I need to look for in the log files ?

---

### Post by Hilko on 2008-10-20
anyone ??

---

### Post by Manoboy on 2008-10-23
I'm having the same problem, but with a webcam Clone 10027.
We need to find a way to make Skype work with V4L2 driver.
Finding that solution believe that our problems are solved.


[http://ubuntuforums.org/showthread.php?p=6005350#post6005350](http://ubuntuforums.org/showthread.php?p=6005350#post6005350)

---

### Post by Hilko on 2009-01-22
Hurray ! It seems to work now. Testing my webcam in Skype doesn't crash anymore. I think some updates have fixed the problem.
Many thanks to the Ubuntu community !!!

---

### Post by Hilko on 2009-01-22
Some improvement for Cheese. The application can start and the system doesn't crash anymore.

However, it doesn't work, it doesn't do anything. I see the green light that my webcam is on, but no output. The window is just gray. If I click on record video or take a photo Cheese crashes and I can only force quit.

---

### Post by gsbnd1 on 2009-01-23
I have a Dell vostro 1500 laptop and I have installed Intrepid Ibex on it. I have exactly the same problem with my webcam.
But a funny thing is, I installed Hardy Heron a few month ago on my laptop and never had such problem!

---

### Post by khelben1979 on 2009-01-23
I don't think you want to do this, but you might try to get the Windows version of Skype version working through Wine. Maybe it could work as a temporary solution?

[Here's a list]("http://www.oldversion.com/program.php?n=skype") of different versions of Skype to experiment with if you're interested.

---

