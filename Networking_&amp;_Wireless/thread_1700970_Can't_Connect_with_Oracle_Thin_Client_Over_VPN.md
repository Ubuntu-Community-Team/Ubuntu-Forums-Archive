---
title: "Can't Connect with Oracle Thin Client Over VPN"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by 10GritSandpaper on 2011-03-05
I'm a developer and I'm new to Ubuntu (I wanted better memory performance than my windows gave me).  I really like it, but I go a really frustrating problem.  I cannot connect to my work's oracle DB over VPN from my home.  When I'm in the office I can connect fine.  I can even connect over VPN from our public "guest" wireless network, which does not provide access to our internal servers.

I'm using Cisco's AnyConnect VPN client, but I see the same behavior using openconnect.

I can ping and ssh to the server fine over VPN from home.

If I boot into windows, I can connect over VPN from home.

I think that it may be a problem with the way that I installed oracle instantclinet because I can't get sqlplus to work from work or home.  (I'm using Netbeans to test my connection)
```

/usr/lib/instantclient_11_2$ ./sqlplus
./sqlplus: error while loading shared libraries: libaio.so.1: cannot open shared object file: No such file or directory

```

I pretty much followed these [instructions]("http://geniusworldone.blogspot.com/2009/07/installing-oracle-instant-client-11.html") in setting it up.  I changed the env vars to:
```

export ORACLE_BASE="/usr/lib/instantclient_11_2"
export ORACLE_HOME="${ORACLE_BASE}"
export LD_LIBRARY_PATH="${ORACLE_BASE}"
export NLS_DATE_FORMAT="YYYYMMDD"
export NLS_LANG="AMERICAN_AMERICA.UTF8"
export TNS_ADMIN="/etc/oracle"
export SQLPATH="${ORACLE_BASE}"

```

---

### Post by 10GritSandpaper on 2011-03-05
OK, I made some progress and uncovered a new error.  I found the missing library in /lib32 now I get:
```

/usr/lib/instantclient_11_2$ ./sqlplus
./sqlplus: error while loading shared libraries: libaio.so.1: wrong ELF class: ELFCLASS32

```

I'm running Ubuntu 10.10 64bit.  Does this error mean that I have the 32 bit library installed?  If so, how is that possible?  I don't think I've ever touched the /lib32 directory.

Thanks, in advance for you help.

---

