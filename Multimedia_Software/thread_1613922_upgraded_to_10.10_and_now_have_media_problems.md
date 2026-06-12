---
title: "upgraded to 10.10 and now have media problems"
date: 2010-11-05
forum: Multimedia Software
---

### Post by Basheequa on 2010-11-05
Hey guys,

I had Ubuntu 10.04 and recently upgraded to 10.10

Before the upgrade I could watch videos and listen to music on my desktop just fine. Now though things are so great.

After the upgrade I try to view a video on my hard drive... no sound comes through and the video lags heavily even though the time slider is going smoothly. When i try listening to music, no sound happens even though the slider is moving smoothly.

I tried removing Movie Player and re-installing it but the issue remains. None of this happened before the upgrade.

Thanks for any help in advance.

---

### Post by garvinrick4 on 2010-11-05
> **Basheequa said:**
> Hey guys,

I had Ubuntu 10.04 and recently upgraded to 10.10

Before the upgrade I could watch videos and listen to music on my desktop just fine. Now though things are so great.

After the upgrade I try to view a video on my hard drive... no sound comes through and the video lags heavily even though the time slider is going smoothly. When i try listening to music, no sound happens even though the slider is moving smoothly.

I tried removing Movie Player and re-installing it but the issue remains. None of this happened before the upgrade.

Thanks for any help in advance. Just for the sake of it try vlc media player to
see if that works fine. It can play anything you throw at it. Looks like just a little unobtrusive little media player but it is big inside. Copy and paste this in terminal:
```
sudo apt-get install vlc
```
Let me know if does the job:
If you do want to remove and reinstall a package always clean your cache out or you get the same package back.
```
sudo apt-get clean
```
Go's out to repositorys and fetches a new package now, not one in your cache in system.

---

### Post by Basheequa on 2010-11-05
> **garvinrick4 said:**
> Just for the sake of it try vlc media player to
see if that works fine. It can play anything you throw at it. Looks like just a little unobtrusive little media player but it is big inside. Copy and paste this in terminal:
```
sudo apt-get install vlc
```Let me know if does the job:
If you do want to remove and reinstall a package always clean your cache out or you get the same package back.
```
sudo apt-get clean
```Go's out to repositorys and fetches a new package now, not one in your cache in system.


I downlowded VLC and the video plays on it well even, however it seems every now and then the media hic-ups. As in the video and audio will lag for a split second then continue playing.

Could this be a problem with my crappy system? I have only 256MB of RAM. Is the video lagging because I upgraded the system and now the RAM has to work more on keeping the OS running leaving less for other stuff?

---

### Post by garvinrick4 on 2010-11-07
> **Basheequa said:**
> I downlowded VLC and the video plays on it well even, however it seems every now and then the media hic-ups. As in the video and audio will lag for a split second then continue playing.

Could this be a problem with my crappy system? I have only 256MB of RAM. Is the video lagging because I upgraded the system and now the RAM has to work more on keeping the OS running leaving less for other stuff?
256 meg of Ram is at the lowest for running Ubuntu. I imagine you will get quite a few hic-ups as you call them in that range of installed RAM.

---

### Post by Basheequa on 2010-11-09
> **garvinrick4 said:**
> 256 meg of Ram is at the lowest for running Ubuntu. I imagine you will get quite a few hic-ups as you call them in that range of installed RAM.

Heh well sorry, wasn't sure what to call them. But I'm thinking it's the upgrade that's causeing the lag. After all it didn't do it before the upgrade.

---

