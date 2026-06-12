---
title: "ssh start up on boot"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by liquid_legs on 2012-01-01
i was wondering how do you start up an ssh server on boot, im guessing it has something to do with chmoding the sshd config file from this path etc/ssh/sshd_config and then typing in a few commands in the terminal to make start on boot, but im not quite sure.

---

### Post by fdrake on 2012-01-01
once you have installed openSSH and generated your keys with ssh-keygen, reboot. The ssh server should start automatically at boot time. check with "nmap 127.0.0.1"

---

### Post by liquid_legs on 2012-01-02
thanks fdrake. just wondering, if lets say the ssh server gets killed or is told to stop and then you restarted the computer would the ssh server still load on bootup.

also, after using the ssh-keygen command is used am i to run the server after for it come up at boot

---

### Post by Lars Noodén on 2012-01-02
> **liquid_legs said:**
> lets say the ssh server gets killed or is told to stop and then you restarted the computer would the ssh server still load on bootup

Yes.  **sshd** will restart automatically when the machine restarts.  [upstart](http://upstart.ubuntu.com/) takes care of that by using the configuration file [font=Courier New]/etc/init/ssh[/font].  You can still stop it, start it, or reload it manually if you want.

---

### Post by Lars Noodén on 2012-01-02
> **fdrake said:**
> check with "nmap 127.0.0.1"

You can also use [scanssh](http://manpages.ubuntu.com/manpages/oneiric/en/man1/scanssh.1.html) which is design to scan specifically for ssh servers.

---

### Post by liquid_legs on 2012-01-03
awesome thanks

---

