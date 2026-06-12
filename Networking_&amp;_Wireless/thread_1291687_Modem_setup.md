---
title: "Modem setup"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by Jestersage on 2009-10-15
Good news: I eceived my first technica support call, which will be good for my resume.
Bad news: It involves installing modem on a Ubuntu, which:
a) No idea what packages are installed
b) No idea what modem the guy was given. The guy in charge of the hardware gave my customer a set of modem cards; however, I do not know if they are compatible or even tested.

I am going to follow the instructions on [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto), since I do not know if GNOME-PPP is installed. The network is with VCN, which have documentation for Ubuntu (not Fedora :) ) at [http://www2.vcn.bc.ca/dial-up#set_up](http://www2.vcn.bc.ca/dial-up#set_up).

Are the any thing I have to watch out for? It is gonna be 8.04, btw.

---

### Post by sir_cheats_a_lot on 2009-10-15
I've no idea what you hope to accomplish without direct physical access, or at least a remote desktop connection to the machine in question.  if you are lucky one of the modems has a smart-link chip set or at least one compatible with the driver, or is an actual hardware modem.  not very many internal modems are. 
    best bet is to pop them in one at a time(or have them do it), and find out what modem is what through the lspci command.  after getting the result of lspci google the info, you may get lucky, and one will just work on /dev/modem; though it again is unlikely.

---

