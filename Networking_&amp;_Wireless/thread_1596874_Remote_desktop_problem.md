---
title: "Remote desktop problem"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by deesto on 2010-10-14
I'm now running 10.10 at home, and I'm trying to get a remote desktop session from elsewhere.  I have "screen sharing" enabled on the Ubuntu host, and I've tried several remote clients now, but they all show only my desktop and pointer, but I can't do anything else: no menus or icons are visible, and there's nothing to click.  In reading about remote connections, it seems this ma be related to X window geometry.  But I don't think there's a "screen sharing" option that deals with window geometry.

Clients I've tried include gvncviewer (from another Ubuntu) and OS X's Screen Sharing, and Chicken of the VNC.  They all show the same blank desktop.

I should also mention that I've tried running an X11 VNC server thread manually through a separate SSH connection:
> x11vnc -display :0 -ncache 10

Accessing a session via this thread has the same result.

---

### Post by deesto on 2010-10-18
I've now also tried this from a Windows 7 machine as well as other client apps in Linux and OS X.  I'm convinced it's a window configuration problem, but I've no idea how to fix it.

---

### Post by krunge on 2010-10-18
What X server are you running on the remote desktop?  What desktop/window-manager are you running there too?  Can you verify using, ps, top, etc, and maybe xdpyinfo that they are actually running there? (e.g. run these from inside a separate ssh shell)

I'm thinking you are running a 'vncserver' (and so Xvnc is the X server) on the remote machine and its default is a very minimal window-manager (twm IIRC.)

---

### Post by deesto on 2010-10-18
Hi krunge,
> **krunge said:**
> What X server are you running on the remote desktop?  What desktop/window-manager are you running there too?  Can you verify using, ps, top, etc, and maybe xdpyinfo that they are actually running there? (e.g. run these from inside a separate ssh shell)
Default X.Org X Server 1.9.0 on the default Gnome WM.  `xdpyinfo` returns a ton of results.
```
$ **ps auwwx|grep X|grep -v grep**
root      1125  0.6  7.0 212552 35484 tty7     Ss+  07:16   3:27 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-3LjJMx/database -nolisten tcp vt7
```

Mayne `-nolisten` is a problem here ... but I don't know where it's coming from, as there's nothing with regard to TCP in /etc/init/gdm.conf .

> I'm thinking you are running a 'vncserver' (and so Xvnc is the X server) on the remote machine and its default is a very minimal window-manager (twm IIRC.)Possibly.  I started out with what I thought was the simplest route: letting Ubuntu/Gnome handle all this by enabling System->Prefs->Remote Desktop.

---

### Post by krunge on 2010-10-18
The "-nolisten tcp" is not a problem.  Unix socket will be used to connect to the X server.

Do you see gnome window manager processes running in ps? (metacity, etc.)

What happens if you type "xterm -display :0 &" on the remote machine?  Do you then see the terminal when you connect via VNC?

---

### Post by deesto on 2010-10-19
Thanks krunge.  all of that seems fine.  What's not fine is what I likely should have mentioned from the start: the Ubuntu instance is a virtual machine (VirtualBox) on a Windows 7 host.  I believe the problem has to do with VB's graphics drivers and guest additions: I've updated those and I can now connect via VNC and get a full desktop session.  Now, the problem is that the visuals are so painstakingly slow that the desktop is unusable: there's a few second delay before any typed characters display on the screen (could be network or graphics, or both), terminal refresh takes seconds, and GUIs are even worse.  Since VB has a very small memory limit on VM graphics (I believe it's 128 MB), I'm not sure this can be helped in any way.  I guess I should be happy that I can get a working shell.

Just to answer your questions for completeness: `xterm -display :0 &` does pop a remote terminal, and:
```
$**ps auwwx|grep metacity|grep -v grep**
metacity --replace
```

If there's a way to get a super-compressed, super-minimal remote window session, maybe that would be useful in this case?

---

### Post by krunge on 2010-10-19
For the delay try running x11vnc with "-noxdamage" to work around Xorg bug.

Also, get rid of "-ncache" to start.  Add it once everything is working OK and see if it makes an improvement or not (it might not be worth it over LAN or even slow down response.)

---

### Post by deesto on 2010-10-20
> **krunge said:**
> For the delay try running x11vnc with "-noxdamage" to work around Xorg bug.

Also, get rid of "-ncache" to start.  Add it once everything is working OK and see if it makes an improvement or not (it might not be worth it over LAN or even slow down response.)
Thanks for that krunge.  I'm giving those options a try now; server-side output [here]("http://deesto.pastebin.com/cbU5RmFH").  But right now, I'm back to square 1, as I'd listened to someone's advice on a VirtualBox forum to install the "official" guest additions that come with the VirtualBox installation into the Ubuntu virtual machine, and that's given me nothing but trouble.  Now I'm back to viewing a blank desktop with no menus, even after re-installing the Ubuntu virtualbox-* packages and modules.

BTW, it was helpful to learn from [this blog post]("http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line") that it's possible to enable/disable Ubuntu's Remote Desktop function from the command line ... this allowed me to disable it for testing and run x11vnc on the same port through my firewall:
```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false
```

**_Warning_**: simply switching the above from *false* to *true* does not work!  Some bug regarding dbus communication with gconftool-2.

---

### Post by deesto on 2010-10-21
Seems fairly clear at this point that the problem is with VB, not with Ubuntu.  Thanks, krunge.

---

