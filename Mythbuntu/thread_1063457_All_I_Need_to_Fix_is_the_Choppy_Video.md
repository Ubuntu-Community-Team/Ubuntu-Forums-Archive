---
title: "All I Need to Fix is the Choppy Video"
date: 2009-02-07
forum: Mythbuntu
---

### Post by carrucha on 2009-02-07
So close.

OK, I've tried and failed many times at getting a linux dvr working.  We've had Tivo for the last year and like it a lot (OK, we like DVRs, not necessarily Tivo).  I really want to make it work, I just have one issue left.  My video is choppy.  Too choppy to watch.  I've read several threads about this and have tried some of the advice offered, but I still haven't gotten it to work.  A couple of years ago I actually did have good video (but other issues), so it's pretty irritating that I can't get it now.  Here's my setup:

Mythbuntu 8.10
IBM Netvista P4 1.8GHz
796MB RAM
160GB IDE HD
WinTV PVR-150

I've got everything working except, well... the most important part.  I have tried a few things to fix the video, but have been unsuccessful so far.

My first thought was that my video card needed something other than the "open source" drivers.  Do the open source drivers typically work just fine?  I tried getting the updated driver for my card, but it said that it was built into Ubuntu and no longer needed/offered.  So thinking that was the problem I went to a (gave up) Windows XP MCE setup.  I didn't like it much, but the video worked perfectly!  I decided I wouldn't wimp out that easily (though I've spent way too much time on this already).  

So I changed to a better video card.  Couldn't get X to work after that, so I just reinstalled.  Once everything was good to go I tested again and... same problem!  It was also using the open driver, but it looks like I have the option now to use the proprietary one.  I tried to install it, but it wouldn't download for some reason.  Anyway, I would assume the open driver would be good enough, but correct me if I'm wrong.  So I'm ruling out the video card since they both are giving me the same problem.

Here are my other red flags and things to note:

I'm pretty much using the out of the box install.  Haven't changed anything yet.  Ext3 file system.
I've installed in the "safe video" or whatever mode.  Seemed like I had to, not sure if that matters.
System seems to work fine until I watch live TV, then HD immediately starts working hard.
Recorded TV choppy too.
What should my screen resolution be on the TV?
My cable connection isn't that great.  My Tivo works good enough.  An issue?
Initially I thought it was a slow hard drive, so I used a newer one.  Didn't fix anything.
I turned off the IDE acceleration stuff in my BIOS thinking it was causing issues.  Didn't fix anything.
I'm using S-VIDEO out to a CRT TV.  Is S-VIDEO good enough?
For a CRT TV, do I need to change my video size, bitrate, etc?  Am I doing extra work with too high of settings?
DVD playback seemed to be just as bad.

A separate question...  Once I get this perfect, how do I image the setup for a quick reinstall?  Ghost didn't seem to be able to handle Ext3, etc.

Thanks,
Damon

---

### Post by carrucha on 2009-02-07
Update: Installed the proprietary ATI/AMD driver and watching live TV... worse.  It froze on a single frame although it continued to record.  Playing it back showed the same single frame, but in the thumbnail area it showed perfectly that it had recorded. 

Any ideas?

---

### Post by |{urse on 2009-02-07
open a terminal ( applications > accessories > terminal )

type this command

> gstreamer-propertiesclick the upper right tab and select (NoXv) from the dropdown list. 
click Ok
viola!

---

### Post by carrucha on 2009-02-08
Nope, that didn't work.  App wasn't installed, but after installing it and running it as you said, it didn't change anything.  Clicking on the test button suggested it was a valid configuration.

I tried a couple of other things as well:

1. Enable OpenGL vertical sync for timing. (This improved it some)
2. Change from MPEG2-PS to MPEG2-TS. (No noticeable change)
3. Turn off audio in BIOS. (No noticeable change)

There's something in there that's eating up too much CPU.  When running the frontend and watching TV, here's my load:

2.1

mythfrontend.re 65% CPU
Xorg 7%
mythbackend 4%
lirc_dev 1%

Seems pretty CPU-intensive since I have on-board MPEG encoding (PVR-150).  Correct me if I'm wrong.  But a load of 2.1 I would think would be enough to do it.

Getting out of the frontend and live TV the load is around 0.05.

Also, watching the video with an LCD monitor through VGA looks the same.

So, is it a problem with my system being to slow?  Is there some eye candy I can turn off that will help?  Everywhere I read says I have more than enough hardware for this modest DVR.

Thanks.

---

### Post by nicoloks on 2009-02-08
> **carrucha said:**
> A separate question...  Once I get this perfect, how do I image the setup for a quick reinstall?  Ghost didn't seem to be able to handle Ext3, etc.

Thanks,
Damon

Hi Damon,

Seems you are in a similar situation to me. Desperately wanting to use Linux but are hitting major hurdles, and the Windows MCE demon is starting to appear on your shoulder as you know it will just work without all this fuss. For you it is video, for me it is the remote control/IR receiver.

Anyway, I can't offer you much advice as far as your card goes. I currently use the onboard Nvidia 6150 which is perfect for anything upto 720p or 1080i, but doesn't cut it for 1080p. I'm about to upgrade to an Nvidia 8400GS to get VDPAU support as it makes a HUGE difference when watching mpeg 1/2, x264, wmv or vc1 encoded 1080p material. I've seen systems go from near 100% cpu usage with drastic stutter and audio sync issues to only using 15% CPU with no issues simply by using VDPAU. That's Nvidia only though, not sure what vendor you are using.

For backups I'd suggest using remastersys. It is about the closest thing you'll get to ghost on linux from my experience.

---

### Post by carrucha on 2009-02-08
Thanks for the tip on remastersys, I'll have to give that a try.  

Anyone have any other thoughts on the video issue?

---

### Post by scary_jeff on 2009-02-08
Try recording a program, then opening the file with a different player, for example mplayer. I guess that if this plays back ok, then there isn't a problem with your tuner.
You could also try using something like MeTV, to prove you have enough processing power to capture and play TV at the same time.

---

### Post by rschapman on 2009-02-08
What playback profile and on screen display are you using? I had a machine with almost the same specs and I had to change those settings to it working right. Once I changed the OSD and Playback to slim and CPU-- it worked fine for me.

---

### Post by carrucha on 2009-02-09
I haven't tried the other stuff yet scary_jeff, but rschapman I did change the playback profile to CPU-- and then to slim.  Not sure if that's what you meant.  I didn't see anything in the OSD to change for that.  Please clarify if you meant for me to do something else.  Doing that looks better and lowers the load on the system a lot.  It's still hovering around 1.2 I think.  My understanding is that a load of 1 means the computer can keep up with exactly what it's doing and a load of 2 means everything takes twice as long since the system can't keep up with the demand.  Correct me if I'm wrong.  So if that's true, I would think I'd need to get below a 1 to not lose performance. 

The picture looks really great now, but it still seems like it's dropping a lot of frames.  Anything with much motion in it looks bad.  I'll take a look at the other stuff though.

Any other thoughts?  This same hardware seemed to work better when I tried this a couple of years ago.  And do the open video drivers work fine for most people?

---

### Post by carrucha on 2009-02-10
So, I tried changing some of the recording bitrates, size, etc and it made a little difference, but not much.  It just seems like my hard drive is working too hard.  

I tried playing a recording in the VLC Media Player and the picture looked much better!

So... where do I go from there?  I can't be opening up some other player all the time.  How can I make mythtv show the recording better?  

And is this the effect of my computer being so slow?  Because it's true, this computer is getting older, but it's plenty powerful enough from the documentation I read.  They need to change it if that's the case.

---

### Post by newlinux on 2009-02-10
If it plays recordings fine in other players but not in myth your disk probably isn't the problem. Especially for PVR-150 recordings which should work on very old hardware. Your problem is most likely:

1. Myth's internal player doesn't play well with ATI. YMMV in all cases with aTI video

2. Most likely you need to play with your playback profiles. I'd actually recommend you try others like CPU++.

for more detailed help, I need to you see your frontend logs from when you are playing back recordings and having problems. You may need to create a custom playback profile to get the best possible picture (I did on all my frotends after playing for a while). I recommend you not change the settings in the stock profiles and create new ones when you want to play, so you always have the stock ones set to their defaults...

[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

---

### Post by tehbeermang on 2009-02-11
I also have a Hauppauge 150. Mine was absolutely painful on live tv and recordings, chopping, flickering green and purple with some nasty ghosting. 
> **carrucha said:**
> 
2. Change from MPEG2-PS to MPEG2-TS. (No noticeable change)

I changed that setting to MPEG1 VCD quality on all four profiles.

It's slightly fuzzy, but it works!

---

### Post by carrucha on 2009-02-13
Tried the VCD thing.  It did make the video perfectly smooth at that point, but the picture wasn't very sharp.  Overall, I'd say there wasn't any gain.

So... I'm thinking I just need newer hardware.  Is that really going to be how to make it work?  

Or do I need to downgrade the software?  Would MythTV on an older Linux work better than mythbuntu?  Or an older version of mythbuntu?  It worked 2 years ago on this same hardware!

---

### Post by carrucha on 2009-02-13
So... I'm probably too new at Linux to understand all this.  I've been trying to make sure I have DMA turned on on my hard drive.  It should be enabled in BIOS, but checking to see if it's turned on in the OS doesn't seem to be working.  

$ sudo hdparm -d1 /dev/sda?

/dev/sda1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

Doing a df shows that my drive is sda.  

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             11535344   1752708   9196668  17% /
tmpfs                   386484         0    386484   0% /lib/init/rw
varrun                  386484       368    386116   1% /var/run
varlock                 386484         0    386484   0% /var/lock
udev                    386484      2784    383700   1% /dev
tmpfs                   386484         0    386484   0% /dev/shm
lrm                     386484      2000    384484   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6            147292260    174840 147117420   1% /var/lib

So, now I'm confused, sda... is that correct for my IDE drive?  Shouldn't it be hda?  

Is this a big problem, or am I just not getting it?

Thanks.

---

### Post by newlinux on 2009-02-14
sda is right - ubuntu read all drives now as sd* - they made this change a few releases ago.

what does:

```

sudo hdparm -i /dev/sda1

```

return? That will show you what DMA mode your drive is using and capable of.

---

### Post by tehbeermang on 2009-02-14
> **carrucha said:**
> Tried the VCD thing.  It did make the video perfectly smooth at that point, but the picture wasn't very sharp.  Overall, I'd say there wasn't any gain.

So... I'm thinking I just need newer hardware.  Is that really going to be how to make it work?  

Or do I need to downgrade the software?  Would MythTV on an older Linux work better than mythbuntu?  Or an older version of mythbuntu?  It worked 2 years ago on this same hardware!Are you running an ATI video card? ATI linux support is sketchy.

Wednesday night I updated my video card from the 32m onboard vga (I think it was an intel vga chip) to a PNY NVidia chip model (AGP slot, 256m, $54 at TigerDirect) with the restricted NVidia Linux drivers.

I can run the MPEG2 format without flickering now. 

To put your mind at ease about old hardware: the rest of my Myth system was harvested from an old Compaq. It's an AMD2400+ processor and 256m PC2100 ram.

---

### Post by carrucha on 2009-02-16
Video card (swapped the better one out since it made no difference) is a Geforce2 MX 200.  Nvidia?  I see lots of people have this card, so I don't think it's a problem.  It's just a problem with the built-in player, it works outside of mythtv just fine.  

I need to look at the output of 
  sudo hdparm -i /dev/sda1
when I'm in front of the box.

---

### Post by carrucha on 2009-04-30
Gave up.  Got a faster computer.  Works now.

---

