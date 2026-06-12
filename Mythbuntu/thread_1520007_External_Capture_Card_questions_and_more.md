---
title: "External Capture Card questions and more"
date: 2010-06-29
forum: Mythbuntu
---

### Post by intelquadcore on 2010-06-29
Hello, 
I am doing some research and wanted to start a mythbuntu box for a summer project :)
So I have a few questions...

I noticed on the wiki page that displays supported tv capture cards, but my question is has anyone tried the Black Magic Intensity Shuttle?

[http://www.blackmagic-design.com/products/intensity/](http://www.blackmagic-design.com/products/intensity/)

I want to know if it will work with 10.04 mythbuntu. Another thing I can't really grasp/comprehend is how does mythbuntu tell external capture cards to start recording? Like if I am away from my mythbuntu box and I have a a program set for a recorded time of my choosing, will it command the external capture card to start recording?
If I am not mistaken I noticed some people using a Hauppauge HD PVR as an external capture card since it takes so much stress of the computer. 

I currently have ATT U-Verse which is IPTV if I am not mistaken. Has anyone had success with their mybuntu box having U-Verse as a provider?

Through the web console, am I able to pull off recorded programs from my mythbuntu box to the PC from which I am accessing the mythbuntu box from? Say if my mythbuntu box is in the living room, and I am upstairs accessing the mythbuntu box via the IP address from my computer upstairs, can I move the file over the network to my computer upstairs?

And lastly for the configuration, I have a Cisco IPN 4320 DVR box that comes with the ATT U-Verse. It has coaxial, component, composite, and HDMI outputs. Say if I used an external capture card do I simply use the component output of the Cisco IPN 4320 to the input component of the external capture card and then have a usb connect to the pc (in the case of the Hauppauge HD PVR ) ? Does the source need to loop back to my TV? In my scenario I am using HDMI as a connector from the Cisco IPN 4320 to my TV.

---

### Post by iponeverything on 2010-06-29
> **intelquadcore said:**
> Hello, 
I am doing some research and wanted to start a mythbuntu box for a summer project :)


Sounds like fun.

> **intelquadcore said:**
> 
So I have a few questions...

I noticed on the wiki page that displays supported tv capture cards, but my question is has anyone tried the Black Magic Intensity Shuttle?

[http://www.blackmagic-design.com/products/intensity/](http://www.blackmagic-design.com/products/intensity/)

I want to know if it will work with 10.04 mythbuntu.



Unless there is specific feature from 10.04 you need, I would go for a less bleeding edge release, or even something like linhes.
> **intelquadcore said:**
> 


 Another thing I can't really grasp/comprehend is how does mythbuntu tell external capture cards to start recording? Like if I am away from my mythbuntu box and I have a a program set for a recorded time of my choosing, will it command the external capture card to start recording?

The actual recording is done on the myth box. The capture card is just the shim to feed the video into the computer. The mechanism that myth uses to read from a device varies according to hardware and really should not need consume any of brain cycles unless you really want to know, and in case you immerse yourself a bit into myth.

As for knowing what is on when, I use schedules direct (just do google search on it) it is a great service.  

> **intelquadcore said:**
> If I am not mistaken I noticed some people using a Hauppauge HD PVR as an external capture card since it takes so much stress of the computer. 

I currently have ATT U-Verse which is IPTV if I am not mistaken. Has anyone had success with their mybuntu box having U-Verse as a provider?

Through the web console, am I able to pull off recorded programs from my mythbuntu box to the PC from which I am accessing the mythbuntu box from? Say if my mythbuntu box is in the living room, and I am upstairs accessing the mythbuntu box via the IP address from my computer upstairs, can I move the file over the network to my computer upstairs?


Easily accomplished via a remote frontend.
> **intelquadcore said:**
> 
And lastly for the configuration, I have a Cisco IPN 4320 DVR box that comes with the ATT U-Verse. It has coaxial, component, composite, and HDMI outputs. Say if I used an external capture card do I simply use the component output of the Cisco IPN 4320 to the input component of the external capture card and then have a usb connect to the pc (in the case of the Hauppauge HD PVR ) ? Does the source need to loop back to my TV? In my scenario I am using HDMI as a connector from the Cisco IPN 4320 to my TV.

It sounds like fun project, I am sure that you will have good time getting all the pieces to work together. Just remember to keep it light, use google liberally and giving things a rest for few days when you hit a snag really helps to bring the issues into better focus.

---

