---
title: "HDMI Passthrough issue?"
date: 2012-01-16
forum: Multimedia Software
---

### Post by gdselzer on 2012-01-16
I have lubuntu 11.10 on a system based on the ASROCK E350M1.  The computer is connected to a Yamaha receiver via HDMI.  The receiver is then connected to my Samsung HDTV via HDMI.  Catalyst 11.8 is installed.

If I turn on the TV, then turn on the receiver, everything works as expected.  If I turn on the receiver then the TV, I get no sound.  If I have sound (playing music, for example) and turn off the TV, the sound goes away.  If I then turn off the receiver, wait 10 seconds, then turn just the receiver back on, the sound is there.

I assume this has something to do with the way the drivers are reacting to the HDMI hotplug events, but I have no idea how to correct it.  Does this theory seem right?  I would like for the sound to continue even when the TV is turned off.  Can anyone provide some help?

---

### Post by gdselzer on 2012-02-17
bump

---

### Post by depuyc on 2012-03-30
I have the exact same setup and same problem.  On my older Foxconn motherboard running Ubuntu 11.04 this did not occur.  If there is a fix I would love to hear it as I control my music through an XBMC remote app on the ipad so do not want the TV on.

---

### Post by marinara on 2012-03-31
buy a different video card?

---

### Post by BicyclerBoy on 2012-03-31
If you study your AVR HT amp user manual..hopefully you will find a section on ELD/EDID management.

You should be able to set ELD:
- cached
- TV pass thru'
- AVR ELD only.

AFAIK
The HT amp has to modify the display ELD to add its own capabilities.
The amp has higher capability than display.

Cached: means the amp stores the ELD from TV when it is off so audio continues without TV turned on.
AVR ELD only: you get full amp capability without display audio limits; audio setup..

I think that with HDMI amp & display there should be 2 ELD sections in the 
EDID data returned to alsa.
Alsa 1.0.24 & later use ELD to limit/setup audio codecs available.
I think you can trick alsa with cached ELD from file just like EDID from file for video display problems.

---

### Post by depuyc on 2012-04-05
I really appreciate the information you gave.  I sat down last night and tried to work it out and I do not have options for that on my receiver but I did find some very interesting things that I can live with.  I always knew that turning off my TV usually caused the sound to cut out.  Turning the TV back on would restore video fine but still no sound until I power cycled the receiver. 

I found if I power cycle the receiver after turning the TV off the sound comes back and turning on the TV again it stays.  Yay I thought I was happy.  Then I realized that when the TV is on, changes to the audio settings on the tv change the sound coming out of the receiver.  Subtle changes but still actually sounds better.  Lastly I realized that turning up the speakers on the tv to only 3 makes an even better sound.  

Hope this can help anyone else work around this problem in their setup.

---

### Post by gdselzer on 2012-04-22
I am unable to find a way to change the EDID options on my AV receiver (Yamaha RX-V371.)  The issue definitely appears to be related to different EDIDs being pass through to the computer and the system getting confused.

I used 
> sudo get-edid|parse-edid
to get the EDID info coming through to the computer.

When the Yamaha AND the TV are on, the above command gives me information on the Samsung TV.  When I turn the TV off, it provides me with the EDID info on the Yamaha receiver.  If i turn the TV back on, EDID info goes back to Samsung.

So the issue seems to be related to the changing EDID.  Can anyone help me to figure out how to either 1) stop the EDID from changing or 2) tell the HTPC to ignore the changing EDID?

Thanks

---

### Post by BicyclerBoy on 2012-04-22
This is guessing..
I think alsa 1.0.25 has better ELD support.
When you have HDMI amp & TV connected I think you have (2) ELDs files:  /proc/asound/cardx/eld#y.0 & eld#y1.1 where x is the card number & y =[0, 1]

I believe part of the problem could be that there are multiple valid ELD arrangements & not all cases were handled correctly.
Shame HT amps do not handle this better..

I would guess that this issue will get worked out over coming months.
MythTV developers are planning to directly utilise the ELD data in the audio control/setup.

The users of nVidia video cards can use an EDID/ELD from file.
The get-edid program only works on 32bit?
It has never worked for me but the nVidia EDID tool does work.

