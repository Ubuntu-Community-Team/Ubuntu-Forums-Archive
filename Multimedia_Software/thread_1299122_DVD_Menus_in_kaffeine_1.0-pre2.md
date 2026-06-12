---
title: "DVD Menus in kaffeine 1.0-pre2"
date: 2009-10-23
forum: Multimedia Software
---

### Post by sneakers563 on 2009-10-23
I'm running the Kubuntu Karmic Koala beta.  I've been playing dvd's with Kaffeine 1.0-pre2 and everything is good EXCEPT I can't figure out how to skip directly to the dvd menu, either from the endless "coming soon on dvd" nonsense or from inside the movie.  I had no problem with this in 0.7, it the option was in the right-click popup.  I haven't seen anyone else complaining about this, so I assume that I'm just missing something, but what?

I have libdvdcss, libdvdnav4, libdvdread4 installed.  After the movie has ended and it goes to the menu, I can navigate around the menu fine, but I don't know how to go directly there.

---

### Post by dwasifar on 2009-11-05
I had the same problem.  No DVD menu option, no way to get to them, the traditional 'D' keyboard shortcut didn't work.  Also, there was no way to mount a folder containing DVD files.

I fooled with it a while and then said the hell with it, uninstalled 1.0-pre2, and went back to the 0.87 version shipped with Jaunty.  It's at [http://packages.ubuntu.com/jaunty/amd64/kaffeine/download]("http://packages.ubuntu.com/jaunty/amd64/kaffeine/download") if you want to go that route.  Works fine for me.  

Are you using KDE or Gnome?  I'm using Gnome.  Perhaps 1.0-pre2 just doesn't want to run without the full KDE desktop installed.

---

### Post by Krister Hallergard on 2009-11-29
Am using Kubuntu and my situation is similar to yours. I have my DVD collection on a hard drive and use a remote control to watch the DVD:s on the TV screen: 

1. How to start a DVD from a drive (rather than from a disk) 
2. Are there any keyboard shortcuts to navigate the DVD menu?

---

### Post by Krister Hallergard on 2009-12-03
Shall I conclude that it is not at present possible to start a DVD from the hard disk?  Also there are no possibility to use keyboard shortcuts to navigate the DVD menu?  Correct?

---

### Post by SunnyRabbiera on 2009-12-03
Kaffeine in KDE 4 to me is junk, I would actually install totem, or smplayer, or VLC, or xine...
All are much better players anyhow

---

### Post by Krister Hallergard on 2009-12-03
Thanks Sunny, I agree, actually thought all KDE4 wass junk, but recently I started to realize some benefits when I finally tried to get it going.  One important benifit is the Folder View widget in my opinion.

I only used three KDE3 things: Konqueror, Kaffeine and Amarok.  On all three I have experienced regression.  I am now confident to use Konqueror again.  Kaffeine I think is actually better now for DTV, but for DVD:s I now prefer VLC.  Amarok started with mainly minuses compared to the old one, but now I feel there are some pluses as well.  So I think we have to give the developers some time space.

Still I wish that I could play DVD:s from the hard disk and navigate the DVD menus with keyboard shortcuts (in my case using irxevent keyboard comands)

---

### Post by Krister Hallergard on 2009-12-04
In another forum I have now learnt that I can start a DVD on the hard disk by entering the folder (kaffeine /path/ rather than kaffeine dvd:/path/ as in kaffeine with KDE3).

I still have not had any replies to my question how to navigate the DVD menu. Suppose I can use PageDown and PageUp to switch to the next/previous chapter, but that is not really using the DVD menu is it. So for now I prefer using VLC.

---

### Post by Krister Hallergard on 2009-12-05
> kaffeine dvd:///path/ actually works best.  Remains how to navigate the DVD menu using the keyboard?

---

### Post by madmax75 on 2010-08-01
> Remains how to navigate the DVD menu using the keyboard?     The same problem here. Some dvd menus work fine, but then others cannot be accessed with a mouse at all, so it's kind of sketchy. And if you can't do it with a mouse, you're out of luck with Kaffeine. No way to choose and access dvd menu entries with a keyboard AFAIK. Same with any other playback program really, some dvd menus just don't work.

[LEFT]Kaffeine version: 1.0-svn3 (using it on Ubuntu Linux Lucid Lynx 10.04)
[/LEFT]

---

### Post by madmax75 on 2010-08-02
Playback -> Toggle Menu
Playback -> Title...
Playback -> Chapter

These gives you some control on the dvd menus. With Playback -> Title I could access all the extras in a dvd by skipping the dvd menus altogether. All you get is a numbered list, but with a little bit try and search I could watch all the extras.

---

### Post by sneakers563 on 2010-10-06
I ended up going to VLC and never looked back.

---

