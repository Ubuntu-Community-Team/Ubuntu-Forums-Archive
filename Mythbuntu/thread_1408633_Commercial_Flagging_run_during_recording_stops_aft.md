---
title: "Commercial Flagging run during recording stops after a few minutes"
date: 2010-02-16
forum: Mythbuntu
---

### Post by Medieval Cow on 2010-02-16
Hey all,

So I finally went ahead and snagged myself an Apple TV to set up as a Mythbuntu frontend, allowing me to move my big old desktop out of the living room. It's much quieter, much nicer looking, and I'm very happy. The bonus to this is that I now no longer have to run the Frontend software on my poor little PIII 600 MHz machine I had been using. Since I'm using a Hauppage 350 card that handles all the MPEG2 encoding/decoding, the processor is mostly free and can be pretty useful despite how old it is. With the frontend software no longer occupying that CPU, I gave it a shot at allowing it to start commercial flagging when the recording starts, and it works beautifully.

Now, here's where the problem comes in. I'd like to be able to distribute the jobs between both machines, so things don't get bottlenecked if I'm recording a bunch of things. This is mostly working out ok! If my Apple TV starts flagging a recording after it's finished, or even a good bit into the recording, it works just fine. But! If it starts flagging as the recording starts, it seems to catch up to where the recording is after about 8 or so minutes, decides it's reached the end, and stops flagging with whatever it's found to that point. Then I have to either wait until the recording is done and re-run it, or go into the job queue and select the option to re-queue the job after a bit of buffer recording has been built up.

I've been searching like crazy, but I can't seem to find anyone else who's had this issue. I know people are running this on much more powerful hardware than my Apple TV, so if it really is just a problem of it "catching up" with the recording, I'd think it would happen with others as well. I'm only recording standard def stuff (all my little 600 MHz backend will handle, HD is a project for the future). Running Mythbuntu 8.04.1 on both machines. Any ideas on this? I want to be able to flag while recording, but I don't want to just disable commercial flagging on the Apple TV, because I want to share the load between the two machines, especially right now, as I'm recording tons of Winter Olympics programming. I've checked Mythbackend.log too, and didn't notice anything that seemed out of the ordinary in there, but I can post that if it'd help.

---

