---
title: "sound only from movies or mp3, but not both"
date: 2011-03-30
forum: Multimedia Software
---

### Post by bp787 on 2011-03-30
I have an ASRock 880GMH/USB3 MicroATX motherboard.  I have recently installed Ubunto 10.10.  This is primarily an HTPC.  
 
I'm using the integrated ATI 4250 video and integrated audio.  Video quality is quite good on 1080P content.  using XBMC or VLC, etc... I was able to get dvd rips to play with DD 5.1 sound properly.  It took some very odd combinations of selecting the audio device in XBMC and then setting the passthrough device to get it to work, though.  (I will have to wait until I get home to post up the specific details).
 
I am using HDMI to the tv, but using the board's optical audio output to my receiver.  Again, this works fine for movies now.
 
However, in this configuration I cannot hear any other audio.  No mp3s, flac files, system sounds, etc...
 
In the audio device configuration, i have the HDMI device selected.  This works to go out the optical output without a problem and again, DVD sound works.  The device shows up as "stereo", for what it's worth.
 
If I switch it to the internal audio device, IEC980 stereo device, I can hear system sounds, MP3's, etc... BUT I lose sound from movies.
 
I'm kind of at a loss with this.  
 
I will post up screen shots and any other log files you might need after work, but I appreciate any thoughts until then.
 
Thanks!

---

### Post by lidex on 2011-04-01
Check out the 'Simultaneous Output' tab of PulseAudio Preferences (System > Preferences > PulseAudio Preferences). If not installed:
```
sudo apt-get install paprefs
```

---

### Post by bp787 on 2011-04-04
> **lidex said:**
> Check out the 'Simultaneous Output' tab of PulseAudio Preferences (System > Preferences > PulseAudio Preferences). If not installed:
```
sudo apt-get install paprefs
```
 
 
Tried this.  Seemed to work for XBMC multimedia playback.
 
I had some skipping and weird audio playback issues with Amarok, but Rythmbox seemed to work ok.
 
However, when I went back to XBMC, DVD audio stopped working again.
 
It's still odd to me that the audio devices all come up a digital stereo devices, not digital 5.1/7.1 devices.  
 
I'll post screens tonight (been too busy to get them uploaded lately)

---

### Post by bp787 on 2011-04-05
Ok, so I had a network outage and couldn't get the pics uploaded last night.  so after work, up they go.
 
I tried a few things:
1.  Fedora 14 live - Same problem
2.  Ubuntu 11 alpha on a live usb - still had problems, but I was able to get VLC to output digital audio out S/PDIF to my receiver and video playback was very smooth, but boxee/XBMC do not run well on it yet.  I may have poorly compiled XBMC though.  
 
I went into alsamixer to adjust some settings in ubuntu.  The biggest difference I saw was that in 11.04 alpha, the HDA ATI SB sound device was detected as the default sound device and the basic iec958 device was even in the list as an option.  The only other option is the HDMI device.
 
So tonight, I'm going to do a fresh Meerkat install, ignore the ATI drivers and update the alsa devices to the latest.
 
Should I also update the Realtek drivers from the Realtek website?
 
As a control, I'm going to load up windows 7 on another drive just to be see what it reports.
 
Thanks!

---

