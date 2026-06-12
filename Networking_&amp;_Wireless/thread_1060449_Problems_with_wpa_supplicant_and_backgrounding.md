---
title: "Problems with wpa_supplicant and backgrounding"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by lridium on 2009-02-04
I'll start with the general overview and I'll post information as people request it.

The basic setup of the box (it's my DVR) is it's running a Broadcom 4318 (Air Force One) PCI card with ndiswrapper (this works better than b43, so that's what I'm sticking with) and wpa_supplicant for a WPA2 network.  The configuration is handled through whereami which manages switching between the wired connection (if present) or the wireless.  There is no network manager running in GDM (neither NetworkManager nor wicd are running)

The box worked great under Gutsy but I needed to upgrade due to the new TV tuner (not yet installed, so that's ruled out as a problem) so it's now running Intrepid and just about everything is great, except the wireless.  If I start the wireless without backgrounding or detaching any of the associated processes (start-stop-daemon, whereami or wpa_supplicant) the connection will work just fine.  If I detach or background any of these processes, the card will still associate and claims to be sending packets back and forth (counters go up on ifconfig) but I can't ping anything or send/receive any other traffic.  wpa_supplicant will also continuously associate, progress to connected, and then back to associated until the end of time.

I've tried letting wpa_supplicant run without backgrounding it and the rc.d entry that seems to be the cutoff is S30 which is the starting point for GDM and System-tools-backends.  Once GDM loads, I have no connectivity.

I'm going absolutely nuts on this as I'm so close to having this working again.  I'd appreciate any help that anyone can offer and again, I can paste any relevant information that is requested.

---

### Post by lridium on 2009-02-05
Just for some updates, I've tried having NetworkManager installed and running and that doesn't work either.  The best results I get are with NM uninstalled and the detached processes (associated, but no connection) or attached (connected and working great, but won't progress any further through startup until the process is killed).  No luck yet :/

---

### Post by lridium on 2009-02-05
Well, it's less than elegant but it works... I'll leave this unmarked as fixed for the time being, just in case anyone has a real reason for what's going on.

It appears to be a race condition to some resource that is being claimed or conflicted once these other processes start up.  However, what is working for me is to start wpa_supplicant and detach the process (&) and then sleep for 10 seconds.  If I try to background the process (wpa_supplicant -BW), it will fail, even with the sleep.  Beats me as far as what's going on, but it's an interesting study in pain.

---

