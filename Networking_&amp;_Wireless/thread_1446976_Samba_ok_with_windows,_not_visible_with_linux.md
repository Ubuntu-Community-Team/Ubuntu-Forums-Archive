---
title: "Samba ok with windows, not visible with linux"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by sabersong on 2010-04-04
I'm having an odd problem with samnba.  I have 2 kubuntu computers and one Windows laptop connected through a wireless router.  The Windows laptop connects with the 2 linux boxes without any trouble.  But the 2 linux boxes can't seem to connect with one another.  Rather, they do occasionally, but for the most part they don't.  I click on Samba under Network on either of the Kubuntu machines and nothing shows up, most of the time.  But every once in a while, it does.  Any ideas on this?

---

### Post by pdc on 2010-04-04
[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

---

### Post by sabersong on 2010-04-05
Thanks for the link.  Unfortunately, I followed the guide and still can't see any samba shares from either kubuntu computer.

---

### Post by kblft on 2010-04-05
did you check to see that you have smbfs installed ?

```
dpkg -l | grep smbfs
```

If not install it :

```
sudo apt-get install smbfs
```

I had some similar problems that were fixed with a smbfs installation...

---

### Post by sabersong on 2010-04-05
Yes, I have smbfs installed.  But now I know how to check for it! :)

---

### Post by Morbius1 on 2010-04-05
> I click on Samba under Network on either of the Kubuntu machines and nothing shows up, most of the time. But every once in a while, it does. Any ideas on this?When you say nothing do you mean you're presented with a blank screen.
If so does Dolphin have a "Reload" button. In Nautilus when this happens you need to keep hitting the Reload button - sometime up to 15 times - then all of a sudden your machines and shares appear.

It's probably because the default mechanism of browsing is set this way:
> name resolve order = host lmhost wins bcastIt's the order in which samba attempts to convert machine names to ip addresses. The first three are either non-functional or not set up in a home network. Only bcast works by default and it's last in order. Throw in a wireless network and it spends a lot of time in the "wins" part.

swerdna mentions in one of his tutorials that he usually changes the order to:

```
name resolve order = bcast host lmhost wins
```So that the only default mechanism that's functional appears first.

---

### Post by sabersong on 2010-04-05
I tried changing the order of name resolve as suggested, but still no results. And yes, I do mean a blank screen.  The windows computer doesn't show up on the kubuntu sets either.I'm trying all suggestions on both kubuntu machines.

---

### Post by sabersong on 2010-04-05
I'm calling this solved.  The samba problem still exists, but I got the linux computers to network with nfs, so my needs have been met.

---

