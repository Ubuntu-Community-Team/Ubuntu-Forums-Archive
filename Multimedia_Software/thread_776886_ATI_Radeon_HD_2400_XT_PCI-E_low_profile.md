---
title: "ATI Radeon HD 2400 XT PCI-E low profile"
date: 2008-05-01
forum: Multimedia Software
---

### Post by daehenoc on 2008-05-01
Hi all,

I've got a new work computer, a Dell Optiplex 755 with a low-profile PCI-E ATI Radeon HD 2400 XT add-on video card, which disables the on-board video.

It's got our corporate SOE on it, Windows XP and of course the dual-displays work in XP with the ATI drivers.

When I boot it up off the Ubuntu live CD, with both monitors attached to the special dual-DVI break-out cable, I get a cloned screen, and going to System -> Preference -> Screen Resolution, I couldn't get the Screen Resolution program to detect the two displays - when I uncheck the 'Clone Screens' button, one display is correctly detected (Dell 24") but the Acer 24" does not show up.

Any tips on getting the second monitor correctly detected and display on it?

---

### Post by Teloid on 2008-05-01
You may use ATI management tools, or manualy add second monitor to your /etc/X11/xorg.conf - you must have separate sections "Device", "Monitor", "Screen" for each monitor.
When you finish editing config, restart your X server. If you use Gnome (default Ubuntu) press Ctrl+Alt+Fn where n is integer from 1 to 6. Then login into console, and type
sudo /etc/init.d/gdm restart

---

### Post by daehenoc on 2008-05-01
OK, where do I get the ATI management tools?  Are they pre-installed?  And what exactly do I have to put in the xorg.conf file?

I have also found the linux drivers off the ATI web site: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

And the link to the unofficial wiki for the ATI driver on Linux: [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

On this wiki is the page on how to install this ATI driver on Hardy: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

So I think I'll give the instructions on that last page a go tomorrow (almost time to go home here).

---

### Post by Teloid on 2008-05-01
ATI tools goes with ATI driver, at Win they named Catalyst(maybe I'm wrong, cause I'm nvidia owner ;) ). For some reasons AMD very slow  develop their graphical drivers and utils for non-win systems, and xorg.conf way is a "true" way. But, first, try to install drivers by Envy util. Run
```
sudo apt-get install envy
```
and then run it (maybe with sudo). Envy will ask some quiestions, and then download(if you connected to internet) and install driver that you need.
Then, if no ATI tools were installed, you need to change your /etc/X11/xorg.conf. If you use Gnome, and prefer gedit as window-based text editor type at terminal:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo -b gedit /etc/X11/xorg.conf

```
Then try to simply duplicate sections "Device" "Monitor" and "Screnn", but at one "Device" section set
```
Screen 0
```
at another set
```
Screen 1
```
And all "Identifier" fields make different.
Then scroll up and at section "ServerLayout" and type
```

Screen      0  "SCREEN_0" 0 0
Screen      1  "SCREEN_1" RightOf "SCREEN_0"

```
where SCREEN_0 means Identifier from "Screen" section from one monitor and SCREEN_1 from another. Then save file and restart X session, as I described. That config will make two separate screens with same resolution.
Maybe I'm wrong somewere at details, but concept is right =) After successful X restart you can change resolution from native gnome GUI tools.
If something goes wrong just replace xorg.conf by backup.

---

