---
title: "Natty issues so far"
date: 2011-01-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dr_kabuto on 2011-01-05
Hi everyone,
just want to share my list of issues I've with natty so far:
- Kernel 2.6.37-11 segfaults at boot (can't reach gdm)
- Kernel 2.6.37-10 boots but results in a black screen in place instead of gdm;
(I can boot fine with 2.6.37-9)
- Applets in gnome-panel at login crashing (using classic desktop, unity is unusable for me at this point);
- Flash plugin crashing everytime in Chromium;
- Lots of add-on are disabled in Firefox (why don't keep a stable release instead a developing one?)
- Apache crash everytime try logging in password protected sites i'm developing locally.

---

### Post by jerrylamos on 2011-01-05
> **dr_kabuto said:**
> Hi everyone,
just want to share my list of issues I've with natty so far:
- Kernel 2.6.37-11 segfaults at boot (can't reach gdm)
- Kernel 2.6.37-10 boots but results in a black screen in place instead of gdm;
(I can boot fine with 2.6.37-9)
- Applets in gnome-panel at login crashing (using classic desktop, unity is unusable for me at this point);
- Flash plugin crashing everytime in Chromium;
.
What video graphics do you have?  Example this is:
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Unity isn't intended to run on this, but classic does with 2.6.37-11, however boot or restart crashes half the time.  Totally dead can't run ubunt-bug.

Now to get to this point after install I had to:
boot in recovery mode,
sudo service gdm start && gnome-panel &
At this point no panel, Alt-F2 and Ctrl-Alt-T did not work, so:
right mouse click to create launcher
launcher command: gnome-terminal
select gnome terminal:
gconftool-2 --shutdown
rm -rf ~.gconf/apps/panel
pkill gnome-panel
got me a panel, so 
logout
login selecting "classic"

Now it boots to a cursor and wallpaper, and I have to issue the 
gconftool etc. stuff every time.  I made it into an exec.
At this point running O.K. for an Alpha 1.

This is swiftfox running O.K.

Joys of an Alpha 1...half the time it crashes on boot so I power off/power on and try again.

Joys of dealing with early development "Unity" intended for "newbies" but saddled on the rest of us too.

Jerry

---

### Post by dr_kabuto on 2011-01-05
Hi Jerry, my graphic card:
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 0a)

Unity runs fine here, just is not mature yet (for me, clearly!) for daily use. At this point I'm running classic desktop now.
For the kernel issue: seems a problem with the kms intel driver, solved with the latest RC kernel.

---

### Post by zika on 2011-01-05
> **jerrylamos said:**
> 
sudo service gdm start && gnome-panel &
JerryI would be surprised if this would work...
I think You've invoked gnome-panel in tty and not in GUI...
May be that I'm wrong...

---

### Post by davideotape on 2011-01-05
Does anyone know if there's a bug for the applets crashing problem?

---

### Post by hugmenot on 2011-01-05
I can confirm the crashing applets in classic session and the crashing Apache.

About Firefox: the development version has to be tested early, and the testing ground is the development release.

---

### Post by Harry33 on 2011-01-05
> **davideotape said:**
> Does anyone know if there's a bug for the applets crashing problem?

Here are just a few of them. There are quite a lot of them in Launchpad.
Bug #674791
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/674791](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/674791)

Bug #683100
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/683100](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/683100)

---

