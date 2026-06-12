---
title: "ALC888 chipset: Only 2 channel AC3/DTS?"
date: 2009-02-13
forum: Mythbuntu
---

### Post by nicoloks on 2009-02-13
I'm sure I've read this issue somewhere else while looking for a solution for something else, but just can't seem to find it now. I have a board with the ALC888 codec onboard, and I am trying to use Mplayer to spit the digital audio out over the SPDIF connector so that my receiver can decode the AC3/DTS streams. 

This works as the DTS or Dolby Digital lights show up on the amp when playing appropriately encoded files, however I am only able to get 2 channels. Doesn't matter what program I use, I only have the front left and front right speakers.

Any suggestions?

---

### Post by nicoloks on 2009-02-14
Anyone?

---

### Post by konadad on 2009-02-14
Not sure if it is relevant since I am not using Mplayer, but I also have an ALC888 based board.  Am just bringing my system up, and got my PVR-150 working fine sending2 channels of audio (all I should have) to my receiver for analog cable tv.  When I hooked up my second capture card though for HDTV antenna I could not get any audio - just a clicking sound.  I was using "ALSA-Defaut" for the Audio Output Device in MythTV.  I tried all of the standard ALSA selections available as Audio Output Devices in MythTV - got nothing on any of them.

After struggling a bunch, I finally connected the dots and figured out what was wrong - I was trying to send all of my audio through the Analog side of the ALC888 instead of the digital.  The big revelation was that I could just type the info for an Audio Output Device into the MythTV setup - I typed in "ALSA:plughw:0,1" and it is working perfectly now.  It now passes perfect 6 channel AC3 to my receiver when watching HD, and still sends 2 channel audio over when watching SD broadcasts.

My guess is that you are somehow only configured to use the analog device half of the ALC888 and need to specify the digital portion of the device - this is what the 0,1 specifies in my line above (Card 0, Device 1).  Device 0 is the analog portion.

Best of luck.

---

### Post by nicoloks on 2009-02-14
Thanks for the reply. Have you made any customisations to get it working? Could you post your asound.conf/alsa-base ?

This is the output I get from running "aplay -L";

```
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output

```

When I run this;
```
speaker-test -Dplug:iec958 -c6 -l1 -twav
```

I only get output on the two front channels. By specifying iec958 I am definitely using the SPDIF connection, besides optical fibre is the only way my Mythbuntu box is connected to my receiver.

The fact I am getting DTS and AC3 pass through to work means the soundcard is working. The fact I am only getting two channels suggests to me I have config issue.

I did notice in the [mplayer section  of the Digital Pass Through]("http://alsa.opensrc.org/index.php/DigitalOut#mplayer") guide on the ALSA wiki site they say;
> Do not specify channels, because history dictates channels be set to 2, the default.
However, they don't give any explanation of why this is. Indecently I was using the analog output up until a week ago, and I am able to get all speakers working through it. It is just the digital output that is not working correctly.

---

### Post by konadad on 2009-02-14
I was getting the same thing running the exact same speaker test command line that you quoted - only 2 speakers.  Can't remember the site that I saw it at (might have been the mythtv wiki), but somewhere I was reading that this is normal for speakertest.

I am not an expert by any means, but even though you are using the SPDIF hardware I don't think that this means that you are necessarily passing the original digital signal - internally your application/soundcard could still be doing the AC3 decoding and just sending out 2 channel PCM over the SPDIF to your receiver.  I was clearly getting the same thing with mine until I found the way to specify using the digital device.  I even tried specifying both ALSA:iec958 and ALSA:SPDIF in mythTV prior to that and they got me nothing different.

I saw almost identical output running aplay -L.  Only difference on mine is addition of an HDMI entry for digital because my mobo has that.  If you try aplay -l you will probably get something that tells you that analog is device 0 and digital is device 1.  You need to find some way in mplayer to specify the device differently.  Wish I could help you there.

I did nothing different with my asound.conf - can't get to my mythbox right now so can't give you the config, but I don't think that is your answer.  Will try to get it tomorrow though just to give you the comparison point though.  Good luck again.

---

### Post by nicoloks on 2009-02-15
Thanks konadad, I appreciate any help you can give. Looking forward to seeing what your mplayer command line swtiches are.

---

### Post by konadad on 2009-02-15
I can't find an asound.conf file in /etc where everything says it should be - if you have another idea where it might be let me know and I will post it.  I have alsa-base, but based on the revision date it is just whatever came with the 8.10 distribution.  I can't figure out how to attach it here (got an error), so will paste in below.  I never got far enough in my wiki reading and experimentation to try any changes to these two files.

