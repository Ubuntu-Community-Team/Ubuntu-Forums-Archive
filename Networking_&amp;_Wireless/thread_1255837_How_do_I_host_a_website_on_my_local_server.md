---
title: "How do I host a website on my local server?"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by RFXCasey on 2009-09-01
Hi, I'm running Debian on a Dell poweredge 2400 I have in my garage. I am currently running an FTP server on it using ProFTPD but would like to know how I can run a website from the same machine? I would also like to know if there is some way to integrate the FTP server into the website. Thanks.

---

### Post by cariboo on 2009-09-01
installing the packages you need for a web server are pretty easy, open a terminal and su to root, the type:

```
tasksel
```

you should be able to mark LAMP for installation. Once apache, php and mysql are installed you should be able to access the web site by typing:

```
http://<server>
```

in a browser. Substitute your server name or ip address in the above command. If every thing installed properly you should see a web page that says It Worked!

---

### Post by RFXCasey on 2009-09-02
Ok so once I do that do I just move my stored website into a specific directory to host it.

---

