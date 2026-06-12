---
title: "Unity menu showing applications I don't have installed??"
date: 2011-03-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2011-03-11
I have just realised that when using the search box in the unity menu half the results that are coming up are for apps I don't even have installed! Clicking on them does nothing.

What is going on here? Surely this can't be normal.

---

### Post by anders_c_ on 2011-03-11
I think it's supposed to launch Software Center to install them but I only get a message that Software Center has crashed when i click one. 
Anyway I think its a good idea that Dash suggests apps that are available from the repositorys, and I'm sure it will work the way it's intended soon.

---

### Post by terry_gardener on 2011-03-11
i think it is a good idea if they separate it out from installed applications, put it underneath with title suggested applications for example.

---

### Post by macroshaft on 2011-03-11
> **terry_gardener said:**
> i think it is a good idea if they separate it out from installed applications, put it underneath with title suggested applications for example.

If you browse to a category, i.e. browse internet apps then it does. It's only when searching they seem to be mixed in. For whatever reason my software centre is so broken it doesn't even get as far as crashing at the moment!

---

### Post by r-senior on 2011-03-11
That was an update in Unity 3.6.4 that only came out yesterday. 

[webupd8.org - Unity 3.6.4]("http://www.webupd8.org/2011/03/unity-364-brings-resizable-launcher-alt.html")

It's launching Software Centre ok for me.

---

### Post by mc4man on 2011-03-11
> my software centre is so broken

The software-center break is noted here with link to main bug (As dino noted i should have titled diff.
[http://ubuntuforums.org/showthread.php?t=1704714](http://ubuntuforums.org/showthread.php?t=1704714)
 - note it only affects some hardware/driver combos, other packages can also be affected

You can wait it out, revert to prior libgl1-mesa-glx package  or there is a way to fix software-center itself by editing the launch command in  ubuntu-software-center.desktop.
The function in dash can also be restored - have done so here, but that's a bit of a hack.

---

### Post by terry_gardener on 2011-03-11
> **macroshaft said:**
> If you browse to a category, i.e. browse internet apps then it does. It's only when searching they seem to be mixed in. For whatever reason my software centre is so broken it doesn't even get as far as crashing at the moment!

i think it is a bad idea to mix the results for searching as this will be bad for especially new users who don't know exactly what apps they have installed.

---

### Post by terry_gardener on 2011-03-11
i have done more checking and it only happens in the dash search. 
if you load the applications icon in launcher and then search it separates them.

---

### Post by KrazyPenguin on 2011-03-11
When I press <superkey><a> for apps I get three categories:

1) Most Frequently Used
2) Installed
3) Apps Available For Download

I get an error when I click on Apps Avaiable for Download.  Ubuntu Software Center crashes!!!

I would like to know how the DASH chooses to show which apps are available for download, since they seem random.

---

### Post by Decatf on 2011-03-11
Suggested applications is a major let down. 

The Applications menu has basically become Ubuntu App Store.

---

### Post by macroshaft on 2011-03-12
It's getting there, I do think it's an interesting idea to suggest downloads alongside the installed apps but they really do need the dash search to separate installed and suggested apps just like they are elsewhere in this menu system.

It does seem though that we're half way to making software centre obsolete here!

---

