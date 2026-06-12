---
title: "Frontend only Mythtv install"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by Gammell on 2007-03-28
Howdy.
I'm trying to install mythfrontend to run off of my laptop connecting to my household backend server. I've changed both ~/.mythtv/mysql.txt and /etc/mythtv/mysql.txt to point to the backend server and everything mysql related seems find (gets channel listings, etc).
However, it attempts to connect to the backend server on localhost. Anyone know where to change it? The Mythfrontend package doesn't seem to come with mythtv-setup (which I believe is only for the backend anyway) and I don't know of any other configuration files to change other than the mysql.txt files. Does anyone have any ideas?

Thanks.

---

### Post by newlinux on 2007-03-28
your DBHostname should point to the ip of your master backend (in ~/.mythtv/mysql.txt). That should have been alll you had to change if memory serves me correct. 

I believe you can also set this in mythfrontend from Utilities/Setup->Setup->General. Check to see that points to the right place...

what messages do you get from mythfrontend?

---

### Post by Gammell on 2007-03-28
> **newlinux said:**
> your DBHostname should point to the ip of your master backend (in ~/.mythtv/mysql.txt).

Yup, I've changed those, it seems that it's connecting to mysql fine. It gets the channel listings and such.

> **newlinux said:**
> what messages do you get from mythfrontend?
Running from the terminal, it gives:
```
2007-03-28 17:50:28.904 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-03-28 17:50:28.905 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
```

In the actual Mythfrontend there are the popup messages about 'unable to connect to backendserver, are you sure its running'.
Could it be a setting on the backend server that is shared over mysql? I wonder if the master backend server is defined simply as 'localhost', which would obviously confuse the laptop... I'll dig around a bit I guess if no one knows anything else, but that could be messy...

---

### Post by reclusivemonkey on 2007-03-29
> **Gammell said:**
> Could it be a setting on the backend server that is shared over mysql? I wonder if the master backend server is defined simply as 'localhost', which would obviously confuse the laptop... I'll dig around a bit I guess if no one knows anything else, but that could be messy...

You master backend server should have a reachable IP address, such as 192.168.1.5 or whatever its internal LAN IP address is. I think you can do this from your frontend installed on the backend server if that makes sense!

---

### Post by majoridiot on 2007-03-30
check the address of your backend with:

```
$ ifconfig 
```

and the enter that reported ip in the *frontend* setup- setup>>general 

save the setup, **exit** the frontend and then start it again for the new setting to take effect.

---

### Post by Gammell on 2007-04-02
> **reclusivemonkey said:**
> You master backend server should have a reachable IP address, such as 192.168.1.5 or whatever its internal LAN IP address is. I think you can do this from your frontend installed on the backend server if that makes sense!
Yeah, I got it. I had set up the backend server so long ago that it just had "localhost" instead of real IP addresses. Thanks everybody. Has anyone had success using computer names (ie, NetBIOS names) instead of ip addresses? I tried in the backend configuration, but had to go with absolute ip addresses, even though I have a working WINS server.

---

### Post by reclusivemonkey on 2007-04-02
> **Gammell said:**
> Yeah, I got it. I had set up the backend server so long ago that it just had "localhost" instead of real IP addresses. Thanks everybody. Has anyone had success using computer names (ie, NetBIOS names) instead of ip addresses? I tried in the backend configuration, but had to go with absolute ip addresses, even though I have a working WINS server.

AFAIK, You have to stick to IP addresses. I've tried to use hostnames, but never had any luck.

Glad you got it sorted =]

---

### Post by superm1 on 2007-04-02
> **Gammell said:**
> Yeah, I got it. I had set up the backend server so long ago that it just had "localhost" instead of real IP addresses. Thanks everybody. Has anyone had success using computer names (ie, NetBIOS names) instead of ip addresses? I tried in the backend configuration, but had to go with absolute ip addresses, even though I have a working WINS server.
I use host names for mine, but I have DNS properly setup in my appt to register all host names.  Eg, if the computer is called mythdell, i can use mythdell and it resolves to mythdell.mythweb.homeip.net in my appt which is 192.168.6.52 for me.

---

