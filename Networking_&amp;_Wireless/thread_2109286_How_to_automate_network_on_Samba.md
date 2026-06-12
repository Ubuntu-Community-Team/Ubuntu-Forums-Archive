---
title: "How to automate network on Samba?"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by artificialname on 2013-01-27
Hi
I want my network to work automatically when my computer is on without having to type this in a terminal window

sudo chmod 0777 /myshare
sudo service smbd restart
sudo service nmbd restart

I followed these instruction:
[http://www.linuxhaxor.net/nixies-linux-haxor-quickie-setting-up-file-sharing-between-windows-linux-and-macs-with-samba/](http://www.linuxhaxor.net/nixies-linux-haxor-quickie-setting-up-file-sharing-between-windows-linux-and-macs-with-samba/)

Now my network works (from my linux desktop to my mac book pro laptop). BUT I want it to work automatically when I turn my desktop on - i.e. so I don't have to type the following every time in terminal to start my network:

sudo chmod 0777 /myshare
sudo service smbd restart
sudo service nmbd restart

By the way, 
1) is this "secure" (setting it up to work automatically)?
2) am I going about setting up a home network in the right way? Is using Samba and the above "linuxhaxor" guide the right method?

---

