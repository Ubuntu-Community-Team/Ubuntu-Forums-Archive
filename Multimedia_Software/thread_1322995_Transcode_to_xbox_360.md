---
title: "Transcode to xbox 360"
date: 2009-11-11
forum: Multimedia Software
---

### Post by whaase on 2009-11-11
I'm pulling my hair out trying to get something working for my 360. Here is my setup.



Ubuntu server 8.04LTS
Core2Duo E7800
2 gigs ram
Raid 5 w/7TB of storage



HTPC upstairs
Core2Duo E7800
2 gigs ram
160 HD
Running Media Portal for a front end.



Downstairs

Xbox 360



Now, my media consists of a mix of avi and mkv. I used avi when I ripped movies we wanted to keep, but were not really worth a high quality rip.



I used MKV for all my bluray rips. Works awesome and great quality.

For my machine upstairs I just use shares from the server. For the xbox I need to transcode all the mkv's. I'm currently using tversity and it works, but I want to do this from the server and utilize it a lot more.



I tried ushare, but it doesn't transcode the mkv's



I tried mediatomb and I couldn't get it to transcode on the fly.



I read in one place that PS3 media server works for the 360 and transcodes on the fly. Problem is, my server is a headless box with no gui lol



Anyone have a suggestion/ideas how I can do this? I've googled for hours and seem to run into dead ends. I don't want to convert my mkv's to a lesser quality. It would look crappy on my htpc upstairs lol. There must be a way?

Thanks!

---

### Post by mr_muddle on 2009-11-11
I think [FUPPES]("http://fuppes.ulrich-voelkel.de/features/") should do what you want. It certainly works for me, but I've not tried it on Ubuntu yet. I've used it with my NAS (freeNAS) to transcode various video & audio to the 360 and it's worked with 90% of stuff I've thrown at it. The webGUI isn't the most awesome, but it does work and I'm using an old version - perhaps it's even improved. I'm not sure if it will transcode .mkv on the fly but it's worth a look.

[Here]("http://cantthinkofa.com/platforms/linux/remuxing-mkv-for-the-xbox-360.html/comment-page-1#comment-181") could be a solution? But there are comments mentioning that the 360 has issues playing back files > 4GB which doesn't sound too good for Blu-Ray :(

---

### Post by whaase on 2009-11-11
Thanks, ill read up on fuppes.

I wonder if you are transcoding a video on the fly, does that count towards the 4gig limit?

---

### Post by Shhnap on 2009-11-11
I agree, try and install fuppes but build from source if you can and go from there. You may have a few problems because fuppes is a little old. Improvements are hopefully on their way.

---

### Post by whaase on 2009-11-12
> **Shhnap said:**
> I agree, try and install fuppes but build from source if you can and go from there. You may have a few problems because fuppes is a little old. Improvements are hopefully on their way.

Well, I got it all installed using a guide on here. I was able to get my videos working (avi's). But I couldn't get my mp3's working.

I would have thought by now someone would have come out with something fairly simple to set up. I've been using linux for 11 years now, and this is the first thing I've really had to fight with.

I guess ill stick with tversity for now and hope that someone will make something that doesn't require a masters degree to configure.

---

### Post by Shhnap on 2009-11-12
You just have to run the ./configure script with the audio encoding options in order to get your mp3's working. Just type in ./configure --help and install all of the -dev packages for the audio encoder/decoder software that you want then configure and make again and it should all work. It works just fine for me, I can play my mp3's through my XBox. If you still don't manage to do it then just send me a PM, it is not our aim to make it difficult to configure. (if it was a package then there would be no problems at all; packages usually hide all of this from you)

---

