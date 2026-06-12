---
title: "Which WebCam?"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by CyberAngel on 2007-05-12
I would like to buy a WebCam and as I saw [here]("http://mxhaard.free.fr/spca5xx.html") the logitech USB Video Class webcams are supported on linux through Linux-UVC driver and also have by far the best quality of all other webcams!! (check the asterisks in the above site)

Has anyone try any of these webcams on ubuntu?
Quickcam Ultra Vision or QC Orbit etc..

I`m on kubuntu feisty right now ;)

Thanks.

---

### Post by sse450 on 2007-05-13
I have one of those USB Video Class webcams: Logitech Notebooks Pro. This webcam is based on the same linux-UVC driver like the ones you mentioned in your post.

linux-UVC driver uses v4l2 API. So if your client program is written to use v4l2 API, then this webcam shouldn't have any problem. At least this is the theory. BTW, I am on ubuntu feisty.

So far I have found only two programs which work with this webcam: ekiga and luvcview. I couldn't get it working with kopete and amsn.

Perhaps someone can give us a hint on how to use this webcam with clients written for v4l or info if there are other clients which use v4l2 API.

Good luck!

---

### Post by CyberAngel on 2007-05-13
> **sse450 said:**
> I have one of those USB Video Class webcams: Logitech Notebooks Pro. This webcam is based on the same linux-UVC driver like the ones you mentioned in your post.

linux-UVC driver uses v4l2 API. So if your client program is written to use v4l2 API, then this webcam shouldn't have any problem. At least this is the theory. BTW, I am on ubuntu feisty.

So far I have found only two programs which work with this webcam: ekiga and luvcview. I couldn't get it working with kopete and amsn.

Perhaps someone can give us a hint on how to use this webcam with clients written for v4l or info if there are other clients which use v4l2 API.

Good luck!

Thanks for the reply!

That`s a bit bad if it is working only with programs using v4l2 API :(

If I buy a webcam I would like it to work everywhere and mostly on messengers.. aMSN, Kopete etc

EDIT:
I Did some google search about v4l2 and kopete or amsn and as I read both programs support the v4l2 API but there is some problems with driver and the MJPEG support of aMSN and kopete probably..
Any new programs supports v4l2 API so it is not as bad as I wrote before that usv driver support only this one :)

The quotes below are from the aMSN forums!

> The logitech quickcam 5000 uses the uvc driver, which I think uses the MJPEG palette. MJPEG is not supported yet in amsn. There have been some posts about this recently. I'll paste the relevant quote here: 

> Posted: Fri Dec 29, 2006 9:41 pm  	 	 	Reply with quote
Please test with last SVN :
I currently have a fresh bought Quickcam Pro 5000 with a patched linux-uvc driver (I transmitted to the author a patch) and it works perfectly...

So now the steps to make the webcam working :
Download the last SVN of aMSN and compile it...
Download the last SVN of linux-uvc (current is r74)
File uvc_v4l2.c line 189 :
remove the line fmt->fmt.pix.bytesperline = format->bpp * frame->wWidth;
and replace by fmt->fmt.pix.bytesperline = format->bpp * frame->wWidth / 8;
Compile and install the driver...
Run aMSN and it should work well...

NB : There are several types of webcams supported by linux-uvc driver
The old ones doesn't support the YUYV format for low resolutions and for them the MJPEG should work perfectly without any patching...
For the new ones (like mine) you will have to patch the driver to avoid a segmentation fault in aMSN...
If you don't know, either patch or either wait for an update of the driver...

EDIT : the author of the driver fixed it in revision 75 !
So now you must only download the last driver version and the last aMSN version and compile/install all !

So as it says on the second quote if you use aMSN svn it will probably work now!!

Can you try it?? :)
It is very easy to compile aMSN :)

---

### Post by sse450 on 2007-05-13
CyberAngel,

First of all, no need to modify anything on SVN of linux-uvc driver as it is already done in the last trunk (r109).

I downloaded SVN of aMSN and compiled it. Yes, aMSN now supports v4l2 API. The webcam works nicely.

Besides, I would still buy a webcam which supports v4l2 as the old v4l1 is now depreciated.

Cheers.

---

### Post by CyberAngel on 2007-05-13
> **sse450 said:**
> CyberAngel,

First of all, no need to modify anything on SVN of linux-uvc driver as it is already done in the last trunk (r109).

I downloaded SVN of aMSN and compiled it. Yes, aMSN now supports v4l2 API. The webcam works nicely.

