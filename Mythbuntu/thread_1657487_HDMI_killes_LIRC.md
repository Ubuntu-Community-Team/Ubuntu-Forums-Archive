---
title: "HDMI killes LIRC"
date: 2011-01-01
forum: Mythbuntu
---

### Post by microtechno on 2011-01-01
Hey all
Not sure what is happening but it is really wierd. LIRC works for me all  the config files are correct for my remote and MythTv. Using a home  brew serial receiver that is tested to work when I am connected to a  computer monitor, irw outputs the correct key information and the remote  works in mythtv when connected via DVI or DSUB.
Once the mythtv box is connected to the LCD TV it all stops working. The  tv is a Sony Bravia KDL-40EX500. Using irw when the tv is turned off  and connected outputs the correct key mappings and information.
As soon as the tv is powered on irw stops outputting any information and  remains blank. Using irrecord outputs either lots of dots or nothing  and then has multiple errors when trying to map keys (did this for a  test).
The tv comes with the HDMI cec which turned on or off makes no differance.
The nvidia driver for the card is 173 this provides the same error as using the current driver.
Further to that from
"dmesg | tail"
[   91.520028] Clocksource tsc unstable (delta = -250005107 ns)

System Specifications
lsb_release -rd
Description:    Ubuntu 10.04.1 LTS
Release:        10.04

01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400GS] (rev a1)

---

### Post by ian dobson on 2011-01-01
Hi,

Not sure if this helps, but I have a very similar frontend setup (Homebrew IR,NVidia 9600 HDMI to Sony kd42) and the system works without any problems. I've run all versions from 9.04 to 10.10 without any problems.

Do you see any other interesting messages in dmesg.

Regards
Ian Dobson

---

### Post by LowSky on 2011-01-01
How would HDMI cause IR problems? Something else has to be at fault.

---

### Post by microtechno on 2011-01-02
> **ian dobson said:**
> Hi,

Not sure if this helps, but I have a very similar frontend setup (Homebrew IR,NVidia 9600 HDMI to Sony kd42) and the system works without any problems. I've run all versions from 9.04 to 10.10 without any problems.

Do you see any other interesting messages in dmesg.

Regards
Ian Dobson

Are you getting sound through the HDMI, as I am unaware of the nvidia cards being able to output sound. Also does your TV have the sony CEC (Bravia Sync)? Because I thought this might be killing LIRC somehow, as using BS the tv remote can control a PS3 over HDMI. Which might some how interfear with the myth box somehow.. but no idea how.

I am not sure about why HDMI is cutting out LIRC, but thats the only thing that changes between LIRC working and not.
I have a feeling that it has something to do with the timing or something, as from dmesg I get the clocksource tsc error (as above). Which I have no idea what this means. Below is dmesg related to lirc, there is something odd there also, the spike which I have no idea about either :S

```
dmesg | grep lirc
[   19.341896] lirc_dev: IR Remote Control driver registered, major 61 
[   20.310030] lirc_serial: auto-detected active high receiver
[   20.310035] lirc_dev: lirc_register_driver: sample_rate: 0
[   20.310115] lirc_serial $Revision: 5.104 $ registered
[   64.042821] lirc_serial: ignoring spike: 0 0 4d2003e6 4d2003e6 bd56c bd549
```

---

### Post by nickrout on 2011-01-02
> **microtechno said:**
> Are you getting sound through the HDMI, as I am unaware of the nvidia cards being able to output sound.of course they can, what rubbish>  Also does your TV have the sony CEC (Bravia Sync)? Because I thought this might be killing LIRC somehow, as using BS the tv remote can control a PS3 over HDMI. Which might some how interfear with the myth box somehow.. but no idea how.

I am not sure about why HDMI is cutting out LIRC, but thats the only thing that changes between LIRC working and not.
I have a feeling that it has something to do with the timing or something, as from dmesg I get the clocksource tsc error (as above). Which I have no idea what this means. Below is dmesg related to lirc, there is something odd there also, the spike which I have no idea about either :S

```
dmesg | grep lirc
[   19.341896] lirc_dev: IR Remote Control driver registered, major 61 
[   20.310030] lirc_serial: auto-detected active high receiver
[   20.310035] lirc_dev: lirc_register_driver: sample_rate: 0
[   20.310115] lirc_serial $Revision: 5.104 $ registered
[   64.042821] lirc_serial: ignoring spike: 0 0 4d2003e6 4d2003e6 bd56c bd549
```

