---
title: "Music Player + iPod Sync"
date: 2009-12-09
forum: Multimedia Software
---

### Post by Narusegawa on 2009-12-09
I use iTunes extensively on Windows (99% of my PC uptime has iTunes running). 

I'm looking for an application in Ubuntu 9.10 that plays music well but one that has iPod sync support with it. Syncing with my iPod as iTunes does is very important to me.

I like the look and feel of RhythmBox but it's wiki says it doesn't support transfer to/from iPod yet. Songbird the last time I checked had experimental support but had other issues.

Edit: Forgot to say, mine is an old 5th Gen iPod Video albeit the firmware is fully up-to-date

---

### Post by LuisGMarine on 2009-12-09
Hello!

Good news for you!  First of all I have all the links that you need in my signature.  
[LIST]
[*]Install Songbird on Ubuntu
[*]Sync your iPod with Songbird
[/LIST]

As for Songbird, it is now out of the experimental stages, and is relatively stable.  Right now iPod sync is broken by default Ubuntu, so only rythmbox can detect your iPod.  However if you follow my other guide, there is a nice and quick workaround so that every other application can see your iPod.

I highly recommend Sonbird, it's the closest thing to iTunes, and even better.  

Please don't hesitate to post back if you run into any problems! Good Luck!:popcorn:

---

### Post by Narusegawa on 2009-12-10
Ohh I'll check out Songbird, I used it on Vista awhile back and liked it. 0.9 I think.

Is there a nice Ubuntu skin for it? The one on their own appearance site is over a year old and for version 0.61 where they now have 1.2 or so.

I'm trying this again at the weekend so will let you know how it goes. (Was awaiting a new hard drive however the store got 2 orders mixed up so my hdd is in another country)

---

### Post by mike2434 on 2009-12-10
Hi Luis.  Ive been trying forever to get my ipod to sync with 9.10.  I did exactly as you said on your website and when i saved the sb file and put the code in my terminal i get this


tar: Songbird*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors


Not sure what im doing wrong but i'd really appreciate your help.

Thanks

---

### Post by LuisGMarine on 2009-12-10
> **mike2434 said:**
> Hi Luis.  Ive been trying forever to get my ipod to sync with 9.10.  I did exactly as you said on your website and when i saved the sb file and put the code in my terminal i get this


tar: Songbird*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors


Not sure what im doing wrong but i'd really appreciate your help.

Thanks


Are you sure that you are navigating to the folder where you downloaded Songbird?  That output is pretty much telling you that you are running the command in the wrong folder.  If you downloaded songbird and it saved to your /home/username/Downloads, make sure you navigate there with.

```
cd /home/username/Downloads
```

of course subsitute *usersname* with your actual username.

---

### Post by mike2434 on 2009-12-11
Do I enter that code in a terminal?

---

### Post by mike2434 on 2009-12-11
I downloaded sb and the ipod add on and now sb isnt recognizing either of my ipods.  Ive tried a nano 4g and a ipod color. does it have to be an ipod not previously synced with itunes?

---

### Post by LuisGMarine on 2009-12-11
> **mike2434 said:**
> I downloaded sb and the ipod add on and now sb isnt recognizing either of my ipods.  Ive tried a nano 4g and a ipod color. does it have to be an ipod not previously synced with itunes?

No, that's fine that it has been synced with iTunes before.  Now, go ahead and follow this other link on how to get your iPod recognized in Songbird.

I'm already hoping that at this point Ubuntu can recognise your iPod, just not Songbird. 

Here is the guide, post back if you run into any more problems.

[http://luisgmarine.blogspot.com/2009/12/fix-ipod-detection-in-ubuntu-910.html]("http://luisgmarine.blogspot.com/2009/12/fix-ipod-detection-in-ubuntu-910.html")

---

### Post by Narusegawa on 2009-12-12
I've got Songbird installed now thanks. Looks good. One thing... if I have multiple users, will each user have their own .profile folder with their own seperate music library?

Not tried the iPod sync yet, attempting that later today :)

---

### Post by mike2434 on 2009-12-12
Just tried it and when i type in nautilis the only program it gives me an option to open is a cd dvd burner program. if i dont type in nautilis and just selct songbird it opens but still does not show my ipod.  is there anything else i can do to get this working?  thanks for all your help

---

### Post by LuisGMarine on 2009-12-12
> **mike2434 said:**
> Just tried it and when i type in nautilis the only program it gives me an option to open is a cd dvd burner program. if i dont type in nautilis and just selct songbird it opens but still does not show my ipod.  is there anything else i can do to get this working?  thanks for all your help

I'm not sure I understand what it is you are saying.  All you have to do is open up terminal, and type in 
```

killall -9 nautilus
```

Connect your iPod.  Hit Alt + F2 and type in nautilus and hit run, that is it.  Then open up your media player manager, and hopefully your ipod is being recognised.  Just make sure that after you connect your ipod give it 30-60 seconds before you run nautilus again.

---

### Post by mike2434 on 2009-12-12
Just tried it again the right way and songbird still will not recognize it.  not sure why this isnt working.  is this all i can do to have my ipod work with sb?

---

### Post by LuisGMarine on 2009-12-13
Do other applications other than Rhythmbox recognise your iPod?  Like do you see ubuntu mount the device when you connect it?

---

### Post by jmate24 on 2009-12-13
banshee works better. for ipods and syncing.

jmate24--:D

---

### Post by mike2434 on 2009-12-13
Yes.  Banshee rarely recognizes it and when it does it will not work becuase it tells me that it needs to rebuild my database becuase ive already used the ipod with itunes.  Gtkpod wont mount it for some reason, rhythmbox recognizes it just fine but wont allow syncing and yes songbird has yet to recognize it.  And also ubuntu does recognize it.  I was convinced it was just my ipod but ive tried older ipods and still none of them work.

---

### Post by dtr1001 on 2010-01-04
Support for ipod in songbird is broken at the moment....

[http://getsatisfaction.com/songbird/topics/potis_ipod_policy_should_be_rethought](http://getsatisfaction.com/songbird/topics/potis_ipod_policy_should_be_rethought)

regards

David

---

### Post by LuisGMarine on 2010-01-04
That's been the case for a really long time.  I don't know what banshee is doing different but they got their iPod sync on point (at least for me).  THe only problem is that they lack extensions that are powerful like "The Exorcist" to handle duplicate songs.  TO me that is the only down fall to banshee.   Hopefully some of these issues will be look at in future releases.

---

