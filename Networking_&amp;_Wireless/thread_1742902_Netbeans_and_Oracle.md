---
title: "Netbeans and Oracle"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by potupaul on 2011-04-29
"Forgive me i am posting this in wrong section "

I have windows 7 as host and ubuntu 9 as guest on my vbox.
Netbeans is installed in ubuntu and oracle database is installed in win,
now i want connect both of these to do my development work...plz spotl8 on this,i have no idea how to achieve this...
if any1 require any kind of info plz let me know..

thnx
Ron

---

### Post by antikyte on 2011-05-03
I could be wrong as I haven't tried this, but I don't think your Ubuntu Guest is going to be able to see the database on your Windows host.
If you want to give it a go, you can always install the Oracle Client on Ubuntu then add the appropriate entry to the tnsnames.ora and see if that gets you anywhere ( or simply connect via the thin driver specifying the database location, port etc).
An alternative may be to get both NetBeans and Oracle installed on Ubuntu.
Oracle Express Edition can be installed on Ubuntu desktop.
Instructions on installing the Oracle Client can be found [here]("http://wp.me/pweWl-eO") .
Instructions on installing Oracle XE 10g on Ubuntu are [here]("http://wp.me/pweWl-2t") .

If none of this is helpful, maybe you could let us know which version of Oracle you are using ?

Mike

---

### Post by potupaul on 2011-05-03
thnx for ur reply
oracle n netbeans works fine on ubuntu 
but oracle on windows doesnt seems to connect witrh netbeans at ubu 
even after installing oracle client it gives the same error TNS:could not resolve the connect.......im using 10gxe and netbeans 7 and ubuntu 9

---

