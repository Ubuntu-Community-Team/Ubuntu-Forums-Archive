---
title: "Homerun"
date: 2012-07-28
forum: Mythbuntu
---

### Post by benlyboy on 2012-07-28
I'm thinking of up grading my systen with the addition os a Homerun prime tuner box.

This would give me 3 extra tuners, and more importantly access to the digital content on my cable (now I only have analog tuners)

But while researching the Homerun I read that any copy protected channels could not be opened
 
So I have two questions 

(1) Is there a way to know what channels are copy protected before buying the tuner?

(2) Any one using the Homerun...what do you think of it and how much can it view?

thanks for any feed back

---

### Post by klc5555 on 2012-07-30
> **benlyboy said:**
> I'm thinking of up grading my systen with the addition os a Homerun prime tuner box.

This would give me 3 extra tuners, and more importantly access to the digital content on my cable (now I only have analog tuners)

But while researching the Homerun I read that any copy protected channels could not be opened
 
So I have two questions 

(1) Is there a way to know what channels are copy protected before buying the tuner?

(2) Any one using the Homerun...what do you think of it and how much can it view?

thanks for any feed back

Can't address no. 2, because I don't use the device, but go to Silicon Dust's own site under "support" and "channels", plug in your zipcode, and see what is more or less available in the clear in your area, OTA and on the various cable providers. [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/)

---

### Post by TheFu on 2012-07-30
> **benlyboy said:**
> I'm thinking of up grading my systen with the addition os a Homerun prime tuner box.
This would give me 3 extra tuners, and more importantly access to the digital content on my cable (now I only have analog tuners)

But while researching the Homerun I read that any copy protected channels could not be opened
 
So I have two questions 
(1) Is there a way to know what channels are copy protected before buying the tuner?
(2) Any one using the Homerun...what do you think of it and how much can it view?
thanks for any feed back

I have an HDHR3, not a prime, I use it for ClearQAM recordings only.  

My understanding is that you need a CableCARD from the cable company installed into the Prime, but that all content you are supposed to view will be seen live, but that the mandatory copy protections will be honored.  These flags are built into the ATSC spec, so it needs to be supported to pass certification. 
[http://www.missingremote.com/guide/cablecard-tuner-essentials](http://www.missingremote.com/guide/cablecard-tuner-essentials) says:
> 
[LIST]
[*]Copy Freely means there is no protection on the files and  they can be played on any PC, edited, modified, and commercial skipped.
[*]Copy  Once means content can only be copied a single time (e.g. when it is  originally recorded) and can only be played back on the device which  copied it originally.
[*]Copy Never is only permissable [sic] in rare  cases such as PPV transmission and means that content may never be  copied (recorded), only viewed.
[/LIST]
Cable companies in different areas of the country either set or do not set those flags.  Unless you find someone on the same cable head with the same channel plan that you have, it is impossible to tell which channels have those flags set without trying it yourself.  

I used to get about 70 channels in ClearQAM from my provider before they encrypted everything except shopping, local networks and local government access channels. Even OTA broadcasts can have this flags.

[https://help.ubuntu.com/community/HDHomeRun](https://help.ubuntu.com/community/HDHomeRun) is where the SiliconDust guys point MythTV users for installation/setup instructions.

At this point I have to admit to running the TV recording part on Windows7. It  was better for me, but I watch everything through VLC or XBMC or a WD-TV Live. Free schedule data was the main concern, plus I had an unused, free Win7-Ult license. Here's my setup: [http://blog.jdpfu.com/2012/02/06/running-windows7-media-center-inside-a-kvm-vm](http://blog.jdpfu.com/2012/02/06/running-windows7-media-center-inside-a-kvm-vm)

I think only Windows7 has full DRM facility, so if any channels have any flag besides "copy freely" set, then a Linux recorder won't work. My understanding is this is strictly the content providers preventing that capability, since everything worked on Linux before the CableCARD validation testing.  In order to get a "certified" from the CableCARD industry group, they had to disable certain capabilities from the Linux drivers. That industry group is owned by the cable companies ... who are owned by big content.

[http://www.silicondust.com/support/hdhomerun/instructions/](http://www.silicondust.com/support/hdhomerun/instructions/) has a few links that could help. 

I hope this makes sense.  Try it. ** I know that I'll never go back to any other tuner after having an HDHR.  **

If I get some free time, I'll setup a mythtv box - the fantastic thing about the HDHR architecture is that any computer on the network can access an available tuner. It isn't limited to a single-PC.

---

### Post by benlyboy on 2012-08-01
Thanks guys for the replys 


You have given me a lot to think about. 
I think I may just go for it and see how things go.
I went down to the cable company's local office and they had no idea about flags, they just kept telling me if I had there card I could watch what ever I had paid for. Not sure this is true, but I guess I will find out.

---

### Post by nickrout on 2012-08-02
> **benlyboy said:**
> Thanks guys for the replys 


You have given me a lot to think about. 
I think I may just go for it and see how things go.
I went down to the cable company's local office and they had no idea about flags, they just kept telling me if I had there card I could watch what ever I had paid for. Not sure this is true, but I guess I will find out.

There are many people on the mythtv-users mailing list who know what local providers make freely available. Post there with your location and cable provider and you will most likely get a better idea.

---

