---
title: "Not Filling TV Screen"
date: 2010-09-05
forum: Mythbuntu
---

### Post by Chromag on 2010-09-05
I am (very) new to MythTV and giving it a test run.  I installed Mythbuntu 10.04 on my box that has a GeForce 210 card and Hauppauge 1600.  I've got my 210 connected to my HDTV set via HDMI but it's not filling the screen.  It almost looks like an aspect ratio problem.  There is just black a few inches around the entire TV screen.   It's fullscreen when plugged into my monitor but not TV.  Any ideas?

Thanks.

---

### Post by kja999 on 2010-09-05
Hi,

So people can help, can you post your Xorg log.
This is /var/log/Xorg.0.log


Cheers

---

### Post by Chromag on 2010-09-06
> **kja999 said:**
> Hi,

So people can help, can you post your Xorg log.
This is /var/log/Xorg.0.log


Cheers
Sure thing - hope this helps.  The log file is pretty long so I posted it to pastebin rather than quoting the entire thing here.

[Xorg.0.log File]("http://pastebin.com/iv61iTbu")

Thanks!   I'm also having an issue where clicking on Live TV goes to the "Please wait" screen and shows a black screen with the program info then the MythTV frontend crashes.  But I'll probably start another thread on that later.

Thanks again.

---

### Post by JMcFly on 2010-09-06
Are you watching a 4:3 broadcast of a 16:9 show? Sounds like you might want to try changing your zoom.

Here's how you assign buttons on your remote:
> gedit ~/.lirc/mythtvAdd an entry for an unused button (MCE and Hauppuage remotes usually have Red, Blue, Yellow and Green buttons that are unused, use 'irw' in terminal and press the button to find out what it is called, ctrl-c to exit irw when you're done) corresponding to the key 'w' to cycle between all of the zoom modes.

Also I suggest you connect buttons to PgUp and PgDown as after a few weeks your recordings list can be really long, I use Green for down and Red for up so it is easy to remember.

After that:
> sudo /init.d/lirc restart to restart LIRC, start the frontend again and check to see if your settings worked.

Also, some TVs are a little odd about HDMI inputs from computers.  Check your TV's menu settings to see if one of the HDMI inputs can be set to a PC mode or anything like that.  Also try setting your video card to send the TV the native resolution of your panel.

---

### Post by LowSky on 2010-09-06
if it connected via hdmi go to nvidia-settings and adjust overscan compensation

---

### Post by itlarson on 2010-09-07
If the gui fits the screen, but high def pictures don't, this could very likely be a DPI issue.  Mythbuntu likes it's "dots per inch" to be at 100.  With the nvidia driver, you can force dpi to 100 by adding:

Option "UseEdidDpi" "FALSE"
Option "DPI" "100 x 100"
  
to the "Monitor" section of /etc/X11/xorg.conf.  For me this fixed a picture which was squashed vertically.  Note this only works with the nvidia driver.

---

### Post by Chromag on 2010-09-07
> **itlarson said:**
> If the gui fits the screen, but high def pictures don't, this could very likely be a DPI issue.  Mythbuntu likes it's "dots per inch" to be at 100.  With the nvidia driver, you can force dpi to 100 by adding:

Option "UseEdidDpi" "FALSE"
Option "DPI" "100 x 100"
  
to the "Monitor" section of /etc/X11/xorg.conf.  For me this fixed a picture which was squashed vertically.  Note this only works with the nvidia driver.
Nope - the gui doesn't fit either.  I'll check out zoom and overscan tonight when I get home and see if that works.  Thanks for the info.

---

