---
title: "Can only run Banshee as root!?"
date: 2009-11-03
forum: Multimedia Software
---

### Post by Mach1723 on 2009-11-03
EDIT: It works now, just needed to restart.

Whenver i try and start banshee without sudo it doesnt start and only says this in terminal.
```
mach@mach-desktop:~$ banshee-1 --debug
** Running Mono with --debug   **
[Debug 12:21:16.324] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with InQueue

```But when i run it with sudo it starts perfectly?
```
mach@mach-desktop:~$ sudo banshee-1 --debug
** Running Mono with --debug   **
[Info  12:19:23.141] Running Banshee 1.5.1: [Ubuntu karmic (development branch) (linux-gnu, i486) @ 2009-10-19 14:46:07 UTC]
[Warn  12:19:26.113] DBus support could not be started. Disabling for this session.

``` though it doesnt have d-bus but could that be because i am running it as root?

---

