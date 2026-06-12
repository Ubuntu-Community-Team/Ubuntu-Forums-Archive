---
title: "Help with ET freezing"
date: 2009-01-31
forum: Multimedia Software
---

### Post by noclueatall21 on 2009-01-31
I've installed wolfenstein enemy territory. the problem i am having is the fact that when i run the game it becomes extremely choppy and i get no sound and than when it gets to the menu to enter your character name and setup your specifications it freezes or moves even slower. from this screen i can see my mouse and when i try to move it i lose it and i can't find it again. also on that menu it says my graphics settings are set to high. so i figure it has something to do with my video driver. so i tried to get an updated driver by going to applications>system>hardwaredriver. it updated my nvidia driver to version 177. i only chose it because it says recommended. 

first my question is this how do i know this is even the right driver for my card? also how do i stop it from running the game in the highest setting because i believe this may be the cause of the problem. but again i am not sure i just installed xubuntu today and wanted to try this out instead of windows. i like it but there are so many little things i have to do that are extra just to get something to work and i'm not sure its even worth it.

also don't assume i have any skills with shell commands. i'm still trying to figure out what terminal and shell even mean.

---

### Post by ohgodnotanother1 on 2009-02-04
It's hard to help you when you don't exactly describe how you run the game.

Since the game sounds familiar to me I suppose that you tried to run it through Wine. It's a Windows "emulator". If so here is a nice site where you can get more information about running specific games with Wine: [http://appdb.winehq.org/](http://appdb.winehq.org/)


Regarding you graphic card: I don't used to rely on graphical tools to upgrade my hardware, since I don't see whats actually happening - so it could download something I don't need.

Type in lspci into a terminal window and check the output. Look for something with Nvidia (if that's your card manufacturer). Mine look like this:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

Drivers can be obtained from the website of the manufacturer. Hopefully they supply a README so you know how you can install it. At least ATI provides one. However installing the driver is not very easy and as you mentioned that you have little knowledge yet, I would not recommend you to do it.

For now, please tell us how you try to run the game and what the "lspci" output for your graphic card looks like.
Maybe you can also run "fglrxinfo" and paste the output. But that's only important if you intend to use OpenGL in your games.

---

### Post by Tomatz on 2009-02-04
If you run compiz you may have to disable compiz first (depending on your system specs).

run the command:

```
metacity --replace
```

To temporarily disable compiz. If it works you can use **compiz switch** (below) to turn compiz on and off easily ;)

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

