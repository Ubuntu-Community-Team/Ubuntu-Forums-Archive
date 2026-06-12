---
title: "How do I get a desktop ?"
date: 2011-02-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by robert shearer on 2011-02-08
I have tried two downloads (386 and 64bit) that both md5sum correctly.

On two machines (amd cpus (2600+ and3000+) and ati graphics (9250 and 9550)

If they boot to unity desktop then the lefthand icon strip/panel shows but nothing is clickable.

if I boot to classic no panels show and nothing is clickable.

In both, all I can do is right click the desktop and change appearances, make folders etc. 

If I drop to a terminal then later attempt ```
startx
``` I get a "you are not authorised to run x" and sudoing is no better.

I heard that Unity would simplify the desktop but this seems too simple :lolflag:

Tried Mr Google, forum search and 'site:ubuntuforums.org" search.

Anyone have suggestions.
(have tried F6, nomodeset etc no help)

---

### Post by bikeboy on 2011-02-08
What did you download, Alpha 2 or a daily CD image?

---

### Post by robert shearer on 2011-02-09
> **bikeboy said:**
> What did you download, Alpha 2 or a daily CD image?

Alpha 2.

Tried it with 'acpi off' and got unity running only to have it crash on nearly every app.

*Sigh* Will wait and try Beta or RC though from what I have seen and read so far it seems Ubuntu continues to move away from supporting older hardware so I don't hold out much hope.

Still, Artist-x 1.0 has just been released so there **is** a new toy to play with. Yipee !
(more apps than you could poke an old twisty stick at and the potential for mayhem and freezes galore.):P oh what fun.)

Will try a daily build of Nutty just for kicks.

Thanks for your reply.

---

### Post by P4man on 2011-02-09
FWIW, on my desktop with an ATI 4870 I cant get unity to work either, not with OSS drivers, not with catalyst. All kinds of issues, corruption, some windows even flip upside down ! It works fine on my intel IGP laptop and secondary machine with nVidia graphics though.

---

### Post by robert shearer on 2011-02-09
> **P4man said:**
>  ....some windows even flip upside down ! 

Cool !, and they don't even charge extra for those sorts of features.
isn't Open Source great !.

It will all sort out in the wash.

(checks top-loader, nah..compy won't fit, still I could pull the ATI card and give that a cycle.
If you can put a keyboard through the dishwasher for a clean and rejuve maybe a Graphics card in a clothes washer, or take my mobo down to the car-wash...or..or..)

---

### Post by coffeecat on 2011-02-09
> **P4man said:**
> FWIW, on my desktop with an ATI 4870 I cant get unity to work either, not with OSS drivers, not with catalyst. All kinds of issues, corruption, some windows even flip upside down ! It works fine on my intel IGP laptop and secondary machine with nVidia graphics though.

Talk about YMMV! Unity desktop works just fine (or as fine as an Alpha can) on my ATI HD4350 desktop and Mobility Radeon HD4200 laptop, both with open-source drivers. But when I tried it on a machine with nvidia 8200GS graphics it was a complete mess. From what I've read in this sub-forum I thought all nvidia was pretty much a no-no with the newer xserver version at the moment.

---

### Post by Harry33 on 2011-02-09
> **coffeecat said:**
> Talk about YMMV! Unity desktop works just fine (or as fine as an Alpha can) on my ATI HD4350 desktop and Mobility Radeon HD4200 laptop, both with open-source drivers. But when I tried it on a machine with nvidia 8200GS graphics it was a complete mess. From what I've read in this sub-forum I thought all nvidia was pretty much a no-no with the newer xserver version at the moment.

Some people can get their desktop to work with nouveau.
But true, proprietary drivers do not boot with xserver 1.10 right now.
Nouveau is still very far away from nvidia-current.

---

