---
title: "Newbie Questions before i build Mythbuntu box!"
date: 2009-01-25
forum: Mythbuntu
---

### Post by Sopranosmainman on 2009-01-25
Hi everyone.

i would like to build a mythbuntu box, but before i go out and start buying some hardware i have some questions.

I live in the US, and currently am a cable subscriber. I receive digital cable and HD through a cable box.

Now i know i need a tuner card in my box so that i can record tv. 

How does this work exactly? do wires have to come from my cable box to the tuner in the pc? if so what, and does this allow for the recording of HD programming?

Once i have this answer then i can start the building process and ask about tv tuner cards. Any and all help is much appreciated. Thank you!

---

### Post by crez79 on 2009-01-25
You can record from a cable box using firewire, but not the encrypted channels. How many channels that are encrypted vary from provider to provider and area to area, so there the only guarantees are the local channels. You can check the [silicon dust]("http://www.silicondust.com/hdhomerun/channels") website to get an idea of what channels would be available to you. I also recommend Silicon Dust's HDHomerun. 

To get encrypted content you would need a tuner. Most if not all tuners can capture from s-video, but I believe there is only one that can [capture in HD]("http://www.hauppauge.com/site/products/data_hdpvr.html"), but isn't totally supported by myth yet. So with the s-video/tv tuner arrangement, you can receive any channel your cable box does, but in 480p max resolution. The firewire capture method allows for whatever resolution it is sent in up to 1080i, as does the HDHomerun. 

I had a rough time getting firewire and the HDHomerun to work, but now that it is setup, it works great. There are many possibilities, some work better and are easier to setup than others. Before you buy I recommend you search around to find the exact model to get to minimize disappointment.

---

### Post by Sopranosmainman on 2009-01-26
> **crez79 said:**
> You can record from a cable box using firewire, but not the encrypted channels. How many channels that are encrypted vary from provider to provider and area to area, so there the only guarantees are the local channels. You can check the [silicon dust]("http://www.silicondust.com/hdhomerun/channels") website to get an idea of what channels would be available to you. I also recommend Silicon Dust's HDHomerun. 

To get encrypted content you would need a tuner. Most if not all tuners can capture from s-video, but I believe there is only one that can [capture in HD]("http://www.hauppauge.com/site/products/data_hdpvr.html"), but isn't totally supported by myth yet. So with the s-video/tv tuner arrangement, you can receive any channel your cable box does, but in 480p max resolution. The firewire capture method allows for whatever resolution it is sent in up to 1080i, as does the HDHomerun. 

I had a rough time getting firewire and the HDHomerun to work, but now that it is setup, it works great. There are many possibilities, some work better and are easier to setup than others. Before you buy I recommend you search around to find the exact model to get to minimize disappointment.

So i can only record in 1080p with a firewire cable... but may be able to record all channels. To record all channels i need a tuner card... but then i only get 480p max resolution. But how do i get the HD channels and all the channels that my cable box gets through the tuner? don't you need to put in the cable card, like the cable box has? i am confused. can you please clarify. And why would i need the s-video c able. shouldn't the tuner provide video!

i am now totaly confused. Thanks!

---

### Post by crez79 on 2009-01-26
Recording via firewire only requires a cable box with a firewire port (most if not all). It will capture whatever the source resolution is, up to 1080i, which is the most that is broadcast. Depending on your cable provider, some channels will be 5c encrypted. You can usually assume all premium channels will be encrypted. Some providers encrypt everything, some very little. This is digital cable.

Recording the encrypted content requires you to connect the output, that would normally be connected to your TV, to a tuner card with a video cable (either s-video (better) or composite (not as good)). Connecting this way will capture the resolution that is brodcast in, up to 480i. Connecting this way will allow you to record anything that you can watch from your cable box, but it won't be in HD. This way also requires a method of changing the channels on the cable box and this is usually done with via firewire or with an IR (infrared) blaster. This is digital cable converted to analog.

Another option is using just a tuner card. This would be the equivalent to hooking up cable straight to your TV. Whatever channels you would get on your tv you would get here. This is analog cable.

