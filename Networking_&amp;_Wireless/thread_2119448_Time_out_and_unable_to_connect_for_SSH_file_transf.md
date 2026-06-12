---
title: "Time out and unable to connect for SSH file transfer"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by zlummis on 2013-02-23
Hi all,

I just got my server up and running but i am running into a problem. I can use webmin to upload files to my server but I am unable to use filezilla to upload them using ssh. Any ideas on how to fix this without needing to reinstall the server os?

Thanks

---

### Post by x64Architecture on 2013-02-23
Can you provide some more details, like what error message your receiving when you try to upload files through SSH.

---

### Post by papibe on 2013-02-23
Hi zlummis. Welcome to the forums ):P

> **x64Architecture said:**
> Can you provide some more details, like what error message your receiving when you try to upload files through SSH.

+1

Is the client a Linux machine or a Windows client?

If it is Linus, could you post the details of a connection attempt using the triple verbose option?
```
ssh -vvv yourserver
```
Regards.

---

### Post by zlummis on 2013-02-24
The server is running ubuntu but i am trying to upload to it using my laptop running windows 7. I am trying to use filezilla to upload to the server but the error i am getting is: error: connection timed out; error could not connect to server. The first server I made had no problems like this what so ever. 

@papibe: what name should i be using where you have your server:
> If it is Linus, could you post the details of a connection attempt using the triple verbose option?
Code:
ssh -vvv yourserver

---

