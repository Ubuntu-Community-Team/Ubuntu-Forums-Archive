---
title: "Way to keep xrandr settings after reboot"
date: 2008-09-17
forum: Multimedia Software
---

### Post by winrowc on 2008-09-17
Okay so Im not completely knowledgeable about video settings, but I finally got my dual monitor setup to work. Unfortunatly though to do so I have to type:

```
xrandr --output DVI-0 --off

and then


xrandr --output DVI-0 --auto --right-of VGA-0
```

So this turns off one monitor and then uses xrandr or whatever that is to give me dual monitor support. Is there a way to keep these settings after reboot? I wasn't successful in my searches. 

I tried just using hibernate as a way around it but even that doesnt work, I assume because X is restarted (?).

Also: I am getting some neon green lines on top of my panels. Well on the bottom of the top panel (taskbar? whatever you call it)... I am running compiz fusion icon at start up so I assume its something to do with the video effects. Any suggestions? Its not really bothersome , and I'd rather have the effects than get rid of the lines...

---

### Post by winrowc on 2008-09-17
Nevermind: the green lines were just a shadow thing I just disabled it and reloaded the window manager and it fixed it.

---

### Post by winrowc on 2008-09-17
Anyone? Is it just a question of getting xrandr to start at startup? Im not quite sure what exactly xrandr is, I just know it fixes all the problems I had with dual monitors.

---

### Post by winrowc on 2008-09-18
Well I guess no one could help me but for others with this problem, this page helps:

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

### Post by fffuusky on 2008-09-18
bump up lurk&#12288;&#12288;When the young waitress in the caf&#233; in Tom's building started waving hello everyday. Tom was flattered, for she was at least 15 years younger than he. &#12288;&#12288;One day she waved and beckoned to Tom again. When Tom strolled over, she asked, "Are you single?" &#12288;&#12288;"Why, yes," Tom replied, smiling at her broadly. &#12288;&#12288;"So is my mom," she said. "Would you like to meet her?"--------------------------------The WoW Power Leveling ( World of warcraft Power Leveling ) site offer buy [WoW Power Leveling](http://www.powerlevelingweb.com), cheap [WoW Power Leveling](http://www.igsstar.com), free [wow power leveling](http://www.wowgoldweb.com), 1- 70 level [wow power leveling](http://www.sf10001.cn) and [wow power leveling](http://www.powerleveling-wow.com/siteMap.asp) news!

---

