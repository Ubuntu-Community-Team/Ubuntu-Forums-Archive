---
title: "Remote Desktop FROM Windows 7 TO Ubuntu 11.04 via TightVNC Viewer = Wallpaper Only"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by Ryoga303 on 2011-06-02
**[COLOR=Red][SOLVED][/COLOR]**[SIZE=2]**[COLOR=Red] This issue has been solved![/COLOR]**[U][B]

The Issue[/B][/U][/SIZE]
Whenever I attempt to connect to Ubuntu 11.04 from Windows 7  Professional 64-bit via TightVNC Viewer, I can only see the Ubuntu wallpaper  from the Windows 7 machine (or the exact state of the Ubuntu desktop at  the moment a VNC connection is made, though any visible panels/windows  are non-interactive).  The display never refreshes.  Manual refreshing  does not cause the display to update.  Moving the mouse pointer around  on the Windows 7 (TightVNC Viewer) window causes the mouse pointer to  move on the Ubuntu machine.  In fact, if I watch the Ubuntu machine's  monitor, I can fully interact with the Ubuntu desktop from the Windows 7  keyboard and mouse!  But nothing I do causes the Windows 7 (TightVNC  Viewer) display to update.

[SIZE=2]_**The Configuration**_[/SIZE]
**Ubuntu 11.04 on a Dell XPS M1730 Laptop:**
I just installed a brand new download of Ubuntu 11.04 onto my Dell XPS  M1730 laptop.  Apart from updating it with the Update Manager, I have  installed only 3 additional downloads (so this installation is pretty  much virgin apart from these):

[LIST]
[*]Sun Java 6 JDK (proprietary)
[*]Eclipse
[*]Android SDK
[/LIST]
 I don't know if this is relevant, but I log Ubuntu only into the Ubuntu  Classic Gnome desktop shell [because I can't stand Unity in its current  iteration].  I also have both of the top and bottom panels set to  Autohide.

On this Dell/Ubuntu laptop, I have enabled Remote Desktop with the  following settings (from System -> Preferences -> Remote Desktop):

[LIST=1]
[*][x] Allow other users to view your desktop
[*][x] Allow other users to control your desktop
[*][x] Require user to enter this password:  xxxxxxx
[*][x] Configure network automatically to accept connections
[*][x] Only display an icon when there is someone connected
[/LIST]
 **Windows 7 Professional 64-bit on an Alienware Aurora R2**:
While this is not a fresh install of Windows 7, I have downloaded and  installed (only the Viewer component) of the latest version of TightVNC  from [http://www.tightvnc.com/](http://www.tightvnc.com/).  I have attempted too many configuration  variations to cite them all here and none have succeeded in showing me  any more than a non-interactive version of the Ubuntu desktop.

[SIZE=2]_**What I've Tried So Far**_[/SIZE]
Google provides hits for only a different version of Ubuntu, a different version of Windows,  recommendations to or away from TightVNC, and a slew of posted questions  without solutions.  I'm sorry if this exact issue has already been  solved on the Ubuntu Forums -- many posts seem related but are actually  outdated or otherwise irrelevant to my specific configuration -- and I  would very much appreciate any relevant links if they exist.

Many posts recommend changing "System -> Preferences -> Appearance -> Visual Effects" to None, but there is no "Visual Effects" tab, button, panel, or other UI element on the Appearance Preferences dialog in Ubuntu 11.04 (running the Ubuntu Classic Gnome desktop shell).
 
I have experimented with very many configurations of the Ubuntu Remote  Desktop Preferences and the TightVNC Viewer settings.  I have even  attempted to run TightVNC Viewer "As Administrator", to no avail.  Having  exhausted all that I can think of, I am now asking for your help.

[SIZE=2]_**The Solution**_[/SIZE]
A little further digging found a workable solution:
1. Run gconf-editor
2. Navigate to /desktop/gnome/remote_access
3. Set:  [x] disable_xdamage

---

### Post by pj42uk on 2011-06-06
Thank you for this post. It worked for me also.

---

### Post by toorudez on 2011-06-09
Has anyone else besides me had this solution not work? I've tried every setting on the Ubuntu machine, as well as on the Windows machine, to no avail. I've tried logging into Ubuntu with just the classic desktop, and it still doesn't work. I'm at the point where I'll be down grading to 10.10. If I can't remote into my server in the basement, then it's completely useless to me.

---

### Post by sahwan on 2011-06-21
works...!!

thanks allote

---

### Post by VcDeveloper on 2011-06-26
Thanks! it worked for me also! How can you up the performance if possible?

---

### Post by t3ddyg on 2011-07-30
And you just saved me a ton of anger management classes.  THANKS!

---

### Post by echristian@dmainc.com on 2011-08-08
Thank you!  Worked perfectly.

---

### Post by pwm5js on 2012-03-19
> **toorudez said:**
> Has anyone else besides me had this solution not work? I've tried every setting on the Ubuntu machine, as well as on the Windows machine, to no avail. I've tried logging into Ubuntu with just the classic desktop, and it still doesn't work. I'm at the point where I'll be down grading to 10.10. If I can't remote into my server in the basement, then it's completely useless to me.

This is also not working for me. I can see my Ubuntu wallpaper and any files on the desktop but cannot see the top or bottom menu bars. I can navigate around a bit by right clicking and making a new folder, from which i can find directories. But I can't see see the tool bar on the top for minimizing, closing, or expanding the window. I can't even open a terminal.

Any help would be much appreciated!!

Thanks. Sorry, I'm a bit of a noob.

---

### Post by pwm5js on 2012-03-19
This is probably irrelevant, but remote desktop connecting in the other direction (i.e. from my Ubuntu 11.10 box to my Windows 7 box) is working flawlessly using Remmina. What a better program thank Vinagre.

pete

---

