---
title: "need to set  DNS"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by tonymax99 on 2009-05-17
hi,

having sorted my wireless connection, i need to set the DNS server in ubuntu 9.04.

my ISP has had me set this up manually in vista in wireless settings so i can connect to the internet, the router DNS did not work.

the server settings i have been given are in hex ie 212:135:1:36 and a secondary.

where would i put these values into ubuntu and how?? ithink it was the IPv4 setting i had to change, i can seethis in ubuntu, but its asking for something like 121.121.121.121 wher as i have : in between the numbers

thanks for any help from this ubuntu noob...

i have only seen ip settings for DNS not hex code

Tony):P

---

### Post by puppywhacker on 2009-05-17
put them in /etc/resolv.conf

In case this file seems to be overwrite everytime you restart, that could be caused by the dhcp client overwriting the values. To prevent that you can prepend values you receive over dhcp, by something you prefer

prepend domain-name-servers 212.135.1.36;
in the file
/etc/dhcp3/dhclient.conf

goodluck

---

### Post by tonymax99 on 2009-05-17
Hi, thanks 

tried usin gthe dhcp3 file but i do not have permission to save in that directory. any ideas on how to do this...

ubuntu is hard when you start out... ;-)


thanks

---

### Post by puppywhacker on 2009-05-17
I did a little bit of research and IPv4 212.135.1.36 is the DNS server of easynet in the uk. it's not hex, just normal decimals. The official separator should be a dot, but some tools may accept colons aswell.

In a terminal run an editor and add the nameserver to the resolv.conf file.
```
gksudo gedit /etc/resolv.conf
```

and make sur it contains this line
```
nameserver 212.135.1.36
```

---

### Post by tonymax99 on 2009-05-17
thanks puppywhacker... i called the isp, yes i can use . as well...

i still cannot get permission to save the file, any idea on how to do that..
appreciate all the help. overwhelmed with ubuntu at the moment, took me ages to install nvidia drivers...:D

---

### Post by tonymax99 on 2009-05-17
sorted..

getting my head around ubuntu... sudo is your friend....;)


thaks puppywhacker for your help, worked a treat.. 

and yes its ukonline...

---

### Post by puppywhacker on 2009-05-17
Ubuntu has a strict security policy. To change the file you need root (like administrator) access. In ubuntu you can execute commands with superpower by using sudo. by running the command
```
gksudo gedit
```
an editor should open with administrative power after you type your password.

In all fairness, I still remember my babysteps on linux, installing it and then have no clue what to do with it. The learning curve was steep, but it was definitely worth it =) so all the best to you.

---

### Post by tonymax99 on 2009-05-18
eh,

thanks again..

baby steps indeed.... fun working it all out tho...

any more resources i can look into??

have a great day and thanks for all the help



Tony:)

---

