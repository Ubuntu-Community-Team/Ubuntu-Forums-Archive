---
title: "dialling up"
date: 2005-01-30
forum: Networking &amp; Wireless
---

### Post by contra on 2005-01-30
For a newbie to Linux and Ubuntu how do I get on the internet. I have the modem selected in the network panel and when I click activate it dials up but then it disconnects after a while and meanwhile I can't browse.?

---

### Post by m4ng0 on 2005-01-30
Open a terminal, type:
sudo tail -f /var/log/messages
then try to dial up and see what comes from the terminal. It should help if there are problems.

---

### Post by contra on 2005-01-30
did what you said and this is the result:

ppp generic driver version 2.4.2
pppd 2.4.2 started by root, uid 0
serial connection established
Using interface ppp0
Connect: ppp0<--->/dev/ttyS1
LCP terminated by peer
Hangup (SIGHUP)
Modem hangup
Connection terminated
terminating on signal 15
Exit

---

### Post by m4ng0 on 2005-01-30
From pppd man page:
> EXIT STATUS
...
    15     The link was terminated because the peer is  not  responding  to
           echo requests.


Try this:
sudo pppconfig
name the connection, insert all the requested informations and double check they are correct.
Then type:
sudo pon connection_name
where "connection_name" is the name you previously chose.
To disconnect:
sudo poff.
If everything works fine, you can add your user to "dip" group, so you can call pon and poff without sudo (you can use Modem Lights applet too).

---

### Post by contra on 2005-01-31
[QUOTE=m4ng0]From pppd man page:


Try this:
sudo pppconfig
name the connection, insert all the requested informations and double check they are correct.
Then type:
sudo pon connection_name
where "connection_name" is the name you previously chose.
To disconnect:
sudo poff.
If everything works fine, you can add your user to "dip" group, so you can call pon and poff without sudo (you can use Modem Lights applet too).[/QUOTE]


Still get the same reply  "LCP terminated by peer"???

---

### Post by m4ng0 on 2005-01-31
LCP means Link Control Protocol,  so it seems a problem in the remote server.
You can try to add
lcp-max-configure 30
to /etc/ppp/options
and, if problems still occur, add also
debug
and check the logs again...

---

### Post by jllitvay on 2005-04-01
I have the same problem with my USR2976. Find it, dial, make noise, but do not connect. :-| 
seems the pppd is not sending or answer the provider properly.

---

