---
title: "No sound with Neomagic 256AV"
date: 2008-09-10
forum: Multimedia Software
---

### Post by uaskg on 2008-09-10
I have made a clean install of xubuntu 8.04 on my old HP Omnibook 4150 laptop. Sound does still not work.

askg@hp:~$ cat /etc/issue
Ubuntu 8.04.1

askg@hp:~$ aplay -l
aplay: device_list:205: inga ljudkort hittades...(no soundcard found)

askg@hp:~$ lspci -v | grep -A 5 [Aa]udio
01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)
	Subsystem: Hewlett-Packard Company MagicMedia 256AV Audio Device on Voyager II
	Flags: fast Back2Back, medium devsel, IRQ 10
	Memory at fe000000 (32-bit, prefetchable) [size=4M]
	Memory at fe700000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

Apparently this is a tough one to crack. I have found some solutions that involve using another module than snd-nm256 (on a Dell Inspiron). Has anyone out there a simpler, or more straightforward solution to this problem? Thanks in advance,

/GA

---

### Post by mali2297 on 2008-09-11
There are some old bug reports that might be related to your problem:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/47706](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/47706)
[https://launchpad.net/ubuntu/+bug/65247](https://launchpad.net/ubuntu/+bug/65247)

None has been resolved though, sorry.

---

### Post by mister_playboy on 2009-02-24
Same problem here, on a Gateway Solo 3100 with Xubuntu 8.10.

No idea what to do about it...

---