There is also another, very new and not quite supported method of recording. That is using the [Hauppauge hdpvr]("http://www.hauppauge.com/site/products/data_hdpvr.html"). This captures up to 1080i. Recording this way requires you to connect your cable box to this device with three component cables (these are the red, green, and blue ones). It allows you to record anything you can view from your cable box in HD. It is an ideal solution, but is still being implemented into myth, so it would require lots of patience and manual configuring. In time, I am sure it will be supported out of box, but not yet.

You may have heard of cable card tuners. These are windows only and must be purchased with a specific model of computer. They are not available aftermarket. From what I have heard their performance is spotty. They seem to work very well or not at all. But if you want to go with mythtv, these aren't an option until Cablelabs wises up and eases some of their ridiculous restriction.

Hope this makes a little more sense. There are many different options and the all have their pros and cons. Continue to do research and gather as much knowledge as you can and you will be much happier in the long run. This can be an expensive hobby and making quick uneducated purchases has already cost me a lot of pain, suffering, and loss of perfectly good beer money.:(

Edit: There is also the option to tune local broadcast channels with an antenna. These stations are usually in HD and don't require a cable subscription. Just a tuner card that is capable of receiving OTA (over the air), and an antenna are required for this.

---

### Post by Sopranosmainman on 2009-01-26
Thank you for your quick and very thorough response. It almost makes more sense just to buy tivo lifetime subscription lol. but the problem is i like challenges. what about HDMI cable? is that an option?


also is it easier to setup the HDPVR in windows?

---

### Post by crez79 on 2009-01-26
HDMI will work to deliver the video signal from your computer to your TV, but I don't think there are any hdmi capturing devices. HDMI in a non-compressed digital signal, so there is an insane amount of data.

The HDPVR should be easier to set up in windows, but I don't think it works with Windows Media Center yet. The best results are from the program that is from Hauppaugue. I am not really sure because I have never used it, I have just tried to keep an eye on it because it seems like it will be sweet when it gets more support.

SageTV supports the HDPVR i believe, but I am not too interested in leaving mythtv.

Tivo would be easier, but where's the fun in that? Mythtv has many more features than just recording tv. After all, there is a full blown computer running it. Ironically Tivo is out for your money, so they are much more restrictive. Mythtv is open source, and completely free, and there really isn't anything that you can't implement with the proper knowledge.

---

### Post by movieman on 2009-01-27
> **crez79 said:**
> HDMI in a non-compressed digital signal, so there is an insane amount of data.

It's only about 180MB/second, so a decent RAID could handle it; throw in an MPEG-2 or H.264 encoder chip and a single disk could. The real issue is that the HDCP folks won't sell HDMI chips to people who would use them to let people capture video, though I'm guessing the encryption will be broken before long if it hasn't been already.

---

### Post by Sopranosmainman on 2009-01-27
Thanks for your reply's guys. 

Is there a guide to getting the HDPVR working in mythbuntu?
if so can you point me in the right direction. 
Also, right now its limited to 1080i.. but i think thats because thats the highest that is broadcasted right now... if it ever gets to 1080p, will this device support it?

from the look of it, i dont think it can because it doesnt have an hdmi port. I think with the hd cables  themselves, thats limited to 1080i?

---

### Post by crez79 on 2009-01-27
> **Sopranosmainman said:**
> Thanks for your reply's guys. 

Is there a guide to getting the HDPVR working in mythbuntu?
if so can you point me in the right direction. 
Also, right now its limited to 1080i.. but i think thats because thats the highest that is broadcasted right now... if it ever gets to 1080p, will this device support it?

from the look of it, i dont think it can because it doesnt have an hdmi port. I think with the hd cables  themselves, thats limited to 1080i?

There is a wiki [here.]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR") Component cables can carry 1080p. I doubt they are going to brodcast any higher that 1080i any time soon. The advantage of HDMI is it includes audio and video in one cable. It is not necessarily required for 1080p.

---

