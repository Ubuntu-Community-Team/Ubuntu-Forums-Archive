---
title: "NetworkManager not starting - No networking"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by linduxed on 2009-07-27
After some serious digging I found out that the reason my networking has died is because some reboot ago my NetworkManager daemon decided not to start at boot. This renders the nm-applet useless and makes networking pain.

The problem is easily remedied by running:
```
sudo NetworkManager
```
...but I find it irritating to have to run it on every reboot, and more importantly, I want to find out *why* it doesn't do this by itself.

---

### Post by lirpa on 2009-08-22
I am having what appears to be the same problem. I have been starting it manually by running:

```
sudo /etc/init.d/NetworkManager start
```I have tried removing the startup scripts and reconfiguring the package, but it didn't seem to fix it

```
sudo update-rc.d -f NetworkManager remove
sudo dpkg-reconfigure network-manager
```This reinstalled the startup scripts into each runtime, but it still doesn't fix it.

Any help would be appreciated.
Thanks!

---

### Post by linduxed on 2009-08-22
No progress on my issue so far.

I believe that adding the command I specified in my first post to a startup script would suffice, but that's an ugly solution to a problem that shouldn't occur in the first place.

---

### Post by lirpa on 2009-08-22
linduxed, What kind of a system are you running?

I am running 9.04 on a Dell XPS M1530 laptop. I didn't used to have this problem, but I can't remember when it originally started - I want to say that it was after upgrading to 9.04, but I'm not certain.

I've tried looking through the sys logs to see if there might be some clue, but I didn't find anything.

Any Ubuntu experts care to give some suggestions?

---

### Post by DJJo on 2009-08-22
i am busy to get a network with out networkmanager. sie my toppic
but i turnt it off with

> nano /etc/default/NetworkManager
nano /etc/default/NetworkManagerDispatcher
Add a line with "exit" to both files

so dose 2 files can not exist of contans exit

---

### Post by linduxed on 2009-08-23
Turning off NetworkManager is not a solution in this case. While I may prefer WICD for WiFi and ethernet management, NetworkManager has VPN support built in so in some cases it's superior.

Even if having a separate VPN client is an option, this thread was created because this is quite an issue for those not knowledgeable enough to fix a sudden absence of the daemon.

---

### Post by linduxed on 2009-08-23
> **lirpa said:**
> linduxed, What kind of a system are you running?

I'm having these issues on an Acer Aspire 8930g, but I don't believe this has any relevance.

The "solution" of having to type "sudo NetworkManager" is a question of a daemon not starting up at the time it should, the only reason I can come up with that would lead it to be a hardware issue is if the cards can't be reached within a timeout of some sort at bootup, but that's remarkably far-fetched.

Besides, it worked after the installation of 9.04, only to fail a while later. This issue has never occured with any other GNU/Linux install I have had, including the previous two Ubuntu versions.

---

### Post by newb85 on 2009-10-12
This may not help either of you, but I would try adding it back to startup via the GUI.  System>Preferences>Startup Applications - If Network Manager is in the list and unchecked, simply check it.  If it's not in the list, click add and in the command box fill in "nm-applet --sm-disable".  If it's in the list and already checked, please disregard this post entirely.

---

