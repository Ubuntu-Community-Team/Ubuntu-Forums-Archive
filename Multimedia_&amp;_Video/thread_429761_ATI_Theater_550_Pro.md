---
title: "ATI Theater 550 Pro"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by fAlCoNNiAn on 2007-05-01
Just a shot in the dark, i googled and i couldnt find anything. Anyone know if this is supported? It is the only thing  that is keeping me from switching on my desktop.

---

### Post by madmetal on 2007-05-01
> **fAlCoNNiAn said:**
> Just a shot in the dark, i googled and i couldnt find anything. Anyone know if this is supported? It is the only thing  that is keeping me from switching on my desktop.

i dont find this model here
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
but i think you wont face any serious problem...(besides ATi minor driver problems..)
run live cd first to see if everything is ok and then move on..

UAResolved.

---

### Post by fAlCoNNiAn on 2007-05-01
All the video cards that i am looking at with ubuntu are general graphics cards, not tv tuner cards. I wonder if anyone has gotten the 550 pro or the 650 pro, since they are pretty much the same thing, working. If someone got the all-in-wonders working, then is there any special steps that were taken in order to get the tuner working.

---

### Post by rsambuca on 2007-05-01
The 550 pro is a brick in linux.  No drivers available.

---

### Post by fAlCoNNiAn on 2007-05-01
> **rsambuca said:**
> The 550 pro is a brick in linux.  No drivers available.

:( boo

---

### Post by rsambuca on 2007-05-01
Yeah, I know.  I gave mine to my mom and got a Hauppauge once I started using Linux a lot.

---

### Post by gridsleep on 2007-06-09
The Gatos Project  () appears to be making at least an attempt at getting the ATI video capture cards to work under Linux.  I experimented with it previously under Mandrake (pre-Mandriva) but did not achieve appreciable success.  I have not installed Ubuntu on my workstation, but did try the live CD, thus learning that Ubuntu could not see my Theater 550 card nor the HP scanner on USB.  I have not been to Gatos in a while so there may be some improvements.

---

### Post by gridsleep on 2007-06-09
That's [http://gatos.sourceforce.net]("http://gatos.sourceforce.net").  The poster did not properly install the URL link in the last message.

---

### Post by rsambuca on 2007-06-09
> **gridsleep said:**
> That's [http://gatos.sourceforce.net]("http://gatos.sourceforce.net").  The poster did not properly install the URL link in the last message.

I think there must be a typo in your link.

---

### Post by Bohlio on 2007-06-10
I have the ATI Theater 550, It came with my dell, and it doesnt work in ubuntu :-( This makes me sad...

---

### Post by gridsleep on 2007-06-13
Apologies.  It's [http://gatos.sourceforge.net]("http://gatos.sourceforge.net").  If you're fooling around with Linux and don't know SourceForge, you haven't been in it for very long.

---

### Post by gridsleep on 2007-06-13
> **rsambuca said:**
> I think there must be a typo in your link.

Apologies.  It's [http://gatos.sourceforge.net]("http://gatos.sourceforge.net").  If you don't know SourceForge, you haven't been using Linux for very long.  Thanks for catching that.

---

### Post by rsambuca on 2007-06-13
Yeah, I knew that, but I thought I would point it out for anyone that doesn't know yet.  In any event, the 550 pro isn't covered in that project, as far as I can tell.

---

### Post by roadrocket13 on 2007-09-13
i understand that the ATI Theater 550 Pro is not explicitly declared in that project page but does that mean another driver could not be manipulated to provide limited operability ?


from the project page; [http://gatos.sourceforge.net/ati.2.php]("http://gatos.sourceforge.net/ati.2.php")

     "ati.2 drivers allow you to take advantage of video and TV playback features of cards made by ATI, inc...

      These drivers should work fine with any Mach64, Rage128 or Radeon card, in particular:"

---

### Post by rsambuca on 2007-09-13
I'm not 100% positive, but I think those are all software encoders, not hardware like the 550.  I am afraid it is still a linux paperweight.

---

### Post by acoustibop on 2007-09-13
You may not get your card working in Ubuntu, fAlCoNNiAn, but it won't affect how Ubuntu runs.  The card just won't work.

I tried to get several ATI VIVO and AIW cards running in Edgy and Feisty: the cards worked fine as video cards, but I could never get a peep out of video or tuner inputs.  I gave up and went with a straight ATI 9800 XT and a Hauppauge ImpactVCB capture card - no tuner; I'm on cable and don't need one.  Worked out of the box; I just installed TVtime and that was it.

---

### Post by 1Xtreeme on 2007-10-04
erm, AIW drivers will be MUCH diff then the ATI HD tuner drivers. Just look at the xp drivers once to see what I mean. At any rate.....ati rage 128 and all that is video not tuner. Heck my linux box has one. (Ancient card anyways). 

I think this lack of ATI hd tuner support is a major blow to ubuntu and other 'nix distros. I know of many folks that want a linux box for pure media use, and well ATI hd tuners are pretty popular if not the most well known (not saying best). Lots of dissapointed folks. Youd think someone would be working on correcting this issue. I mean they are working on wifi and thats a waaaaay broader range of hardware! Ati has what 4 or 5 diff chips for tuning. Not that much. 2 that are hd, rest are aiw and like ATI tv wonder pro (stereo analouge, physical tuner) and the latest analouge digital tuner (like 650pro has). Persoanlly I have two digitals ATI 650 pro AND the ATI HDTV wonder, and one analouge only, the ATI tv wonder pro.

Has anyone suggested or tried NDISwrapper? Use the XP drivers.:confused:

I find it hard to believe the older tuners atleast arent working. I mean the conexant chipset is VERY common. In fact if you look long enough I bet some of the working card have conexant chips! Im gonna give ndiswrapper and the XP drivers a go once this evening.

Found this for older conexant cards still looking for HDTV drivers/support though
[http://linux.bytesex.org/v4l2/cx88.html](http://linux.bytesex.org/v4l2/cx88.html)

---

### Post by cordova59 on 2007-11-24
i have a ATI tv wonder pro using a conexant chip and it works fine for me

---

### Post by rsambuca on 2007-11-24
That is a different chip from the Theater 550 Pro.

---

