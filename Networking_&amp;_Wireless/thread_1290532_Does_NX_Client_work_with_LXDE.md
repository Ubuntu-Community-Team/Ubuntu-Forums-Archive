---
title: "Does NX Client work with LXDE?"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2009-10-13
Does anyone know if NXClient will connect to LXDE server?

Thanks

---

### Post by mer_ge on 2010-04-11
I tried exactly that and did _not_ get it to work. Has anyone done this?

---

### Post by hedge_hog on 2010-04-28
> **mer_ge said:**
> I tried exactly that and did _not_ get it to work. Has anyone done this?

Yes, but using a openSUSE 11.2 remote machine and a Ubuntu 9.10 client.  
Try this...

On the remote machine install (from the NoMachine download page):
nxclient 3.4.0-7
nxnode 3.4.0-7
nxserver 3.4.0-7

On the local machine install:
nxclient 3.4.0-7

On the local machine:
```
Applications>Internet>NX Client for Linux>NX Client for Linux:
 - Configure
    - Desktop
       - Select: Unix, Custom
         - Settings
            - Application
               - Select: 'Run the default X client script server'
            - Options
               - Select: 'New virtual desktop'
- Save 
- Login :)

```HTH

---

### Post by vinan on 2010-04-29
hvae you tried teamviewer for linux
 
[http://www.teamviewer.com/da/download/index.aspx?os=linux](http://www.teamviewer.com/da/download/index.aspx?os=linux)

---

### Post by 5hamar on 2011-06-22
Alternatively you could try: nxclient -> Configure -> Desktop (Unix-Custom) -> Settings -> 'Run the following command' -> /usr/bin/startlubuntu. It worked for me (server - Lubuntu 10.10; client - Ubuntu 10.04; NXclient - v3.5.0.6). Best of luck.

---

### Post by Khannie on 2011-07-08
> **DapperMe17 said:**
> Does anyone know if NXClient will connect to LXDE server?

Thanks

This is the number one hit in google for this issue, so I'm updating to try to help others who come across this issue.

In your nx session config, under desktop, choose Unix, Custom, click the settings button, choose the "run the following command" radio button and put in lxsession (or /usr/bin/lxsession).

---

### Post by 5hamar on 2011-07-09
> **Khannie said:**
> This is the number one hit in google for this issue, so I'm updating to try to help others who come across this issue.

In your nx session config, under desktop, choose Unix, Custom, click the settings button, choose the "run the following command" radio button and put in lxsession (or /usr/bin/lxsession).
For me "lxsession" didn't work out. But "startlubuntu" did the job perfectly :)

---

### Post by xkcdcode on 2012-07-03
Had the same issue. This works for me on LUbuntu 12.04.

In NoMachine-->Custom-->Settings-->Run the following command, put

/usr/bin/lxsession -s Lubuntu -e LXDE

Then choose "New virtual desktop" in the bottom. That's all!

---

### Post by wildmanne39 on 2012-07-03
Thread closed, it is almost three years old.

---

