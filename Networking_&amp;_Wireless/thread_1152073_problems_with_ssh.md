---
title: "problems with ssh"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by sn0m on 2009-05-07
Chaps any of you could tell me why I can't connect using ssh.
I ve got laptop and a desktop in the house both running ubuntu.
I usually work on my laptop and would like important documents to be backed up in my desktop periodically.
I'm trying to use a guide reg rsync but can't get machines to connect via ssh. This is what rsync churns out:
sn0m@sn0m-laptop:~$ rsync -avz -e ssh [email]sn0m@sn0m-desktop.local[/email]:/remote/dir /this/dir/ 
ssh: connect to host sn0m-desktop.local port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(600) [receiver=3.0.5]
sn0m@sn0m-laptop:~$ 

Why don't I get propt for a password and connect rather then connection refused. Is it by default refused and where do you change it to accept?
Regards
Sokol

---

### Post by Iowan on 2009-05-07
You installed openssh-server on the desktop? Do your machines actually have the .local on hostname?

---

### Post by Alterax on 2009-05-07
Try apt-get install sshd (on your desktop).

By default you get an ssh *client,* but the ssh server that can accept connections isn't (for security reasons).

You can also, once this is set up, create a private/public key setup that will let you connect to your desktop from your laptop without being prompted for a password.  This is GREAT for things like Rsync.

First things first though.  Install sshd (which is openssh-server) and see if you can get a connection first.

---

### Post by sn0m on 2009-05-08
Thank you my friends, installing ssh-server sorted it out. I can start backing up my documents now.
Thanks again
Sokol

---

### Post by jeffplanes on 2009-05-12
I didn't want to create a new thread on virtually the same subject, so I'm just going to join in. Here is the issue:

Just as TS, I've got **sshd** installed on my notebook. It does all I need it to, but the thing is the **sshd** seems to run as a daemon from the startup. 
That means it leaves an open opportunity for everyone who knows my server IP, if and when I run the server.

**The question is**: how can I prevent **sshd** from running on a startup, calling it only when I need some **ssh**-related testing?

---

### Post by Brandon Williams on 2009-05-12
Run 'sudo update-rc.d ssh remove'. This will remove all the symlinks that cause init to start/stop the ssh daemon automatically.

That said, I don't think you need to be worried about having sshd running, provided that you only allow key-based authentication.

---

### Post by jsast21 on 2009-05-12
> **Alterax said:**
> Try apt-get install sshd (on your desktop).

By default you get an ssh *client,* but the ssh server that can accept connections isn't (for security reasons).



If you have a client on the laptop and the SSH server on the desktop, does that mean you can only log onto the desktop from the laptop and not vice versa?

---

### Post by Iowan on 2009-05-12
> **jsast21 said:**
> If you have a client on the laptop and the SSH server on the desktop, does that mean you can only log onto the desktop from the laptop and not vice versa?Correct! If you wanted to log into the laptop from the desktop, you'd need to install the server on the laptop.  Both machines *can* have both client *and* server software installed.

---

### Post by jeffplanes on 2009-05-13
[Brandon Williams]("http://ubuntuforums.org/member.php?u=744208")[B]:
[/B]Thanks for the advise. I run the command you suggested,  but that still didn't solve the issue. After reboot, both ssh and sshd still were on.  
Anyways, I used your hint as a key for search, and finally found that all directives for the start-up services are placed in **/etc/rc1.d** - **/etc/rc6.d** folders as links to the original scripts (located in **/etc/init.d/**); Each of the folders contains the README file with the instructions regarding disabling/enabling services through renaming of the link files. 
So I renamed the links and got the **sshd** daemon out of boot sequence. 
It still can be run manually by executing: **"sudo /etc/init.d/ssh **stop/start[B]"

ps
[/B]I understood the** "rc.*d** "- folders are the priority structure for satrtup services; But why is that so the link to **ssh **was put into all of them (at least  in my case )?
And why the **sshd** service enabling/disabling is controlled via **ssh** service calls (**/etc/init.d/ssh **start/stop)?

---

### Post by Iowan on 2009-05-13
> **jeffplanes said:**
> [b]ps
[/B]I understood the** "rc.*d** "- folders are the priority structure for satrtup services; But why is that so the link to **ssh **was put into all of them (at least  in my case )?
And why the **sshd** service enabling/disabling is controlled via **ssh** service calls (**/etc/init.d/ssh **start/stop)?Linux (at least the distro's I've used) have different runlevels.  The rcX.d directories define what services are started/stopped in each level.  If a service is to start (or stop) in all levels, it has a link in each directory. Notice that the links in the rcX.d directories point to the service in /etc/init.d.

---

### Post by Brandon Williams on 2009-05-13
> **jeffplanes said:**
> [Brandon Williams]("http://ubuntuforums.org/member.php?u=744208")[B]:
[/B]Thanks for the advise. I run the command you suggested,  but that still didn't solve the issue. After reboot, both ssh and sshd still were on.

Ah, right, I forgot that you would need the -f flag, since /etc/init.d/ssh still exists. I should have suggested 'sudo update-rc.d -f ssh remove'.

Glad you figured it out.

---

### Post by jeffplanes on 2009-05-14
> **Brandon Williams said:**
> Ah, right, I forgot that you would need the -f flag, since /etc/init.d/ssh still exists. I should have suggested 'sudo update-rc.d -f ssh remove'.
Glad you figured it out.

Thank you, again. And yet another thing, just in case anybody look into this topic for the same reason I did: 
This command - 
```
sudo update-rc.d -f ssh remove
```will only remove link files from **rc*.d** folders; however, if the source script still remains int the **/etc/init.d  **the link files will be restored during the next packages update.
It seems that the following syntax would be more appropriate:
```
sudo update-rc.d ssh start/stop
```While the "remove" modificator actually removes link files, the "start/stop" changes "S<number><name>" to "K<100-number><name>" in the link filename.

---

