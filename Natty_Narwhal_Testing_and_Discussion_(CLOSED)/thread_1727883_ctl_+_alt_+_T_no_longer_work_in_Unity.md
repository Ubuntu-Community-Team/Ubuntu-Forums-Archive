---
title: "ctl + alt + T no longer work in Unity"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-04-13
It would be ridiculous to have to bring up the dash everytime to use the terminal and I don't want to waste the space in the Unity bar for the terminal (god knows, seeing that the dash is such a horrid way to find and launch applications the unity bar is going to be quite crowded) I am trying to use hotkey to bring up the terminal but it doesn't work anymore. Moreover, the old Preference > Keyboard Preference in the gnome terminal is no longer present either.

Now how am I supposed to bring up the terminal with the keyboard?

If users have to relearn something so basic from scratch and there is even no documentation for it I can't see how this would represent "progress" in UI design.

Sorry if I sound annoyed because I am. I can understand bugs (this is a beta after all) but I can't understand difficulty by design ("features" that make you want to scream)

---

### Post by Mr. Picklesworth on 2011-04-13
Hate to say this, but it's in CompizConfig right now :)
If I recall correctly, those shortcuts used to be handled by Gnome Panel or Metacity, neither of which exist in Unity. You can enable Compiz's Commands plugin to add in these sorts of things. (Yes, configuring Compiz is a pain. I hope someone works on that some day&#8230;)

For what it's worth, you can press Super + a number key to open any of the first 10 items in your launcher. Hold down the Super key and you'll get a little overlay over each item saying what its trigger is. I find it quite useful, though it is a bit to get used to (and maybe not quite as easy to press).

---

### Post by mc4man on 2011-04-13
You should get Ctrl+Alt+t in unity if you have the "Gnome Compatibility Plugin" enabled 
(ck. and if needed set in ccsm, there are conflicts that will be resolved vs. setting in gconf-editor

It's also what gives you the screenshot bindings

---

### Post by beew on 2011-04-13
> **Mr. Picklesworth said:**
> Hate to say this, but it's in CompizConfig right now :)
If I recall correctly, those shortcuts used to be handled by Gnome Panel or Metacity, neither of which exist in Unity. You can enable Compiz's Commands plugin to add in these sorts of things. (Yes, configuring Compiz is a pain. I hope someone works on that some day…)

For what it's worth, you can press Super + a number key to open any of the first 10 items in your launcher. Hold down the Super key and you'll get a little overlay over each item saying what its trigger is. I find it quite useful, though it is a bit to get used to (and maybe not quite as easy to press).

Well I don't want to put the terminal on the Unity bar and I don't want it to be overly crowded either. 

As for ccsm it is not even installed by default (Mark S's "zero configure experience"?)and I have not been using it much because everytime I did Compiz crashes. I am just sick of having to reboot everytime I change a setting. It would be a very effective way to deter people from configuring too much, which the Unity team seems to hate.

---

### Post by beew on 2011-04-13
> **mc4man said:**
> You should get Ctrl+Alt+t in unity if you have the "Gnome Compatibility Plugin" enabled 
(ck. and if needed set in ccsm, there are conflicts that will be resolved vs. setting in gconf-editor
Thanks, will try that when I am prepared for another crash.

 But the point is I shouldn't have to configure ccsm (how many "new users" would know about ccsm? It is not even installed by default). Something so basic should be built in. Sorry for the rant, but I get frustrated very quick with Unity.

---

### Post by Mr. Picklesworth on 2011-04-13
Ah, my mistake, Compiz handles this as well through Gnome Compatibility. The application you want is the same old Keyboard Shortcuts. Just search for it under the Control Centre. My &#8220;Open a terminal window&#8221; shortcut changed to Disabled as well for some reason (maybe the dconf migration script?), but I changed it back just now and it's working as it should.

Edit: Err, yeah, what mc4man said :)

---

### Post by beew on 2011-04-13
> **Mr. Picklesworth said:**
> Ah, my mistake, Compiz handles this as well through Gnome Compatibility. The application you want is the same old Keyboard Shortcuts. Just search for it under the Control Centre. My “Open a terminal window” shortcut changed to Disabled as well for some reason (maybe the dconf migration script?), but I changed it back just now and it's working as it should.

Edit: Err, yeah, what mc4man said :)

Thanks. Found it.

---

### Post by mc4man on 2011-04-13
> But the point is I shouldn't have to configure that. Something so basic should be built in.
It is the default - if you did a fresh install or even created a new user, you'd get it.

There are currently a few plugins that will. when enabling or disabling in ccsm,   unset all  the plugins, maybe that happened to you? 
In that case it's quite easy to not re-enable all that one may want or need.

---

### Post by beew on 2011-04-13
> **mc4man said:**
> It is the default - if you did a fresh install or even created a new user, you'd get it.

There are currently a few plugins that will. when enabling or disabling in ccsm,   unset all  the plugins, maybe that happened to you? 
In that case it's quite easy to not re-enable all that one may want or need.

It is a fresh install. I wouldn't upgrade my 10.10 to this mess. :)

---

### Post by Visceral Monkey on 2011-04-13
Woot. Still works by default in Gnome 3 ;)

---

### Post by beew on 2011-04-13
Just want to report Compiz crashed again after I set gnome compatibility in ccsm>

---

### Post by mc4man on 2011-04-13
> It is a fresh install
When I say 'fresh install' I sorta mean a recent .iso if not the current one.

I do a 'fresh' install at least once a week and can virtually guarantee you that gnomecompat is a default active plugin. ( at least as recent as 04/08

As far as a 'mess' - far from it. Though that's not to say any one person's current 'accumulated' install couldn't be  a bit of a mess for any number of reasons

> Just want to report Compiz crashed again after I set gnome compatibility in ccsm>
That's a known, being worked on bug, in most cases unity/compiz will reset though generally good practice to do a logout/in afterwards

---

