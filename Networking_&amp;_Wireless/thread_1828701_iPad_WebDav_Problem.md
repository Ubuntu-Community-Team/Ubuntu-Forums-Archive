---
title: "iPad WebDav Problem"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by dwitkin on 2011-08-19
I'm hoping a WebDav / networking expert can help me with a problem. I'm trying to copy files to a mounted WebDav location and getting an "Invalid filename" error.

Here is the situation in detail:
I have an iPad app called GoodReader, which provides access to an app-specific file system on the iPad via a web address (e.g., [http://192.168.X.X:8080](http://192.168.X.X:8080)).

When I connect to the address using the places menu, I am able to  transfer files to the iPad just fine.  However, I want to use a program (SuperFlexible -- same general concept as Unison) to automatically sync files from my Ubuntu 10.10 laptop to the iPad and to do that I need to mount the iPad (e.g., to /media/iPad).

So, I mounted the iPad using this command (there is no username or password necessary):
```
sudo mount -t davfs  'http://192.168.X.X:8080' /media/iPad
```

At first, I was getting what appeared to be permission errors so I changed ownership recursively of all files to my user:group, but now I get the "Invalid filename" error.

Why would the connection and file transfer work fine when mounted via the Places menu but not work when mounted from the command line? Am I using an incorrect command line?

Appreciate your help!
Dave

---