Does your TV have a video only mode ?
Note: alsa 1.0.25 user libraries can be installed on non-1.0.25 kernel module.
alsa 1.0.25 archive is broken need to use git.

[http://www.mythtv.org/wiki/User_Manual:HDAudioPassthrough#Checking_your_TV_.2F_Amplifier_.2F_Audio_Processor_capabilities](http://www.mythtv.org/wiki/User_Manual:HDAudioPassthrough#Checking_your_TV_.2F_Amplifier_.2F_Audio_Processor_capabilities)

Good reading for ATI?AMD users:
[http://www.avsforum.com/avs-vb/showthread.php?t=1227161](http://www.avsforum.com/avs-vb/showthread.php?t=1227161)

Possible ways to upgrade alsa:
This ppa has easy to use snd-hda kernel module package using dkms:
[https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily](https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily)

or Replace whole alsa kernel modules (& user-space for precise only).
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

---

### Post by gdselzer on 2012-04-23
Thanks for all the info.  I'm starting to get a sense of how this all fits together, but I think I'm still missing a few pieces.

I am only able to see one ELD file, /proc/asound/card0/eld#0.0, not two.  If only one ELD exists, will upgrading ALSA make a difference or is there a different problem going on?

Regarding my TV and video-only mode, it allows me to choose the source (HDMI, VGA, Antenna, etc.)  Is that what you are referring to?

---

### Post by BicyclerBoy on 2012-04-25
I have not come across any TVs with video only mode. Just wishful thinking.

A VGA connection to TV or dual HDMI connections (separate video & audio connections) could work.

Some video card/drivers do not like to output audio over HDMI with no video..
The nVidia X driver must be active server screen to get HDMI audio.
So an audio only HDMI link requires a dummy (forced) screen output.

I don't know what AMD does..

Pity there is not a option keyword like "AudioOnlyLink".

Can you capture your ELD files for each of the (2) situations..
Maybe you can just overwrite the eld file after the hot plug event with a cached copy..

---

### Post by depuyc on 2012-05-14
Cannot say I understand this but is this what you wanted?  Note my system is exactly like GDSELZER except mine is an RX-V367 Receiver.  I pulled the /proc/asound/card0/eld#0.0 and output of get-edid | parse-edid at each of the following steps;
1, TV on and sound functioning.
2, TV off and sound has gone silent.
3, TV off and sound recovered by power cycling HT
4, TV back on and sound silent

> ##### TV:                       On
##### HT Audio decoder status:  PCM
##### Audio:                    Working

# cat /proc/asound/card0/eld#0.0

monitor_present		1
eld_valid		1
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0

# get-edid | parse-edid

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "SAMSUNG"
	VendorName "SAM"
	ModelName "SAMSUNG"
	# Block type: 2:0 3:fd
	HorizSync 26-81
	VertRefresh 24-75
	# Max dot clock (video bandwidth) 230 MHz
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1920x1080"	# vfreq 60.000Hz, hfreq 67.500kHz
		DotClock	148.500000
		HTimings	1920 2008 2052 2200
		VTimings	1080 1084 1089 1125
		Flags	"+HSync" "+VSync"
	EndMode
	Mode 	"1280x720"	# vfreq 60.000Hz, hfreq 45.000kHz
		DotClock	74.250000
		HTimings	1280 1390 1430 1650
		VTimings	720 725 730 750
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
EndSection


##### TV:                       Off
##### HT Audio decoder status:  Decoder Off
##### Audio:                    Silent

# cat /proc/asound/card0/eld#0.0

monitor_present		0
eld_valid		0

# get-edid | parse-edid

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fc
	Identifier "RX-V367"
	VendorName "YMH"
	ModelName "RX-V367"
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
	HorizSync 15-91
	VertRefresh 23-121
	# Max dot clock (video bandwidth) 150 MHz
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1920x540"	# vfreq 60.053Hz, hfreq 33.750kHz
		DotClock	74.250000
		HTimings	1920 2008 2052 2200
		VTimings	540 542 547 562
		Flags	"Interlace" "+HSync" "+VSync"
	EndMode
	Mode 	"1920x540"	# vfreq 50.044Hz, hfreq 28.125kHz
		DotClock	74.250000
		HTimings	1920 1968 2012 2640
		VTimings	540 542 547 562
		Flags	"Interlace" "+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
EndSection



##### TV:                       Off
##### HT Audio decoder status:  PCM
##### Audio:                    Working

# cat /proc/asound/card0/eld#0.0

monitor_present		1
eld_valid		1
monitor_name		
connection_type		HDMI
eld_version		[0x0] reserved
edid_version		[0x0] no CEA EDID Timing Extension block present
manufacture_id		0x0
product_id		0x0
port_id			0x0
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x0]
sad_count		0

# get-edid | parse-edid

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fc
	Identifier "RX-V367"
	VendorName "YMH"
	ModelName "RX-V367"
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
	HorizSync 15-91
	VertRefresh 23-121
	# Max dot clock (video bandwidth) 150 MHz
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1920x540"	# vfreq 60.053Hz, hfreq 33.750kHz
		DotClock	74.250000
		HTimings	1920 2008 2052 2200
		VTimings	540 542 547 562
		Flags	"Interlace" "+HSync" "+VSync"
	EndMode
	Mode 	"1920x540"	# vfreq 50.044Hz, hfreq 28.125kHz
		DotClock	74.250000
		HTimings	1920 1968 2012 2640
		VTimings	540 542 547 562
		Flags	"Interlace" "+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
EndSection



##### TV:                       On
##### HT Audio decoder status:  Decoder Off
##### Audio:                    Silent

# cat /proc/asound/card0/eld#0.0

monitor_present		0
eld_valid		0

# get-edid | parse-edid

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "SAMSUNG"
	VendorName "SAM"
	ModelName "SAMSUNG"
	# Block type: 2:0 3:fd
	HorizSync 26-81
	VertRefresh 24-75
	# Max dot clock (video bandwidth) 230 MHz
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1920x1080"	# vfreq 60.000Hz, hfreq 67.500kHz
		DotClock	148.500000
		HTimings	1920 2008 2052 2200
		VTimings	1080 1084 1089 1125
		Flags	"+HSync" "+VSync"
	EndMode
	Mode 	"1280x720"	# vfreq 60.000Hz, hfreq 45.000kHz
		DotClock	74.250000
		HTimings	1280 1390 1430 1650
		VTimings	720 725 730 750
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
EndSection

---

### Post by BicyclerBoy on 2012-05-14
Can you post your
aplay -l
& the version reported by speaker-test

I'm not sure that ELD is the correct one for the HDMI connection..
The ELD file does not have valid data for any of your test conditions..

When the ELD file is empty alsa makes some assumptions (I think)..

---

### Post by depuyc on 2012-05-16
Here is the output when the sound is functioning properly.

> ubiserver uboolean # aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubiserver uboolean # speaker-test

speaker-test 1.0.24.2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Channels count (1) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument


If I turn the TV off, ie break the sound, this is what the same commands report.

> ubiserver uboolean # aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
ubiserver uboolean # speaker-test

speaker-test 1.0.24.2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy


In my previous post I do see where the system is reporting the correct device being attached, yamaha vs samsung, but when the status changes it goes to saying nothing is there.  I wish there was a way to prevent the TV from sending it's data through the receiver or to hard code the system to only use the yamaha receiver.

---

### Post by BicyclerBoy on 2012-05-16
Sorry, You did get the right ELD file..& valid ELD is reported..
> 
##### TV: Off
##### HT Audio decoder status: PCM
##### Audio: Working

# cat /proc/asound/card0/eld#0.0

monitor_present 1
eld_valid 1
monitor_name
connection_type HDMI
eld_version [0x0] reserved
edid_version [0x0] no CEA EDID Timing Extension block present
manufacture_id 0x0
product_id 0x0
port_id 0x0
support_hdcp 0
support_ai 0
audio_sync_delay 0
speakers [0x0]
sad_count 0


There is no good audio data in there..
dmseg | grep hda

Perhaps alsa is misinterpreting the ELD data..there are multiple (2?) possible formats.
I would try to upgrade alsa to 1.0.25, kernel & user-space.

speaker-test -c 2 -r 48000 -l 2 -D hw:0,3

---

