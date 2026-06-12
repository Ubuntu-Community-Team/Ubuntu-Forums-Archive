---
title: "Proxy settings in Ubuntu server 9.04"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by bereta on 2009-07-07
Hello all

I have installed Ubuntu server 9.04 on a box that is behind a proxy. My theory is that as a result I can not reach the package repositories and install or update new packages. I did not enter any proxy information during the install process. The proxy that I am behind requires identification (username and password)

My question is how do I configure the proxy setting, I know how it’s done and firefox or IE but this is obviously different. I have come across an old thread ( [http://ubuntuforums.org/showthread.php?t=136065&page=2](http://ubuntuforums.org/showthread.php?t=136065&page=2) ) discussing this, and suggesting the following command:

```
export http_proxy=http://usernameassword@proxyort

```

But in my case I don't know what the proxy port is. The setting URL that I use in firefox points to a proxy.pac file (proxy auto cofig). 
How do I set this up in the server version? I know I can be done in the desktop edition, all though I never actually tried it.

Thanks I advance.

---

### Post by LukaszSJHS on 2009-07-23
I am having the same problem.  I was given our proxy server name, and I entered it into /etc/apt/apt.conf
And it essentially breaks my internet.  My admin prefers to points me to a config.pac file, which I believe is from a Windows Proxy Server.  Is it possible to somehow enter the path to the .pac file for Ubuntu Server to use?

---

### Post by LukaszSJHS on 2009-08-03
The solution was that I had to ask permission to bypass the proxy.  Our hypothesize was that Linux cannot authenticate against this proxy because the proxy required a Windows authentication.   Perhaps there is a method of doing the authentication, but a username and password in the conf.apt file was insufficient.

---

### Post by rickbeton on 2009-09-29
If you have been given a proxy URL (i.e. [http://something/proxy.pac](http://something/proxy.pac)), this is all you need for your Gnome desktop and/or web browser.

But for APT you need to know the actual address of the proxy server. You can do this by inspecting the proxy.pac script: simply open its URL in your browser and view the file, which contains a Javascript function. Likewise for wpad.dat, try the URL [http://wpad/wpad.dat](http://wpad/wpad.dat) instead.

The function is explained on the Web (Google for FindProxyForURL) and you need to know the value the function returns when accessing the Web. When you have deciphered it, paste it into /etc/apt/apt.conf along with your proxy authentication credentials.

My /etc/apt/apt.conf looks like this:
[FONT="Courier New"]Acquire::http::proxy "http://myusername:mypassword@10.2.5.200:8080/";
Acquire::ftp::proxy "ftp://myusername:mypassword@10.2.5.200:8080/";
Acquire::https::proxy "https://myusername:mypassword@10.2.5.200:8080/";[/FONT]
Aptitude now works well.

What I'd like to know is how to make this more secure - it's far from ideal pasting my normal username and password into this text file.

---

