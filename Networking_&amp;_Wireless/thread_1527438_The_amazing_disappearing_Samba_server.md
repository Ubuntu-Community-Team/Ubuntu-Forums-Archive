---
title: "The amazing disappearing Samba server"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by frankvw on 2010-07-09
Hi, everyone,

Once more SMB networking is driving me to the clear blue edge of insanity.

I have a Karmic server running Samba, and two Windoze XP workstations that access its files and printers. This has worked for ages without a hiccup. On the Windoze boxes I can type "net view" and the Linux server shows up in the list along with the two Windows machines that also share some directories.

But now. This morning I had the audacity of installing Samba on an Intrepid workstation (a laptop) and share my home directory thereon. This worked fine: on the XP boxes a 'net view' showed the Intrepid machine (named HP-550_, and I could do a "net view \\HP-550' to view its shares, while a 'net use' would map a drive letter to its share. This worked perfectly. All was fine.

But then, a few minutes later, XP started moaning that the drive letter mapped to the share on my newly Samba-ized Intrepid laptop was unavailable. A quick 'new view \\HP-550' came up with an "error 53" indicating that no shares on HP-550 could be found. A 'net view' would bring up a list of available hosts that still included the HP-550, but it would not respond anymore. After a few minutes the HP-550 disappeared from the lists of available hosts.

A few minutes later more things went haywire: other hosts began to disappear, too. I suspected a browser conflict between the laptop and the server, so I included a 'local browser = yes' in the smb.conf on the server, and a 'local browser = no' on the workstation, then restarted samba on both machines. This restored the list of available workstations, but it only showed the server and both XP boxes, as before, and the HP-550 Intrepid laptop was no longer listed.

However - from the server I can do an 'smbclient -L hp550' (using the IP hostname rather than the SMB hostname) and that will show all shares on the HP-550. So Samba is running on the laptop, and it offers the required shares - but Windows doesn't see it. At the same time file shares on the server can be viewed and accessed from the XP box without any hiccups.

Aargh.

Who can offer some enlightenment before I loose it completely?

Thanks!!

---

### Post by Iowan on 2010-07-09
Thread is marked [SOLVED] - did you find a solution, or did that tag (under Thread Tools) accidently get set?

---

### Post by frankvw on 2010-07-11
After about an entire day of banging my head against the wall, I discovered that the problem originated between keyboard and chair. I had made a stupid typo in the netmask bits field of one of the IP addresses in the 'interfaces' field in smb.conf that I looked at, but did not see, a gazillion times. My stupidity was made worse by teh fact that I also did not realize that the edit took place between the 'working' and 'not working' phase, because I only noticed that it had stopped working when my E-mail program crashed when I tried to send a message, about 20 minutes after said edit. Maybe I'm getting too old for this work.

I would have deleted my post if I had been able to figure out how (if it is possible at all) but failing that I marked it 'solved' to prevent other people from wasting time on it.

Sorry for the confusion.

// FvW

---

