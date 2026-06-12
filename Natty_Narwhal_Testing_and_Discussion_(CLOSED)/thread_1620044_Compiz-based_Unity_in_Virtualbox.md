---
title: "Compiz-based Unity in Virtualbox?"
date: 2010-11-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kaldor on 2010-11-12
I added the PPA to Natty running inside Virtualbox. I installed Unity and upgraded Compiz via apt-get, but selecting Netbook Edition in GDM does the same thing that Mutter used to do; blank background with a mouse cursor.

3d acceleration IS enabled.

Is this related to the Compiz breakage? Will Unity be able to run in Virtualbox now that it's based on Compiz?

---

### Post by godhika on 2010-11-12
To try the compiz based Unity, log in to a normal desktop session and activate the Unity plugin in compiz-config-settings-manager. But don't be too disappointed - there is not much to see yet.

---

### Post by kaldor on 2010-11-12
Did that just now; nothing :(

Edit:

Enabled Unity in ccsm. 

- I logged out, and logged into the Netbook session; Nothing. 
- I enabled desktop effects on GNOME (missing panels and window borders occurred) and rebooted back into GNOME; no Unity.


Is this a Virtualbox thing or am I doing it wrong? :)

Edit 2: Weird... what's this about?
```

michael@natty-daily:~$ unity
The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity
michael@natty-daily:~$ sudo apt-get install unity
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity is already the newest version.
The following package was automatically installed and is no longer required:
  libvpx0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by godhika on 2010-11-12
I would say, its a Virtualbox thing. For the error you posted: I get the same thing - I see the first glimpses of the Unity shell nonetheless. Can you normally run Compiz in Virtualbox?

---

### Post by kaldor on 2010-11-12
I've never tried it on Ubuntu, but it worked on a Fedora guest a while back.

---

### Post by seeker5528 on 2010-11-12
> **kaldor said:**
> - I logged out, and logged into the Netbook session; Nothing.

Looks like the session stuff hasn't been updated for the compiz based unity yet, when I select the netbook session it still starts with Mutter as the window manager.

Later, Seeker

---

### Post by kaldor on 2010-11-12
> **seeker5528 said:**
> Looks like the session stuff hasn't been updated for the compiz based unity yet, when I select the netbook session it still starts with Mutter as the window manager.

Later, Seeker

Explains a lot. Thanks :)

---

### Post by seeker5528 on 2010-11-12
I don't have an option showing up to trun on desktop FX, maybe because I am pulling from the gnome3 PPA?

However if you create a '.xprofile' file in your home directory and add the line ```
export WINDOW_MANAGER="/usr/bin/compiz"
``` then log in with the normal 'Ubuntu Desktop' session, that seems to work just fine.

I lost my window boarders when I enabled the Unity stuff, but after logging out and back in, seems fine.

Unfortunately Firefox and Totem are the only applications showing on my launcher and I can't find a way to run anything else.

Later, Seeker

---

### Post by kaldor on 2010-11-12
Tried it just now... still regular GNOME except now it has the default GNOME theme and looks broken.

---

### Post by seeker5528 on 2010-11-12
> **kaldor said:**
> Tried it just now... still regular GNOME except now it has the default GNOME theme and looks broken.

If by broken you mean the windows don't have any boarders, then compiz probably died for some reason.

In the Unity mega thread, it was indicated the key combination 'Ctrl'+'Alt'+'T', should bring up a terminal window.

Later, Seeker

---

### Post by kaldor on 2010-11-12
by broken I mean it's using the default GNOME controls and icon theme. Looks like I'm back in 2002 :)

---

### Post by fluteflute on 2010-11-30
There's a [bug report tracking the use of Natty's Unity/Compiz in VirtualBox]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/675307").

---

