---
title: "No Users &amp; Groups in menu"
date: 2011-01-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-01-21
In one of my Nattys I have Users & Groups in the menu but in this one I don't! Why might that be? And how do I get to it via CLI? Thanks :-)
It doesn't show as an option in the Menu Editor.
In the other install (the one with Users & Groups) I wasn't listed as an Admin, I was listed as Custom. I don't know how that happened either. I changed it to Admin.
But in my current install I can't get to that screen :-(
I'm using Unity, if it matters.

---

### Post by coffeecat on 2011-01-21
> **Quackers said:**
> In one of my Nattys I have Users & Groups in the menu but in this one I don't! Why might that be? And how do I get to it via CLI? Thanks :-)

There's a [ringing]("http://ubuntuforums.org/showpost.php?p=10222825&highlight=users+groups+gnome-system-tools&postcount=99") [in my]("http://ubuntuforums.org/showpost.php?p=10223151&highlight=users+groups+gnome-system-tools&postcount=105") [ears]("http://ubuntuforums.org/showpost.php?p=10223212&highlight=users+groups+gnome-system-tools&postcount=106"). Can you hear it? :p

Any help? :)

---

### Post by efflandt on 2011-01-21
What menu you are referring to, because I have not seen an applications menu in Natty Unity (just applications directory with launchers)?  Dash was recently added, but I have not played with that yet.

The launcher in my /usr/share/applications simply shows the command in Users and Groups launcher as **users-admin**, which is apparently part of **gnome-system-tools** (Synaptic shows my version as 2.32.0 0ubuntu4).  Maybe that was not updated on that system.

Before there was any Users and Groups launcher in Natty, I simply used **adduser** from a shell (preferred over useradd) and manually edited /etc/group (which technically from shell should use **vigr** on multi-user system).

---

### Post by Quackers on 2011-01-21
I don't understand :-(
I am talking about the Global menu thing. There is no Users and Groups, no Gnome-system tools. 
But, in my other Natty install, Users and Groups is in the global menu thing (usr/share/applications).
Both Nattys should be the same. I've updated them the same and they both have one user.
I'm looking over your links again coffeecat, to refresh my (ageing) memory :-)

---

### Post by Harry33 on 2011-01-21
> **Quackers said:**
> I don't understand :-(
I am talking about the Global menu thing. There is no Users and Groups, no Gnome-system tools. 
But, in my other Natty install, Users and Groups is in the global menu thing (usr/share/applications).
Both Nattys should be the same. I've updated them the same and they both have one user.
I'm looking over your links again coffeecat, to refresh my (ageing) memory :-)

Have you installed the package gnome-system-tools?
It also install a lot of new dependencies.
See here (64-bit):
[https://launchpad.net/ubuntu/natty/amd64/gnome-system-tools/2.32.0-0ubuntu4](https://launchpad.net/ubuntu/natty/amd64/gnome-system-tools/2.32.0-0ubuntu4)

---

### Post by Quackers on 2011-01-21
Yes, Harry33, I have just installed gnome-system-tools and the Users and Groups icon has appeared in the global menu window. So thanks for the suggestions, all.
However, unless I did it in my sleep, I don't remember installing gnome-system-tools in the other Natty install. I will reboot and check that.

---

### Post by Quackers on 2011-01-21
Please disregard all previous mumblings! Gnome-system-tools is installed in my other system. I must have listened to coffeecat more than I thought :-)
Thanks all. Case closed!

---

### Post by mc4man on 2011-01-21
gnome-system-tools is currently part of the default install and probably has been for a little bit.

---

### Post by coffeecat on 2011-01-21
> **mc4man said:**
> gnome-system-tools is currently part of the default install and probably has been for a little bit.

Agreed, it certainly is now. But it seemed to go awol from some people's systems - certainly mine - last December. I can't now remember whether the system it was missing from was installed from an Alpha1 ISO or was an upgrade from Maverick.

---

### Post by mc4man on 2011-01-21
> But it seemed to go awol from some people's systems 
I think it was fairly recently that it was added.
I've taken the view, (rightly or wrongly) that with natty a new install from time to time may be more reflective of it's current state that an older one updated, I don't think they always equal the same.

---

### Post by Quackers on 2011-01-21
Hmm interesting. I wonder how my older Natty escaped that. It's kept fully updated, unless there's a problem with updates, temporarily.

---

### Post by mc4man on 2011-01-21
> I wonder how my older Natty escaped that. It's kept fully updated
If it wasn't part of the default install then in the case of this package and others like it 'updates' would generally have no reason to install

---

### Post by Quackers on 2011-01-21
> **mc4man said:**
> If it wasn't part of the default install then in the case of this package and others like it 'updates' would generally have no reason to install

Understood :-)
Updates want to remove evolution now! Leave me alone! :-)

---

### Post by Harry33 on 2011-01-21
> **Quackers said:**
> Understood :-)
Updates want to remove evolution now! Leave me alone! :-)

Perhaps it is this new evolution update you need to have:
[https://launchpad.net/ubuntu/natty/+source/evolution/2.32.1-0ubuntu3](https://launchpad.net/ubuntu/natty/+source/evolution/2.32.1-0ubuntu3)
There is ligdata API bumb: libgdata10 => libgdata11

Also this one is updated:
[https://launchpad.net/ubuntu/natty/+source/evolution-data-server/2.32.1-0ubuntu4](https://launchpad.net/ubuntu/natty/+source/evolution-data-server/2.32.1-0ubuntu4)

---

### Post by Quackers on 2011-01-21
Hopefully it'll appear in synaptic soon :-)

---

