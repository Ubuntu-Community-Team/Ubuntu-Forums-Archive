---
title: "Privoxy will start manually but not during init"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by methanol on 2010-02-24
Long-time linux user, new to Ubuntu (mainly a gentoo user).

I need to get tor and privoxy up and running for a less computer-capable user.  I installed Tor and Privoxy, configured them (apparently correctly) and they both appear to work just fine when I start them manually from their init scripts:

sudo /etc/init.d/tor start
sudo /etc/init.d/privoxy start

However, I cannot seem to get privoxy to start up properly when the machine boots.  Tor starts up and waits patiently, but privoxy is dying or getting killed for some reason I can't understand, and on Ubuntu, have no idea how to diagnose.  There's no privoxy process after booting, and the init.d script reports status: not running.  I have the startup scripts for both Tor and Privoxy linked to in all the relevant runlevels.  I played with the order thinking it might be a dependency thing.  Hell, I even put a line in rc.local to try and force it to go.  But no matter what I do, I can't seem to get the privoxy service to start for me any way but by manually typing 'sudo /etc/init.d/privoxy start' in a terminal, after logging in.

So I am looking for two kinds of help:

1.  Help me get privoxy to auto-start during init
2.  OR Help me figure out how to figure out how to get privoxy to auto-start during init.  On Gentoo, all of the init scripts are listed on the screen during init as they run, and you can even run through them interactively by pressing I during startup.  I have no idea how to do this on Ubuntu.  I modified the kernel line to remove the splash screen, but the information Ubuntu puts on the screen during init is quite haphazard.  How do I figure out what's going wrong with the privoxy init script? :confused:

---

### Post by methanol on 2010-02-25
... no one?

---

