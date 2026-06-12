---
title: "ubuntu 12.10 refuses to see other networked machines"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by dureal99d on 2013-02-22
I am at my end here.

For some reason I cannot get ubuntu to see other windows machines nor any other ubuntu machines on the network.

I can connect using the server option but in nautilus nothing

I have installed samba, winbind and configured the smb.conf to the best of my knowledge which is not much.

Crazy thing is my windows machines can see my ubuntu machines with no issues & I am able to shares files and the whole bit.

My ubuntu machines can see my printer and my western digital networked live drives can be seen by my ubuntu machine but thats it.

Sooooo, what do I have to do/Configure in order for my ubuntu machines to see each other and for them to see my windows machines in nautilus.

I am willing to post my network config file if it will help you to help me.

I thank any & all in advance.

---

### Post by JRV on 2013-02-22
Try starting nautilus from the command line to see what error messages you receive.

Ubuntu to Ubuntu:
```

nautilus sftp://[USER]@[HOSTNAME/USER/HOME/

```

Ubuntu to Windows:
```

nautilus smb://[WINDOWS_HOSTNAME]/[WINDOWS_SHARENAME]

```

---

### Post by dureal99d on 2013-02-24
[QUOTE=JRV;12524262]Try starting nautilus from the command line to see what error messages you receive.

I will and shall post the results.

---

