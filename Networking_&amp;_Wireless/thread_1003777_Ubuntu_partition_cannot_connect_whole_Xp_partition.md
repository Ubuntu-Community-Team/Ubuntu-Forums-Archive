---
title: "Ubuntu partition cannot connect whole Xp partition can?"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Knivex on 2008-12-06
I recently installed ubuntu 8.10 on a partition (the other partition has Windows XP x64 installed)

I have no problems connecting to my Linksys WRT54GS router on XP, but when I boot up ubuntu my computer is unable to connect properly.

Can anyone help me? 

Thanks.

---

### Post by MeURi on 2008-12-06
Please, be more specific.

Are you using a wired or wireless connection? Which ethernet or wireless adapter do you have on your pc? Is your router set up to use DHCP or you use static IPs in your lan?

---

### Post by Knivex on 2008-12-06
I'm using a wired connection, it's a direct connection from my PC to router, and my router is set up for DHCP.

---

### Post by MeURi on 2008-12-06
Ok, so you *should* be online with ease, since Ubuntu configures ethernet with DHCP by default...

Is your ethernet card somehow exotic? Please, post the output of the following commands (without the quotes):
[list]
[*]"lspci | grep ethernet"  -  if it shows nothing, use Ethernet instead of ethernet (I'm on Windows right now and cannot check)
[*]"ifconfig"
[*]"sudo /etc/init.d/networking restart"
[/list]

The first will show you the ethernet card Ubuntu identifies; the second prints out the current configuration for your interfaces; the third one makes Ubuntu restart the networking service (it should try to acquire a new address from your router).

If you got nothing suspicious, like warnings or errors, try to ping, for example, Google, by issuing a "ping -C 3 www.google.com", and see if it complains about something (here again, no quotes).

All these commands have to be inserted from the terminal.

EDIT: I just realized that you have no connectivity from Ubuntu, so save the output to a text file, and copy it into your Windows partition, so that you can post it back (if you use notepad to open those text files, you will get all the file on one line, because of different line endings from linux to Windows; use wordpad, or copy the files from the terminal using "mcopy -t *source destination*").

---

