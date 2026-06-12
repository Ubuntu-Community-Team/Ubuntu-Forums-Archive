---
title: "Firestarter causing issues with Samba"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by thegamefreak0134 on 2009-01-21
Hi all. I'm fairly new to Ubuntu and I'm not terribly familiar with the linux architecture, as should be painfully obvious by my post count, so bear with if I'm not explaining this properly.

I got fed up with the Windows 7 beta... sucking in terms of stability, and rather than step back to Vista, I decided to move way forward and go with a Linux distro on this PC. I'm now having some issues with Samba and the firewall.

When I installed the distro, Ubuntu was able to instantly browse the list of computers on my Windows network and with a bit of coaxing (it wouldn't display the folder names, for example, but would still connect to them) I was able to begin copying my files. So far so good, Samba was working when I installed.

I soon got ambitious, installed Wine, and attempted to start trying to make WoW work under linux. The tutorial I was using at the time had me opening up ports, and recommended "Firestarter" as an easy way to do this, so I installed Firestarter, and Samba died.

I find now that I can go into Firestarter and disable the firewall completely, which allows Samba to work. However, (this wasn't an issue before) when I start copying files over again from my Win to my Linux, Samba will randomly stop working after 200 MB or so, and the only way I've found to make it work again is to completely restart the machine. (You know, like I was running windows or something.)

What I would like greatly is to completely disable the firewall. I'm sitting behind a router that blocks incoming traffic anyway, which makes the most secure of firewalls (That are purely firewalls and nothing else) quite useless, so there's not a security risk imho. From what I can tell, Firestarter seems to be more of an interface to the firewall, as uninstalling it doesn't fix the Samba issues that it broke when I installed it.

Would someone walk me through (as a new ubuntu user, I'm not afraid of linux in general, notepad/command lines don't scare me) disabling the firewall in Ubuntu? I really think it will solve the issues. Thanks!

-gamefreak

PS: Yes, I tried setting a policy in Firestarter to let Samba through, with no luck at all, it still doesn't work. The only thing that shows results is disabling the firewall through Firestarter completely, and that still fails for large files or large amounts of transfers.

---

### Post by asuastrophysics on 2009-08-11
^ I'm having the same issue, only after deleting firestarter, i can no longer share anything anymore. period. it totally broke samba and ubuntu's lack of a restore feature has led me to believe that i must now nuke everything and reinstall :(

---

