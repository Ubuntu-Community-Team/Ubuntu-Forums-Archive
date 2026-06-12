---
title: "Switching proxy using shell script"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by hari.iiitb on 2010-10-07
Hi, can you please advise me how to do this?

Hi,

Is it possible to manipulate the selection of network proxy through shell script?

[IMG]http://i53.tinypic.com/9tigy9.png[/IMG]

to 

[IMG]http://i56.tinypic.com/j14y38.png[/IMG]

How to change the selection of "Default" to "Something" through shell script? What I am trying to say is, I have created a new location called "Something" with HTTP Proxy as proxy and port as 8080. If I am at my home, I use "Default". If I goto my college, I should change it to "something". How to do this via shell script?

---

### Post by hari.iiitb on 2010-10-07
Solved it myself :-)


if [ $# -eq 0 ] 
then 
echo "$0 : You must give/supply one integers" 
exit 1 
fi 
 
if test $1 -eq 1 
then 
gconftool-2 --type string --set /system/proxy/mode manual 
gconftool-2 --type boolean --set /system/http_proxy/use_http_proxy true 
gconftool-2 --type string --set /system/http_proxy/host proxy 
gconftool-2 --type integer --set /system/http_proxy/port 8080 
gconftool-2 --type boolean --set /system/http_proxy/use_same_proxy true 
else 
gconftool-2 --type string --set /system/proxy/mode none 
fi

---

