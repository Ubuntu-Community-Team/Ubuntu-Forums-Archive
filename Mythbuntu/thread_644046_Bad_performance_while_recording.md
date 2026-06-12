---
title: "Bad performance while recording"
date: 2007-12-18
forum: Mythbuntu
---

### Post by WaggonerW on 2007-12-18
I have the following system: 

- GigaByte MA69GM-S2H mainboard with onboard ATI Radeon XPRESS 1250; 
- Athlon 64 X2 4200+; 
- 2 GB DDR2-667 dual channel Kingston memory; 
- Samsung Spinpoint T166 (HD501LJ) 500 GB SATA II harddisk; 
- Samsung SH-S203B DVD writer; 
- Terratec Cinergy 1200 DVB-C.

I have done a fresh install of Mythbuntu 7.10. After sorting out problems with the video driver (using fglrx now), scanning channels etc. I have got it working, but some problems are still unsolved. 

The biggest problem is that when watching live TV, the performance is not good enough to prevent frame skipping. There also seems to be relatively heavy disk access. While playing recordings however, everything's very smooth and there hardly seems to be any disk access. 

I have already moved the DVD writer and the harddisk to differen SATA channels, to no avail. 

There has been a bug report about slow SATA performance (see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730)), I'm not sure if this could have something to do with it. When I get the drive settings for /dev/sda with hdparm, it shows it is not using any DMA mode. When I attempt to switch it into DMA mode, it fails and I get the message that it reverts to PIO. But then there are also reports that say this can't be set at all for SATA drives. 

My questions are therefore: 
- Is the harddisk performance a likely cause for this problem? 
- Is there anything I can do to solve or work around this? 

Thanks for any help!

---

### Post by majoridiot on 2007-12-18
hard disk performance will absolutely cause issues like dropped frames.
until you get to the bottom of the possible hard disk issues, there is one thing
that comes to mind--

you could try increasing the buffer to see if that helps... i know i had to increase
it for best performance streaming HD over firewire.

the buffer setting is in frontend setup: tv settings-->general-->general (advanced) 

by default the HD ringbuffer size is set @ 9600.   i recommend you adjust it up a
step at a time, testing livetv as you go.  if you find a setting that stops dropped
frames, stop there-- setting the bufffer too high can be as bad as too low.

---

### Post by WaggonerW on 2007-12-18
Thanks for the suggestion. I have tried several settings, but in my case it doesn't seem to have any effect on the frame rate.

---

### Post by jayson.rowe on 2007-12-18
Is "MythBuntu" a distribution or a Meta-Package?

If it's a distribution, does it ship w/ the Real-Time Kernel?

If it's a Meta-Package, try installing the Real-Time Kernel to see if that helps your situation.

---

### Post by tgalati4 on 2007-12-18
Check your SATA settings in BIOS.  Sometimes you can get a little more performance by tweaking.

This might be related to another post with throughput limits hitting 33 MB/sec going through a gigabit ethernet.  The motherboard may have a bottleneck in the SATA/IDE controller that is causing slowdowns due to excessive interrupts.  During simple playback this might not be a problem due to buffering.

Post the output of:

>sudo hdparm -tT /dev/sda

---

### Post by WaggonerW on 2007-12-18
Yes, MythBuntu is a distro and I'm not sure about the real-time kernel, but it must be optimised for multimedia. 

My timings look good:
 
/dev/sda:
 Timing cached reads:   2190 MB in  2.00 seconds = 1095.94 MB/sec
 Timing buffered disk reads:  246 MB in  3.00 seconds =  81.96 MB/sec

But that doesn't necessarily men anything. It took me about 8 seconds to copy a 218 MB file. 

I have already looked at the bios, but there are no user configurable settings for SATA. 

Strange thing is that the framerate looks good for a fraction of a second until disk activity kicks in.

---

### Post by jayson.rowe on 2007-12-18
Does it use the Ubuntu repos?
If so you can install the realtime kernel packages - it works wonders for doing audio recording - I would assume it would do the same for recording realtime video.

