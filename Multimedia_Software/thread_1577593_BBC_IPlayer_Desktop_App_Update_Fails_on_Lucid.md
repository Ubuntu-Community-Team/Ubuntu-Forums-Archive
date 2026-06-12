---
title: "BBC IPlayer Desktop App Update Fails on Lucid"
date: 2010-09-19
forum: Multimedia Software
---

### Post by jbrice on 2010-09-19
Recently (after the new version iPlayer was released I guess) I have been unable to download IPlayer content. On going to download, the IPlayer screen offers to install the IPlayer Desktop app, tries to install Air (already installed via Software Centre) and fails with a message like "A download error occurred. Try to download again?". Repeating just loops around to the same error message.

This happens on both my PC and laptop - both running Lucid. Have tried uninstalling the Iplayer app and Air, but still the same happens. Any suggestions, or do I have to wait for the Beeb to get it sorted?

TIA

---

### Post by jbrice on 2010-09-20
Plenty of people have looked at my post, but no replies.
Am I the only person having this problem?

---

### Post by Peter09 on 2010-09-20
The BBC Iplayer is crap - I've manged to install it three or four times but it is completly unstable (64 bit makes it worse). At the moment I have it installed but it refuses to download anything.

---

### Post by jbrice on 2010-09-20
> The BBC Iplayer is crap - I've manged to install it three or four times but it is completly unstable (64 bit makes it worse). At the moment I have it installed but it refuses to download anything.

Thanks for that thought. My systems are 32-bit - so that's not an issue here. In fact IPlayer downloads have worked pretty well for me up until now.

---

### Post by DominicF on 2010-09-20
Hi,

Are you able to play/watch content online?  I am unable to do this, I've tried a few times now and it seems to hang for me after seeing the initial bbc logo/theme.

Thanks.
Dom.

---

### Post by jbrice on 2010-09-20
> **DominicF said:**
> Hi,

Are you able to play/watch content online?  I am unable to do this, I've tried a few times now and it seems to hang for me after seeing the initial bbc logo/theme.

Thanks.
Dom.

Yes Dom, ordinary online playing is fine. So must be something different to your case. 

Digging deeper, I have persuaded Opera to download the IPlayer .AIR application and have installed it. IPlayer Desktop now works fine, and downloads programmes if I use Opera or Chromium to select the downloads. However F.fox still insists on trying to install Air and IPlayer Desktop instead of starting a download.

Going to the IPlayer install page [http://www.bbc.co.uk/iplayer/install]("http://http://www.bbc.co.uk/iplayer/install"), both Opera and Chromium show IPlayer as installed. For the same page F.fox tries to start up the install sequence.

So the root problem is that F.fox cannot detect Air/IPlayer as being installed. Is it the BBC's code or my PCs? Now I have IPlayer Desktop working, I think I'm going to leave it at that - it will get sorted in time whatever the cause.

---

### Post by imbjr on 2010-09-20
> **jbrice said:**
> Recently (after the new version iPlayer was released I guess) I have been unable to download IPlayer content. On going to download, the IPlayer screen offers to install the IPlayer Desktop app, tries to install Air (already installed via Software Centre) and fails with a message like "A download error occurred. Try to download again?". Repeating just loops around to the same error message.

This happens on both my PC and laptop - both running Lucid. Have tried uninstalling the Iplayer app and Air, but still the same happens. Any suggestions, or do I have to wait for the Beeb to get it sorted?

TIA

I find my connection not good enough to use iPlayer directly, so I use this to download the video:

[http://po-ru.com/projects/iplayer-downloader/](http://po-ru.com/projects/iplayer-downloader/)

---

### Post by jbrice on 2010-09-21
> **imbjr said:**
> I find my connection not good enough to use iPlayer directly, so I use this to download the video:

[http://po-ru.com/projects/iplayer-downloader/](http://po-ru.com/projects/iplayer-downloader/)

Thanks - that could be useful.

---

### Post by cefn on 2010-11-28
I experienced exactly the same thing. Didn't go through an Opera install yet, as that seemed like overkill for what should be a fixable problem, but thanks for the suggestion.

In the end I found that after disabling the Flashblock plugin, the install in Firefox worked fine again. I don't know what domain the package is coming from, but it's not the BBC as that's on my whitelist.

If you are running Flashblock, try disabling it and revisiting the BBC iPlayer install page again. I'm back up and running on Lucid.....AAARGH

Spoke too soon. This time the install succeeded, (previously I couldn't install), but downloads are still failing with a redirect to the install page.

Again spoke too soon. (you're getting a minute by minute update). After yet another Firefox restart, it recognises that iPlayer is installed and continues with the download. 

Sometimes iPlayer crashes and stops downloading for no reason, but I can live with that compared to nothing at alll.

---

### Post by Richy_303 on 2011-02-25
> **jbrice said:**
> Recently (after the new version iPlayer was released I guess) I have been unable to download IPlayer content. On going to download, the IPlayer screen offers to install the IPlayer Desktop app, tries to install Air (already installed via Software Centre) and fails with a message like "A download error occurred. Try to download again?". Repeating just loops around to the same error message.

This happens on both my PC and laptop - both running Lucid. Have tried uninstalling the Iplayer app and Air, but still the same happens. Any suggestions, or do I have to wait for the Beeb to get it sorted?

TIA

Having the same problems but think I may have got around it.  The problem appeared in FF and Chrome.  Like you I also installed Air and use Balsamiq without any probs, so know Air is installed okay.

After reading a few more posts I disabled ABP Adblock Plus in FF and the BBC web site then "agreed" to install desktop iPlayer without the Air loop issue.

As I type I have two programming downloading, however I had to use Chrome to queue the downloads as FF took my back to the iPlayer installation page!  FF is still having problems with blocking but I'm wondering if this is due to a clash with iPlayer and add-ons rather than FF itself?

BTW running 64bit Maverick

PS - may have spoke too soon. First download completed.  System hang! Couldn't get it back no matter what, so hard reset (flash back to M$ days - ouch!).  Completed download refuses to play, plays the ident then nothing!  Second download in progress .....

---

### Post by imbjr on 2011-02-26
> **imbjr said:**
> I find my connection not good enough to use iPlayer directly, so I use this to download the video:

[http://po-ru.com/projects/iplayer-downloader/](http://po-ru.com/projects/iplayer-downloader/)

There is also get-iplayer in the repositories. This can act as a PVR.

---

### Post by SilverWave on 2011-03-12
> **imbjr said:**
> There is also get-iplayer in the repositories. This can act as a PVR.

Wow this looks good!
```

get_iplayer -h

get_iplayer
...
820:    The Sky at Night - 700 Not Out, BBC One, Factual,Science & Nature,TV, default
...
INFO: 960 Matching Programmes

get_iplayer -g The Sky at Night
```

Nice

---

