---
title: "wpa_supplicant prevents harddisks from going to sleep"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by phyrexianhulk on 2009-09-17
Hi everyone,

i just set up a media fileserver using ubuntu on a ZOTAC ION D board. Everything workes fine except that i (approx. 5h ago) came to understand that the two harddisks are woken up every 30s and therefore cannot go to standby/sleep.

Using iotop with
```
iotop -o -d 10 -b
```i found out that wpa_supplicant spams the message
```
CTRL-EVENT-SCAN-RESULTS
```to /var/log/wpa_supplicant.log about every 30s.

So here is the thing: I do not need WIFI since my fileserver is directly connected to my router. This offers a few solutions for me (and probably lots more i did not think about :)):


[LIST]
[*]Disable WIFI connector in BIOS: Does not work since the ZOTAC bios will not let me do it.
[*]Disable WIFI in ubuntu: i did an ifconfig down, but wpa_supplicant keeps on spamming
[*]Uninstall wpa_supplicant: Oh my, unfortunately this would cause NetworkManager and ubuntu-desktop do be uninstalled. I do want to reside those on my server just in case i need a UI.
[*]Disable wpa_supplicant logging: Didn't find anything on the web about that.
[/LIST]
So, people, since i am neither a linux chief nor a guru you are my last hope of revelation :). What can i do to make my HDDs reside in standby/sleep?

Thanks in advance.

---

### Post by louigi600 on 2009-09-17
Yes wpa_supplicant writes status info to a file :

```
home@eng-prova:~$ ps -ef | grep wpa
root      2860     1  0 17:01 ?        00:00:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
home      4163  3835  0 17:20 pts/0    00:00:00 grep wpa
home@eng-prova:~$
```

-f /var/log/wpa_supplicant.log specifyes the location where that happens.

I'm not sure why you would want any desktop features on a file server .... but anyway:
this is the snag with the user friendly distro's .... if you do not have a button for it then it's going to be difficult ...

You could try workaround the problem by making the location of the logfile be on a tmpfs (ram filesystem) so that you will not be actually writing to disk ....
Ubuntu (and I think any distro using recent udev) has /dev already mounted in tmpfs ...
try changing the destination of the log file in /dev/something and you might be able to get away with it.

Disabling wpa_supplicant is going to be difficult ... I mean it's closely interlaced with the way ubuntu makes it easy to configure wireless links so disabling it will most likely fave impact on system utilities that configure network connections.

If this still makes you unhapy you are probabbly using the wrong distribution for your fileserver requirements :-D

---

### Post by phyrexianhulk on 2009-09-17
thanks for the info. i'll definitely give this a try.

however, here is the story: i wouldn't go so far to say that it all started with a big bang but i tried to install the ubuntu server distro with the result that my server freezed within the installer every time. 

the only (ubuntu) distro i was able to install was jaunty alternate desktop. so that's where i am stuck now. 

you are probably right. maybe i should go with another distro...

---

### Post by phyrexianhulk on 2009-09-19
Ok, here is what i did to stop wpa_supplicant from spamming my syslog:

I installed sysv-rc-conf with

```
sudo apt-get install sysv-rc-conf
```

and disabled the NetworkManager daemon, who is imho responsible for starting the wpa_supplicant annoyance. Together with mounting the harddrives with noatime i do not have any disk activity when my server is idle, now. \\:D/

I assume disabling the NetworkManager daemon is an absolute NO-GO for desktop systems, so be warned.

Coming back to wpa_supplicant: I think that even for a perfectly typical i-want-my-auto-config desktop system it is unwanted to hinder the harddrives from spinning down because wpa_supplicant feels the need to log its status messages to syslog. Even for a desktop i would want to leave my machine alone in the faith that it automatically reduces power consumption if there is no load. What say ye? :?:

---

