---
title: "No desktop on every other bootup"
date: 2009-02-17
forum: Mythbuntu
---

### Post by Caysho on 2009-02-17
Every other time I boot up myhbuntu, I get no desktop.
When it happens, I cannot ssh into the machine either.

The load sequence itself appears to be ok (splash screen etc).
Updates are current, using nVidia closed source driver.

.xsession_errors contains:
```

/etc/gdm/Xsession: Beginning session setup...

2009-02-17 18:26:22.581 Using runtime prefix = /usr
2009-02-17 18:26:22.582 Empty LocalHostName.
2009-02-17 18:26:22.582 Using localhost value of pvr
2009-02-17 18:26:22.665 New DB connection, total: 1
2009-02-17 18:26:22.668 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:26:22.668 Closing DB connection named 'DBManager0'
2009-02-17 18:26:22.669 Connected to database 'mythconverg' at host: localhost
/usr/bin/startxfce4: X server already running on display :0
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-TChEoz6317/agent.6317
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (update-notifier:6597): WARNING **: already running?

2009-02-17 18:26:29.312 Using runtime prefix = /usr

** (nm-applet:6610): WARNING **: No connections defined
2009-02-17 18:26:29.845 XScreenSaver support enabled
2009-02-17 18:26:29.846 DPMS is active.
2009-02-17 18:26:29.846 Empty LocalHostName.
2009-02-17 18:26:29.846 Using localhost value of pvr
2009-02-17 18:26:29.850 New DB connection, total: 1
2009-02-17 18:26:29.854 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:26:29.854 Could not open settings file /home/mythtvuser/.mythtv/config.xml for writing
2009-02-17 18:26:29.854 Closing DB connection named 'DBManager0'
2009-02-17 18:26:29.855 Primary screen 0.
2009-02-17 18:26:29.855 Connected to database 'mythconverg' at host: localhost
2009-02-17 18:26:29.856 Using screen 0, 1920x1080 at 0,0
/usr/lib/thunar/thunar-vfs-pixbuf-thumbnailer-1: Unrecognized image file format.

```

[renaming ~/.config/xfce4-session/xfce4-session]("http://ubuntuforums.org/showthread.php?t=1016346") as described in that thread did not fix the problem.

My guess is that there are session locks not being cleared.  Anyone have any ideas ?

---

### Post by Caysho on 2009-02-20
Anyone ?

I've since done a complete reinstall, rebooting between configuration steps and the problem has not occurred yet.

---

### Post by Caysho on 2009-02-20
I encountered the problem again after installing the nvidia drivers (177 as recommended by the Restricted Drivers Manager - I have an 8400GS card).
I went to reboot and the screen went blank.
top shows Xorg at 100% (or 99%) CPU.
Eventually I simply hit the reset button, but now that means the ssh and X locks are still in place and so these servers don't run again after bootup.

Unable to switch to console - how is a repair done in this situation ?

---

### Post by scary_jeff on 2009-02-20
Why are you unable to switch to console? This seems strange if its an X problem. You could always press whatever key it is to bring up the GRUB menu at bootup, and select console only. Then when you try and start anything that has a lock, it will tell you where the lock file is, and you can delete it.
I had a lot of X issues initially, and was always able to switch to console, so this is definitely odd.

---

### Post by Caysho on 2009-02-20
I wish I knew :)

I know the screen is receiving a signal, but otherwise it is completely unresponsive to the keyboard.

I then discovered the ubuntu/grub recovery mode, so I went and had it create a fresh xorg and it booted ok after that.  I figure it's something to do with the nvidia driver.

After some hunting around, I found [bug 262043]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/262043"), stating that version 177 is not compatible with the Intrepid kernel.  The whole process has been a bit strange because I actually ran with this configuration for two days before the no desktop wierdness started.

I have since been able to use the envyng tool to get the driver working (with the supposedly incompatible version 177 driver), both pre and post update.

Maybe I have a rare edge case happening.

Edit: Just did a reboot, and the same problem came up.  I will try the new nvidia drivers from their website.

---

### Post by Caysho on 2009-02-21
Did something different - I used the envyng tool to install the nvidia 180 driver.  This time, the mythbuntu splash completed as usual but the display dropped back to the text screen with the following (typed by hand as it still locks up):

```

* Starting System Tools Backends system-tools-backends       [ OK ]
* Loading LIRC modules                                       [ OK ]
* Starting remote control daemon(s) : LIRC                   [ OK ]
* Starting deferred execution scheduler atd                  [ OK ]
* Starting periodic command scheduler crond                  [ OK ]
* Checking battery state...                                  [ OK ]

```

and stops there, cursor blinking on the left.  Again, a hard reset is needed.

---

### Post by Caysho on 2009-03-01
Ended up [reporting a bug]("https://bugs.launchpad.net/bugs/333048").

---

### Post by Caysho on 2009-03-02
Found this in /var/log/syslog

```

NVRM: loding NVIDIA UNIX x86 Kernel Module 180.11 Wed Nov 26 10:53:26 PST 2008
NVRM: request_mem_region failed for 16M @ 0xfd000000. This can
NVRM: occur when a driver such as rivatv is loaded and claims
NVRM: ownership of the device's registers.
nvidia: probe of 0000:01:00.0 failed with error -1

```

After some searching around, I found that this is often an issue with BIOS's not being truthful, and also with 4GB ram installed.  However, my understanding is that linux ignores the BIOS by default.

I'm using an Asus P5QL-E with current BIOS.  Looks like I can force the kernel to use the BIOS for the PCI information instead of probing devices itself.

Checked the motherboard manual, and it states that my PCI-E slot and the first PCI slot share an IRQ.  I have one of the tuners in that slot, so "Just in case", I moved it to the end (three PCI slots).

I did a complete re install using mythbuntu 8.10, had it grab all the updates as of yesterday/today.

I appended pci=bios to the end of the grub kernel line, and that error no longer occurs.  Now it gets to the desktop, I can move the mouse for a few seconds, and one of two things occurs:

[LIST=1]
[*]the mythtv frontend starts, or
[*]I get the lockup.
[/LIST]

If the front starts, I can use it.  Then I found that if I exit the front end, and start it again, I get the hang.

---

### Post by Caysho on 2009-05-18
Looks like the hardware was dying.
I found an MTRR message in the syslog, though I understand nvidia uses PAT now.
Then I found some google results about C1E causing problems, and came across [this "interesting" post]("http://vip.asus.com/forum/view.aspx?id=20080713214821640&board_id=1&model=P5Q&page=1&SLanguage=en-us") about the Asus P5Q series of motherboards.

I now have a Gigabye GA-EP45-UD3L motherboard and PALIT 9400GT graphics card, and mythbuntu installs without problems with the nvidia driver, no hangs.

---