---

### Post by jayson.rowe on 2007-12-18
*UPDATE
I did some research for you, and trolled through some mailing list archives, and it seems that Mythbuntu doesn't ship w/ the RT kernel by default, but it is a reccomended tweak, so simply "apt-get install linux-rt" - it'll keep your old kernel in place as an option in grub should you want to go back.

---

### Post by tgalati4 on 2007-12-19
218 MB in 8 seconds is ~27.25 MB/s even though the drive can support 82 MB/sec, which is excellent.  So obviously there is a bottleneck.

The framerate in the beginning is being fed by your high memory throughput:  1,095 MB/sec until it asks for more from the disk then it's 1/100 that speed.

The real-time kernel will help reduce interrupts at the expense of a super-laggy mouse and keyboard, but that won't cure a throughput problem.

Who knows what the required throughput needed for HD content?  720p vs 1080p?
I'm sure it's greater than 33 MB/s.

---

### Post by majoridiot on 2007-12-19
> **tgalati4 said:**
> Who knows what the required throughput needed for HD content?  720p vs 1080p?
I'm sure it's greater than 33 MB/s.

it depends on the bitrate of the stream itself, which may be the problem here.

check to see what the recording bitrate is set at- you'll find it in setup-->tv settings-->recording profiles-->live tv.
i suggest cranking down the bitrate a little at a time to see if and where the dropped
frames stop happening.  if this helps, my guess is the impact on the quality of 
the livetv video will be negligible.

---

### Post by tohc1 on 2007-12-19
Are you sure it's a hard disk problem, I have a motherboard with the same chipset 690G with the express 1250 (Biostar TA690G) and I had problems with the xv overlay not being enabled which led to bad playback when watching TV.

Running the frontend from a terminal gave me a message about no overlays found will drop frames etc....

It turns out that the fglrx drivers (as far as I'm aware - as of around November07) don't support any overlays yet as it's too new.This could be your problem, unless you know of some newer drivers that do support xv i which case I'd be keen to find out. In the end I installed a nvidia card in the computer.

---

### Post by WaggonerW on 2007-12-19
I'm not sure it is the harddisk. I have been struggling with video drivers too, I still have an issue with live video overlaid in the program guide, which is garbled and misplaced. Have you tried the closed source ATI driver? 

I am currenlty trying to get everything running on the realtime kernel, it meant recompilation of some extra modules that I require. I will also try the suggestion of the bitrate. Still I have the feeling that my system should be powerful enough to handle these framerates. 

I also noticed that the frame skipping is not always the same. For instance, I have had times when there was hardly any skipping while watchng and recording an HD channel.

---

### Post by WaggonerW on 2007-12-19
I think I should give up on this realtime kernel. As soon as I start watching something now, mythfrontend aborts. I already tried other MPEG filters, but no joy. I think I'll just revert to the standard kernel and start looking into solving the video problems.

---

### Post by WaggonerW on 2007-12-20
I have reinstalled MythBuntu completely, because I kept having issues with the realtime kernel, this time with a different TV card (SkyStar DVB-S) but it has the same problem. Concerning the rate, it is DVB which directly receives and writes MPEG-2 1 to 1, so I can't crank this down. I think the chance is still big that it is caused by the SATA drive, or the ATI video driver.

---

### Post by majoridiot on 2007-12-20
have you ensured that xv overlay is properly configured in your xorg.conf?  per old notes i have from
when i was running an ati card, i had to add the following to the "Device" section of xorg.conf for 
the video card.  as i recall, ati-config was pretty dodgy generating a correct xorg.conf (not that 
nvidia is much better in that respect). ;)

```
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
```

as a troubleshooting measure, you can also try running mythfrontend from a terminal window- then
launch livetv.  when the video starts, alt-tab back to your terminal window and see if it is throwing
xv-related errors or any other errors that might help track this down.

---

