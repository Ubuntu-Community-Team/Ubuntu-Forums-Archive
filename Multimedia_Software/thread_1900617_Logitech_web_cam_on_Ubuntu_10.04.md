---
title: "Logitech web cam on Ubuntu 10.04"
date: 2011-12-26
forum: Multimedia Software
---

### Post by paulmagarey on 2011-12-26
p { margin-bottom: 0.21cm; }  I have a Dell Latitude D610 loaded up with dual boot Windows XP and Ubuntu 10.04.3 Desktop i386 image.  
 

 Web cam works fine on Windows.
 

 For a long time my Logitech web came was not recognised on Ubuntu, then out of the blue, it started working - just once, on cheese and skype and google talk, then the computer froze and crashed and then it stopped being recognised and I've done a complete re-install but still can't get Cheese to find the device.
 

 Relevant lsusb output:
 Bus 001 Device 003: ID 046d:08c3 Logitech, Inc. Camera (Notebooks Pro) 
 

 So I believe the camera usb input is recognised and I have some kind of driver problem.
 

 I've installed guvcview and get the following message:
 

 Guvcview error: unable to open device: Please make sure the camera is connected  and that the correct driver is installed.
 

 I've installed xawtv from the Ubuntu Software Centre but it doesn't seem to run when I select it from the menu.
 

 I've been unable to find easy instructions for running Gstreamer, so can't test output from that.
 

 Output from ls /dev/video* is:
 

 paul@paul-laptop:~$ ls /dev/video* 
 /dev/video    /dev/video2   /dev/video31  /dev/video43  /dev/video55 
 /dev/video0   /dev/video20  /dev/video32  /dev/video44  /dev/video56 
 /dev/video1   /dev/video21  /dev/video33  /dev/video45  /dev/video57 
 /dev/video10  /dev/video22  /dev/video34  /dev/video46  /dev/video58 
 /dev/video11  /dev/video23  /dev/video35  /dev/video47  /dev/video59 
 /dev/video12  /dev/video24  /dev/video36  /dev/video48  /dev/video6 
 /dev/video13  /dev/video25  /dev/video37  /dev/video49  /dev/video60 
 /dev/video14  /dev/video26  /dev/video38  /dev/video5   /dev/video61 
 /dev/video15  /dev/video27  /dev/video39  /dev/video50  /dev/video62 
 /dev/video16  /dev/video28  /dev/video4   /dev/video51  /dev/video63 
 /dev/video17  /dev/video29  /dev/video40  /dev/video52  /dev/video7 
 /dev/video18  /dev/video3   /dev/video41  /dev/video53  /dev/video8 
 /dev/video19  /dev/video30  /dev/video42  /dev/video54  /dev/video9 
 

 I've spent a long time trying to sort this one out and am totally frustrated. 



Any help targetted at a newbie would be appreciated.


:confused:

---

### Post by Rhizoid on 2011-12-27
Have you tried the settings in;  ```
gstreamer-properties &
```

---

### Post by paulmagarey on 2011-12-27
Thanks for that advice. Output as follows:

```
paul@paul-laptop:~$ gstreamer-properties &
[1] 1955
paul@paul-laptop:~$ gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline6/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline7/GstV4l2Src:v4l2src1:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Custom': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline8/GstV4l2Src:v4l2src2:
system error: No such file or directory]
```

The really weird thing is that the output from 'ls /dev/video*' seems to have changed:

```
paul@paul-laptop:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
```

I would have thought this indicates a hardware problem?? Except that Windows XP works fine (if slow)

---

### Post by Rhizoid on 2011-12-27
Have you tried the camera in a different USB port?  It running, but slowly, in XP would make me think hardware too.

---

### Post by paulmagarey on 2011-12-27
yes, have tried all different ports. XP as a whole runs slowly (especially to load), but Web cam and skype are fine on XP. Probably just need to remove some software as I don't think I've run into any hardware problems using XP and I did conduct Memory Testing (for a while) before most recent installation of 10.04.

---

