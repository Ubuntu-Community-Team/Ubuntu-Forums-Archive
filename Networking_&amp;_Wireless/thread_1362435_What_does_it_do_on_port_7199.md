---
title: "What does it do on port 7199"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by pktrivedi on 2009-12-23
Hi,
i have two problem that needs to be resolved.

I just installed Ubuntu 9.10 Karmic Koala.
I live in a university with a proxy that requires username & password.
I know how to configure **/etc/apt.conf**. I did that and updated the installation by firing
```
sudo apt-get update
```It got updated alright.

Now when I try to install any software from "Ubuntu Software Center" it fails and says error code 407 proxy require authentication. 
Does it not take proxy authentication from **/etc/apt.conf**? If not from where does it take?

Another problem is our university proxy is slightly paranoid.
It temporarily blocks IP address of PCs which harass it. I mean some bombarding or some activity that proxy does not like. And there is a page where it show IP addresses and ports that are temporarily blocked. Now my IP appears in that list with port **7199**.
So my question is what does this Ubuntu installation do to offend our proxy through this port?

Thank you

---

### Post by pktrivedi on 2009-12-23
Oh and now proxy page shows port **6599** against my blocked IP.

---

### Post by pktrivedi on 2009-12-23
Moreover I noticed some strange thing.

There was a file named **apt.conf~** which did not contain username and password for proxy so I edited it too.
But again when I saw it created new file named **apt.conf~~** without username and password!!!

This keeps on occurring, so what is going on here?

---

### Post by BkkBonanza on 2009-12-23
Gnerally speaking files with ~ at the end are automated backups. So perhaps apt-get is just making a backup of it's config in case something goes wrong.

If you want to know what is using port 7199 or any other port you can use the netsta command. eg.

sudo netstat -nptu 
will show open connections in tcp and udp protocols. You'll see one or more connected with "foreign port" 7199 and at the line end it will have a process name.

If you use -lntpu it will show any servers listening on your machine. (l = listen)
You probably don't need thatt now but maybe someday.

---

### Post by pktrivedi on 2009-12-23
> **BkkBonaza said:**
> Gnerally speaking files with ~ at the end are automated backups. So perhaps apt-get is just making a backup of it's config in case something goes wrong.


Well that is what I knew, but the problem I mentioned is that it is not the backup.
Because original file has entry **"...username: password@proxyserver: port"** and the file with ~ has the entry **"...proxyserver: port"** only.

> **BkkBonaza said:**
> If you want to know what is using port 7199 or any other port you can use the netsta command. eg.

sudo netstat -nptu 
will show open connections in tcp and udp protocols. You'll see one or more connected with "foreign port" 7199 and at the line end it will have a process name.

If you use -lntpu it will show any servers listening on your machine. (l = listen)
You probably don't need thatt now but maybe someday.

Now the situation has become more complicated.
As I told you our proxyserver temporarily blocks IPaddr of offending PCs.
I change my IP to continue working and installing required packages.

For example my IP was 10.141.200.73 now I changed it to ....74 and start working.
After a while proxy removes ban on ...73 and puts ban on ...74 so I change my IP back to ...73 and now since installation is complete I leave for my home on campus.
But from home what do I see on proxy's block page?? Surprise!! It is still blocking the IP 10.141.200.74 which I changed so my PC at work does not have that IP anymore but proxy still keeps on blocking it and to add more to the strangeness the port keeps on changing which shows it is not the same old block. 
Something from IP 10.141.200.74 is still offending proxy on different ports in some way.
I pinged ...74 but there is nothing there. I did ssh to my work PC which has now IP ....73 and execute ""netstat" and there is no connection to proxy.

You might say there some problem from proxy server that it keeps on showing the blocked IP which does not exists. 
But wait now I go to my workplace again and remove the LAN cable of my PC and bingo after a while proxy page removes IP ....74 from the ban-list.

And I am completely baffled.

---

### Post by BkkBonanza on 2009-12-23
I was just remembering. Some editors backup with ~ just before they save the new version of a file. So the backup would be from before you edited the username/passwor part. I think that makes sense. 

As for the other ban list stuff - no idea what's going on there.

---

