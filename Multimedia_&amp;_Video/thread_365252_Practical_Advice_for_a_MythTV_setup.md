---
title: "Practical Advice for a MythTV setup"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by jethro10 on 2007-02-19
Hi,
I've read everything to death about mythTv but still have questions. I wonder if any Actual users of MythTV here can answer some of them.
I've sucessfully installled it all on a PC without a tuner card, just to get a feel for it and to see if I could. All seems fine. UK based BTW.


1. Is ext2/3 ok for the file system. It implies its not the best, deleting big files it seems. How does yours work?

2. Freeview DTV cards. Most seem to be software based for mpeg encoding. Can anyone recomend a Hardware based card available in the UK?

3. If I have to stick with software encoding, what impact will recording 2 chanels say, have on a reasonable P4 2.6Ghz processor with 1Gb ram. What resolution do you normal record in to be as good as normal TV.

3a. To record one program while watching a previous recording, Do i need 2 cards?

4. It seems that you can record in mpeg2, So to watch a recording I guess i just use a Normal linux media viewer on the file ? this seems strange ! I gather Myth just shells out to a player?

5. On my normal consumer DVD player, I can GOTO say, 48 minutes into the program. How does Myth do this. It seems all the current players use sliders to navigate a file.

6. Can you recomend an analogue card (to capture an input from my Sky box). Is this right, I need a seperate sound card for this to record the sound? wow!

7. If I play a DVD or have an MPEG stream with Dolby 5.1 can you pass this through to the Soundblaster digital output to go to my surround system. Currently it seems to be downmixing to stereo-totem, gxine etc. Am I missing something.

8. Reliability - software wise, Is this really good enough to replace my other gear permanently.

Hope this is not too much for anyone.

Ta
Jeff

---

### Post by barney_1 on 2007-02-19
> **jethro10 said:**
> 
1. Is ext2/3 ok for the file system. It implies its not the best, deleting big files it seems. How does yours work?
Yes, you can use ext2/3 for your file system.  I did for a while but when I decided I needed  more room for recordings (wend from 80gigs to 180gigs) I used gparted to resize my partitions appropriately and then reformatted the large one in XFS.  I would recommend that you keep a separate partition for recordings if you plan to use your computer for services other than mythtv.

> 2. Freeview DTV cards. Most seem to be software based for mpeg encoding. Can anyone recomend a Hardware based card available in the UK?
I'm certain that there are pal versions available of mpeg encoder cards.  But since I'm in the US, can't get you specifics.

> 3. If I have to stick with software encoding, what impact will recording 2 chanels say, have on a reasonable P4 2.6Ghz processor with 1Gb ram. What resolution do you normal record in to be as good as normal TV.
You need to get the hardware incoder cards.  With your setup you will be able to record two channels at once if both are hardware encoder cards.  With software encoding you will be limited to one.  The resolution will be just as good as normal TV.

> 3a. To record one program while watching a previous recording, Do i need 2 cards?
Yes, but I do have my cable TV hooked up to my mythbox AND my TV, so I can just change my TV input and watch live tv there if mythtv is currently recording.  You also have the option to watch a recording currently in progress or a previously recorded show.

> 4. It seems that you can record in mpeg2, So to watch a recording I guess i just use a Normal linux media viewer on the file ? this seems strange ! I gather Myth just shells out to a player?
I think mythtv used mplayer to play it's recordings.  You can play it on anything, I also like to use either nuvexport or mytharchive if you want to save your recordings but also free up some space.

> 5. On my normal consumer DVD player, I can GOTO say, 48 minutes into the program. How does Myth do this. It seems all the current players use sliders to navigate a file.
I use a remote (via lirc) to operate Mythtv.  I use the arrow keys to navigate; up/down goes forward/back 10 minutes, right goes forward 30 seconds, left goes back 5 seconds.

> 6. Can you recomend an analogue card (to capture an input from my Sky box). Is this right, I need a seperate sound card for this to record the sound? wow!
Look for a capture card that has RCA or SVIDEO inputs on it.  You can set those inputs up as a different encoder input.

> 7. If I play a DVD or have an MPEG stream with Dolby 5.1 can you pass this through to the Soundblaster digital output to go to my surround system. Currently it seems to be downmixing to stereo-totem, gxine etc. Am I missing something.
No idea.

