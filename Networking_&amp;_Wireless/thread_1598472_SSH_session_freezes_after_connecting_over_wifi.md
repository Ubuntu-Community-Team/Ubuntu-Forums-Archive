---
title: "SSH session freezes after connecting over wifi"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by davidshere on 2010-10-16
I am connecting from my WinXP laptop to my Ubuntu Server desktop using PUTTY.  The laptop is using Wifi and the desktop is on a wire.  I have a D-Link DI-524 wireless router.  My session works fine for a while, and then freezes, sometimes after only a few seconds, and sometimes after many minutes.  The same thing happens when I use VMWare Server Console to connect from the laptop to the desktop's virtual machines.  Other connections between these machines under this setup (RDP, samba, SVN) do not experience problems.  I usually do not experience problems establishing the SSH and VMWare connections.

I have ended up using Windows Remote Desktop to connect to a Windows XP virtual machine on the desktop, and opening a PUTTY session on that machine.  That's a nice workaround, but it makes it so that I have to have that VM running in order to have a reliable SSH session to the box.

I also connect in the same setup (WinXP-Wifi/Ubuntu-wired with PUTTY) at work, and do not experience any problems there.

---

### Post by davidshere on 2010-10-29
super cow powers bump. :)

---

### Post by davidshere on 2010-11-05
New Super Mario Brothers Bump

---

### Post by davidshere on 2010-11-11
MarioKart for DS bump

---

### Post by davidshere on 2010-11-28
Shopping cart bump

---

### Post by tbridges42 on 2011-01-01
I have a similar issue with my setup, although my connections are reversed. My main PC is a Windows 7 box on a wire, and I'm trying to SSH into my Hardy box which is on wifi.

I can usually get 10-15 minutes of stable connection, but once it hangs on me, I have to manually reboot the Hardy box to connect again. Obviously this is less than ideal.

---

### Post by rogere84 on 2011-10-31
Just to confirm that this still happens in 11.10. It happens during SSH terminal sessions and SSH connections to server folders.

---

