---
title: "Ubuntu II can't connect to SAMBA shares. Kubuntu II can."
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by Quaxo76 on 2008-12-03
Hello all, I have been using Kubuntu for a few years now, but with the new II release, I'm switching to Ubuntu. I really don't like the new KDE4, I feel less "in control", it feels unfinished. Maybe next release it'll be OK, but for II I think I'm staying with Ubuntu.
Now, I have a file server set up on a different machine, using samba. I need it to access common data from all the computers on my network. This worked perfectly with Kubuntu (GG, HH, and II) using Smb4k: it would show me the available shares, I could double-click them, it asked for username and password, and that was it - share mounted and usable.
I need something like that (GUI-ish) because some of the people who need to use the shares are computer-illiterate and can't use a command line.

Now, with Ubuntu II, when I try going to Places > Network, I see the server icon. I double click it, and it opens and shows me the available shares.
I open one, it asks for user name and password, but when I enter them an error window pops up which says "Unable to mount location - Failed to mount Windows share".
In Kubuntu, with smb4k, it worked flawlessly without having to configure anything. But I don't want to install smb4K here because it depends on a lot of KDE packages I'd rather avoid installing.

Any idea what's happening? Why can't Ubuntu mount a share that Kubuntu sees? Should I install a GUI share browser like smb4K? If so, which?

Thanks in advance,
Cristian

---

### Post by dollylamb on 2008-12-03
I guess samba package is not installed. Try "dpkg -l | grep samba". If you see nothing, then issue apt-get install samba command.

---

### Post by Quaxo76 on 2008-12-03
Hello,
Yes, of course samba is installed:

```

cristian@ubuntu:/media/mp3$ dpkg -l | grep samba
ii  samba                                     2:3.2.3-1ubuntu3.3                    a LanManager-like file and printer server fo
ii  samba-common                              2:3.2.3-1ubuntu3.3                    Samba common files used by both the server a

```

Just to experiment, I installed another instance of Ubuntu II on an empty partition, and installed smb4K there. It installed a bunch of other stuff (including dolphin!!), BUT it works. I can run smb4k, see the shares, double click them, enter user/pwd and they get mounted under /home/smb4k/<sharename>.
So, system-wise, samba works. But I really would like to be able to do that without installing all that kde related stuff. Is there something like smb4k for gnome?

---

### Post by wylfing on 2008-12-03
I don't have any good suggestions for you, other than to confirm that samba browsing has been thoroughly borked since Hardy. (It worked fine in Feisty.) Through vast amounts of experimentation the source of the problem has been pinpointed to Nautilus, which is why samba seems to be working properly (it is) and why everything works fine in KDE.

---

### Post by Quaxo76 on 2008-12-03
This is disappointing. Kubuntu is taking a path I don't like, and Ubuntu falls short on such basic things as networking...
Oh well. I might have to just install smb4k and hope that things will change in the future...

---

### Post by wylfing on 2008-12-03
I agree it is disappointing. You can always do things "old school" though, i.e., create a directory like ./winshares/frotz and then use smbmount to mount a Windows share manually to that directory. It's a tad awkward, but it'll get you access to your stuff.

---