Besides, I would still buy a webcam which supports v4l2 as the old v4l1 is now depreciated.

Cheers.

Yeah I know that you don`t need to change something in the linux uvc. It also writes it as a note that it has been patched since Revision 75.. The post of the aMSN site I quoted is about 4-5 months ago :)

So if it is working now with the last amsn I will buy the Logitech QuickCam Fusion :)

(Off Topic.... Just a tip for the amsn that you may already know.. If you want aMSN to look much much much better compile it with tcl/tk 8.5. Search ubuntu forums for "DeUglify aMSN" and you will find a post describing exactly what to do)

Thank you sse450 for the replies :)

---

### Post by sse450 on 2007-05-13
Although it took plenty time, the fonts are now anti-aliased after compiling amsn with tcl/tk8.5. aMSN really looks magnificient now.

Thank you for the tip.

---

### Post by CyberAngel on 2007-05-13
> **sse450 said:**
> Although it took plenty time, the fonts are now anti-aliased after compiling amsn with tcl/tk8.5. aMSN really looks magnificient now.

Thank you for the tip.

You are Welcome :)

---

### Post by BrewBelly on 2007-07-08
Hi, I wanted to keep this thread going.

I have a Logitech Quickcam for Notebooks Pro.  I can get it to work in Ekiga (as mentioned above, it needs the v4l2 support selected).  I mostly use my can on Flash-based sites like Stickcam, but they never see the camera.

Does anyone have this (or similar) cam working on in-browser, FLASH web-chat sites?

-BB

oh, I have feisty installed.

---

### Post by CyberAngel on 2007-07-09
Finally I bought the Logitech QuickCam Fusion (I Already have this 2 months now) and it is working nicely on my kubuntu feisty amd64 :)

aMSN from svn also supports this type of webcams :)

---

### Post by hhpeter on 2007-07-09
> **CyberAngel said:**
> Finally I bought the Logitech QuickCam Fusion (I Already have this 2 months now) and it is working nicely on my kubuntu feisty amd64 :)

aMSN from svn also supports this type of webcams :)

Hi

I have a logitech ultra vision webcam and I can't get it to work  I installed the uvc driver  still nothing.
Can u tell me please how u did maybe a step by step tutorial I'm new to linux and is very probable that I did something wrong

Thank you!

---

### Post by CyberAngel on 2007-07-09
> **hhpeter said:**
> Hi

I have a logitech ultra vision webcam and I can't get it to work  I installed the uvc driver  still nothing.
Can u tell me please how u did maybe a step by step tutorial I'm new to linux and is very probable that I did something wrong

Thank you!

I am using feisty and it was/is plug n' play!
I did not need to do anything to make it work :)

It was not working with aMSN but this is aMSN`s problem. If you try aMSN from SVN is working fine :)

---

### Post by schlox on 2007-12-03
> **CyberAngel said:**
> Finally I bought the Logitech QuickCam Fusion (I Already have this 2 months now) and it is working nicely on my kubuntu feisty amd64 :)

aMSN from svn also supports this type of webcams :)


How is the video quality? Do you advise?

Actually, I am searching for the best video quality webcam which is also supported at 7.10 (not so expensive though)

Schlox
:KS

---

### Post by CyberAngel on 2007-12-03
> **schlox said:**
> How is the video quality? Do you advise?

Actually, I am searching for the best video quality webcam which is also supported at 7.10 (not so expensive though)

Schlox
:KS

Hello!

I am very satisfied from my camera`s video quality.

Also as you can see on [this]("http://mxhaard.free.fr/spca5xx.html") link that has a quality comparison (more asterisks the better the quality) between the cameras, QC Fusion has the most asterisks together with some other logitech`s QuickCams.

I am on kubuntu gutsy 64bit now and I don`t have a single problem ;)
Also it`s built in microphone works!

I can also confirm to you that it is working on aMSN (SVN) and Linux Skype 2 beta both on my laptop with an ati x700 graphics card and on my desktop with an nvidia 6600GT.
I think that it will also work with any other programs that support a webcam.

As for the price, I bought this camera from e-bay at 49Euro included the shipping costs.

I hope that I was helpful,
Good luck!

Vangelis.

---

### Post by rsambuca on 2007-12-03
> **CyberAngel said:**
> Hello!

