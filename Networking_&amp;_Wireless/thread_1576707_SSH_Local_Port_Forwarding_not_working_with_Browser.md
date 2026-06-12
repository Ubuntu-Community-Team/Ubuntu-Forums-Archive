---
title: "SSH: Local Port Forwarding not working with Browser"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by abid_naqvi83 on 2010-09-17
I am running Ubuntu 9.10 on a Dell Inspiron E1705. Having read the instructions on [https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding") I tried to connect to specific websites via a secure SSH tunnel using local port forwarding using the command:

```
ssh -L 8080:www.ubuntu.com:80 <user on remote host>@<remote host>
```

This command gives me the expected access to the remote host and NO error is displayed indicating that the port forwarding has failed. I then open up my browser (both Firefox and Chrome) and attempt to access [http://localhost:8080/](http://localhost:8080/) and I get the following message (in the browser window):

```
ERROR

The requested URL could not be retrieved

While trying to retrieve the URL: http://localhost/

The following error was encountered:

Access Denied.
Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect.

Your cache administrator is webmaster. 
Generated Fri, 17 Sep 2010 21:42:13 GMT by privet.canonical.com (squid/2.6.STABLE18)
```

I expect the local port forwarding to forward localhost:8080 to [www.ubuntu.com:80](www.ubuntu.com:80) via the remote host over the secure ssh channel between my computer and the remote host and then on an open channel from the remote host to the [www.ubuntu.com](www.ubuntu.com) server. I think the problem is on my end and has to do with the browser being denied access to port 8080 (or any other free port that I attempt to use instead of 8080)when I point it towards 'localhost'. 

Find attached the ssh_config file (as a .txt file) I am currently using. I am guessing that since I am forwarding ports locally it is the SSH Client Configuration file that matters.

Any help would be appreciated.

---

