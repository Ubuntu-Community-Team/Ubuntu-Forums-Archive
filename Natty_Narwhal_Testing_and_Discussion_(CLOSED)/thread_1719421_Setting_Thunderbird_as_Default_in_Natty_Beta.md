---
title: "Setting Thunderbird as Default in Natty Beta"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by willygatti on 2011-04-01
I installed Thunderbird successfully from the software center, but Ubuntu 11.04 Natty Beta won't let me set it as my default email client via preferred applications in the control center.  How do I set Thunderbird as my default email client in Ubuntu 11.04 Natty?

---

### Post by drs305 on 2011-04-02
Thread moved to Natty Testing.

---

### Post by Harry33 on 2011-04-02
> **willygatti said:**
> I installed Thunderbird successfully from the software center, but Ubuntu 11.04 Natty Beta won't let me set it as my default email client via preferred applications in the control center.  How do I set Thunderbird as my default email client in Ubuntu 11.04 Natty?

Perhaps not so important to set is default there.
In Libreoffice writer (emailmerge installed) go to
Options - Internet - E-mail
Then write into the box:
/usr/bin/thunderbird

Also you can uninstall evolution.

---

### Post by willygatti on 2011-04-08
I uninstalled Evolution and copied the code you suggested in Libreoffice Writer, but when I click the Check Email button in the Unity menu, Thunderbird still doesn't launch. I still have to go to my applications menu to open Thunderbird.

---

### Post by Harry33 on 2011-04-08
> **willygatti said:**
> I uninstalled Evolution and copied the code you suggested in Libreoffice Writer, but when I click the Check Email button in the Unity menu, Thunderbird still doesn't launch. I still have to go to my applications menu to open Thunderbird.

Don't know how it is done in Unity (if at all possible) because I do not use Unity.
But after you done what I wrote, Libreoffice Writer will open Thunderbird when you click on email address.

---

### Post by MadCow108 on 2011-04-08
the problem with the preferred applications has been solved yesterday.
[https://bugs.launchpad.net/bugs/719919](https://bugs.launchpad.net/bugs/719919)

---

### Post by Harry33 on 2011-04-09
> **MadCow108 said:**
> the problem with the preferred applications has been solved yesterday.
[https://bugs.launchpad.net/bugs/719919](https://bugs.launchpad.net/bugs/719919)

The thunderbird update was on 6th April.
And it seems to make it possible to choose thunderbird from the "Preferred Applications".

---

### Post by rabideau on 2011-04-11
Yes you may now select T'bird as the default email... it just doesn't do anything. e.g. if you access Systems Settings and then email... you get evolution settings. :confused:

---

