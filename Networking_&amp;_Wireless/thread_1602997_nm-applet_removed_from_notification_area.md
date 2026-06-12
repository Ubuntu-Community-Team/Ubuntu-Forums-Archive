---
title: "nm-applet removed from notification area"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by Bytesource on 2010-10-22
Hi all,

After upgrading to Kubuntu 10.10 the icon for the gnome-network-manager (which I had installed instead of the former knetworkmanager) does not show up.

Although I can connect to the Internet, I am not able to set up my VPN without an icon showing up.

Checking at the terminal indicates that there is indeed something wrong here: 

```
sovonet@sovonet:~$ nm-applet
** Message: applet now removed from the notification area
** (nm-applet:3027): DEBUG: old state indicates that this was not a disconnect 0

** (nm-applet:3027): WARNING **: Fallback icon 'gtk-dialog-error' missing: (0) Icon 'gtk-dialog-error' not present in theme
**
ERROR:applet.c:2932:nma_icons_reload: assertion failed: (applet->fallback_icon)
Aborted
```

gnome-icon-theme is installed on my computer. 

Does anybody know what this problem is all about and how to solve it?

Stefan

---

### Post by Bytesource on 2010-10-22
Update:

I managed to to get the nm-applet icon appear in the system tray following this workaround:

1) Select a Gnome icon theme
System Settings --> Application Appearance --> Icons: select *Gnome*

2) In terminal type
```
nm-applet
```

Now the nm-applet appears in the system tray, but using Gnome icons in Kubuntu is rather ugly.

There my question: Is there a way to selectively copy the icons used by nm-applet to the Oxygen icon collection?


Stefan

---

### Post by Bytesource on 2010-10-23
I finally found a more pleasant workaround that works for me:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2566236.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2566236.html)

Make sure to log in as root before following the commands listed in the above link:
```
sudo su
```

Stefan

---

### Post by ZeroGodForce on 2010-10-24
I'm having the same problem (except I just installed 10.10 clean), but I have neither the gnome-icon-theme nor the tango-icon-theme installed and as far as I've tried, I can't even find them let alone install them.  So unless I'm missing a trick (which is entirely possible) I can't even execute the workarounds.  Could one of you possibly help me out cause this is driving me absolutely freaking mental! Seriously I am this close to giving that my Linux partition back to Wndows! :mad:

Thanks.

---

### Post by Bytesource on 2010-10-24
You can install the Tango icon theme by copying the following command into the terminal (*Konsole* on Kubuntu):

```
sudo apt-get install tango-icon-theme
```

Best regards,

Stefan

---

### Post by nortexoid on 2010-10-24
> **Bytesource said:**
> I finally found a more pleasant workaround that works for me:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2566236.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2566236.html)

Make sure to log in as root before following the commands listed in the above link:
```
sudo su
```

Stefan

Thanks! I had found that bug report, commented there, but forgot to subscribe so I didn't get the workarounds. Thought I would do a search again and found this thread. Fantastic.

---

### Post by ZeroGodForce on 2010-10-27
Thanks Stefan, and everyone else; that one was really driving me nuts.  

Now that its working I can't believe how much better is than the KDE network manager. Don't get me wrong, I've got much respect for KDE's developers but I just don't understand why it's so bad when the Gnome one is so good.

---

