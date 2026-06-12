---
title: "Citrix Receiver 11 crashes when IE or Lotus Notes is launched."
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by brion@cbkidder.com on 2011-02-02
Citrix Receiver 11 crashes when IE or Lotus Notes is launched.

Citrix Receiver 11 launches and runs my company's virtual WindowsXP desktop fine until I try to launch either Internet Explorer or Lotus Notes; running either of these crashes Citrix and the Citrix window closes. OpenMotif is installed.

Citrix was working fine on 10.03LTS but now that I have upgraded to 10.10 I am having this crashing problem. Any recommendations appreciated.

brion@brion-ThinkPad-T61:~$ ldd /usr/lib/ICAClient/wfcmgr
	linux-gate.so.1 =>  (0x00d84000)
	libXm.so.4 => /usr/lib/libXm.so.4 (0x004d4000)
	libXp.so.6 => /usr/lib/libXp.so.6 (0x00446000)
	libXpm.so.4 => /usr/lib/libXpm.so.4 (0x00d8c000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00f1f000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x001b6000)
	libXmu.so.6 => /usr/lib/libXmu.so.6 (0x007a5000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00de4000)
	libdl.so.2 => /lib/libdl.so.2 (0x00110000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00146000)
	libc.so.6 => /lib/libc.so.6 (0x001cf000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00160000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00ac0000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00114000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00124000)
	libuuid.so.1 => /lib/libuuid.so.1 (0x00128000)
	/lib/ld-linux.so.2 (0x00e96000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00c8e000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x0012d000)
brion@brion-ThinkPad-T61:~$

---

### Post by brion@cbkidder.com on 2011-03-04
This is still a problem so I rolled back from Maverick 10.10 to Lucid 10.04LTS but Citrix Receiver still crashes if I launch Lotus Notes or Internet Explorer inside the virtual machine. 

You know what's really annoying? Sometimes after working in Citrix for a long while, I'll try to launch Notes and it will work fine without crashing. But then next time I try it will crash the Citrix window. I'm guessing that whatever changed from Citrix 9 to Citrix 11 is causing the intermittent problem. Maybe it's a memory problem, I don't know. Man I don't want to have to go back to XP :(

Any suggestions will be appreciated.

---

### Post by vanwijngaarden on 2011-05-10
I guess there is no solution yet? I have the same problem and it is really annoying.

Regards,
Arie

---

