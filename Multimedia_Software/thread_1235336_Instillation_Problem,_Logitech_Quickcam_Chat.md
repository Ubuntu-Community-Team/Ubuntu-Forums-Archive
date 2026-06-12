---
title: "Instillation Problem, Logitech Quickcam Chat"
date: 2009-08-09
forum: Multimedia Software
---

### Post by GuitaristS on 2009-08-09
Hello, I have recently purchased a "Logitech Quickcam Chat" just to find out, I cannot get it to work on my ubuntu, when I double click the icon on my desktop that appears once I insert the disk. 

The option setup.exe appears, of course that's how you set it up, and of course you can't rune .exe's in Ubuntu, so I tried it with Wine, I get no response, it might be trying, it might not, all I know is that it doesn't work. 

I don't know what else to do really, that is why I'm here, please help ASAP, I have an angry misses who is out of town who wants to see me on it while she's gone. 

Thanks.

EDIT: I Installed Camorama webcam viewer, it opens, and Instantly has an error, "Unable to capture image." and closes.

---

### Post by bcschmerker on 2009-08-10
Sorry, it looks as though ye put yourself up a creek without a paddle.  Upon reviewing the [berliOS® LinUX USB Video Class&#8482; project page](http://linux-uvc.berlios.de/), I saw no mention of your camera model, meaning that it most likely uses a CCD that is unsupported in UVCVideo.  The minimum camera from [Logitech® Corporation](http://www.logitech.com/) that is known supported in LinUX as of 9 August 2009 is the QuickCam® Communicate&#8482; MP (SPCA 527 CCD; P/N 960-000240), recently superseded in production by the Webcam&#8482; C500 (CCD unknown as of 9 August 2009; P/N 960-000371).

I am currently testing the likewise recently-discontinued QuickCam® Communicate&#8482; Deluxe&#8482; S7500 (SPCA527 CCD; P/N 960-000247), which packs a manual-focus glass lens; the Communicate MP and Webcam C500 use fixed lenses (plastic for the MP, glass for the C500).

Addendum:  Upon reviewing the [Non-UVC Webcams page](http://www.quickcamteam.net/devices/non-uvc-webcams) at QuickCamTeam.net, I discovered that your model, the QuickCam® Chat&#8482;, uses the SPCA561B CCD, which may or may not be supported in the BZip2 tape archive for the GSPCA driver source-code in the Ubuntu repositories (Logitech® provided for this model in the SPCA5xx driver package).

---

