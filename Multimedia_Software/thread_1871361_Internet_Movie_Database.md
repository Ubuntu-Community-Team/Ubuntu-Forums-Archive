---
title: "Internet Movie Database"
date: 2011-10-28
forum: Multimedia Software
---

### Post by bofak on 2011-10-28
Anybody got any idea why I can't play any of the clips on Internet Movie Database ( [www.imdb.com](www.imdb.com) )?  I'm running 11.04 with several media players installed, and can play YouTube just fine.  If you can play these clips, just tell me what they open with.

TIA   Bofak

---

### Post by inobe on 2011-10-28
works fine with firefox and flash, using kubuntu 11.10

do you get any messages/ errors?

---

### Post by bofak on 2011-10-28
> **inobe said:**
> works fine with firefox and flash, using kubuntu 11.10

do you get any messages/ errors?

No errors, etc.  Quite simply, nothing happens.  I'm running FF 7.0.1.

---

### Post by inobe on 2011-10-28
must be some adblock stuff, maybe even noscript?

---

### Post by bofak on 2011-10-28
> **inobe said:**
> must be some adblock stuff, maybe even noscript?
 
Don't have Adblock or Noscript.  Tried running FF in safemode with all addons disabled.  Tried unticking Block pop-up windows.  Still no go.

Could it be blocked by something in the Hosts file?  I use the MVPS hosts list.

---

### Post by enkay009 on 2011-10-28
It's hard to tell if your hosts file is preventing it. I can imagine a scenario where it would block it. 

Say on IMDB they need your browser to communicate with a third party ad server before sending you the video. With the MVPS hosts file, if that ad server is in the list, the request will never reach it and you will never see the video.

But I'm only guessing here. I have no way of knowing what kind of policy they have in place on IMDB.

---

### Post by bofak on 2011-10-29
> **enkay009 said:**
> It's hard to tell if your hosts file is preventing it. I can imagine a scenario where it would block it. 

Say on IMDB they need your browser to communicate with a third party ad server before sending you the video. With the MVPS hosts file, if that ad server is in the list, the request will never reach it and you will never see the video.

But I'm only guessing here. I have no way of knowing what kind of policy they have in place on IMDB.

Yes, I imagined the same scenario and tried with Hosts disabled, but still no success.

I made another discovery playing about with those clips on IMDB.  They invite the public to submit "demo reels", which you will find on certain pages.  Well, these play just fine.  And they have links to trailers etc on external sites, which of course also play OK.

So what is it with the clips on their own pages?  Do I have a Flash problem?  Here I'm getting out of my depth.  All I know is I have the latest Flash:  11-something.

Thanks, folks, for your suggestions so far.  I'm really determined to get to the bottom of this one (movie buff!)

---

### Post by enkay009 on 2011-10-29
I have a suspicion. But could you post a link to one of the videos you're trying to view but can't? I wanna try something.

---

### Post by bofak on 2011-10-29
> **enkay009 said:**
> I have a suspicion. But could you post a link to one of the videos you're trying to view but can't? I wanna try something.

Try these:

[http://www.imdb.com/video/imdb/vi2866585113/]("http://www.imdb.com/rg/VIDEO_PLAY/LINK//video/imdb/vi2866585113/")


[http://www.imdb.com/video/imdb/vi1775738393/]("http://www.imdb.com/rg/VIDEO_PLAY/LINK//video/imdb/vi1775738393/")


[http://www.imdb.com/video/screenplay/vi27592217/]("http://www.imdb.com/rg/VIDEO_PLAY/LINK//video/screenplay/vi27592217/")


[http://www.imdb.com/video/screenplay/vi4172744217/]("http://www.imdb.com/rg/VIDEO_PLAY/LINK//video/screenplay/vi4172744217/")

All I get in each case is a black rectangle; no start button, no spinning wheel . . .

---

### Post by inobe on 2011-10-29
i had a y.t. downloader app in the past, and could not watch hulu!

maybe disabling any dl apps, it could be some sort of drm on the page.

---

### Post by bofak on 2011-10-29
> **inobe said:**
> i had a y.t. downloader app in the past, and could not watch hulu!

maybe disabling any dl apps, it could be some sort of drm on the page.

A good idea and I'll keep it in the back of my mind, but no, I don't have any kind of downloader.

I just had the bright idea of trying it on my netbook (running FF on Ubuntu 10.04) and it won't play those clips either.  What I really need to know is whether other people can play them, using Ubuntu.  You said they played fine using Kubuntu.

Now I'm wondering whether location has anything to do with it.  I'm in Canada.  A few times when I took my netbook to Europe I couldn't play certain YouTube clips that I can play in North America.  But then I would get a message that this material is not available in my location.  In this case I just get nothing.  But it could indeed be some sort of drm.

---

### Post by bofak on 2011-10-29
Well, guys, the problem is solved.  You have to be in the US to play that stuff.

Other sites will give you an explanation.  IMDB apparently doesn't have the basic savvy!

Thx for your efforts to help.

---

### Post by maclenin on 2011-10-29
> **bofak said:**
> Try these:

[http://www.imdb.com/video/imdb/vi2866585113/]("http://www.imdb.com/rg/VIDEO_PLAY/LINK//video/imdb/vi2866585113/")


[http://www.imdb.com/video/imdb/vi1775738393/]("http://www.imdb.com/rg/VIDEO_PLAY/LINK//video/imdb/vi1775738393/")


[http://www.imdb.com/video/screenplay/vi27592217/]("http://www.imdb.com/rg/VIDEO_PLAY/LINK//video/screenplay/vi27592217/")


[http://www.imdb.com/video/screenplay/vi4172744217/]("http://www.imdb.com/rg/VIDEO_PLAY/LINK//video/screenplay/vi4172744217/")

All I get in each case is a black rectangle; no start button, no spinning wheel . . .

...hmmm...no problems from the UK with 10.04 via FF 3.6.23 (flash plug-in)....

---

### Post by moldaviax on 2011-10-30
just to confirm last users findings by adding that its ok from UK with 11.04 with FF4.01

M.

---

### Post by bofak on 2011-10-30
[QUOTE=moldaviax;11408639]just to confirm last users findings by adding that its ok from UK with 11.04 with FF4.01]

Yes, this sort of restriction, copyright protection, drm, or whatever, seems to vary from country to country and according to the type of media.  For instance here in North America we can't access a lot of BBC stuff.

After blaming Ubuntu, FF, Flash, my own hardware, etc etc, I found the answer when I got onto a friend's Windows machine and discovered that those IMDB clips wouldn't play on that either.  Then we clicked on an Amazon link on IMDB which wouldn't play but gave a message along the lines of "We have detected that your computer is not located in the US . . ."  Much more informative than a blank screen!

So if you can play those clips in the UK, thank your stars (or the teams of copyright lawyers).  Canada seems to have fallen through the cracks on this one.  I'm still annoyed at the amount of time I wasted on this yesterday, when a simple message from IMDB, like you get on other media sites,  would have clarified things.  After all, they are accessed all over the world (and are owned by Amazon too!)

Cheers, Bofak

---

