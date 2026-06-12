---
title: "Problems with xinetd"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by me.shanky on 2010-03-04
Hello ppl,

I'm facing an unusual problem and I have no clue to what is the reason for the problem. I will be very happy if anyone can give me a possible reason

I'm trying to make an application run using xinetd. I have written the following configuration file in a file named 'keskya'(keskya is the name of the application)

```
# Keskya Configuration file for xinetd
service keskya
{
	disable = no
	socket_type = stream
	type = UNLISTED
	protocol = tcp
	wait = no
	user = aluru
	server = /home/aluru/keskya/bin/keskya
	server_args = -u <value> -p <val> -h <val> -d <val>
	only_from = 127.0.0.1
	port = 2347
	log_type = FILE/tmp/keskya.log
}
```

This application interacts with a database and hence i have given all the args in the server_args parameter

I placed this in /etc/xinetd.d folder and restarted the xinetd service

Unfortunately xinetd says there are no services running. I checked if xinetd is running properly by installing an ftp server and it works fine. 

So, can anyone tell me what might be causing this problem?[-o<

 I understand that if xinetd is running fine, the problem should be in the application or configuration file. Application in stand alone mode is running fine! The configuration file contains nothing complex and all the args I gave are valid.

---

