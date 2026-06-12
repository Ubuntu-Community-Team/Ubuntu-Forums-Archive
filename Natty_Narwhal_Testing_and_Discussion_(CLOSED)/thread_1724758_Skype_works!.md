---
title: "Skype works!"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VMC on 2011-04-08
After reading WebUpd8 and finding a new Skype update for Linux, I thought I would try it out.

First I tried on Lucid. It worked. Then on my natty-unity. It needed a few more files, but it too worked! 

What I needed to do was go to system settings and adjust sound to point the mic to my webcam.

I usually call a friend in Japan everyday and I was having to use Windows to use Skype. Tomorrow I will see if any video/audio problems exists.

You can get the Skype beta [_here_]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/?cm_mmc=PXBL|0700_B6-_-linux-20110406"). I used 10.04+ 64 and then let natty download the 4 or 5 extra files.

---

### Post by cecilpierce on 2011-04-08
It worked before but the new one has no video.

---

### Post by VMC on 2011-04-08
> **cecilpierce said:**
> It worked before but the new one has no video.

It never really worked for me before. I could only see video. Now they both work.

Is your also amd64 or i386?

---

### Post by cecilpierce on 2011-04-08
> **VMC said:**
> It never really worked for me before. I could only see video. Now they both work.

Is your also amd64 or i386?

i386, I've tried it on 3 different installs and when I go to test video, camera don't turn on.
I installed cheese and the camera comes on and works OK.

---

### Post by VMC on 2011-04-08
> **cecilpierce said:**
> i386, I've tried it on 3 different installs and when I go to test video, camera don't turn on.
I installed cheese and the camera comes on and works OK.

Thanks, that explains it. I forgot that in the past when I tried Skype it was on a i386 system. Now that I think about it, this is the first time, I've tried on amd64. Even so, I still couldn't get audio input to work on my webcam. Now I can.

---

### Post by cecilpierce on 2011-04-08
> **VMC said:**
> Thanks, that explains it. I forgot that in the past when I tried Skype it was on a i386 system. Now that I think about it, this is the first time, I've tried on amd64. Even so, I still couldn't get audio input to work on my webcam. Now I can.

Well I don't use it much but it would be nice if I could, I'll try it on my grandsons win98 rig and see but its old as the hills and slow. :(

---

### Post by theanswriz42 on 2011-04-08
The audio seems to be a lot worse than before.

---

### Post by cecilpierce on 2011-04-08
> **theanswriz42 said:**
> The audio seems to be a lot worse than before.

my audio has all ways been crackly, it might be I don't have enough memory, even youtube bombs in and out.

---

### Post by theanswriz42 on 2011-04-08
> **cecilpierce said:**
> my audio has all ways been crackly, it might be I don't have enough memory, even youtube bombs in and out.

Luckily I hadn't had that problem until this release. I'll be rolling back which is pretty unfortunate.

---

### Post by VMC on 2011-04-08
I just got off the skype from Japan. We talked from almost 1 hour! That is a record for me, skype and linux. Usually it bombs out after just a few minutes. Also natty and unity crashes sometime in between that time.

I was nervously waiting for skype and/or unity to go belly up. They both held up fine. Either skype has improved their network a lot or this new beta is working better than the previous or my hardware or some combination thereof.

When you say your audio doesn't work well. Is that both ways or you hearing them or visa versa?

---

### Post by cecilpierce on 2011-04-08
@VMC

When it was working before upgrade it was doing it both in and out.

---

### Post by philbrown7 on 2011-04-13
I can't get Sykpe to see my web cam. Though other software can see it.  Also the sound in this new release is very garbled, unlistenable.  Whilst trying to fix the sound I have completely wreaked it so no sound at all now (which is actually better than the distorted noise before) but far from ideal. I have a Forte media 801 sound card which is recognized. In Alsamixer I have unmuted every box and reinstalled the alsa system. All to no effect. The only thing that works is I can hear my mic out my speakers.

---

### Post by rajeev1204 on 2011-04-13
> **philbrown7 said:**
> I can't get Sykpe to see my web cam. Though other software can see it.  Also the sound in this new release is very garbled, unlistenable.  Whilst trying to fix the sound I have completely wreaked it so no sound at all now (which is actually better than the distorted noise before) but far from ideal. I have a Forte media 801 sound card which is recognized. In Alsamixer I have unmuted every box and reinstalled the alsa system. All to no effect. The only thing that works is I can hear my mic out my speakers.


I suggest you follow the skype linux forums and post it there,the developer is at least reading it since its just released, you might get some help.

---

### Post by areteichi on 2011-04-13
> **philbrown7 said:**
> I can't get Sykpe to see my web cam. Though other software can see it.  Also the sound in this new release is very garbled, unlistenable.  Whilst trying to fix the sound I have completely wreaked it so no sound at all now (which is actually better than the distorted noise before) but far from ideal. I have a Forte media 801 sound card which is recognized. In Alsamixer I have unmuted every box and reinstalled the alsa system. All to no effect. The only thing that works is I can hear my mic out my speakers.

Have you checked this thread?
[http://ubuntuforums.org/showthread.php?t=1722876](http://ubuntuforums.org/showthread.php?t=1722876)

Check post #12 and a few more that follow.

Canonical has been applying a patch to fix this problem until this most recent version. I guess they haven't gotten around to applying for this version yet.

I remember I always had to use this workaround before Canonical started distributing their patched version through the partner repository.

---

### Post by Muskegman on 2011-04-13
I can also confirm Skype is working great for me on Natty Beta1 64bit.
The first time i installed it 2 weeks ago it failed to install. I reinstalled it a week ago and video and sound now works flawlessly.

Running a full install of Natty on an Acer Aspire 4520 AMD 64 Athlon X2 with nvidia GeForce 7000m

---

