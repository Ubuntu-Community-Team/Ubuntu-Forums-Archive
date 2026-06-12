---
title: "Uh-Oh...We need at least Flash 9.0.115!!"
date: 2009-06-14
forum: Multimedia Software
---

### Post by RKilbride on 2009-06-14
Hi all ... having a bit of an issue trying to watch Fancast .... I get the error listed in my title. I have read through many posts as well as trying several ideas ranging from installing the GNOME Player (works great) to disabling all plug ins and seeing if that will work... no avail.

Anyway I have tried to install Adobe Flash Player version 10.0.22.87 Linux Flash ver .deb for Ubuntu 8.04+ to no avail as well... I must be missing something simple ?  I've only been using Ubuntu for 3 days(!) and totally love it, I have installed Ubuntu on 1 other laptop and a desktop and have had no flash issues on those...

Must be something simple?

Thanks!

Ross

---

### Post by jimv on 2009-06-14
Works fine for me.  Are you able to use other sites like Youtube or Hulu?

---

### Post by RKilbride on 2009-06-14
You Tube works fine but when I go to Hulu I get this : 

Hulu requires Flash Player 9.0.115.0 or higher.

I checked my desktop and I was wrong from my previous post, I can watch You tube but not Fancast or Hulu ...

Maybe it's the way I imstalled? I did the entire disk install and wiped windows xp off both.

Maybe re install ubuntu?

---

### Post by jimv on 2009-06-14
Do you have the "ubuntu-restricted-extras" package installed?

---

### Post by RKilbride on 2009-06-14
I just tried that as well and no change... Hulu, Fancast do not play. What's interesting is that I tried to copy the libflashplayer.so into the Firefox plugins directory and could not even do that. This has got me stumped, I'm pretty tenacious when it comes to fixing things so anyother suggestions would be welcome.

I can't help but think it's the way I installed Ubuntu because I have the same problem on 2 computers (desktop old Abit be-II) and a Toshiba Satellite laptop.

Would it have mattered if I installed while Firefox was open? Maybe I should of save the flas file to desktop, close browser and install?  Should I just start from scratch and re install Ubuntu?

---

### Post by RKilbride on 2009-06-14
Came across this link and put the commands below into terminal ... Magic! I can watch Hulu, Fancast etc. on both computers that had issues... hopefully others can benefit ! (I'm running Ubuntu 9.04)

_Link:_

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

_Commands in terminal: _ (Make sure FireFox is closed)

wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)

sudo bash ./flash10_en.sh

---

