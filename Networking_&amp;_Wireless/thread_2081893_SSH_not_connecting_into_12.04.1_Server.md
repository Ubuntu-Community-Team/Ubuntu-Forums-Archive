---
title: "SSH not connecting into 12.04.1 Server"
date: 2012-11-08
forum: Networking &amp; Wireless
---

### Post by Drone86 on 2012-11-08
Puzzling problem - I can SSH into my fresh 12.04.1LTS Server from one computer but not another.

What I seek: What to check for, that I haven't already.

Background -

I set up a server a few days ago and followed an online guide to secure it [(here)]("http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics"). I could still SSH into it afterwards using my laptop after a reboot, so it was fine at that point.

Start of problem: Today it hiccuped - corrupted a partition, and wouldn't mount the swap partition. I took the busted partition out of fstab for fixing later, so it'd boot - I also disabled the boot splash and plymouth while I was at it. Seems unrelated, think the hdd might be on it's way out. This was all done from my laptop.

On the last reboot, it wouldn't allow me to connect from the laptop I'd been using through (Win7.64/Putty - "Server unexpectedly closed connection"). Funny thing is, if I SSH into the OpenSUSE box I have on the same switch, then SSH from that into the new server, it works just fine. They're all on the same network - laptop via WiFi, both servers via switch, into the same router serving the WiFi. 

[LIST]
[*]I disabled both Denyhosts and Fail2Ban even after finding nothing in their logs (I didn't install PSAD).
[*]I've checked dmesg after each attempt at connecting from the laptop - nothing. 
[*]Firewall not running.
[*]I changed to a non-standard SSH port at install time, so that hasn't changed.
[*]I have "UseDNS no" in sshd_config.
[*]All changes in the [guide]("http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics") were implemented before successive reboots and reconnects.
[/LIST]    

So - what do I check next? Cheers.

---

### Post by 2F4U on 2012-11-08
Can you ping the server from laptop?

---

### Post by Drone86 on 2012-11-08
It wasn't before - I had net.ipv4.icmp_echo_ignore_all = 1 in sysctl.conf. Changing it back got ping back, but still no change in SSH behaviour.

---

### Post by Drone86 on 2012-11-09
Ah, think we can shelve this one.

I just rebooted the router (Thomson TG585V8) and it now works as normal.
Beats the heck out of me, that router hasn't had config changes in the year preceding the last 30mins.

*Love* computers...

---

