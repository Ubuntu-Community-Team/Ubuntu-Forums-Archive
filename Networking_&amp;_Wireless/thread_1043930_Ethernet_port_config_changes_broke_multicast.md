---
title: "Ethernet port config changes broke multicast?"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by acilate on 2009-01-19
I'm running ubuntu 8.10 server.  I have installed fuppes onto ubuntu, which worked wonderfully.

Yesterday, I placed a new ethernet card into the server, move the config to the new port (eth0 to eth1) and then noticed that the new card was having issue.  I then moved the config back to the original port, and everythings working fine... kinda

After this happened, I noticed that fuppes no longer communicated with my ps3/360.  I started doing some packet sniffing and realized fuppes isn't doing any sort of discovery/replying to the multicast address (or anything else for that matter) it uses for uPnP discovery.

Then I installed mediatomb and have noticed that mediatomb also is not sending/recieving anything on the multicast address.  However, mediatomb and fuppes see each other jsut fine

I've put explicit statements in ufw to allow port 1900, I've tried disabling ufw all together, I've verified that multicast is enabled on eth0.  I've completely re-installed fuppes.  Nothing makes any difference.

What could be broken that is preventing fuppes or media tomb from working?  I'm assuming this is a general system issue, and not application specific as mediatomb is also having the issue

---

### Post by acilate on 2009-01-21
Ah ha!

As I suspected, there was an issue with the ethernet port configurations.  The port I thought I had turned down had the same ip address as the one I was using, and it also had the "allmulti" tag.  By removing the allmulti tag, changing the ip address, and turning down the port (I was pretty sure I had it off before, but perhaps by setting the ip or taking off the allmulti tag it was enabled again?), I returned my multcast applications to full functionality.

---

