---
title: "Mouse arrow keeps disappearing..."
date: 2010-07-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-07-01
as the title says, the mouse keeps disappearing, have to move for it to show...

---

### Post by berthiggins on 2010-07-01
Mr too!

---

### Post by Framli on 2010-07-01
If you have the "unclutter" package installed (recommanded by ubuntu-desktop since a few days IIRC), it's not a bug, it's a feature! :D

---

### Post by .kelp on 2010-07-01
Isn't that a good thing? I had to install Unclutter just to get that effect.

---

### Post by dagrump on 2010-07-01
Something more to remember to uninstall, Thank you ubuntu.

---

### Post by MacUntu on 2010-07-01
> **.kelp said:**
> Isn't that a good thing?
No.

---

### Post by VMC on 2010-07-01
> **MacUntu said:**
> No.

Agreed! I didn't install Unclutter and my mouse is also disappearing.

---

### Post by dagrump on 2010-07-01
It's unclutter, remove it & restart X.
*****
they slipped it in the other day.

---

### Post by zekopeko on 2010-07-01
Why the hell did they install that? I thought the point was to make the cursor disappear when you are writing something not when you aren't doing anything.

---

### Post by mc4man on 2010-07-01
It's not the worst thing, some may like it. 
The only issue is the default idle value of 1 is too short and becomes an annoyance (idle time seems to be 2 sec's per 1

---

### Post by andrewabc on 2010-07-01
Pleaseee get rid of
*Are you sure you want to shutdown*
that pops up when you want to shutdown.

Pointless. Yes I know how to google to remove it (have to use gconftools, or input command into terminal), not sure on the reasons for it. You only have to mistakenly click on wrong shutdown/restart once to learn your mistake.

I agree with changing idle time for mouse to disappear from 1 second, to maybe 10 seconds.

---

### Post by mc4man on 2010-07-01
With an idle of 5 here it takes about 8 secs which works fine, with fs video better than moving the cursor off of an available  side

---

### Post by Anduu on 2010-07-01
I have been using unclutter since I first started running Ubuntu with Dapper.I love it.

If it weren't for this thread I never would have realised it had been added to the default install.

---

### Post by VMC on 2010-07-01
> **mc4man said:**
> With an idle of 5 here it takes about 8 secs which works fine, with fs video better than moving the cursor off of an available  side

Strange. If I type *unclutter* return it hangs. Ctrl+c to get cursor back. Also, if I type *unclutter -idle 5*, that to hangs, and Ctrl+c brings back cursor, but now the cursor doesn't disappear at all! *man unclutter* was of no help. What am I doing wrong?

---

### Post by kyleabaker on 2010-07-02
I've never used Unclutter in the past, but I'm getting used to it now. Seems to be useful for me so far. Too bad it can't fade out for a more astheticly pleasing appearance instead of simply disappearing.

---

### Post by tad1073 on 2010-07-02
I removed it because I didn't know how to configure it...seems to me that they would add it to System>Preferences>Mouse

---

### Post by mc4man on 2010-07-02
Don't see any way to configure thru gconf-editor or in preferences, though you'd think there would be.

So an edit here seems the way atm
```
gksu gedit /etc/default/unclutter
```

at least here about 1.5 sec.'s per 1 (-idle 5 = 8 sec.'s

---

### Post by kyleabaker on 2010-07-02
> **tad1073 said:**
> I removed it because I didn't know how to configure it...seems to me that they would add it to System>Preferences>Mouse

+1 You should file a bug against this any maybe they will fix it for Maverick.

---

### Post by BwackNinja on 2010-07-02
Its a real pain when you consider reading tooltips. Mouse pointer disappears, so does tooltip.

---

### Post by kyleabaker on 2010-07-02
> **BwackNinja said:**
> Its a real pain when you consider reading tooltips. Mouse pointer disappears, so does tooltip.
Tooltips remain for me. I just tested on Rhythmbox hovering the forward button.

The tooltip flashes off, but its immediately back on.

---

### Post by andrewabc on 2010-07-02
> **kyleabaker said:**
> Tooltips remain for me. I just tested on Rhythmbox hovering the forward button.

The tooltip flashes off, but its immediately back on.

Same situation for me.
Visual effects turned off.

---

### Post by BwackNinja on 2010-07-02
> **kyleabaker said:**
> Tooltips remain for me. I just tested on Rhythmbox hovering the forward button.

The tooltip flashes off, but its immediately back on.

I don't know about the other applications, but tooltips were disappearing for me on webpages in firefox. I uninstalled it, and then I no longer had any issues.

---

### Post by jerrylamos on 2010-07-03
Where is the mouse pointer idle time set?

Before Alpha 2, mouse pointer action was just fine.  How do I get back to that for the mouse pointer?

Thanks, Jerry

---

### Post by mc4man on 2010-07-03
> Where is the mouse pointer idle time set?
unless someone can provide you with some other means see post 17

---

### Post by tad1073 on 2010-07-03
> **mc4man said:**
> unless someone can provide you with some other means see post 17

[http://ubuntuforums.org/showpost.php?p=9536975&postcount=17](http://ubuntuforums.org/showpost.php?p=9536975&postcount=17)

---

### Post by mc4man on 2010-07-03
> 
Originally Posted by tad1073
Quote:
[QUOTE]Originally Posted by mc4man  
unless someone can provide you with some other means see post 17
[http://ubuntuforums.org/showpost.php...5&postcount=17](http://ubuntuforums.org/showpost.php...5&postcount=17)[/QUOTE]

"This is like deja vu all over again."
  --  Yogi Berra

---

### Post by tad1073 on 2010-07-03
> **mc4man said:**
> "This is like deja vu all over again."
  --  Yogi Berra
I didn't read the entire post

---

### Post by kansasnoob on 2010-07-16
I sure hope they don't make unclutter a hard dependency, it's incredibly annoying to me since I'm visually impaired.

---

### Post by mc4man on 2010-07-16
> I sure hope they don't make unclutter a hard dependency

I believe it was mentioned somewhere that it was included by mistake, so no worries there down the road.

---

