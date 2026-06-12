---
title: "SquidGuard rewrite not working."
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by CyberAxe on 2011-03-22
Running Ubuntu Server 10.10

I am unable to successfully get rewrite working, i also can't find any documentation on it anywhere.

Here's my config, i've also tested it and there is not syntax errors, if i use Redirect in the ACL that works but Rewrite doesn't.

```
dbhome /var/lib/squidguard/db
logdir /var/log/squid

#------------
# Time Rules
#------------
# Abbreviation for Weekdays:
# s = sun, m = mon, t =tue, w = wed, h = thu, f = fri, a = sat

time workhours {
        weekly mtwh 09:00 - 12:30
        weekly mtwh 13:00 - 16:00
        weekly f 09:00 - 13:00
}

#---------------
# Rewrite Rules
#---------------

rew strictgoogle {
  s@safe=images@safe=strict@r
  s@safe=off@safe=strict@r
  s@(.*google..*)(/imghp\?)@\1&safe=strict@r
  s@(.*google..*)(.safe.off)@\1&safe=strict@r
  s@(.*google..*)(/images\?.*q=.*)@\1&safe=strict@r
  s@(.*google..*)(/groups\?.*q=.*)@\1&safe=strict@r
  s@(.*google..*)(/search\?.*q=.*)@\1&safe=strict@r
  s@(.*google..*)(/news\?.*q=.*)@\1&safe=strict@r
}

#------------------
# Source Addresses
#------------------

src admin {
  ip            192.168.0.5
  #user         root foo bar
  #within       workhours
}

src staff {
  ip 192.168.0.0-192.168.1.255
}

src clients {
  ip 192.168.2.0-192.168.255.255
}

#---------------------
# Destination Classes
#---------------------

#dest adult {
#       domainlist      adult/domains
#       urllist         adult/urls
#       expressionlist  adult/expressions
#}

acl {
  admin {
    pass none
    rewrite strictgoogle
#    redirect %strictgoogle
  }

#  staff {
#    pass any
#  }

  clients within workhours {
    pass none
    rewrite strictgoogle
  }

  default {
    pass none
#   redirect http://www.google.co.uk/
    #rewrite dmz
    #redirect http://admin.foo.bar.de/cgi-bin/squidGuard.cgi?clientaddr=%a+clientname=%n+clientident=%i+srcclass=%s+targetclass=%t+url=%u
  }
}
```

---

