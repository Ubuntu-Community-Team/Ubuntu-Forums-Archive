---
title: "NIS server keeps resetting domain name"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by cvp on 2009-03-30
I have a small cluster of Ubuntu machines, and I'm trying to set up NIS on 'em.
I followed this guide: [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

The master server is called x61s-nps, and the domain is test.domain. I followed the guide I linked to above to the letter, and none of the machines have anything out of the ordinary going on; they're updated vanilla installs of Ubuntu.

I can refer to the domain as many times as I like as test.domain, but every time I restart the NIS service, I see "Setting NIS domainname to: x61s-nps" (the name of my machine, instead of the test domain name I set up). All the other machines are trying to connect to test.domain but can't because my master server keeps changing the name to the wrong thing every time it starts.

My /var/yp has a test.domain directory, and it looks like it's ready to start serving that domain. There is no x61s-nps domain. That string means nothing except that it's the name of my machine, and it has nothing to do with any domain I've set up.

The only places 'x61s-nps' is mentioned that's relevant to nis:
```
root@x61s-nps:~# grep -Hn x61s /etc/yp* /etc/default/nis /var/yp/*
/etc/yp.conf:16:domain test.domain server x61s-nps
/var/yp/ypservers:1:x61s-nps
```

I've run '/usr/lib/yp/ypinit -m', I've restarted the service and the machine several times... none of it helps.
```
root@x61s-nps:~# domainname
x61s-nps
root@x61s-nps:~# domainname test.domain
root@x61s-nps:~# /etc/init.d/nis restart
 * Setting NIS domainname to: x61s-nps
 * Starting NIS services
 * binding to YP server...
 * ....
 * ....
 * ....
 * ....
 * ....
 * ....
 * ....
 * ....
 * ....
 * ....                                                 [fail]
                                                        [ OK ]
root@x61s-nps:~# cowsay I\'m going to punch a kitten.
 ______________________________
< I'm going to punch a kitten. >
 ------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

My patience is really starting to wear thin here... any suggestions would be very welcome.

Thanks!
-cvp

---

### Post by cvp on 2009-03-30
Found the problem.
In /etc/init.d/nis:
```
oname=`domainname`
nname=`cat /etc/defaultdomain`
if [ "$oname" != "$nname" ]; then
    log_action_msg "Setting NIS domainname to: $nname"
    domainname "$nname"
fi
```

'x61s-nps' was in /etc/defaultdomain. It'd be nice if this file was ever mentioned anywhere that talks about NIS.

---

