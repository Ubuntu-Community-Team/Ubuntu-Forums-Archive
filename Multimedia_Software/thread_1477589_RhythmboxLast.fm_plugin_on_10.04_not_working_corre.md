---
title: "Rhythmbox/Last.fm plugin on 10.04 not working correctly"
date: 2010-05-08
forum: Multimedia Software
---

### Post by justinmiller87 on 2010-05-08
I was able to log in to Last.fm through the plugin in Rhythmbox and begin playing the radio. However, it only will successfully scrobble the first song played and no other. In addition, when I clicked the button to "love" the track, it crashed Rhythmbox.

Has anyone seen this? If you need more information to help me, let me know and I'll see what I can provide.

---

### Post by rhc on 2010-05-15
It's very interesting that many people have the same problem, me too, but no one gives a care about this.

FFS, why Rhythmbox last.fm plugin just scrobble the first song and then it stops?

---

### Post by justinmiller87 on 2010-05-15
Yeah, I know. I found a separate plugin that will load the Last.fm software, but then you can't use Rhythmbox to play the radio through it. Then again, if you're loading the Last.fm player for the purposes of using the radio feature, why do you even need Rhythmnbox?

I haven't actually played a track through it as my media is stored on my network and I haven't gotten my network setup yet under Ubuntu, so I'll see if that will still work once I get some music to play.

---

### Post by rhc on 2010-05-15
Yeah, i know that plugin also.

But i need a built-in plugin with Rhythmbox because i can't use the great Context Pane. Also i can't get cover art and something like that.

I think i'll use Banshee until that Rhythmbox problem be solved. I suggest it to you also. 

**(BTW, it's weird that a simple problem like this can't be solved. No one is interested with it.)**

---

### Post by justinmiller87 on 2010-05-15
I happen to prefer Banshee as well. If they can get the Ubuntu One Music Store integrated into anything other than Rhythmbox, I'm all for it. Not that I've actually used it yet but I don't really want to jump back and forth between programs if I don't have to. I already do that in Windows between the Amazon downloader, iTunes, and MediaMonkey (great powerful app if you have to use Windows and love music, definitely worth the $20). Of course something else that would be even more epic is being able to access Ubuntu One outside of Ubuntu and being able to use it when I am in Windows, which I know is in the works, but isn't available yet.

---

### Post by rhc on 2010-05-15
There's a Banshee Ubuntu One Music Store extension in Synaptic.

---

### Post by justinmiller87 on 2010-05-15
Ah, cool. I shall look into that.

---

### Post by Mugatu on 2010-06-14
> **rhc said:**
> It's very interesting that many people have the same problem, me too, but no one gives a care about this.


> **rhc said:**
> 
**(BTW, it's weird that a simple problem like this can't be solved. No one is interested with it.)**

Umm... not trying to be rude, but if you care so much, then why didn't you file a bug report?  At least I couldn't find one, but maybe I just wasn't looking hard enough.

At any rate, I have the same problem, and I filed a bug report.  Posting on the forums is great for help, but if we want anything to get fixed, we need to file bug reports.  If you're not sure how, this should help:

[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

(I got that by Googling "ubuntu file bug report")

But anyway, no hard feelings.  Here's the bug I filed:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/594245]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/594245")

If you're having this problem and would like to see it fixed, please at least create an account, log in, and where it says "Does this bug affect you?", click that and then click "Yes, it affects me."  That'll help get it some attention.  You can also comment on the bug, or feel free to submit your own bug report and mark it as a duplicate of mine (if I'm not mistaken that's the easiest way for the developers to get the information they need.)

I think it might also help if you close Rhythmbox, open a terminal, run this command:
```
rhythmbox -d 2>&1 | egrep "audioscrobbler|lastfm" > rhythmbox-debug.txt
```

It'll open Rhythmbox.  Listen to a few songs in the Last.fm radio, then close Rhythmbox.  There should be a file in the folder you ran that command (probably your home folder if it was a new terminal window).  Attach that file to the bug I created.  I'm thinking that may help the developers.

Thanks!

---

### Post by cybrsaylr on 2010-06-14
I was having the same problem with Last.FM not playing well with Rhythmbox. I switched to Vagalume.
Try Vagalume, it's in Synaptic.

Vagalume plays LastFm very well.

---

