---
title: "can i upgrade directly from 10.10 to 11.04 beta1?"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rvchari on 2011-04-07
i am happily using 10.10 and i just downloaded the alternate iso for 11.04 beta 1. i burnt the image on the cdrom, can i directly upgrade to 11.04 ? hope my data and other sys config and tweaks will remain intact ? 
a detailed how to will help guys like me to upgrade :P

---

### Post by wilee-nilee on 2011-04-08
You can upgrade and keep your stuff with the alternate, I have never done it though, I always fresh install. I wouldn't do anything though without imaging the Maverick as well. I also would not do this until some time after Natty is released. 

Your risking a lot here if your trying to upgrade your main OS with a not released distro, and don't have it imaged, dual boot it first see if it runs okay.

---

### Post by rvchari on 2011-04-08
i have also started the download of the standard desktop edition... (beta1)
somewhere in the web, i came across with an article that alternate iso upgrade safeguards the work. i asked this questing in this thread coz natty will be running gnome 3 and some new updates not available in maverick. as u said, i should nt end up with a hangup of this cross breed ! so i asked to double check.

---

### Post by ikt on 2011-04-08
I have and my advice is don't, wait until beta 2.

beta 1 is still fairly buggy at this point.

---

### Post by garvinrick4 on 2011-04-08
If you want to upgrade and not do a fresh install:
Back-up all your /home:
comment out medibuntu and ppa's in sources.list
```
sudo apt-get update and sudo apt-get upgrade
``````
sudo apt-get install aptitude
``````
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

```Uncomment medibuntu leave as maverick
Fix up your ppa's if any ```
sudo aptitude update  && sudo aptitude safe-upgrade
```#I find it better to use the aptitude safe-upgrade for Alpha's and Beta's
** You do understand natty is not stable and will have to deal with breaks.
***Ubuntu does recommend update-manager for dist-upgrades***
                           This above has worked well for me:

---

### Post by rvchari on 2011-04-08
noted all the replies....
i have decided to wait !!! thanks for your advice guys...

---

