---
title: "How to Access Shared Folders on Windows LAN"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by Alexdelpiero1974 on 2010-09-19
Hello All ,

would anyone please tell me ,  
how to access shared folder on windows LAN computers using Ubuntu 

i do it when i use windows as following :
i goto Run then 
type \\  computer IP
 
and i'm in 

now i want to know , how to do so using ubuntu , and what the problems 
might occur ??????????????


thanks

---

### Post by Joe of loath on 2010-09-19
Places - > network -> Windows network. All the shares should be in there. If you want to do it the same way as you did in windows, with the IP address, go Places -> connect to server, and select 'windows share' from the dropdown list.

---

### Post by Morbius1 on 2010-09-19
> i do it when i use windows as following :
i goto Run then 
type \\  computer IP
 
If you are looking specifically for the functional equivalent of the above process then this is the Linux way:

Pressing Alt and F2 at the same time brings up run.
Then type: 
```
smb://computer_ip_address
```

---

### Post by serverfarm on 2010-09-19
Or you  could go to places--> Connect to Server--> select "windows share" from drop down menu and then enter the IP of server under "Server" along with any other needed credentials (e.g. username, password, or folder)

---

