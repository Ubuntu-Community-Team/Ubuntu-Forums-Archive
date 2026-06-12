---
title: "Ubuntu friendly camcorders"
date: 2009-11-14
forum: Multimedia Software
---

### Post by dillandriskell on 2009-11-14
Hi!

I am going to buy a camcorder, but I want to avoid the mistake I made last year when I bought a printer incompatible with Ubuntu :(

Soo I'm looking for a camcorder compatible with Ubuntu.  One that has good quality, not great (a.k.a. expensive), but decent enough.  I'm not sure what the terminology for camcorders are but I do NOT want the one's with tapes, I'm looking for one with a hard drive.  Other than that I'm not too picky.

So long question short, does anyone know where I can find a list of Ubuntu 9.10 compatible camcorders?

I haven't found very much documentation on the subject, or maybe I just suck at Google :P  But any help with the subject would be MUCH appreciated.

Oh, and in case hardware is an issue I'm running a Dell Dimension 5100.

---

### Post by tidris on 2009-11-14
I would recommend SDHC memory instead of hard disk. If you go for SDHC, I would recommend a model that comes with no internal flash at all. Let all recording be on external SDHC cards.

I would recommend a camcorder with a 1080p mode over one with only 1080i mode. I have found 1080i video doesn't look so good on a computer screen due to the interlacing artifacts in moving scenes. The progressive scan modes (1080p, 720p, etc) don't have that problem.

As for compatibility with Ubuntu, if the camcorder has a USB2.0 port it should show up as a hard drive on the desktop when you connect it to the computer. Then you can simply copy the video files as you would with an ordinary external hard drive. If you go with SDHC cards and your computer has an SDHC card reader, that gives you an additional way to transfer the video files.

The video codecs in Ubuntu aren't always up to date and Ubuntu might not include some important codecs due to licensing issues. In case of trouble you might end up having to get the latest video codec source code from the developers and compiling it yourself.

---

### Post by RedRat on 2009-11-14
I have a Canon HDV Vixia HV30, it has 1080p output. This is a tape camera and not a hard drive or card. I connect via a FireWire and can get the video imported into Ubuntu. 

Since I am running 8.04 I use the command line to get the HD video off the tape. Works fine. The Ubuntu video editing software for 1080p is a bit sketchy right now for my particular distribution but perhaps improved for 9.10, e.g., KdenLive, Cinelerra, etc. So far, at least for me, the video editing software has been the main limitation since HD seems quite new to the Linux group. Think that might improve in the next year.

---

### Post by metol on 2009-11-14
I just had my Canon Vixia HF20 show up today and I am fairly impressed with the camera.  A night and day difference from the our VHS tapes I just converted over to mpeg format.  The HF20 has 32Gb of internal storage and a SDHC slot for additional storage.  I believe the HF200 is the same camera but only has the SDHC slot for storage (ie no internal storage).

A problem that I am having is that when I connect the camera via USB to my Ubuntu box (ver 9.10), the transfer seems to be limited to MTP only... for the life of me I can not set this so that is sees the internal memory and the SDHC card as 'standard drive'.  MTP seems to be the only option aside from connection to Canon's dvd recorder under the USB options.  OK, this does not seem like a big deal, Ubuntu does recognize the drives eventually (literally takes 5min or so).   And after waiting several minutes, I can transfer files but it is extremely slow.  On the order of 50kb/s.  It took about a half hour to transfer a video recorded in 1080p that was only about 1 minute in length.  The solution is to copy the videos from internal storage to an SDHC card in camera (easy to do).  Pop out the SDHC card then transfer to my computer.  A little bit of a pain, but doable. I am hoping to resolve this slow transfer issue.

So in hind sight, I probably should have saved $100 by going for the HF200 model since I seem to have to copy the files to the SDHC card anyway so that I can efficiently move them to Ubuntu.  So I will second the comments made by tidris regarding external storage.

Aside from this slow transfer issue, I have had a few other minor issues.  The camera stores the videos in 'MTS' format (AVCHD Video File).  From what I gather this is true of almost all HD video recorders.  Mplayer plays the file, but the audio does not sync.  Gxine gripes of a missing codec (not sure what is going on there).  I did find that the VLC player does a pretty good job but chews up quite a bit of CPU while playing the file since it lacks VDPAU support for my nVidia video card.  My PC is not top of the line but no slouch either (E8500 dual core processor @ 3.2GHz with an nVidia 9500GT graphics card).  Not sure what a Dell Dimension 5100 has under the hood, but if you are looking for HD playback and editing of 1080p video, I would not go much lower than this.

Transcoding the MTS file to mpeg works wonders though and playback in mplayer is quite good after doing this operation.  I have been chopping them down to lower resolutions since full 1080p is a little bit of overkill for me.

Sorry for rambling on... just wanted to share my experience in the hopes that it might be helpful to others.

Regards,
Metol

---

### Post by MusJet on 2009-11-15
Hello [dillandriskell]("http://ubuntuforums.org/member.php?u=933992") ! 
If you want buy one camcoder totally linux compatible look for samsung HMX-H105.
This camcorder records video in the MPEG-4 AVC/H.264 format. You can play video using mplayer, vlc, xine and others.
Also this camcorder do: 1080/60i/60i N/30P, 720/60P (60 frames per secs progressive is fantatisc, pretty smooth video)
Also you can edit using avidemux editor. Of course, you will need re-encode but this program has good resources.
Its a excellent camcorder !

Check site:
[http://www.camcorderinfo.com/content/Samsung-HMX-H105-First-Impressions-Camcorder-Review-36130.htm](http://www.camcorderinfo.com/content/Samsung-HMX-H105-First-Impressions-Camcorder-Review-36130.htm)

Cheers,

  MusJet

EDIT: if you need videos sample, send me private message.

EDIT2: If you dont need Full HD (1080i) camcorder, exist other choice cheap and good performance. Its HD camcoder (720p with 60fps)
check site:
[http://paulstamatiou.com/review-samsung-sc-hmx10c-hd-camcorder](http://paulstamatiou.com/review-samsung-sc-hmx10c-hd-camcorder)

EDIT3: At 1080i with HMX-H105, we have a problem but solved. Check [http://ubuntuforums.org/showthread.php?t=1302249](http://ubuntuforums.org/showthread.php?t=1302249)

---

### Post by cotcot on 2009-11-15
Buy a camera with exchangeable data carrier such as SDHC cards. If the camera does not get recognised as mass storage through a usb or firewire cable than at least you have a fall back with a SDHC card reader.

More important is to check out the file format that the camera stores (.mts , .mpg, ...) and look for a video editor that can handle this format or check if ffmpeg/mencoder is able to convert it in a useable format. 
look for sample files of the camera of your choice and check it out.

I have a Canon HF100. It produces .mts (AVCHD file format) that I convert with mencoder to .mpg and edit mostly with blender VSE and sometimes with cinelerra. It is too early for a well proven direct AVCHD editor.

---

### Post by RedRat on 2009-11-15
> A problem that I am having is that when I connect the camera via USB to my Ubuntu box (ver 9.10), the transfer seems to be limited to MTP only... for the life of me I can not set this so that is sees the internal memory and the SDHC card as 'standard drive'. MTP seems to be the only option aside from connection to Canon's dvd recorder under the USB options. OK, this does not seem like a big deal, Ubuntu does recognize the drives eventually (literally takes 5min or so). And after waiting several minutes, I can transfer files but it is extremely slow. On the order of 50kb/s. It took about a half hour to transfer a video recorded in 1080p that was only about 1 minute in length. The solution is to copy the videos from internal storage to an SDHC card in camera (easy to do). Pop out the SDHC card then transfer to my computer. A little bit of a pain, but doable. I am hoping to resolve this slow transfer issue.

That really does not sound right. Are you sure that it is not transcoding as it moves the data? That is way to slow for USB, i.e., 50kb/s. USB is far, far faster than that. Perhaps you transfer cable is faulty.

---

### Post by metol on 2009-11-15
> **RedRat said:**
> That really does not sound right. Are you sure that it is not transcoding as it moves the data? That is way to slow for USB, i.e., 50kb/s. USB is far, far faster than that. Perhaps you transfer cable is faulty.

Good point - I will try with another cable.  I know my usb ports are good because my external hard drive transfers at around 25Mb/s.  I do not believe it is transcoding, just transferring.  CPU is near 0% but I/O is pegged according to system monitor.

- - - - -

Update - I replaced the USB cable with a known good one and still have lousing performance.  Tried on another box running 9.10 and the results were the same.  Plugged it into my kids box running XP and it transfered fine there... scouring the net but not finding a solution.

- - - - -

Second Update - My wife's laptop is running Ubuntu 9.04, it works just fine transferring at 7.5Mb/s.  Go figure, I'm guessing this is an issue on 9.10?

---

### Post by RedRat on 2009-11-15
> **metol said:**
> Good point - I will try with another cable.  I know my usb ports are good because my external hard drive transfers at around 25Mb/s.  I do not believe it is transcoding, just transferring.  CPU is near 0% but I/O is pegged according to system monitor.

- - - - -

Update - I replaced the USB cable with a known good one and still have lousing performance.  Tried on another box running 9.10 and the results were the same.  Plugged it into my kids box running XP and it transfered fine there... scouring the net but not finding a solution.

- - - - -

Second Update - My wife's laptop is running Ubuntu 9.04, it works just fine transferring at 7.5Mb/s.  Go figure, I'm guessing this is an issue on 9.10?

I guess this is a good reason to not jump on the latest and greatest update. I am sure that it will be fixed. This is one reason I continue to run 8.04 and will probably wait a couple of months after 10.04 is released to upgrade. It sounds as if there might be a problem with your USB drivers, maybe they are holdover from 9.04. By chance, do you have good transfer rates with something other than that camera, e.g. a hard drive running thru that USB port, or some other device???

---

### Post by dillandriskell on 2009-11-15
Thank you tidris, metol, and cotcot.  You've all given me a lot of information, really good points, and known issues for me to consider when purchasing a camera, now I pretty much know what to look for.  So I'll go for SDHC (no need for internal flash), one with 1080p not 1080i (a.k.a. progressive scan mode), and one that has a USB port (SDHC will make file transferring easier).  And aside from that when I've put enough aside to buy the camera I'll probably have to put aside a little more to upgrade to a decent graphics card :oops:.

Thank you redrat and musjet for giving me specific cameras I can look at.  I really don't think I can do the Canon HDV Vixia HV30 though, I can't stand how long it takes to transfer files from tape and I don't have firewire :( However the Samsung HMX-H105 seems rather promising and I've already bookmarked the links you provided musjet :D I just hope it comes in 1080p.

Again thank you all for the extensive information, this gives me a lot to work with.  I still have to look around a bit, but now I know exactly what to look for and I have some examples of what does work.

And good luck to metol with your camera problem, I'm sure a patch will be provided in the future.  I keep having issues with the new 9.10 as well and I'm considering duel booting it with 9.04 but I'll probably just tough it out till it's fixed :P

---

### Post by tidris on 2009-11-16
One more thing to look for is the size of the image sensor (CMOS or CCD). The larger it is the better the quality of the videos indoors and in low light in general. However the larger the sensor chip the more expensive the camcorder will usually be. So if you buy a model with a small sensor don't expect great videos in low light. 

My Samsung HMX-H100 has a small sensor and it makes grainy looking videos in low light, but I got what I paid for, and I expect to take most of my videos outdoors during daytime. This model does 1080i but not 1080p. However it also does 720/60p which works very well for the kinds of videos I like to take (with lots of fast moving scenes). Of course, if someone gave me a new camcorder with a huge image sensor and 1080/60p mode, I would be more than happy to accept it :). 

If you want to see what a 720/60p video looks like, here is one I took recently:
[http://www.youtube.com/watch?v=SJXHWCFN42Q](http://www.youtube.com/watch?v=SJXHWCFN42Q)


As for USB speed, you should be able to get at least several megabytes per second transfer speeds from a modern digital camera or camcorder that has a USB2 port. It isn't enough for the computer to have USB2 port, the camera itself also needs to have a USB2 port to get the higher speed, and if there is a USB hub between camera and computer, the hub also needs to have USB2 ports.

---

### Post by metol on 2009-11-16
> **RedRat said:**
> I guess this is a good reason to not jump on the latest and greatest update. I am sure that it will be fixed. This is one reason I continue to run 8.04 and will probably wait a couple of months after 10.04 is released to upgrade. It sounds as if there might be a problem with your USB drivers, maybe they are holdover from 9.04. By chance, do you have good transfer rates with something other than that camera, e.g. a hard drive running thru that USB port, or some other device???

All other USB devices seem fine on 9.10.  My external hard drive transfers at around 25Mb/s but this is in MSC mode (Mass Storage Class).  I think the problems is that my camcorder only uses MTP mode (Media Transfer Protocol).  Works fine in 9.04, but I suspect something is not right in 9.10.

I am sure it will be fixed and I have reasonable workarounds.  Just a temporary inconvenience. Thanks for your help and suggestions.

---

### Post by dillandriskell on 2009-11-16
First of all, you have a really steady hand tidris! :D You got some really good shots.  Your Samsung looks like more than enough for what I could possibly ever need it for, so I'm definitely looking into that particular model.

Image sensor size, another thing I'll keep in mind!  Being a half-nocturnal insomniac I probably want to invest more in this field.  I just checked and luckily I do have USB 2.0 (which I was surprised to find as my computer's over 8 years old) so that's good.  

> **tidris said:**
> Of course, if someone gave me a new camcorder with a huge image sensor and 1080/60p mode, I would be more than happy to accept it :smile:. 

Haha, if I ever have any just lying around I'll let you know :P

---

### Post by lisati on 2009-11-16
I have a Sony DCR-SR45 which both Windows (XP & Vista) and Ubuntu see as a 30GB hard disk. The quality isn't the greatest I've used - it's automatic setting *sometimes* have trouble coping in poor light, particularly if there's backlighting, but it has spot-focus and spot-exposure which can be quickly used to set things manually if needed, and I think its resolution is only 720 rather than 1080. (Edit: it can take stills, but it doesn't have a flash, so the lighting needs to be good)

I also have a couple of tape based cameras (one a Digital-8 model by Sony and a MiniDV model by Panasonic) which can be used with FireWire/i.Link, though getting them to work with Ubuntu would need some tinkering with the firewire drivers.

(confession: I do most of my video editing with Windows)

EDIT: Sample footage, which has had a little bit of processing can be found here:

Sony DCR-SR45 (HDD, USB) - [http://www.youtube.com/watch?v=gThbOBaUhDU](http://www.youtube.com/watch?v=gThbOBaUhDU) (sunlight, editing could have been better)

Sony DCR-SR45 (HDD, USB) - [http://www.youtube.com/watch?v=uUheQ2o_zNo](http://www.youtube.com/watch?v=uUheQ2o_zNo) (performers on stage inside, soundtrack has had backing track added)

Panasonic NV-GS27 (MiniDV, firewire) - [http://www.youtube.com/watch?v=qNm1aD74r0o](http://www.youtube.com/watch?v=qNm1aD74r0o)

Sony DCR-TRV147E PAL (Digital-8, firewire) - [http://www.youtube.com/watch?v=pB7TYjF8UV8](http://www.youtube.com/watch?v=pB7TYjF8UV8)

---

### Post by dillandriskell on 2009-11-16
> **lisati said:**
> I have a Sony DCR-SR45 which both Windows (XP & Vista) and Ubuntu see as a 30GB hard disk. The quality isn't the greatest I've used - it's automatic setting *sometimes* have trouble coping in poor light, particularly if there's backlighting, but it has spot-focus and spot-exposure which can be quickly used to set things manually if needed, and I think its resolution is only 720 rather than 1080.

I also have a couple of tape based cameras (one a Digital-8 model by Sony and a MiniDV model by Panasonic) which can be used with FireWire/i.Link, though getting them to work with Ubuntu would need some tinkering with the firewire drivers.

(confession: I do most of my video editing with Windows)

Thanks!  That's another model I'll look at.  I've got a Sony right now that I'm ditching because it's tape.  If you're looking for good video editing software for Ubuntu I'd recommend Pitivi.  I haven't used it yet but I've heard a lot of good things about it.  I've been Microsoft free for over two years now and I'd hate to turn back now for this #-o

I wonder if you can get the more advanced video editors to work on Ubuntu with Wine though?  Like Sony Vegas Pro and Adobe After Effects.  I wouldn't want to shell out a thousand dollars for Adobe After Effects though unless I was sure it worked! :shock: Or better yet I wonder if there's freeware out there that can come close to After Effects?  Hmm, definitely worth looking in to.

---

### Post by spegru on 2009-11-22
Hi lisati. My brother has one of those Sony DCR-SR45 cams and is using ubuntu based Linux Mint (down to me!). When you plug into ubuntu, what exactly happens and is there anything special you have to do to extract the videos from the cam? Also what format do they come in? 

thanks

---

### Post by RedRat on 2009-11-22
> **spegru said:**
> Hi lisati. My brother has one of those Sony DCR-SR45 cams and is using ubuntu based Linux Mint (down to me!). When you plug into ubuntu, what exactly happens and is there anything special you have to do to extract the videos from the cam? Also what format do they come in? 

thanks
A bit more information would be helpful here. How does the camera output? e.g., FireWire, USB, etc. Also, what version of Mint? i.e., is it based on 9.04, 8.10, 8.04, or is it the new RC1 based on 9.10?

---

### Post by spegru on 2009-11-24
Unfortunately i dont have the camera to hand as my brother has it in New Zealand an I am in UK.
However I am told it uses USB.
My brother and i are both using Gloria - so ubuntu 9.04 based.
My bro is not that tech so I am helping remotely
I just want to know if there was any special tricks to get the thing to appear as an external hard disc. If it just comes up as a disc then maybe he just hasnt spotted it!

---

### Post by gordintoronto on 2009-11-28
> **metol said:**
> All other USB devices seem fine on 9.10.  My external hard drive transfers at around 25Mb/s but this is in MSC mode (Mass Storage Class).  I think the problems is that my camcorder only uses MTP mode (Media Transfer Protocol).  Works fine in 9.04, but I suspect something is not right in 9.10.

I am sure it will be fixed and I have reasonable workarounds.  Just a temporary inconvenience. Thanks for your help and suggestions.

When I connect my Samsung F30 to a 6-year-old system running Karmic, files transfer at 4 MB/sec, same as when I connect to my new computer running Jaunty.  Both computers see the Samsung as an external hard drive.

---

### Post by metol on 2009-11-28
> **gordintoronto said:**
> When I connect my Samsung F30 to a 6-year-old system running Karmic, files transfer at 4 MB/sec, same as when I connect to my new computer running Jaunty.  Both computers see the Samsung as an external hard drive.

Thanks for the info... do you know if you are communicating in MTP mode?

I did a little more digging and found the following error in dmesg after connecting the camcorder:

> device descriptor read/all, error -110

I found the following [Ubuntu Bug Report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433438") (unique to Karmic kernel 2.6.31) which closely resembles the issue that I am having.  I will certainly post here once I find a solution or the issue has been resolved.

---

### Post by gordintoronto on 2009-11-28
> **metol said:**
> Thanks for the info... do you know if you are communicating in MTP mode?



To my computer, my camcorder appears to be a hard drive.  I think that means I am not communicating in MTP mode.

---

### Post by spegru on 2009-12-01
Good news: The Sony DCR-SR45 cam seems to work perfectly without any changes. It comes up as external drive over USB. All I need to do now is to show my bro how to edit, but that's nothing to do with the cam

---

### Post by johnwillis on 2010-02-27
> **metol said:**
> Good point - I will try with another cable.  I know my usb ports are good because my external hard drive transfers at around 25Mb/s.  I do not believe it is transcoding, just transferring.  CPU is near 0% but I/O is pegged according to system monitor.

- - - - -

Update - I replaced the USB cable with a known good one and still have lousing performance.  Tried on another box running 9.10 and the results were the same.  Plugged it into my kids box running XP and it transfered fine there... scouring the net but not finding a solution.

- - - - -

Second Update - My wife's laptop is running Ubuntu 9.04, it works just fine transferring at 7.5Mb/s.  Go figure, I'm guessing this is an issue on 9.10?

Just a quick note - I had similar problems with Ubuntu 9.10 when it did a kernel update to 2.6.31.19 i think...

All I did was use "Startup Manager" to tell it to boot my previous version of the kernel (2.6.31.17) i think and it sorted out my USB copy speed under 9.10

As I say I think it is more to do with something being updated (or broken) under the hood rather than your camera or cable...

---

