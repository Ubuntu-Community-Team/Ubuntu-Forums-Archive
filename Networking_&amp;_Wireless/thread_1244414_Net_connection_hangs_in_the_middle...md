---
title: "Net connection hangs in the middle.."
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2009-08-19
I am using broadband connection,and i configured my pppoe connection using "sudo pppoeconf" and for connecting i use "sudo pon dsl-provider" but sometimes my net connection stops in the middle..When i see my plog output,it shows me the following result...
karthick@karthick:~$ plog
Aug 19 21:39:39 karthick pppd[3696]: primary   DNS address 218.248.255.193
Aug 19 21:39:39 karthick pppd[3696]: secondary DNS address 218.248.240.79
Aug 19 21:41:58 karthick pppd[3875]: No response to 4 echo-requests
Aug 19 21:41:58 karthick pppd[3875]: Serial link appears to be disconnected.
Aug 19 21:41:58 karthick pppd[3875]: Connect time 5.0 minutes.
Aug 19 21:41:58 karthick pppd[3875]: Sent 44606 bytes, received 320589 bytes.
Aug 19 21:42:04 karthick pppd[3875]: Connection terminated.
Aug 19 21:42:04 karthick pppd[3875]: Modem hangup

Can someone fix this???

---

### Post by Bucky Ball on 2009-08-19
Have you got the correct DNS addresses and DNS setup correctly?

Try to give specific details of your exact setup. Dial-up? Router?

---

### Post by superprash2003 on 2009-08-19
BSNL dns servers are pretty bad , do try using opendns servers - 208.67.222.222 and 208.67.220.220

---

### Post by karthick87 on 2009-08-19
I think i haven't setup my DNS..How to setup DNS?

---

### Post by Bucky Ball on 2009-08-19
Try going to:

System->Admin->Network

You don't need to unlock. There is a tab called 'DNS'. They are the servers you are using in there. Copy those IPs (usually two) to where they need to go.

---

### Post by karthick87 on 2009-08-20
I cant find network in System>Administration..

---

### Post by Bucky Ball on 2009-08-20
Maybe try right clicking your network icon in the toolbar and manual configuration. I am on Xubuntu at the moment but think that is it. Just look for that DNS tab.

---

### Post by kixome on 2009-08-20
thats because they moved it to network connections under system>preferences and also the dns tab is not there

---

### Post by kixome on 2009-08-20
dont you just hate when they change things that work, I loved the general tab where you could change your hostname, but now you have to do via cli and it resets when you restart.

some things should be left alone, or just added to, but not take features away

---

### Post by karthick87 on 2009-08-20
When i open system>preferences>network connections i cant able to see anything in wired tab..Why?

---

### Post by kixome on 2009-08-20
did you check the dsl tab, maybe because your ethernet adapter is not configured or because it isn't what is being used to connect.

---

### Post by karthick87 on 2009-08-20
Yes i have checked my DSL Tab,but nothing found there..I use sudo pon dsl-provider to connect to the internet..

---

### Post by superprash2003 on 2009-08-24
check out this guide [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