I would still be thinking it is something with not having the device selected - did you see and do the command line listed in [this section]("http://alsa.opensrc.org/index.php/DigitalOut#Use_Your_Device") of the Digital Out setup in the wiki pertaining to mplayer?

I also opened up mplayer on my machine, and looking in Preferences - Audio I was able to select ALSA then select "configure driver".  This gave me a box with a drop down menu for Device - in this drop down you can pick hw=0.1 or even type in plughw=0.1 both of which should do the same thing for you in mplayer as what I did typing similar into Myth's audio preferences for device.  I don't have a video file with AC3 to try it in mplayer, but based on the similarity I think that this is where you need to be.

---

### Post by konadad on 2009-02-15
forgot to post the alsa-base, here it is:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

```

---

### Post by nicoloks on 2009-02-15
Sounds like our config files are now identical, yet I am still only getting 2 channel DTS/AC3 streams. I tried specifying the "alsa:device=hw=0.1" and "alsa:device=plughw=0.1" in the mplayer command line, however doing this resulted in no sound and there was no DTS or Dolby Digital lights on my reciever which means it wasn't getting anything from the PC. Card 0, device 1 is defintely my SPDIF output too, I double checked this with "aplay -l".

I'm not so sure this is a soundcard issue now, but rather an ALSA issue. I've just built a HTPC for a mate on Mythbuntu 8.10 that uses the VIA 	
VT1708B HD audio. I output to HDMI rather than SPDIF, however I notice that Mplayer is still reporting 2 channel audio streams rather than 6. I have triple checked with mediainfo that the movie I am playing actually does have 6 channel DTS audio. One thing I did notice is that I am actually getting 2.1 sound (fronts + LFE). I also tested mythdvd with my monsters Inc. DVD which has a THX test on it that outputs static to each channel (much like speaker-test), however it also only uses 2.1 rather than 5.1. Playing that same DVD though my Pioneer DVD player is definately 5.1.

Maybe time to hit the ALSA mailing lists as I can't seem to find anything about this anywhere.

---

### Post by HyRax on 2009-06-03
I know this is an old thread, but I thought I'd quickly add my experiences to this.

I just recently setup a MythTV box for my folks based on Ubuntu Jaunty 9.04 using a Gigabyte S-Series GA-EG41M-S2H/S2 motherboard (built-in SPDIF out x2, SPDIF in x1, HDMI out x1) which also uses the ALC888 audio chipset. Ubuntu Jaunty itself had no issues with the hardware, correctly identifying that it had SPDIF on card 0, device 1 and HDMI on card 0, device 3 (according to APlay's "-L" parameter output).

Like everyone else, I had to un-mute the IEC958. This is just a checkbox, but it did NOT appear in the Volume Control GUI. I had to drop into a terminal, run up "alsamixer" to bring up the terminal version of it, scroll far right where I found three IEC958 entries, two enabled and one muted. As soon as I unmuted the third IEC958 entry (called "IEC958 1"), the laser in the toslink cable suddenly lit up. Hooked it up to the amp and it immediately registered a connection.

I found that the Speaker Test app would only allow me to play two channels no matter what, however within MythTV after specifying "ALSA:iec958" as the default audio device and enabling the two "AC3/DTS pass-through" checkboxes, true 5.1 played without an issue from the system. Oddly, however, all audio stops if I specify the "maximum sound channels" to be "5.1" instead of stereo, so I left it as "stereo". The amp still confirms a 5.1 AC3 or DTS input however, and decodes accordingly.

With the MythVideo add-in, to get passthrough working there, I had to modify the MPlayer parameters to include "-ac hwac3 -ao alsa:device=iec958" and my DVD rips with original DD/DTS audio tracks played like a charm without being dumbed down to 2 channels.

I found [this page](http://alsa.opensrc.org/index.php/DigitalOut) on the ALSA wiki most helpful in this task.

Not quite as painful as I thought it would be!

---

### Post by jyavenard on 2009-06-03
Here is what I use on a board with a ALC885

~/.mplayer/config:
# Write your default config options here!
ao=alsa:device=spdif
ac=hwac3,hwdts,

This will make mplayer use AC3/DTS passthrough if possible.

On a board with a ALC883 and HDMI port, I use in ~/.mplayer/config:
ao=alsa:device=hdmi
ac=hwac3,hwdts,

---

