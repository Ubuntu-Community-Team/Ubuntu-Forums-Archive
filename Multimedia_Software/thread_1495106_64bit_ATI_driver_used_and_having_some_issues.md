---
title: "64bit ATI driver used and having some issues"
date: 2010-05-27
forum: Multimedia Software
---

### Post by bone2006 on 2010-05-27
For years now I've had issues with my the restricted video that's a Radeon HD 3200 Graphics.   
99% of people I don't think would notice, because you have to actually pass audio and video through HDMI, put it on a large LCD and look for it and there's a really really tiny thin line you can see that starts on the top and goes to the bottom in a cycle if you watch any movie.

It's been so annoying to me that I went back to windows.  Well finally after a few years I tried ubuntu on my HTPC again and the line is still there.  Nothing has changed....well after looking into it.  

I went to ATI's website and download:
ati-driver-installer-10-5-x86.x86_64.run

I uninstalled the restricted driver from ubuntu an then ran these commands to install that driver:

sudo chmod +x the_name_of_the_file_that_You_have_downloaded.run
sudo sh ati-driver-installer-10-5-x86.x86_64.run
sudo aticonfig --initial -f
sudo reboot

Then I played a video and the picture quality was the best I've seen except the video was playing as if I was fastfording it and the sync was way off.   So I just went to unrestricted drivers and re-enabled the ubuntu's driver.

Well that fixed everything.  My video quality for the first time in 2 years is now working the way it should.  I don't know what happened.  I don't know if some settings ati-driver-installer-10-5-x86.x86_64.run stayed with the restricted drivers, but I'm really really happy for the first time that I actually get really good picture quality.

One problem.  XBMC won't even start up now, it complains about openGL.   Well I tried to search as much as possible on the subject and I also noticed that if I go to system, preferences, appearance, and visual effect it's off as I want it to be off.  Well I tried going to normal and it errors out about using a non-supported driver.

I'm really happy with the video quality for the first time, but it would be nice to be able to use XBMC.  Any suggestions?  Not sure about the xorg file or what I could do?  Don't want to give up this video quality for movies though

---

### Post by ghostborg on 2010-06-15
I was having problems with tearing video and choppy audio.
Videos might play for a minute and then start skipping with choppy audio.
I was focused on the audio and it never occurred to me that a setting in Compiz was my problem. I found the tidbit below in a forum. Just verify your monitor's refresh rate and move the slider, 60 worked for me. I'm no expert just relaying some info from another forum.


Compiz

Problem with sound and jerky/tearing video.
Use Compiz Settings Manager.
General->General Options->Display Settings Tab
Uncheck Detect Refresh Rate
Use refresh slider and move it from 50 to 60 hz
Verify the refresh setting from System->Preferences->Monitors
Check Sync To VBlank

---

