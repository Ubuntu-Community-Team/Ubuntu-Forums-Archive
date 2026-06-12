---
title: "Adobe Premiere Pro 2.0, Ubuntu, and WINE"
date: 2010-08-24
forum: Multimedia Software
---

### Post by brenti on 2010-08-24
I may be kicking a dead horse, but I figured I would give it a try...

After having installation issues with XP, I decided it was time for something different.  I DLed and installed Ubuntu 10.04 without a hitch.  Next, I installed WINE.  Step three was to install a legitimate copy of Adobe CS2 Production Studio Premium.  Installation went great and there didn't seem to be any issues...

Here is my problem:  All of the products in the suite installed fine with the exception of Premier and Encore.  Below is a screen shot of Premiere starting to load.  after that nothing happens.

[IMG]http://s3.amazonaws.com/twitpic/photos/full/150620568.png?AWSAccessKeyId=0ZRYP5X5F6FSMBCCSE82&Expires=1282690640&Signature=os63u%2BstZFGzivMt%2BV%2FvLBbTUsk%3D[/IMG]

Any thoughts on how to get this thing going completely?

Thanks,

Brent
Ubuntu 10.04 - Lucid Lynx
Wine 1.3.0
Adobe CS2


ps.  I even edited the above photo in photoshop in ubuntu

---

### Post by hsoulen on 2010-08-24
Hi there,

You may be flogging that horse.

According to WineHQ it looks like Premiere is mostly unsupported: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=128](http://appdb.winehq.org/objectManager.php?sClass=application&iId=128)

And the same for Encore: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=9012](http://appdb.winehq.org/objectManager.php?sClass=application&iId=9012)

Not to say you could not get them working, just the time and investment might not be worth it.

I can suggest you have a look at Kino (synaptic search "kino"): [http://www.kinodv.org/](http://www.kinodv.org/) which is what I use for DV video editing and I love it.

For DVD authoring have a look at this page: [https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring) I don't do a lot of it but it seems there are some nice tools.

You are probably super comfortable with the Adobe suite but you never know, try a few Open Source alternatives and you might be surprised :-)

Cheers,

Hank

---

### Post by brenti on 2010-08-24
Hank,

Thanks for the reply.

May I point your attention to the following links:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5878](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5878)

[http://appdb.winehq.org/screenshots.php?iAppId=128&iVersionId=5878](http://appdb.winehq.org/screenshots.php?iAppId=128&iVersionId=5878)

Evidently, Jelle De Loecker has been successful in getting PP 2.0 to run in Ubuntu.  I have sent him a message and am hoping to hear back from him on the issue.

In the mean time, could you please explain to this noob how much work would be involved in getting this thing working.  I can live without Encore, but there is nothing that can compare to Premiere besides Final Cut and possibly Sony Vegas.  Is it just a matter of getting the right dll's into the wine library?

I welcome additional thoughts.

Thanks,
Brent

---

### Post by Madspyman on 2010-08-24
Wish I could be of help, but I actually have a question? 

You said all of the other programs worked except Encore and Premiere, what version of After Effects came in production bundle CS2, I have an older bundle with AE 6.5 that works great, but up until recent I didn't think any other version of AE after 6.5 would install properly in Wine.

I know Premiere is probably your editor of choice, but editing can be done in AE, personally I use Blender. Also keep your eye on this 
 [http://www.editshare.com/index.php?option=com_content&task=view&id=155&Itemid=203]("http://www.editshare.com/index.php?option=com_content&task=view&id=155&Itemid=203") for the future.

---

### Post by brenti on 2010-08-24
It is actually AE 7.0, and I need to correct myself.  It is telling me that my serial is invalid and it wont open.  I will be investigating this issue.  Also, to my surprise, Image Ready and Illustrator are not functioning either. This is not a big deal to me, since my staples are Premiere, Audition, and Photoshop.

I will see about getting AE to work and report back on the issue.  However, I am still trying to get Premiere to work as well.

Thanks,

Brent

---

