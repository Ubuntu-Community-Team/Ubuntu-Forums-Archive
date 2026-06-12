---
title: "mythfrontend usually asks for locale at boot"
date: 2014-04-15
forum: Mythbuntu
---

### Post by mikitz on 2014-04-15
Even though the locale is set to en_CA, mythfrontend asks for the country and city during boot time (most of the time).  /etc/network/interfaces is already set to static ip. 
Any ideas why mythfrontend is still asking for the country, city?


Here is part of the mythfrontend.log that shows it recognizes the locale:

```
Apr 15 17:51:36 mythbuntu mythfrontend.real: mythfrontend[2341]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_CA
Apr 15 17:51:36 mythbuntu mythfrontend.real: mythfrontend[2341]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_CA
Apr 15 17:51:36 mythbuntu mythfrontend.real: mythfrontend[2341]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml

```

---

### Post by blm-ubunet on 2014-04-16
If mythfrontend launches with the country/language screen it means mysql server is not running.

sudo service mysql status

I assume when you exit & then re-start the mythfrontend & all is well ??

I guess this problem is caused by upstart job problems..
Check the latest upstart job script example in mythtv wiki (should same as mybuntu 0.27+fixes).
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

---

### Post by pgreenwood on 2014-04-18
> **blm-ubunet said:**
> If mythfrontend launches with the country/language screen it means mysql server is not running. 

I've noticed, in launching the 12.04 64-bit LiveCD mythfrontend from the command line that the country/language screen will show up even if the backend is otherwise connected and running if the time-zone on the frontend and backend do not agree. Also the app complains that user mythtv must be a member of the mythtv group before it can launch the frontend.

---

### Post by blm-ubunet on 2014-04-19
The TZ difference issue could be useful for very remote FEs.

Missing mythtv group is a bug (which has been reported)..
The LiveCD mythbuntu FE user is not a member of the required group.
To workaround you have to:
- fix the group
- logout/login

---

