---
title: "Resolution issue help"
date: 2010-09-23
forum: Mythbuntu
---

### Post by A3M0N on 2010-09-23
Hey all, new to MythTV, intermediate Ubuntu user.  

I'm using some old hardware to try out Mythbuntu, and its working great(ish).  I'm just using it for music and video playback due to the old hardware.  

Either Mythbuntu doesn't like my video card, or the card isn't recognizing the monitors.  The resolution caps off at 800x600, but I know the card is capable of more.  I got it working in a much better res by creating my own xorg.conf file and defining the monitor and some available resolutions.  The desktop and MythTV display great! But when I play a video in that resolution, the hardware just can't handle it.  But it also displays the video huge, like off the sides of the screen, majorly, not just a little bit.  

I guess my question is, can I have the GUI be higher res, and MythVideo play in 800x600?  

Hardware: 

P3 750mhz
512 mb RAM
S3 Savage4 APG video card

I'm happy with its performance for what it is, but I can squeeze more out of it, awesome! 

Thanks!

---

### Post by ian dobson on 2010-09-23
Hi,

I'm supprised that you could even play a video on a s3 video card. MythTV uses the Xorg resolution for videos and I don't think you can change it.

Maybe look around for a better graphic card, almost anything is better than that :)

Regards
Ian Dobson

---

### Post by A3M0N on 2010-09-23
Ha, I hear ya.  Its an old web server I had sittin around, thought I'd try it out.  Even though the desktop and MythTV GUI looks iffy, the video playback looks pretty good.  Good enough that I'll probably keep using it for a while as is.  

Now if I could only get the Graphite theme working.  It seems to be missing some images or just can't display properly in QT.  

Thanks for trying :)

---

### Post by LowSky on 2010-09-23
have you ever thought, maybe my video card doesn't like my choice of OS?

Video is usually shown in the resolution it was recorded in. You could always trancode it to a smaller resolution using software like handbrake, but its would take forever on a P3 @ 750Mhz.

I can't even recommending an upgrade to the video card. You will be limited by the AGP slot. Not much is available and none of it is current generation stuff, most will need a AGP 8x slot, which you don't have either. So replacement will be hard. And the rest of the machine is by computer life times, Ancient! 

I love it when people get old hardware working, and running things that we would all be surprised they can run. I did it as a kid with an Intel 486 @ 25Mhz, 4MB of RAM and 256MB hard drive. 

Good luck getting things working on that old machine.

---

### Post by A3M0N on 2010-09-23
I have an old Radeon 9000 in my Windows box, that computer doesn't do anything but surf the web really, and the occasional video or music playing.  It has on board video, so I'm thinking about ripping it out and throwing it into the Mythbuntu box and seeing what happens.  I've never just changed hardware in a Ubuntu machine, will it plug and play and find drivers and such?  

I like my old hardware, except that it makes me feel old :(

---

### Post by LowSky on 2010-09-24
I hate to be the bearer of bad news but that old Radeon 9000 wont do you any good. ATI doens't support models older than the HD 2xxx series for Linux, including Ubutnu.

Otherwise for hte most part Ubuntu is plug and play for hardware and drivers. Video cards can be a bit tricky sometimes, like switching form ATI to Nvidia, but if you remove the drivers before installing a new card things are not so bad.

---

### Post by A3M0N on 2010-09-24
Ok, so I yanked out the Radeon 9000 from my Windows box (onboard video, still works for the wife) and threw it in my Mythbuntu box using the "ati" driver.  Glorious.  It looks nice in the desktop and in MythTV, plays videos awesome. Still can't paint in OpenGL, not too worried about it though.  I know it couldn't play live TV, not my goal right now anyway. 

Now, to start a topic on why all the themes (except for the MythTV default ones) are missing images.  Graphite looks so tempting, but is missing the image for the menu option that is highlighted.  In any menu.  

Later, and thanks for the help guys.

Edit: Just for fun...

PIII 750 
512 MB 
Radeon 9000
SoundBlaster 16 (ISA)

Just used for music and watching TV episodes (stationed in the UK and don't like waiting for new shows).

---

