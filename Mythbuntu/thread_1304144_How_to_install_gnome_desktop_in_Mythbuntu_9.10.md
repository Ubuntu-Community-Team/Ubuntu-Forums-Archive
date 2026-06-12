---
title: "How to install gnome desktop in Mythbuntu 9.10?"
date: 2009-10-29
forum: Mythbuntu
---

### Post by yonkiman on 2009-10-29
The xfce scheme is perfect if this was only going to be a myth box, but I want to also run gnome.  I went into the Mythbuntu Control Centre and told it I wanted to configure it as an "Ubuntu Desktop" and and it downloaded a ton of standard Ubuntu packages, but it kept the xfce desktop.

No problem, I then opened Synaptic and asked it to add "Gnome".  It said it would need to remove gnome-bluetooth (??? but fine with me, I don't use bluetooth here) and add about a hundred other packages (also fine with me).  But when I tell it to accept these changes, I get the following error box:

[INDENT]Could not mark all packages for installation or upgrade.  

The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

gnome:
 Depends: gnome-desktop-environment but it is not going to be installed
 Depends: gnome-vfs-obexftp but it is not installable
[/INDENT]

What do I do now?

---

### Post by AJ1000 on 2009-10-29
All you needed was to tick the ubuntu desktop in mythbuntu control center.

After this you will still be in the Xfce desktop. To change desktops do the following.

1) Logout of the xfce desktop. (i.e. select Logout rather than Shutdown or Restart etc).

2) Select your user and then the GNOME desktop option for your user (see the bottom of the screen for this, it will say Xfce but can be changed by the combobox).

3) Then type in your password and login, you will be in the gnome desktop.

However, there will be a policykit issue when trying to shutdown or restart when using the gnome desktop. Another thread solves this issue. The thread is here: [http://ubuntuforums.org/showthread.php?t=1299948](http://ubuntuforums.org/showthread.php?t=1299948)

---

### Post by yonkiman on 2009-10-29
> **AJ1000 said:**
> All you needed was to tick the ubuntu desktop in mythbuntu control center.

Thanks for responding, but I already did that...

> After this you will still be in the Xfce desktop. To change desktops do the following.

1) Logout of the xfce desktop. (i.e. select Logout rather than Shutdown or Restart etc).

I did that, too...

> 2) Select your user and then the GNOME desktop option for your user (see the bottom of the screen for this, it will say Xfce but can be changed by the combobox).

There was no Gnome option.  Which makes sense because Synaptic says Gnome is not installed.

> However, there will be a policykit issue when trying to shutdown or restart when using the gnome desktop. Another thread solves this issue. The thread is here: [http://ubuntuforums.org/showthread.php?t=1299948](http://ubuntuforums.org/showthread.php?t=1299948)

That's a good tip - I'll keep that in mind if I ever manage to get Gnome installed...

---

### Post by AJ1000 on 2009-10-29
Did you select your user? The gnome option does not appear until you press the user and it shows the password dialog.

See this:

[http://ubuntuforums.org/archive/index.php/t-573888.html](http://ubuntuforums.org/archive/index.php/t-573888.html)

or  try, in a terminal,

sudo apt-get install ubuntu-desktop

---

### Post by yonkiman on 2009-10-30
> **AJ1000 said:**
> Did you select your user? The gnome option does not appear until you press the user and it shows the password dialog.

Ahh...my bad - the desktop selection was at the bottom of the screen - I was looking for something in the center dialog box.

Thanks!

---