> 8. Reliability - software wise, Is this really good enough to replace my other gear permanently.
This is a subjective question.  I find that my MythTV box replaces my girlfriend's vcr (I really never recorded stuff on tape so the ability to record is a new feature for me).  I also find that it replaces my live tv watching (I don't use my digital cable box anymore, and will probably get rid of digital cable until the switch in 2009).  

That being said, I still have a modded Xbox that I think is a far superior media center for streaming audio, video, DVD ISO, and pictures over my home network.  I use both boxes about equally.

---

### Post by scottishnarn on 2007-02-19
I use the Avermedia DVB-T 771 and it works great. It is however, a little hard to get a hold of now. BTW if it's digital TV then the card doesn't do any encoding at all. It's already in mpeg2 format, since it's a digital channel. It only works with free to view channels though, as do all current PC cards I think. To get top up tv you're going to need a seperate digi box and an encoder card (I use WinTV PVR 150, which works well). As long as you only want one of these cards working at a time, I recommend using Ubuntu 6.06.

---

### Post by Erlander on 2007-02-19
> **jethro10 said:**
> Hi,
2. Freeview DTV cards. Most seem to be software based for mpeg encoding. Can anyone recomend a Hardware based card available in the UK?
Jeff
DVB-T is already encoded as broadcast.  All the tuner card does is to allow you to copy the stream to your pc.  This uses very little of your cpu's capacity.  ie about 3%.

To record more than 1 channel you need more than one tuner except when you are recording different streams from the one channel.

To view the Tv your graphics card should be in Windows terms capable of handling Direct X 9.  Then it does the decoding for viewing and not your cpu.  This is why I'm replacing the old TNT 2 I'm currently using. (see signature below)

Rob

---

### Post by jethro10 on 2007-02-20
> **scottishnarn said:**
> I use the Avermedia DVB-T 771 and it works great. It is however, a little hard to get a hold of now. BTW if it's digital TV then the card doesn't do any encoding at all. It's already in mpeg2 format, since it's a digital channel. It only works with free to view channels though, as do all current PC cards I think. To get top up tv you're going to need a seperate digi box and an encoder card (I use WinTV PVR 150, which works well). As long as you only want one of these cards working at a time, I recommend using Ubuntu 6.06.

Right, thats fine.
So to capture freeview this hardware/sofware encoding is meaningless as freeview being a digital mpeg stream is basically "passthrough" to the disk?
And to capture Sky uses an analogue card and this one need to be a hardware decoder to reduce CPU usage when recording/watching Sky?
So 2 Freeview and one Analogue card seems easily feasible.
thanks great

Jeff

---

### Post by jethro10 on 2007-02-20
> **Erlander said:**
> DVB-T is already encoded as broadcast.  All the tuner card does is to allow you to copy the stream to your pc.  This uses very little of your cpu's capacity.  ie about 3%.

To record more than 1 channel you need more than one tuner except when you are recording different streams from the one channel.

To view the Tv your graphics card should be in Windows terms capable of handling Direct X 9.  Then it does the decoding for viewing and not your cpu.  This is why I'm replacing the old TNT 2 I'm currently using. (see signature below)

Rob
Thanks, I've re-iterated most of this in my answer to another post. But as far as the graphics card goes. I believe the Built in one does Directx 9. But basically If I play an mpeg2 file and look at the cpu usage, if it's low, were fine then?

When looking around the net, there were lots of info that explained functions, but not how it impliments in real terms.
Thats where this thread is really helping.

Jeff

---

### Post by jethro10 on 2007-02-20
> **barney_1 said:**
> 

This is a subjective question.  I find that my MythTV box replaces my girlfriend's vcr (I really never recorded stuff on tape so the ability to record is a new feature for me).  I also find that it replaces my live tv watching (I don't use my digital cable box anymore, and will probably get rid of digital cable until the switch in 2009).  


My aim is to replace everything as well, so lets hope.

Ta
J

---

### Post by jethro10 on 2007-02-20
Another question I've just thought of,

Do you all just use the remote control, or have you a keyboard/mouse attached.

To use as a proper consumer electronics replacement, i'm guessing just a Remote?

Or a wireless keyboard/mouse ? Or is there a super media centre keyboard thingy.

Jeff

---

