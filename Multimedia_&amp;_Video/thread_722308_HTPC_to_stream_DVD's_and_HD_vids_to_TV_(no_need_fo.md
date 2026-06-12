---
title: "HTPC to stream DVD's and HD vids to TV (no need for myth)"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by Rizla on 2008-03-12
Alright guys, im hoping someone else might have run into the situation I want to set up.

I have an HDTV in the living room and a file server with my video content (480P and 720P).  I want to know what the best setup to use to get that video onto my tv.  I want to build a small form factor PC that doesnt use a lot of power and is silent.

My main question is regarding what video card I should get that can do HD streaming that plays nice with ubuntu.

I dont need it to act as a TV tuner, i have another pc with Myth for that.  This is just going to be a front end unit.  

To reiterate the main point is I want it capable of playing 720P and possibly 1080P (in the future).  I know 1080 content is pretty CPU intensive so is there a video card that would be best to use to future proof?  Any help would be great.

Thanks

---

### Post by aeiah on 2008-03-12
i dont think the graphics card is too important, as long as it is above average id say. go with nvidia to avoid problems. i have no issues with a 7800gt. the main issue is with the CPU, since x264 has a lot of fancy things going on. i have an AMD x2 3800 and things run ok. although you're going for something small and silent, i would make sure it isnt too slow, and you should probably go for a multi-core cpu.

you'll also want gigabit ethernet on both your fileserver and your htpc. i would think. if your router is only 10/100, you might as well test it with that first. you'd be very lucky to get a decent enough connection through wifi.

as for accessing it, you could look into elisa (although your pc will take a performance hit, and you might get juddering on your HD films) or just use your filebrowser.

---

### Post by Rizla on 2008-03-12
**This post could be related to an Ubuntu bug filed at**: I got hellanzb working yesterday based on the initial setup in this post, come to find out after reading ALL 26 pages.  That its in the repo's now.  For the sake of easy managemnt, I want to remove all the files associated with hellanzb that I installed and configed yesterday.  Whats the best way to do this. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **aeiah said:**
> i dont think the graphics card is too important, as long as it is above average id say. go with nvidia to avoid problems. i have no issues with a 7800gt. the main issue is with the CPU, since x264 has a lot of fancy things going on. i have an AMD x2 3800 and things run ok. although you're going for something small and silent, i would make sure it isnt too slow, and you should probably go for a multi-core cpu.

you'll also want gigabit ethernet on both your fileserver and your htpc. i would think. if your router is only 10/100, you might as well test it with that first. you'd be very lucky to get a decent enough connection through wifi.

as for accessing it, you could look into elisa (although your pc will take a performance hit, and you might get juddering on your HD films) or just use your filebrowser.

Alright, i'll go with a higher end Nvidia card.  Just wondering if I need to get one that has some sort of x/h264 deconding on the card to help the cpu out.  Would a decent speed dual core be good like 3Ghz+?  I just picked up a Quad core that i'm going to use to build my server/encoding box.

Hmm.. as for the phyical connection to the TV, shoudl i go with a vga > component or vga >HDMI.

I was thinking that intially i'd just have a shared folder that the HTPC would access the movies on.  Now that I think about it, i dont want it to transfer the movie and play it.  I want it streamed.  If thats the case does that mean myth is my route?  If not is there a nice program i can use from the HTPC that will allow me to browse my library with IMBD info/covers pulled?

OH, forogt.  Another biggie is the sound card.  I want to hook it up to 5.1/7.1 surround so I need some sort of ouput that can do that.  I've had soundblaster cards in the past, would the newer ones cut it for digital sound output to reciever?

Sorry for the dis congruent comment, it was off the top rambling.

---

