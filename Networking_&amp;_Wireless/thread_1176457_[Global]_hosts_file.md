---
title: "[Global] hosts file?"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by ninuhadida on 2009-06-02
Hi guys,

currently i have several computers hooked up to my network.. and on my ubuntu server i configured the hosts file.. say;

192.168.1.100 ubuntu.server
192.168.1.101 ubuntu.desktop

.
.
.

etc

now obviously, this is limited to my server.. i mean if i go on my desktop (without configuring its hosts file) and use "ubuntu.server" i would not be able to connect.. i would have to configure each individual hosts file on each individual machine to reflect this, the one on my desktop, laptop, etc...

my question is, is there some way i can do this "globally".. like set a host file which reflects all my machines? I'm guessing this have to do with my router..

any help is greatly appreciate. i tried searching this but couldn't come up with any valid answers, mostly due to not knowing much about networking, i.e. not knowing the technical terms.

thanks!

---

### Post by DBrocks on 2009-06-02
Check this out:
[http://ubuntuforums.org/archive/index.php/t-1123006.html](http://ubuntuforums.org/archive/index.php/t-1123006.html)
I would recoment setting up a BIND9 server on your network. 
 
Here's a good tutorial:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
 
Good luck!!

---

### Post by Iowan on 2009-06-02
Before I replaced my dial-up router/firewall with a DSL modem, it was my network DNS server - running DNSMasq. By editing the **hosts** file there, it shared the information across the network.

---

### Post by ninuhadida on 2009-06-03
thanks for the input guys.

one question before i get going with this.. my network "topology" is like this..

modem -> router -> server | desktop | wifi devices

can it work with this? or to install the dns with bind i have to have something like this..

modem -> server -> router -> desktop | wifi devices | etc ?

excuse my ignorance, networks are not exactly my thing.

---

### Post by DBrocks on 2009-06-03
> one question before i get going with this.. my network "topology" is like this..

modem -> router -> server | desktop | wifi devices

Yes, this will work for you. On all your machines, however, you will have to set their DNS server to point to your server. 


> modem -> server -> router -> desktop | wifi devices | etc ?
This will also work, but it is slightly more difficult. You have to have two ethernet cards, and you would need to configure ip masquerading on your server. (Basically you would turn your server into your router). I have done this before, but it is certainly easier to take the first suggestion.

---

