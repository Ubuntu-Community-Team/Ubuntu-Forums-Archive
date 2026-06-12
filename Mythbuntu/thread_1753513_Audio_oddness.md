---
title: "Audio oddness"
date: 2011-05-09
forum: Mythbuntu
---

### Post by uteck on 2011-05-09
I just upgraded the TV in the bedroom from an old 21" CRT to a 32" Vizio LCD.  Changing Myth to use HDMI was easy for video, but audio is being a pain.  "aplay -L" does not see HDMI as an output, so I grabbed some old PC speakers and hooked them up.  
Myth works over the speakers, but other sounds do not.  Firefox, Boxee, Hulu do not make any noise.  It is the same output that I was using on the old tv, so why does it not work now?
As long as I can get one audio output to work with all apps, I don't care which it is.

Another odd issue is that the music channels pause for a second every 10 seconds or so, but no other channels do.  When I bring the channel schedule up the skip goes away and the music plays fine.

HDMI is over the built-in GeForce 9300 GE
Running Mythbuntu 10.10, upgraded from 10.04 to try to fix audio
11.04 live cd does not see HDMI audio either

---

### Post by nickrout on 2011-05-09
what version of mythtv are you using?

what version of alsa?

---

### Post by uteck on 2011-05-10
Myth .24 and Alsa 1.0-23

---

### Post by earlneath on 2011-05-10
have you removed pulseaudio? pulse doesnt play nice with hdmi

---

### Post by agamotto on 2011-05-10
Ditch PulseAudio if it is running/installed.  Getting HDMI audio out is usually easy, but here are some ideas that you may be missing.  In Alsamixer or the gui mixer that is supplied by default, make sure that the HD nvidia or the Azalia 'sound card' is the highlit/selected sound card.  After this point, add controls, making sure that Master, Master Front, and Center are on, and sitting at somewhere around 75%.

In the Myth setup, select ALSA:hdmi, or just hdmi: as the audio device, and things should work...

---

### Post by nickrout on 2011-05-10
don't forget to scan for audio devices in myth setup.

---

### Post by uteck on 2011-05-11
Latest update from PPA fixed the issue with sound pausing on the music channels.

Pulse audio is not installed. alsa only sees analog devices.

```
aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, ALC1200 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Hardware device with all software conversions

```

lshw only finds one multimedia for audio;
product: MCP61 High Definition Audio
vendor: nVidia Corporation

The video card according to lspci is;
VGA compatible controller: nVidia Corporation G98 [GeForce 9300 GE] (rev a1)

I do have have the nvidia-current driver installed, 260.19.06-0ubuntu1

---

### Post by nickrout on 2011-05-11
Did you scan for audio devices in mythtv?

What device is mythtv using?

---

### Post by uteck on 2011-05-14
> **nickrout said:**
> Did you scan for audio devices in mythtv?

What device is mythtv using?

Myth only sees the devices that aplay sees. 
 I think it is using: plughw:CARD=NVidia,DEV=0

---

### Post by nickrout on 2011-05-14
did you scan in mythtv setup?

---

### Post by uteck on 2011-05-15
> **nickrout said:**
> did you scan in mythtv setup?

Yes, Myth sees the audio devices that aplay finds.

The analog audio works for Myth, but other system sounds do not play.  Firefox and Boxee have no sound, but they worked prior to the upgrade from 10.04 to 10.10.

---

### Post by nickrout on 2011-05-15
do you have an /etc/asound.conf or ~/.asoundrc?

---

### Post by uteck on 2011-05-16
> **nickrout said:**
> do you have an /etc/asound.conf or ~/.asoundrc?

Nope, just /etc/asound.names.

---

### Post by joho500 on 2011-05-17
Did you use alsamixer to unmute the digital device(s)?

---

### Post by uteck on 2011-05-18
> **joho500 said:**
> Did you use alsamixer to unmute the digital device(s)?

Alsa mixer is not muted. I have each level enabled and almost maxed out.
From other posts I have seen, alsa should see a device called HDMI, or at least one called digital, but is does not.

---

### Post by nickrout on 2011-05-18
I am unclear. Is your aim to get audio over hdmi working, or to get apps other than myth to work with analogue audio?

---

### Post by uncle hammy on 2011-05-20
Unless you're using ALSA 1.0.24, you're fighting a losing battle with HDMI audio.  Use this ppa [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa) and install the current version of ALSA.  You'll also need a .asoundrc file to specify the HDMI card as your default audio device for outside of Myth.

After all that, getting HDMI to reliably work with a 9300 is unlikely.

---

### Post by nickrout on 2011-05-20
Frankly I don't think you need alsa 1.0.24 for an older card like a 9300, but I may be wrong. I thought 1.0.24 was only needed for audio over hdmi on newer cards like the GT430.

---

### Post by uncle hammy on 2011-05-21
You could be right.  I am just going by my experiences with a 220 and 430....and JYA always pounding people about getting up to 1.0.24 on the mailing list.  I am pretty sure that to get it going with < 1.0.24, you have to stand on your head during a full moon, whereas with 1.0.24, it will likely just work (or as close as we get with HDMI audio right now, anyways).

---

### Post by zorro07 on 2011-06-09
Hi, 
As aplay -l does not see any digital devices I wonder if HD Audio has been disabled in the bios.  I would have a look and make sure HD audio is enabled.

I would also install alsa 1.0.24 as it make nvidia hdmi much easier to achieve.  I have a Asrock 330 ion net top and the only way to get hdmi to work at all was to install alas 1.0.24.  It's not difficult.  It is easy to find the instructions, I would also install alsa backports ;)

Once alsa 1.0.24 is installed the nvidia sound is picked up by the mixer app, select it and then select controls make sure you enable the switches for iec958 

Also run alsamixer from a terminal and ensure the iec958 mixer sliders are not muted.

You should then get hdmi sound easily.

If the above is not clear pm me and I'll try to help.  

I'm writing this from memory so hope it's a help.

Regards. Paul

---

### Post by uteck on 2011-06-16
I double checked the bios, but only options for audio are to turn it off, so I will give up on getting sound over HDMI with this card.

I did get audio working in Boxee, which has a similar audio setup as Myth does. So once I was familiar with it in Myth, then I saw that Boxee was using the wrong device after the upgrade.

So now my wife can watch the The Daily Show and anime on Crunchyroll in bed, so I can stop playing with settings now.

---

