---
title: "Zotec F Front-End/Back-End setup for bedroom"
date: 2010-04-25
forum: Mythbuntu
---

### Post by kendoori on 2010-04-25
I have a firewire enabled Scientific Atlanta cable box in my bedroom that I would like to tap off of for DVR purposes, also watching streaming movies from Amazon.com etc... was thinking of building or buying a fanless dual core ION-based box for this, but have had problems finding something that's suitably small that would allow me to use firewire and not have a tuner. It seems that this [http://cgi.ebay.com/ZOTAC-IONITX-F-E-Intel-Atom-330-Mini-ITX-WiFi-M350-2GB-/400117302556?cmd=ViewItem&pt=Desktop_PCs&hash=item5d28d9851c](http://cgi.ebay.com/ZOTAC-IONITX-F-E-Intel-Atom-330-Mini-ITX-WiFi-M350-2GB-/400117302556?cmd=ViewItem&pt=Desktop_PCs&hash=item5d28d9851c) would fit the bill. It has a PCI-E x16 expansion slot slot, so it seems that I would be able to get a Firewire card to fit this.

I'd appreciate a reality check on this set up.

Also, I've not yet made the leap to Myth yet, so I'd appreciate feedback on the idea of combining front end/backend in the same box.

---

### Post by garyedwardjohnston on 2010-04-25
if it is for a dedicated media box i would go with

[http://www.mythbuntu.org/]("http://www.mythbuntu.org/")

and use a box that fits their specs

[http://www.mythtv.org/wiki/Hardware_Requirements]("http://www.mythtv.org/wiki/Hardware_Requirements")

---

### Post by movieman on 2010-04-25
My new frontend uses an Ionitx F-E motherboard and it plays most things with no problems; oddly it seems to have less trouble playing 1080P H.264 than MPEG-2.

I'm not sure it's really suitable for fanless use though; I tried running mine without the fan and the case over the CPU felt pretty hot. I eventually installed the fan because I couldn't get lm-sensors to tell me the CPU temperature.

---

### Post by kendoori on 2010-04-26
@Movieman Somehow the message in the forum clipped a piece of what I received in the email notification. You asked about about what I would be using Firewire for. Not sure it's doable because of my cable provider, but in our neck of the woods you do need a cable box to do pretty much anything and was hoping to use FW in lieu of a tuner, but also for channel changing.

Question regarding frontend/backend. If I decide to separate FE/BE, and attach my cable box to a BE, is that where the computing power needs to lie (assuming I want to do HD)? Trying to get a feel with how little I can reasonably get away with on a FE and BE and still do HD.

---

### Post by JMcFly on 2010-04-26
Flash (Hulu, etc) takes some juice on the front end, dual-core atom seems to be the recommendation for such a netbook. Back-end needs power to do commercial flagging, transcoding, ripping, etc at a reasonable rate but you can get away with a ~2004 vintage single-core P4 if you're not expecting the backend to do any software encoding of an analog stream (basic cable, in other words; this can be mitigated with an analog tuner with a hardware MPEG encoder) and can live with commercial flagging happening overnight vs near-realtime.
 
I would at least consider getting a digital tuner (or having an open slot to add one in the future) on the backend so you could grab one stream OTA while the other gets it from firewire. Two shows are always better than one, and would reduce the chance of missing a show.

---

### Post by LowSky on 2010-04-26
Withut Windows, you can forget streaming purchased video off Amazon. The downloads are covered in icky DRM.

You live in the US, so here's the best place to search for computers and parts. [http://www.newegg.com/](http://www.newegg.com/)

Firewire is on its way out so buyin a card for it is going to be tough. Buying a small comuter with it built in will be a challage unless you build your own box.

---

### Post by kendoori on 2010-04-27
I'm becoming convinced that a separate frontend/backend set up is the way to go for this. My cable provider (Cablevision) doesn't allow for much content without a set top box, and it seems the firewire option may not be an option because of encryption and some recent firmware updates. Assuming I want HD, is a USB capture device a reasonable option? if so, any suggestions?

---

### Post by larsolav on 2010-04-27
> **kendoori said:**
> I'm becoming convinced that a separate frontend/backend set up is the way to go for this. My cable provider (Cablevision) doesn't allow for much content without a set top box, and it seems the firewire option may not be an option because of encryption and some recent firmware updates. Assuming I want HD, is a USB capture device a reasonable option? if so, any suggestions?

If you want to record the **encrypted **HD programming from your cable provider, I believe your only option is the [HD-PVR]("http://www.hauppauge.com/site/products/data_hdpvr.html"). "HD-PVR records component video (YCrCb) from cable TV and satellite set top boxes, with a built-in IR blaster to automatically change TV channels for scheduled recordings."

---

### Post by Lepy on 2010-04-27
HD-PVR, as larsolav said, is your only option if you want to capture component (HD) output from your provider's STB. If you plan on watching and recording two shows at the same time, you will need 2 STBs and 2 HD-PVRs.

The only other way to get HD programming will be with a digital tuner that can pick up ATSC/ClearQAM. This is an excellent resource to find what OTA and ClearQAM channels you can receive in your area. Don't neglect the provider drop down!
[http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us)

Firewire would be the easiest as no blaster is required to tune channels, but most providers seem to disable this feature or encrypt all but the basic channels.

You could also wait for the 4 digital tuner w/ cablecard Ceton. This card will be amazing if it can get running under myth. Imagine recording any 4 HD channels at once on a single line. Not sure if there will be an opensource driver (I'm thinking not) and I'm really not sure of the status of cablecard in myth either. Something to watch out for though.

---

### Post by LowSky on 2010-04-28
> **kendoori said:**
> I'm becoming convinced that a separate frontend/backend set up is the way to go for this. My cable provider (Cablevision) doesn't allow for much content without a set top box, and it seems the firewire option may not be an option because of encryption and some recent firmware updates. Assuming I want HD, is a USB capture device a reasonable option? if so, any suggestions?

As larsolav said This will capture from a HD cable box using the RGB componant cables (1080i), and it works with MythTv

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815116030](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116030)

---

