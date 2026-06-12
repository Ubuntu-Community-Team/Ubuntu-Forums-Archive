---
title: "Monitor Sever Using Web Interface"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by erbag on 2010-07-21
I want to install ubuntu server on an old pc and use it in my home office. However, I'll have to borrow a monitor to do the instillation... when I'm done I'll have to return it. **Is there a way to monitor/manage the sever by using my web browser, free of cost?**

**Also seeing that I'm not so savvy with commands should I install the desktop interface?**

---

### Post by oomar on 2010-07-21
Unless you NEED to use the desktop just set up Webmin. It works great. for anything else you could possibly need (there isn't much Webmin can't do) you can SSH in. Using the CLI everyonce and a while is healthy.

If Webmin doesn't satisfy you, there is a WONDERFUl little CLI monitering thing I use called htop. just ssh in, install it, run htop and watch as you see your computer.... well probably dooing nothing but showing status of your programs. but its good. :D then you can always use ss, netstat, lsof to monitor things more specifically


EDIT: everything I just posted is EXTREMELY easy to use. these commands you just run. no options to make it confusing. if you absolutely must have a GUI then you could always leave a VNC server on it, but I dont suggest it.

---

### Post by erbag on 2010-07-21
Sorry I'm a little confused...

Are you saying that I don't need to install the Desktop GUI and I should just install "Webmin", only install the Desktop GUI if I _HAVE_ to.

---

### Post by cariboo on 2010-07-22
If you use the Server install CD, there is no gui included. Running the desktop gui all the time on a server connected to the outside world, is just asking to be cracked. 

The webmin .deb is available [here]("http://www.webmin.com/")

Once it installed point your web browser to [http://servername:10000](http://servername:10000), you can do all the administration from your browser.

There are links to running demo's on the webmin home page, so you can give it a try before installing.

---

### Post by erbag on 2010-07-23
Thanks alot! Appreciated... Downloading the iso now...

---

### Post by dca on 2010-07-23
Depends on it's usage.  If the server you're building is to be used as a host to share files only, the easiest is 'FreeNAS' or I think there's another out there.
 
If it's to be used to host files along w/ being a host to media files, emails, web, then Ubuntu Server 10.04LTS is the way to go... and correct, no GUI.  You can add GUI by typing *sudo apt-get install ubuntu-desktop* @ CLI but as suggested, just as easy to install webmin util from repos and go from there...
 
...downside, using FreeNAS, limited on drivers so you wouldn't be able to do anything via wireless, server has to be cabled...

---

