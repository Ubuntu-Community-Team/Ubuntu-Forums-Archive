---
title: "Ubuntu 9.04 Server help"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by KixZick on 2009-06-24
I wanted to know what I can do with a Server like make a web (I'm new to this) I only figured out that I can't do any thing. I herd that If you want to use it as a home server you can control other pcs with a home server How. I can't do anything because I don't know Terminal. Would help If you know a guide to learn Terminal.

---

### Post by jonobr on 2009-06-24
Hello


Just wondering what your goal is for your system.

It sounds as if you want to have a gui environment but are only getting a login prompt.
The server is built like this as its meant to be a functional application and server box which will be slowed down by the use of a GUI.

You can install the this environment , however, I would suggest you start from a different angle.

I would recommend you install the desktop and get used to the file structure and specifically dealing with the terminal and ubuntu/linux in genereal, this will strengthen you ability to use the server.
You can install apache from the desktop envirement, you can also use programs like webmin to work with your server.

IN regards to your question about apache

if you login to your server, and type in

```
sudo /etc/init.d/apache2 status
```

If it says apache is running.
You already have it installed, you need to go /var/www/ and create your web content in there ( create an index.html page or whatever content you want)
In fact , an easier way to test is to put the address of your server in the browser and you should get a message back saying it works

---

