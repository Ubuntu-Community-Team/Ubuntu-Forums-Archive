---
title: "ProFTPD Server (550 error)"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by tottenham12712 on 2011-02-28
Hey guys,

I have a web server that is going to be used to start hosting web sites and up till now ftp wasn't needed. But now that customers want access it needs to work. Basically I can go through all the /www files just like I setup. But when I try to delete, move or write I get this: ```
550 index2.html: Operation not permitted
```

I searched around the forums and couldn't find anything to relevant but if anyone has a link or a fix for this it would be much appreciated! 

Thanks,
Dylan

EDIT: I am also using webmin to manage this server

---

### Post by tottenham12712 on 2011-03-03
bump, help anyone?

---

### Post by tottenham12712 on 2011-03-21
bump for help!

---

### Post by thewipe on 2011-03-22
Hi Dylan,

I'm not an expert, your problem might be only within your proftpd.conf file. I'm having the same problem before  but I fix it by changing this part down below the DIRECTORY part, or  try to delete it first and see if it works .


	```
<Limit MKD STOR DELE XMKD .....>
	DenyAll
	</Limit>
```

---

### Post by tottenham12712 on 2011-07-13
> **thewipe said:**
> Hi Dylan,

I'm not an expert, your problem might be only within your proftpd.conf file. I'm having the same problem before  but I fix it by changing this part down below the DIRECTORY part, or  try to delete it first and see if it works .


    ```
<Limit MKD STOR DELE XMKD .....>
    DenyAll
    </Limit>
```


I actually gave up on it and switched to pureftpd and that works great if you still having issues

---

