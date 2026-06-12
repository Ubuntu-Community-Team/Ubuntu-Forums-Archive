---
title: "Replace Totem with VLC as Default Multimedia player"
date: 2008-06-27
forum: Multimedia Software
---

### Post by SonicSteve on 2008-06-27
I'm ranting a bit here (sorry in advance)

I've been using Ubuntu for a few years now, from what I've seen;
 
-Totem is hasn't made any major strides in all that time. 
-It can't support DVD menu's properly, 
-It seems to have more problems playing virtually all forms of media than other players.

The only thing it has going for it is that it integrates well into gnome.

Is it not possible to integrate VLC into Gnome??? Or something better than Totem. It seems like Totem is being totally neglected.

After ranting and whining like that you'd think I'm after like opinions and soothsayers right? 
[SIZE=5]No[/SIZE], firstly I admit that I was whining a bit. I would like some knowledgeable  Ubuntu/Gnome users to  comment.  I'm just really tired of Totem and it's slow development.  

Let me explain what set me off. I bought some USB speakers, and guess what they work. They only work with programs that tightly integrated into Gnome though. I have no sound out of VLC, Firefox, Kaffeine, (the programs I like and use) and I do have sound out of Totem and Rythmbox. Unfortunately because Totem stinks at playing all forms of media in the latest version (hardy) I have to use VLC or Kaffeine. I like both those programs, they won't use the USB speakers though. Totem will use them quite nicely, as will any other program that actually listens to the System>preferences>sounds applet. Essentially any program that integrates tightly with Gnome. 

In my mind one of the glaringly obvious deficiencies of Ubuntu is a really Good, out of the box multimedia player. 

I turn the floor over to the rest of you. What do you have to say?

---

### Post by flytripper on 2008-06-27
i learned this tonight.. try right clicking the file you want to play. change "opens with" then add vlc and boom...

---

### Post by flytripper on 2008-06-27
lol forget me. i'm half asleep. i cant read....

---

### Post by SonicSteve on 2008-06-27
> **flytripper said:**
> i learned this tonight.. try right clicking the file you want to play. change "opens with" then add vlc and boom...

It's true you can do that. However since VLC isn't integrated into Gnome it has limitations. I don't have problems setting as the default program that opens, what I want to see is time spent on integrating into Gnome so that it is truly part of Gnome. Ya I know that Gnome.org dictates what programs are default. It just seems like we already have a wheel and it's VLC, why for the love of ... do they have re-invent the wheel when we have a perfectly good one already. 

It's frustrating.

---

### Post by mc4man on 2008-06-27
Try this
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by SonicSteve on 2008-06-27
> **mc4man said:**
> Try this
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

I'll try this again, though  I don't think it will have the effect I'm wanting. I'll be very happy if I'm wrong by the way. I'm looking for a deeper integration. For instance.
If you go to System>preferences>sounds and you have a pair of USB speakers you can select them for being the default sound output for various aspects of Gnome function. In fact you select the to do everything. the problem is that only programs that are developed by the Gnome Developers work properly. They have been programed to be part of Gnome, not just programed to work along side gnome. 
VLC and Kaffeine work well along side Gnome but they aren't really part of it. Totem on the other hand has been developed for Gnome, and it obeys the various applets that Gnome gives you for configuration. VLC and Kaffeine because they are designed to work in various environments don't have this kind of Gnome co-operation.

---

### Post by markbuntu on 2008-06-27
You can change the default apps to anything you want in the file manager. 

The developers chose Totem as the default because it has extensive support for many file types, is easy to use for beginners, and hard to wreck. 

vlc has far more options and could easily become a train wreck in the hands of someone who doesn't have a clue.

---

### Post by mc4man on 2008-06-27
sorry misunderstood problem (usb speakers)
Totem-xine will give you better menu, playability than totem-gstreamer
Have you browsed thru this thread?
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)
I know back in gutsy some people w/ usb speakers had success using esound but i thought pulse audio was supposed to resolve these issues in hardy

---

### Post by SonicSteve on 2008-06-29
> **mc4man said:**
> sorry misunderstood problem (usb speakers)
Totem-xine will give you better menu, playability than totem-gstreamer
Have you browsed thru this thread?
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)
I know back in gutsy some people w/ usb speakers had success using esound but i thought pulse audio was supposed to resolve these issues in hardy

Thanks for the toem-xine tip, I had forgotten how much better it is. This raises yet another question. Why on earth does Ubuntu package gstreamer by default when Xine is so much better? Every time I've ever had trouble with media it seems that the solution is to remove Gstreamer, and install xine.

I gave it a try, it seemed to help a bit then they stopped working altogether. I can't even get gnome programs to work with them now. I'm sure I could get that back by reversing some of the config files. The real problem is that you don't sometimes if your being thwarted by a bug, or if the config files are off slightly. I don't think Pulse audio is quite ready for the world.  I'll just have to use the speakers on a Windows machine and try them again every once in while after upgrades, and updates. There is some hope, the speakers are recognized by the Ubuntu Kernel, but more work needs to be done.

This brings me all back to my original thoughts, 
Ubuntu needs to package a different Media player as the default and spend time integrating it into Gnome. From my understanding of Linux and it's packaging model this would likely be far too large of an undertaking. 

We should start a remove Totem campaign

---

