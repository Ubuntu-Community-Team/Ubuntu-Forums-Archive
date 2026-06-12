---
title: "configuring network for WINS"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by AQ80 on 2009-05-14
Hi All,

Sorry if it's a newbie question.

I'm trying to switch my office PC from win XP   to ubuntu , but for the network to connect to the internet I have to configure two WINS IPs , that is beside the other settings of course such as IP, subnet mask, DNS and etc...

the problem is that I know how to set it in windows but not in Linux. All help is appreciated but a GUI way is preferred.

this is a link to the photo below exactly like my situation except I have two WINS IPs
[U][http://it.cas.psu.edu/Training/HowTo/images/LANconnections9.jpg](http://it.cas.psu.edu/Training/HowTo/images/LANconnections9.jpg)

[IMG]http://it.cas.psu.edu/Training/HowTo/images/LANconnections9.jpg[/IMG]
[/U]
  
thank you

---

### Post by sahabcse on 2009-05-14
For networking set-up pls follow below url

[http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html](http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html)

---

### Post by Peter09 on 2009-05-14
Does this thread resolve your question?

[http://www.linuxquestions.org/questions/linux-networking-3/setting-up-wins-on-ubuntu-450401/](http://www.linuxquestions.org/questions/linux-networking-3/setting-up-wins-on-ubuntu-450401/)

---

### Post by AQ80 on 2009-05-14
thanks guys,

but not exactly to my point.

upon farther search I found out that what I need is to enable my pc to be a WINS client by modifing smb.conf file at
;   wins server = w.x.y.z


but I'm still wondering about: 
-the 2nd WINS IP , is it possible just to repeate the line above for th 2nd IP
-and what about the name resolve order what should it be
-and what about connecting to a different networks do I have to modify that file every time I change the network

thank you all

---

### Post by Iowan on 2009-05-14
Hmmm... > It is strongly recommended to set up only one WINS server. [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2576893]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2576893")
Otherwise... on other services, multiples might be separated by a space or comma or on separate lines.

---

### Post by AQ80 on 2009-05-15
> **Iowan said:**
> 

    Quote:
It is strongly recommended to set up only one WINS server.                       

I have seen this recommendation before but that is the configuration at my office 

anyway I'm back to the office on Monday so I'll give a feed back on how it goes then.

thank you all

---

### Post by AQ80 on 2009-05-28
[CENTER][SIZE=5]hi all
sorry for taking so long to post back but went by other problems (needed to configure system proxy) and fixed them all
now I'm logging from my work computer and all is fine

thank you all for the help
[/SIZE][/CENTER]

---

