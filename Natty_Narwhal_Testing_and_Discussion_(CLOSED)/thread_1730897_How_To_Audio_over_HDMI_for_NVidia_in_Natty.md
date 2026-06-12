---
title: "How To: Audio over HDMI for NVidia in Natty"
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Hedgehog1 on 2011-04-16
This post has been moved to here:

[http://ubuntuforums.org/showthread.php?t=1741294]("http://ubuntuforums.org/showthread.php?t=1741294")

***The Hedge***

:KS

---

### Post by 23dornot23d on 2011-04-16
Looks good - but I do not get those options ..... ](*,)

My guess is I do not have the right hardware to do this ...... have a hdmi out ... and connected to a 32 inch tv .....

Here are my settings does anybody know if I can do the above ?

```

keith@keith-Aspire-7730ZG:~$ grep ^Codec /proc/asound/card?/codec*
/proc/asound/card0/codec#0:Codec: Realtek ALC888
/proc/asound/card0/codec#1:Codec: LSI ID 1040
/proc/asound/card0/codec#3:Codec: Nvidia MCP77/78 HDMI
keith@keith-Aspire-7730ZG:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0500000 irq 46
keith@keith-Aspire-7730ZG:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
keith@keith-Aspire-7730ZG:~$ lsmod | grep snd
snd_hda_codec_hdmi     28272  1 
snd_hda_codec_realtek   257696  1 
snd_hda_intel          33132  4 
snd_hda_codec          93180  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13413  1 snd_hda_codec
snd_pcm                81557  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13170  0 
snd_rawmidi            25327  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51702  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29140  2 snd_pcm,snd_seq
snd_seq_device         14160  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    56136  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
keith@keith-Aspire-7730ZG:~$ 


```Laptop is a [Acer Aspire 7730zg]("http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire7730ZG/Aspire7730ZGsp2.shtml")
I think mine is intel - not sure why it mentions nvidia .....

Sound Subsystem Dolby®-optimized surround sound system with two built-in stereo speakers and one subwoofer supporting low-frequency effects.
Optimized  2nd Generation Dolby Home Theater® audio enhancement, featuring Dolby®  Digital, Dolby® Digital Live, Dolby® Pro Logic® IIx, Dolby® Headphone,  Dolby® Natural Bass, Dolby® Sound Space Expander technologies.
True 5.1-channel surround sound output.
High-definition audio support.
S/PDIF (Sony/Philips Digital Interface) support for digital speakers.
MS-Sound compatible.
Built-in microphone .
HDMI out

---

### Post by lucazade on 2011-04-16
Nice how-to.. thanks for sharing Hedgehog1
As soon as I buy a new hdmi cable (I have a crap one that doesn't work good, I'm stick with dvi atm) I'll try audio over hdmi.

---

### Post by Hedgehog1 on 2011-04-16
[lucazade]("http://ubuntuforums.org/member.php?u=242850") - I don't know if they are as cheap for you in Italy, but these HDMI cables work nicely and are inexpensive:

 [http://www.amazon.com/AmazonBasics-High-Speed-Cable-Ethernet/dp/B003ES5ZUU/ref=sr_1_4?ie=UTF8&qid=1302980479&sr=8-4-spell](http://www.amazon.com/AmazonBasics-High-Speed-Cable-Ethernet/dp/B003ES5ZUU/ref=sr_1_4?ie=UTF8&qid=1302980479&sr=8-4-spell)

I bought about a dozen of these Amazon Basic HDMI cables in various lengths They work for everything including 3D, and are cheap enough I now have spares...


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-16
> **23dornot23d said:**
> Looks good - but I do not get those options ..... ](*,)

My guess is I do not have the right hardware to do this ...... have a hdmi out ... and connected to a 32 inch tv .....

Here are my settings does anybody know if I can do the above ?

