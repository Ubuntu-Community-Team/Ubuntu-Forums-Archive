---
title: "[Application] Atheros (Ath5k) Control Panel and Tray Icon for Ubuntu. Acer AOA150/ZG5"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by Repgahroll on 2011-08-08
Hello there.
I've installed Ubuntu 11.04 on an Acer ZG5 and the Wifi interface doesn't work well by default. I've asked here but no one replied, after some research I discovered that there are working commands to control and monitor the interface, so i made a program that does basic things and monitor the status.

It's a single file. It uses bad programming techniques and has a lot of ugly things, but it's working perfectly and doesn't have memory leaks, etc. It was made in a hurry.

It has some basic dependencies but any Ubuntu setup should have them all.

I've attached the file, to make it work just download it to your home folder (or any other, but home is recommended as it's a dotfile (hidden)).

Then you just need run on terminal:
```
chmod +x .athtray.py
./.athtray.py
```

And follow the instructions:

[[IMG]http://img11.imageshack.us/img11/420/77191934.png[/IMG]](http://imageshack.us/photo/my-images/11/77191934.png/)
Uploaded with [ImageShack.us](http://imageshack.us)

At the first launch, probably the default interface address is not the right one, so you'll get an blue "refresh" icon. Click it to open the main dialog (as shown above)

Clicking "Options\Configuration" button will open the following dialog:
[[IMG]http://img10.imageshack.us/img10/2022/56575067.png[/IMG]](http://imageshack.us/photo/my-images/10/56575067.png/)
Uploaded with [ImageShack.us](http://imageshack.us)

If you want the program to configure sudoers for you, just click the button "Configure Sudoers (Dangerous)", a xterm window will open asking for your password: (tested with Ubuntu 11.04)
[[IMG]http://img32.imageshack.us/img32/1777/97315059.png[/IMG]](http://imageshack.us/photo/my-images/32/97315059.png/)
Uploaded with [ImageShack.us](http://imageshack.us)

Type it and hit enter.

You can also configure the sudoers manually, you can find instructions on the "Help \ Exit Program" button (main dialog). Basically you just need to add the line
```
<your username> ALL=(ALL) NOPASSWD: /sbin/iwconfig, /sbin/modprobe ath5k, /sbin/modprobe -r ath5k
```
and run (in the same directory .athtray.py is)
```
echo "1" > .ath5kconfig
```

After configuring the sudoers the program will not display that text and button again.

If you want the program to start automatically, just click the "Write Auto Startup File (Ubuntu)" button (recommended) if you're not using Ubuntu and Gnome you may find another way to make it launch on startup, if you're using other distro and Gnome, it may work as far as i know.

You can now click the "Configure & Exit" button and everything should be working, just logout-login and the icon should be there.

PS: It doesn't work on Unity, you'll have to use the classic mode (Gnome).
The problem is that the tray icon doesn't appear under Unity, don't know why.

The icons are borrowed from system defaults, later i'll chose better ones, at the moment they are:

The "network or wired network" icon, that indicates the interface is turned on
The "delete or exclude" icon, that indicates the interface is off
The same icon blinks when the program detects an error.
The "reload or refresh" icon, that indicates when the interface was not found or the program is loading or frozen.

On the default theme, the on icon is:
[[IMG]http://img26.imageshack.us/img26/4049/iconon.png[/IMG]](http://imageshack.us/photo/my-images/26/iconon.png/)
Uploaded with [ImageShack.us](http://imageshack.us)

The off icon is:
[[IMG]http://img714.imageshack.us/img714/5762/iconoff.png[/IMG]](http://imageshack.us/photo/my-images/714/iconoff.png/)
Uploaded with [ImageShack.us](http://imageshack.us)

And the "refresh" one is that blue icon on the 1st image.


Here is the full help with further instructions:
(couldn't put it inside code tags because there's no automatic line break
=========================================================================

Help:

This is a simple application to monitor and control yout Atheros Wifi Card using the Ath5k module.

First steps:
Configure the program using the Options/Configuration button. Choose your wifi interface from the dropdown or type it if it's not listed.
 > The 1st button is the monitoring interval, for example, every 5 seconds the program will read the interface status and update the icon and the control panel.
 > The 2nd button is for optional initialization actions. The action selected is executed when the program loads.
 > The 3rd button saves the settings and exit the program, you need to relaunch it manually after clicking this button.

IMPORTANT!: If it's the first time you launched the program, it's going to show you one extra button that configures the sudoers file automatically in order to enable the program to run the commands properly. If you click it, a xterm window appears asking for your password. After entering it, you should click on the 3rd button and relanch the program.

Troubleshooting:
You shouldn't use the network manager or the physical switch, if you use them the interface may stop working, if that happens you should click "Reset Module", trigger the physical switch and click "Reset Module" again. Wait some seconds (depending on the refresh frequency and it should be working again, if not, repeat the procedure.

Manual Sudoers Configuration:
Open the sudoers file on a text editor, or use the visudo program (recommended), for example on terminal enter:

sudo gedit /etc/sudoers

 save a backup and then add the line: (at the end of the file)

<your username> ALL=(ALL) NOPASSWD: /sbin/iwconfig, /sbin/modprobe ath5k, /sbin/modprobe -r ath5k

 save and close the file. Now enter the folder where this program is located, e.g:

cd apps

and run this command:

echo "1" > .ath5kconfig

this command will remove the button to edit the sudoers file automatically.

=========================================================================



Thank you.

EDIT:
For some reason it's not possible to upload a file without extention (nonsense) so i've renamed it to .athtray.py and updated the tutorial

---

### Post by cejack on 2011-09-02
I loaded 11.04 on ZG5 AOA and didn't have any problems with wireless 802.XX connections.  

3G is problematic but that is kind of another issue entirely in my opinion.  

Just wanted to mention my experience with my ZG5 on 11.04 is different.  Worked out of the box and updated fine wirelessly for me.

---