possibly the tv screen is outputting sufficient light to swamp the IR receiver. Try moving it so light from the screen is less likely to affect it.

---

### Post by microtechno on 2011-01-02
> **nickrout said:**
> of course they can, what rubbish

I wasnt aware of this, thought it was just ati. Do you have a link for compatible cards and how to set it up then? as if it is possible to run the audio through the hdmi that would be great, saves an extra cable.

> **nickrout said:**
> possibly the tv screen is outputting sufficient light to swamp the IR receiver. Try moving it so light from the screen is less likely to affect it.

I just checked that and it works, covered up the TV and it worked. Don’t I feel foolish now :S
I shall have to reposition the IR receiver then.
Thanks though for all the help

---

### Post by ian dobson on 2011-01-02
Hi,

New nvidia cards (2xx series) have an onboard audio device that Linux/alsa can directly control. Older cards 8x and 9x series sometimes has a spdif input. So in my case I've connected the spdif output on the motherboard to the spdif input on the Graphic Card, the graphic card then multiplexes the audio into the HDMI signal that the TV can then play back.

Regards
Ian Dobson

---

### Post by microtechno on 2011-01-02
Wow
I didnt know that. Guess the saying you learn something new every day is true. Shall have to check out if my card has this.
Although it doesnt have a dedicated HDMI output I am using a DVI to HDMI converter so I am not getting my hopes up high.

---

### Post by ian dobson on 2011-01-02
Hi,

Sorry bur DVI doesn't support audio output. Have a look here [http://en.wikipedia.org/wiki/Digital_Visual_Interface#HDMI_audio_support](http://en.wikipedia.org/wiki/Digital_Visual_Interface#HDMI_audio_support)

Regards
Ian Dobson

---

