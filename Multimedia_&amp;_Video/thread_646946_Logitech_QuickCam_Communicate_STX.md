---
title: "Logitech QuickCam Communicate STX"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by Ek0nomik on 2007-12-21
I was curious to know if anyone has this webcam and the microphone working in the new Skype Beta.  I believe I have .27 of the Beta.

WengoPhone works, but sadly it seems like it buffers a lot (the data can't be transferred without pauses because the connection isn't holding up).  I am assuming Skype, given it's licenses, has a better, less bandwidth hog of a algorithm to transfer the audio and video.

Any help is appreciate.  Thanks!

---

### Post by linuxwizard on 2007-12-22
Look on this page for: List of Webcams that 'Just Work > your webcam >notes

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by mendieta on 2007-12-25
> **Ek0nomik said:**
> I was curious to know if anyone has this webcam and the microphone working in the new Skype Beta.  I believe I have .27 of the Beta.

WengoPhone works, but sadly it seems like it buffers a lot (the data can't be transferred without pauses because the connection isn't holding up).  I am assuming Skype, given it's licenses, has a better, less bandwidth hog of a algorithm to transfer the audio and video.

Any help is appreciate.  Thanks!

Hi, 

I got your PM ;-)

I have never had problems using the mic of this camera with Skype 1.4. The latest beta (2.0.0.27) also works fine, both sound and video, in my Kubuntu box. I am not at home for the next few days, so I can't check the details (I am typing from my shiny, lovely eeepc on the road, but I digress ;-) )

Essentially, all I had to do to get it running was to look into the Options ins Skype, Devices, Sound, and find the mic listed like an USB device. Just selected it. The other trick (in KDE) is to make sure skype is called as "artdsp -m skype" (I am typing this by heart, please check the syntax, it is well documented in the Skype Linux FAQ).

I always use skype with windows users, and they are impressed about the image quality (sound is pretty good, too)

Cheers!
Hope this helps!

---

### Post by chochem on 2008-02-27
I bought this webcam having done a quick search of 'ubuntu webcam works'... And it does, sort of: I get a picture but it's hugely disstorted with lots of flicker (at least as far as camorama and cheese goes... I haven't really got further). It's usually the lower half of the screen that gets disjointed from the upper but colour distortion and just noise is also there from time to time. I have checked the connection and yeah, "it works in windows" :(

---

### Post by chochem on 2008-03-10
bumpetity bump bump... Anybody?

---

### Post by linuxwizard on 2008-03-10
Try using Ekiga see if the cam works.. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by chochem on 2008-03-10
No, sadly I get exactly the same result from Ekiga as from everything else. As I said, I do get an image, it's just completely unusable. The lower half of the screen goes purple, into static or some other craziness every two seconds.

---

### Post by linuxwizard on 2008-03-10
You might want to check and see if their is a newer version of the driver for your webcam and give that a try if available.

---

### Post by chochem on 2008-03-11
How would I do that? I don't really know what driver it is using...

---

### Post by linuxwizard on 2008-03-11
It should be the spca5xx driver. But to be sure post results of the command > lsusb

---

### Post by suterb42 on 2008-03-17
I bought this webcam a couple weeks ago, and the video works great. However, I've had some problems with the microphone. If I go to Preferences > Sound and change the sound capture device for audio conferencing to "USB Audio" (i.e. the webcam mic) and hit "Test", I can hear myself talk. However, it won't work with any other programs. Does anyone know what the problem could be? I've went through all the other walkthroughs I've seen links for without any success.

---

### Post by linuxwizard on 2008-03-18
suterb42
Look over this, see if it might help

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by scottslinux on 2008-04-15
Okay... I along with many others have been suffering from the incompatibility of linux and current webcams on the market. I am running kubuntu on a thinkpad 2.6.22-14 ... Embarrassed though I am I will admit that I have purchased three different webcams with miserable results. I installed the latest gspca driver and updated the linux-uvc driver. And still nothing..then I was given an old camera -a labtec by logitech and it functioned fairly well but with low resolution. There was hope...so with renewed enthusiasm I went back to the Ubuntu forum and found a post recommending the Logitech Quickcam Communicate STX ---which btw is avail now at best buy! The problem was that all of the old camera which were compatible are not currently for sale. The communicate STX is a new cam and avail now. It works flawlessly with camorama and skype though the former requires addition of color correction filter. easily done. Excellent microphone function. It jsut works completely!
Just wanted to pass this info on as it seems the end of a long journey and many here have helped me. Just giving back.

Thanks
Scott

---

