---
title: "Thunar and network browsering"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by Tares on 2011-10-23
hello,

how can I browse my network with thunar? I've seen some screenshots that thunar had "Network" link on the side bar, but my doesn't have this option.

---

### Post by Kronalias on 2011-10-23
You need to use Gigolo which, on a standard installation, doesn't work. Read on.

Gigolo is part of the standard installation.
Application Menu => System => Gigolo

Just check Gigolo is borked. Start it and View => Sidepanel. If you can't see a Network tab read on.
Gigolo needs gvfs-backends, which isn't loaded, so:
sudo apt-get install gvfs-backends
Log out, log back in and see whether Gigolo works. If it doesn't then read on.
Add yourself to the fuse group
sudo gpasswd -a YOURNAME fuse
Log out, log back in and see whether Gigolo works. If it doesn't then read on.
Create the file ~/.local/share/applications/defaults.list so that Thunar is used to open folders by gvfs-open:
leafpad ~/.local/share/applications/defaults.list
and put the following lines in it:
-------------------------------------------------
x-directory/gnome-default-handler=Thunar.desktop
inode/directory=Thunar.desktop
x-directory/normal=Thunar.desktop
-------------------------------------------------

When Gigolo's working:
Edit => Preferences => General =>
 File Manager: gvfs-open
 Bookmark Auto-Connect Interval: 60
Edit => Preferences => Interface =>
 Tick Save window position and geometry
 Tick Show status icon in the Notification Area
 Untick Start minimized in the Notification Area
 Tick Show side panel
 Tick Show auto-connect error messages
Edit => Preferences => Interface =>
 Tick Show toolbar
 Style: Both
 Orientation: Horizontal
View =>
 Tick Toolbar
 Tick Side Panel
 Tick Status Icon
 Radiobutton On: View as Detailed List
Click the Network tab, browse, click on network share =>
Service type: Custom Location, click Connect
Right click in right pane on a connection and Create Bookmark, Ok
Click the Bookmarks tab, highlight a connection and click Edit Bookmarks.
Higlight a Bookmark in the right pane, right click it and click Edit Bookmark.
Double click on a bookmark (or right click and edit).
Now tick Autoconnect if you want to...

Et viola! You have a large violin and a Network thingy in Thunar!

---

### Post by keltux on 2011-11-13
If you switch to "toolbar style" under view in thunar, you can simply type in the network address like 
sftp://user@192.168.0.1:22/folder
:)

---

### Post by capscrew on 2011-11-13
> **keltux said:**
> If you switch to "toolbar style" under view in thunar, you can simply type in the network address like 
sftp://user@192.168.0.1:22/folder
:)

Ah, yes; but the OP didn't ask how to connect.  The question was how to browse.  As in:"how can I **browse** my network with thunar? "

---

