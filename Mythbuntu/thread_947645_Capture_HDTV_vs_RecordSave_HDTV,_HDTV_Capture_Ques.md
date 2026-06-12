---
title: "Capture HDTV vs Record/Save HDTV, HDTV Capture Question"
date: 2008-10-14
forum: Mythbuntu
---

### Post by Sircyro on 2008-10-14
I've been doing some research into what hardware I'm going to need for my first MythTV box. I live in Canada and have Rogers HD cable and would like to use MythTV to replace my PVR so I can add more functionality. 

I was looking at some of the ATSC capture cards so that I can record the HD and SD channels and I stumbled upon [this]("http://ubuntuforums.org/showthread.php?t=633908") article. It mentions that:

> There are no known consumer-level capture devices which will allow you to capture the HDTV output (DVI, HDMI, VGA, YPbPr / Component) from a set-top box commonly found with digital cable systems or satellite systems. None of the capture devices listed above perform any encoding; they merely allow your computer to save a copy of a HDTV stream which has already been converted to MPEG-2 at the broadcast facility.

What exactly is the difference between "capturing" HDTV and saving a copy of the HDTV stream? I was hoping to just grab the HDMI/Component out from the Rogers HDTV box and input it into the capture card, however I found that there really aren't a lot of HDMI input / component options. The only cards on the supported list have a coax connector only so I'm assuming that the video quality will be on par HDMI or component. I guess I always assumed that the coax out from the Rogers box would just be SD and I'd have to use HDMI or component to get HD picture.

As I said, this is my first MythTV box or any PVR type box for that matter, so any input would be greatly appreciated. I had my eye on one of the pcHD-TV cards if I can find one available to Canada, but any other suggestions would be welcomed. I also noticed that most of the HDTV capture cards on the supported list do not do hardware encoding, is that because the HDTV signal is already encoded mpeg2 from the source? And then the cpu would transcode the mpeg2 to something else like x264?

---

### Post by newlinux on 2008-10-14
The tuner cards that capture HD content from cable capture it via unencrypted QAM, not from a cable box (I guess this works the same in the US). Meaning, tuner cards actually tune a signal without a cable box, whereas capture would capture the signal from a cable box or other video output device. A tuner card tuning a digital signal wouldn't need to encode the mpeg 2 stream as you suggest, so no hardware encoding is needed. In the US, most cable locations only transmit the HD Locals and a smattering of other channels unencrypted via QAM.

Again, this is U.S. info, not sure how it works in Canada, but HDMI capture cards I know of won't work with cable due to HDCP content protection. The will only capture non HDCP HDMI streams, like what would come from a hidef video camera.

Your best bet for now to capture HD from set top box are:

Firewire - you can capture true HD from firewire, but what stations are available depend on the 5c copy protection setting.

Hauppage HD-PVR: Myth drivers are in alpha or beta status, but this device captures streams from component in encodes them to h.264.

---

### Post by mrand on 2008-10-14
> **Sircyro said:**
> I've been doing some research into what hardware I'm going to need for my first MythTV box. I live in Canada and have Rogers HD cable and would like to use MythTV to replace my PVR so I can add more functionality. 

I was looking at some of the ATSC capture cards so that I can record the HD and SD channels and I stumbled upon [this]("http://ubuntuforums.org/showthread.php?t=633908") article. It mentions that:



What exactly is the difference between "capturing" HDTV and saving a copy of the HDTV stream? I was hoping to just grab the HDMI/Component out from the Rogers HDTV box and input it into the capture card, however I found that there really aren't a lot of HDMI input / component options. The only cards on the supported list have a coax connector only so I'm assuming that the video quality will be on par HDMI or component. I guess I always assumed that the coax out from the Rogers box would just be SD and I'd have to use HDMI or component to get HD picture.

As I said, this is my first MythTV box or any PVR type box for that matter, so any input would be greatly appreciated. I had my eye on one of the pcHD-TV cards if I can find one available to Canada, but any other suggestions would be welcomed. I also noticed that most of the HDTV capture cards on the supported list do not do hardware encoding, is that because the HDTV signal is already encoded mpeg2 from the source? And then the cpu would transcode the mpeg2 to something else like x264?Howdy,

