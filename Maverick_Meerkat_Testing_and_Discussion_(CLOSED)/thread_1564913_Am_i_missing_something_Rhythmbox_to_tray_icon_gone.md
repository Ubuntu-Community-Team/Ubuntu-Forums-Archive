---
title: "Am i missing something? Rhythmbox to tray icon gone?"
date: 2010-08-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ELD on 2010-08-31
Okay in Lucid you can close Rhythmbox had it's own tray panel and clicking close on the applications window would send it to the tray, seems at the moment theres no way to do that?

---

### Post by go7Ul1ai on 2010-08-31
There is no need for the Rhythmbox indicator applet now that there has been work done to the sound indicator to integrate Rhythmbox.

---

### Post by ELD on 2010-08-31
> **lee.jarratt said:**
> There is no need for the Rhythmbox indicator applet now that there has been work done to the sound indicator to integrate Rhythmbox.

I was thinking that.

My question is still valid though - how do we go about getting it to either minimize or close to tray?

---

### Post by ranch hand on 2010-08-31
> **ELD said:**
> I was thinking that.

My question is still valid though - how do we go about getting it to either minimize or close to tray?
That, as an old instructor of mine used to say, is an excelent question.  Seems to be lacking in some very basic functionality.

---

### Post by ELD on 2010-08-31
Yes it does, i like to have it hidden away and not taking up space, there must be a way, surly at least one developer has looked at it and thought "wait why can't i...".

---

### Post by Madspyman on 2010-08-31
click edit, select plugins from the dropdown menu, select status icon, and then click configure, set status icon to owns the main window. That should help.

---

### Post by ELD on 2010-08-31
Why is it something to be "upgraded" has to take a few steps back at the sametime?

I will try what you suggest.

---

