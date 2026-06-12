---
title: "X server already running error on bootup"
date: 2008-12-19
forum: Mythbuntu
---

### Post by jabrown65 on 2008-12-19
I using mythbuntu Intredip with all updates install.

Since the last update mythubuntu stopped booting up properly. Instead of mythtv frontend, I get the desktop with a message saying that the last session lasted less than 10 seconds etc. with the option of "Viewing Details". If I don't view details then it quickly drops out to a login screen. If I do view the details can use the desktop, for as long as I leave the details displayed. Once I close the details it quickly drops out to the login screen.

The 'details' are:

/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-EORXvR5234/agent.5234

** (xfwm4:5365): WARNING **: The display does not support the XComposite extension.

** (xfwm4:5365): WARNING **: Compositing manager disabled.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (update-notifier:5379): WARNING **: already running?


** (nm-applet:5384): WARNING **: No connections defined

** (update-notifier:5398): WARNING **: already running?


** (nm-applet:5404): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:5404): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Session management error: IO error occured opening connection

(xfce4-panel:5372): libxfcegui4-WARNING **: ICE I/O Error

(xfce4-panel:5372): libxfcegui4-WARNING **: Disconnected from session manager.
ICE default IO error handler doing an exit(), pid = 5376, errno = 104
Segmentation fault




I tried reinstalling networkmanager  and nm-applet, but the problem remains. Similarly, I have tried updating again to no avail

I have been searching using google and can't find anything on the problem

Have others experienced this?

As I said, it was working fine before the my last update.

Ideas?

---

### Post by piobair on 2008-12-19
[/QUOTE]

(xfce4-panel:5372): libxfcegui4-WARNING **: ICE I/O Error

(xfce4-panel:5372): libxfcegui4-WARNING **: Disconnected from session manager.
ICE default IO error handler doing an exit(), pid = 5376, errno = 104
Segmentation fault

[/QUOTE]

In a Mythtv forum, someone else had the same problem with the Mythtv backend, as did I. I note that Mythtv uses OpenGL, and if I try to compile a trivial OpenGL program, I get a segmentation fault. I suspect that the problem is with the Nvidia driver. I am using an Nvidia Geforce 6200, and the generic nv driver.

---

### Post by jabrown65 on 2008-12-20
Thanks, but my hardware is an EPIA EN12000 motherboard using the onboard VIA video and hardware accelerator, so no Nvidia or OpenGL involved. Also, it is a fanless mythtv frontend which accesses the backend via a wired gigabyte ethernet network. The backend is working fine, as is a Ubuntu frontend running on the same EPIA frontend in a different dual boot partition which hasn't been updated.

(I always have two installations on the frontend to make sure that at least one is always working. This means that whatever happens I can always watch recordings! One installation is Mythbuntu and the other is Ubuntu. Currently the Mythbuntu partition is not working, and the Ubuntu partition is not being updated or changed until I get Mythbuntu working again. I highly recommend this strategy! The rest of the people in the household greatly appreciate it!)

---

### Post by teddydov on 2008-12-20
I would like to join in. 
I am having the same issue ever since the last update.. I was told to restart my computer in order to apply changes... 
since then I am getting the this error no matter what I try.. 

please help...

---

### Post by curtistee on 2008-12-20
> **teddydov said:**
> I would like to join in. 
I am having the same issue ever since the last update.. I was told to restart my computer in order to apply changes... 
since then I am getting the this error no matter what I try.. 

please help...

Same issue here; it seems to be specific to compiz for me. I tried uninstalling NetworkManager & got segfaults from compiz anyway. There is a workaround I found somewhere (don't click on the "OK" button in the dialog box), so it's merely an annoyance.

Here's my .xsession-errors. Note I suspect the segfault message at the end is from compiz, but can't say for sure:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
User id(1000) name = curtis
euid = root
dir '/var/turboprint/curtis' already existing
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 10 overrides entry on line 7
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 

** (update-notifier:11308): WARNING **: already running?

** (nm-applet:11328): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

(nm-applet:11328): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (update-notifier:11320): WARNING **: already running?

evolution-alarm-notify-Message: Setting timeout for 39594 1229846400 1229806806
evolution-alarm-notify-Message:  Sun Dec 21 00:00:00 2008

evolution-alarm-notify-Message:  Sat Dec 20 13:00:06 2008

** (update-notifier:11342): WARNING **: already running?


** (update-notifier:11371): WARNING **: already running?

** (nm-applet:11363): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

(nm-applet:11363): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(xfce4-panel:11253): libxfcegui4-WARNING **: ICE I/O Error

(xfce4-panel:11253): libxfcegui4-WARNING **: Disconnected from session manager.
Segmentation fault
```

---

### Post by curtistee on 2008-12-20
Solved. I did a little more digging & found this in dmsg:

[FONT=Courier New][27856.597170] xfce4-session[16168]: segfault at b72932f8 ip b72932f8 sp bf9c03c0 error 4 in LC_CTYPE[b7299000+3f000]

[/FONT] Then I found this:

[http://ubuntuforums.org/showthread.php?p=6330684](http://ubuntuforums.org/showthread.php?p=6330684)

and tried getting rid of the old xfce4-session.rc as described:

[FONT=Courier New][18:33:54 curtis ~]$ mv ~/.config/xfce4-session/xfce4-session.rc ~/.config/xfce4-session/xfce4-session.rc.old[/FONT]

Logged out & back in again; everything's fine & dandy. HTH.

---

### Post by jabrown65 on 2009-01-12
Yep, getting rid of the old xfce4-session.rc as described worked for me too! Thanks!

---

