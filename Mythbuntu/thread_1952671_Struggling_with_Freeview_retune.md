---
title: "Struggling with Freeview retune"
date: 2012-04-04
forum: Mythbuntu
---

### Post by NautiusMaximus on 2012-04-04
Today is the day when I was supposed to retune all my Freeview channels.

I attempted to rescan my channel list at first. The channels were all still visible when I'd done this, but many of them wouldn't work. Channel information and what was playing would be displayed, but only on a blank screen. No actual TV programmes were displayed (this is the same behaviour as I had before I attempted to retune).

On browsing through these forums, I saw a suggestion to delete the video source in the MythTV backend set up and start again.

So I did.

Now I just can't get any channels at all. The channel scan simply doesn't find anything.

I assume I'm missing something obvious here. Any ideas where to start looking?

I'm using Mythbuntu 10.04 with a Hauppauge WinTV-NOVA-T-500 tuner.

Many thanks
NM

---

### Post by nickrout on 2012-04-05
Freeview where? There is more than one market with a service called Freeview.

---

### Post by NautiusMaximus on 2012-04-05
Sorry, of course there is. 

Freeview in the UK, specifically in London.

---

### Post by nickrout on 2012-04-05
> **NautiusMaximus said:**
> Sorry, of course there is. 

Freeview in the UK, specifically in London.

You have probably noticed this thread by now anyway, but just in case you haven't, does this post help?

[http://www.gossamer-threads.com/lists/mythtv/users/511029#511029](http://www.gossamer-threads.com/lists/mythtv/users/511029#511029)

---

### Post by NautiusMaximus on 2012-04-11
Thanks Nick, I hadn't seen that post, and it does contain much information that's relevant to my situation.

Unfortunately, however, it didn't solve my specific problem. My problem was not about when I needed to retune, it was about the mechanics of retuning, which didn't seem to work.

Anyway, I figured it out in the end. If anyone else is having similar problems, this is what I did.

Just to recap, after my initial attempt to rescan channels failed, I deleted the video source altogether and inserted a new one so I could do a fresh scan (I found this procedure recommended on one thread here, can't remember which one now). That failed miserably. Scanning for channels didn't find a single channel.

At that stage, I restored from a mythconverg database backup to get me back to where I was before I deleted anything.

This time round, rather than deleting the whole video source, I kept the existing video source and deleted all the channels. This left me with an existing video source and an empty channel list.

From that position, I scanned for channels again, and everything just worked! :)

Not sure why inserting a new video source didn't work. I suspect that some parameter of the video source was different to what it was before and that was screwing things up. But really, I have no idea.

---