### Post by mc4man on 2010-08-31
> Why is it something to be "upgraded" has to take a few steps back at the sametime?
Not too sure rhythmbox has taken a 'step back'. actually it's in better shape than it's been in the past pre-releases.
Sometimes defaults change or aren't set optimally or are set one way for a reason.
(atm it appears closing (exiting) rhythmbox from the icon is more of a crash than clean exit, whether it owns the window or not.

.

---

### Post by cariboo on 2010-08-31
Some may see this as a step back, but it's actually a step forward. The design team is trying to get rid of all the icons in the system tray, and replace them with windicators. The icon functionality now shows up in the sound icon, instead of having a separate icon sitting in the system tray.

---

### Post by Madspyman on 2010-08-31
> **cariboo907 said:**
> Some may see this as a step back, but it's actually a step forward. The design team is trying to get rid of all the icons in the system tray, and replace them with windicators. The icon functionality now shows up in the sound icon, instead of having a separate icon sitting in the system tray.

Are there plans to have it minimize to the sound icon as well?

---

### Post by ktp on 2010-08-31
> **Madspyman said:**
> Are there plans to have it minimize to the sound icon as well?

I sure hope so...but I am not holding my breath for it.  Anyone write up a bug for this missing functionality.

---

### Post by Madspyman on 2010-08-31
> **ktp said:**
> I sure hope so...but I am not holding my breath for it.  Anyone write up a bug for this missing functionality.

If they don't they've kind of missed a major point of the Rhythmbox status icon.

I think they will (have to) enable minimization to the sound icon, because if they don't the Rhythmbox status icon will still remain necessary and will be re-enabled by many users, defeating the original purpose of cleaning up the system tray.

I wonder how many of the devs use rhythmbox? Anyone who does, knows it's pretty obvious this feature is missing. It's another reason why I think it'll get fixed.

---

### Post by cariboo on 2010-08-31
I use docky, when I start rhythmbox via the sound icon, then minimize rhythmbox, there is an icon in the dock, why have another one in the system tray? I don't use a bottom panel, but I'm sure that it is minimized to the panel too.

---

### Post by kyleabaker on 2010-08-31
The Rhythmbox text in the sound menu already calls Rhythmbox back into view when its minimized, so it would really just be a matter of hiding Rhythmbox when its minimized rather than closing it and simply letting the user restore the window from the sound menu.

This could probably be easily accomplished by adding a new plugin for this that is enabled by default. That way there wouldn't need to be specific code for this managed by the menu, but rather by the Media player and using a plugin would make it easy to maintain too.

So this hasn't been filed yet? It seems to be less of a Rhythmbox bug and more of a sound menu bug, but I think it should ultimately be fixed used a plugin. No? What are other media players doing in this case?

---

### Post by Madspyman on 2010-09-01
> **kyleabaker said:**
> So this hasn't been filed yet? It seems to be less of a Rhythmbox bug and more of a sound menu bug, but I think it should ultimately be fixed used a plugin. No? What are other media players doing in this case?

Rhythmbox is unaffected, as it's native status icon is easy enough to restore. Also the sound icon isn't broken, as it's not a bug when something won't do something it wasn't designed to do.

It's just an inconvenience that can be fixed by putting the status icon in the notification area again. That's what'll happen if someone installs Amarok or Banshee anyway. Don't really see why we need to kill the Rhythmbox status icon, just because it's the default. I'm keeping mine. 

Speaking of the notifications, why do we still have both an indicator applet and a notification area? I thought part of cleaning up the panel was unifying all the notification/indication areas.

---

### Post by ELD on 2010-09-01
> **cariboo907 said:**
> I use docky, when I start rhythmbox via the sound icon, then minimize rhythmbox, there is an icon in the dock, why have another one in the system tray? I don't use a bottom panel, but I'm sure that it is minimized to the panel too.

The point of having the ability before to minimize/close it to a tray icon was to save space. Many people like myself don't like having a window open constantly for something like a music app working in the background.

Where can i bring back the rhythmbox tray icon? I can't see it under plugins or add to panel?

---

### Post by 23meg on 2010-09-01
> **ELD said:**
> Where can i bring back the rhythmbox tray icon? I can't see it under plugins or add to panel?

To illustrate [post #6]("http://ubuntuforums.org/showpost.php?p=9788973&postcount=6"):

[IMG]http://img810.imageshack.us/img810/2112/screenshotry.png[/IMG]

---

### Post by 23meg on 2010-09-01
> **Madspyman said:**
> Speaking of the notifications, why do we still have both an indicator applet and a notification area? I thought part of cleaning up the panel was unifying all the notification/indication areas.

Because [the transition]("https://bugs.edge.launchpad.net/ubuntu/+bugs?field.tag=indicator-application") is still ongoing.

---

### Post by ktp on 2010-09-01
@23meg

Do you know if they are planing to "hide" rhythmbox without having to enable "status icon"?

---

### Post by ELD on 2010-09-02
> **ktp said:**
> @23meg

Do you know if they are planing to "hide" rhythmbox without having to enable "status icon"?

This i would also like to know.

---

### Post by 23meg on 2010-09-02
According to [the spec]("https://wiki.ubuntu.com/SoundMenu#Rhythmbox"), when the Rhythmbox window is closed while it's playing, it should "hide". But this is not the current behaviour.

---

### Post by ktp on 2010-09-02
> **23meg said:**
> According to [the spec]("https://wiki.ubuntu.com/SoundMenu#Rhythmbox"), when the Rhythmbox window is closed while it's playing, it should "hide". But this is not the current behaviour.

Thanks.

---

### Post by kyleabaker on 2010-09-02
> **23meg said:**
> According to [the spec]("https://wiki.ubuntu.com/SoundMenu#Rhythmbox"), when the Rhythmbox window is closed while it's playing, it should "hide". But this is not the current behaviour.

According to the spec (thanks 23meg), the preferences window is due for a few major rearrangements! However, its not likely we will see these in Maverick due to the Interface and Feature freezes, so I'm wondering if thats why this still isn't working as we all expect? Surely they won't wait until Natty to complete this functionality.

Also, its kind of funny that the menu example at the top shows the artist "Acon" instead of [Akon]("http://en.wikipedia.org/wiki/Akon"). Did someone pirate some mislabeled music and type it into the mockup wrong too? :P

---

### Post by ktp on 2010-09-02
> **kyleabaker said:**
> Also, its kind of funny that the menu example at the top shows the artist "Acon" instead of [Akon]("http://en.wikipedia.org/wiki/Akon"). Did someone pirate some mislabeled music and type it into the mockup wrong too? :P

:lolflag:

---

### Post by locosway on 2010-09-04
> **Madspyman said:**
> click edit, select plugins from the dropdown menu, select status icon, and then click configure, set status icon to owns the main window. That should help.

The problem with this is you end up with another tray icon, instead of preserving the new functionality that the devs are trying to implement. What should happen is the player should hide to the sound notification/applet area, instead of running a second icon.

I hate having windows open if they're passive, such as a music player. I hate it so much I'll switch music players to one that has a tray icon instead. This is true for any apps that I use which are passive.

---

### Post by ELD on 2010-09-04
> **kyleabaker said:**
> According to the spec (thanks 23meg), the preferences window is due for a few major rearrangements! However, its not likely we will see these in Maverick due to the Interface and Feature freezes, so I'm wondering if thats why this still isn't working as we all expect? Surely they won't wait until Natty to complete this functionality.

Also, its kind of funny that the menu example at the top shows the artist "Acon" instead of [Akon]("http://en.wikipedia.org/wiki/Akon"). Did someone pirate some mislabeled music and type it into the mockup wrong too? :P

It's spelt right everywhere apart from the actual shot mockup...odd.

I still think it's something that needs to be put in before Maverick goes final, you can garuntee there will be a lot of people asking why they can't minimize it to tray easily.

---

### Post by dadush777 on 2010-09-04
Hello,
since I upgraded my Ubuntu from 10.04 to 10.10 whenever I close my RhythmBox Window,
the music STOPS and Rhythmbox is closed instead of showing in the upper panel...

what can I do to fix that? and I cant see the new Sound Menu they added in Ubuntu 10.10

Thanks in advance.

---

### Post by ktp on 2010-09-04
> **locosway said:**
> The problem with this is you end up with another tray icon, instead of preserving the new functionality that the devs are trying to implement. What should happen is the player should hide to the sound notification/applet area, instead of running a second icon.

This is the end goal, which is stated in the spec that was linked.

> **locosway said:**
> I hate having windows open if they're passive, such as a music player. I hate it so much I'll switch music players to one that has a tray icon instead. This is true for any apps that I use which are passive.

Rhythumbox can still have it's "status icon" and hide the window.  You just have to enable it in the preferences.  You can use that to hide Rhythumbox using that until the feature is fully developed.

---

### Post by Rasa1111 on 2010-09-04
well it is still in BETA,
meaning it still has issues to be worked out and is not ready to be used by everyone yet.
Only those wanting to test it for problems. 

 Upgrading your entire system before a release is not the smartest thing to do. 

If you wanted a stable, fully working system, you should have kept Lucid. 

 good luck.

---

### Post by Elfy on 2010-09-04
moved to maverick forum

---

### Post by ktp on 2010-09-04
> **dadush777 said:**
> Hello,
since I upgraded my Ubuntu from 10.04 to 10.10 whenever I close my RhythmBox Window,
the music STOPS and Rhythmbox is closed instead of showing in the upper panel...

what can I do to fix that? and I cant see the new Sound Menu they added in Ubuntu 10.10

Thanks in advance.

Please see following thread...make sure to read the whole thing:

[http://ubuntuforums.org/showthread.php?t=1564913](http://ubuntuforums.org/showthread.php?t=1564913)

---

### Post by ranch hand on 2010-09-04
> **ktp said:**
> Please see following thread...make sure to read the whole thing:

[http://ubuntuforums.org/showthread.php?t=1564913](http://ubuntuforums.org/showthread.php?t=1564913)
Oh come on, next you will be wanting folks to use a forum search.

---

### Post by ktp on 2010-09-04
> **ranch hand said:**
> Oh come on, next you will be wanting folks to use a forum search.

search what is that?? :lolflag:

---

### Post by Rasa1111 on 2010-09-04
> **ktp said:**
> search what is that?? :lolflag:

UF search function~ could be far better. 
That's what. lol  :P

---

### Post by Mr. Picklesworth on 2010-09-04
Run it in a terminal to get the error output. Last I checked, it was segfaulting when I closed the main window. The intended behaviour is it keeps running in the background as a service.

---

### Post by mc4man on 2010-09-04
> it was segfaulting when I closed the main window.
A few days ago it was only segfaulting when the status icon plugin was enabled, now it must from another of the default enabled plugins 
(or maybe more than one

If it mattered which one(s), wouldn't be hard to track down, process of elimination, ect.

(4 that can cause - status icon, ubuntuone music store, song lyrics, Jamendo

---

### Post by 23meg on 2010-09-04
> **ktp said:**
> Please see following thread...make sure to read the whole thing:

[http://ubuntuforums.org/showthread.php?t=1564913](http://ubuntuforums.org/showthread.php?t=1564913)

Merged with that thread.

---

### Post by mc4man on 2010-09-09
The issues with segfaulting because of some plugins have been resolved atm and rhythmbox will now hide without the use of the status icon. (clicking the X button will hide.
There does though now seem to be some possibilities of having sound pref.'s crashing, ie. no sound
[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/633897](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/633897)

---

### Post by ktp on 2010-09-09
thanks...marked the bug as affects me.

---

### Post by kyleabaker on 2010-09-09
I haven't finished downloading and installing the latest updates, but it looks like this behavior may now be fixed with an update..
[https://launchpad.net/ubuntu/+source/rhythmbox/0.13.1-0ubuntu4/+changelog](https://launchpad.net/ubuntu/+source/rhythmbox/0.13.1-0ubuntu4/+changelog)

Well see when installation finished. :/

---

### Post by mc4man on 2010-09-09
Seems a bit easier to crash now, one way - open from sound prefs., close with X button (not playing), then try to re-open from sound prefs.
The report indicates bug still open. (in progress

---

### Post by kyleabaker on 2010-09-09
Yep, its fixed now, but you restore the window from the sound menu. Thats how I expected it to work all along after the changes to the sound menu anyway so I'm quite pleased with the fix!

---

### Post by kyleabaker on 2010-09-09
> **mc4man said:**
> Seems a bit easier to crash now, one way - open from sound prefs., close with X button (not playing), then try to re-open from sound prefs.
The report indicates bug still open. (in progress

Yea, didn't catch that before you mentioned it. I guess I just won't be clicking the close icon while I'm not playing something, lol.

---

### Post by ktp on 2010-09-09
> **mc4man said:**
> Seems a bit easier to crash now, one way - open from sound prefs., close with X button (not playing), then try to re-open from sound prefs.
The report indicates bug still open. (in progress

this is exactly what i saw.

---

### Post by Jetro on 2010-09-25
> **ktp said:**
> Rhythumbox can still have it's "status icon" and hide the window.  You just have to enable it in the preferences.  You can use that to hide Rhythumbox using that until the feature is fully developed.
How to do the opposite of this? D: I hate that Rhythbox doesn't close, but just hides itself. And that it doesn't show up when I press the icon. -_-

---

### Post by mc4man on 2010-09-25
> I hate that Rhythbox doesn't close, but just hides itself. And that it doesn't show up when I press the icon. -_-

Well then don't enable the status icon plugin (of no great value anyway)

If rhythmbox is playing when you close it then it 'minimises' to sound preferences. If it's not playing then it will close out.

---

### Post by VMC on 2010-09-25
I noticed that on a recent install -todays iso, Rhythmbox now defaults to icon on the top panel like it was in Lucid.
It doesn't hide. Also it doesn't appear inside the volume indicator applet, as it did in previous iso installs.

---

### Post by mc4man on 2010-09-25
> I noticed that on a recent install -todays iso, Rhythmbox now defaults to icon on the top panel like it was in Lucid.
It doesn't hide. Also it doesn't appear inside the volume indicator applet, as it did in previous iso installs. 

See the same on a live cd, though disabled the status icon and it shows up.
(why it is a default enabled plugin doesn't make sense

---

