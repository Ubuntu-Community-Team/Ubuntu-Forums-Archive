---
title: "Home Folder"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by livelong on 2012-02-11
Dear All,

I am running Ubuntu 10.10, Why my _**Home**_ folder is shown as shared folder on my network. I haven't enabled sharing for this one I dont want it shared and accessed by the computers on my network. Any help would be appreciated.
Thanks.

---

### Post by savanna on 2012-02-11
Could you give some more detail? Like is it being shown as shared from other Windows machines, other Macs, ...?

Also, go to the shell prompt (terminal), and type in:
[B]
sudo netstat -tanp[/B]

and paste the results into your post. This will show what network ports you've got open.

---

### Post by livelong on 2012-02-11
It is seen in other PC in network running Ubuntu 11.10. I haven't checked on Windows Pcs yet. About the shell command I will update soon.

Thanks for your response.

---

### Post by livelong on 2012-02-11
Following is the Netstat::

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      751/cupsd       
tcp        0      0 192.168.1.2:32857       125.252.225.134:80      ESTABLISHED 2863/firefox-bin
tcp       24      0 192.168.1.2:44385       192.168.1.2:139         ESTABLISHED 2016/gvfsd-smb-brow
tcp        0      0 192.168.1.2:32847       125.252.225.134:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:60732       209.85.229.138:80       ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:46013       192.168.1.15:139        ESTABLISHED 2016/gvfsd-smb-brow
tcp       28      0 127.0.0.1:45102         127.0.0.1:139           ESTABLISHED 2016/gvfsd-smb-brow
tcp        0      0 192.168.1.2:32861       125.252.225.134:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:32851       125.252.225.134:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:32844       125.252.225.134:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:50041       125.252.225.113:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:60095       125.252.225.136:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:46224       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.2:60786       69.63.189.11:80         ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:55703       209.85.148.113:80       ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:50050       125.252.225.113:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:60093       125.252.225.136:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:46014       192.168.1.15:139        ESTABLISHED 2016/gvfsd-smb-brow
tcp        0      0 192.168.1.2:32862       125.252.225.134:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:34168       125.252.225.104:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:34167       125.252.225.104:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:32845       125.252.225.134:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:46827       98.136.145.152:80       ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:32846       125.252.225.134:80      ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:55806       125.56.199.49:80        ESTABLISHED 2863/firefox-bin
tcp        0      0 192.168.1.2:32856       125.252.225.134:80      ESTABLISHED 2863/firefox-bin
tcp6       0      0 ::1:631                 :::*                    LISTEN      751/cupsd       
tcp6       0      0 :::445                  :::*                    LISTEN      680/smbd        
tcp6       0      0 :::139                  :::*                    LISTEN      680/smbd        
tcp6       0      0 192.168.1.2:139         192.168.1.4:35551       ESTABLISHED 2710/smbd       
tcp6       0      0 192.168.1.2:445         192.168.1.4:39935       ESTABLISHED 2825/smbd       
tcp6       0      0 192.168.1.2:139         192.168.1.4:45071       ESTABLISHED 2824/smbd       
tcp6       0      8 192.168.1.2:445         192.168.1.3:2521        ESTABLISHED 2738/smbd       
tcp6       0      0 127.0.0.1:139           127.0.0.1:45102         ESTABLISHED 2019/smbd       
tcp6       0      0 192.168.1.2:139         192.168.1.2:44385       ESTABLISHED 2734/smbd
```

---

### Post by livelong on 2012-02-20
Awaiting expert advice......

---

### Post by Morbius1 on 2012-02-20
Please post the output of the following command:
```
smbtree
```

---

### Post by livelong on 2012-03-06
SMBTREE out put::

$ smbtree

Enter adeel's password: 

WORKGROUP
    \\LINUX                  linux server (Samba, Ubuntu)
        \\LINUX\english idioms  
        \\LINUX\uninstall          
        \\LINUX\english idioms     
        \\LINUX\english poetry     
        \\LINUX\fun with figures     
        \\LINUX\mp3                
        \\LINUX\un zip             
        \\LINUX\ubuntu fixes           
        \\LINUX\IPC$               IPC Service (linux server (Samba, Ubuntu))
        \\LINUX\adeel              
        \\LINUX\print$             Printer Drivers


I think this would help..

---

### Post by Morbius1 on 2012-03-06
The following does in fact look like your home folder:
> \LINUX\adeel              Samba isn't in the habit of doing this sort of thing on it's own though so to to dig a little deeper run the following commands to see where samba is setting it to shared:
```
testparm -s
``````
net usershare info --long
```

---