### Post by lidex on 2011-04-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by bp787 on 2011-04-05
[http://www.alsa-project.org/db/?f=6481fae752a1b5f2a900786a9b64243e070f83f0](http://www.alsa-project.org/db/?f=6481fae752a1b5f2a900786a9b64243e070f83f0)

---

### Post by lidex on 2011-04-05
ALC892, eh? Don't have any documentation on that codec and your dmesg is showing some errors. 
Try upgrading your alsa-driver modules to get better support.
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

If that doesn't work, I would suggest a full alsa upgrade. you would first remove the ppa and the ppa modules then follow the link in my sig.

---

### Post by bp787 on 2011-04-05
Ok.  So a little more information.

xbmc options that are available to me:

audio output: 
* Optical/Coax - Analog - HDMI

Audio Output Device:  
* Internal Audio Digital Stereo (IEC958)
* RS880 Audio Device (Radeon HD 4200) | Digital Stereo HDMI
* defaults
* custom

Passthrough output device:
* HDA ATI SB iec958
* hdmi
* iec958
* custom
* HDA ATI HDMI hdmi
 
Other relevant xbmc information:  
* Speaker Configuration: 5.1
* DD/AC3 capable receiver is selected
* DTS capable receiver is selected

Selected Sound configuration is shown in the attached pictures:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=188234&stc=1&d=1302055364[/IMG]



[IMG]http://ubuntuforums.org/attachment.php?attachmentid=188235&stc=1&d=1302055358[/IMG]




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=188237&stc=1&d=1302055567[/IMG]


When I go to use Boxee, DVD audio is FINE!  I have DD 5.1 and DTS working.
Audio selections in boxee are:
Audio Output: Digital
Audio output device:  plughw: CARD=HDMI, DEV=3
Passthrough output device:  plughw:CARD=SB,DEV=1

However, music files will not play at all in boxee. 

With VLC, I am able to get digital output by setting the Output module to ALSA audio output and enabling the SPDIF option.  (Video is not rendering well, but that's a different problem...)  DD5.1 is also achieved setting to ALSA audio with the device set to:  default and selecting SPDIF.  HOWEVER, with any settings, I can't get mp3's to play with VLC.

I'm lost at this point... kinda frustrating.

I need the digital audio out from the HTPC to go into the audio receiver.  I think my only other possible configuration option is to send everything out the HDMI to the tv, and then connect the tv's Optical audio connection to the receiver.

Thoughts?

---

### Post by lidex on 2011-04-05
If your internal audio device's profile is set to stereo, it will output in stereo. Do you have other profiles available?

---

### Post by bp787 on 2011-04-05
I cannot seem to access any other setting other than stereo, unless I set it up as analog 5.1 or analog 7.1.  In terms of the digital settings, i'm not seeing anything that indicates that it support digital 5.1/surround sound

---

### Post by bp787 on 2011-04-05
And I did upgrade alsa as you indicated.  Nothing different on my end.

I'll do the complete alsa upgrade tomorrow to see what happens.

---

### Post by lidex on 2011-04-05
My profiles are the same, no digital surround.
Some references:
[http://ubuntuforums.org/showthread.php?p=10058679](http://ubuntuforums.org/showthread.php?p=10058679)
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)
[http://ubuntuforums.org/showthread.php?t=877811](http://ubuntuforums.org/showthread.php?t=877811)
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html](http://www.sabi.co.uk/Notes/linuxSoundALSA.html)

---

### Post by bp787 on 2011-04-08
well, audio actually works on the system.  So the driver support is fine, etc...  

in XBMC, I had to disable menu sounds, then audio gets passed correctly in DD 5.1/DTS and mp3/music files audio works fine as well.

It seems that there is a problem with xbmc, pulseaudio, and alsa all working together nicely.

annoying, but at least 99% works now.

---

### Post by lidex on 2011-04-09
> **bp787 said:**
> well, audio actually works on the system.  So the driver support is fine, etc...  

in XBMC, I had to disable menu sounds, then audio gets passed correctly in DD 5.1/DTS and mp3/music files audio works fine as well.

It seems that there is a problem with xbmc, pulseaudio, and alsa all working together nicely.

annoying, but at least 99% works now.

Do you need pulseaudio?
[http://forum.xbmc.org/showthread.php?t=59877](http://forum.xbmc.org/showthread.php?t=59877)

---

### Post by dixonstalbert on 2011-04-09
hello

I have had lots of trouble setting my onboard sound as well.

The alsainfo script says I have

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

which is similar to yours.

My problem was that if I watched a youtube with sound in firefox, later there would be no sound in rhythmbox and vice-versa

I found a post about how to switch from pulse to plain alsa that had this procedure:

```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio

Then log out and log in again.
Use alsamixer to adjust your sound card volume levels.
```

This worked for me and allows me to have simultaneous sound from firefox, rhytmbox, and my USB wintv.

according to the ubuntuforums post, you can switch back to using pulse with
```
sudo apt-get install ubuntu-desktop
``` 

sorry I did not keep the address of the post. If you try this, definitely back up your system first, so if this does not work, you can at least get back to where you are now.

also try searching on "Azalia (Intel HDA)" I think that is how to found the post above

Good luck

---

