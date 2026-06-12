---
title: "Internet connection using Intrepid-&gt;BT-&gt;VZW LG Env"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by ReichhartKG on 2009-02-11
I used this page as a starting point:
[http://www.thinkdigit.com/forum/showthread.php?t=73530](http://www.thinkdigit.com/forum/showthread.php?t=73530)

It was close, but not quite right for my Ubuntu version and cell provider.

Here's the commands I used and the contents of the files I edited.  When I get it working with NetworkManager, I'll post those steps also.


root@althea:~# # these first two commands give you the <cell phone mac>
root@althea:~# # and <channel> you'll need later
root@althea:~# sdptool search DUN
root@althea:~# hcitool scan
root@althea:~# # these three files are cat'd below
root@althea:~# vi /etc/bluetooth/rfcomm.conf 
root@althea:~# vi /etc/ppp/peers/vzw
root@althea:~# vi /etc/chatscripts/vzw
root@althea:~# # the doc i linked to above says you need to restart to
root@althea:~# # create /dev/rfcomm0, but this will do it without
root@althea:~# # restarting
root@althea:~# sudo rfcomm bind /dev/rfcomm0 <cell phone mac> <channel>
root@althea:~# # now disconnect your current inet connection and try it
root@althea:~# pppd call vzw



root@althea:~# egrep -v '^$|^#' /etc/bluetooth/rfcomm.conf 
rfcomm0 {
bind yes;
device <cell phone mac>;
channel <channel>;
comment "vzw";
}


root@althea:~# egrep -v '^$|^#' /etc/ppp/peers/vzw 
/dev/rfcomm0 115200
connect "/usr/sbin/chat -v -f /etc/chatscripts/vzw"
crtscts
modem -detach
noccp
defaultroute
usepeerdns
noauth
ipcp-accept-remote
ipcp-accept-local
noipdefault


root@althea:~# egrep -v '^$|^#' /etc/chatscripts/vzw 
ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE' ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED
'' ATZ
OK-AT-OK "ATDT#777"
CONNECT \d\c

---

### Post by ReichhartKG on 2009-02-11
I forgot to mention that for the first two command to succeed, you have to have your phone paired already and set blurtooth discovery mode on the phone to "visible."

---

