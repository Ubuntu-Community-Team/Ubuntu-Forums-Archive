---
title: "Setting up SSH Server: Newbie help"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by Brian96 on 2011-03-06
I have an LMDE box that I'm trying to use as a proxy server for my Ubuntu laptop when I travel.  I figure port forwarding with SSH is the way to go, but I'm running into problems.  Here is what I've done so far:

1. Configured my 2Wire router/firewall to forward port 22 to the host machine (I did this by adding SSH as an allowed application).  As far as I can tell this is set up correctly, as the firewall summary page shows access for port 22 on the host machine.

2. Tested SSH on the host machine with the command "ssh -v localhost".  This, too, appears to have worked fine.

3. On a somewhat unrelated note, I have previously configured and used samba to be able to sync files across my LAN using grsync.  I don't understand all the details of this, but I understand that SSH is playing some role here, too.  This works fine.

However, when I try to connect to the host machine from my Ubuntu laptop, I get a "connection timed out" error.  I have tried to connect with various commands: "ssh username@##.##.###.###", "ssh -D 8080 username@##.##.###.###", and "ssh -D 8080 username@##.##.###.###" (where "username" is the username that works for grsync and the #s are the static public IP address I got from whatismyip.com).  I've tried this both locally from within my LAN, but also from a public wifi connection.

I recognize there are a lot of points in this system at which the failure could be occurring, but am I missing something obvious?

Also, I know there are additional configurations I may need to do to enhance security (keys vs. password, nonstandard port, etc.), but I'd like to see it work with the defaults before I get into all of that.

If there is a better way to get to the goal of having a secure connection to my home internet connection when I travel, then I am also open to that.

Thanks in advance!

---

### Post by mimor on 2011-03-06
From within your LAN network try this:
ping [servername] -> getting a reply?
ssh -v [username]@[servername]

What's the output of these 2 commands?

---

### Post by Brian96 on 2011-03-06
> **mimor said:**
> From within your LAN network try this:
ping [servername] -> getting a reply?
ssh -v [username]@[servername]

What's the output of these 2 commands?

Thanks for jumping into the fray.

If I ping or ssh using the local LAN address everything is peachy.  But when I try to ssh using the public IP address (which I guess is also the IP address of my router) then I get stuck ("connection timed out" message). I can also ping the public IP address.

I have the router configured to allow TCP traffic on the desired port, and the port forwarding tool at yougetsignal.com shows that port as open (which I would think means that it is properly forwarded).

---

### Post by Brian96 on 2011-03-06
The howto I used had recommended changes to the sshd_config file on the host.  Should there also be changes to the ssh_config on the client?  If so, what would they be?

---

### Post by kevdog on 2011-03-06
To answer the question above -- it would just depend.  The sshd_config file always should be altered (although it will run out of the box), the ssh_config file I rarely alter.

---

### Post by Brian96 on 2011-03-09
Not totally sure what finally clicked, but it is working now.

---

### Post by mimor on 2011-03-10
Mark your thread as solved ;)

---

