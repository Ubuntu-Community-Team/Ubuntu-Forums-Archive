---
title: "Karmic: Computer Name Change GUI"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Hozza on 2009-11-03
How do you change your computers name in Karmin (GUI style please)?

---

### Post by Hozza on 2009-11-05
anyone??

---

### Post by shredder12 on 2009-11-05
If you actually mean hostnames of the computer then it is easy to change.(Hostname is the name by which you are identified on a  network. Run the command hostname to see your hostname).

Now, in order to change it you will have to edit /etc/hostname file 
use gedit to open it.

```
sudo gedit /etc/hostname
```
and put whatever name you want.
you might need a restart after editing the file...
I am not sure if this method really works in Karmic but this is a proper method for Debian systems so it should work.

---

### Post by rickyjones on 2009-11-05
> **Hozza said:**
> anyone??

I have a fresh install of 9.10 in Virtualbox and I just looked through all the menus. I don't see any way to change the computer name with a gui. Best option at this point is to use the terminal application.

Applications -> Accessories -> Terminal

Type: sudo gedit /etc/hostname
Enter your password

There should be a single line with the hostname. Modify this line and save the file.

You might need to modify the /etc/hosts file to reflect the name change but I'm not positive on that. I usually do for consistency but I'm not sure on the necessity.

I feel a GUI to facilitate this change is a pretty basic item...

Thanks,
Richard

---

### Post by itsjustarumour on 2009-12-15
> **rickyjones said:**
> I feel a GUI to facilitate this change is a pretty basic item...


Indeed there was one once, in 8.04 if memory serves me correctly.  Why they took it away is anyones guess!  :roll:

I've just had a quick search for it - just install gnome-network-admin

Then go to System>Administration>Network and you can change it on the "General" tab.

:)


EDIT:  I've just downloaded and tested this package on 9.10, and it simply didn't work.  Well, I guess that kinda answers the question as to why it isn't included in a default install any more! :roll:   

Just a shame that this package wasn't updated and was just thrown on the scrapheap when there was no other replacement for this functionality... (from the GUI point of view)

---

### Post by jhansonxi on 2010-02-14
The Gnome tool is not helpful (bug #163720).  It wouldn't change the hostname on my laptop when I tried it.  I suspect that the functionality will be added to Network Manager in the future.

---

