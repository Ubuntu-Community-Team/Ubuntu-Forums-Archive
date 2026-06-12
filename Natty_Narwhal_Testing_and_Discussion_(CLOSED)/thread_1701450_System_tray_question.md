---
title: "System tray question"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sffvba[e0rt on 2011-03-06
Hi,

I have a question about the system tray in the top right hand corner in Unity.  I like to run applications and tell them to minimize to this area so I can keep them running but keep them out of the way (I can think of X-Chat, KeepassX) but does far none of the applications seem to be able to put an icon in this area... Once I minimize it becomes impossible for me to bring the application back up (alt-tab etc. doesn't work and there is no icon for me to use).

Is this area supposed to work this way or is there something else wrong?


Cheers
404

---

### Post by lucazade on 2011-03-06
> **not found said:**
> Hi,

I have a question about the system tray in the top right hand corner in Unity.  I like to run applications and tell them to minimize to this area so I can keep them running but keep them out of the way (I can think of X-Chat, KeepassX) but does far none of the applications seem to be able to put an icon in this area... Once I minimize it becomes impossible for me to bring the application back up (alt-tab etc. doesn't work and there is no icon for me to use).

Is this area supposed to work this way or is there something else wrong?


Cheers
404

If I remember well only white-listed apps could use legacy notification area in Unity (skype, wine..). Maybe you should ask to ayatana mailing list or irc channel how to allow a new app to use old systray.

---

### Post by terry_gardener on 2011-03-06
the top right is now used for indicators. 

for example rhythmbox under the sound icon and network etc. 

when you open app and then minimise the app it is stored in the unity launcher and is represented by a white triangle on the left of the app icon. 

to open the minimised app click the icon that represents the app in question.

---

### Post by sffvba[e0rt on 2011-03-06
Thanks for the replies... had a chat to the guys on #ayatana and they basically explain this to me too...

Just got to change my habits I guess :)


Cheers
404

---

### Post by lucazade on 2011-03-06
[http://www.webupd8.org/2011/02/unity-systray-is-back-themable-top.html](http://www.webupd8.org/2011/02/unity-systray-is-back-themable-top.html)

look at this post!

edit: i've seen your latest post when I've refreshed page.

---

### Post by cariboo on 2011-03-06
For Xchat at least, if you install xchat-indicator, the envelope icon changes color, when someone pings you. Most application icons in the panel wiggle, when your attention is needed.

There is also a list of keybaord shortcuts available [here]("http://askubuntu.com/questions/28086/keyboard-shortcuts-in-unity"). There was a wiki page, but it seems to no longer be available.

---

### Post by sffvba[e0rt on 2011-03-06
Thanks to all!

---

### Post by dsonck on 2011-04-01
I know this question is solved but this seemed the best place for my message.

If you definitely want your system tray back (like me:P), you could use StandaloneTray (stalonetray). When I saw that Unity removed the system tray, I knew that there was a package that gives windowmanagers like windowmaker and openbox a system tray. It works perfectly (after some tweaking) in Unity too.

Somehow Compiz sees the system tray as a panel (:)) and resizes windows accordingly.

I managed (with this .stalonetray file) to get the system tray on the right side and high enough for an 1080p screen.
```

grow_gravity N
icon_gravity S
geometry 1x44-0-0
background "#3C3B37"

```It work best with the ambiance style (dark background). If you don't have the same resolution, you'll have to try adjusting the 44 to something appropriate.

I hope this message will help people in desperate need of a system tray.

---

### Post by cariboo on 2011-04-01
What do you do about applications that use the app-indicator area, like brasero, do you still get an icon in the old style system-tray?

---

### Post by mc4man on 2011-04-01
You are free to add apps that can use systray to the systray whitelist, then test and see if the app works correctly, AND if there are any ill effects else where. If not suitable then you'd simply remove. (and or disable in app preferences

And if it does work ok, also take a look variations when minimizing to tray and or launcher. (I've found with the 2 tested so far to minimize to systray by clicking on icon in systray is preferred 

So here both vlc and banshee, neither which atm  use sound preferences, work absolutely fine from the systray and also bring back track change osd, ect.

Can be done directly in dconf-editor or cli using gsettings

---

### Post by dsfitzpat on 2011-04-05
Right now I'm running Natty Beta 1 on my netbook, via an upgrade from 10.10.  Is there a way to get a system tray running so that I can get notifications from update-notifier and apport?
I know the update system changed a few versions ago, but I always liked having the little update icon on my panel as a passive notification when I have updates.  It worked in 10.10 running the UNE Unity, but no longer in 11.04.
Apport is probably the bigger issue right now while testing the beta version - I'm not getting any crash reports!  I logged into the Ubuntu Classic session and got about a dozen crash reports all at once from crashes that occurred in a unity session, without any notification.
Is anyone else having this problem?

---

### Post by skibler on 2011-04-07
You can adjust the white list, see this link:
[http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/)

If adding things to the white list one by one seems like a giant pain in the butt, you can just white list everything:
```

gsettings set com.canonical.Unity.Panel systray-whitelist " [ 'all' ] "

```

What a silly situation! If you install a new program, how are you supposed to know if it even has a system tray icon to white list?

---

### Post by dsfitzpat on 2011-04-07
Thanks, I'll give this a try.  White-listing everything might be the best bet - I never found that my notification area was all that crowded (perhaps I'm not multitasking enough?)
I much prefer having things like update notifications in the panel where I can ignore them for a while if I'm busy working, as opposed to having the update manager jump out at me.  Right now I'm also dealing with a weird bug where I only get apport crash notifications in Ubutnu Classic - again since the crash icon usually appears in the notification area, and Ubuntu Classic still uses the older version.

---

