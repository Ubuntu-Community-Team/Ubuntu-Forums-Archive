---
title: "Realtek Installation"
date: 2009-01-03
forum: Multimedia Software
---

### Post by Black_agent on 2009-01-03
Hey Guys,

I'm a new to Ubuntu and I installed Ubuntu,to say good bye to XP.But at this time I got serious problem with my sound card.My Motherboard is GIGABYTE GA-81945... And it has on-board sound card.But It not taken by ubuntu system.I tried Ubuntu documentation[,http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449").But still I can't hear any sound.

I need to know whether there is Realtek installation package to ubuntu as XP.

Thanks!

---

### Post by 73ckn797 on 2009-01-03
Go to Applications/Accessories/Terminal. Enter ```
lspci
```This will tell you whether your sound/audio device is recognized.

Right click on the speaker icon at top right and set sound levels. Make sure it has not been muted first. You may have to select preferences and set all levels up. 

Try that.

---

### Post by Black_agent on 2009-01-03
> **73ckn797 said:**
> Go to Applications/Accessories/Terminal. Enter ```
lspci
```This will tell you whether your sound/audio device is recognized.

Right click on the speaker icon at top right and set sound levels. Make sure it has not been muted first. You may have to select preferences and set all levels up. 

Try that.

Yes it says
>  Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


But I still get no sound..what should I do?

---

### Post by laceration on 2009-01-04
This post might help you:
[http://ubuntuforums.org/showthread.php?p=4263007#post4263007](http://ubuntuforums.org/showthread.php?p=4263007#post4263007)

---

