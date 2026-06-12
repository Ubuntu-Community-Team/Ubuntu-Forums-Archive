---
title: "[SOLVED] Can't connect to Apache server from LAN computers"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by rogdawg on 2008-12-12
I am really stumped on this one...

I am using Hardy Herron (8.04). I have set up Apache2, and everything seems to work fine when testing it locally. My php pages seem to work, html pages work, I have even begun setting up Subversion server so my laptop computer (macbook) can use my linux box as a code repository. If I enter [http://mycomputername/svn](http://mycomputername/svn) into the local browser, I get the correct page, telling me that that is working locally.

But, I can't do any of this from any other computers on my LAN. Everything is connected via a router. I can "see" the ubuntu machine from the other computers, and I can work with the shared folders.
The Ubuntu computer's IP address is 192.168.0.102

From my Macbook...
If I ping 192.168.0.102, that works
If I telnet 192.168.0.102, I get "Connection refused"

If I ping 127.0.1.1 (Apache Server), I get nothing
If I telnet 127.0.1.1, I get nothing. (timeout)

It seems something must be amiss with my Apache settings but, I can't find anything that looks out of place.
Does anyone have any suggestion as to how I can debug this?

Thanks in advance for any help you can provide.

---

### Post by jcwmoore on 2008-12-12
i'm not seeing it in your post, but what happens when you go to [http://192.168.0.102](http://192.168.0.102) from your mac book, or non-local computer?  I see that you can ping it and i'm assuming you tried to go to [http://nameofserver](http://nameofserver) and that filed, am i correct?  my first guess is host file of the client may not be set up for the LAN.

---

### Post by rogdawg on 2008-12-13
Thank you for your response. 

If I enter [http://192.168.0.102/](http://192.168.0.102/) in the browser on my Macbook, I actually get the index.html page that I placed in the web-root of my Ubuntu machine. That is progress. That wasn't happening before. I wasn't getting that before. The only thing I have done is completely reboot my cable model, and my router. 

But the original problem, that I did not mention in my first post, still exists. I cannot create a repository in Eclipse on my Macbook that points to the svn server I installed on Ubuntu. That is what alerted me to the original problem. I know this sounds like a completely different issue (and it is) but, I was originally attempting to do this when I realized I could not even view simple web pages from my Ubuntu computer. 

Now that that issue seems to be resolved. I can get back to figuring out the svn problems. 

If, when trying to create the repository, I enter "svn+ssh://192.168.0.102/svn", I get the following error: "There was a problem while connecting to 192.168.0.102:22". I have tried many different ways of formatting the URL, but none works. 

The svn directory is on the root of my Ubuntu machine, and my dav_svn.conf file looks to be set up correctly. I have this:
<Location /svn>
    DAV svn
    SVNPath /svn
    AuthType Basic
    AuthName "Subversion Repository"
    AuthUserFile /etc/apache2/dav_svn.authz
</Location>

That is pretty much it. Does anyone have any suggestions?
Thank you, and thanks again for your reply.

---

### Post by rogdawg on 2008-12-13
I solved the problem.

SSH was not running on my Ubuntu machine!

I downloaded/installed it, and BINGO! 

What a releif.

---

### Post by superprash2003 on 2008-12-13
please mark thread as SOLVED

---

