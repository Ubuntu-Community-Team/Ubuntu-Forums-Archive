---
title: "Combined Frontend/Backend, want to add External Frontend"
date: 2012-09-20
forum: Mythbuntu
---

### Post by johnvic on 2012-09-20
Currently, I am running a mythbuntu combined frontend and backend system. The version is 12.04.1 LTS. The desktop is kfce 4.8. The PC is an AMD 64 X2 4400. The mobo is Asus A8V with 2 gigs of RAM.

The second frontend will be an XBMC, which is already running. All devices are on the same network.  I am not sure what I need to do to externally access the backend from the xbmc or even if I were to add a dedicated mythtv frontend. I changed the ip address in the backend setup to the ip address as opposed to localhost or 127.0.0.1, and did the same in the my.cnf file for the bind-address. But the tutorials I see all mention a skip-networking, but the comments in the file state that is not used anymore.

Is there a tutorial on turning a dedicated backend into a shared backend?

---

### Post by nickrout on 2012-09-21
> **johnvic said:**
> Currently, I am running a mythbuntu combined frontend and backend system. The version is 12.04.1 LTS. The desktop is kfce 4.8. The PC is an AMD 64 X2 4400. The mobo is Asus A8V with 2 gigs of RAM.

The second frontend will be an XBMC, which is already running. All devices are on the same network.  I am not sure what I need to do to externally access the backend from the xbmc or even if I were to add a dedicated mythtv frontend. I changed the ip address in the backend setup to the ip address as opposed to localhost or 127.0.0.1, and did the same in the my.cnf file for the bind-address. But the tutorials I see all mention a skip-networking, but the comments in the file state that is not used anymore.

Is there a tutorial on turning a dedicated backend into a shared backend?

pretty sure that what you need in order to proceed further is:

```
sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common
```

XBMC has a great plugin for accessing a myth backend called mythbox. Unfortunately it doesn't work with 0.25. Best to just install mythfrontend on the client machine. You can install xbmc as well of course,and try mounting your video directories over the network to the xbmc machine.

---

### Post by johnvic on 2012-09-21
Thanks nick. The reason I wanted to use the apple tv xbmc as a frontend is to have a quiet frontend and use my old PC ( the current combined frontend/backend ) as a dedicated backend. If I get some time this weekend I'm going to setup my PC as a 11.10 backend and see if xbmc sees it.

---

### Post by uteck on 2012-09-23
There is forked mythbox plug that works with .25 for the most part. [https://github.com/mitchcapper/mythbox](https://github.com/mitchcapper/mythbox)
 The coverart does not allways showup, but it plays recordings if you NFS mount the backend were they are stored.  Still does not work to watch LiveTV on remote frontends.

---

### Post by tgm4883 on 2012-09-23
> **uteck said:**
> There is forked mythbox plug that works with .25 for the most part. [https://github.com/mitchcapper/mythbox](https://github.com/mitchcapper/mythbox)
 The coverart does not allways showup, but it plays recordings if you NFS mount the backend were they are stored.  Still does not work to watch LiveTV on remote frontends.

You have to mount the recordings directory for mythbox to play back recordings? Sounds like they are doing it wrong.

---