### Post by WaggonerW on 2007-12-20
Thanks majoridiot, that was a good suggestion. It did not fix the problem (now I have no image at all), but at least we are getting some troubleshooting info now: 

2007-12-20 20:15:02.334 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-12-20 20:15:02.334 Using protocol version 31
2007-12-20 20:15:02.347 TV: Attempting to change from None to WatchingLiveTV
2007-12-20 20:15:02.348 Using protocol version 31
2007-12-20 20:15:02.411 DPMS Deactivated 
2007-12-20 20:15:02.433 NVP: Disabling Audio, params(-1,2,44100)
2007-12-20 20:15:02.445 VideoOutputXv: Physical size of display unknown.
                        Assuming 17" monitor with square pixels.
2007-12-20 20:15:02.446 VideoOutputXv: XvMCTex: Init failed
2007-12-20 20:15:02.446 VideoOutputXv Error: Could not find suitable XVideo surface.
2007-12-20 20:15:02.446 VideoOutputXv: Falling back to X shared memory video output.
                              *** May be slow ***
2007-12-20 20:15:02.701 Realtime priority would require SUID as root.
2007-12-20 20:15:02.703 TV: Changing from None to WatchingLiveTV
2007-12-20 20:15:02.706 Couldn't load deinterlace filter bobdeint
2007-12-20 20:15:02.719 Video timing method: USleep with busy wait
2007-12-20 20:15:07.052 VideoOutputXv Error: 
***
* Your system is not capable of displaying the
* full framerate at 1440x900 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.

---

### Post by tgalati4 on 2007-12-20
I found this at another post.  Good explanation of where bottlenecks can occur.  It only takes one to screw up video playback.

[http://www.dell.com/content/topics/global.aspx/vectors/en/2004_pciexpress?c=us&l=us&s=corp](http://www.dell.com/content/topics/global.aspx/vectors/en/2004_pciexpress?c=us&l=us&s=corp)

Vido playback at higher resolutions can often exceed the pci bus throughput.

Try running at 640 by 480 or 800 by 600 and see what your performance is like.

---

### Post by WaggonerW on 2007-12-22
OK, to me it is clear now that the frame rate problems are caused by the lack of support from the ATI drivers for XV, at least where the usage of XV by MythTV is concerned. I have installed the latest ATI Catalyst drivers (7.12), but the problems remain. 

I suppose for playback Myth uses a different method, probably OpenGL, can anyone could confirm this? 

Is there anyone who can report a decent frame rate for Live TV using any ATI card? I suppose the only option is wither to wait for a new driver providing better support OR a new MythTV version using something else then XV OR get an NVidia card.

---

### Post by majoridiot on 2007-12-22
unfortunately you are discovering the same lack of support and annoyances that finally
led me to abandoning ATI cards altogether.  i fought xv and tv out for months, then 
switched to nvidia cards.

i've never been happier and had ess trouble.

you would be surprised how little money a workable nvidia card costs- i had a triple-screen rig
running myth on third head that was driven by 2 *cheap* 5500FX cards.  i never had a problem
with dropped frames, etc. and both cards were less than $130 for the pair.

IMO, a switch to nvidia will seriously improve your quality of life ;)

---

### Post by WaggonerW on 2007-12-22
Majoridiot, I suppose you are right. 

One more update: the reason I have problems getting XV to work is probably my 690G chip set, see [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting). I am still trying to figure out if the problem is the chipset or the ATI driver, I don't want to be stuck with the same problem with a new NVidia board on this chipset.

---

### Post by majoridiot on 2007-12-22
ATI is your problem, i think... i have not seen any reports of that chipset having the same problems with nvidia cards.

if you can, borrow a newer nvidia card to test before buying a new one.  i definitely would stay with a more 
modern series of cards- something new withing the last year or so, to avoid legacy issues.

even the cheap cards work very well- a 5500fx pci (not pci-e or agp) card i was using had no problems at all
with 720p HD streamed over my network from firewire out on the cable box... it never dropped frames, etc.
and ran beautifully with no interlacing.

---

