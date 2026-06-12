---
title: "No wired network connection until I sudo dhclient"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by Shawn K on 2012-03-01
Had a new problem develop last night.  Suddenly, my computer no longer sees the wired connection to my network (I don't have wireless on this machine).  If I open a terminal and run dhclient, it comes up zeroes all around.  However, if I *sudo* dhclient, then it sees the network and everything works correctly until I restart the computer.  Once I restart, I have to re-sudo dhclient in a terminal to make it all work again (which is what I've had to do to even type this message).

The first thing I thought of was to check and see that Network Manager was still on startup (it is), but I have no idea what the settings *should* be to work correctly.

So now I'm at a point where I know *that* sudo dhclient makes the wired connection work, but I don't know enough to know *why* it works, and I don't know how to fix this problem permanently.  Can anyone give me some pointers?

For the record, I'm running 10.04 with all updates current at the time of this writing.  It seems like things started going wonky after my last update, which was Tuesday night.

---

### Post by Shawn K on 2012-03-01
I found the issue... I think.

I looked at /etc/network/interfaces and saw the following:

[i]auto lo
iface lo inet loopback[/i]

So I changed it to:

[i]auto eth0
iface eth0 inet dhcp[/i]

...based on a suggestion I read elsewhere.

I rebooted, and everything seems to be working normally.  (Knock on wood)

Still can't figure out why that would be set to loopback like that after an update.

What makes it worse is that I apparently changed the right thing and made it work, but I really have no idea *what* I did.

---

### Post by dandnsmith on 2012-03-02
> **Shawn K said:**
> ...Still can't figure out why that would be set to loopback like that after an update.
Your inference here is wrong.
It is the *loopback* interface *lo* which is set to loopback - as it should be, but the eth0 interface wasn't shown until you did the edit.
I think the interfaces file doesn't usually show the auto eth0 - mine only shows entries for lo, and to find the details I have to use the system network info from the desktop.

---

### Post by Iowan on 2012-03-02
Hopefully you *added* the **eth0** info - rather than *replace* the **lo** information. Older versions of Network Manager wouldn't touch interfaces defined in */etc/network/interfaces*, but more recent versions are a bit more aggressive. You might check settings in NM (Network Manager) to see if the interface is set to connect automatically on power-up.

---

### Post by praseodym on 2012-03-03
Add those two lines immediately!

Otherwise your components dont work properly concerning data transmission inside the system! Reboot after that

---

### Post by Shawn K on 2012-03-04
Actually, I replaced the first two lines with the second two lines.  Works like a charm now.  Been using for a couple days, did a number of restarts... seems back to normal.

Now that I think about it, this all started the first time I rebooted after my last kernel upgrade (to 2.6.32-39).  Was this a known issue or something?

---

