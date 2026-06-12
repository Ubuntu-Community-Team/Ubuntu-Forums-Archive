---
title: "Firestarter broke my Internet connection"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-11-19
Recently, I was "reminded" that I accidentally left my vino-server (VNC) listening on port 5900 without a password, and someone on the LAN I connect to sniffed it.  Being alert, I disconnected them within seconds, disabled VNC all together, then proceeded to install Firestarter in an attempt to monitor other potential attacks like this so I could log the source address of the perp.

In doing so, I seem to have broke my Internet connection.

From the moment I login, nothing works online.  I can't launch Skype, Pidgin, evolution, Firefox just sits there and times out.  But if I open Firestarter, and hit the "Stop Firewall" button, everything runs smoothly.  The entire time, even if I wait for several minutes, Firestarter never shows any Events as one might expect if there was traffic being blocked.

Now, there is an unknown variable about this:  The network I'm connecting to.

I purchase my Internet from a local ISP (and I mean LOCAL, as in, they probably only provide service for about 1000 or 2000 people out here, getting their feed entirely through a satalite dish; we are literally in the middle of nowhere... I'm a contractor... enough said).  Anyway, I have not a clue how the topology of their infrastructure is, what security measures they have in place, what sort of non-standard protocols or practices they have up and running on their networks.  How anything the ISP might be doing could affect the utter lack of "Events" in firestarter from showing up, or why nothing Internet-wise works when the firewall is up and running, I have no clue.

I'd be happy if anyone knows how I could uninstall Firestarter and be left with what I had before it was installed.  My only fear about not doing that immediately is the control panel/program being removed, but the changes to the iptables being left behind so when I reboot, the firewall is back up and I have no easy way to "stop" it like I do with the button in Firestarter.

Alternatively, I'm open for theories about what might be causing the problem.  I'm just so used to seeing events and a big red stop-sign show up whenever traffic is blocked, and yet firestarter is acting like not a thing is being blocked at all....

---

### Post by jessiebrownjr on 2009-11-19
Im not 100% sure but this might give you something to look into.

Firewalls out of the box block everything I think but like, port 80 etc.. You have to set up what you want allowed. I downloaded GUFW and out of the box, all my stuff is working.. You might consider finding documentation for what you downloaded, and find out how to allow certain programs/ports for certain things..

---

### Post by diablo75 on 2009-11-20
Well I'm happy to report that simply doing a "Complete Removal" of firestarter via Synaptic (aka, a purge) got firestarter off and the Internet is working after a restart.  Problem solved.

---

