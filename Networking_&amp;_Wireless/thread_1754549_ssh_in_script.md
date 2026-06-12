---
title: "ssh in script"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by teknoman on 2011-05-10
Hi all.
I need to access all PCs in our LAN via ssh from our server in order to do some maintenance. All of them have Ubuntu or Kubuntu Lucid Lynx.

Some of the PCs allow this access with no problems, but most of them not. They just answer "Connection refused". I realized that these PCs don't start sshd at startup.

If I type "sudo service ssh start" manually in these PCs then sshd starts and all works. But I need it to be started automatically.

I tried some workarounds to solve with no success. I always tried to run a script at startup that could start ssh.

If I write a script with this single command inside (service ssh start) and execute it as root, it doesn't work! It doesn't start ssh.
But if I execute the same command directly in the command line, it works.

I don't understand this behaviour.
Also I don't understant why it doesn't happen to ALL the computers. Some of them start ssh at startup with no problems.

Any ideas?
Thank you in advance.

---

### Post by karthick87 on 2011-05-10
Why cant you add that command to startup list?

---

### Post by dasan on 2011-05-10
give a delay in script and try..
like 
sleep .9

---

### Post by iponeverything on 2011-05-10
ugly but you might just add "service ssh start" to your /etc/rc.local above the "exit 0"

---

### Post by teknoman on 2011-05-10
> **iponeverything said:**
> ugly but you might just add "service ssh start" to your /etc/rc.local above the "exit 0"
I did it. No success.
Thank you anyway.

---

### Post by teknoman on 2011-05-10
> **dasan said:**
> give a delay in script and try..
like 
sleep .9

I did it also. No success.
Thank you.

---

### Post by teknoman on 2011-05-10
I don't understand this difference in its behaviour:

If I type "service ssh start" as root then it works (it starts ssh service).
If I create a bash script with this command inside and I execute it, it doesn't work.
I also tried a php script (using the exec function). Same results.

I have no idea.

---