### Post by Ms. Daisy on 2011-12-27
It seems that Logitech does not play nicely with Ubuntu.  I've seen a lot of threads about Logitech cameras failing to work. Here's one that may help you: [http://ubuntuforums.org/showthread.php?t=1897464](http://ubuntuforums.org/showthread.php?t=1897464)

And perhaps a more promising one here:
[http://ubuntuforums.org/showthread.php?t=1893830](http://ubuntuforums.org/showthread.php?t=1893830)

Hopefully those can set you in the right direction.

---

### Post by Cpierce on 2011-12-27
This is what fixed it for me using Skype. Maybe there is something in this command to help you out:

[http://ubuntuforums.org/showpost.php?p=8390933&postcount=13](http://ubuntuforums.org/showpost.php?p=8390933&postcount=13)

Basically, right click on "Applications" and select "edit menus", then go to internet and find Skype. Highlight it and click on properties. Delete the command and replace it with this:

 sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'

---

### Post by paulmagarey on 2011-12-28
> **Ms. Daisy said:**
> It seems that Logitech does not play nicely with Ubuntu.  I've seen a lot of threads about Logitech cameras failing to work. Here's one that may help you: [http://ubuntuforums.org/showthread.php?t=1897464](http://ubuntuforums.org/showthread.php?t=1897464)

And perhaps a more promising one here:
[http://ubuntuforums.org/showthread.php?t=1893830](http://ubuntuforums.org/showthread.php?t=1893830)

Hopefully those can set you in the right direction.
Thanks for this. Different circumstances. The web cam won't even work with Cheese, with one exception. If I have just been using the webcam on my XP (I run a dual boot) it seems to work for a while with both cheese and Skype, but then eventually stops working! Totally bizarre. At least, it's happened this way twice. 

Have tried with another webcam, unfortunately again a Logitech (Quickcam Express Plus) and again, this one works initially briefly, then stops, though I can manage to take a photo with Cheese, even if I can't see myself on the screen. In Skype, the screen is just blank. 

Totally frustrating. Any other advice for a newbie would be welcome.

---

### Post by paulmagarey on 2011-12-28
tried this and it stopped skype working once I'd re-booted. Thanks anyway!

---

### Post by Cpierce on 2011-12-28
That is really weird. It should not have stopped Skype. Sorry, but this is over my head, but at least you ruled this fix out and are one step closer.

---

### Post by paulmagarey on 2012-03-23
Is there any way of getting this problem promoted to a higher level?  Am totally frustrated by this problem. Be grateful for any advice.

---

### Post by sffvba[e0rt on 2012-03-24
*Thread moved to **Multimedia & Video**.*

Hopefully some others can see your problem here and give advice.


404

---

### Post by mörgæs on 2012-03-24
I also have a D610 with a Logitech web cam, and with Lubuntu 11.10 in a fresh install Guvcview works out of the box (actually I worked with the developer to fix some bugs in the previous version, so I can almost promise you a good result). 

The version number must be 1.5.3 or above.

---

### Post by paulmagarey on 2012-03-25
> **mörgæs said:**
> I also have a D610 with a Logitech web cam, and with Lubuntu 11.10 in a fresh install Guvcview works out of the box (actually I worked with the developer to fix some bugs in the previous version, so I can almost promise you a good result). 

The version number must be 1.5.3 or above.

THanks, and yes, I have tried Ubuntu 11.10 on this D610 and found the camera did work but the computer because ridiculously slow (and some other things didn't work - I can't remember) so I went back to Ubuntu 10.10. Maybe I should try the Lubuntu version. I was just hoping that if they can fix it for Ubuntu 11.10 couldn't they also fix it in 10.04?? 

thanks for the tip.

You wouldn't have any advice on my wireless issue as well would you?  Would Lubuntu fix that?  See [http://ubuntuforums.org/showthread.php?t=1945971](http://ubuntuforums.org/showthread.php?t=1945971)

Cheers,

Paul

---

### Post by mörgæs on 2012-03-25
10.04 being maintained means that security bugs are fixed, not that new functionality is added. It is very unlikely that Guvcview will be backported.

Xubuntu and Lubuntu 11.10 are your best options. When you have one of these running with wired internet access we can take a look at the wirefree.

---

### Post by paulmagarey on 2012-03-28
> **mörgæs said:**
> 10.04 being maintained means that security bugs are fixed, not that new functionality is added. It is very unlikely that Guvcview will be backported.

Xubuntu and Lubuntu 11.10 are your best options. When you have one of these running with wired internet access we can take a look at the wirefree.

well, I managed to install Lubuntu 11.10 and initially couldn't get the webcam working, but after installing a stash of gstreamer applications (no idea what they do) from the Lubuntu Software Centre, the web cam is now working! YIPPEEEE! Do you think I could also get the webcam's inbuild microphone working as well?  Any advice on this?  Will also work on trying to get the wireless features working - any advice on this appreciated as well, but I should probably create a sepate problem for this.

Cheers,

Paul

---

### Post by mörgæs on 2012-03-28
It surprises me that you had to install anything beyond the regular updates. Are you on version 1.5.3 of Guvcview, and was it a clean install of 11.10?

Anyway, for sound problems I recommend
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

and for networking 
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
(including the sticky notes).

---

### Post by paulmagarey on 2012-03-28
> **mörgæs said:**
> It surprises me that you had to install anything beyond the regular updates. Are you on version 1.5.3 of Guvcview, and was it a clean install of 11.10?

Anyway, for sound problems I recommend
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

and for networking 
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
(including the sticky notes).

looking up Guvcview on the Lubuntu Software Center shows the installed version as being only 1.4.5-1 - and it seems rather unstable - crashed whenever I try and record video with it.

Re clean install, I md5sum'ed the file and the CD and checked the CD for errors as well as checked the memory of the PC for half a day - all fine. But there was one issue with the install - the photo to go with log-on didn't work. And there seem to be other things wrong e.g. the re-boot facility doesn't seem to work very well. Will look at those sound and networking issues, but any advice on whether I should re-do the install would be appreciated.

cheers,

Paul

---

### Post by paulmagarey on 2012-03-28
also Cheese seems to crash easily as well...

---

### Post by mörgæs on 2012-03-28
Sorry, I forgot that I installed 1.5.3 from the PPA. Instructions are here:

[http://guvcview.sourceforge.net/downloads.html](http://guvcview.sourceforge.net/downloads.html)


You could also install Lubuntu 12.04 beta, if you want guvcview and all the other new packages in one go. Though it is a beta it is fairly stable. If you have a few GB spare, you could install next to 11.10 for comparison.

Always remember to have wired internet access while installing.

---

### Post by paulmagarey on 2012-03-28
> **mörgæs said:**
> Sorry, I forgot that I installed 1.5.3 from the PPA. Instructions are here:

[http://guvcview.sourceforge.net/downloads.html](http://guvcview.sourceforge.net/downloads.html)


You could also install Lubuntu 12.04 beta, if you want guvcview and all the other new packages in one go. Though it is a beta it is fairly stable. If you have a few GB spare, you could install next to 11.10 for comparison.

Always remember to have wired internet access while installing.

well, based on this and the previous advice that you were surprised that I needed anything other than regular updates, and also because guvcview & cheese were crashing and sometimes when I re-booted the mouse wouldn't move or the task bar down the bottom wouldn't appear, I decided to do a complete re-install. Have now completely removed the packaged version of guvcview (1.4.something) and installed guvcview as per instructions above (ie [http://guvcview.sourceforge.net/downloads.html](http://guvcview.sourceforge.net/downloads.html)). Initially it seemed to work, though did crash when I tried to open a file from it. As I don't really need to use it, I thought I'd install skype and have now got that installed, but camera is not working. Currently, without any gstreamer files installed, have no video on skype, cheese can't find the camera and guvcview no longer can find the camera or the 'correct driver'. GRR. So, I think my only option is to install some gstreamer files, not that I have any idea what they do... Have not installed Lubuntu Software Centre this time - am just going to rely on Synapic - do you think that'll be OK??

cheers,

Paul

---

### Post by mörgæs on 2012-03-29
Have you tried 12.04 in a live boot?

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

---

### Post by paulmagarey on 2012-03-29
> **mörgæs said:**
> Have you tried 12.04 in a live boot?

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

No, not yet. I can do so (have now downloaded the file), but it just seems I'm going from version to version without getting any problems fixed. Currently guvcview works when I initially start it up, then it crashes as some point and refuses to work again until I re-start the computer. No video with skype, though I'm hoping if I install Gstreamer files that it'll come good. Would be happy to do some testing or give further data if so directed.

Cheers,

Paul

---

### Post by paulmagarey on 2012-03-30
> **mörgæs said:**
> Have you tried 12.04 in a live boot?

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

Have downloaded the file, MD5SUM checked out ok, burned disk, again MD5Sum checked OK, used the check disc facility when using the disc from boot, but then when trying to run the live CD it just freezes, so, hmm, don't think this is a goer for me. Any data you'd like?

Cheers,

Paul

---

### Post by mörgæs on 2012-03-30
You need to do some more testing.

Does the CD boot other computers? 
Can you boot the D 610 with a USB stick created with Unetbootin?

---

### Post by paulmagarey on 2012-05-12
> **mörgæs said:**
> You need to do some more testing.

Does the CD boot other computers?
Can you boot the D 610 with a USB stick created with Unetbootin?

Have managed to:
* create Linux Mint 12 USB boot stick and install on ACER desktop
* run Linux Mint 12 USB boot stick on this Dell Lattitude D610 without installing, though it was very slow and kept on freezing
* create Lubuntu 12.04 USB boot stick from which I then installed it on a ACER desktop and it runs OK.

I can not, however, get Lubutu 12.04 installed on this Dell Lattitude D610 at all, via CD ROM (with correct MD5SUM) or via USB boot stick. Each time the laptop just freezes, either when trying to run 12.04 live (without installing) or when trying to go straight to the installation. The 12.04 CD doesn't even get to the boot menu before freezing, whereas the USB boot stick gets past the boot menu and allows me to check the disk (its OK) but then freezes when trying to install or run as live.

Be grateful for any advice. Currently I've re-installed 10.04 and that seems to be working fine, though I've got to install all the software updates yet and I haven't really tested in on all the programs I want to run.

Has anyone else had issues with installing 12.04??

---

### Post by mörgæs on 2012-05-13
Have you tried the alternate ISO for Lubuntu 12.04?

---

### Post by paulmagarey on 2012-05-19
> **mörgæs said:**
> Have you tried the alternate ISO for Lubuntu 12.04?

Well, I misread this and tried the alternate ISO for Ubuntu 12.04, which installed OK and I was getting hopefull for a while, but then it freezes when trying to boot after installation seemed successful. Am anticipating this will happen with altenate ISO for Lubuntu 12.04, but will give it a try!  Yikes! frustrated.

---

### Post by paulmagarey on 2012-06-16
Have now tried so many varieties of alternative iso's and etc I'm really sick of it!  I can not get Lubuntu 12.04 installed on this D610, though I can get it working on my ACER desktop. So it seems I'm stuck with Lubuntu 11.10, for which I've just recently re-installed and web cam seems to be working fine after installation of Gstreamer files (didn't test without them - should have). So, it seems like when Lubuntu 11.10 runs out of support I'll have to get a new distribution of Linux as I can't get 12.04 to work in any form... though I suppose I haven't tried Xubuntu. Is this even more lightweight?  

I've still got 10.04 working on it as a back up to the 11.10, but managed to erase my MS Windows files by stuffing up the grub file at one point... any feedback welcome.

---

### Post by mörgæs on 2012-06-17
You should see any of the supported Lubuntus as valid candidates. There is no reason to switch to 12.04, if 11.10 is working fine.

11.10 is supported until april 2013, so you will have the option of trying both 12.10 and 13.04 when that time comes. 

Testing 12.10 in development and reporting the bug is also an option.
[http://ubuntuforums.org/forumdisplay.php?f=416](http://ubuntuforums.org/forumdisplay.php?f=416)

Xubuntu is medium-weight. Should be no problem for a D610.

---

### Post by paulmagarey on 2012-10-24
I can't seem to get Lubuntu 12.04 working on my Dell Latitude d610.

---

