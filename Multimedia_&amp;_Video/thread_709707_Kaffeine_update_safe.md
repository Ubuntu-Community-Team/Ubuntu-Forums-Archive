---
title: "Kaffeine update safe?"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by randcoop on 2008-02-27
Updates this morning (27 Feb) say that they will install kaffeine and kaffeine-gstreamer 0.8.6 and remove kaffeine-xine 0.8.5.  That worries me, since I don't use the gstreamer engine; I use the xine engine.  Does anyone know why it removes kaffeine-xine 0.8.5 but doesn't upgrade it to 0.8.6?  Is this update safe?  Will Kaffeine still work using the xine engine?  Does 0.8.6 have kaffeine-xine built in?

---

### Post by ajgreeny on 2008-02-27
Presumably you are using kubuntu and not ubuntu, or at least have the kubuntu-desktop installed as well as ubuntu-desktop.  I have kaffeine-xine on my ubuntu (not kubuntu) machine and no update is available to 0.8.6, but I don't even use totem-gstreamer, I use totem-xine instead.  If you prefer the xine engine, don't upgrade.

---

### Post by Tanker Bob on 2008-02-27
Don't upgrade kaffeine to 0.8.6 if you use the xine engine! I did, and kaffeine-xine 0.8.5 was automatically uninstalled with loss of all its supported codecs. I used "aptitude install kaffeine-xine" to reinstall the codecs, and aptitude was smart enough to offer to "downgrade" kaffeine to 0.8.5, which restored my system. Until kaffeine-xine is updated to 0.8.6, don't upgrade kaffeine.

---

### Post by james_xxx on 2008-02-28
I found this thread after also having upgraded Kaffeine. I also used aptitude to downgrade kaffeine and re-install kaffeine-xine, but after doing this, i have a number of videos that kaffeine will no longer play. 

Any suggestions?

---

### Post by randcoop on 2008-02-28
Thanks to all.  I use Kubuntu, but it's amazing that I had to post here (I posted on Kubuntu forums and got no responses) before finding the problem.

I'll of course hold off until kubuntu-xine 0.8.6 is available.

---

### Post by james_xxx on 2008-02-28
I do not know about any of you, but downgrading Kaffeine did not fix everything for me. There are still videos that will no longer play. Why the Kaffeine upgrade was put in the repos before a corresponding upgrade for kaffeine-xine is available is very hard to understand, and appears to just be more sloppiness.

If anyone has a suggestion on how to get kaffeine working again, I would be thankful.

---

### Post by meldroc on 2008-03-01
Any updates on this?  I have kaffeine downgraded to 0.8.5 since it'll remove kaffeine-xine if I upgrade.

When are we going to see a proper kaffeine-xine 0.8.6 in the repos?

Any idea how to get a hold of the maintainers?  Do they actually read these forums?

---

### Post by james_xxx on 2008-03-08
I continue to have the same issue, and can find nothing that mentions a fix for this. I don't know if this is an issue with Canonical, or with Medibuntu, but no matter how you look at it, someone was sloppy.

I have not filed a bug report, but I should look to see if something is there.

Also, right now in 0.8.5, subtitles have quit working since the last libxine upgrade. Gutsy has been a barrel of bugs.

---

### Post by Tanker Bob on 2008-03-08
The update is still not fixed here. Someone is apparently asleep at the switch. 0.8.5 is still working fine here, but I don't use subtitles.

---

### Post by james_xxx on 2008-03-16
Bump. 

Do so few people use Kubuntu that this just does not warrant attention?

---

### Post by Lantesh on 2008-03-16
Just to give some of you another option why not consider using 0.8.6 with the Gstreamer engine.  That's what I'm doing, and with all the proper codecs installed I have yet to find a video that I can't play.  It took a little doing in the beginning to get everything installed, but it works great.  If it matters I'm on regular Ubuntu, not Kubuntu.

---

### Post by Chareos on 2008-03-19
> **Lantesh said:**
> Just to give some of you another option why not consider using 0.8.6 with the Gstreamer engine.  That's what I'm doing, and with all the proper codecs installed I have yet to find a video that I can't play.  It took a little doing in the beginning to get everything installed, but it works great.  If it matters I'm on regular Ubuntu, not Kubuntu.

I've read about gstreamer being a nightmare about playing DVD (commercial encrypted) movies... is this still correct ?

---

### Post by spikyjt on 2008-03-19
Personally I'm a tad cheesed off about this. As previously mentioned, the update to Kaffeine should not have been released without a corresponding kaffeine-xine update. For an ordinary, non-techie user, this would be a totally confusing nightmare and make ubuntu/kubuntu look very poor quality. Although Kaffeine may well work with gstreamer, why would we want it? Most people using Kaffeine will be using KDE (and probably Kubuntu) and therefore xine. This does not bode well for the future either as KDE 4 uses xine entirely for its media backend, instead of arts. Please can a maintainer read this forum and act, or let us know how we can help make this work? This should never have happened.

---

### Post by spikyjt on 2008-03-19
Ooops - :redface: sheepish look.... ignore my above post. Just realised I had backports enabled for testing KDE4 packages... so the kaffeine upgrade was just a testing package. Sorry lovely ubuntu people all is forgiven... everything is still very professional and wonderful. No non-techie users should have this problem, as they shouldn't have backports enabled!

---

### Post by Tanker Bob on 2008-03-19
Yep, you're right. I had no problems with backports until now. I'm better now as well.

---

### Post by fabiomb on 2008-04-19
the same problem with backports, so now i cant play videos with audio on Kaffeine :mad:
i downgraded from 0.8.6 to 0.8.5 and still have de same problem

---

