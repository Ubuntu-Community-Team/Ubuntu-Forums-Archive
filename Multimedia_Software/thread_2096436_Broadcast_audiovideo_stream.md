---
title: "Broadcast audio/video stream?"
date: 2012-12-19
forum: Multimedia Software
---

### Post by Roasted on 2012-12-19
With the newfound information of our first child coming in August I've begun to see if I can somehow utilize some existing tech gear in the form of a fully functional baby monitor. I have several things available, such as an Atom based nettop, two Raspberry Pi's, and two wireless surveillance cameras. I've tried to tinker with how I would actually capture audio/video from a USB webcam and a USB microphone, but that didn't seem to work out too well. 

Part of me is thinking to hook up the nettop with Ubuntu and utilize something to broadcast the audio/video stream of the USB peripherals... I don't know... maybe through VLC? If VLC, I have no idea what I would even do to get started and push the stream. I would then utilize one of the Raspberry Pi's to act as the client in the bedroom so we have a continual feed of what's going on. I'm not entirely sure how do-able this is, but it's looking to be like the most optimal option because it sounds like the audio is pretty terrible on my actual surveillance cameras. At least in the case of having a dedicated microphone I can position it where it needs to be.

Anyway, still throwing ideas around, but like I said I'm drawing up absolutely nothing in reference to actually capturing the audio and video stream and broadcasting them together. Is this something that VLC can do? Or is there some sort of application to handle this?

Note - I don't need recording. I just want live in-sync video/audio feeds on my LAN.

Thanks everyone!

---

### Post by Roasted on 2012-12-20
Nothing?

---

### Post by BicyclerBoy on 2012-12-21
Cheapest low power soln could be an IP webcam & zoneminder.

There's zoneminder support in mythtv.

---

### Post by greatsirkain on 2012-12-21
How exactly are the wireless cameras received? do they plug into your tv? what connectors do they use etc? Just using the devices you've mentioned, if they use like phono leads or something it would be easy enough to use an audio splitter to merge the sound from a mic with video into a t.v scart socket then feed the output from the t.v into the netbook and broadcast it to your lan from there

---

### Post by Roasted on 2012-12-21
> **BicyclerBoy said:**
> Cheapest low power soln could be an IP webcam & zoneminder.

There's zoneminder support in mythtv.

I do have an IP Cam, but its audio support is pretty bad. I plugged in an extended mic, but I just hear noise in it, as if it's a continual bass line drowning out the rest of the sounds. I'm relatively certain it's the camera, because Foscam has gotten a bad reputation with usable audio from their cameras.

I've used ZoneMinder consistently, but I wouldn't really need to utilize ZoneMinder for this since I would just be monitoring, which I can do through the IP Cam with VLC. ZoneMinder would be nice if I was recording, but ZoneMinder requires quite a bit of horsepower to run the feeds (hence why I primarily use Motion these days... tutorial in my signature)

> **greatsirkain said:**
> How exactly are the wireless cameras received? do they plug into your tv? what connectors do they use etc? Just using the devices you've mentioned, if they use like phono leads or something it would be easy enough to use an audio splitter to merge the sound from a mic with video into a t.v scart socket then feed the output from the t.v into the netbook and broadcast it to your lan from there

The camera I have is wireless and hooks right into the LAN. Then if you get the full URL stream (which I dug up in the manual) you can pull the network stream for it through Totem or VLC. Totem seems to be quite terrible at doing this as it'll buffer for 10 seconds to play 1 second, then repeat 10, 1, 10, 1, etc. VLC will play it just fine. There's no TV or anything like that involved.

In our bedroom I'll be hooking up a Raspberry Pi along with a computer monitor. This will be playing VLC with the network stream. The only thing stopping me, literally, is the terrible audio on the IP camera. That's why I began to consider, maybe instead of wireless cam to R-Pi, I could do Ubuntu nettop to R-Pi instead. I just don't know how to take a video/audio stream from a microphone/webcam on system A and "publish" it to a stream available to system B... 

I suppose I can try my luck with a wireless indoor camera from another manufacturer, but it'd be cool to get something set up between two Linux boxes too.

---

### Post by Roasted on 2012-12-26
Hello! Still trying to crack this one. In theory this is simple, yet in practicality it seems significantly more difficult.

What do you think, fellas? How can I take the video stream from a USB camera and the audio stream from a USB microphone and "broadcast" them both, as one in sync across the network to another system on the LAN?

---

### Post by greatsirkain on 2013-01-18
sounds like you're doing cctv the hard way...I'd use a T.V :P
go on one of those live cam sites and ask one of the chicks tech questions...If nothing else it'd be funny for an hour or so

Couldn't you just use a web conferencing program, even skype or something to stream it?
For skype you could just create different accounts named after the rooms in your house?
I'm just brainstorming 'cause your question hasn't been answered

---

### Post by Roasted on 2013-01-18
> **greatsirkain said:**
> sounds like you're doing cctv the hard way...I'd use a T.V :P
go on one of those live cam sites and ask one of the chicks tech questions...If nothing else it'd be funny for an hour or so

Couldn't you just use a web conferencing program, even skype or something to stream it?
For skype you could just create different accounts named after the rooms in your house?
I'm just brainstorming 'cause your question hasn't been answered

I forgot to re-post here with some updates. I had originally been using an Intel Atom nettop with external USB HDDs as my backup server, but eventually this got old so I ended up building a low powered i3 server instead, which frees up the nettop. As a result, I found the perfect purpose for it.

I installed Lubuntu 12.04 on the nettop and set it to auto login, etc. FYI, Lubuntu is obnoxiously fast, even on an Atom. The nettop has built in wifi b/g/n, which has its benefits when streaming things wirelessly. I attached the nettop to a 17" LCD monitor via double sided tape, along with its power brick. That "poor man's all-in-one" system is going to have a home in our bedroom. Then in the baby room I'm going to have an indoor wireless camera with a microphone attached. Which camera? No idea - I'm still doing homework on finding a solid indoor camera that has exceptional audio. So far I can only base my opinion against my current Foscam, which is the definition of terrible.

At any rate, yeah things kind of changed a little bit, but this nettop plan is going to work out nicely. I'm trying to find a way to auto launch VLC to the stream, which would negate the point of having a mouse or keyboard attached, but for right now my "worst case scenario" plan is to leave a USB mouse plugged in on the base of the monitor so I can double click the VLC icon on the desktop and then launch the "recent" stream.

If anybody has any suggestions for an indoor camera with wifi b/g/n, IR, and great audio quality, I'm all ears!

---

### Post by dannyboy79 on 2013-01-18
i just picked up 2 logitech c260 webcam's from newegg for only $16/each. it does 720p video and the mic quality is good enough for me to use it for youtube let's plays and commentaries. however, not sure how good it is as far as how far away it can pick up audio from. you can use ffmpeg to capture and then to create a UDP stream or what have you so you can access that from your computer in your bedroom

---

