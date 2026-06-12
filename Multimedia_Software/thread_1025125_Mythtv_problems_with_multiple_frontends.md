---
title: "Mythtv problems with multiple frontends"
date: 2008-12-29
forum: Multimedia Software
---

### Post by eskimomo on 2008-12-29
I need some help configuring my second mythtv frontend. I already have a combination frontend, backend connected to my network. Now I want to add a new frontend on the computer in my room so I can watch tv up there. 

I don't use mythbuntu and won't because it doesn't work with my wireless adapter.

I used virtualbox to run Ubuntu as a vm on my mac, I installed mythfrontend and configured it to connect to my backend at 192.168.0.3. I changed the backend settings so that it identifies itself as being at 192.168.0.3. I commented out he line in a mysql file that prevents outside connections yet I am still getting errors.

This is what the terminal shows when opening mythfrontend
```
2008-12-29 19:35:32.514 Testing network connectivity to 192.168.0.3
2008-12-29 19:35:52.747 Cannot find (ping) database host 192.168.0.3 on the network
2008-12-29 19:35:52.748 Cannot find (ping) database host 192.168.0.3 on the network
2008-12-29 19:35:52.829 Primary screen 0.
2008-12-29 19:35:52.830 Using screen 0, 800x600 at 0,0
2008-12-29 19:35:52.864 No theme dir: /home/eli/.mythtv/themes/blue
2008-12-29 19:35:52.867 Switching to square mode (blue)
2008-12-29 19:35:53.046 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-12-29 19:35:53.049 lirc_init failed for mythtv, see preceding messages
2008-12-29 19:35:53.071 JoystickMenuClient Error: Joystick disabled - Failed to read /home/eli/.mythtv/joystickmenurc
2008-12-29 19:35:53.977 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2008-12-29 19:35:53.979 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...

```

Any ideas?
Thanks

---

### Post by wackston on 2009-01-03
Could be you modified the wrong mysql config parameter.

You want

/etc/mysql/conf.d/mythtv.cnf

[mysqld]
bind-address=192.168.0.6

As (AFAIK) this over-rides the default settings in /etc/mysql/my.cnf for
the specific mythtv database.

---

### Post by wackston on 2009-01-03
Ooops... of course its 192.168.0.3 (.6 is for my home network :) )

---

