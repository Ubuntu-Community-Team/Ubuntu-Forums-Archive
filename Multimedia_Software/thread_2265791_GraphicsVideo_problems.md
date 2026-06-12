---
title: "Graphics/Video problems"
date: 2015-02-17
forum: Multimedia Software
---

### Post by jaguar072 on 2015-02-17
I recently re-installed Ubuntu 12.04. I had tried installing ver. 14.04, but that ran much too slowly - so I decided to switch back. Whereas the video was fine (in 12.04) before the switch, it is now very slow and crashes often (media only) - and looks like the attached screen grab, using any media sites, live streaming, etc. Adobe Flash Player is up-to-date. What would cause the video display to present itself like this, and how can it be changed? Thank you.

---

### Post by David_LIMB on 2015-02-18
Quite the same problem here ... I know it's not my Laptop (hardware) as the same videos were absolutely fine when I was running WINDOWS7 (which was overall slow and constantly asking to pay for upgrade). But since I installed Ubuntu (14.04) can't read them properly very slow, audio out of sync, youtube embeded vids freeze in any browser ... I'm running the CPU monitor and it seems that when running some videos (VLC or Mplayer) data usage goes through the roof. Never experienced that with Windows on the very same machine. what can I do ?

---

### Post by mc4man on 2015-02-18
> **jaguar072 said:**
> I recently re-installed Ubuntu 12.04. I had tried installing ver. 14.04, but that ran much too slowly - so I decided to switch back. Whereas the video was fine (in 12.04) before the switch, it is now very slow and crashes often (media only) - and looks like the attached screen grab, using any media sites, live streaming, etc. Adobe Flash Player is up-to-date. What would cause the video display to present itself like this, and how can it be changed? Thank you.

Haven't used 12.04 in a long time nor ever with similar hardware so can't really help.
What may be useful to others is to know - did you re-install using your old image or the latest (12.04.5
This may show - 
```
lsb_release -a && uname -r
```

If your issue is the new 12.04.5's kernel & or mesa libs & you can't find a solution then most of the previous images from 12.04  thru 12.04.3 are here - maybe try an earlier one. ( I'd use 12.04.1 over 12.04 if going back that far, you'd need to pick thru carefully as there are numerous available..

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

The current 12.04 releases are here - 12.04.4 & 12.04.5
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

---

### Post by Portaro on 2015-02-18
Maybe reinstall the flash - player for ubuntu can solve the problem is an idea that I suggest, there are other users with this problem that I remember with related similar problems in past on 12.04, and Debians. Try reinstall [https://launchpad.net/ubuntu/+source/flashplugin-nonfree](https://launchpad.net/ubuntu/+source/flashplugin-nonfree)

---

### Post by jaguar072 on 2015-02-18
> **mc4man said:**
> Haven't used 12.04 in a long time nor ever with similar hardware so can't really help.
What may be useful to others is to know - did you re-install using your old image or the latest (12.04.5
This may show - 
```
lsb_release -a && uname -r
```

If your issue is the new 12.04.5's kernel & or mesa libs & you can't find a solution then most of the previous images from 12.04  thru 12.04.3 are here - maybe try an earlier one. ( I'd use 12.04.1 over 12.04 if going back that far, you'd need to pick thru carefully as there are numerous available..

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

The current 12.04 releases are here - 12.04.4 & 12.04.5
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Thank you, Mac4Man, for your responce. For this computer, I had actually re-installed ver 12.04.4  - from the original disk I made quite a while ago.. and as mentioned had encounterd no previous problems with video using the software as originally installed - and until I endeavoured the ill-fated switch to 14.04. As I have downloaded all the updates for this version and confirmed Adobe Flash Player is also the most recent version, is it advisable to re-install using the hyperlink you kindly provided - or will that just be retracing my tracks?
 I know I never had 12.04.5 on this machine - and hesitate to go anywhere in advance of 12.04.4 (simply because this old computer just doesn't have the horses to make a go of it). 
Is it possible that I had downloaded something or changed settings (at some time - although I really don't recall having done) in Ubuntu to sort out the graphics/video?
I don't think it was anything that was "fixed" downloading Ubuntu's standard updates (I d/l them all.. "suggested" as well as "important" ones).
I do seem to recall encountering this issue with this setup.. initially when I switched this computer to Ubuntu (12.04.4) from Windows XP many months ago. The graphics had always been fine using XP too, btw... so I'm sure the hardware isn't wonky.
Thank you once more. Still working at this.. I will post any resolutions that might find me.

---

### Post by jaguar072 on 2015-02-18
> **Portaro said:**
> Maybe reinstall the flash - player for ubuntu can solve the problem is an idea that I suggest, there are other users with this problem that I remember with related similar problems in past on 12.04, and Debians. Try reinstall [https://launchpad.net/ubuntu/+source/flashplugin-nonfree](https://launchpad.net/ubuntu/+source/flashplugin-nonfree)

Thank you, Portaro. I will have a go at this.. I seem to have been dancing around this (the Flash Player "theory") anyway - might as well give it a shot.

---

### Post by jaguar072 on 2015-02-19
> **jaguar072 said:**
> I recently re-installed Ubuntu 12.04. I had tried installing ver. 14.04, but that ran much too slowly - so I decided to switch back. Whereas the video was fine (in 12.04) before the switch, it is now very slow and crashes often (media only) - and looks like the attached screen grab, using any media sites, live streaming, etc. Adobe Flash Player is up-to-date. What would cause the video display to present itself like this, and how can it be changed? Thank you.
Following-up and replying to my own question - not sure if this is the correct way to this, but it gets the job done:
I was going to persue this further this morning - when I was prompted by Ubuntu, upon start-up, to download new updates - which I did, figuring I would renew efforts at resolving the graphics/video issue (including attempting to re-install Flash Player) after doing that.
Long story short, the video amazingly worked perfectly after the downloads were done (see screen-grab, below). Apparently, Ubuntu get 'round to addressing this issue in the course of updates - since I had done absolutely nothing to proactively "fix" the problem. That's why I didn't remember what I had done concerning this issue previously (my initial incarnation of 12.04.4)... 'cause I had actually done nothing. :-|
So.. in my case, anyway - the issue kind of resolved itself. Hope this is helpful to anyone experiencing this problem. Hang in there.. it gets better (probably). O:)

---

### Post by Portaro on 2015-02-19
Nice , this means that UBuntu updates provided by community , already have a patch to solve the problem (your and other users with same problem) , maybe the problem is on flash player, and in 12.04 video performance is less that in 14.04 in vlc and mplayer its a problem caused by some things like plugins for videos, new implementation of ffmpeg substitues etc.

I see that in 12.04 my videos stops in some formats like wmv and in 14.04 works with more efficiency. 

And of corse , graphic performance change if yo uhave or not a good support to the video card.

---

