---
title: "Selecting a specific audio device"
date: 2009-08-25
forum: Multimedia Software
---

### Post by sangandongo on 2009-08-25
Hey everyone,

This may fall under more than one category, but because its related to both internal audio and usb audio, i figured i'd start here.

I run Windows XP inside VirtualBox for work to connect to client networks. At work, we use OCS (Office Communications Suite or something like that) to make calls and IM internally. Overall, my system is speedy and audio works beautifully.

We were issued Plantronics headsets to make calls over OCS. The plantronics on its own works great under Ubuntu. It works like garbage inside the VirtualBox over emulated USB.

Because the host operating system recognizes the Plantronics as USB audio, I should technically just be able to use it with the guest VM in the same way I use the normal internal audio of the host system. In other words, I should be able to select this device as my primary sound source and use both the microphone and ear piece to talk.

Within Ubuntu I can select the different sources. When I bring up VirtualBox, it doesn't differentiate sources. There's only one Alsa option, only one OSS option and only one PulseAudio option.

Anyone have a suggestion for me to get audio routed to the guest through the USB audio card rather than the internal one?

Thanks!

--
john

---

### Post by sangandongo on 2009-08-25
Just an update- 

I was able to get the headset to work in the Guest OS by blacklisting the internal audio device in /etc/modprobe.d/blacklist.conf, but this is not really an optimal scenario for me. 

Seems there should be a better way to do this whereby I can have the USB Audio route to the VirtualBox app and the Host system retain its normal audio. 

I'll play around with some blacklisting. Perhaps I can blacklist the USB device on the main config and blacklist the internal sound card within OSS, then choose OSS as the sound server for VirtualBox. 

I'll report back with success or failure in case anyone else needs this information in the future.

---

### Post by sangandongo on 2009-08-26
blacklisting the internal sound card at the OSS level fails when trying to specify only OSS to the VirtualBox guest. the internal card simply acts as though its being blacklisted at the top level. Perhaps I misunderstood how the blacklist-oss worked. 

Anybody have a suggestion?

---

### Post by sangandongo on 2009-08-27
Beuller?

Is there a way to separate better the sound controllers or route sound from one controller to specific apps?

---

