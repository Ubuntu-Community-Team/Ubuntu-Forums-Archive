---
title: "Freenx Server ... Any Help would be appreciated."
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by dalesomers on 2010-01-22
I have installed Freenx-server on my ubuntu 9.10 workstation and i am unable to create custom keys.

I enter 

```
sudo dpkg-reconfigure freenx-server
```

into the terminal, follow the prompts choosing "Create New Custom Keys"
and then "SSH"

afterward i get an error in terminal that says

```
update-rc.d: warning: freenx-server stop runlevel arguments (1) do not match LSB Default-Stop values (0 1 6)
```

I'm at a loss trying to figure the problem...any help would be greatly appreciated.

---

### Post by 2hot6ft2 on 2010-01-25
Check the guide and see where you messed up.
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
Troubleshooting at the bottom has
> Solution: Check that this line exists in /etc/ssh/sshd_config "AllowUsers nx" and this line also exists and is set to authorized_keys2 "AuthorizedKeysFile %h/.ssh/authorized_keys2", if commented, just uncomment them. after that run this command in a terminal sudo /etc/init.d/ssh restart .This issue is due custom SSH server configuration.
Might be what you need. Just started using FreeNX and SSH myself.

---

### Post by rihkama on 2010-01-29
I seem to have ran into a similar issue. I followed the guide and everything works perfectly other than that I am unable to switch freenx to use custom keys. During the installation I also replied to the script that I want to use the custom keys.  ```
 update-rc.d: warning: freenx-server stop runlevel arguments (1) do not match LSB Default-Stop values (0 1 6) Not starting freenx-server, it's already started. 
```

---

### Post by kyeongsoo on 2010-02-03
I too have the exactly same issue.

Now I wonder whether this has something to do with my running the command through Putty terminal over ssh session. My understanding is that runlevel for just a terminal session is different from that for GUI desktop.

Regards,
Joseph

---

### Post by kcowolf on 2010-02-05
I'm having the same problem as the op.  I'm getting the same message after telling selecting custom keys / SSH in dpkg-reconfigure, and I'm not seeing a custom_keys directory in /var/lib/nxserver/home/.

---

### Post by fishtek on 2010-02-05
Yup exactly the same problem here too!

My output:
```

update-rc.d: warning: freenx-server stop runlevel arguments (1) do not match LSB Default-Stop values (0 1 6)
Not starting freenx-server, it's already started.

```

Anybody have any ideas?

---

### Post by rihkama on 2010-02-06
I solved the key problem by manually deleting the default nomachine key from /var/lib/nxserver/home/.ssh/authorized_keys2 and replaced it with the key I created using ssh-keygen (I created the keypair without passphrase, I am not sure if passphrase works or not).  Everything works perfectly and server refuses to connect if I do not have the proper private key set on client.

---

