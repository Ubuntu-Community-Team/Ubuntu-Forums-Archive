---
title: "Changing IP Alias?"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by lumpy211 on 2009-11-16
Hi all,

I like to access my home computer from my via SSH and SFTP. The issue is, my ISP gives my home connection a rotating IP address. So sometimes I connect one day to one IP address, and the next the IP has changed so I have no way of connecting.

I've thought about how to get around this, and I've come up with a solution, but I need help on how to execute it. I've got Dropbox running on both my laptop and my home computer, and so my idea is to echo my home computer's IP address to a file which is then synced to Dropbox and thus my laptop computer. I've got this part figured out.

The extra step that I want to take is this: if I "http://home:8080" into Firefox, my laptop automatically knows the current IP address in the IP file. So how can I set up an IP "alias" that dynamically changes without having to reboot? In particular, I want to read my current desktop's IP from the file (located in, say "~/Dropbox/ip.txt") and run a command that updates the alias "home" say every 5 minutes or so. I've explored the command hostname, but apparently that's just for changing the current computer's alias. I know I can change hostnames on boot, but I don't want to reboot my computer every five minutes.

Any ideas for help? If this doesn't make any sense (I'm a little tired, so it may not) let me know and I can clarify.

Thanks!

---

### Post by doas777 on 2009-11-16
look into a dynamic dns provider like [http://www.dyndns.com/](http://www.dyndns.com/)

---

### Post by Iowan on 2009-11-16
[http://www.no-ip.com/]("http://www.no-ip.com/") is another. :p

---

### Post by lumpy211 on 2009-11-16
Thanks for the replies. I'll look into them :)

Just out of curiosity now, is there any way to make my original idea work?

---

