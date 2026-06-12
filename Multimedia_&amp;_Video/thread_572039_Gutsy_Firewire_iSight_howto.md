---
title: "Gutsy Firewire iSight howto"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by stuporglue on 2007-10-10
I tried to follow these instructions to get my firewire iSight to work with Ubuntu (x86, non Apple machine), but they didn't quite work. Here are some updated instructions if anyone is interested...

Old instructions (For Dapper Drake) : [http://ubuntuforums.org/showthread.php?t=143501](http://ubuntuforums.org/showthread.php?t=143501)

New Instructions: 

link: vloopback page: [http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice](http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice)

Install coriander, build-essential, subversion, and linux-header-(your version)

Use the svn repository listed at the link above  to get the latest version of vloopback and build it. Modprobe the modules, and enjoy

```
svn co http://www.lavrsen.dk/svn/vloopback/trunk/ vloopback
cd vloopback
make
sudo make install
sudo modprobe videodev
sudo modprobe vloopback

```

You should now be able to test it with Coriander by running "sudo coriander". In Coriander, press the 'Start' button under 'Global Iso Control', then choose the 'Services' tab.

Under 'Services' choose 'Receive', then 'Display'. If it works, turn off display, and turn on V4L. The device "Video loopback 0 output" should now appear under the Ekiga V4L device list. 

Note 1 : This short howto doesn't cover changing the permissions on your firewire or video devices. I just chmodded them 777 for the purpose of testing
Note 2 : Coriander chews up about 80% of the processor for me when V4L is turned on.

---

### Post by RemmyLee on 2007-11-05
I was going crazy trying to compile this. Had no idea there was an svn repository. Thanks a million.

---

### Post by stuporglue on 2007-11-05
Can you tell me how it works for you? Like I said, it uses about 80% of the CPU for me, and I'd love to hear if someone else had the same problem, and if they found a way to resolve it.

---

### Post by RemmyLee on 2007-11-05
Well, I'm actually still getting an error. Coriander isn't finding the device on the bus which is strange. Going to continue playing around with it and see if I can figure it out.

---

### Post by the ev on 2007-12-18
Everything seems to work with me up to Ekiga, where I get this error

```
Error while opening video device /dev/video0

There was an error while opening the device. Please check your permissions and make sure that the appropriate device is loaded.
```

I ran ```
sudo chmod 777 /dev/video0
``` but still got the same error in Ekiga.  Coriander works fine.

And I don't know if it's when your using it with Ekiga or not, but simply serving to V4L from Coriander uses about 5-11% of my CPU.

Any thoughts? Thanks for the help/tutorial!

---

### Post by jslmg on 2008-01-03
> **the ev said:**
> Everything seems to work with me up to Ekiga, where I get this error

```
Error while opening video device /dev/video0

There was an error while opening the device. Please check your permissions and make sure that the appropriate device is loaded.
```

I ran ```
sudo chmod 777 /dev/video0
``` but still got the same error in Ekiga.  Coriander works fine.

And I don't know if it's when your using it with Ekiga or not, but simply serving to V4L from Coriander uses about 5-11% of my CPU.

Any thoughts? Thanks for the help/tutorial!

I've been getting the same message in Ekiga, and worse...

After install and initial run in Coriander, the display worked, but barely. The video started out slow and jumpy, in both V4L and not in V4L. The longer it ran, the slower it got, until it began to crunch the whole system. I had to do a hard shutdown after everything on the desktop froze, except the mouse.

After rebooting, I opened Ekiga to see if maybe a reboot would have got the module working. No dice.

I opened a terminal and tried to get Coriander going. Here's what it said:
> Warning: Could not get a handle on your IEEE 1394 card.

Please check that:
- the card is present
- the IEEE 1394 modules (ieee1394, ohci1394, raw1394 and video1394) are loaded
- you have read/write permissions on the /dev/raw1394 devices. 

So, where do we go from here?

---

### Post by jslmg on 2008-01-11
Bump...

Please check my previous message...

---

### Post by bus_ter on 2008-01-15
> **jslmg said:**
> Bump...

Please check my previous message...

First of all check if it's a permissions issue.

Start Coriander as root with

```

sudo coriander

```

If that works then you simply need to set the permissions for your user account.

---

### Post by jslmg on 2008-01-15
Thanks for the reply. Yes, Coriander does open under sudo.

I'll need a howto for setting permissions on /dev/raw1394 devices. Can you help with that?

---

### Post by bus_ter on 2008-01-15
I installed Ubunto last night for the first time. I'm a newbie myself so I'm quite surprised my first post on here was to help someone else :-)