I am very satisfied from my camera`s video quality.

Also as you can see on [this]("http://mxhaard.free.fr/spca5xx.html") link that has a quality comparison (more asterisks the better the quality) between the cameras, QC Fusion has the most asterisks together with some other logitech`s QuickCams.

I am on kubuntu gutsy 64bit now and I don`t have a single problem ;)
Also it`s built in microphone works!

I can also confirm to you that it is working on aMSN (SVN) and Linux Skype 2 beta both on my laptop with an ati x700 graphics card and on my desktop with an nvidia 6600GT.
I think that it will also work with any other programs that support a webcam.

As for the price, I bought this camera from e-bay at 49Euro included the shipping costs.

I hope that I was helpful,
Good luck!

Vangelis.

What drivers are you using with the Fusion?  According to the uvc website, the fusion is not a good choice as there are a lot of problems with it.  I can't get mine to work at all.

---

### Post by CyberAngel on 2007-12-03
> **rsambuca said:**
> What drivers are you using with the Fusion?  According to the uvc website, the fusion is not a good choice as there are a lot of problems with it.  I can't get mine to work at all.

```
$ lsmod | grep uvc
uvcvideo               52228  0
compat_ioctl32         11136  1 uvcvideo
videodev               31360  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
usbcore               161584  7 uvcvideo,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

```

As you can see the uvc driver...
I haven`t done anything at all in both of my computers.
Just recognised automatically from my kubuntu (in feisty and now in gutsy).

---

### Post by schlox on 2007-12-03
This question might seem a little lame but forgive me, I am a 1 week linux user:

You said it is working on Kubuntu. I have Ubuntu Gutsy. Those letters in front of the Ubuntu name, don't have anything to do with webcam's working condition, do they?

They are just the graphical interfaces.

---

### Post by rsambuca on 2007-12-03
> **schlox said:**
> This question might seem a little lame but forgive me, I am a 1 week linux user:

You said it is working on Kubuntu. I have Ubuntu Gutsy. Those letters in front of the Ubuntu name, don't have anything to do with webcam's working condition, do they?

They are just the graphical interfaces.

For the most part you are correct.  The uvc video drivers are built into the kernel, so it will be in *buntu.

---

### Post by schlox on 2007-12-03
Thanks for the reply. One other question:

I have a casual intel processor. This should be 32bit unlike CyberAngel's amd. May this fact affect the situation? Can there be a driver problem even if I buy the same model?
:confused:

---

### Post by rsambuca on 2007-12-03
> **schlox said:**
> Thanks for the reply. One other question:

I have a casual intel processor. This should be 32bit unlike CyberAngel's amd. May this fact affect the situation? Can there be a driver problem even if I buy the same model?
:confused:

It shouldn't, but I still wouldn't recommend the Fusion as there are known problems with it, despite CyberAngel's positive experience.  The Quickcam Pro 9000 might be a better choice, since it doesn't have any reported problems, according to the [uvcvideo developers]("http://linux-uvc.berlios.de/").

---

### Post by CyberAngel on 2007-12-03
You are correct about the K/X/Ubuntu. These are just ubuntu core with different graphical interfaces.
I am using KDE (that`s why I have Kubuntu).
So for the webcam, if is working it will not have to do with what GUI are you using, because the drivers has to do with the kernel that is the same on all ubuntu flavors.

Also for the 64bit computing I don`t think that it is problem. Actually, it is more common that the 64bit programs/drivers has problems from time to time, because of the not so good 32bit compatibility. Most of the programs are mainly focused on 32bit yet. Simple popular examples are Skype, Acrobat reader, flash player and many more.

As for the webcam problems that others experiencing with this webcam, if you check the [uvc`s project website]("http://linux-uvc.berlios.de/") you will see that > First and second generation Logitech webcams suffer from firmware bug which make the camera somehow unstable
except the following the following models:
```
046d:0990  	Logitech Quickcam Pro 9000
046d:0991 	Logitech Quickcam Pro for Notebooks (2007 model)
046d:0992 	Logitech Quickcam Communicate Deluxe
046d:0994 	Logitech Quickcam Orbit/Sphere AF
```

So probably I have a third generation of QuickCam Fusion (If exists a third generation) or I am lucky not having those bugs. 
Maybe these bugs are in combination with your hardware but then I am so lucky not having them on both of my Computers!

Also from the uvc website:> 
More information about the issue, including possible workarounds, are available on the [QuickCam Team]("http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities")  website.

So maybe try these workarounds??

Hope that any of these helps you to solve some of your questions :)

---

