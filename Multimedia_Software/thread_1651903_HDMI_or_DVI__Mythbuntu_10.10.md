---
title: "HDMI or DVI  Mythbuntu 10.10"
date: 2010-12-23
forum: Multimedia Software
---

### Post by mtbdrew on 2010-12-23
For the love of all things that are holy, what magic spells, animal sacrifices or, which kidney do I have to sell to get audio to my TV through the HDMI cable?

I have an ECS gf7100pvt-m3 that has the Nvidia MCP73 chipset that supports HDMI out. Unfortunately the MB only has a DVI connector which from what I have read is supposed to cross wire the audio to the correct pins on the HDMI (have a ticket in with ECS to see if like ATI there is a special adapter).
I have tried every thing but only Analog audio is working.
I've tried listed on these links to no avail:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[http://ubuntuforums.org/showthread.php?t=1565479](http://ubuntuforums.org/showthread.php?t=1565479)


[http://art.ubuntuforums.org/showthread.php?t=1620198](http://art.ubuntuforums.org/showthread.php?t=1620198)


[http://ubuntuforums.org/showthread.php?t=789578&highlight=howto+pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=howto+pulseaudio)


[http://forum.notebookreview.com/linux-compatibility-software/441755-ubuntu-9-10-hdmi-audio-out.html](http://forum.notebookreview.com/linux-compatibility-software/441755-ubuntu-9-10-hdmi-audio-out.html)


[http://www.gossamer-threads.com/lists/mythtv/users/456260](http://www.gossamer-threads.com/lists/mythtv/users/456260)


[http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI](http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI)
[http://ubuntuforums.org/showpost.php?p=9988441&postcount=18](http://ubuntuforums.org/showpost.php?p=9988441&postcount=18)
[http://ubuntuforums.org/archive/index.php/t-1617334.html](http://ubuntuforums.org/archive/index.php/t-1617334.html)
[http://ubuntuforums.org/showthread.php?t=666954](http://ubuntuforums.org/showthread.php?t=666954)
[http://ubuntuforums.org/showthread.php?t=877811](http://ubuntuforums.org/showthread.php?t=877811)
[http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html](http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html)

The only error is the at the Aumix isn't touching....
I can select HDMI or IEC958 1 etc etc and the audio mixer shows full blue as if it should be working but I can't get VLC or MythTV to output sound.

Any help would be appreciate
Thanks
Andrew

---

### Post by mtbdrew on 2010-12-26
Bump, anyone?

---

### Post by mtbdrew on 2010-12-29
?? Anyone out there have any knowledge on this subject?

---

### Post by AKADAP on 2010-12-30
DVI does not support audio.

HDMI uses the same signaling as DVI and includes audio in the digital data.

Some DVI devices can use HDMI audio signaling.

If you are lucky, your device might support audio over DVI. If it does, it will show up in "Sound Preferences"

There are different levels of support for audio on HDMI. Some only support stereo (this allows DTS and dolby digital 5.1 audio), others support multi-channel PCM.

Read the data on your device carefully to see what it supports.

---

### Post by brian70809 on 2010-12-31
I have had problems with Audio output in Nvidia chipset video as well. It cannot do a straight passthru. Make sure you are not trying to do that. It has to be AC3.. If you try DTS you will hear nothing.
 
I also question the sound output on a DVI port, if they claim there is a workaround I don't know if it works in Ubuntu.
 
Good Luck!

---

### Post by mtbdrew on 2011-01-01
Thanks for the replies. The MB has on board HDMI Audio and I have this showing up in Ubuntu and can select it either through Alsa or Pulse controllers. Changing VLC audio to this device shows audio movement on the sound bar but nothing comes out the speakers. I put a second drive in and booted WinXP but no joy here either though I do get a message "unknown pin configuration" in the IDT sound controller. I finally moved another machine into the living room and hooked it to the TV to test the DVI to HDMI adapter, cable, TV settings etc. This system is using a Nvidia 9600 video card with spdif pass through and sound worked perfectly. 
So either the ECS MB is not using standard pinout for audio through DVI or maybe the board is just bad?

---

### Post by mtbdrew on 2011-01-06
BTW, I solved this by buying a $33 EVGA Geforce 210. Audio over HDMI worked with no issues or reloads needed. Also don't need the DVI to HDMI adapter either as the video card comes with HDMI standard and its own sound.

---

### Post by BicyclerBoy on 2011-01-06
Mate you should have got the GT220 as a minimum...

---

### Post by Rumpty on 2011-01-06
I have a G210 card on my HTPC too. What am I missing that the G220 provides?

---

### Post by BicyclerBoy on 2011-01-06
GT210 is to slow for advanced (x2) de-interlacing methods 

and (I think) HQ scaling not possible.


For the price difference (to GT220) of couple dollars, the GT210 is not worth considering.

Same argument leads to GT430 as recommended.

---

### Post by Rumpty on 2011-01-06
Ok, thanks for the comments. Don't think I need the de-interlacing function. Also it is not required to produce 1080 here, only 720p.

The 210 I have is fanless, which was what I wanted. Is the 220 available fanless.

I suppose it's a matter of where does one stop?

---

### Post by BicyclerBoy on 2011-01-06
All 1080 material over dvb-t & dvb-s is interlaced.

Almost all DVD material is interlaced & is best GPU HQ scaled before feed to HD display.

The advanced de-interlacing methods are motion adaptive & vector adaptive.

If you have CRT or plasma or fast LCD & like moving images then there's no argument.

If your GPU is working right you should have great difficulty determining the material is interlaced..

---

### Post by Rumpty on 2011-01-06
BicyclerBoy, I am probably watching video in blissful ignorance! Can you point me to a downloadable interlaced file to play with?

---

### Post by mtbdrew on 2011-01-06
> **BicyclerBoy said:**
> All 1080 material over dvb-t & dvb-s is interlaced.

Almost all DVD material is interlaced & is best GPU HQ scaled before feed to HD display.

The advanced de-interlacing methods are motion adaptive & vector adaptive.

If you have CRT or plasma or fast LCD & like moving images then there's no argument.

If your GPU is working right you should have great difficulty determining the material is interlaced..

All the GT220 where twice the price. 
We are not talking gaming but hardware supported video playback as this is only for MythTV. Beside TV shows and Movies are only 24 - 29fps even with 60Hz sudo 120Hz Samsung I have so this card can handle the motion with no issues. Also could find anything that stated the GT220 had built in audio which the 210 does. Then there is power consumption and heat factors. Also it was leaps above the on board 7100.

So does the GT220 have sound built in or only pass through?

---

### Post by BicyclerBoy on 2011-01-07
@Rumpty
Anything from FreeviewHD dvb-t ONE TV2  TV3

Any DVD ...

The GT210 is not capable of the same PQ as the GT220.

The GT430 is better again due to power/size/later GPU.
The GT220 & 430 support hdmi audio.
The GT430 supports HD audio over hdmi & it is supported now in 3rd party MythTV 0.24 ppa.

Not sure about the GT220 &HD audio
Don't know about GT210 & it is not relevant to me because the card's video performance.

@mtbdrew
.I don't think you understand how the current gen hdmi audio works/

---

### Post by mtbdrew on 2011-01-07
> **BicyclerBoy said:**
> @Rumpty
Anything from FreeviewHD dvb-t ONE TV2  TV3

Any DVD ...

The GT210 is not capable of the same PQ as the GT220.

The GT430 is better again due to power/size/later GPU.
The GT220 & 430 support hdmi audio.
The GT430 supports HD audio over hdmi & it is supported now in 3rd party MythTV 0.24 ppa.

Not sure about the GT220 &HD audio
Don't know about GT210 & it is not relevant to me because the card's video performance.

@mtbdrew
.I don't think you understand how the current gen hdmi audio works/

Trust me I've done enough troubleshooting trying to get the audio over HDMI to understand HDMI audio.
Basically you have two types of support on video cards, Pass -through were you have to connect the spdif from you sound card in to the video card (if this is provided by the vendor) 
The other method is the way ATI and some of Nvidia's line up does it which is by providing there own sound hardware on the video car itself. The 210 has four separate devices according to aplay -l and is supported under latest Alsa that comes with 10.10. After all the headaches I had with the ECS chipset I was looking for ease of use that's why I got the 210.
However after reading your comments about de-interlacing and then reading up on the different methods I would have to agree the 210 is not up to the challenge. I also wonder if this may be why my HDTV MPEG dumps don't look as clear as the original broadcast even though I turned off trans-code. 
So took your advice and returned the card, found a PNY GT 430 for $60 after rebate. Hopefully the audio will not give me any issues.

---

### Post by BicyclerBoy on 2011-01-07
I assumed wrong.

You certainly do understand hdmi audio issues.
The pass thru' method is no good for HD audio as S/PDIF only supports 5.1 matrix encoded AC3 DTS & 2 ch PCM 96KHz max.
The current gen video cards do not use the S/PDIF method.

I believe you need the latest nvidia 260.29.19 driver & alsa 1.0.23 for hdmi audio with the GT430.
Alsa 1.0.23 could be in your *buntu kernel or in a backport/update.

Support for HD audio in MythTV 0.24 is available in JYA's mythtv ppa.

To enable the de-interlace features use vdpau profile with advanced 2x de-interlacer.
Can add filters: vdpauhqscaling, vdpausharpen=[-1:1] vdpaudenoise=[-1:1]
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

vdpausharpen=0.3 & vdpauscaling is very good for DVDs & other SD material.

---

### Post by mtbdrew on 2011-01-07
> **BicyclerBoy said:**
> I assumed wrong.

You certainly do understand hdmi audio issues.
The pass thru' method is no good for HD audio as S/PDIF only supports 5.1 matrix encoded AC3 DTS & 2 ch PCM 96KHz max.
The current gen video cards do not use the S/PDIF method.

I believe you need the latest nvidia 260.29.19 driver & alsa 1.0.23 for hdmi audio with the GT430.
Alsa 1.0.23 could be in your *buntu kernel or in a backport/update.

Support for HD audio in MythTV 0.24 is available in JYA's mythtv ppa.

To enable the de-interlace features use vdpau profile with advanced 2x de-interlacer.
Can add filters: vdpauhqscaling, vdpausharpen=[-1:1] vdpaudenoise=[-1:1]
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

vdpausharpen=0.3 & vdpauscaling is very good for DVDs & other SD material.

Thank you for the correction and even more so for the information on deinterlacing as I was getting reading to ask what method you recommended. 

My system is already running Alsa 1.0.23 (Ubuntu 10.10 with Myth and XBMC added after). 

In Myth I had already switched to the VDPAU High but not worked with the deinterlacing at all yet.

BTW, for anyone looking at the Geforce 210, I've done some further checking at there seems to be some confusion on whether this unit actually has hardware support for HD (does not say this on Nvidia's spec page). Where as the 430 clearly states HD and BluRay hardware support.

Couple of good links on deinterlacing

[http://www.mythtv.org/docs/mythtv-HOWTO-10.html](http://www.mythtv.org/docs/mythtv-HOWTO-10.html)

[http://www.100fps.com/](http://www.100fps.com/)          (little out of date but gives some very good information on the different types)

---

### Post by BicyclerBoy on 2011-01-07
Here are some test patterns for those so inclined..

[http://www.avsforum.com/avs-vb/showthread.php?t=1157287](http://www.avsforum.com/avs-vb/showthread.php?t=1157287)

The files are zipped.

---

### Post by mtbdrew on 2011-01-07
> **BicyclerBoy said:**
> Here are some test patterns for those so inclined..

[http://www.avsforum.com/avs-vb/showthread.php?t=1157287](http://www.avsforum.com/avs-vb/showthread.php?t=1157287)

The files are zipped.

Thanks again.

Well the card went in and audio works. This card gives the same 4 audio devices aplay -l sure wish I could get a good technical breakdown of what each of these support? Have a ticket in with Nvidia but no answer so far.
Found one sight that gave a general breakdown for the 210 but it didn't match with the EVGA 210 512MB.

---

### Post by BicyclerBoy on 2011-01-07
Not sure nvidia creates the alsa audio devices..
I think the alsa module does this.

Search the mythtv forums about GT220 240 430 hdmi audio & you're sure to find an answer.
I have the hdmi audio devices but never used them.

---

### Post by mtbdrew on 2011-01-07
> **BicyclerBoy said:**
> Not sure nvidia creates the alsa audio devices..
I think the alsa module does this.

Search the mythtv forums about GT220 240 430 hdmi audio & you're sure to find an answer.
I have the hdmi audio devices but never used them.

Going to have to as I spoke too soon, sound in desktop but not in MythTV.

---

### Post by BicyclerBoy on 2011-01-07
If your MythTV version is 0.24...
Rescan the audio devices..
It generates a list of all possible valid devices.
It also parses your (custom) device entry

It provides a multi-channel speaker test as well ..

---

### Post by efflandt on 2011-01-08
I have a GT 430, but don't have MythTV, so not sure what is specific to that.  But for regular Ubuntu Maverick or Natty development, all I had to do to be able to select HDMI stereo with Sound Preferences to work with any audio was add a line after the commented out alsa-sink line in **/etc/pulse/default.pa** which was the card,device that worked with **aplay -D plughw:1,9 /usr/share/sounds/alsa/Front_Center.wav** after unmuting the HDA NVidia devices in **alsamixer**

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```However, the Output device in Sound Preferences for HDMI sound is "HDA NVidia", not the one that says HDMI.  Not sure if a different setup or device on the card is used for surround sound.

---

### Post by BicyclerBoy on 2011-01-08
From the horse's mouth so to speak..

[http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7)

---

### Post by mtbdrew on 2011-01-08
> **efflandt said:**
> I have a GT 430, but don't have MythTV, so not sure what is specific to that.  But for regular Ubuntu Maverick or Natty development, all I had to do to be able to select HDMI stereo with Sound Preferences to work with any audio was add a line after the commented out alsa-sink line in **/etc/pulse/default.pa** which was the card,device that worked with **aplay -D plughw:1,9 /usr/share/sounds/alsa/Front_Center.wav** after unmuting the HDA NVidia devices in **alsamixer**

```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```However, the Output device in Sound Preferences for HDMI sound is "HDA NVidia", not the one that says HDMI.  Not sure if a different setup or device on the card is used for surround sound.

I didn't have to comment out the module-alsa-sink. For me the device is 0,9 as the others don't put out any sound unless you active the 0,9 device.
Strange how these are so different from the 210 I had when the aplay -l gives the exact same output for both.
For MythTV have to add the plughw:0,9 as the audio device. For XBMC select HDMI at the top and the Nvidia HDA HDMI in the bottom two selections of the system page under audio.

---

