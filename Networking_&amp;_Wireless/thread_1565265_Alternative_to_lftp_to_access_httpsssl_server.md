---
title: "Alternative to lftp to access https/ssl server?"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by Benic on 2010-08-31
I use lftp to access a remote https/ssl server for my job. I just do very simple stuff: upload/download files and directories and rename them.

I was wondering: if there is a suitable alternative?

Thanks!

---

### Post by pricetech on 2010-08-31
Several.  My pick is FileZilla.  Nautilus will do FTP also if I'm not mistaken.  Most web browser can handle FTP also, though some need a plugin or addon to do it.

---

### Post by pqwoerituytrueiwoq on 2010-08-31
I use [Fireftp]("https://addons.mozilla.org/en-US/firefox/addon/684/").

---

### Post by Benic on 2010-08-31
> **pricetech said:**
> Several.  My pick is FileZilla.  Nautilus will do FTP also if I'm not mistaken.  Most web browser can handle FTP also, though some need a plugin or addon to do it.

I tried FileZilla. Unfortunately it doesn't work with HTTPS. With Firefox, I can access the server and download the files, but I can't upload or edit names. I've been trying recently different setups with Nautilus and so far, no luck.

---

### Post by Benic on 2010-09-01
> **pqwoerituytrueiwoq said:**
> I use [Fireftp]("https://addons.mozilla.org/en-US/firefox/addon/684/").

Same as FileZilla: doesn't seem to work with HTTPS.

Today, I've found Gnome Commander. Its interface is quite similar to FileZilla and the likes. It connects to a remote server using the same window as Nautilus. While Nautilus couldn't connect to the server using secured WebDAV protocol, Gnome Commander does. It's a bit puzzling to me... 

Anyway, Gnome Commander can do pretty much all that is needed and seems to be one of the very few program, along with lftp, to be able to connect to a remote https server.

---

