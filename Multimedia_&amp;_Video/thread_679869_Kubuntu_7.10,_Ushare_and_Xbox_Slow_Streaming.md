---
title: "Kubuntu 7.10, Ushare and Xbox Slow Streaming"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by wilburburns on 2008-01-27
OK, after much pain, I was finally able to upgrade to Gutsy 7.10 and get Ushare Installed.  All of this just to stream Music and Videos to my Xbox 360.  

Now for a little background... Previously, I had been using Windows 2000 and Tversity to stream my videos and Music to the Xbox and everything worked great without any lag or buffering problems.  BUT.. The latest version of Tversity requires Win XP and I'm not willing to purchase a new version of Windows just to do this, nor will the 700mhz computer run XP very well.  

All my current videos are currently encoded as WMV files and should not need any transcoding.  

So, I thouht I would give Ubuntu a shot... 

Now back to my current setup.. 
Ubuntu 7.10 Gutsy
Ushare 1.1 (installed from the Package, not compiled from source) - With all prerequisits (libUPNP, etc). 

The Xbox 360 sees the computer and videos fine from the dashboard.  They even begin to play, but continuously stops and begins to buffer.  I get approx 10-15 seconds of video then a pause and has to buffer another 10-15seconds.  

Here is what I think is happening... I think Ushare is trying to transcode the native WMV files to something else then stream them to the Xbox 360.  I fully realize the system is not powerful enough to do the transcoding on the Fly before sending to the Xbox.  

So, Does anyone have any idea how I can correct this issue

Thanks,
Cliff

---

### Post by DJmart on 2008-01-28
I am not 100% sure, but I think ever since I installed the latest Ushare... my WMV-HD videos have been slower to stream..

I know its not a network issue because I rebooted the routers and switches. 


I am going to see if I can uninstall Ushare 1.1 and install the older one.


-DJ

P.S. my "server" has two 3.20Ghz Xeons and 3GB of ram, so power isnt a problem.

---

### Post by wilburburns on 2008-01-28
This seems quite Odd and bad considering that I could stream Native XBOX 360 WMV files with Win 2000 and Tversity without any problems, But Ubuntu and Ushare is extremely slow... 

Upon more investigation, I see that Ushare does not do any transcoding, therefore, it should be just a direct transfer from the computer to the Xbox. 

In my situation, Speed should be directly related to my network speed.  And nothing else has changed on my network.  As a test, I even fired up the old system (Dual boot into Windows) and ran Tversity to make sure it still worked fine and it did.  

There must be something wrong....

Cliff

---

### Post by DJmart on 2008-01-28
Would be nice if we could figure this one out :P


Expert advice might just be required :P

---

### Post by DJmart on 2008-01-30
Problem solved. but not really.


I reverted back to Ushare 1.0 and all the problems of speed are gone.... and so is compatibility to watch DivX etc.



Oh well...

---

