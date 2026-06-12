---
title: "Flash in Firefox Kills Sound In Other Apps"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by HalNineThousand on 2007-07-12
I've seen people having problems with Flash not being loud enough to be heard, but this is almost the opposite.

I'm using Feisty, upgraded from Edgy on Kubuntu.  Whenever I play a Flash video in Firefox, it kills the sounds for other apps, like Amarok, VLC, and others.  It took me a long time to narrow this down, but I finally found out that exiting Firefox lets the sound start playing again for other aps.  I've learned to avoid links to YouTube (which I tend to avoid anyway), but there are times when a web page uses Flash and I don't know until I load it.

My best guess is that Flash does something to a volume setting that is undone when I quit Firefox.  Right clicking on a Flash video gives me a config menu, but nothing that effects playback volume.

I've posted about this before (3 weeks ago) and didn't get any responses but now I know it's not just Firefox, but specifically that it's tied in with Flash. 

Is there anything I can do or a setting I can override?  I didn't find any thing useful in about:config but it might not have been an obvious setting.

Thanks for any help on this!

---

### Post by deadgobby on 2007-07-12
Lets take a look at your sound device. Are you using a on board sound device or a sound card, like Sound Blaster for a example? If you use a on board sound device that it may get confused on which sound source to play. Thus you need to kill out one app to listen to what is on the web.  If you have a sound card. Check you BIOS to see if the on board sound is disable. It all so may be on how much ram you have on your system. If you have like 256 megs of ram. You may get some thing like what you said.

---

### Post by HalNineThousand on 2007-07-12
I doubt it's RAM.  I've got 2 GB.  I will check the BIOS next time I boot.  I can't remember if this board has onboard sound or not so I'll have to check.  I am using a Soundblaster for this, but I've never had a problem with apps getting confused or one blocking out the other before.  KInfoCenter doesn't indicate more than one sound card.

Since it's Firefox that seems to grab and hold the channel, is there anything I can change in Firefox or is there a Flash config file somewhere so I can set something to release the channel?

---

### Post by deadgobby on 2007-07-12
Check your BIOS and see if that is the problem. I have a SB too and do not have such a thing. If you have a AMD cpu it could be a cause of your problem. 
Gobby

---

