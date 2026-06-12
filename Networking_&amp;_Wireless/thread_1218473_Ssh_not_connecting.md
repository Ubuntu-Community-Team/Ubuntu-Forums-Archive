---
title: "Ssh not connecting?"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by Dorzu on 2009-07-20
I have two computers(desktop+netbook) on a LAN at home. I previously set up ssh and used ssh/scp multiple times, both across the LAN and from external networks to home. I mostly use this for copying files without writing removable media.

I recently upgraded my desktop machine to 9.04 from 8.04 and the process was rough, but succeeded. Now I can't ssh from either machine to the other. When I attempt to ssh, the command ... pauses? waits? hangs? for an indefinite period of time. (Time scales measured in multiple minutes. I'll kill it after ten when I'm tired of checking the terminal.) In essence, the password/login prompt no longer appears, so I'm guessing that either the connection is failing for some reason, or some other setting is incompatible. 

I have port forwarding on my router, rules set to allow the non-standard port in ufw, and sshd_config edited where I thought it would work. Any suggestions?

---

### Post by martinbaselier on 2009-07-20
Can you login locally?

ssh 127.0.0.1

---

### Post by Dorzu on 2009-07-20
My apologies. I should have included that. I already tried that. ssh localhost and ssh 127.0.0.1 both work. I connect without any issue to the localhost on both machines.

---

### Post by martinbaselier on 2009-07-21
Just a bit of brainstorming:

So the ssh-server is working.
If you connect to a wrong ip, or on a wrong port, access will be blocked and you will just get an error.

Maybe ~/ssh/known_hosts would give a problem?

You could try renaming it.

---

### Post by superprash2003 on 2009-07-21
try disabling ufw temporarily just to ensure that nothing wrong with the firewall settings.

---

### Post by Dorzu on 2009-07-21
Thanks for the suggestions, but neither appears to change anything.

---

