---
title: "Stuttering Video (VDPAU) Problems"
date: 2010-02-21
forum: Multimedia Software
---

### Post by daveshep on 2010-02-21
Gday, I've been trying to get my HTPC set up properly for a while now and it's time to ask for help... I'm using Mythbuntu (9.10).

I've got an Asus M4N78 Pro motherboard with 2GB of RAM, an AMD 5050e CPU and an Technisat Airstar 2 tuner card. The problem is the video, I'm just using the onboard Nvidia 8300 GPU and I've been playing around a lot with the TV Playback settings in MythTV but just can't get them right. I've got the HTPC connected to my 32" full HD (ie 1920 x 1080) Samsung LCD TV. At the moment i've got something like this: for SD video Decoder VDPAU, Renderer VDPAU and no deinterlacer. That works fine as long as I set the minimum CPU frequency at least 1.8GHz. I just can't get HD video (live or recorded TV, or video file eg DivX) to work properly using the same setup (ie VDPAU for both decoding and rendering). I get real bad stuttering where some frames get split up and the right hand part of the screen gets moved to the left and the rest of the screen gets shifted across to the right, kind of like you'd expect on an old video projector if the film and shutter aren't sync'd correctly, I can get HD television to display correctly if i use eg the standard decoder (ffmpeg?) with VDPAU rendering and one field deinterlacing. But with that setup i get bad stuttering when i try and watch HD (h.264) video files. i haven't checked but i'm guessing ANY h.264 video is bad... i've changed the BIOS setting on the Mobo to give 512MB of memory to the GPU, and now i don't know what else to try! what is annoying is that reading through various forums it seems that other blokes have got their systems working well with the same hardware! 

so i've got 2 questions... 

any suggestions for getting the video to work correctly? i don't really mind if the full HD television isn't full HD (i can use the TV's tuner to watch the cricket), so if my GPU simply isn't good enough i would be happy to drop the resolution of HD video...

and is there a better way to get the CPU frequency up without just setting the minimum allowed frequency higher? doing it that way means my CPU is running fast all the time, which aint so good for energy consumption, heat, cooling fan noise etc. the load on the CPU is so low when watching videos and using VDPAU decoding/rendering that even setting the "up threshold" to 1 doesn't seem to get the CPU frequency up high enough to stop the stuttering (when watching videos on the HTPC on the TV, with my laptop ssh'd to my HTPC if i manually set the minimum CPU frequency to 1.8GHZ, the stuttering disappears, set the minimum CPU freq back to 1GHZ and the stuttering returns).

---

### Post by jobba876 on 2010-03-05
im having stuttering problems with my NVIDIA graphics card on full screen mode, sounds like similar issues.  Have you found any answers?  I am going to look into your comments about cpu speed.

---

