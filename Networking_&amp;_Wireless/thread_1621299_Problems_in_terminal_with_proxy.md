---
title: "Problems in terminal with proxy"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by tariqsheikh on 2010-11-14
I have configured the Gnome network Proxy to use my university's proxy. Everything works, including Google Chrome, Firefox, Synaptic, Dropbox. But I am facing problems with the terminal. There are things (like wget) which work and things (like apt-get) which do not. Is there any workaround for this?

Thanks in advance.

---

### Post by tariqsheikh on 2011-04-21
Figured it out myself, or rather found it in the Ubuntu Help site. The solution is as follows:

This method adds a two lines to your .bashrc file in your $HOME directory. This method is useful if you would like apt-get and other applications for instance wget, to use a http-proxy.


> gedit ~/.bashrc

Add these lines to the bottom of your ~/.bashrc file (substitute your details for yourproxyaddress and proxyport)


> http_proxy=http://yourproxyaddress:proxyport
export http_proxy

Save the file. Close your terminal window and then open another terminal window or source the ~/.bashrc file:

> source ~/.bashrc

Test your proxy with sudo apt-get update and whatever networking tool you desire.

---