```

keith@keith-Aspire-7730ZG:~$ grep ^Codec /proc/asound/card?/codec*
/proc/asound/card0/codec#0:Codec: Realtek ALC888
/proc/asound/card0/codec#1:Codec: LSI ID 1040
/proc/asound/card0/codec#3:Codec: Nvidia MCP77/78 HDMI
keith@keith-Aspire-7730ZG:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0500000 irq 46
keith@keith-Aspire-7730ZG:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
keith@keith-Aspire-7730ZG:~$ lsmod | grep snd
snd_hda_codec_hdmi     28272  1 
snd_hda_codec_realtek   257696  1 
snd_hda_intel          33132  4 
snd_hda_codec          93180  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13413  1 snd_hda_codec
snd_pcm                81557  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13170  0 
snd_rawmidi            25327  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51702  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29140  2 snd_pcm,snd_seq
snd_seq_device         14160  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    56136  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
keith@keith-Aspire-7730ZG:~$ 


```Laptop is a [Acer Aspire 7730zg]("http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire7730ZG/Aspire7730ZGsp2.shtml")
I think mine is intel - not sure why it mentions nvidia .....

Sound Subsystem Dolby®-optimized surround sound system with two built-in stereo speakers and one subwoofer supporting low-frequency effects.
Optimized  2nd Generation Dolby Home Theater® audio enhancement, featuring Dolby®  Digital, Dolby® Digital Live, Dolby® Pro Logic® IIx, Dolby® Headphone,  Dolby® Natural Bass, Dolby® Sound Space Expander technologies.
True 5.1-channel surround sound output.
High-definition audio support.
S/PDIF (Sony/Philips Digital Interface) support for digital speakers.
MS-Sound compatible.
Built-in microphone .
HDMI out

Your video is (according to the web site link):
```
NVIDIA® GeForce® 9600M GT with up to 2303 MB of TurboCache&#8482; (512 MB of  dedicated GDDR3 VRAM, up to 1791 MB of shared system memory), supporting  NVIDIA® PureVideo&#8482; HD technology, OpenEXR High Dynamic-Range (HDR)  technology, Shader Model 4.0, Microsoft® DirectX® 10, or
NVIDIA®  GeForce® 9300M GS with up to 2047 MB of TurboCache&#8482; (256 MB of dedicated  DDR2 VRAM, up to 1791 MB of shared system memory), supporting NVIDIA®  PureVideo&#8482; HD technology, OpenEXR High Dynamic-Range (HDR)  technology, Shader Model 4.0, Microsoft® DirectX® 10.
```What are the options you see in the two tabs pictured above?  Can you do a screen shot of  both of them please?

 Are you running the Nivida Restricted Video Driver? The generic video and open source driver do not support sound-over-hdmi for Nvidia.
[I][B]
The Hedge[/B][/I]

:KS

---

### Post by 23dornot23d on 2011-04-16
I only get these three options ..........

[IMG]http://img842.imageshack.us/img842/9097/sound1o.jpg[/IMG]



to get any sound at all I have alwatys had to edit the config file and add the last line .......
---------------------------------------
gksudo gedit /etc/modprobe.d/alsa-base.conf

**options snd-hda-intel model=auto** 
----------------------------------------
I will remove it and see what happens now ....... maybe its been fixed for me ........

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=auto

```

---

### Post by lucazade on 2011-04-16
> **Hedgehog1 said:**
> [lucazade]("http://ubuntuforums.org/member.php?u=242850") - I don't know if they are as cheap for you in Italy, but these HDMI cables work nicely and are inexpensive:

 [http://www.amazon.com/AmazonBasics-High-Speed-Cable-Ethernet/dp/B003ES5ZUU/ref=sr_1_4?ie=UTF8&qid=1302980479&sr=8-4-spell](http://www.amazon.com/AmazonBasics-High-Speed-Cable-Ethernet/dp/B003ES5ZUU/ref=sr_1_4?ie=UTF8&qid=1302980479&sr=8-4-spell)

I bought about a dozen of these Amazon Basic HDMI cables in various lengths They work for everything including 3D, and are cheap enough I now have spares...


***The Hedge***

:KS

Yes, they are cheap also here..
problem is I get a poor image quality with hdmi (no problem with dvi)... I think it might depends on cable quality or probably to a broken firmware of my samsung p2370hd lcd. :confused:

---

### Post by Hedgehog1 on 2011-04-16
> **23dornot23d said:**
> I only get these three options ..........

[IMG]http://img842.imageshack.us/img842/9097/sound1o.jpg[/IMG]



I see you are running Gnome 3.0 - so our UI is different!

It appears to me that (1) You don't have the restricted Nvidia  video driver loaded or (2) your hardware just does not support audio-over-hdmi.


***The HDMI Hedge***

:KS

---

### Post by 23dornot23d on 2011-04-16
I have more options now .... but no sound after commenting out the intel ...

[IMG]http://img862.imageshack.us/img862/3585/sound3.jpg[/IMG]





Although I have the choices I still get no sound out ............ 


Here is after I enable HDMI OUTPUT ...........

[IMG]http://img855.imageshack.us/img855/336/sound4.jpg[/IMG]



[B]NVidia Restricted Video Driver loaded to support Audio over HDMI for NVidia cards

Which one is this do you have a link to it ..... I am running the latest 270.41 ...... at the moment

[IMG]http://img851.imageshack.us/img851/1706/sound5.jpg[/IMG]


I have a feeling I am out of luck here - been reading this ..... [LINK]("ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html") ..... but cannot really understand it

but the command they say to use does not show Nvidia for me at all .........

```

