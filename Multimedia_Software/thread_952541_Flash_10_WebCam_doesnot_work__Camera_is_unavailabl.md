---
title: "Flash 10: WebCam doesnot work : Camera is unavailable"
date: 2008-10-19
forum: Multimedia Software
---

### Post by sarath_it on 2008-10-19
I am trying to get my webcam work with live.yahoo.com or justin.tv in ubuntu. For some reason adobe flash is unable to open my web cam. It shows up a modal dialog box: "Camera is unavailable, may be in use by another application" Results from video test on Skype, on the other hand, is positive on my system. So My webcam is not the issue here.

Screenshots and info here:
[http://blog.sarathonline.com/2008/10/flash-in-ubuntu-webcam-doesnot-work.html](http://blog.sarathonline.com/2008/10/flash-in-ubuntu-webcam-doesnot-work.html)

Another unresolved forum thread:[http://ubuntuforums.org/showthread.php?t=689094](http://ubuntuforums.org/showthread.php?t=689094)

---

### Post by sarath_it on 2008-10-20
bumping, so some one can notice :(

---

### Post by sarath_it on 2008-11-04
> **sarath_it said:**
> bumping, so some one can notice :(

really? No one? Where is the love?

---

### Post by fabiomb on 2008-11-04
maybe your camera is not supported by ubuntu (it's very common, i have two cameras, no one is supported, no drivers yet!)

wich model/brand do you have?

---

### Post by scotty64 on 2008-11-05
I am having exactly the same problem. Flash10 only discovers the "Laptop Integrated Webcam" - and that one does not work - on my Dell XPS 1330, but all the external cameras (Philips / Logitech) that used to work fine with version 9 do not work with version 10 anymore. I tried this on several Ubuntu install and all show the same problem. The only solution I came across was installing version 9 in a separate directory (/usr/local/flashplayer9) and to use "galternatives" so switch between versions when needed.
I filed a bug in Adobes bug-database. Read this and you will learn how Adobe keeps the bug statistics down - after posing with the "big strides their engineer made towards better camera support" they made the bug a missing feature and changed the status to "Resolved" and "deferred".

[https://bugs.adobe.com/jira/browse/FP-775](https://bugs.adobe.com/jira/browse/FP-775)

I would like to encourage everybody who is affected by this problem to leave an appropriate comment in the bugtracker.

Archives of old Flashplayer versions can be downloaded here:
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266)

---

### Post by TeoK on 2008-11-06
i'm having identical problem.

in 8.04 everything worked - recording , flash, skype, youtube..

upgrading to 8.10 have messed up my system completely:
flash 10 doesnt recognize my webcam ( logitech 4000) AND a linux microphone. reverting to flash plugin 9   recognizes the webcam but then there's no sound !

i've been searching all over these forums for solution with no luck.

i'm seriously thinking of wiping everything and going back to Hardy

---

### Post by scotty64 on 2008-11-06
> **TeoK said:**
> i'm having identical problem.

in 8.04 everything worked - recording , flash, skype, youtube..

upgrading to 8.10 have messed up my system completely:
flash 10 doesnt recognize my webcam ( logitech 4000) AND a linux microphone. reverting to flash plugin 9   recognizes the webcam but then there's no sound !

i've been searching all over these forums for solution with no luck.

i'm seriously thinking of wiping everything and going back to Hardy

Your soundproblem is most likely caused by "pulseaudio". While Flash10 supports pulse, Flash9 only supports it with libflashsupport installed - and that is not always free of issues. I would recommend to use alsa or try to start your browser (e.g. Firefox) with pasuspender:
pasuspender -- firefox
for this you have to make sure that there is no .asoundrc installed in your homedirectory that sets pulse as the default output.

---

### Post by TeoK on 2008-11-06
you appear to be right, Scotty.
I completely removed PulseAudio from my system and reverted to Flash plugin 9

everything works now

---

### Post by mr.big_gun on 2009-04-11
> **scotty64 said:**
> Your soundproblem is most likely caused by "pulseaudio". While Flash10 supports pulse, Flash9 only supports it with libflashsupport installed - and that is not always free of issues. I would recommend to use alsa or try to start your browser (e.g. Firefox) with pasuspender:
pasuspender -- firefox
for this you have to make sure that there is no .asoundrc installed in your homedirectory that sets pulse as the default output.











how would i do that
?????

---

### Post by scotty64 on 2009-04-16
The problem is clearly caused by the buggy v4l implementation in Flash Player 10. I am currently using an application called "Webcamstudio" to get my camera(s) running with Flash 10.
Webcamstudio is great. It creates a virtual webcam via vloopback that can be used by any kind of application (including Flash10 and Skype). You can mix almost any kind of video source (and even stills, text and console output) and apply various effects. It is based on java and uses gstreamer to manage the streams.
You get it here: [http://webcamstudio.wiki.sourceforge.net](http://webcamstudio.wiki.sourceforge.net)

---

### Post by stkrzysiak on 2009-04-29
webcam studio FTW!  Thanks scotty64.  Still working out some kinks getting wcs to output proper, but at least I am not getting the 'no webcam found' error.

fyi to anyone having issues getting webcam studio to work, I had to do a chmod 666 /dev/video* to get anything in the output dropdown under the virtual webcam tab.

---

### Post by no2498 on 2009-12-31
with adobe 10 did you reset the settings manager to allow and remember for the site you use

---

### Post by DPic on 2010-03-17
Many more details on this issue: 
[http://ubuntuforums.org/showthread.php?p=8978659#post8978659](http://ubuntuforums.org/showthread.php?p=8978659#post8978659)

---

### Post by scotty64 on 2010-03-17
The V4L1 compatibility library was the ultimate solution for all camera related Flash problems for me - here is how it works:

[http://ubuntuforums.org/showthread.php?t=1398279](http://ubuntuforums.org/showthread.php?t=1398279)

---

### Post by lleachii on 2010-06-09
> **scotty64 said:**
> I am having exactly the same problem. Flash10 only discovers the "Laptop Integrated Webcam" - and that one does not work - on my Dell XPS 1330, but all the external cameras (Philips / Logitech) that used to work fine with version 9 do not work with version 10 anymore. I tried this on several Ubuntu install and all show the same problem. The only solution I came across was installing version 9 in a separate directory (/usr/local/flashplayer9) and to use "galternatives" so switch between versions when needed.
I filed a bug in Adobes bug-database. Read this and you will learn how Adobe keeps the bug statistics down - after posing with the "big strides their engineer made towards better camera support" they made the bug a missing feature and changed the status to "Resolved" and "deferred".

[https://bugs.adobe.com/jira/browse/FP-775](https://bugs.adobe.com/jira/browse/FP-775)

I would like to encourage everybody who is affected by this problem to leave an appropriate comment in the bugtracker.

Archives of old Flashplayer versions can be downloaded here:
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266)

Thanks, I have made a comment in the Adobe bug report and posted a link to this on every Ubuntu forum regarding this issue.

---

