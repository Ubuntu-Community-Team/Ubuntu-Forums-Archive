---
title: "Webcam+Effectv+Ustream Possible?"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by DragonSpirit on 2008-02-14
I've been trying to figure out if I can use effects on my webcam similer to alot of users I've seen online on ustream.tv that are running Windows. So far I've installed Effectv and was very impressed with all the neat things it could do with live video. 

It works locally with VLC Media Player (but not ustream.tv, skype, amsn, etc..) when I do this command:

*effectv -size 640x480 -device /dev/video0  -vloopback /dev/video1*

I am running Ubuntu Gutsy 7.10, I have a Logitech QuickCam Communicate STX, I also installed the kernel module vloopback.ko ([http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice](http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice)) because it didn't seem to be offered in Ubuntu or any repository. I did this in an attempt to get a "looped back" video device to see if i could pipe it through effectv from my webcam on /dev/video0. I thought it would show up on /dev/video1 because of the command I issued but it actually appears on /dev/video2 when I access it with VLC. Which didn't make sense to me.

If I try and select the Effectv loopback device in "Multimedia Systems Selector" in the Video Default Input part and then click test I get this output when I had effectv started on command line
[I]
vloopback: unsupported pixel format(9) is requested.
vloopback: ioctl 40107613 unsuccessfully handled.
vloopback: unsupported pixel format(14) is requested.
vloopback: ioctl 40107613 unsuccessfully handled.
vloopback: unsupported pixel format(16) is requested.
vloopback: ioctl 40107613 unsuccessfully handled.
vloopback: unsupported pixel format(11) is requested.
vloopback: ioctl 40107613 unsuccessfully handled.
vloopback: client closed device.[/I]

Then the Multimedia Systems Selector closes itself without warning. Though VLC handles it fine.

Basically what I am trying to see if I can do is take my Webcam, and see if I can put a wide selection of effects on it like Effectv or something similer, then make that video accessable to a flash app like ustream or any other "community" cam streaming site. All using tools you can use on Ubuntu. It doesn't even have to be Effectv, just something with a selection like it does, though I would prefer Effectv because I like what it does. Don't know if I am asking to much, sorry if I am, just was hoping I could do what my friends on Windows could do, maybe even do some cooler things to show them up. :)

---

### Post by nickzeff on 2008-03-14
Did you get this working? I'm trying to do exactly the same thing!

---

### Post by nickzeff on 2008-03-14
From other info on the web, it would appear that Skype only accepts input from video4linux devices, rather than the raw format that comes out of vloopback.

Back to the drawing board.

Anybody anywhere got any ideas how to add cool effects to Skype video? 

Cheers

N

---

### Post by nickzeff on 2008-03-15
OK. I did it! It's cool!

The trick is to use gstfakevideo to stream the vloopback outback back to skype through gstreamer.

To summarise what I did (probably made mistakes here - I don't know very much about building and installing stuff!...):

1. Install effectv package

2. Build and install vloopback as per

[http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice](http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice).

It will stick its input/output on /dev/video1 and /dev/video2 if you have your cam on /dev/video0.

3. Move your existing video0 stream (my webcam) over to /dev/video3, since gstfakevideo streams to 0 by default. You can change this by other means, but as a proof of concept, just use

```
sudo mv /dev/video0 /dev/video3
```

for now.

4. Fire up effectv through vloopback as so:

```
effectv -device /dev/video3 -vloopback /dev/video1
```

Now we have the nice app that lets you scroll through effects with the cursor keys etc.

5. Get gstfakevideo and build it

```

svn checkout http://gstfakevideo.googlecode.com/svn/trunk/ gstfakevideo
make
sudo make install

```

I got some dependency type errors, so had to get the gstreamer libraries with

```
sudo apt-get install libgstreamer0.10-dev 
```

6. Next, we need to start up skype via gstfakevideo. Once in the gstfakevideo directory, the command that worked for me was:

```
./gstfakevideo v4lsrc device=/dev/video2 ! ffmpegcolorspace
```

This streams the output of vloopback through gstreamer to create a fake v4l device that skype can use. Ensure that any instance of Skype is closed before you issue this command.

7. Skype should start up automatically now, and going into test video devices should allow you to see the fakewebcam device with the output of effectv. If you scroll through the effects from within effectv, you should see that reflected in the test signal in Skype.


There is definitely going to be a good way to set this up as a nice bash script, but I'm not bothering with that today - I've got other things to do. But I've proved it can be done!

Cheers

N

---

### Post by iamah on 2008-06-04
bump, this is what is missing in my ubuntu, but is there a way to doesnt specify the application? i wanna use it for other apps, not skype.:guitar:

---

