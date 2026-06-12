---
title: "SSH loses connection"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by counterpoint on 2010-01-21
I'm having regular problems with an SSH connection being dropped.  All I see is:

```
Timeout, server not responding.
Fatal Error: Lost connection to the remote system

```

The server is certainly still alive, although it is possible there has been a delayed response.  I can't find any way to adjust the configuration to prevent this happening.  It should be possible, because on other systems (running an unmentionable operating system) I am able to keep an SSH connection for far longer.

Any suggestions?

---

### Post by Grenage on 2010-01-21
Is the machine with the problems under heavy CPU load?

---

### Post by stim on 2010-01-21
I had the same problem.  Set your ServerAliveInterval  to something small (like 5), see if that helps, if it does, increase the value to something more server friendly.

you can find the settings in /etc/ssh/ssh_config

---

### Post by counterpoint on 2010-01-21
Well, the server that I'm connected to is going to be busy at times.  But if a Windows laptop based on a Turion processor can maintain its connection, I'd expect an Ubuntu desktop running on Athlon X2 to be able to do the same!  The Ubuntu machine dropped the connection most recently while I was reading a book.  There would have been processes running, but nothing much.

Thanks for the config suggestion - I should have posted my settings at the outset.  In fact, that item is already set to 5.  I've played around with this before, but never been able to stop the failures.  The non-commented items in the config are:

```

    SendEnv LANG LC_*
    HashKnownHosts yes
    TCPKeepAlive no
    ServerAliveInterval 5

```

---

### Post by stim on 2010-01-21
Not trying to be a dickbag, but are you sure you are looking at the settings in /etc/ssh/ssh_config(your client settings) and not /etc/ssh/sshd_config (your server settings).  

After you change something in the ssh_config files, 

```
sudo /etc/init.d/ssh restart
```

If you are in the right place and restarting the service didnt help, set TCPKeepAlive to yes.

Good luck.

---

### Post by counterpoint on 2010-01-22
Thanks for the suggestions. Yes, I'm sure I know which is which of the SSH config files!

And actually I've tried TCPKeepAlive set to yes - it made matters a lot worse, I'm afraid.

Maybe another relevant point is that there's a wireless link between me and the internet, but it should be possible to configure communications to tolerate its vagaries.

---

### Post by stim on 2010-01-22
Wireless link is good to know. I've actually had similar problems with wireless and ssh.

[http://ubuntuforums.org/showthread.php?t=898903](http://ubuntuforums.org/showthread.php?t=898903)

[http://ubuntuforums.org/showthread.php?t=838873](http://ubuntuforums.org/showthread.php?t=838873)


Are you using ndiswrapper? What wireless chip do you have?  I would be VERY curious, to see if you could possibly use a wired connection (even just for a few minutes), to see if that fixes the problem.

---

### Post by counterpoint on 2010-01-22
Ah, it's not that simple!  I didn't say I was using a wireless network card.  My office has several computers and other devices connected together with a gigabit wired LAN, but connected to an internet router via an ethernet convertor.  And no, it is not possible to install a wired connection.

---

### Post by stim on 2010-01-22
Aha! You sir have a somewhat unique setup.  I am out of ideas. Sorry I couldn't be of more help. Maybe as a last resort, 

```
sudo apt-get remove --purge openssh-client && sudo apt-get install -y openssh-client
```


Sorry bud, good l uck.

---

### Post by counterpoint on 2010-01-25
In case it helps others, I do seem to have a workable solution.  Maybe other values would be even better, but I have changed the key parameters in /etc/ssh/ssh_config to:

[PHP]
    TCPKeepAlive yes
    ServerAliveInterval 15
    ServerAliveCountMax 20
[/PHP]

And I now have a terminal session that has been connected to the remote server for several days!

---

