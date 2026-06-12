---
title: "/etc/hosts"
date: 2008-11-02
forum: Mythbuntu
---

### Post by axelsvag on 2008-11-02
I got mythbuntu 8.04 on an amd 64 bit.

After the last update I had to reboot to make the changes take effect. Aftera while in the boot process a message came up suggesting that somethins is wrong . It said something about that my /etc/hosts that was not alright. "could not find internetadress for myusername-mythtv it is possble that.... "I had two alternatives 1. keep going 2. keep going. Yes the same text in both alternatives. If I tried the one to the right nothing happened and when I tried the one at the left everything went on fine and mythtv starts.

There is one suggestion in the text the I should add myusername-mythtv in a file called /etc/hosts.

When I look in that file I can find myusernam-mythtv with an adress like 127.0.1.1. What can I do to make the machine boot normally again

---

### Post by ian dobson on 2008-11-02
Hi,

What does your hosts file look like exactly.

Heres mine:-

```

127.0.0.1       localhost                     alpha2
127.0.1.1       alpha2.planet-ian.com         alpha2
192.168.0.1     planet-ian.com                alpha2
192.168.0.2     planet-ian.com                alpha2
192.168.0.3     myth-frontend.planet-ian.com  myth-frontend
192.168.0.55    avr-router.planet-ian.com     avr-router
192.168.0.5     portable.planet-ian.com       portable
192.168.0.6     blue-water.planet-ian.com     blue-water
192.168.0.7     blue-water2.planet-ian.com    blue-water2
192.168.0.254   router.planet-ian.com         router

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

The format of the hosts file is:-
"IP Address"  "Full Host Name"  "Short Name"

Note alpha2 is my main server and it have 2 seperate IP addresses.

Regards
Ian Dobson

---

### Post by axelsvag on 2008-11-02
This is my /etc/hosts
```
127.0.0.1 localhost
127.0.1.1 myusername-mythtv.Arbetsgrupp

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```




and this is my /etc/resolv.conf

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5258
#
### END INFO



nameserver 192.168.0.1
```

---

### Post by ian dobson on 2008-11-02
Hi,

Try adding your host name as ip 127.0.0.1 to hosts, something like:-

127.0.0.1 myusername-mythtv.Arbetsgrupp  ServerName

Regards
Ian Dobson

---

### Post by axelsvag on 2008-11-02
OK But what server name should I use. Has it something to do with the mythbuntu computer or the router. Where did your server name come from.

---

### Post by axelsvag on 2008-11-02
Could there be any log file that show what went wrong during startup?

---

### Post by ian dobson on 2008-11-02
Hi,

If you go to the terminal and type hostname you'll see the name of your system

Regards
Ian Dobson

---

### Post by axelsvag on 2008-11-02
Ok I found it. And now I put it in the etc/hosts after "username-mythtv.Arbetsgrupp" and reboot or??

---

### Post by ian dobson on 2008-11-02
YES, that should do it.

Regards
Ian Dobson

---

### Post by axelsvag on 2008-11-03
OK I will try that after my wife allow me to reboot.

---

