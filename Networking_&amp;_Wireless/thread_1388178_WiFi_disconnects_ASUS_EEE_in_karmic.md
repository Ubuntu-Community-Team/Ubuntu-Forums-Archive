---
title: "WiFi disconnects ASUS EEE in karmic"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by Rallg on 2010-01-22
I have a stable, well-updated karmic (standard distro, not remix) on my ASUS EEPC1005HA. Had it since karmic was released, and before that had jaunty. Until recently, no problem with WiFi.

Lately, the WiFi has been subject to frequent, random disconnects. Once disconnected, it is often hard to reconnect. Others using the same WiFi (Windows or Mac notebooks) have not had the same problem.

This is on WiFi that does not require a password.

Today, after the random disconnect, I was not able to reconnect at all, even after reboot and waiting. The WiFi signal is properly seen. But it won't connect.

On the same computer, in the same location, if I boot Windows XP it does connect. I've tried it back and forth: No connect in karmic, connect in XP, no connect in karmic.

Has there been something in recent updates that might cause this? I haven't changed the BIOS since its last update back in early December, so it's not a BIOS change.

---

### Post by pdc on 2010-01-22
on this page, is a diagnostic script that runs on linux and aims to diagnose problems; and suggest solutions;

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English)

can I suggest you download it, and run it, and see if it helps you to diagnose?

---

### Post by Rallg on 2010-01-23
I'll give it a try. Of course, before running any shell scripts, I will read through them!

Further information: After asking others, it seems that Mac laptop users (but not Windows users) have also had similar problems in the same area. Meanwhile, one or two Windows users have complained that their laptops are  infected with viruses (hey do not know enough to describe it further).

I wonder if the virus-infected laptops are doing something, such as repeated port scans, that chokes the WiFi on Mac or Ubuntu, but does not choke securely-updated Windows systems? I use UFW with Ubuntu.

Right now I'm up early in the morning, with nobody else around, and there is no problem on Ubuntu or Windows.

---

### Post by framplinux on 2010-01-24
> **Rallg said:**
> I'll give it a try. Of course, before running any shell scripts, I will read through them!
Hm ... do you want to read > 2000 lines of bash script? Just read the faq and/or google for collectNWdata - it was used successfully by a lot of people already and helped them to fix their problem on their own. It also provides a lot of network config details for people so they can help to solve the network problems.

---

### Post by Rallg on 2010-02-10
I moved this to "solved," as I haven't seen it happen lately. No doubt it was a transient problem.

UPDATE: Others have seen the problem, but reported it in different ways. Often, it is accompanied by an odd behavior in the notification area: The WiFi icon and the sound icon are mingled. Since the problem is being addressed in a different way, I'll leave this thread as "solved."

---

