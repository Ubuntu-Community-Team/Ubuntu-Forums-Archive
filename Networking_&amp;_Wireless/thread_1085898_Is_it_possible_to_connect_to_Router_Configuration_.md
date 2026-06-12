---
title: "Is it possible to connect to Router Configuration from 8.04 Server?"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by yawnzzzz on 2009-03-03
I have a 8.04 Server set-up that I'm doing some Dev work on, and I need to connect to my router's configuration settings.  Normally, I'd user another computer with a Web Browser, but currently, I have nothing but servers on this network.

Anyone have any ideas?

---

### Post by whoop on 2009-03-03
Maybe lynx or lftp? Don't know what protocols your router supports. Maybe post some router information

---

### Post by cariboo on 2009-03-03
Any text based browser should work, I prefer elinks.

Jim

---

### Post by yawnzzzz on 2009-03-03
I believe it's a Linksys WRT54G.  I'm not sure on the version number.

The default settings are:
IP address 192.168.1.1
Username leave blank 
Password admin

I'd check more thoroughly, but I'm currently on a business trip and away from my server, which is the main reason I'd like this information.  I'm hoping to SSH in and forward some ports needed to connect through FTP.

---

### Post by yawnzzzz on 2009-03-03
> **cariboo907 said:**
> Any text based browser should work, I prefer elinks.

Jim

Very cool.  I'm new to Ubuntu (and servers in general), so I didn't even know anything like that still existed.  Worked like a charm.  Thanks again.

---

### Post by whoop on 2009-03-03
Might want to change your password to something non-default. Even if administration is only accessible via lan. I no at least of one crack in the wild that can access the router via lan authentication with a default password, so there might even be more.

---

### Post by whoop on 2009-03-03
> **cariboo907 said:**
> Any text based browser should work, I prefer elinks.

Jim

My router does not support it :-(

---

### Post by yawnzzzz on 2009-03-03
Almost.. worked like a charm.  I'm a bit confused on how to save.

I can get to my port forwarding page that looks like this:

SSH___ 22_____ 22_____ 192.168.1.100_ [x]
______ 0______ 0______ 192.168.1.0___ [_]

It will let me click Enter to edit each value, then I click enter post it.  I get the message "Do you want to post form data to URL [http://192.168.1.1/PortRange.tri](http://192.168.1.1/PortRange.tri) (POST DATA)?" I hit Yes, but the information doesn't appear to be sent back.  Any ideas?

---

### Post by whoop on 2009-03-03
> **yawnzzzz said:**
> Almost.. worked like a charm.  I'm a bit confused on how to save.

I can get to my port forwarding page that looks like this:

SSH___ 22_____ 22_____ 192.168.1.100_ [x]
______ 0______ 0______ 192.168.1.0___ [_]

It will let me click Enter to edit each value, then I click enter post it.  I get the message "Do you want to post form data to URL [http://192.168.1.1/PortRange.tri](http://192.168.1.1/PortRange.tri) (POST DATA)?" I hit Yes, but the information doesn't appear to be sent back.  Any ideas?
Maybe the page is just not updated. Move away from that page and go back to see if it has changed. I know that a lot of linksys firmware has this problem.

---

### Post by yawnzzzz on 2009-03-03
> **whoop said:**
> Maybe the page is just not updated. Move away from that page and go back to see if it has changed. I know that a lot of linksys firmware has this problem.

I've closed out elinks and opened it back up, and the information isn't saved.

When I click Yes to posting back data, it takes me to a screen that says "http://192.168.1.1/PortRange.tri (POST DATA)" my cursor gets sent to the lower right corner, and in the lower left corner of the gray display it says OK.  But the only option I seem to be able to do is go back.

---

### Post by Iowan on 2009-03-03
As I recall, phpMyAdmin was somewhat painful to use via **elinks**.  I had to highlight a data entry field, hit enter, enter data, and hit enter again... This was for online class - I started using laptop w/ graphical browser to make changes (Still used **elinks** if time permitted).

---

