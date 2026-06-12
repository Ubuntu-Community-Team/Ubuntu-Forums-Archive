---
title: "GTK themeless"
date: 2011-02-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 3rdalbum on 2011-02-18
Hi, for the last couple of days I've had no theme on my GTK.

Opening gnome-appearance-properties used to say that gnome-settings-daemon wasn't running, but now it doesn't say that. However, no matter what settings I choose, they don't apply - still stock Gnome icons and the chunky "no theme" GTK look.

Starting gnome-settings-daemon from the terminal gives this message:

```
** (gnome-settings-daemon:1855): WARNING **: libgdk-3.0.so.0: cannot open shared object file: No such file or directory

** (gnome-settings-daemon:1855): WARNING **: Cannot load plugin 'XRandR' since file '/usr/lib/gnome-settings-daemon-3.0/libxrandr.so' cannot be read.

** (gnome-settings-daemon:1855): WARNING **: Error activating plugin 'XRandR'

** (gnome-settings-daemon:1855): WARNING **: libgdk-3.0.so.0: cannot open shared object file: No such file or directory

** (gnome-settings-daemon:1855): WARNING **: Cannot load plugin 'X Settings' since file '/usr/lib/gnome-settings-daemon-3.0/libxsettings.so' cannot be read.

** (gnome-settings-daemon:1855): WARNING **: Error activating plugin 'X Settings'

** (gnome-settings-daemon:1855): WARNING **: libgdk-3.0.so.0: cannot open shared object file: No such file or directory

** (gnome-settings-daemon:1855): WARNING **: Cannot load plugin 'Wacom' since file '/usr/lib/gnome-settings-daemon-3.0/libwacom.so' cannot be read.

** (gnome-settings-daemon:1855): WARNING **: Error activating plugin 'Wacom'

** (gnome-settings-daemon:1855): WARNING **: libgdk-3.0.so.0: cannot open shared object file: No such file or directory

** (gnome-settings-daemon:1855): WARNING **: Cannot load plugin 'Keyboard' since file '/usr/lib/gnome-settings-daemon-3.0/libkeyboard.so' cannot be read.

** (gnome-settings-daemon:1855): WARNING **: Error activating plugin 'Keyboard'

** (gnome-settings-daemon:1855): WARNING **: libgdk-3.0.so.0: cannot open shared object file: No such file or directory

** (gnome-settings-daemon:1855): WARNING **: Cannot load plugin 'Mouse' since file '/usr/lib/gnome-settings-daemon-3.0/libmouse.so' cannot be read.

** (gnome-settings-daemon:1855): WARNING **: Error activating plugin 'Mouse'

** (gnome-settings-daemon:1855): WARNING **: libgdk-3.0.so.0: cannot open shared object file: No such file or directory

** (gnome-settings-daemon:1855): WARNING **: Cannot load plugin 'Keybindings' since file '/usr/lib/gnome-settings-daemon-3.0/libkeybindings.so' cannot be read.

** (gnome-settings-daemon:1855): WARNING **: Error activating plugin 'Keybindings'

** (gnome-settings-daemon:1855): WARNING **: libgdk-3.0.so.0: cannot open shared object file: No such file or directory

** (gnome-settings-daemon:1855): WARNING **: Cannot load plugin 'Background' since file '/usr/lib/gnome-settings-daemon-3.0/libbackground.so' cannot be read.

** (gnome-settings-daemon:1855): WARNING **: Error activating plugin 'Background'

** (gnome-settings-daemon:1855): WARNING **: libgdk-3.0.so.0: cannot open shared object file: No such file or directory

** (gnome-settings-daemon:1855): WARNING **: Cannot load plugin 'Automount' since file '/usr/lib/gnome-settings-daemon-3.0/libautomount.so' cannot be read.

** (gnome-settings-daemon:1855): WARNING **: Error activating plugin 'Automount'

** (gnome-settings-daemon:1855): WARNING **: libgdk-3.0.so.0: cannot open shared object file: No such file or directory

** (gnome-settings-daemon:1855): WARNING **: Cannot load plugin 'Clipboard' since file '/usr/lib/gnome-settings-daemon-3.0/libclipboard.so' cannot be read.

** (gnome-settings-daemon:1855): WARNING **: Error activating plugin 'Clipboard'

** (gnome-settings-daemon:1855): WARNING **: Name taken or bus went away - shutting down

```

Can anyone help? This has already been reported as a bug but there's been no reply on the bug report. If there is any more information that should be gathered to help on this other person's bug report, then please let me know so it can be fixed.

---

### Post by Jay_Bee on 2011-02-19
I think some of the *svg libraries are broken, try this, open synaptic and reinstall all installed libraries with svg in the name. After that logout and back in. That fixed the problem on my liveUSB couple of days ago.

---

### Post by Harry33 on 2011-02-20
> **3rdalbum said:**
> Hi, for the last couple of days I've had no theme on my GTK.

Opening gnome-appearance-properties used to say that gnome-settings-daemon wasn't running, but now it doesn't say that. However, no matter what settings I choose, they don't apply - still stock Gnome icons and the chunky "no theme" GTK look.

Starting gnome-settings-daemon from the terminal gives this message:

[code]
...

** (gnome-settings-daemon:1855): WARNING **: Cannot load plugin 'Clipboard' since file '/usr/lib/gnome-settings-daemon-3.0/libclipboard.so' cannot be read.

...
Can anyone help? This has already been reported as a bug but there's been no reply on the bug report. If there is any more information that should be gathered to help on this other person's bug report, then please let me know so it can be fixed.

What system do you have installed?
Do you use Gnome3 PPA?
You have a file gnome-settings-daemon-3.0 installed.
In a default Natty-alfa2 there should be gnome-settings-daemon-2.0.

In Gnome3 there are problems concerning themes.

---

### Post by 3rdalbum on 2011-02-21
Clever, clever man - Synaptic is removing the newer gnome-settings-daemon now. I'd forgotten that I'd briefly added the Gnome 3 PPA.

---

### Post by Harry33 on 2011-02-21
> **3rdalbum said:**
> Clever, clever man - Synaptic is removing the newer gnome-settings-daemon now. I'd forgotten that I'd briefly added the Gnome 3 PPA.

You're welcome ):P

---

### Post by speakman on 2011-02-28
I'm having about the same issue, but with a fresh install of Maverick! 

This is the full backtrace of the stuck daemon: [http://pastebin.com/JtUiB8TD](http://pastebin.com/JtUiB8TD)

I've also seen this on my pal's fresh Maverick installation. We've both got new assembled computers, but the only stuff in common is that we're both running X58 chipset and running very fast OCZ SSD disks (RevoDrive vs Vertex 2).

Any ideas?

---

### Post by Harry33 on 2011-02-28
> **speakman said:**
> I'm having about the same issue, but with a fresh install of Maverick! 

This is the full backtrace of the stuck daemon: [http://pastebin.com/JtUiB8TD](http://pastebin.com/JtUiB8TD)

I've also seen this on my pal's fresh Maverick installation. We've both got new assembled computers, but the only stuff in common is that we're both running X58 chipset and running very fast OCZ SSD disks (RevoDrive vs Vertex 2).

Any ideas?

Just to remind you that this is Natty Development Forum.
And this was a GTK+3.0 issue.

---

### Post by speakman on 2011-02-28
Oh, I just found it through Google. Sorry! :D

---

