---
title: "SSH &quot;Error in stream protocol: End of stream&quot; help"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by nevarDeath on 2009-09-29
I'm using nautilus to transfer files over SSH and keep getting this error:
[IMG]http://i138.photobucket.com/albums/q249/nevarDeath/ssh_error.png[/IMG]

It first started happening after transferring 4GB of a 33.4 GB file. It has since been happening frequently after 2-500MB of 551MB files. It's gotten to the point I can't transfer them anymore. This is all over the course of 1 day btw, I haven't installed any new software.

The SSH 'server' I'm pulling the files from is a Windows Vista Ultimate Laptop with copSSH installed. The client is an ubuntu netbook remix netbook computer. I am connecting them over a private network I've setup. It's a linksys WRT54G router with the vista computer connected to ethernet and the ubuntu netbook is wireless. They are the only 2 computers connected to the router and there's no internet access. I have forwarded port 22 and optimized the speed by using the QOS options in the router and set it to G-only. I even tried changing the wireless channel thinking it might be getting interference from something, which didn't seem to help. I did not set static IPs, if that matters.

Does anyone know what settings I need to check from here, or what could possibly be the cause of this error?

---

### Post by nevarDeath on 2009-09-30
Wanted to bump this and report a change. I switched over to the madwifi drivers for my atheros card which resulted in a 400kbps speed bump, but I'm still getting this error. One thing happened I would like to mention though.

I was transferring a file from the vista computer to ubuntu and I opened chrome to go to facebook (not thinking lol) and as soon as I clicked on facebook from my start page, this error popped up on my ubuntu computer. which makes me think it's somehow related. I have closed everything I can think of that would be generating traffic on the vista computer though. TCPView reveals there are many instances of svchost.exe that are trying to maintain connections :( I started closing them all down but windows didn't like that.

Really if anyone just knows the right direction to point me in, I would be grateful. I'm a pretty good googler, but have just gotten so stuck. any tidbits of help are very appreciated at this point

---

### Post by nevarDeath on 2009-10-07
I guess this was due to wireless interference of some type. I tried them with ethernet cables hooked into a small switch and it went flawlessly. Hooked them into my router with ethernet and it went perfect again.

---

