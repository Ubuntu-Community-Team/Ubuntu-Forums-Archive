---
title: "freeradius can't start debug mode radiusd -X"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by BudworthTDog on 2013-03-12
I'm going by the instructions on the freeradius website and they make a big hubbub about starting the server in debug mode while configuring it. I don't doubt this is necissary so I don't want to move on until I figure this step out. The Ubuntu spicific instructions leave mush to be desired but I consider myself smart enough, or at least determined enough, to fill in the Ubuntu specific blanks on my own.

I've looked all over the place and have found people that have had the same problem but it seems the threads always trickel off into something else, I dunno it's hard to explain. Point being I would like a nice simple and consise answer if anyone knows of one.

The instructions I am following can be found at [http://wiki.freeradius.org/guide/Basic-configuration-HOWTO](http://wiki.freeradius.org/guide/Basic-configuration-HOWTO) but in short it says I'm supposed to run the radiusd -X as root. When I do so I get this


```
root@xxx:/etc/freeradius# radiusd -X
The program 'radiusd' can be found in the following packages:
 * radiusd-livingston
 * yardradius
Try: apt-get install <selected package>
```

If I install those packages in uninstalls freeradius. I've tried everything. If it helps here is the contents of the freeradius folder

```
root@xxx:/etc/freeradius# ls
acct_users              attrs.access_reject        **[COLOR=#0000ff]certs[/COLOR]**         eap.conf           huntgroups    policy.conf     proxy.conf       **[COLOR=#0000ff]sites-enabled[/COLOR]**   templates.conf
attrs                   attrs.accounting_response  clients.conf  experimental.conf  ldap.attrmap  policy.txt      radiusd.conf     sql.conf        users
attrs.access_challenge  attrs.pre-proxy            dictionary    hints              **[COLOR=#0000ff]modules[/COLOR]**       preproxy_users  **[COLOR=#0000ff]sites-available[/COLOR]**  sqlippool.conf  users~



```

Highlited blue are files but I scouered them and cant find anything of use. I read the radiusd.conf file but really couldnt find anything defiantive in it other than the same old "be sure to run in radius debug radiusd -X" I already see listed everywhere.

Anyone got any idea what I'm going wrong?

---