keith@keith-Aspire-7730ZG:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, HDMI 0
    HDMI Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct sample mixing device
dmix:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Hardware device with all software conversions
keith@keith-Aspire-7730ZG:~$ 


```
[/B]

---

### Post by Hedgehog1 on 2011-04-16
23dornot23d,

Well, those pictures establish that you **have indeed loaded the correct restricted nvidia drivers**.

So this is either a hardware specific thing, or a Gnome 3.0 thing. I think in your case you will be forced to use a variation of the updating of the asla setup files typically done for 10.10 install.

I am not running Gnome 3.0 at this time, so I cannot reproduce the situation on my system.

***The Hedge***

:KS

---

### Post by 23dornot23d on 2011-04-16
Cheers for taking time to have a look ...... 

Mine is this one  ......

NVIDIA®  GeForce® 9300M GS with up to 2047 MB of TurboCache&#8482; (256 MB of dedicated  DDR2 VRAM, up to 1791 MB of shared system memory), supporting NVIDIA®  PureVideo&#8482; HD technology, OpenEXR High Dynamic-Range (HDR)  technology, Shader Model 4.0, Microsoft® DirectX® 10.

I did go through this in detail in 10.10 development  ...... to get the sound working  ... thats when the intel line was added and I got sound .......  

one day we will have a solution so that it all works ok ....... it does in Linux Mint ....

Getting closer ......Thanks  ....

---

### Post by DukeBoxer on 2011-04-18
BEAUTIFUL!!! Thank you! I have a GeForce GTX 460 and mine was digital audio nr2 and I had to turn off analog to be able to control the volume through ubuntu and not my TV. It just keeps getting better!!!

---

### Post by Hedgehog1 on 2011-04-18
> **DukeBoxer said:**
> BEAUTIFUL!!! Thank you! I have a GeForce GTX 460 and mine was digital audio nr2 and I had to turn off analog to be able to control the volume through ubuntu and not my TV. It just keeps getting better!!!

Happy to help.  It's a 'helpful hedgie' thing...


***The Hedge***

:KS

p.s. I route the sound through the ARC (Audio Return Channel) between the TV and the Receiver (ARC makes the HDMI between the HDTV and the Receiver bi-direction for sound); this allows me to pump the sound through my big speakers.  **Makes Banshee sound really nice...**

---

### Post by Hedgehog1 on 2011-04-18
> **23dornot23d said:**
> Cheers for taking time to have a look ...... 

Mine is this one  ......

NVIDIA®  GeForce® 9300M GS with up to 2047 MB of TurboCache&#8482; (256 MB of dedicated  DDR2 VRAM, up to 1791 MB of shared system memory), supporting NVIDIA®  PureVideo&#8482; HD technology, OpenEXR High Dynamic-Range (HDR)  technology, Shader Model 4.0, Microsoft® DirectX® 10.

I did go through this in detail in 10.10 development  ...... to get the sound working  ... thats when the intel line was added and I got sound .......  

one day we will have a solution so that it all works ok ....... it does in Linux Mint ....

Getting closer ......Thanks  ....

I did update one of my Natty installs with Gnome 3.0 - and I found all  of the same options as I did in Unity (the list was complete).  So this is not a gnome 3.0 issue as far as I can tell.

***The Hedge***

:KS

---

