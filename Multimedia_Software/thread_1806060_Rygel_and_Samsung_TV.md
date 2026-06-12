---
title: "Rygel and Samsung TV"
date: 2011-07-17
forum: Multimedia Software
---

### Post by Derek Karpinski on 2011-07-17
Can someone please guide me through getting my Samsung TV and/or XBox360 to see my pictures, videos, and music folders using rygel?

Those devices are not seeing my ubuntu computer at all.  I have installed UPnP inspector, and if I turn off my firewall completely, I can see the TV and XBox, but they still can't see my computer.

Help! :D

---

### Post by livecooool on 2011-07-17
You can watch live tv channels from all around the world, Pakistani and Indian news, sports, entertainment, movies 

channels. just visit [http://www.channel.pk]("http://www.channel.pk/")
Regards,
BW -22616

---

### Post by Derek Karpinski on 2011-07-17
Uhhhhhhhhh........thanks?:confused:

---

### Post by Derek Karpinski on 2011-07-17
Solved:

Rygel doesn't run automatically upon installation.  After setting the preferences, you must run from terminal, or write a script that will run at startup with:

```
rygel
```

That's it!:D

---

### Post by BigCityCat on 2012-04-21
Well yeh if your firewall is disabled. 

You can start rygel on start up by simply opening StartUp Applications and adding
Name rygel
Command rygel

You should run rygel in the terminal once. Type rygel in terminal. make sure you have rygel-tracker isntalled.

Do not look to see if your xbox 360 sees your pc on the network. It doesn't. Just goto music or video and open music player. Look at the bottom and you will see shared files. Make sure you started rygel first.

---

