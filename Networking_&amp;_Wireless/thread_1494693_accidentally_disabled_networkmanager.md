---
title: "accidentally disabled networkmanager"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by OkoSanto on 2010-05-27
Hi,

Using kubuntu 10.04, I accidentally disabled networkmanager on startup for one of the users of my system.  This user now has to manually start networkmanager each time after logging in.  How can I make kde run networkmanager automatically again?

How this happened: when I started a parallel session as an other user, while already connected via networkmanager in my own profile, kde detected this and asked something along the lines of "There's already a networkmanager running, run networkmanager automatically in the future?"  Since I was a little confused, I clicked "no", and that's how things are ever since.  I thought there would be some system setting that would allow me to restore this setting, but I haven't found it yet...

---

### Post by Iowan on 2010-05-27
I haven't used Kubuntu - I found this tidbit:> Never mind, I found it. There are to options: a) You can add a link in ~/.kde/Autostart/ to the desired app, or
b) KDE in Kubuntu is configured to load the previous session, so you could as well leave the app open when you exit KDE and it will be launched automatically.

---

### Post by OkoSanto on 2010-06-01
Thanks for the reply.  I had actually already tried both a) and b), but to no avail.  Other programs left running at shutdown (for example, Amarok) will run automatically on next login, but not networkmanager.

However, as a brute-force solution, deleting the ~/.kde directory gives you a clean config on next login, with networkmanager starting automatically as it should.

Of course you lose all your configuration this way, which was fine for me since I had just made a fresh install anyway.  I guess you could just delete/edit a specific config file somewhere in that .kde folder instead of removing everything, but which file would that be?

---

