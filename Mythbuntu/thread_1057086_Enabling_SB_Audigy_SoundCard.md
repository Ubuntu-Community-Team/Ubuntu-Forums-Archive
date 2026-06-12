---
title: "Enabling SB Audigy SoundCard"
date: 2009-02-01
forum: Mythbuntu
---

### Post by ptmuldoon on 2009-02-01
Well, I'm still brand new at mythbuntu, and starting to pull what what little hair I have out.

I just can't seem for the life of me to get sound to work.  I have an SB Audigy card in the machine, but only the onboard sound seems to work.  I've tried disabling the onboard sound in bios, hoping the sound would work, but nothing either on the front end ir with vlc and xine.

I think partly the issue could be by video card, and ATI HD 3600 card that has built in HDMI and 5.1 surround. (I have not enabled the ATI proprietary driver yet).

I'm been looking at the alsamixer settings, but my SB audigy card is not showing there.  

I'm very new at Mythbuntu and linux, but I think I should be able to get this sound working.

Any one have any suggestions or help they can offer?

Thanks
Pt

---

### Post by ptmuldoon on 2009-02-03
I hate to bump a post.  But does anyone have any suggestions in trying to get an SB Audigy Sound card to work?  I thinking I have a driver issue, but could it be a hardware conflict with the HD video card that includes HDMI out.  I'm currently not using the HDMI, but the vga out of the video card.

---

### Post by slick666 on 2009-02-06
I have it working but not under Mythtv.

i.e. I can open a movie under vlc with the myth frontend closed and it plays just awesome :). Unfortunately I can't get MPlayer under Mythtv to run it the same way.


Here's what I did to get it running
[LIST=1]
[*]Go to the console
[*]Type alsamixer
[*]make sure the iec958 in unmuted
[*]Make sure the next frew iec related level are set to about 80% (dbgain=-0.5)
[*]Hit the Tab key to go to input devices
[*]select the "Digital" entry and scoll down until it displays IEC958 o (IEC958 out)
[*]Then hit escape
[/LIST]

This should allow digital output to work but not analog. I hope this gets you up to speed and if anyone could offer some advice on how to configure myth it would be greatly appreciated.

---

### Post by slick666 on 2009-02-08
ok I got audio working but the audio I get is all I get is pulsing audio. It's almost like the digital signals are being interpreted literally and I get this really pulsing audio.

Has anyone else gotten this?

the system plays fine if I close mythfrontend and open up the disc manually with VLC. I'm wondering if I should switch from mplayer to VLC in the mythfrontend setup.

Any input welcome

---

### Post by itlarson on 2009-02-08
I'm no expert, but this sounds like something in the mythtv audio setup screen.  It's found at setup->setup->general then the third screen in.  My setup is:  

alsa:default
alsa:iec958{aeso 0x02}
stereo,                              passive
yes(ac3->spdif passthrough),         no
yes(dts->spdif passthrough),         no

The third setting needs to be "stereo", despite that I am using my optical spdif out for surround sound.  I am told this is a bug. The static sounds like what I would get from mythtv on the analog out of my old system- which I had hooked up for my amp's "second room" feature.  If I left the remote speakers on by mistake I would have surround in the living room and static in the kitchen.  
   Apologies in advance if all this is too obvious and you have already tried it.  The simple stuff is all I can really help with.

---

### Post by slick666 on 2009-02-08
I know I have successfully setup surround sound (5.1) in the past and the system correctly performs with VLC so I think your right that the problem is in the mythtv setup. I hope you are wrong about the bug because I had this operating perfectly fine on my previous mythbox. I'm still searching for a way.

ptmuldoon, have you been able to get spdif out on your system yet?

---

### Post by itlarson on 2009-02-08
The bug is only that it must be set to stereo- the spdif output will be surround.

---

### Post by slick666 on 2009-02-08
Wow, I got to check that out then.

---

### Post by slick666 on 2009-02-08
OMG your right. Thats the only combination I didn't try.

Just for those who might be following this all I have is 

alsa:default
alsa:iec958{aeso 0x02}
stereo, passive
yes(ac3->spdif passthrough)
yes(dts->spdif passthrough)

And internal sound disabled.

Wow, I would have never guessed that

---

### Post by itlarson on 2009-02-08
Finally!, I helped solve something!

---

### Post by ptmuldoon on 2009-02-15
Sorry for the late response, and thanks for the help everyone..

But... I still have no sound here.  I have ATI HD3600 video card that includes sound as well.

In alsamixer, I the SB Audigy card is card number 1.  So I need to use the -c 1 options to access it.   I've unmuted everything and set the sounds at 90% for all.

But again, I've got no sound either via the mythtv front end or in any application such as mplayer, VLC, etc.

I'm really at a loss for for the lack of sound.  I'm new to mythbuntu, but I would hope to at least get the sound working:(

---

### Post by slick666 on 2009-02-15
What type of output are you attempting to use?

Analog, TOSLINK, or spdif?

---

### Post by ptmuldoon on 2009-02-17
I actually don't understand the difference between TOSLink and spdiff.  But my speakers are connected to lineout 1 and 2 on the card.  So is that spdiff or analog?

I've currently got the pc dual booting, sound works fine in WinXP.  I think I'm close to having it working as I learn more.  I also learned via soundconf to be able to set the Audigy card as the default card now as well.

Just still need to figure out why I have no sound in Mythubuntu.  Currently still no sound via mplayer, VLC, or the front end.    

I return home Wednesday from a quick business trip, so hope to spend some more time on it than.

Thanks again for everyone's help.

---

### Post by slick666 on 2009-02-17
Well toslink is a digital output that transmits the digitally encoded audio (i.e. Doldy 5.1) optically from the source to the receiver. The receiver then decodes the audio and sends it to the speakers.
[http://en.wikipedia.org/wiki/TOSLINK]("http://en.wikipedia.org/wiki/TOSLINK")
Another cable that does the same think is the RCA spdif connector. I think we need to determine if you are transferring the data digitally or sending the analog signals out.

---

### Post by ptmuldoon on 2009-02-18
Ok, It turns out the card is using the Line 1 and 2 outs, which should be the Analog signal.   So now that I have that determined, I would hope that I can get the correct settings figured out to get some sound.

But shouldn't I be able to get sound via VLC or Mplayer even if the mythtv frontend is misconfigured?

---

### Post by slick666 on 2009-02-18
Well ultimately you should :p

what I would check first is your alsamixer settings. From the command line type **alsamixer**. 

You should be sure that you iec958 is **muted**. and also check to see that your audio levels are turned up enough. 

I would also check to be sure that the rest of your setup is configured correctly. A good way to test is to take a pair of headphones and plug them into the back of the PC and see if you hear sound. That way you can tell if your problem is in the computer or outside it.

I hope this gets you started let us know how it works out.

---

### Post by ptmuldoon on 2009-02-18
Success!!! 

Finally, the sound is working. After disbling iec958 as well as dual analog/digital in alsamixer, I've got sound.  I was then able to get the sound working on the Front End as well.  So, my sound issues are finally over.

Now, on to a video issue I'm having.  I'll start a new topic for that one after I do so searches to see if others have it.

Thanks again for everything.  Its really great to see a friendly, helpful community.

---

### Post by slick666 on 2009-02-18
Yay! now I solved something :)

---

