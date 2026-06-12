---
title: "How to switch-off global menu?"
date: 2011-02-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sophont on 2011-02-18
I'm desperately looking for a way to turn-off the annoying global menu. But no luck so far.

I can only hope there is a setting in gconf that allows me to get rid of this anti-feature. I don't need a GUI - I'll take any hackkish solution as long as I can get the old menus back.

I've been a big fan of Ubuntu for ca 5 years now (since edgy IIRC). 
I always liked clean Gnome interface and what Ubuntu did with it (I always removed the bottom panel though).

I'm open for change. PulseAudio is better than sliced bread. Moving the window controls from right to left never bothered me much (and can be changed if needed anyway).
Most of Unity is fine. It doesn't do much for me - but doesn't bother me much either. And I can see why the Unity panel is nice on touch devices.

I can even see the point for a global menu on small display devices which rarely have more than 1 app open anyway - but on 15+ inch desktop screens it makes no sense. Always found it highly annoying on Macs and it was one of the reasons I never got a Mac.

If I can't get rid of the stupid global menu I have to look for another distro - which would make me sad - so please - somebody tell me that there is a setting somewhere to disable this most horrible (on a large screen desktop where I don't maximize my windows all the time) anti-feature.

---

### Post by mc4man on 2011-02-18
If you use the gnome-panel (Classic) login then no global menu it you don't want one

In the unity (Desktop) login you're free to keep menu's in any app's window you wish, only takes a simple edit to each app's .desktop
(or a binary diversion if you start a gui app from the terminal

---

### Post by hugmenot on 2011-02-19
It’s enabled in this file:

```
$ cat /etc/X11/Xsession.d/80appmenu
if [ -f /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so ]
then
	export UBUNTU_MENUPROXY="libappmenu.so"
fi

```

Either you removing appmenu-gtk or this file should do it.

---

### Post by Starks on 2011-02-19
> **mc4man said:**
> If you use the gnome-panel (Classic) login then no global menu it you don't want one

In the unity (Desktop) login you're free to keep menu's in any app's window you wish, only takes a simple edit to each app's .desktop
(or a binary diversion if you start a gui app from the terminal

Umm, no.

Classic is also global menu now.

---

### Post by mc4man on 2011-02-19
> **Starks said:**
> Umm, no.

Classic is also global menu now.

Sure you can, your free to  choose to use the global menu in the classic login, or not at all
(no packages need to be removed, nor hugmenot's method

In the unity login the method mentioned by hugmenot does work, just means when maxed no global menu either. (vs. doing on an individual app basis for apps that one would never max.

---

### Post by Sophont on 2011-02-20
> **mc4man said:**
> Sure you can, your free to  choose to use the global menu in the classic login, or not at all
(no packages need to be removed, nor hugmenot's method

In the unity login the method mentioned by hugmenot does work, just means when maxed no global menu either. (vs. doing on an individual app basis for apps that one would never max.

Thanks for the replies.

Changing to "Classic Login" or "Classic Login (No efffects)" does *not* get rid of the damn global menus (fresh install from a nightly CD image few days ago into VBox 4 VM).

What did you mean by "your free to  choose to use the global menu in the classic login"?
Is there an additial settings I have to change besides switching to "Classic Login"?

It's not the Unity Launcher that I want to get rid off - I can get used to that. It's the global menu (1 menu in top panel instead of menu in every applications window) that's annoying me no end.

---

### Post by mc4man on 2011-02-20
> What did you mean by "your free to choose to use the global menu in the classic login"?
Is there an additial settings I have to change besides switching to "Classic Login"?
In the Classic login the global-menu is like anything else in a panel - an applet, so just r. click on it > unlock > remove 
Once removed sometimes it can be added back, sometimes the choice 'disappears' from the add to panel dialog box.(indicator applet appmenu

> It's not the Unity Launcher that I want to get rid off - I can get used to that. It's the global menu (1 menu in top panel instead of menu in every applications window) that's annoying me no end. 


In unity login you need to do as was previously posted by hugmenot or as mentioned apps can be set indiviually as whether to use the gm or not (just ask if interested in that.

---

### Post by Sophont on 2011-02-21
> **mc4man said:**
> In the Classic login the global-menu is like anything else in a panel - an applet, so just r. click on it > unlock > remove 


{lightbulb above my head lights up}
Thanks - I didn't realize that the global menu is linked to that Applet (obviously that it shows the global menu, but not that menus would re-appear in apps if the applet gets removed).

Yup - that worked fine. Much better.

---

### Post by blueadept on 2011-02-22
Seems to me that this is a feature people should rather have to turn on, not off if they select "Classic Desktop"...

---

### Post by jennybrew on 2011-02-22
> **blueadept said:**
> Seems to me that this is a feature people should rather have to turn on, not off if they select "Classic Desktop"...

Having read Mr Shuttleworth's various comments and read various reviews of the new system I understand the intention is to move away somewhat from the desktop metaphor we have all got used to.
I think having a global menu is all part and parcel of that and probably we are being presented with something which looks and feels a bit like a browser.
Thats a significant change and very brave of Ubuntu to do. However I do have some doubts about the actual implementation and have said so in another thread re: GUI's.

Why is the Classic Desktop there as a log in option ? Well I guess its there for those folks who still like the desktop metaphor. If that is the case I agree. It should be a feature which people should have to turn on.

As an aside I dont think we see enough about about design issues in these forums. There is a strong focus on getting things to work rather than getting things well designed.
I wonder why that should be?

---

### Post by cariboo on 2011-02-22
The forums is not the place for feedback, and thoughts on what is taking place. If you want to have your thoughts seen, I would suggest you become a member of the [Ayatana Team]("https://launchpad.net/~ayatana")

---

### Post by psusi on 2011-02-23
I like the global menu, but only for maximized windows.  I really wish it wouldn't bother when I'm looking at multiple unmaximized windows.

---

### Post by beew on 2011-03-13
I removed the file 
/etc/X11/Xsession.d/80appmenu but still cannot get rid of the global menu. Am I missing something?

---

### Post by 23dornot23d on 2011-04-18
This sorted it for me ..... am happy again can use UNITY at last ....... ;)

Seeing that the top 1/2 inch of my tv screen is hidden and cannot be changed or resized ...:confused: having all my menus up in that space was like - having all your menus removed completely ....
so much fun while it lasted lols :lolflag: 

Glad we have some sanity back in the house now ....... with

[B]sudo apt-get remove appmenu-gtk


( well almost - just no idea what they have done to firefox .... whats with the menu ..... in Gnome-shell cannot select it and in UNITY its still hidden in the top panel  ..... you finally got me to use google-chrome well done )

[/B]Days left to New Release - [LINK]("http://ubuntu.touchlay.com/urb/11.04")

---

### Post by mc4man on 2011-04-18
> just no idea what they have done to firefox .... whats with the menu ..... in Gnome-shell cannot select it and in UNITY its still hidden in the top panel
In firefox it's an extension - just open firefox - tools - addons - extensions and disable (or remove the package in synaptic, search appmenu
for qt4 apps, if any, then remove appmenu-qt

(or any app can be disabled individually if one wanted to keep 'global menus'

---

### Post by 23dornot23d on 2011-04-18
Cheers will do that ... thanks for the quick reply ..... wonder why it stopped me selecting it in gnome-shell ...... even though the menu was visible .... not selectable .....

bizarre ,,, only updated the other day was this the latest addition. :confused:

[IMG]http://img709.imageshack.us/img709/4286/screenshot7ov.jpg[/IMG]


Wow you have now just got another UNITY user ... >>>> Me <<<<<   its now almost useable for me ....

---