### Post by scottishnarn on 2007-02-20
I just use a normal keyboard with a very long extension, since I have never got my remote control working (however, when I get all the bugs out of my system then I'll try and get my remote working).

---

### Post by RizSilverthorn on 2007-02-24
I can't answer some of your questions, just the ones I have experience of.  Starting off with my current setup:
1 x AMD XP 2500+
2 x 256MB PC100
1 x 40GB IDE (for system) split up with /boot, /home, /usr all EXT3
1 x  250GB EXT3 for all recordings
2 x Hauppauge WinTV Nova-T 90002
1 x Geforce FX5200 128MB
Biostar Nforce2 Motherboard
17" CRT monitor & a standard TV

running Edgy Xubuntu for the lower requirement on the window manager (Openbox didn't work properly on dual  monitor for me).

Now your questions:
1. EXT3 will work, just need to tick the "slow delete" box in the Mythbackend configuration. If/when I replace the HDD I'll probably switch to XFS based on recommendations

2.The above are software based, but as Erlander has already pointed out, DVB-T is already encoded. Support is built in to Ubuntu kernel and the setup of the remote is simple (see this [useful site]("http://parker1.co.uk/mythtv_ubuntu.php") for a step-by-step guide).

3.I can record two channels and watch a previous recording or listen to music simultaneously with the above setup. I would recommend the Nova-T PCI cards everytime as they are the easiest to configure. Not sure what my TV is running at, I think it's 1024x768. 


3a. Technically no. In reality you can record the raw stream and use something like VLC to tune to different channels within the recorded stream but that is beyond Mythtv. So in reality and from a ease of use point of view, much easier to get two tuners.

4.Mythtv has it's own internal player, but it can use an external player for those files that it cannot handle natively. For TV recordings, watching TV and most video files I use the internal player, but I use xine for DVD playback and ripped .vob files, mplayer for quicktime .mov and totem for mkv! A bit of a mishmash but I find there are almost no files I cannot play.

5. Not needed that feature so I don't know if it's available. You can configure Mythtv to remember where you were in a recording and continue from there by default.

6. Yup, analogue input required for cable/satellite boxes. Nope, no external sound card required - it's treated exactly like an analogue TV signal.

7. No idea, only have 2.1 audio configured atm

8. Mythtv is as reliable as the hardware it is on. My box is now 199days, 13hours and some minutes from it's last boot. Once it is configured and working as you want it, don't touch it!

Windows Media Center Edition keyboards can work with Linux (and by extension Mythtv) except for the media functions currently. The MCE remotes are reportedly working, although I had so many problems with getting one working on a friends system I gave up and gave her the spare 45 button remote that came with my second Nova-T.

A wireless keyboard came come in handy, but is mostly redundant.

---

### Post by coxc24 on 2007-02-25
I have just finished my MythTV setup.

Intel Pentium 4 650 3.4Ghz Socket 775 800mhz 2mb Cache
Seagate 7200.10 320GB SATAII/300 8.5ms 7200RPM 16MB Cache
Asus Nvidia 7300GS 256MB PCI-E
Ebuyer 1GB DDR2 533MHz PC2-4200 240pin Extra Value Ram
MSI 945P Neo3-F i945P Socket 775 SATA 8-channel audio ATX

I have recorded 1 channel, watched another and had K9Copy encoding an XVID on the desktop at the same time and had no problems.

The TV card I have is the Hauppauge WinTV-Nova-t PCI Freeview Receiver (I am also in the UK). I bought them from Ebuyer and they were £20.28 (ex VAT). This does not have a hardware encoder so uses the processor and like I said, I have had no issues. I can't see you having problems with a 2.6 GHZ P4 if you want to watch/record multiple channels. The remote is also supported in the Kernel of Edgy 6.10 so you don't have to mess with Lirc. You will need to setup the buttons but the basic ones work from the start.

---

### Post by jethro10 on 2007-02-28
Cool,
much more confidence now.
Some of my add on bits are arriving daily so it may get re-built this weekend.

Already had a dry run with as much as I have and got myth installed ok..

Jeff

---

### Post by newlinux on 2007-03-29
> **jethro10 said:**
> Hi,

5. On my normal consumer DVD player, I can GOTO say, 48 minutes into the program. How does Myth do this. It seems all the current players use sliders to navigate a file.

I don't know if anyone answered this, but yes you can do this if you are using myth's internal player. You can just press 48i to go directly to the 48th minute of a program while viewing it.

> 
7. If I play a DVD or have an MPEG stream with Dolby 5.1 can you pass this through to the Soundblaster digital output to go to my surround system. Currently it seems to be downmixing to stereo-totem, gxine etc. Am I missing something.


Yes, you can pass dolby digital or DTS via SPDIF directly your receiver. There is a setting in mythfrontend that allows you to do this...

---