I also have an Apple Isight camera I want to get working in Linux (hence how I came across this thread). I installed Coriander and when trying to start it got the same error as yourself. So I guessed it was permissions and tried to ' su ' (strange how that doesn't work in Ubunto?), and then tried 'sudo'' which worked fine. Coriander picks up my Isight ok but I couldn't get it to show a picture. I'll have another look tonight and hopefully get it working.

I haven't tried to set the permissions yet so it runs as a user. But you could try: ```
 sudo chmod 777 /dev/raw1394
```
I'll have a go tonight, and if I get everything working I'll let you know what I did. Hopefully between the two of us we'll have it sorted!

---

### Post by bus_ter on 2008-01-15
OK I got my Isight showing in ubuntu!

After doing the command above I could start coriander as a user.

Once started under camera Select it shows my Isight "Apple Computer, Inc"

Now to view the Isight video:

1) Click Global Iso Control START (the green light on the Isight should turn on)
2)Click 'Services' Tab. Then click 'Receive'. The Box below it should now show a frame rate (mine shows 15fps)
3) Click 'Display' to view the webcam video!

It works but when I display my video it drops to less than 1 fps and kills the CPU. :(

Not sure what to do about that??? I might try messing around with a few settings.

---

### Post by bus_ter on 2008-01-15
Right I've sorted out the speed issue.

Before you start the video output change the 'Method' in the 'Services' tab.

Change RAW1394 to VIDEO1394. Now runs at the 15fps smooth :)

Next I shall try to get the video working in other applications such as AMSN

---

### Post by bus_ter on 2008-01-15
I've been messing around all night now and I've had enough of the Isight for one day!

I now have the fps showing 30fps. I'm not exactly what I did to do this though?

Anyway here is what I've done so far:

I still had a permissions problem so I set permissions for all the related devices:

```

sudo chmod 777 /dev/raw1394
sudo chmod 777 /dev/video1394/0
sudo chmod 777 /dev/video0

```

Coriander now starts as a user and is fully functional.

I installed some packages that are related to IEEE1394 cameras on Linux

# libpt-plugins-avc - PWLib Video Plugin for IEEE1394 (FireWire) AVC devices
# libpt-plugins-dc - PWLib Video Plugin for IEEE1394 (Firewire) DC Devices

I also setup Vloopback to export the video as V4L (Video 4 Linux)
I downloaded [http://www.lavrsen.dk/twiki/pub/Motion/VideoFourLinuxLoopbackDevice/vloopback-1.1-rc1.tar.gz](http://www.lavrsen.dk/twiki/pub/Motion/VideoFourLinuxLoopbackDevice/vloopback-1.1-rc1.tar.gz)

Then did this from the directory I downloaded the file.
```
 
tar zxvf vloopback-1.1-rc1.tar.gz
cd vloopback-1.1-rc1/
make
sudo insmod vloopback.ko

```

Your Isight should now be available on Linux as a V4L device. I've had mixed success with different programs.

Using **Ekiga** (previously gnomemeeting) it worked!
During the setup select '1394dc' for video plugin and '/dev/video1394/0' for input device

**Amsn** - Couldn't get it to work
The V4L device shows up, but when I select it I just get a black box and it crashes Amsn

**Msn Mercury** - Doesn't detect the Camera at all

That's all I've tried just now. I hope all this info proves useful to someone.

So far I haven't got the Isight to work with MSN in Linux (my ultimate goal). If anyone can get this to work them please post here how!

---

### Post by jslmg on 2008-01-15
> **bus_ter said:**
> OK I got my Isight showing in ubuntu!

After doing the command above I could start coriander as a user.

Once started under camera Select it shows my Isight "Apple Computer, Inc"

Now to view the Isight video:

1) Click Global Iso Control START (the green light on the Isight should turn on)
2)Click 'Services' Tab. Then click 'Receive'. The Box below it should now show a frame rate (mine shows 15fps)
3) Click 'Display' to view the webcam video!

It works but when I display my video it drops to less than 1 fps and kills the CPU. :(


Yeah, this was the state of things here when I sent that first S.O.S. I'd gotten iSight to work in Coriander, as it does now, but with abysmal f.p.s. and increasingly high demand on my CPU.

 I'll follow your next steps and see what happens.

---

### Post by jslmg on 2008-01-15
Well, bus_ter, basically, I had already done all the steps you took. I already had those libpt plugins installed, and vloopback. I had done all those steps to get Coriander running with iSight. 

One change that worked:
Just before pressing "receive", I changed the "method" from "raw1394" to "video1394." Positive signs showed up when the f.p.s. began approaching 15, though not steady. Over time, it drops down to about 6-8 fps.
The fps under "Display," when I'm looking at the camera image, remains slow. 

Two differences though:
1)I was able to chmod /dev/raw1394 and /dev/video1394/0, but NOT /dev/video0. On that last one, no file or directory was found.

2)I clicked "V4L" in that row under Switch/FPS--the same row that has "Receive" and "display"--and I got this message:

> Warning: Could not start the V4L service.

Please check that:
-V4L kernel modules are loaded or that V4L support is in your kernel.
-You have read/write permission on the selected video device.
-The vloopback module is loaded.

How do we load the vloopback module--it IS installed.

Any other tips on getting read/write permission set on the device?

 I'm still back at square one--same as when I sent my first S.O.S.

More help, someone, please!


> **bus_ter said:**
> I've been messing around all night now and I've had enough of the Isight for one day!

I now have the fps showing 30fps. I'm not exactly what I did to do this though?

Anyway here is what I've done so far:

I still had a permissions problem so I set permissions for all the related devices:

```

sudo chmod 777 /dev/raw1394
sudo chmod 777 /dev/video1394/0
sudo chmod 777 /dev/video0

```

Coriander now starts as a user and is fully functional.

I installed some packages that are related to IEEE1394 cameras on Linux

# libpt-plugins-avc - PWLib Video Plugin for IEEE1394 (FireWire) AVC devices
# libpt-plugins-dc - PWLib Video Plugin for IEEE1394 (Firewire) DC Devices

I also setup Vloopback to export the video as V4L (Video 4 Linux)
I downloaded [http://www.lavrsen.dk/twiki/pub/Motion/VideoFourLinuxLoopbackDevice/vloopback-1.1-rc1.tar.gz](http://www.lavrsen.dk/twiki/pub/Motion/VideoFourLinuxLoopbackDevice/vloopback-1.1-rc1.tar.gz)

Then did this from the directory I downloaded the file.
```
 
tar zxvf vloopback-1.1-rc1.tar.gz
cd vloopback-1.1-rc1/
make
sudo insmod vloopback.ko

```

Your Isight should now be available on Linux as a V4L device. I've had mixed success with different programs.

Using **Ekiga** (previously gnomemeeting) it worked!
During the setup select '1394dc' for video plugin and '/dev/video1394/0' for input device

**Amsn** - Couldn't get it to work
The V4L device shows up, but when I select it I just get a black box and it crashes Amsn

**Msn Mercury** - Doesn't detect the Camera at all

That's all I've tried just now. I hope all this info proves useful to someone.

So far I haven't got the Isight to work with MSN in Linux (my ultimate goal). If anyone can get this to work them please post here how!

---

