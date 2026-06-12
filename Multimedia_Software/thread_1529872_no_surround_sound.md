---
title: "no surround sound"
date: 2010-07-12
forum: Multimedia Software
---

### Post by nhasian on 2010-07-12
My motherboard has both the optical audio out as well as the coax one. which one is preferable to use?

I also have a Sony 5.1 Dolby Digital/DTS Surround sound decoder that I'm outputting the audio to.

I tried both audio connectors the coax and the optical and in Sound Preferences-> Hardware, under the Profile drop down box, I am unable to choose Analog Surround 5.1 Output + Analog Stereo Input. I'm guessing this is the right profile to use right? I only hear sound when I choose *Digital Stereo* or *Analog Stereo* Output but then i only get stereo and not surround sound :(

Please advise. thanks!

---

### Post by lidex on 2010-07-14
From this page:
[http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut")
> Digital Sound Media

Digital signals (PCM or BitStream) can be sent across different media. We can distinguish:

    * Coaxial S/PDIF - a coaxial wire is used to send data in S/PDIF format. This connection has a throughput that allows at most two raw PCM channels or some "lossy" compression codecs. No "lossless" compression codec can be used on this media. This means that in order to have 5.1 sound with a coaxial S/PDIF connection, the sound must be transmitted in a (supported) encoded bit stream and decoded by the receiver.
    * TOSLINK S/PDIF - same as coaxial S/PDIF but the information is transmitted through an optical link. The throughput is the same as for coaxial S/PDIF, hence the same limitations apply.
    * HDMI - audio information can be transmitted together with video through an HDMI connection. The throughput of an HDMI connection is sufficient to allow 8 raw PCM channels or a "lossless" compression codec bit stream [perhaps HDMI before version 1.3 allows a little bit less]. That means that, with a HDMI connection, decoding of 5.1 or 7.1 sources can be done either before sending the data (i.e. on the computer and sending data as raw PCM channels) or after sending the data (i.e. by the receiver). 

---

### Post by nhasian on 2010-07-14
thanks so there is no difference between using the optical or coax.  still my original issue persists.  how can i get surround sound?

---

### Post by Starfleet on 2010-07-14
nhasian...I had the same problem. Couldn't use my 5.1 surround sound. But found that it was in my Alsamixer settings. I'm using my coax. Make sure the surround sound settings are correct. First, I have selected _analogue stereo duplex_ in my _sound preferences_ and not 5.1 surround sound (Sound Preferences = the place where you click on the volume control on the task bar). Next in a terminal window type 'alsamixer' which will bring up the full alsamixer controls. Tab along the bottom buttons using the cursor keys left and right, and make sure all the surround sound controls are switched on by pressing 'M' on your keyboard eash time you select a feature. When you do this two zero's will appear and that feature will be switched on. Make sure you increase the volume levels of each individual item you enable. Some of them will not have a volume level eg: external amplifier, that you can increase so just turn it on. Obviously, there may be some things you don't need to switch on but make sure anything to do with the surround sound is turned on including the 'external amplifier' button if you have one, and the 'duplicate' button too. This should produce your surround sound in stereo. Good luck!

---

### Post by lidex on 2010-07-14
> **nhasian said:**
> thanks so there is no difference between using the optical or coax.  still my original issue persists.  how can i get surround sound?

Did you read the linked page? Also scroll down to surround sound section on this page:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012]("http://ohioloco.ubuntuforums.org/showthread.php?t=843012")

Also this:
[http://ubuntuforums.org/showthread.php?t=1491347]("http://ubuntuforums.org/showthread.php?t=1491347")

---

