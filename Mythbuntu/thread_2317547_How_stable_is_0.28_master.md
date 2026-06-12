---
title: "How stable is 0.28 master?"
date: 2016-03-17
forum: Mythbuntu
---

### Post by JamesNorris on 2016-03-17
As my BD collection grows and storage capacity plummeting, I become increasingly tempted my h.265, which is only in 0.28.

I cannot use an external player through Myth, as I'm using storage groups (please do tell me if this has changed), so I'm wondering about 0.28.

What do people say?

---

### Post by melben on 2016-03-17
I'm not really a power user, I only use Myth for recording and playing back dvb. For playback of videos I usually use Kodi.

0.28 has been generally stable for me since I upgraded a couple of weeks ago. There are a couple of things I have noticed to be aware of:

1. Every time there is an update for 0.28, the bind address in /etc/mysql/conf.d/mythtv.cnf gets commented out. If you reboot (or probably restart mysql) before fixing this, the frontend won't be able to connect and sometimes gets stuck in an annoying restart loop. Fortunately it's very easily fixed from the Mythbuntu Control Centre - in the Mysql section change the Master Backend Role back to Enabled.

2. This may not affect you, but I have found the OpenGL Normal profile to not work when the Paint Engine is set to Auto. Setting the Paint Engine to OpenGL 1 fixes this. I have logged a bug for this.

Ben

---

### Post by yonkiman on 2016-03-19
I'm also just a user (not a dev), but I've been using 0.28 fixes (on 14.04) for a LONG time - at least a year, could it be two?  I update every week or two, and it's run great - I've maybe had one update that caused problems but it was fixed a day or two later.

So I'd imagine 0.28 master will work fine for you.

---

### Post by JamesNorris on 2016-03-23
Brill, I'll take the plunge, then.

---

### Post by mattlach on 2016-03-24
> **melben said:**
> I'm not really a power user, I only use Myth for recording and playing back dvb. For playback of videos I usually use Kodi.

Ditto.

I have a dedicated backend that is used solely to schedule and record live TV and present the mpeg2 streams to the frontends via network for playback.

All of my frontends run Kodi with Janbar's MythTV plugin.   The MythTV plugin works excellently in Kodi for TV recording and live playback.   Everything else is played directly through Kodi from my NAS, and doesn't involve MythTV at all.

If your mythtv backend also serves as your storage server, you could just install the NFS server, and set up a share which the frontends can connect to.

I don't wind up using the MythTV frontend at all.

---

