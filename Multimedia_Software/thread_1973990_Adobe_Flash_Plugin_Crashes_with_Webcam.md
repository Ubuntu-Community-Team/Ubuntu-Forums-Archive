---
title: "Adobe Flash Plugin Crashes with Webcam"
date: 2012-05-05
forum: Multimedia Software
---

### Post by StewartM on 2012-05-05
Greetings,

On my 10.04 machine, I have a webcam that has always worked with Flash. Well, up until recently, that is.

Now, I have discovered that if I go to a test site like:

[http://www.testmycam.com/](http://www.testmycam.com/) 

I get the error message that "The Adobe Flash Plugin Has crashed". It happens with Firefox 12 (I've backported it via PPA) and but I've tried Opera and that doesn't work either.  Needless to say, the webcam works fine locally (in Cheese and Kamoso).

Curiously, the webcam works on two other Ubuntu 11.10 machines I've tested both using Firefox 12 and Flash 11.2.202.235 (the same Firefox/Flash combon as on my 10.04 machine). I've tried completely removing the plugin from both the Ubuntu Software Center and the command line (and doing a -clean and -autoremove to remove broken packages) then re-installing it to no avail. I just can't get it to work anymore and it used to.

I've tried googling for this problem, for people having problems with the combination of 10.04/Firefox 12/Adobe Flash 11.2.202.235 (or 233) and I don't see anything--which makes me wonder if this is unique to my machine. I have the proprietary NVDIA card in my system enabled and I guess I could try re-enabling the open-source nouveau driver but I recall the webcam still worked with the NVDIA driver and besides I would think the NVIDA driver problem would probably also cause my webcam not to work locally. I don't use the webcam a lot with Flash, so I can't remember where exactly in the sequence of flash updates/Firefox updates/kernel updates this happened. I did try rolling back to the 2.6.32-40 kernel and checking and it still crashed with that. Flash works perfectly fine with all non-webcam applications.

Anyone else seeing this? Any ideas?

-StewartM

---

### Post by StewartM on 2012-05-07
Update on this.

After reading some posts, and installing Flash-Aid (thanks LovingLinux) I went back to the [Adobe Flash Archive]("http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html"). 

There, by installing various versions, I can confirm that the webcam works up to version 11.2.102.63. If I go to a later version (11.2.202.xxx) series, it does not work.

Unfortunately, that simple downgrade is not a fix, as interestingly enough, Youtubes will not play with 11.2.102.63. Other videos (say, Google Videos) will, but Youtubes hang. Youtube must be requiring the latest flash version for viewing content on its site.

So--it seems like a temporary solution until I upgrade to 12.04 (scheduled in July) is to use two browsers, one using 11.2.202.233 and one using 11.2.102.63, and manually place in the plugins folder in my /home directory the older version of just for webcam use. With firefox, at least, if you replace the libflashplayer.so file with the older one (under ~/.mozilla/plugins), Firefox will still use the older, local,  version even if you update the one for all other users in your system.

I'd like to keep Firefox though for general usage, including playing youtubes. The question then, how do you do this "local flash version override" for Chromium, Rekonq, Opera, or any other browser??

What's really weird about this all is that this somehow must be related to a library file or files or some hardware detection component elsewhere in the system, as Firefox 12 and flash 11.2.202.233 work just fine on two 11.10 systems. 

-StewartM

---

### Post by StewartM on 2012-05-07
Found at least the beginning of a fix! With Chromium, it's stored in:

/usr/lib/chromium-browser/plugins

And plopping libflashplayer.so into that allows Chromium to use 11.2.102.63 (which allows the webcam to work) but allows firefox to use 11.2.202.233 (the latest). For some reason Chromium is also playing Youtubes which Opera and Firefox did not. Weird.

The only problem with this setup is that if I update Flash, then I have to go back and manually replace the file under /usr/lib/chromium-browser/plugins with the old one. So simply putting in whatever location chromium uses for local plugins under my /home directory would still be preferable.

StewartM

---

### Post by StewartM on 2012-05-12
The last holdout--Skype. The webcam (a QuickCam Pro 9000) used to work with Skype. Now the microphone works, but not the video (at least in conferencing with a Windows7 64-bit user running Skype 5.9)

I know that there are suggestions like these:

[http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html](http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html)

But I can't see why this would be a problem, as the webcam used to work with the V4L2 library. Moreover, the last time I checked it still worked with another Linux computer running Skype 2.2 (I'll check again). This makes me wonder if the problem is with the two Skype versions (2.2 beta for Linux, 5.9 for Windows 7)--if this is just a compatibility problem between these two versions.

Still, I'd like to know if Skype uses Adobe flash, where the setting or "pointer" in Skype to Flash for Linux is, as then I could try updating that and pointing Skype to use an older version (the one that used to work).

Any hints or comments appreciated.

-StewartM

---

### Post by StewartM on 2012-05-12
> **StewartM said:**
> Moreover, the last time I checked it still worked with another Linux computer running Skype 2.2 (I'll check again). 

Just checked--the webcam works properly with in Skype test mode, and it when I skype the other user it starts up (I see the camera light come on) but the other user sees a just a blank screen). 

So it may be I have two problems, Skype compatibilities (Wikipedia says that the video codec for Skype changed from VP7 to VP8 at Skype 5.5).

-StewartM

---

### Post by StewartM on 2012-05-20
Well, found out I probably have multiple problems. Much of it boils down to hardware. I'm posting this in case someone else is helped by what I've found.

For starters, I found out yesterday that the webcam (a Logitech QuickCam 9000 Pro) *does* work with Skype in 10.04. IF I plug it directly into the computer and not a unpowered USB hub which I had plugged it in beforehand, it works. What's odd is that it worked with all other applications plugged into that same hub! It was just chance that I found this out.

I also found out that a friend computer which I upgraded to 12.04 yesterday has a Rocketfish webcam which works with Skype in 12.04 (and and probably the latest Flash/Firefox 12 as well, though I'll confirm--at least it did in 11.10). But on my 12.04 laptop, my QuickCam Pro still causes crashes with Flash and Firefox 12. This happens with both the Ubuntu repository and Adobe Flash versions, the latter installed with Flash-Aid. 

My Quickcam Pro can work with Chromium *if* I tell it to "always allow" the site access to the camera in the Adobe settings manager; if I don't do that even in Chromium clicking on the window setting to "allow" when prompted when visiting a flash webcam page it doesn't respond--nothing happens. The same seems to happen with Rekonq and Konqueror.

So it seems that one thing that might fix my problem is simply getting a new webcam. A powered USB hub if I choose to plug it into the hub could help too.

-StewartM

---

