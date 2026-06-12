---
title: "Media Applications Do Not Run"
date: 2012-05-24
forum: Multimedia Software
---

### Post by spiritusumbrarum on 2012-05-24
My Audacity Can Not Run. It Shows Many Of These:

[1m[31mERROR:JackAudioDriver::ProcessGraphAsyncMaster: Process error [0m, 

Ardour Shows: 

Alsa Connection Changed.

And Something About Alsa Graphics Change.

Sweep Just Does Not Run.

Openshot Does Not Run.

Many Others Do Not Run.

Audacious And Gnome Player Do Not Play Anything Sometimes.

I Tried To Completely Remove Jack And These Applications With Synaptic And Re-Install Them, But They Still Do Not Run.

What The Hell Can I Do?

Updates Do Not Fix Anything.

I Tried To Manually Remove Configuration Files And All Stuff (I Fixed Akonadi Server In This Way) But All These Applications Still Do Not Work.

Is There An Application To Diagnose And Fix Ubuntu, Lubuntu, Etc. Without Restoring The Whole System To The Original Point?

Thanks For Your Answers.

---

### Post by Rodney9 on 2012-05-24
Have you installed lubuntu restricted extras.
```

sudo apt-get install lubuntu-restricted-extras
```

These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


You may want to install pavucontrol it lets you choose your sound source etc.   ```
sudo apt-get install pavucontrol
```



For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

