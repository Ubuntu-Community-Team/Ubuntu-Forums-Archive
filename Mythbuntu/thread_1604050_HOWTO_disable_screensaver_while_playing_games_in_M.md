---
title: "HOWTO disable screensaver while playing games in Mythgame"
date: 2010-10-23
forum: Mythbuntu
---

### Post by thatguruguy on 2010-10-23
I use a generic XBox gamepad to play games in Mythgame.  In my experience, neither pcsx-r (which I use to play PlayStation games) nor dolphin-emu (which I use for Gamecube and Wii games) would automagically turn off the screensaver when playing games, which could lead to the screen going blank at really inconvenient times.  Although the screen would come right back on if I pressed a key on the keyboard, this was fairly annoying. However, I didn't want to turn off the screensaver forever; I just didn't want it to operate while I was playing games.  There's probably a setting somewhere in mythbuntu that will fix the issue, but I haven't seen it.  If you are having the same issue, this is how I fixed it.

The first thing you'll need to do is identify your desktop.  To do so, open a terminal on an otherwise blank desktop and enter the following code:
```
xwininfo
```You will receive the following message:
```
Please select the window about which you would like information by clicking the mouse in that window.

```Simply click on an empty space on your desktop.  A bunch of text should appear in your terminal.  You want the first line, which will say something like this:
```
xwininfo: Window id: 0x2200003 "Desktop"
```Make a note of that number, we're going to use it in a second. We'll set up both pcsx-r and dolphin-emu as follows:

**THE SCRIPT FOR PCSX-R**

Using your terminal, open a text editor with super user privileges and create a file called lauchpcsx (or whatever you'd like to name it) in your /usr/local/bin directory.  Since I have gedit installed on my mythbuntu box, I'd type:
```
sudo gedit /usr/local/bin/launchpcsx
```In that file, type the following:
```
#!/bin/sh
xdg-screensaver suspend 0x2200003
pcsx -nogui -cdfile "$1"
xdg-screensaver resume 0x2200003

```Needless to say, substitute whatever your particular Window id number is for where I put "0x2200003". Save that file. 

Now, we need to do the same thing for dolphin-emu:

**THE SCRIPT FOR DOLPHIN-EMU**

This time we'll make a file called **/usr/local/bin/launchdolphin**:
```
 #!/bin/sh
xdg-screensaver suspend 0x2200003
dolphin-emu -e "$1" -b
xdg-screensaver resume 0x2200003

```Again, make sure you use the correct Window id.

When finished, make sure that both scripts are marked as executable.  You can do that by chmodding the files, or by running thunar with super user privileges (sudo thunar) and clicking the checkbox for "Allow this file to be run as a program" in the properties dialog.

Finally, we need to make changes to the way the emulators are launched in Mythgame.

**Mythgame settings:**

In your pcsx setup in mythgame, for "Command" should read as follows:
Command: **launchpcsx %s**

Your dolphin-emu setup should show the following:
Command: [B]launchdolphin %s
[/B]
That's what worked for me.  Good luck.

---

### Post by glennric on 2010-11-25
This is now built into dolphin-emu.

---

### Post by thatguruguy on 2010-11-26
When will that make it into the linux version?  I'm using the latest build available from your ppa (2.0+svn6441-0ubuntu1~maverick, uploaded on 2010-11-19), and I still have to use the workaround mentioned here to avoid the screensaver coming on.  Or this there a hidden setting for this somewhere within dolphin-emu?

---

