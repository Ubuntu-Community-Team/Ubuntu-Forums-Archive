---
title: "Amarok problems after upgrading to 10.10"
date: 2010-10-11
forum: Multimedia Software
---

### Post by rockaroundtheclock on 2010-10-11
I'm having a couple of problems with Amarok after upgrading. First when I open Amarok the window is just blank grey. No GUI. If I maximize/resize the window the GUI shows up. That happens every time I open it. 

The other problem is more serious. Sometimes the top menu (Amarok,View,Playlist,Tools,etc) stops working. As in, the menu doesn't show up when I click any of those headings. This only happens sometimes, usually after having Amarok open for a while.

Anyone else having these problems?

---

### Post by jpelorat on 2010-11-13
Hi,

I'm a Kubuntu/Amarok user and since I installed from the scratch Kubuntu 10.10 I'm having the same problem with the menus that don't work after Amarok it's been in use for a while. I've looked on the net for answers and this is the only post I've found where this odd behavior is described.  No solutions or answers so far.

---

### Post by tommcd on 2010-11-13
> **rockaroundtheclock said:**
> I'm having a couple of problems with Amarok after upgrading. ...
Are you still having these problems? 
If so, try renaming the .amarok file or directory in your home directory to .amarok.bak. Then restart Amarok. This will create a new .amarok in your home directory. Perhaps there are some settings in your .amarok in your home directory that are not compatible with the newer version of Amarok in 10.10.
You could also try renaming any .kde directories in your home directory to .kde.bak if you still have problems.

And welcome to the Ubuntu forums!

---

### Post by mad_dogs_bite on 2010-11-15
Same menu problem here. It also extends to right-click menus and other menus in the GUI. In my case I don't think it can be due to a corrupted profile resulting from an update, as this was the first Amarok 2 (used Amarok 1.4.10 up until now) install on a fresh Ubuntu 10.10.

Furthermore I don't have the grey GUI upon start, but something similar: when I start Amarok it is minimized to the tray. I have to click the tray icon and choose "restore", and then I get the window (that annoyingly is not maximized). The tray icon in itself also behaves rather oddly: before when clicked it would restore the window, but now it only shows the menu. Is this normal?

A last annoying thing is that I can't read tooltips; they're just black boxes. I'm using the standard Ubuntu 10.10 theme, which has black backgrounds for the tooltips. I assume that Amarok takes the theme tooltip background color, but somehow does not adapt its text color... Is there anything that can be done about this without changing the Ubuntu theme?

---

### Post by sn6uv on 2010-11-30
I have the exact problem as described above running 64 bit ubuntu 10.10 using gnome. I tried a fresh install to no avail.

---

### Post by Papadzulinux on 2010-11-30
Same thing here, but add on top of that that my Amarok doesn't recognise mp3s, even after installing the restricted modules. It just goes through the whole playlist quickly... sad, sad, sad. did I miss something?

---

### Post by mc4man on 2010-11-30
Don't use amarok 2 but have installed it from time to time. Have noticed if things go south it's a pita to restore usability.

Easiest way is to open the home folder, if you don't have any other kde apps or don't mind losing settings then just delete the whole .kde folder itself. (hidden folder
Otherwise open it and delete all amarock folders and files - browse around, there will be several. (share - /apps and /config

> Amarok doesn't recognise mp3s
make sure libxine1-ffmpeg is installed

---

### Post by hiçbir&#351;eyyok on 2010-12-01
Same problems. Additionally, the program always crashes when the 'Save Current Playlist' button is pressed.

---

### Post by luke0111 on 2011-01-07
I also get this menu problem from time to time: right clicking does not work in the playlist and the top menus do not pull down.

I notice I get increased CPU usage from Amarok when I'm experiencing this problem. Restarting Amarok fixes the problem. I am using a new installation of Amarok (fresh ubuntu 10.10 and therefore fresh Amarok installation).

I notice it happens sometimes (not everytime) when I fetch an album cover. 

Papadzulinux's mp3 problem is a different issue having to do with xine1, as mc4man mentioned.

---

### Post by afrodeity on 2011-04-21
```


albumcovers                                         my.cnf
amarokcollectionscanner_batchincrementalinput.data  mysqle
amarokcollectionscanner_batchscan.xml               playlistgenerator.xml
collection_scan.files                               playlist_layouts
current.xspf                                        playlists
dynamic_current.xml                                 podcasts
dynamic.xml                                         scripts
file_browser_layout                                 tooltipcover.png
layout

```
which file do I delete to totally reset the db?

---

### Post by CJ_Hudson on 2011-07-18
Amarok works fine for me except it crashes after about 20-40 minutes whilst moving automatically on to the next track. Incidentally, deriving from the crash bug report I filed with kde open crash bug reporter, it makes no difference whether it's an .wma or a .mp3 file.

I did wonder if the crash had anything to do with my screensaver in Ubuntu that might start after a certain amount of time, and somehow interferes with Amarok?

---

### Post by Degovx on 2012-01-12
I am having the same problem. All menus (right click, toolbar, and things like playlist randomizer options) stop working after Amarok has been running for a while. Similar to the poster above, that experiences high CPU usage, I get high usage on my video card. I don't believe it's a video card problem since this is the second video card this problem has exhibited itself on.

I have experienced this problem now on 2 fresh installs of 64 bit Ubuntu. I have tried deleting the .kde folder and removing and re-installing Amarok to no avail. 

Quitting and restarting Amarok will fix the problem briefly. I love Amarok so these inconveniences won't stop me from using it but it sure would be nice if they weren't there!

---

### Post by afrodeity on 2012-01-13
Try deleting the db file, or settings file, Amarok should then rebuild it.

---

### Post by ansedor on 2012-02-16
> **sn6uv said:**
> I have the exact problem as described above running 64 bit ubuntu 10.10 using gnome. I tried a fresh install to no avail.

I found a work around to the menu problem, but it is quite annoying:
Find the file amarokrc, in many cases (but not always) in
.kde/share/config
Search for MainWindow with your favorite editor:

[MainWindow]
Height 1080=1081
State=AAAA/wAAAAD9AAAAAQAAAAAAAAeAAAAD1PwBAAAAA/sAAAAkAE0AZQBkAGkAYQAgAFMAbwB1AHIAYwBlAHMAIABkAG8AYwBrAQAAAAAAAAGLAAAAsAD////7AAAAGABDAG8AbgB0AGUAeAB0ACAAZABvAGMAawEAAAGRAAAEYgAAAEwA////+wAAABoAUABsAGEAeQBsAGkAcwB0ACAAZABvAGMAawEAAAX5AAABhwAAAYcA////AAAAAAAAA9QAAAAEAAAABAAAAAgAAAAI/AAAAAEAAAACAAAAAgAAABYATQBhAGkAbgBUAG8AbwBsAGIAYQByAQAAAAD/////AAAAAAAAAAAAAAAYAFMAbABpAG0AIABUAG8AbwBsAGIAYQByAAAAAAD/////AAAAAAAAAAA=
ToolBarsMovable=Disabled
Width 1920=1921

Delete the State line, as in:
[MainWindow]
Height 1080=1081
ToolBarsMovable=Disabled
Width 1920=1921

Save the file, and restart Amarok. The annoying thing is You must redo this almost every time before starting amarok.

---

