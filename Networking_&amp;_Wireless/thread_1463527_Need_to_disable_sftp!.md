---
title: "Need to disable sftp!"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by MattBarszcz on 2010-04-27
I have FTPS setup on my ubuntu server 9.10 machine using vsftpd, and I want to disable the default SFTP server in openSSH.  I didn't even know it was on until I accidentally connected to it.  I tried searching the internet, and it seems that all I should have to do is comment out the line:
```

Subsystem sftp /usr/lib/openssh/sftp-server

```restart sshd and it shouldn't work anymore.....except it does.

Thinking that /etc/init.d/ssh restart may not have worked, I restarted the machine, but I can still connect over sFTP.

Please help me turn it off.

Thank You,
Matt Barszcz

---

### Post by v1ad on 2010-04-27
edit: nvrm

---

### Post by MattBarszcz on 2010-04-27
> **MattBarszcz said:**
> I have FTPS setup on my ubuntu server 9.10 machine using vsftpd, and I want to disable the default SFTP server in openSSH.  I didn't even know it was on until I accidentally connected to it.  I tried searching the internet, and it seems that all I should have to do is comment out the line:
```

Subsystem sftp /usr/lib/openssh/sftp-server

```restart sshd and it shouldn't work anymore.....except it does.

Thinking that /etc/init.d/ssh restart may not have worked, I restarted the machine, but I can still connect over sFTP.

Please help me turn it off.

Thank You,
Matt Barszcz

Upon further research, it appears that maybe I can't disable SFTP features, because the FTP client just essentially logs into the shell and sends commands (but displays it in an FTP client interface).  The only way to disable that, would be to disable the shell.

---

### Post by Drenriza on 2010-04-27
did you comment out the 
```
[SIZE=2][FONT=Consolas]Subsystem sftp /usr/lib/openssh/sftp-server[/FONT][/SIZE]
``` ??
 
like this
```
[SIZE=2][FONT=Consolas][COLOR=#FF0000]#[/COLOR] Subsystem sftp /usr/lib/openssh/sftp-server[/FONT][/SIZE]
```
 
And then restarted the service.
 
```
[FONT=Consolas][SIZE=2]/etc/init.d/sshd restart[/SIZE][/FONT]
```

---

### Post by MattBarszcz on 2010-04-27
> **Drenriza said:**
> did you comment out the 
```
[SIZE=2][FONT=Consolas]Subsystem sftp /usr/lib/openssh/sftp-server[/FONT][/SIZE]
``` ??
 
like this
```
[SIZE=2][FONT=Consolas][COLOR=#ff0000]#[/COLOR] Subsystem sftp /usr/lib/openssh/sftp-server[/FONT][/SIZE]
```And then restarted the service.
 
```
[FONT=Consolas][SIZE=2]/etc/init.d/sshd restart[/SIZE][/FONT]
```

Yes I did, and it doesn't change any behaviour whatsoever.

--Matt

---

### Post by nathou on 2010-07-07
Same problem here with Lucid too.

Did anybody found a solution yet ?

---

