---
title: "The Unity launcher default layout has been updated."
date: 2011-03-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Starks on 2011-03-21
As of Unity 3.6.6:

- Nautilus
- Firefox
- LibreOffice writer
- LibreOffice calc
- LibreOffice impress
- Software center
- Ubuntu One control panel

Run 'unity --reset-icons' from Alt+F2 to see the change.

Screencap: [http://i.imgur.com/PMfxB.png](http://i.imgur.com/PMfxB.png)

---

### Post by t1497f35 on 2011-03-21
Are there any plans to make the Unity icons smaller or to add an option to make them smaller?

---

### Post by Starks on 2011-03-21
There is an option in the Unity settings of the CompizConfig Settings Manager.

32 pixels wide is the smallest, I think.

---

### Post by kerry_s on 2011-03-21
> **t1497f35 said:**
> Are there any plans to make the Unity icons smaller or to add an option to make them smaller?

There is no option in version 10.10 if that's what your asking about.

---

### Post by VinDSL on 2011-03-21
> **Starks said:**
> There is an option in the Unity settings of the CompizConfig Settings Manager.

32 pixels wide is the smallest, I think.
Correctamundo!

I run mine on the smallest setting:

[LIST]
[*]This is where you adjust it.
[*]This is how it looks.
[/LIST]


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-21-mar-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-21-mar-2011(2).png")[/INDENT]


Works a treat!  

Dittos for the "Panel Opacity" setting...  ;)

---

### Post by jerrylamos on 2011-03-21
> **Starks said:**
> There is an option in the Unity settings of the CompizConfig Settings Manager.

32 pixels wide is the smallest, I think.
CompizConfig > "Unity settings" ?

Couldn't find anything called "Unity settings".

Starks, could you give me the spelling of the option selection?

Thanks, Jerry

---

### Post by macroshaft on 2011-03-21
> **VinDSL said:**
> Correctamundo!

I run mine on the smallest setting:

[LIST]
[*]This is where you adjust it.
[*]This is how it looks.
[/LIST]


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-21-mar-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-21-mar-2011(2).png")[/INDENT]



Works a treat!  

Dittos for the "Panel Opacity" setting...  ;)

What is that info panel down the right hand side of the screen?

---

### Post by rajeev1204 on 2011-03-21
> **Starks said:**
> As of Unity 3.6.6:


Run 'unity --reset-icons' from Alt+F2 to see the change.

Screencap: [http://i.imgur.com/PMfxB.png](http://i.imgur.com/PMfxB.png)


Hi

Should not this happen automatically with an update ?

---

### Post by daemonk on 2011-03-21
I would love to know what that info panel is on the right is as well ;)

Looks awesome!

---

### Post by xaegis on 2011-03-21
> **macroshaft said:**
> What is that info panel down the right hand side of the screen?

Conky strikes again! :D

---

### Post by rajeev1204 on 2011-03-21
> **daemonk said:**
> I would love to know what that info panel is on the right is as well ;)

Looks awesome!


Its conky i think, but i have also seen it with screenlets.You can install it from the software center.I used to have this some time ago.

---

### Post by macroshaft on 2011-03-21
> **xaegis said:**
> Conky strikes again! :D

Aah!

---

### Post by daemonk on 2011-03-21
Great! Thanks

---

### Post by Amaranth on 2011-03-21
> **rajeev1204 said:**
> Hi

Should not this happen automatically with an update ?

No, if at all possible we don't change user settings on upgrades.

---

### Post by MacUntu on 2011-03-21
Besides, writing migration code for people that (should) know how to fix it themselves is a waste of precious bug squashing time. :P

---

### Post by Starks on 2011-03-21
> **rajeev1204 said:**
> Hi

Should not this happen automatically with an update ?

No, according to Didier Roche, a Unity dev, it will not.

This must be done manually if you are running Natty alphas. Not sure about Maverick Unity.

---

### Post by lucazade on 2011-03-21
> **Starks said:**
> No, according to Didier Roche, a Unity dev, it will not.

This must be done manually if you are running Natty alphas. Not sure about Maverick Unity.

This is why development releases should be used only for testing and reinstalled once released. :)

---

### Post by cariboo on 2011-03-21
> **jerrylamos said:**
> CompizConfig > "Unity settings" ?

Couldn't find anything called "Unity settings".

Starks, could you give me the spelling of the option selection?

Thanks, Jerry

Just click the Ubuntu Unity Plugin icon then click the Experimental tab for the icon size settings.

---

### Post by VMC on 2011-03-21
> **cariboo907 said:**
> Just click the Ubuntu Unity Plugin icon then click the Experimental tab for the icon size settings.

Thanks. For the first time, CCSM didn't crash compiz! Everytime I touch almost anything inside CCSM, compiz follows with a crash. I use that program with caution. That's one of the reasons I have a *[SIZE="1"]compiz --replace[/SIZE]* executable file setting on my desktop.

---

### Post by Starks on 2011-03-21
> **lucazade said:**
> This is why development releases should be used only for testing and reinstalled once released. :)

To paraphrase what he said: "dev releases are a corner case"

---

### Post by cariboo on 2011-03-21
The last several compiz crashes I've had, pop up a window asking if I want to restart it. There have been occasions, where Unity crashes, where unity --reset starts it back up the way it was before the crash.

---

### Post by Starks on 2011-03-21
Unity still crashes from time to time, far more than it should. Having a nautilus window open will always allow you navigate to /usr/bin/unity to restart it.

---

### Post by mc4man on 2011-03-21
I've found several regressions/issues in unity 3.6.6 have made it more likely to fail in some sort.

Most times here it involves the use or repeated use of the dash, I see some of these bugs being worked on.

The default launcher icons have changed a couple of times recently, probably will again
(i'd like to see an icon for the unityshell plugin in the default launcher, would be helpful to new users

---

