---
title: "Drag and Drop failing with VNC"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by stanf on 2010-05-30
Hello,

I have been using Ubuntu 10.04 (32 bit) as a headless workstation, running a VNC screen. Worked perfectly for about 3 weeks, then suddenly, I lost the Drag and Drop capability, for all applications.

For example:


[LIST]
[*]Dragging and dropping to move items on the desktop does not work. The item simply pops back to the original location.
[*]Dragging and dropping to move items from one folder to another does not work. Same behavior -- the item just pops back to the original location.
[*]Dragging and dropping Bookmarks in Firefox does not work. The attempted Drag and Drop is ignored.
[*]Copy and paste still works fine.
[*]The problem does NOT occur when using an attached monitor (primary display screen :0).
[/LIST]
After much Googling (including these forums), I suspected that the changed behavior was caused by an update (from Ubuntu Update Manager). I confirmed this with the following:


[LIST]
[*]Reinstalled Ubuntu 10.04 fresh from the live cd.
[*]Configured minimal networking and installed VNC server.
[*]Tested Drag and drop -- works okay
[*]Applied pending updates (116) from Ubuntu Update Manager
[*]Tested Drag and drop -- not working
[/LIST]
I am using vnc4server and openssh-server installed from the repositories using Synaptic.

Has anyone else observed this problem? Any Ideas?

Thanks in advance.,

Stan

---

### Post by tacted on 2010-05-30
Stan,
I'm getting the same behavior, too. Files spring back to their original location when dropped. This happens from the Downloads directory to the desktop and to the Trash in the places side pane.

Thanks,
Ted

---

### Post by stanf on 2010-05-30
Ted,

Thanks for the reply. Sounds like the same issue. Any GUI operation that requires drag and drop fails.

I have tested this with several VNC viewer clients (linux and windows) and the problem occurs with all. So it does not appear to be a viewer problem.

I'm now setting up the same test with Linux Mint (ubuntu derivative) to see if I get the same result; I'll post the result here.

Stan

---

### Post by stanf on 2010-05-31
I have the luxury of testing with a bare metal machine -- did  a fresh install of Linux Mint 9 from the live CD, accepted all updates from the Update Manager (there were 9).

The same problem occurs in the Mint 9 installation. Drag and drop does not work over VNC after updating the system.

I have been using Mint 8 (based on Ubuntu 9.10) on another PC for about 6 months, up-to-date and have not seen this problem. Using the same VNC server on the Mint 8 box, and same viewers on the remote clients.

---

### Post by stanf on 2010-05-31
Still have not been able to figure this one out, it's a show stopper for me on 10.04. So for now I have gone back to Ubuntu 9.10 and all upgrades. VNC has full GUI drag and drop functions.

When time permits, I'll investigate this further in Virtual Machine environment. Hoping this thread attacts some additional info on this problem.

---

### Post by tacted on 2010-06-12
I removed vncserver and am using x11vnc instead. Drag and drop is working again. I can start it when I need it with...
sudo x11vnc -safer  -geometry 1024x768 -xkb -display :0 &

There's lots of options for starting x11vnc. You may need to find what works for you. [http://www.karlrunge.com/x11vnc/x11vnc_opts.html](http://www.karlrunge.com/x11vnc/x11vnc_opts.html)

-Ted

---

### Post by stanf on 2010-06-13
Ted,

Thanks for the suggestion. I installed and fired up x11vnc and it worked right off the bat. Still having some challenges getting it to work full screen and adjusting the geometry. As you said, there are a lot of options to try out!

Again, thanks for pointing out this alternative!

Stan

---

### Post by jspenguin on 2010-12-20
This is still broken in 10.10. Both RealVNC and TightVNC servers fail, so I think something may have changed in Xlib.

I tried with Xvfb and x11vnc, and drag & drop works. This provides an inefficient, temporary workaround for a headless system.

If Xvfb can make it work, why not XTightVNC?

---

