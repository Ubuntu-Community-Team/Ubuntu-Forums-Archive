---
title: "Overlay Scrollbars"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by seeker5528 on 2011-03-03
Looking forward to this. Read the blog post...

[http://www.markshuttleworth.com/archives/615](http://www.markshuttleworth.com/archives/615)

added the PPA

[https://launchpad.net/~ayatana-scrollbar-team/+archive/release](https://launchpad.net/~ayatana-scrollbar-team/+archive/release)

added the appropriate line to '~/.xprofile':

```
# This file '~/.xprofile' should be used to customize the environment of your X login session similar
# to the way you would use '~/.profile' to customize the environment of your command line login session.

# export PATH="~/some_directory:$PATH"
# export WINDOW_MANAGER="/usr/bin/fluxbox"

export LIBOVERLAY_SCROLLBAR=1
```

Logged out, logged in...

It does look nice in the applications that use it, but seems a lot of applications need to be updated to use it.

You don't see them in Firefox. That's not actually a big suprise. But you also don't see them in gnome-terminal, synaptic, cream.

Later, Seeker

---

### Post by kahping on 2011-03-21
What are the requirements to run this? I've tried with Natty in a VM and have never seen it work. Does it require hardware acceleration to work? or, does it simply not work at all in a VM?

---

### Post by Amaranth on 2011-03-21
It won't work in synaptic because sudo drops your environment so LIBOVERLAY_SCROLLBAR isn't set in the environment synaptic is running in. Firefox is obviously not going to work, they don't actually use GTK+ (they use the lower level parts to draw things in a themed way but not the actual widgets). No idea why gnome-terminal and cream (whatever that is) wouldn't work.

Based on the way this looks visually it appears to require compositing but not 3D acceleration (GTK+ can do in-window compositing using software rendering). Perhaps your virtualbox setup has the X composite extension disabled.

---

### Post by kahping on 2011-03-22
> **Amaranth said:**
> Perhaps your virtualbox setup has the X composite extension disabled.

That raises some interesting questions: Why isn't it enabled? How do I enable it? Is it off by-default, or did I do something that disabled it?

I guess I'll google it, but if anybody knows anything that'll be a big help.:D

Update:

After some googling, I'm guessing it's because I'm using fglrx. Although my Xorg.0.log says:

[    34.125] (II) fglrx(0): Enable composite support successfully

, I wouldn't be surprised that it's buggy...

---

### Post by seeker5528 on 2011-03-24
> **Amaranth said:**
> It won't work in synaptic because sudo drops your environment so LIBOVERLAY_SCROLLBAR isn't set in the environment synaptic is running in. Firefox is obviously not going to work, they don't actually use GTK+ (they use the lower level parts to draw things in a themed way but not the actual widgets). No idea why gnome-terminal and cream (whatever that is) wouldn't work.

It works in Synaptic now.

Cream is a set of macros that work with VIM to provide a GUI that works more like your common text editors while still providing access to the advanced capabilities that VIM provides.

On a secondary note, I just noticed that the menus in Cream are not displayed in either the top panel or in the application window. Hmmm. Basic functions are available on a toolbar so it´s still usable for basic text editing, but in order to take advantage of the real power of VIM you need the menus.

Later, Seeker

---

### Post by mc4man on 2011-03-24
> **seeker5528 said:**
> 
On a secondary note, I just noticed that the menus in Cream are not displayed in either the top panel or in the application window. Hmmm. Basic functions are available on a toolbar so it´s still usable for basic text editing, but in order to take advantage of the real power of VIM you need the menus.

Until fixed, if it can be, you can either adjust the binary w/  an export of 
export UBUNTU_MENUPROXY=0  
(couple of ways to do that

or if starting from the .desktop and or r. click context menu  just edit the launch command in cream.desktop to 
```
Exec=env UBUNTU_MENUPROXY=0 cream
```

```
gksudo gedit /usr/share/applications/cream.desktop

```
This will return working menus to cream window

---

### Post by seeker5528 on 2011-03-25
@mc4man

Thanks for that.

Open/Save, Cut/Copy/Paste, Search/Search & Replace, and Spell check are all on the toolbar, which usually covers my personal needs, when I need such things. 

More typically though I am just adding/removing small bits so typicall just starting Vim from the command line. 

Many is the time I have been using something other than Vim and typed
```
:
wq
```

to save and exit. :oops:

Later, Seeker

---

### Post by traxxas on 2011-04-12
Appmenus work with cream and gvim you just need to run it with the -f flag.

```
Exec=cream -f %F
```

Will solve the problem for opening cream with the launcher.  For launches from terminal you'll need to add an alias to your ~/.bashrc

```
alias cream="cream -f"
```

> **mc4man said:**
> Until fixed, if it can be, you can either adjust the binary w/  an export of 
export UBUNTU_MENUPROXY=0  
(couple of ways to do that

or if starting from the .desktop and or r. click context menu  just edit the launch command in cream.desktop to 
```
Exec=env UBUNTU_MENUPROXY=0 cream
```

```
gksudo gedit /usr/share/applications/cream.desktop

```
This will return working menus to cream window

---

### Post by mc4man on 2011-04-12
> **traxxas said:**
> Appmenus work with cream and gvim you just need to run it with the -f flag.

```
Exec=cream -f %F
```

Will solve the problem for opening cream with the launcher.  For launches from terminal you'll need to add an alias to your ~/.bashrc

```
alias cream="cream -f"
```

That does work  -  the latest cream package keeps menus in cream (and unlike previously they work without any adjustment.

Myself prefer menus in to remain some apps inc. editors

---

