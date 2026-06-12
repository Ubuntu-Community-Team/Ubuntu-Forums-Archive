---
title: "Connecting Xubuntu to a Network."
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2010-07-14
Hi guys i have a computer running xubuntu that I want to connect to a computer running Debian. Can some point me in the right direction on how to set it up. There doesn't appear to be alot of options and my knowledge on networking related commands is lacking somewhat.

All I need it to do is see the Debian comp and grab files from a folder on one of its HDD's.

---

### Post by moore.bryan on 2010-07-14
If you're on the same LAN, you could just [SSH]("https://help.ubuntu.com/community/SSH") into it or use [SSHFS]("https://help.ubuntu.com/community/SSHFS") to mount the folders...

---

### Post by Jonny87 on 2010-07-15
> **moore.bryan said:**
> If you're on the same LAN, you could just [SSH]("https://help.ubuntu.com/community/SSH") into it or use [SSHFS]("https://help.ubuntu.com/community/SSHFS") to mount the folders...

Cheers I'm looking into that.

Just noticed I can find my Debian server through Gigolo, but for some reason I can't connect to it. And I can only see one "print" folder under it which I don't even think exists. Is how do I go about connecting and browsing to the desired drive and folder, or how do I enable it show up?

Note i want to set it up so that my not so tech savvy family can point and click there way through if I'm not around to do it for them.

---

### Post by moore.bryan on 2010-07-15
> **Jonny87 said:**
> Cheers I'm looking into that.

Just noticed I can find my Debian server through Gigolo, but for some reason I can't connect to it. And I can only see one "print" folder under it which I don't even think exists. Is how do I go about connecting and browsing to the desired drive and folder, or how do I enable it show up?

Note i want to set it up so that my not so tech savvy family can point and click there way through if I'm not around to do it for them.

Hmm... point-and-click complicated things a little bit. How good are you with the CLI? I used to SSHFS my media collection on a Debian iMac through fstab on my Thinkpad running Ubuntu. Is that what you're looking for?

---

### Post by Jonny87 on 2010-07-15
> **moore.bryan said:**
> Hmm... point-and-click complicated things a little bit. How good are you with the CLI? I used to SSHFS my media collection on a Debian iMac through fstab on my Thinkpad running Ubuntu. Is that what you're looking for?

CLI? Prob not that good but am willing to learn.

---

### Post by moore.bryan on 2010-07-15
No worries then... I'd first have a read [here]("http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-form-etcfstab") and figure-out, for sure, if this is what you're looking for.

---

### Post by Morbius1 on 2010-07-15
If you're going down the ssh path then this is just informational.
> Just noticed I can find my Debian server through Gigolo, but for some  reason I can't connect to it. And I can only see one "print" folder  under it which I don't even think exists. Is how do I go about  connecting and browsing to the desired drive and folder, or how do I  enable it show up?Gigolo is a Samba browser that can mount remote shares. The reason you can only see one "print" folder on your Debian system is that you haven't created any shares on that system for Gigolo to find. The fact that it can find the machine and the print$ folder is actually a good sign though. It means that samba is working between the two systems.

---

### Post by Jonny87 on 2010-07-15
> **Morbius1 said:**
> If you're going down the ssh path then this is just informational.
Gigolo is a Samba browser that can mount remote shares. The reason you can only see one "print" folder on your Debian system is that you haven't created any shares on that system for Gigolo to find. The fact that it can find the machine and the print$ folder is actually a good sign though. It means that samba is working between the two systems.

Aside from creating a shared folder, what do I need do to get it to connect?

---

### Post by Morbius1 on 2010-07-15
If you created a shared folder on the debian system and are allowing guest access you don't need anything else. Gigolo should see it and mount it.

---

### Post by Jonny87 on 2010-07-15
> **Morbius1 said:**
> If you created a shared folder on the debian system and are allowing guest access you don't need anything else. Gigolo should see it and mount it.

It keeps asking for a pass word and regardless of what password I enter it just keeps prompting for it.

---

### Post by Morbius1 on 2010-07-15
From the debian system post the output of the following commands:
```
net usershare info 
sudo net usershare info
testparm -s
```

---

### Post by Jonny87 on 2010-07-15
Sorry, i've since worked it out the password thing. But now its almost there Its connecting and showing up in the window but I can't open it up in Gigolo or thunar to see the files.

---

### Post by Morbius1 on 2010-07-15
> Its connecting and showing up in the window but I can't open it up in  Gigolo or thunar to see the files.     You should get a folder icon with a name of the form: "share_name on machine_name.

If you double click that it doesn't open up?

Go into Thunar ( sorry it's been a while since I've used Thunar ), make sure "Show Hidden Files" is enabled and go to: /home/user_name/.gvfs. Your remote folder should be there.

---

### Post by Jonny87 on 2010-07-15
> **Morbius1 said:**
> You should get a folder icon with a name of the form: "share_name on machine_name.

If you double click that it doesn't open up?

Go into Thunar ( sorry it's been a while since I've used Thunar ), make sure "Show Hidden Files" is enabled and go to: /home/user_name/.gvfs. Your remote folder should be there.

Yea I see the remot folder in Gigolo but can't open it, its not in .gvfs either, theres nothing there.

---

### Post by Morbius1 on 2010-07-15
I can't reproduce your problem so I went to "help":
[http://www.uvena.de/gigolo/help.html](http://www.uvena.de/gigolo/help.html)
> Gigolo Preferences
The File Manager setting

This setting specifies the command and possible arguments for a file manager to launch when a resource should be opened from within Gigolo. By default, Gigolo uses gvfs-open which should be a good choice for most users. gvfs-open itself launches the system's default file manager with the correct path for the chosen resource. If this does not work for you for some reason, you can change the command to e.g. nautilus to launch Gnome's default file manager.

Gigolo automatically adds the URI of the resource, e.g. sftp://user@server.tld/. So the specified file manager should know how to handle such URIs.

Note

[COLOR=Blue]If your file manager cannot handle URIs, you should install gvfs-fuse, set up FUSE on your system and use gvfs-open as the file manager command. gvfs-fuse will then launch the default file manager with the correct path.[/COLOR] For details on this, see Open resources in Thunar on Xfce 4.4 and 4.6.

You might want to see if you have the requisite packages installed.

---

### Post by Jonny87 on 2010-07-15
SUCCESS!! I got it working though it's a bit slow not sure if its the network or the machine. will play around and try to find out.

---

