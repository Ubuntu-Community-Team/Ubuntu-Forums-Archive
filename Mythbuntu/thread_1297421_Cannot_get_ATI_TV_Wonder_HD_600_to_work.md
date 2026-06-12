---
title: "Cannot get ATI TV Wonder HD 600 to work"
date: 2009-10-21
forum: Mythbuntu
---

### Post by Dougga on 2009-10-21
I purchased the ATI TV Wonder HD 600 but I can't get MythTV (mythbuntu) to recognize it.  I've read claims that it's supported but I don't see how.

I can see it in the PCI system and Mythbuntu logs but it fails to open when I attempt to configure it.

Any help would be appreciated.

---

### Post by deanfox on 2009-11-15
I also just purchased this device:  ATI TV Wonder HD600 USB TV Tuner.  

I installed tvtime from synaptic and started it.  It started and returned that I had no input devices (dev/vidio0) I plugged it the HD600 and started tvtime again absent the device error and saw a blue screen with access to all the tvtime controls.

I checked my "device manager" and the HD600 is correctly identified and was automatically assigned to two devices, video0 and vbi0.

So far I have tried just about every "setting" in tvtime I can think of and scanning for channels... Nothing.

I read forums but they're dated a year ago (10/08) indicating some firmware needed to be installed:

[http://ubuntuforums.org/showthread.php?t=885293](http://ubuntuforums.org/showthread.php?t=885293)
[http://ubuntuforums.org/showthread.php?t=941188](http://ubuntuforums.org/showthread.php?t=941188)

Having just upgraded to 9.10 I guessed a year to be a long time and that the "manual" installation may no longer me required.

Through these links I found:
[http://www.linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB](http://www.linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB)

The last update Aug 2009 - just three months ago.  I'm guessing at this point further firmware may be required.  I have not yet researched further.

Your post is three weeks old.  A long time to go without a resolution.  Since your post have you been able to get it working?

-[d]-

---

### Post by zedmanauk on 2009-11-16
I got the HD 600 working under MythTV by copying the firmware which is listed on the linuxtv link that you posted into /lib/firmware (as root) and then plugging in the HD 600.  It should show in dmesg that the usb device is recognized.  I then configured it as a DVB device under mythtv and it works fine for ATSC broadcast channels.  I'm using MythTv 0.21 under Ubuntu 9.04.  TvTime seems to only work for analog channels (which don't exist anymore), at least for this device.

---

### Post by steveneddy on 2009-11-16
I use a Hauppauge USB tuner for my laptop and use Kaffine to tune in digital stations.

Yes - KDE applications work with Ubuntu.

---

### Post by xtsuname on 2009-11-18
I just bought this device and it's connected to cable TV which I think is broadcasting analog signal, can someone help me on setting up MythTV to work with it? I've nearly tried everything but I have no idea how MythTV is supposed to work with it. Any help at all is really appreciated.

Thank you

---

### Post by cyberey66 on 2009-11-20
I use this program called me-tv to watch tv with the tv wonder hd 600.   For just watching tv, I prefer it over mythtv.

just install 'me-tv' and ''dvb-apps" packages and you should be good to go.'

If me-tv isnt doing and autoscan of the channels for some reason, you can scan manually using:

scan /usr/share/dvb/XXXX  

where 'XXXX' you tab out the channels you want to scan, you can figure it out.  For digital broadcast is:

scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB

My channel.conf looks like this:

ABC16:485028615:8VSB:49:51:1
CBS19:485028615:8VSB:65:67:2
CBS19:503028615:8VSB:49:51:1

it is a direct copy/paste of the output from the scan program.

---

### Post by cyberey66 on 2009-11-20
for the firmware:

wget [http://steventoth.net/linux/hvr1400/xc3028L-v36.fw](http://steventoth.net/linux/hvr1400/xc3028L-v36.fw)
sudo cp xc3028L-v36.fw /lib/firmware

---

### Post by xtsuname on 2009-11-21
I tried doing what you said. Me-TV somehow detectes it as an LG and not ATI TV Wonder. I am not sure why. And I'm getting basic cable from Comcast.

---

### Post by Koppie on 2009-11-23
> **xtsuname said:**
> Me-TV somehow detectes it as an LG and not ATI TV Wonder.

That's because the "digital demodulator" is an LG chip.  See here: [http://www.linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB](http://www.linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB)

I installed the firmware and ran a scan from the command line, picked up a lot of channels, and saved them into my own channels.conf file.  I told Me-TV to pick up this conf file and it imported the channels.  There's a delay when I change channels, and sometimes it gives strange error messages like "CRC32 check failed," but works anyway.  

Thanks for your help!

---

### Post by king vash on 2009-11-23
I have installed the suggested firmware 
dmesg suggests that it is recognizing the device

but when I try to run a scan from the command line (with either dvbscan or scan) I get errors like  "failed to open frontend"

I lsof the /dev/dvb/ and /dev/video0 and no programs are using them.

any advice?


this is a short blog post of the ati tv wonder hd 600 and mythtv
[http://www.kernellabs.com/blog/?p=1092](http://www.kernellabs.com/blog/?p=1092)

---

### Post by Koppie on 2009-11-23
You know what, yesterday it worked but today it doesn't.  Whenever I try to change channels it just hangs.  I didn't change any of the settings and I don't think I installed or upgraded anything new.  Verbose output doesn't give anything useful.  I've heard that it might have to do with not having a valid audio device but I *do* have working audio.

I do get this from the command line:
> demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
Failed to open mrl 'fifo:///home/koppie/.me-tv/me-tv-0.fifo'


---

### Post by cyberey66 on 2009-11-24
[http://linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB#Analog_Audio_Issue](http://linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB#Analog_Audio_Issue)

---

### Post by Koppie on 2009-11-26
> **cyberey66 said:**
> [http://linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB#Analog_Audio_Issue](http://linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB#Analog_Audio_Issue)

sox returns this:
> sox: invalid option -- w
sox: SoX v14.3.0

sox FAIL sox: invalid option


Me-TV worked out of the box but then it stopped, I wish I knew what I did to break it!  I even tried reinstalling but it didn't help.

Anyway I tried Kaffeine and it works GREAT.  It handles the scan (which Me-TV doesn't) and has better channel management.  This is my recommended solution!

---

