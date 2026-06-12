---
title: "How to setup to stream live from firewire camera"
date: 2020-04-02
forum: Multimedia Software
---

### Post by brianthefolksinger on 2020-04-02
Ubuntu 18 LTS
Ubuntu Studio
HP elitebook

Hello, sorry am not at all expert, but have been getting under the hood when I had to, from the time when you had to, to make it work at all, 20 years ago and more. Just been using it since then, make it work, focused on the music, forgotten a lot, and things have changed a lot. Lots of new apps etc. But tasks still the same. So detailed instructions needed for terminal work, though am familiar with working in terminal, very rusty. Mostly looking for standard solutions, but work-arounds ok. I have been searching for a solution for a couple days, when I have time, but only crude but effective at this point. And I don;t mind asking for help, while I keep just making something work.

I'm a performer, and trying to start live streaming shows from home because of present shutdown. Streaming is pretty basic these days, so must be some standard solutions, but have been spending hours searching posts and synaptic trying to find something, and hard to tell, and well, can't get it to work yet, except with ugly work-arounds. Have been working with digital video for 20 years with Linux, but never tried live streaming, or actually, did, but someone else handled it, while I played. Now need to DIY.

Biggest problem seems to be that I have a old pro ieee1394 video camera, Sony PD-150, which I have still working through dvgrab and Kino to capture , and then mix and process files in various video editors, though only Kino sees the camera. Might be able to get the other editors to work for capture, but well, Kino or dvgrab did the job so why bother, simple enough.

Searching w/ synaptic I found OBS, and VLC , which will stream, and seem to be the sort of simple basic interface I'm looking for, but they both are V4Li and don't see my camera, though found a utility dv4l that is supposed to patch ieee1394 into V4Li, but seems to refer to dv1394 rather than raw1394.  Maybe it would be worth it to use the older module. somehow, or perhaps I just need to add some hmm forgot technical name, but redirect old file names apps are looking for to new file name in dev/ , camera showing up as dev/fw1 I believe.

OBS seemed like an easy standard streaming interface (so does VLC), all I need, built in presets for probably wherever I upload to. I have an ugly workaround by putting Kino in capture mode on one monitor and then using screen capture as a source in OBS, on the laptop screen, move the kino window around the monitor to crop off a lot of the Kino toolbars, and well, have a live stream from camera to OBS. Crude but hopefully effective. and though no sound, but I can make a workaround with that, AV cables from camera to Mic/Aux input on laptop, o maybe use Jack to route the audio from the firewire to either mic/aux or the Jack input in OBS source. Though haven't used Jack, yet, or any of the newer audio software in Ubuntu studio. Had a setup that worked recording, was just starting to look into the new stuff available, and Ubuntu studio.

Anyway, don't know if anyone can suggest a simpler solution, eg a streaming app that will recognize my camera, work from raw1394. There might be lots of apps capable of uploading the feed from the camera, but not obvious in Synaptic description. Or a standard work around for OBS or VLC. Even if I have to point ti to the right location, umm dev/fw1,  Or another way to bring the raw1394 into OBS. Or output dvgrab to some simpler uploader, saw something called baresip, but not sure if SIP is appropriate. Again, learning curve, and I mostly justneed to make something work. Almost have it with my workaround, ugly, but effective looks like.I am not sure if I could pipe the output from dvgrab, in an appropriate format, into OBS, or VLC, even just into an xwindow, and use OBS source : window, or screen again, but without having to try to crop kino toolbars.

Thanks for any suggestions or instructions for a work around, will get back to just making it work.. AV cable and adapter into the mic/aux input from the camera and I should be good to go. Actually, probably put my big diaphram mike (camera mic not great and camera motors old and loud, though they shut down after camera idle long enough) into the xlr of the camera or the mixer to the mic/aux. Crude but effective, good enough! Get it done and start playing. Be out on the street this weekend, only venue in town.

Peace!

---

### Post by colin.williams.seattle on 2020-04-03
Hello, if you can display video from the camera using one of the techniques in the accepted answer, you can then use screen sharing software to share that window as mentioned in the second answer: 

[https://unix.stackexchange.com/questions/3304/how-do-i-watch-my-webcams-feed-in-linux](https://unix.stackexchange.com/questions/3304/how-do-i-watch-my-webcams-feed-in-linux)

---

### Post by colin.williams.seattle on 2020-04-03
Also alternatively can just use a smartphone...

---

