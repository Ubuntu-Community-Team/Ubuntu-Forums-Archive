---
title: "Simple DVR options in lieu of mythbuntu"
date: 2020-01-20
forum: Multimedia Software
---

### Post by polvino on 2020-01-20
Is there such a thing as a "simple" DVR implementation? I've been toying with the idea of having a linux-based solution, but it seems awfully complex coordinating all the moving parts. Here's what I want:

[LIST=1]
[*]Linux server running 24/7 with a (compatible) 2-channel capture card for ATSC signals
[*]Front end client that can read the recordings and play them back thru an HDMI cable. Bonus if it can also access my DLNA content.
[*]Easy enough for my wife to operate (I imagine you switch TV source to the front end client, and then use another remote to access the content)
[*]Reliable! I don't want to have to troubleshoot 2 new machines to figure out why nothing works after an update. Can it be up for 2 years with no downtime?
[*]Zero ongoing cost: after purchase of hardware, no subscription or usage costs.
[/LIST]


I believe Mythbuntu had a solution like this at one time. I need guidance on what the front-end client would look like: type of motherboard, form factor, disk, fans, IR receiver, remote, etc. Also compatible tuners for whatever ubuntu distro.


Our primary use will be to pause/rewind live TV, and skip annoying commercials on newscasts and other programming. I'm in the US and my location has very strong OTA signals.

Background: Unix user since 1986, started using Slackware CDs on a PC back around 1994/5 , took a break, running Ubuntu server 18.04 headless server at home for samba and minidlna, also mint and ubuntu desktops in VirtualBox. I'm comfortable with vi and command line tools, and getting used to apt commands. So I guess I'm beginner with Ubuntu but more advanced with unix in general.

---

### Post by TheFu on 2020-01-20
Use Silicon Dust HDHR network tuners.  I have a Quattro and a dual4 for a total of 6 available tuners. ** This is a no-brainer.**  These things completely rock and allow any computing device on your subnet to use DLNA to access a tuner.  Recording a channel is just a file download from a specific URL for that channel.  I've used a combination of **wget** with **timeout** to record stuff.  That saves a .TS mpeg2 file.   Anyways, HDHR devices are compatible with every DRV/PVR/Media center out there and they don't take up a PCIe slot.  Just make certain you get one that supports DLNA. The older models needed specific drivers which were a pain to get working.
[https://www.amazon.com/SiliconDust-HDHR5-4US-HDHomeRun-Connect-4-Tuner/dp/B078LH47CD?th=1](https://www.amazon.com/SiliconDust-HDHR5-4US-HDHomeRun-Connect-4-Tuner/dp/B078LH47CD?th=1) is what I have. Got it for $69 last fall on a deal from Kroger.  They sell some other models with more features.  Silicon Dust tried to make a DVR solution.  I don't know if that actually worked out or was cancelled. Sorry. 
 
I don't know of any free schedule data solution in the US today.  Schedules Direct has a $25 or $35/yr plan that most people seem to get. Otherwise, you are stuck with the 3 hr OTA schedule which doesn't always get provided by the stations and sometimes it is incorrect. Tuners that are in-use can't be used to pull schedule data for all the other channels.

I've never gotten mythtv working, but I have seen clients/front-ends for it on almost every platform, including raspberry pis.  If you don't transcode the ATSC recordings, you'll need to buy the MPEG2 codec license from the raspberry-pi organization for $2. Without that, 1080i shows will stutter.  However, the h.264 video codec is enabled without any license on all raspberry pis, so if you transcode the recordings, you'll have both 60% smaller files, less chance of network stuttering and pretty great resolution.

If you want 4K playback, I don't think any of the raspberry pi models are suitable today. The v4 was supposed to handle it, but I keep seeing issues around 4k playback.  I'm waiting.

If you aren't anti-MSFT, then NextPVR might be a viable option for a DVR.  The Linux version isn't quite ready. I tested it out a few weeks ago. As for playback devices, I like Kodi/OSMC.  Kodi is a DLNA controller and renderer, but not a DLNA server (to my knowledge).

ATSC v3 is coming to the USA. It is being trialed in a few metro areas. Existing tuners will likely become useless when the rollout happens in your area.  It doesn't use mpeg2, selecting to use AVC1 or h.265 which compresses better for higher resolutions but also requires much stronger GPUs to decode it.  None of my video playback devices can handle that codec today.  There will probably be a few years of overlap where both standards are broadcast.

---

### Post by Tadaen_Sylvermane on 2020-01-22
Mythtv is very simple to set up. Granted, it took me quite a time to sort out what is required and what isn't. The guides around the internet are all just a little different. I can get a backend configured in a couple minutes now. For a frontend I use Kodi. My Mythtv backend cheat sheet is in another thread. This is a no frills simple basic setup how I do it. I'd recommend a schedulesdirect.org account and sync with that. 25 bucks a year non profit. Worth it in my opinion.

[https://ubuntuforums.org/showthread.php?t=2429750&p=13901108#post13901108]("https://ubuntuforums.org/showthread.php?t=2429750")

This cheat sheet is actually extracted from my script which does it all for me. Haven't had an issue yet with it.

Post #9

---

