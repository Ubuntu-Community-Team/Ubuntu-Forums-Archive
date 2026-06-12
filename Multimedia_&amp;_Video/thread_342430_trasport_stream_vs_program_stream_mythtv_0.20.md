---
title: "trasport stream vs program stream mythtv 0.20"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by Vincent_Lin on 2007-01-20
Dear all,

My mythtv setup (ubuntu 6.10 + mythtv 0.20) is almost complete.  But my ATSC live TV playing has been suffered by audio stutter.  somewhere I read from the web stating that it can be fixed by setting redording to transport stream instead of program stream.  But I could find anywhere in my installation of mythtv 0.20 mentioning the different options to set.  It was said that it could be set at some options while setting up Capture cards.  I could not find it.

Can someone help me to locate where I can set this option?  

Or is there a better way to solve this problem?

Thanks a lot.

Vincent Lin

---

### Post by Vincent_Lin on 2007-01-23
Dear all,

After some frustrating wait and research, I decided to disable xvmc and use standard instead at TV playback setup in mythtv.  I also played a bit on de-interlace setup, and eventually disabled it as well.  Now there is no delay or audio stutter any more, and pictures of HD/ATSC contents are perfect.  Well, except some tearing of motions as expected.  I will play a bit more on de-interlace setup to find the best combination, hopefully.  Imagine that I was so frustrated and I even suspected that maybe my antenna reception has some problem and I had to hire someone to install a rooftop antenna.  Phew!!

Another problem I have is saa7134-alsa.  

I have Intel HD audio chip and after having compilied and installed alsa driver 1.0.13, the system runs great with audio coming out of analog and SPDIF, even including front headphone jack, while I play all kinds of video clips in mplayer (vob, mpeg, avi, dat, divx etc...).  

However, live TV and recorded TV programs just would not come out via SPDIF after I enabled AC3 and DTS passthrough in mythtv.  Worst yet, analog audio output form live TV and TV recording only consists of popping sound, not real sound at all, even after the solution I described in my first paragraph above.

I always have saa7134-alsa in /etc/modules.  However, I wonder if I really don't need to have saa7134-alsa explicitly put in that file.

Does anyone have any solution to it(the popping non-sound of analog audio + no real digital output, from TV programs)?  

Or I will try the setup without saa7134-alsa in /etc/modules, tonight.

I will let you guys know.

Vincent Lin

---

### Post by Vincent_Lin on 2007-01-24
Dear all,

OK.  Here is what happened.

First, I disabled specifically saa7134-alsa loading within /etc/modules by commenting it out.  Then in mythtv frontend setup, I disabled AC3 passthrough, leaving DTS passthrough there, not using internal mixer.  

That's it.

Front headphone jack and mic, as well as rear analog 5.1 racks and digital SPDIF/optical are working properly now.   I have Options snd-hda-indel model=3stack-dig set in /etc/modprobe.d/alsa-base that enables digital output.

Mythtv 0.20 is using OpenGL for rendering.  So my photo albums has beautiful transition effects.

I use the TV out port with dangle of component video to connect to my Mitsubishi 42" TV, at 1920x1080i resolution, using latest NVidia released driver.  

mplayer is the default media player for my mythtv, and I had set it to run with -vo xvmc -vc ffmepg12mc -monitoraspect 16:9 options, so that the video clips as well vob files displayed in correct/original aspect ratio, as well as using xvmc for smoother motions.

However, live TV and recorded TV would have to be run at kernel deinterlace with standard mpeg2 decoder.  xvmc with bob does not work for me at all, as i caused autio stutter etc...

TV tuner is Kworld ATSC-110, a dual NTSC/ATSC tuner card, which is detected by Edgy default kernel.  As I said above, I do not force saa7134-alsa in /etc/modules, but I do have saa7134-dvb line in this file.  Plus, I have nxt200x firmware dvb-fe-nxt2004.fw downloaded as put in /lib/firmware, as instructed in linuxtv.org.

So far, I am very happy.  I know there is still something wrong, since I have SATA HD, and Asus motherboard with Core Duo processor, that caused some PCI can not allocate resource error, but it does not cause any ill effect, as yet, so I&#30133;ard.

Next step is to have kworld remote work, in some way.  But no rush, since both my wife and I are happy just using keyboard to navigate within mythtv.  I have a nice wireless keyboard.  Now even my 3-year-old girl knows to how press Enter and/or up/down arrow keys to going in and out of video clips.

ubuntu rocks.  ubuntuforums is the best.  Thank you all.

Vincent Lin

---

