---
title: "HOWTO: Cool video effects with Skype"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by nickzeff on 2008-03-15
This is an adaptation of a post I did previously at [http://ubuntuforums.org/showthread.php?t=696978](http://ubuntuforums.org/showthread.php?t=696978)

Follow the following instructions to do fun things with your webcam stream when you video call your mates on Skype.

The trick is to use effectv, vloopback and gstfakevideo to process your webcam stream and feed it back to Skype in a form it understands. Gstfakevideo was previously used to fix webcams incompatible with Skype. I just added the use of the brilliant effectv application.

1. Install effectv package with aptitude or

```
sudo apt-get install effectv
```

Spend some time playing around with it. If you type effectv from a terminal you'll get a video window popping up. If all is working well, when you press the up and down cursor keys you should see your face doing some pretty weird things.

2. Build and install the vloopback module like so:

```
svn co http://www.lavrsen.dk/svn/vloopback/trunk/ vloopback
cd vloopback
make
sudo make install
sudo modprobe vloopback

```

Effectv will use vloopback to allow us to capture the adapted video stream and do something with it. 

This should now stick the vloopback inputs and outputs on /dev/video1 and /dev/video2 if you have your cam on /dev/video0. Type dmesg to check this.

See [http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice](http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice) for more details on this step if anything seems wrong.

3. Move your existing video0 stream (my webcam is on this) over to /dev/video3, since Skype seems to have issues with anything other than /dev/video0.

```
sudo mv /dev/video0 /dev/video3
```

4. Fire up effectv through vloopback as so:

```
effectv -device /dev/video3 -vloopback /dev/video1
```

5. Get gstfakevideo and build it

```

svn checkout http://gstfakevideo.googlecode.com/svn/trunk/ gstfakevideo
cd gstfakevideo
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

Cool!


**Automating It**

If you've done all this, but want to make it a bit quicker next time, you could just put everything in a script. I'm rubbish at writing bash scripts, so I just cobbled something together from the original gstfakevideo script. My code assumes that all the relevant modules and packages have been installed in the steps above.

```
#!/bin/bash
#
# setup gstfakevideo preload to hijack calls made
# to /dev/video0
#
#This script runs Skype with libskype_dsp_hijacker.so "filter"
#It allows redefining of what devices Skype uses for 
#microphone, speakers and mixer (especially microphone and
#speakers can use different devices)

# -- CONFIGURATION --

#default configuration when no option is specified

export HIJACKVIDEO="/dev/video0"
export GST_PIPE="v4lsrc device=/dev/video2 ! ffmpegcolorspace"  

prefix=/usr/local
exec_prefix=${prefix}

#prefer use of libskype_dsp_hijacker from current directory
if test -f ./libgstfakevideo.so; then 
  libdir=.
else
  libdir=${exec_prefix}/lib
fi

LD_PRELOAD=${libdir}/libgstfakevideo.so
if test -f /lib/libdl.so.2; then
	LD_PRELOAD=$LD_PRELOAD:/lib/libdl.so.2
fi
export LD_PRELOAD


#Move current webcam over to /dev/video3

if test -e /dev/video0; then 
  sudo mv /dev/video0 /dev/video3
fi


# load vloopback module first

sudo modprobe vloopback

# invoke effectv first, and give it a second to load

effectv -device /dev/video3 -vloopback /dev/video1 &

sleep 1

exec skype
```

I put the above script in ~/.scripts and can run it when I feel like it. It's not perfect, but until it's all integrated into Skype, or someone can suggest anything better, that's all I've got!

Have fun! 

N

---

