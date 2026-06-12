---
title: "wierd audacity issue"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by nvrpaul on 2007-05-05
SO here is the deal. I have audcatity with fiesty and my lightech quickcam express that works out of the box with both the mic and the camera on fiesty. I can record using the mic in audacity alright (no pro quality, just to help me remember riffs i come up with). But when I import an MP3 backing track for a guitar solo in audacity and click record it gives me this error:"error while opening sound device, pleae check input device settings: Ijust want to record a guitar solo to see how i play on top of tracks my guitar teacher sends me to practice with.
Thank you,
paul
:guitar:

---

### Post by nvrpaul on 2007-05-06
bump, please help

---

### Post by nvrpaul on 2007-05-08
bump, please help!!!

---

### Post by CodeCat on 2007-05-10
I had this issue myself. Haven't found what caused it yet, but there is this workaround that worked for me:

- Install the alsa-oss package.
- Run audacity with **aoss audacity**.
- From within audacity, go to Edit > Preferences, Audio I/O, and select 'OSS' as the device.

You'll have to run audacity with aoss all the time though, or it won't work.

---

### Post by moeman on 2007-05-27
I have been having the EXACT same problem. There doesn't seem to be anyone out there who knows whats going on with this.  The trick about using aoss to run audacity seems to be sort of working for me, but I get alot of lockups and crashes.  I went ahead and edited the menu item for audacity, and I changed the "command" to "aoss audacity" so I can run it form the menu.  I would really really like to get this issue fixed.  Is there anyone who can help us out with this?  I am sure this is just some sort of conflict with the way audacity is interacting with the kubuntu sound system setup.

---

### Post by ryanVickers on 2007-05-27
I noticed that if I have any other sound thing open, like a media player (I use Listen) it gets this error, but if I close it and audacity and re-open audacity it works fine.  Try doing this with nothing else that uses sound running.

---

