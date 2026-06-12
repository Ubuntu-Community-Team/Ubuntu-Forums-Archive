---
title: "Mythbuntu - USB Analog Capture / Encoder"
date: 2015-02-17
forum: Mythbuntu
---

### Post by derek29 on 2015-02-17
I am able to access the USB Live-2 audio and video from mplayer and vlc.  Now I am not sure how to configure the MythTV-backend to accept the device.  I am nearly complete however still unable to "view" the video from the composite source via the MythTV frontend.  This guy had a really good guide to creating a dummy channel for the front-end.  [http://www.gossamer-threads.com/lists/mythtv/users/44731](http://www.gossamer-threads.com/lists/mythtv/users/44731)  Here are my settings on the back-end:      Video sources          Video source name: VCR (call it what you want, VCR is just an example name)         Listings grabber: No grabber         Channel frequency table: default         Network ID: -1      Input connections (choose composite)          Capture device: [MPEG:/dev/video0]         Input: Composite1         Display name: VCRSource         Video source: VCR         External channel change command:         Preset tuner to channel: 1         Starting channel: 1  Channel 1 is my dummy channel.    dmesg reports this error when I try to use the front-end to view the video source:  [ 4968.866751] cx231xx #0:  setPowerMode::mode = 48, No Change req. [ 4968.875207] cx231xx #0: cx231xx_stop_stream():: ep_mask = 8

---

### Post by RayDeCampo on 2015-02-22
> **derek29 said:**
> I am able to access the USB Live-2 audio and video from mplayer and vlc.  Now I am not sure how to configure the MythTV-backend to accept the device.  I am nearly complete however still unable to "view" the video from the composite source via the MythTV frontend.  This guy had a really good guide to creating a dummy channel for the front-end.  [http://www.gossamer-threads.com/lists/mythtv/users/44731](http://www.gossamer-threads.com/lists/mythtv/users/44731)  Here are my settings on the back-end:      Video sources          Video source name: VCR (call it what you want, VCR is just an example name)         Listings grabber: No grabber         Channel frequency table: default         Network ID: -1      Input connections (choose composite)          Capture device: [MPEG:/dev/video0]         Input: Composite1         Display name: VCRSource         Video source: VCR         External channel change command:         Preset tuner to channel: 1         Starting channel: 1  Channel 1 is my dummy channel.    dmesg reports this error when I try to use the front-end to view the video source:  [ 4968.866751] cx231xx #0:  setPowerMode::mode = 48, No Change req. [ 4968.875207] cx231xx #0: cx231xx_stop_stream():: ep_mask = 8

Sorry Derek I can't really help with your problem but I thought maybe you could help me.  I understand that you were able to use the Hauppage USB Live-2 with your Ubuntu machine?  Is that correct?  Also, was there anything special you needed to do to get it to work?  I have been looking for something for composite video capture on linux.

Thanks,
Ray

---

### Post by derek29 on 2015-02-26
Ray:  I apologize for not responding sooner.   I will share with you anything I can to help you with the USB Live-2 and Ubuntu Linux.  

There is a Wiki with a page that takes you though it.  

[http://wiki.robotz.com/index.php/MythTV_Hardware-_Hauppauge_USB_Live-2](http://wiki.robotz.com/index.php/MythTV_Hardware-_Hauppauge_USB_Live-2)

If you have any specific questions please let me know.

---

### Post by RayDeCampo on 2015-02-27
> **derek29 said:**
> Ray:  I apologize for not responding sooner.   I will share with you anything I can to help you with the USB Live-2 and Ubuntu Linux.  

There is a Wiki with a page that takes you though it.  

[http://wiki.robotz.com/index.php/MythTV_Hardware-_Hauppauge_USB_Live-2](http://wiki.robotz.com/index.php/MythTV_Hardware-_Hauppauge_USB_Live-2)

If you have any specific questions please let me know.

No worries Derek.  I pulled the trigger and bought one.  It's mostly working.  I am using VLC to record the input to a file.  It only works for a bit when VLC stops adding to the file silently.  Looking in the VLC log I see a message: "Access_alsa warning: cannot read samples: Broken pipe".  So I am trying to figure out how to mitigate that problem.

---