### Post by microtechno on 2011-01-02
Thought that would have been the case. Oh well might just get another graphics card. The internal graphics have HDMI ATI 2100 but being built into the motherboard will use too much cpu, that and I cant use VDPAU for all the HD videos and playback.
ARG at ATI :(

---

### Post by ian dobson on 2011-01-02
Yuk, I've not used a ati for several years since I spent more than a day trying to get an onboard ati card working. It would work correctly for several hours then suddenly drop back to vga resolution. And that was on Windows XP.

The nvidia Linux drivers have always been better under linux and since vdpau there's no reason to use anything else. I know that the drivers aren't open source, but I want a working system.

Regards
Ian Dobson

---

### Post by nickrout on 2011-01-02
> **ian dobson said:**
> Hi,

Sorry bur DVI doesn't support audio output. Have a look here [http://en.wikipedia.org/wiki/Digital_Visual_Interface#HDMI_audio_support](http://en.wikipedia.org/wiki/Digital_Visual_Interface#HDMI_audio_support)

Regards
Ian Dobson

Again, utter rubbish. DVI and HDMI are digitally identical - thay can carry the same signal. The audio and video are multiplexed in the digital stream so dvi can carry audio. So you can send audio from a dvi based video card to a tv with an hdmi input. There are examples given in the mailing list archives.

---

### Post by ian dobson on 2011-01-02
> **nickrout said:**
> Again, utter rubbish. DVI and HDMI are digitally identical - thay can carry the same signal. The audio and video are multiplexed in the digital stream so dvi can carry audio. So you can send audio from a dvi based video card to a tv with an hdmi input. There are examples given in the mailing list archives.

So please show me real prufe for your comments. Purely from my experience DVI does not support audio, but some NVidia/ATI cards can provide audio over DVI using non-standard pins/special DVI/HDMI adapter.

Here's a link to the DVI version 1.0 specification [http://www.ddwg.org/lib/dvi_10.pdf](http://www.ddwg.org/lib/dvi_10.pdf)
and the HDMI 1.3 specification [http://www.evernew.com.tw/HDMISpecification13a.pdf](http://www.evernew.com.tw/HDMISpecification13a.pdf)
Regards
Ian Dobson

---

### Post by nickrout on 2011-01-02
> **ian dobson said:**
> So please show me real prufe for your comments. Purely from my experience DVI does not support audio, but some NVidia/ATI cards can provide audio over DVI using non-standard pins/special DVI/HDMI adapter.

Here's a link to the DVI version 1.0 specification [http://www.ddwg.org/lib/dvi_10.pdf](http://www.ddwg.org/lib/dvi_10.pdf)
and the HDMI 1.3 specification [http://www.evernew.com.tw/HDMISpecification13a.pdf](http://www.evernew.com.tw/HDMISpecification13a.pdf)
Regards
Ian Dobson

I assume you mean **proof**:

[http://www.gossamer-threads.com/lists/mythtv/mythtvnz/426301#426301](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/426301#426301)

JYA is the guy who writes the audio code on mythtv so I think he knows what he is talking about.

And what do you mean "non standard pins"? the data (audio and video) is carried in a digital TMS stream, so no extra pins are needed.

See also wikipedia > Compatibility with DVI

A DVI signal is electrically compatible with the video part of an HDMI signal; no signal conversion is required when an adapter or asymmetric cable is used, and consequently no loss in video quality occurs.[3] As such, HDMI is backward-compatible with single-link Digital Visual Interface digital video (DVI-D or DVI-I, but not DVI-A) as used on modern computer monitors and graphics cards. This means that a single-link DVI-D source can drive an HDMI monitor, or vice versa, by means of a suitable adapter or cable. However, the audio and remote-control features of HDMI will not be available unless the output supports HDMI via a DVI plug (e.g., ATI 3000-series and NVIDIA GTX 200-series video cards).[3] Additionally, not all devices with DVI input support High-bandwidth Digital Content Protection (HDCP). Without such support by the device, an HDCP-enabled signal source will suppress output and so prevent the device from receiving HDCP-protected content.[91] All HDMI devices must support sRGB encoding. 

---

### Post by BicyclerBoy on 2011-01-04
Play nice...both are sort of right

A single link 19 pin HDMI is an electrical subset of DVI-I.

But the HDMI standard has a lot of extra supported protocols.
DVI standard does not include audio signalling or the remote control stuff.

But DVI is still able to do all this and more if the support is in the video card chipset.

This is fairly universal in the latest graphics card.
That's why it refers to GT200 series or later...(& the ATI thing)

---

### Post by traflaz on 2011-01-24
> **microtechno said:**
> Hey all
Not sure what is happening but it is really wierd. LIRC works for me all  the config files are correct for my remote and MythTv. Using a home  brew serial receiver that is tested to work when I am connected to a  computer monitor, irw outputs the correct key information and the remote  works in mythtv when connected via DVI or DSUB.
Once the mythtv box is connected to the LCD TV it all stops working. The  tv is a Sony Bravia KDL-40EX500. Using irw when the tv is turned off  and connected outputs the correct key mappings and information.
As soon as the tv is powered on irw stops outputting any information and  remains blank. Using irrecord outputs either lots of dots or nothing  and then has multiple errors when trying to map keys (did this for a  test).
The tv comes with the HDMI cec which turned on or off makes no differance.
The nvidia driver for the card is 173 this provides the same error as using the current driver.
Further to that from
"dmesg | tail"
[   91.520028] Clocksource tsc unstable (delta = -250005107 ns)

System Specifications
lsb_release -rd
Description:    Ubuntu 10.04.1 LTS
Release:        10.04

01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400GS] (rev a1)

(Sorry but I'm steering this thread back on track...)

I figured it out. I have pretty much the same setup as you do (Bravia KDL-32EX500). You have to disable the ambient sensor (Settings -> Picture -> 2nd page -> Ambient Sensor).

My guess is that the ambient light sensor works by sending some kind of infrared signal in the room, which bounces back to computer's IR receiver and messes it up.

What thrown me off was that it worked when I plugged my computer with a VGA cable. I guess the TV doesn't activate the sensor when PC input is selected.

EDIT: Nope! That's not it... See next post below.

---

### Post by traflaz on 2011-01-27
Well, this one is proving to be more of a head-scratcher than I thought.

I ***think*** this is what happens. The remote works if I boot the computer **after** the television is open. If I boot it **before** opening the TV, then the little light on my IR receiver is always open (it's not supposed to) and the remote doesn't work.

Is it possible that LIRC calibrates itself when starting up? If it makes the calibration in the dark room, when the TV lights up, it shines back to the receiver and LIRC thinks it's some kind of signal.

Does this makes sense or am I off? Is there a way to redo the calibration, like every minute, or better when a series of wrong inputs are detected? Or just adjust it to be less sensitive?

---

