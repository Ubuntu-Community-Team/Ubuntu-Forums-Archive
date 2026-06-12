---
title: "Webcam surveillance"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by mandragor on 2006-11-01
Hi!

I have the job of setting up a system of webcam-surveillance for an
office, the kind where there will be activity at least 16 hours a day.
What I want to do is to connect 2 or three webcams to a quite powerful
computer which uploads pictures regularly to the webserver on the same
machine. But, I would also like to be able to browse through a stream,
so if for example it is noticed that someone has been spraying grafitti
it is possible to look through recorded video and see when it happened and
who did it.

Any ideas how to fix this setup with free (as in beer) software?
Any help is greatly appreciated.

---

### Post by commonplace on 2006-11-21
I'm looking for the same thing. Anyone?

---

### Post by MJN on 2006-11-21
Check out [http://www.zoneminder.com/](http://www.zoneminder.com/)

Mathew

---

### Post by commonplace on 2006-11-21
> **MJN said:**
> Check out [http://www.zoneminder.com/](http://www.zoneminder.com/)

Mathew

That looks like exactly what I wanted. Actually, it looks even better than what I'd hoped for. I'll be giving it a try soon. Thank you!!

/Kevin

---

### Post by MJN on 2006-11-21
Do let us know how you get on.

I got myself a cheap BT878 capture card and some B&W cameras with the intention of using them (with ZM) to set up a rudimentary security system but never got round to it.... as always!

Mathew

---

### Post by Andrew1234 on 2007-01-09
Just got ZM working on ubuntu and also my webcam, just need to find where the webcam is on my PC?
In source there is dev/video how can I find out where the webcam is for my source, as this does not bring up the camera.

---

### Post by MJN on 2007-01-23
Andrew,
 
Did you ever sort this out?
 
I recently installed ZoneMinder and find it's working really well with my Panasonic IP camera. However, now I'm going to add some more cameras and have got myself a BT878-based capture card and standard camera.
 
Haven't fitted them yet but would be grateful for any pointers to save me reinventing the wheel when I get round to it!
 
Matehw

---

### Post by Andrew1234 on 2007-01-23
Mathew,

I just cannot get my webcam to work on ubuntu, I tried all the posts on the forum and can only get it to work partly showing half the picture. So I have given up on that, but I have just bought a capture card from Bluecherry which has just arrived and I am going to install this evening(Xbuntu) as supplied with the card with zomeminder pre-installed. I will let you know how I get on.

If this works=D>  I am then going to try to remote view over the tinternet via my static IP address, but again I am struggling with up my router to expect incoming ports.

Andrew

---

### Post by josesanders on 2007-01-23
You might have trouble with the BT878 in that it doesn't do any compression itself, so that has to be done by the cpu.  If you have a decent system, you might be able to encode two at a time, but I'd be really surprised if you could do more than that.  If you need to run multiple cards on the same machine, it might be worth it to try a TV card with mpeg compression, like the Haupaugge 150.  I know they are a lot more expensive, but it could save you some headaches.  Just something to keep in mind.

---

### Post by MJN on 2007-01-23
On the contrary - ZoneMinder doesn't utilise MPEG at all hence there'd be no advantage. Rather, it uses JPEGs and MJPEGs. Indeed, local camera's connected via a BT8x8 apparently produce very little CPU overhead for ZM (compared with network cameras) because the output is pretty much in the format it needs (i.e. a raw image as opposed to a JPEG that needs decompressing). ZM can create MPEG videos from archived events, however in this case it uses ffmpeg to create them. This wouldn't be done for live streaming so the lack of hardware acceleration is arguably less of an issue.

I've got the cameras up and running now - although as per usual it wasn't without a bit of trial and error experimenting and random Google searches!

As BTTV support is included in our kernels it was 'simply' a case of seeing what BTTV was seeing the card as by default (using **dmesg |grep -i bttv**). In my case (an el-cheapo card from China) it wasn't being recognised with the upshot that whilst **xawtv -hwscan** showed the device as **/dev/video0** if I ran **xawtv -device /dev/video0** I didn't get any output.

To rectify this, at least in xawtv, I had to change the selected input to composite3 (bad choice of socket - if I'd used the other end (0) it would have picked it up) as well as changing the video type to PAL-NC.

However... this still only produced a black and white image.

This was solved thanks to a throwaway line in somebody's blog - they happened to mention that many of the BT878 cards on eBay contained a Grandtec chipset hence I had to add **options bttv radio=0 card=77 tuner=-1** to **/etc/modprobe.d/options**. One reboot later and the card was thus recognised by the BTTV driver, xawtv showed the image automatically set to PAL (not PAL-NC anymore) and what's more it was in colour!

Incidentally, by default ZM was capturing at the full 40fps which is somewhat overkill (I was getting great results with the IP cam at only 8-10fps) and so I dropped this right down if only to free up headroom for more cameras - I also plan on uploading event images off-site on-the-fly hence the fewer the number of frames to do the better.

Mathew

---

### Post by obscur156 on 2008-03-18
WXCAM ...

[http://wxcam.sourceforge.net/]("http://wxcam.sourceforge.net/")

---

### Post by mujaga on 2008-03-19
Hi,
I read carefully what you wrote about this topic and I think that the more I read the less I understand. I got a surveillance camera connected to Grandec. I intend to used it for monitoring the garden.
What I have been doing lately.
I did dmesg |grep -i bttv and got:

[  109.461286] bttv: driver version 0.9.17 loaded
[  109.461291] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  109.461360] bttv: Bt8xx card found (0).
[  109.461596] bttv0: Bt878 (rev 17) at 0000:01:07.0, irq: 22, latency: 32, mmio: 0xd4000000
[  109.461607] bttv0: detected: Grandtec Grand X-Guard [card=103], PCI subsystem ID is 0304:0102
[  109.461610] bttv0: using: GrandTec Multi Capture Card (Bt878) [card=77,insmod option]
[  109.461676] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[  109.773870] bttv0: using tuner=-1
[  109.773874] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[  110.106326] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[  110.241149] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  110.245523] bttv0: registered device video1
[  110.245554] bttv0: registered device vbi0
[  110.245581] bttv0: PLL: 28636363 => 35468950 .. ok
[  110.277270] bttv: Bt8xx card found (1).
[  110.277312] bttv1: Bt878 (rev 17) at 0000:01:09.0, irq: 20, latency: 32, mmio: 0xd4002000
[  110.277324] bttv1: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[  110.277328] bttv1: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[  110.277362] bttv1: gpio: en=00000000, out=00000000 in=003ff502 [init]
[  110.277738] bttv1: using tuner=5
[  110.277741] bttv1: i2c: checking for MSP34xx @ 0x80... not found
[  110.278476] bttv1: i2c: checking for TDA9875 @ 0xb0... not found
[  110.278994] bttv1: i2c: checking for TDA7432 @ 0x8a... not found
[  110.279524] bttv1: i2c: checking for TDA9887 @ 0x86... not found
[  110.329796] bttv1: registered device video2
[  110.329826] bttv1: registered device vbi1
[  110.329874] bttv1: registered device radio0
[  110.329900] bttv1: PLL: 28636363 => 35468950 .. ok
[  110.361859] input: bttv IR (card=34) as /class/input/input6
[ 5798.848928] bttv0: PLL can sleep, using XTAL (28636363).

Then I went to xavTv and folloving your experiences did the conf. Nothing come out.
Then I did: xawtv -hwscan
and got 


This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
looking for available devices
port 73-73                              [ -xvport 73 ]
    type : Xvideo, video overlay
    name : video4linux

port 74-74                              [ -xvport 74 ]
    type : Xvideo, video overlay
    name : video4linux

port 75-75
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : UVC Camera (046d:0990)
    flags:  capture

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : BT878 video (GrandTec Multi Cap
    flags: overlay capture

/dev/video2: OK                         [ -device /dev/video2 ]
    type : v4l2
    name : BT878 video (Leadtek WinFast 20
    flags: overlay capture tuner
. Nothing again.
I have installed ZM and what ever I put as a source i.e. dev/video(0,1 or 2) and PAL (n,..)
Nothing again.
Pls. give me some ideas what to do to get ZM or xavTv working.

---

