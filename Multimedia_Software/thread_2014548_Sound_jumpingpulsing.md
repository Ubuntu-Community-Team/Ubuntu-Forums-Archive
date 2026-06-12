---
title: "Sound jumping/pulsing"
date: 2012-07-02
forum: Multimedia Software
---

### Post by hornetster on 2012-07-02
Up until about 4/5 days ago, my sound on 12.04 x64 was fine. Since then (maybe a patch??) playing an mp3/flac the sound pulses randomly but regularly (every 10-30 seconds...). Mostly affects audio, but does, for example, skip in kaffeine or similar, every 10 mins or so.
Anyone else having this issue/have any suggestions?
How do you configure/check the audio backend in Ubuntu? I'm used to Suse,
Thanks.

---

### Post by hornetster on 2012-07-04
It appears that this problem is with the user profile - Have logged in as another user and all is OK.
Done lots of googling and can't find any specific usersound troubleshooting...
Any help please?
Thanks.

---

### Post by hornetster on 2012-07-04
S'pose the question is: How can I reset a particular users sound configuration to default?
(and the other question is: what screwed it in the first place? :-) )
Thanks, John.

---

### Post by hornetster on 2012-07-05
Mistaken yet again...
The problem is still occurring, even in the new profile, so I am back to square 1...
Surely someone must have an idea/same problem/something...?
Thanks, John.

---

### Post by hornetster on 2012-07-09
Just an update - not that anyone is interested.. :( - have worked out what the cause is, just haven't worked out how to fix it.
Close Google Chrome - all works fine - open Google Chrome, the problem comes back...
Quick answer: have moved to Firefox....
Thanks for the assistance.
John.

---

### Post by jmfal on 2012-07-09
Try installing ubuntu-restricted-extras you can find it in the software center, synaptic
or using a terminal

```
sudo apt-get install ubuntu-restricted-extras      
```

---

### Post by hornetster on 2012-07-09
Always do this after reinstalling a new version of the operating system... 
Am I supposed to manually update this occasionally??
Will certainly give it a try, but would have thought if I have already done this, shouldn't need to do it again?
Thanks, John.

---

### Post by SmileyChris on 2012-07-09
Hi John,

Just a quick note to let you know that you're not alone. I've got exactly the same problem (also on 12.04 x64, also only with chrome open and only since a Chrome 20 update).

There was a recent problem with flash and osX on Chrome -- I'm wondering whether this is related.

Guess a switch to chromium would be a solution, but I use google profiles so it would be a downgrade.

---

### Post by cootetom on 2012-07-09
I have this problem too. I'm running chrome version 20.0.1132.47.

It's weird because the pulsing sound only starts when chrome is opened. Then I have found a few things that stop it. If I open the sound settings from the Gnome icon bar (top right) the pulsing stops until I close the settings again. Also if I plug my power supply in it stops. It only ever happens when chrome is open though so it must be something to do with that.

I'm stuck for ideas at the moment.

---

### Post by SmileyChris on 2012-07-09
I'm mostly convinced this is a problem with Chrome's flash plugin.

To test it, I've been running a while without flash (not really a big loss...).
You can do this yourself by going to [chrome://plugins/]("chrome://plugins/") and clicking "disable" on flash.

So far I haven't had any more sound glitches.

---

### Post by cootetom on 2012-07-10
I think you're right. I've also disabled flash and it's stopped the problem. Think I'm just going to wait and see if the next release of chrome sorts it out.

---

### Post by cootetom on 2012-07-14
Here is something for people to try. Use gnash and lightspark as a replacement for flash. 

Firstly you need to disable the standard flash plugin. To do this open chrome://plugins in chrome browser. Click on the + sign in the top right corner of the web page which opens up the plugins details. Find the flash plugins, there are probably two. Disable these plugins.

Now install gnash and lightspark..

sudo apt-get install gnash lightspark browser-plugin-lightspark

Open chrome and test some flash pages. 

For me, lightspark didn't work. It just crashed! So if that is the case you can try the following. 

sudo apt-get remove lightspark browser-plugin-lightspark

sudo apt-get install browser-plugin-gnash

Now start chrome again and test some flash. 

For me this has stopped the sound problem and I can use flash on a lot of sites. Unfortunately it's not 100% so where a site doesn't play flash correctly I have to re-enable the PepperFlash plugin in chrome://plugins. However I have been running the PepperFlash + Gnash plugins together for a while and flash seems to work 100% without sound problems.

---

