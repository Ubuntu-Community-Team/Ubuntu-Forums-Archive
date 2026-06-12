---
title: "[SOLVED] 8.04 RC mythfilldatabase fails"
date: 2008-04-20
forum: Mythbuntu
---

### Post by amphibem on 2008-04-20
I have been attempting to get a working guide in MythTV and feel I am very close, with a complete tvguide.xml file full of listings for all channels (not something that has been easy before in NZ!). However mythfilldatabase fails with:

 ```
2008-04-21 11:51:35.692 Unknown xmltv channel identifier: c4 - Skipping channel.
2008-04-21 11:51:35.693 Unknown xmltv channel identifier: prime - Skipping channel.
2008-04-21 11:51:35.694 Unknown xmltv channel identifier: tv1 - Skipping channel.
2008-04-21 11:51:35.695 Unknown xmltv channel identifier: tv2 - Skipping channel.
2008-04-21 11:51:35.696 Unknown xmltv channel identifier: tv3 - Skipping channel.
```

I have run 
```
mythfilldatabase --file -1 tvguide.xml --manual
```
and assigned each of these channels a Channel Number, and in mythbackend setup they have all been assigned to the input (labelled 'Analog') and given the correct frequencies. I have a ChannelInfo.xml with each of the channels numb
ered correctly. However mythfilldatabase fails as above, and finds no shows.

Can anyone see where I have gone wrong?

More details on the current steps here:

[HTML]http://ubuntuforums.org/showthread.php?t=758447[/HTML]

Well found it. I had:

```
mythfilldatabase --file **-1** tvguide.xml
``` and not 
```
mythfilldatabase --file **1** tvguide.xm
```

Seems I got confused with what option was taken out in myth 0.21 :P

---

### Post by agamotto on 2008-04-21
Pardon my ignorance, but why are you needing to do anything other than 'mythfilldatabase?'  I am not sure why you are adding options to the command in the first place.

---

### Post by amphibem on 2008-04-21
> **agamotto said:**
> Pardon my ignorance, but why are you needing to do anything other than 'mythfilldatabase?'  I am not sure why you are adding options to the command in the first place.

There is no built-in xmlTV grabber for NZ where I live, the only way we can get TV listings is thanks to [this guy]("http://www.reven.co.nz") whose has a written an app caled xmlTVNZ which does a screen scrape of local TV listings a nd outputs a n xml file with all the listings. Mythfilldatabase can then do its job working from this file, rather than its interal grabber. Unfortunatly this isn't always as simple as one might hope ;)

---

### Post by laga on 2008-04-21
If your Grabber was baseline compliant, then MythTV would 'see' it and it'd be more integrated. 

See the first paragraph of [HowToWriteAGrabber](http://xmltv.org/wiki/howtowriteagrabber.htm)l and [Capabilities](http://xmltv.org/wiki/xmltvcapabilities.html).

Convince the author of your grabber to be baseline compliant and it'll automatically show up in mythtv-setup :)

---

### Post by amphibem on 2008-04-22
I guess so. I'm pretty sure the bulk of the users of xmlTVNZ are running Windows Media Center though (which requries even more work to get a guide for!) so I guess a 'baseline complaint' grabber isn't a high priority. 

I'm just really glad to be able to get a guide here, there are no official ones outside of what is delivered through digital TV so this is the only way.

---

### Post by MCMcButtah on 2008-05-08
Thanks allot for this info. My mythfilldatabase just stopped working one day and I didn't figuere it was the stupid -l.

---

### Post by amphibem on 2008-05-08
> **MCMcButtah said:**
> Thanks allot for this info. My mythfilldatabase just stopped working one day and I didn't figuere it was the stupid -l.

Glad to help! It was really fustrating me that day so I know what its like

---

