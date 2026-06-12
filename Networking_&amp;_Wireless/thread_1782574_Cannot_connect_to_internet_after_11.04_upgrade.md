---
title: "Cannot connect to internet after 11.04 upgrade"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by Rich.d.berry on 2011-06-14
I've just upgraded to 11.04 on my new desktop and I'm using a wired ethernet connection. My web browsers have stopped working (Chromium and Firefox) but my networking is working because I can still run Package manager to install new packages. The system monitor also shows network activity.

There was no proxy server set up before the upgrade. Does 11.04 require a proxy server setup? Checked and set to auto detect but made no difference.

I'm currently connecting off my old laptop running Windows XP on a wired connection through the same modem.

Any ideas?

---

### Post by eltonw on 2011-06-14
> **Rich.d.berry said:**
> I've just upgraded to 11.04 on my new desktop and I'm using a wired ethernet connection. My web browsers have stopped working (Chromium and Firefox) but my networking is working because I can still run Package manager to install new packages. The system monitor also shows network activity.

There was no proxy server set up before the upgrade. Does 11.04 require a proxy server setup? Checked and set to auto detect but made no difference.

I'm currently connecting off my old laptop running Windows XP on a wired connection through the same modem.

Any ideas?

Try installing skype, or another browser from the package manager, and use *that* as a test to see if you can connect.

At worst, you can use Synaptic or the Software Center to first un-install Firefox, and Chrome, **then** **re**install them. Of course, export [backup] your bookmarks from Firefox, Chrome first.

---

### Post by Rich.d.berry on 2011-06-15
That doesn't work I'm afraid. Neither Skype, nor Rhythmbox (cannot play internet radio channels) work.

Re-installed browsers and that hasn't worked either.

---

### Post by dandnsmith on 2011-06-15
strange that the Synaptic Package Manager still works - I usually notice my networking for browsers etc isn't working because the Synaptic is reported as failing.

Try System | Admin | Network Tools
and use the ping and netstat to see what that says (use [www.google.be](www.google.be) or 209.85.147.104) for the pings.

If that shows connectivity, then there's something else wrong - cannot immediately think what.

---

