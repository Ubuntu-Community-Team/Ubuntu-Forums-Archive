---
title: "Exiting programs"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by canadianwriterman on 2011-04-18
I find the ability to exit (completely close down) programs annoying in Natty Beta 2. 

For example, there seems to be no way to exit Banshee once it has been opened. Although Banshee opens full screen and, therefore, there is a menu in the top bar, there appears to be no "exit" item. I only see a "close" item under the "media" tab. Clicking on the red X in the top left corner also merely closes Banshee, but does not shut it down.

Also, Pidgin must be will not show you a menu until you make it full screen. Who wants to run Pidgin full screen just so you can see a menu and find the exit item to close it down?

Sorry if this issue has been covered elsewhere. I couldn't find it using the search function.

---

### Post by dino99 on 2011-04-18
bugs not reported are not bugs, so its up to you

---

### Post by bluenova on 2011-04-18
> **canadianwriterman said:**
> I find the ability to exit (completely close down) programs annoying in Natty Beta 2. 

For example, there seems to be no way to exit Banshee once it has been opened. Although Banshee opens full screen and, therefore, there is a menu in the top bar, there appears to be no "exit" item. I only see a "close" item under the "media" tab. Clicking on the red X in the top left corner also merely closes Banshee, but does not shut it down.
My experience with Banshee is if a song is playing it will 'close' if a song is not playing it will 'exit'.

> **canadianwriterman said:**
> Also, Pidgin must be will not show you a menu until you make it full screen. Who wants to run Pidgin full screen just so you can see a menu and find the exit item to close it down?
I think you are missing the point of Global menu. The menu is always in the same place at the top of the screen, regardless of whether an app is maximized or not. When an app is active (in the fore-ground) and you roll your mouse over the menu area it will appear. This doesn't please a lot of people (including myself) but this is the correct default behaviour at the moment.

> **canadianwriterman said:**
> Sorry if this issue has been covered elsewhere. I couldn't find it using the search function.

No need to be sorry, that is what forums are for.

> **dino99 said:**
> bugs not reported are not bugs, so its up to you

Nice, that's real helpful of you. The OP didn't mention anything about bugs, this is an intended behaviour issue.

---

### Post by canadianwriterman on 2011-04-19
Thanks, Bluenova. I see how the global menu works now... it's going to take some getting used to. As for the Banshee quit function, it does seem to quit when you close with no song running, although I still find it a bit odd that the "Close" function works differently from other programs, which have a "Quit" function. 

Overall, I find the Unity interface is OK, but am annoyed by the launch bar appearing and disappearing every time my mouse happens to be be too far to the left of the screen.

---

### Post by mafitzpatrick on 2011-04-19
canadianwriterman: You can configure the unity dock to always stay visible by installing Compiz Configuration Settings Manager. You can find more info on this thread here: [http://ubuntuforums.org/showthread.php?t=1732671](http://ubuntuforums.org/showthread.php?t=1732671)

It makes it far more usable for me at least.

I just wish there was a way to make the global menu stay visible at the top. I find things appearing/disappearing really distracting and frustrating.

---

### Post by canadianwriterman on 2011-04-19
Thanks, Mafitzpatrick. I'll give it a whirl. I've been playing with the Unity interface and, as you say, it's annoying to have things appearing and disappearing. In practical terms, it means having to "be careful" all the time.

---

### Post by SushiR on 2011-04-19
Pidgin can be closed with "Strg + Q".

---

### Post by mc4man on 2011-04-19
> As for the Banshee quit function, it does seem to quit when you close with no song running, although I still find it a bit odd that the "Close" function works differently from other programs, which have a "Quit" function. 
That's nothing new for players that use the 'sound preferences' menu (atm amarok, banshee, rhythmbox, exaile

The only way to exit the player is to stop it first, then exit from the player -  there is  no 'exit' available in sound preferences 
The whole deal feels like it was 90% implemented, but never quite finished.

---

### Post by beew on 2011-04-19
> **mc4man said:**
> That's nothing new for players that use the 'sound preferences' menu (atm amarok, banshee, rhythmbox, exaile

The only way to exit the player is to stop it first, then exit from the player -  there is  no 'exit' available in sound preferences 
The whole deal feels like it was 90% implemented, but never quite finished.


In 10.10 you can exit both Banshee and Amarok by right clicking and choose "exit" from the tray icon. But they don't have tray icons in Unity unlesss you edit some whitelist. I have yet to looked up on that (another regression in order to accommodate the anti-feature known as the global menu)

---

### Post by mc4man on 2011-04-19
> **beew said:**
> In 10.10 you can exit both Banshee and Amarok by right clicking and choose "exit" from the tray icon. But they don't have tray icons in Unity unlesss you edit some whitelist. I have yet to looked up on that (another regression in order to accommodate the anti-feature known as the global menu)

That's the systray, rather than 'sound pref's'
At some point the systray may be gone for good so it would be nice if there was more control there.
Atm I've added a few things to the whitelist - Ex. (also keeping the defaults for the moment
```
gsettings set com.canonical.Unity.Panel  systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'Vlc', 'Audacious', 'Opera', 'Exaile']"

```
I do use the global menu but have returned menus for many things like  - 
vlc, audacious, gnome-terminal, gedit, gimp and probably a few others as they're installed (certainly any media player, small window app and anything I may open multiple instances of

(I've always thought the global menus should only be with maxed windows, but that'll never happen or even be a choice

---

### Post by mafitzpatrick on 2011-04-19
> **beew said:**
> I have yet to looked up on that (another regression in order to accommodate the anti-feature known as the global menu)

The link I posted above explains the whitelist too. I don't think the problem is with the global menu per se (File... up top) its the lack of polish on application integration. 

All the disappearing panels pop in out close buttons missing... Now that's a *problem* because it means if you're looking for a way to close an application it takes twice as long to accomplish. Annoyingly I do like the dock+global menu arrangement, but Unity seems to do it badly. Now, if only there were config options...

---