### Post by stanf on 2010-12-20
jspenguin - Thanks for the new info on Ubuntu 10.10 - I ended up staying with 9.10 because the vnc4server gave me cleaner and more responsive window behavior (than with x11vnc) on my particular setup. I'm using the Ubuntu to host VirtualBox, and that's pretty much all it is used for. Does a good job on that with the vnc4server.

Sooner or later I'll need to upgrade, I'm really a procrastinator. So when the time comes, I'll try this again. I think I will probably go for a straight Debian host OS on this machine.

Stan

---

### Post by shearerc on 2011-01-03
I can confirm this bug also present in Debian testing(squeeze), both 32-bit and 64-bit. [-X

package: tightvncserver  1.3.9-6.1+b1  (vnc process is Xtightvnc)


As soon as I moved to NX, I can drag n drop again. Hell, even Xvfb + x11vnc combo works fine.

---

### Post by shearerc on 2011-01-04
Managed to narrow down the problem to libgtk2.0-0.

libgtk2.0-0 stable(lenny) -> DnD works
libgtk2.0-0 lenny-backport (libgtk2.0-0_2.18.6-1~bpo50+1_i386) -> DnD still works
libgtk2.0-0 testing (libgtk2.0-0_2.20.1-2_i386) -> DnD broken

---

### Post by stanf on 2011-01-04
Yes, similar result reported here:

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/587856](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/587856)

---

### Post by redvenomweb on 2011-05-29
Has there been any progress with this bug?  It would be nice to be able to drag and drop again.

---

### Post by Zerauskire on 2011-07-05
Anyone got any updates regarding this bug? Any clue if it will ever be fixed?

---

### Post by stanf on 2011-09-04
Just came back and took another look at this -- appears to be a smattering of folks posting inquiries about this on the web, some referencing this thread. As far as I can tell, this Gnome bug has not received any recent attention.

There's a workaround out there that involves downgrading libgtk2.0-0. Problem with this solution is that several dependencies also need to be downgraded to versions that will not support the latest version of many common applications. So that does not appear to be practical.

As others have noted in this thread, there are alternatives. I have settled on NoMachine's Free NX.

---

### Post by spiky001 on 2011-09-04
Just seen this thread I have 11.04 I use Remmina vnc, I can drag and drop on my headless server, If this helps anyone

---

### Post by stanf on 2011-09-04
Interesting that it's working for you now with Remmina. I have not personally tried that client. Did note [here]("http://askubuntu.com/questions/47241/cannot-move-drag-drop-windows-items-in-remote-vnc-session") that another user observed the bug with 11.04/Remmina. That was around 6 June 2011 I think. Perhaps there has been some recent progress?

---

### Post by marvinthesad on 2011-09-11
> **spiky001 said:**
> Just seen this thread I have 11.04 I use Remmina vnc, I can drag and drop on my headless server, If this helps anyone

I don't know what vncserver is running (x11vnc?) but vnc4server is still not working (both on Ubuntu 11.04), even with Remmina (which uses libvncclient anyway), so I don't think Remmina client is a lot different then any other client, like vncviewer...

---

### Post by a1an on 2012-02-03
The issue is still there as of today on:
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

using xvnc4server
Version: 4.1.1+xorg4.3.0-37ubuntu2

and libgtk2.0-0
Version: 2.24.4-0ubuntu2

I've just seen on the launchpad bug referenced above that there is a fix in gtk-3 and gtk-2.24.8 but its not available on 11.04 updates so I guess no luck unless upgrading to higher release, quite sad.

---

### Post by flittermice on 2012-04-09
Newly installed Lubuntu server (11.10) here. 
I'm using vnc4server which starts a LXDE session.
Viewer: vinagre or remmina

Guess what: It still doesn't work. 
My libgtk version is 2.24.6-0ubuntu5.

Just found:
*"This bug was fixed in the package gtk+2.0 - 2.24.8-2ubuntu4"*
Looks like I will upgrade to Precise a.s.a.p...

---

