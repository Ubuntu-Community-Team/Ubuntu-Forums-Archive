---
title: "Blackberry Tethering Question, So Close"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by warchief_ryan on 2009-12-14
I've been looking at a lot of info on tethering and think I am close to getting it to work but I keep running into this one error, 

```
pppd: In file /etc/ppp/peers/uscellular: unrecognized option '/usr/sbin/chat -f /bbtether/conf/uscellular-chat.conf'
```

I'm not sure how to change or what the correct way to put it would be so that pppd can understand, any suggestions? Would I have to call on "chat" and give it the chat conf in another way?




Here is the uscellular conf and chat files I've found and am using. All I edited was my conf/chat file locations and username/password.

```
# berry4all script and settings -- US Cellular
# by P.K. Carlisle 2009-11-03
# Tested and working on U.S. Cellular with a Blackberry 8330 Curve
# Please update login & password
230400
noipdefault
defaultroute
#nomultilink
ipcp-restart 7
ipcp-accept-local
ipcp-accept-remote
lcp-echo-interval 0
lcp-echo-failure 999
nopcomp
noaccomp
pap-timeout 20
pap-restart 20
lcp-restart 10
nomagic
noccp
#noauth
crtscts
usepeerdns
novj
# does not exist in all pppd versions (osx)
#replacedefaultroute
#US Cellular will supply the user login nnnnnnnnnn
#user nnnnnnnnnn@uscc.net
user xxxx
#US Cellular will supply the user password nnnnnnnnnn
#password nnnnnnnnnn
password xxxx
#uncomment this command for test mode only
#dryrun
connect "/usr/sbin/chat -f /bbtether/conf/uscellular-chat.conf"
```

```
# berry4all script and settings -- US Cellular
# by P.K. Carlisle 2009-11-03
# Tested and working on U.S. Cellular with a Blackberry 8330 Curve
'' 'BBT_OS'
'' 'AT&F'
OK 'ATZ'
OK 'ATI'
SAY 'Dialing...\n'
OK 'ATDT#777'
CONNECT
# Without ~p it does NOT continue past CONNECT
~p
```

---