As you've hinted to, "capturing" involves the video stream passing through an analog stage, while "saving a copy" is presumably done purely in the digital domain.  The options are (best quality listed first):
[LIST]
[*]Digital receiver (no analog)
[LIST=1]
[*]Firewire (everywhere and cheap, but many channels likely encrypted by provider)
[*]Direct OTA or cable (HDHomerun and numerous other internal and external digital receivers.  Many channels likely encrypted)
[*]DVI/HDMI (technically possible, but very difficult due to encryption and the data rate of uncompressed data)
[/LIST]
[*]Analog Capture (analog to digital, obviously)
[LIST=1]
[*]Component ([HD PVR]("http://www.hauppauge.com/site/products/data_hdpvr.html") and one or two others)
[*]Cable/coax or S-video (numerous internal and external devices)
[*]Composite (numerous internal and external devices)
[/LIST]
[/LIST]As you can see, the digital receivers would be ideal (cheap and easy and high quality), but many users are limited to just the local stations - everything else is encrypted.  The reason that the HD PVR excites everyone is that it enables super quality while still having legal access to encrypted channels.  Rogers has been [well discussed]("http://www.gossamer-threads.com/lists/engine?list=mythtv&do=search_results&search_forum=forum_1&search_string=Rogers&search_type=AND") on the mythtv-users list,  I'd suggest reading those threads.

Good luck,

[INDENT]Marc[/INDENT]

---

### Post by Sircyro on 2008-10-14
So looping from the cable out on the stb to one of the supported MythTV supported capture cards would not produce HD? Or just doesn't work with digital channels at all? Are SD digital channels usually unencrypted?

So the broadcasts in [these]("http://www.mythtv.org/wiki/index.php/User_Manual:Watch_TV") photos were of unencrypted channels? 

I was hoping to keep everything in one HTPC box, and I've heard that the Hauppauge HD-PVR get's loud when recording.

---

### Post by newlinux on 2008-10-14
> **Sircyro said:**
> So looping from the cable out on the stb to one of the supported MythTV supported capture cards would not produce HD? Or just doesn't work with digital channels at all? Are SD digital channels usually unencrypted?

So the broadcasts in [these]("http://www.mythtv.org/wiki/index.php/User_Manual:Watch_TV") photos were of unencrypted channels? 

I was hoping to keep everything in one HTPC box, and I've heard that the Hauppauge HD-PVR get's loud when recording.


If the cable coming out of the box is a passthrough of the RF signal comming into the cable box (basically the equivalent of splitting the signal before it comes into the cable box and hooking that up to a tuner card) then you can tune unencrypted digital stations with a QAM tuner card. For me this includes my local major network affiliates and local stations in SD and in HD, as well as a few shopping channels in SD, but not much else. Everything else is encrypted. I think this is typical in the US. This is true of all QAM cards. not just mythtv supported ones. 

If the cable coming out of the box is a TV-out and sends what the cable box is currently tuned to then it will only be in analog SD, and you would need an analog tuner card and there would be no HD. the cable box does not output HD stations from it's coax.

 
The only ways to get all of your cable stations in what amounts to their original quality is using firewire (if all stations weren't 5c protected, but this is unlikely), using a device like the HD-PVR.

---

### Post by Sircyro on 2008-10-14
Ahh ok that clears some things up, thank you both for the info and the link to the Mythtv-users list. 

So only unencrypted SD and HD channels through a tuner card, or if I use an IR blaster to control the cable box I could get all my digital channels through Coax (ch 3), s-video, but they would all be SD correct?

You mentioned analog to digital conversions mrand, component would provide an analog->digital conversion HD quality (720p) while Coax/Composite would provide analog->digital conversion of SD quality correct? You mentioned there were a few other component capture cards, are they not supported by MythTV like the beta HD-PVR drivers? I was hoping for something purely internal, but I can make external work.

---

### Post by newlinux on 2008-10-14
> **Sircyro said:**
> Ahh ok that clears somet things up, thank you both for the info and the link to the Mythtv-users list. 


So only unencrypted SD and HD channels through a tuner card. You mentioned analog to digital conversions mrand, component would provide an analog->digital conversion HD quality (720p) while Coax/Composite would provide analog->digital conversion of SD quality correct? ....

Yes. component can do 1080i and 1080p too (although most devices won't output 1080p over component, it can do it). Coax and composite and s-video are only capable of SD analog signals. You could change the channels with an IR blaster, or with firewire if your box supports it.

I don't know of any other consumer level devices that capture component HD and convert it to digital in real time other than the HD-PVR so I'd be curious to know what those are too...

---

### Post by mrand on 2008-10-14
> **newlinux said:**
> <...>I don't know of any other consumer level devices that capture component HD and convert it to digital in real time other than the HD-PVR so I'd be curious to know what those are too...
I believe there is more than one ([click for possible list]("http://theelectronicmailbox.com/vidcap.htm")) professional grade component capture device out there, but I'm guessing that none of us would be willing to spend the money for it - and if I were to guess, only the windows drivers are available.

Someday there is supposed to be a semi-open source alternative to the HD-PVR, but it isn't on a fixed time table, as one might imagine:
[http://www.gossamer-threads.com/lists/mythtv/users/351665?search_string=pvrcompanion.com;#351665](http://www.gossamer-threads.com/lists/mythtv/users/351665?search_string=pvrcompanion.com;#351665)

I'm hoping it makes it to market before I buy an HDTV (which is also isn't on a fixed time table)!

[INDENT]   Marc[/INDENT]

---

