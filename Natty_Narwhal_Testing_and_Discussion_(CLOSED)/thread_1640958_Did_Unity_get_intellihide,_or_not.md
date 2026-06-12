---
title: "Did Unity get intellihide, or not?"
date: 2010-12-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Bou on 2010-12-08
Hi guys,

I recently read [this post on OMG! Ubuntu!]("http://www.omgubuntu.co.uk/2010/12/intellihide-added-to-unity-launcher/") but have been unable to find such goodness in my Unity install afterwards.

Do you know if Unity does have intellihide, or not?

---

### Post by castrojo on 2010-12-08
It landed on trunk but it's not in Natty yet. You'll see it in natty Thursday/Friday probably.

---

### Post by screaminj3sus on 2010-12-08
I can't find any preferences to change settings in the unity dock period.

---

### Post by castrojo on 2010-12-08
It's not user visible yet, if you launch ccsm you can check the box for it and for float.

See here: [http://askubuntu.com/questions/9865/will-the-unity-launcher-auto-hide/9881#9881](http://askubuntu.com/questions/9865/will-the-unity-launcher-auto-hide/9881#9881)

---

### Post by MacUntu on 2010-12-08
(Very) Short clip of Intellihide in action: [http://www.youtube.com/watch?v=dj6ciufcz7w](http://www.youtube.com/watch?v=dj6ciufcz7w)

As mentioned, it currently has some issues with restoring windows from the launcher bar that overlap (panel won't hide).

---

### Post by donniezazen on 2010-12-08
Are icons in Unity going to get individual menu like in Gnome-panel? Or will there be only two options Pin or quit?

---

### Post by castrojo on 2010-12-08
Yes those are called Quick Lists, but they're not really finished. 

If you launch Tomboy and you right click you should see them there (one for each note).

Eventually you'll have handy things to do there, for example "Compose new mail" for your mailer icon or "Burn a new disc" in Brasero; things like that.

---

### Post by screaminj3sus on 2010-12-08
One basic thing it lacks is dragging icons to move them to a different place in the dock.

---

### Post by castrojo on 2010-12-08
Yeah that will come eventually, now that the main porting to Unity is done we can start to get the basic functionality back.

---

### Post by VMC on 2010-12-08
Will we be able to resize the left side docking panel, at some point?

---

### Post by cariboo on 2010-12-08
From looks of what I've seen on the Ayatana mailing list, it's going to stay at 52px wide. In order to get the look the devs want, they can't use icons smaller than 48X48, as anything smaller, 32X32 for example are fuzzy and not clear.

---

### Post by go7Ul1ai on 2010-12-08
> **cariboo907 said:**
> From looks of what I've seen on the Ayatana mailing list, it's going to stay at 52px wide. In order to get the look the devs want, they can't use icons smaller than 48X48, as anything smaller, 32X32 for example are fuzzy and not clear.

Time for a new icon set? :D

---

### Post by DBO on 2010-12-08
> **screaminj3sus said:**
> One basic thing it lacks is dragging icons to move them to a different place in the dock.

I have this almost done in a branch. It will probably land Friday or late Thursday

---

### Post by kyleabaker on 2010-12-08
Well this thread is just a little goldmine of Unity dock/panel info. :D

---

### Post by Bou on 2010-12-09
> **MacUntu said:**
> (Very) Short clip of Intellihide in action: [http://www.youtube.com/watch?v=dj6ciufcz7w](http://www.youtube.com/watch?v=dj6ciufcz7w)

Wow, cool. I also dig the new "arrow" signalling the active app.

---

### Post by zekopeko on 2010-12-09
> **Bou said:**
> Wow, cool. I also dig the new "arrow" signalling the active app.

From what I can tell active apps also get the background color which is more prominent. The launcher still looks crappy do (compared to the one in the first release).

---

### Post by DBO on 2010-12-09
> **zekopeko said:**
> From what I can tell active apps also get the background color which is more prominent. The launcher still looks crappy do (compared to the one in the first release).

I know I am going to regret this...

What dont you like?

---

### Post by VMC on 2010-12-09
Another bit of oddity, when you minimize a game it goes into the dock on the right but the time keeps going. Using gnome when you minimize a game , time stops. Maybe an oversight.

---

### Post by MacUntu on 2010-12-10
> **VMC said:**
> Another bit of oddity, when you minimize a game it goes into the dock on the right but the time keeps going. Using gnome when you minimize a game , time stops. Maybe an oversight.

```
ubuntu-bug unity
```

---

