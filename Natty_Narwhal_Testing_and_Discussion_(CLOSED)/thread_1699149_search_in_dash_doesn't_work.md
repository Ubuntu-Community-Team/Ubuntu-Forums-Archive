---
title: "search in dash doesn't work"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Masternooob on 2011-03-03
so i have this problem since alpha 1...i cant search anything in the dash...

i found this bug entry:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/662619](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/662619)


but i dont think there will be any work on this in the future but i really need this to be fixes because unity is useles when i can't search for anything...

is there any solution for this or am i the only one who has this bug?

you can see what i mean on this screenshot:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/662619/+attachment/1880943/+files/Bildschirmfoto.png](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/662619/+attachment/1880943/+files/Bildschirmfoto.png)

firefox is installed btw ;-)

so...can somebody help me? ^^

---

### Post by dino99 on 2011-03-03
is there some errors logged ?

watch: /var/log/ & xsession-errors

---

### Post by taavikko on 2011-03-03
Dash does searches by name, rather than exec.
example gnome-system-monitor is the command to launch it, but it's name is system-monitor.

---

### Post by webme on 2011-03-03
> **Masternooob said:**
> so i have this problem since alpha 1...i cant search anything in the dash...

i found this bug entry:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/662619](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/662619)



is there any solution for this or am i the only one who has this bug?



so...can somebody help me? ^^
Did you try to type in search area "fir" for firefox and wait 3.4 seconds to see if something appears? or you type fast and enter the full name at once? This may be the problem.

---

### Post by Masternooob on 2011-03-03
> **taavikko said:**
> Dash does searches by name, rather than exec.
example gnome-system-monitor is the command to launch it, but it's name is system-monitor.

yeah but firefox is the name ;-)

> **webme said:**
> Did you try to type in search area "fir" for firefox and wait 3.4 seconds to see if something appears? or you type fast and enter the full name at once? This may be the problem.

yes i tried this, i waited about 20 seconds...but nothing happens

---

### Post by xgt001 on 2011-03-03
> **Masternooob said:**
> yeah but firefox is the name ;-)



yes i tried this, i waited about 20 seconds...but nothing happens


well with alpha 1 i had the same issues ,.... with alpha 2 dash search worked fine but scrolling didnt. though it took 2-3 seconds for the name to appear. :guitar:
I think you need to install latest unity updates.
hope the issue is completely fixed in alpha-3
:P

---

### Post by Masternooob on 2011-03-03
> **xgt001 said:**
> well with alpha 1 i had the same issues ,.... with alpha 2 dash search worked fine but scrolling didnt. though it took 2-3 seconds for the name to appear. :guitar:
I think you need to install latest unity updates.
hope the issue is completely fixed in alpha-3
:P

i have the latest updates (unity 3.6.0.0 i think)...still doesnt work and no logfile is created when im searching ...or i cant find one at least xD

---

### Post by cariboo on 2011-03-03
If you select the applications icon from the panel, does search work for you?

When using the dash, does clicking the **Find Internet Applications** work? 

Do you get a context menu in the upper right of the applications window?

---

### Post by ratcheer on 2011-03-04
I am having very similar problems.

My natty installation is fully updated as of this morning. I assume I am on Alpha 3. The dashboard does not work. If I click "Find more apps", nothing happens. If I type into the Search box and hit Enter, nothing happens.

However, if I click "View Photos" it does bring up Shotwell. And if I click the "Browse the web" button, it brings up Firefox. So, it is working a little, but not for the things I need.

Tim

---

### Post by webme on 2011-03-04
> **ratcheer said:**
> I am having very similar problems.

My natty installation is fully updated as of this morning. I assume I am on Alpha 3. The dashboard does not work. If I click "Find more apps", nothing happens. If I type into the Search box and hit Enter, nothing happens.

However, if I click "View Photos" it does bring up Shotwell. And if I click the "Browse the web" button, it brings up Firefox. So, it is working a little, but not for the things I need.

Tim
Does the search works in the "other" Dash "Files &Folders"?
Can you select a category in the top-right of the  F&F, App Dash?

---

### Post by ayates on 2011-03-04
I had the same issue until I installed unity-place applications and unity-place-files.

---

### Post by ratcheer on 2011-03-04
> **ayates said:**
> I had the same issue until I installed unity-place applications and unity-place-files.

Thanks. I'll try that. I wonder why they aren't part of the standard installation?

Tim

---

### Post by mc4man on 2011-03-05
> I wonder why they aren't part of the standard installation?
They are - ck. out the manifest of alpha 3 (and likely alpha 2

If you have been upgrading from a previous  .iso then there is a possibility that they either weren't included or that there was a short time they were removed as recommends for unity
(added back around alpha 2

---

### Post by ratcheer on 2011-03-05
Much better. Thank you very much, ayates.

Tim

---

