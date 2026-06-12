---
title: "setting socks proxy in terminal?"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by goof on 2013-03-20
hi sorry not sure if im in the right section here new to ubuntu, i am trying to make a batch file to launch an application through a socks proxy but cant find any info on how to set a system wide SOCKSproxy in a terminal does anyone know how to do this or know of a workaround would appreciate any help as i have looked everywhere thanks

---

### Post by schragge on 2013-03-20
Are you sure you really need to set a *system wide* proxy in order to launch an application? How are you trying to launch it? With ssh? [~/.ssh/config]("http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html") has an option *ProxyCommand*. I guess you can put [netcat]("http://manpages.ubuntu.com/manpages/precise/man1/nc_openbsd.1.html") or [socat]("http://manpages.ubuntu.com/manpages/precise/en/man1/socat.1.html") command in there.

---

### Post by goof on 2013-03-20
i was looking at ssh but cant find a good tut anywhere and when i try to stumboloe hrough it i just keep getting ssh options printed in terminal and although i dont need system wide settings this feture being builth in to ubuntu i tought i might be able to launch it with settings which has been the main  focus  so far surly there is just a bunc of commands i can feed into a terminal to achieve this my brain is just melted at this stage benn stuck on this for 2-3days aaaargh:)

---

### Post by goof on 2013-03-20
k typicall when i post the question i find the answer to set system proxy from terminal in 12.04 you type
[INDENT]gsettings set org.gnome.system.proxy.socks host '192.168.1.1&#8242;
gsettings set org.gnome.system.proxy.socks port 8080
gsettings set org.gnome.system.proxy mode ‘manual'
[/INDENT] **          Disable proxy setting from terminal in ubuntu 12.04**

 [INDENT]gsettings set org.gnome.system.proxy mode ‘none'

but this doesint work for 1210 i dont get error but when i launch the browser its dead nothing loads no bytes packets r bits not even a nibble get through 
i am using tor as localhost for testing. tor is working fine as i can use it thrugh foxyproxy

anyone know how i can get this to work?? t
thanks

[/INDENT]

---

