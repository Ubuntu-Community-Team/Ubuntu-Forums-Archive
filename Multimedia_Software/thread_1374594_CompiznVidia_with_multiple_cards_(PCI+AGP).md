---
title: "Compiz/nVidia with multiple cards (PCI+AGP)"
date: 2010-01-07
forum: Multimedia Software
---

### Post by HyperHacker on 2010-01-07
I have an MSI K8T Neo-V motherboard, and it doesn't seem to be able to run both a PCI and an AGP video card at the same time. nvidia-settings will only detect one card, depending which is enabled in the BIOS.

I have another machine that can do this, but Compiz doesn't play nicely with it. On the PCI card are two monitors using TwinView. The AGP card is a third monitor set up as a separate X screen.
On the third screen, there are no window borders, and Xfce4-terminal (and any popup menus, dialog boxes, etc spawned from it) display as a white box (but still wobble if I have Wobbly Windows on). Using the --indirect-rendering option does not fix this. Is there any other method that might make it work?

---

### Post by alphasoup on 2010-03-14
I have had similar problems with an older MSI 865PE Neo2 for a long time...
First I find setup for multihead on both Fedora and Ubuntu is very painful for this board with a combination of 2 cards either several radeons or nvidia/radeon
The solution worked out about a year ago in another post (Fedora) included the following:
1) If you have an AGP nvidia and a PCI radeon, you may need to set the PCI/AGP order for graphics in the bios or they may never work together -- imho.
If you have an AGP radeo and another PCI I have had best luck with AGP/PCI order -- go figure!
2) the main issue was that the second board was always difficult to bring-up and
impossible if the graphics order was wrong. Looking at the Xorg.*.log one may find that the PCI board for example comes up with the wrong memory size and fails (8MB! instead of 128MB).
3) solution is to bring both board up once in 1 combined configuration without Compiz first (in my case), then bring each one separately, e.g. for two different user multihead configs (with different mouse and keyboard each) if that is the goal.

Attached is a sample common config that worked for the above setup, after this config works once then for the length of the boot I find that I can bring up each board independently and reliably -- with some nasty graphical side effects on the PCI side -- loss of sync that does not repair when resetting the monitor! (I use a vnc server to restart the flaky head and it then stabilizes once X is up with gnome). However once brought up this way both heads are rock solid for as long as you do not logout from one of them... (need remote access to a VNC session to fix it for example). Each time you reboot you must bring the boards together once before using them independently etc.
4) Another issue is that the graphics board take a lot of the (high) main memory (for DMA??). I you have a 512MB board with both DVI and VGA outputs it will take 1G of high memory that is no longer available for apps :( -- so use 128MB or 256MB board if you needs near 4G of memory present.
-- in the attached xorg.conf sample [use for combined bring-up as in item 3)] the screens definitions are not important but everything else seems to be (the layout and the correct card definitions, edit to match your setup). Once both boards come up in this order, things should start working.

---

