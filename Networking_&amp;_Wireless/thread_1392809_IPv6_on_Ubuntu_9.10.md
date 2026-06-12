---
title: "IPv6 on Ubuntu 9.10?"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2010-01-28
Is Ubuntu 9.10 fully IPv6 ready? I notice that command line tools like ping and ssh are treating IPv6 addresses, both with and without the [] characters, as hostnames to be looked up via DNS. Is something else needed to enable IPv6, like special IPv6 versions of packages?

---

### Post by JackRock on 2010-01-28
Yes, 9.10 is IPv6 ready.  Head to System > Preferences > Network Connections and choose your network connection and click "Edit".  Last tab.

---

### Post by Skaperen on 2010-01-29
The interface is already configured with a local IPv6 address.  The problem is getting applications such as ping and ssh to understand IPv6.  Also, this is on Ubuntu Server, so I'm configuring with command lines (ifconfig for temporary changes, emacs of config files and scripts for persistent changes, apt-get for package upgrades and installs ... etc).

---

### Post by gombadi on 2010-01-29
> 
Is something else needed to enable IPv6, like special IPv6 versions of packages? 


I have found that most things just work with ipv6. There is ping6 and traceroute6 but I use mtr (apt-get install mtr-tiny). If I mtr to a server with both ipv6 and ipv4 dns entries then it picks ipv6.

> 
The problem is getting applications such as ping and ssh to understand IPv6


What sort of problems are you having. As above if I ssh to my server, which has both an A and AAAA dns record it connects to the ipv6 address no problems. Apache, lightppd, postfix may need a change to the config to listen on the ipv6 interface but that is about all the changes needed to have an ipv6 server running.

---

### Post by sanderj on 2010-01-29
> **Skaperen said:**
> Is Ubuntu 9.10 fully IPv6 ready? I notice that command line tools like ping and ssh are treating IPv6 addresses, both with and without the [] characters, as hostnames to be looked up via DNS. Is something else needed to enable IPv6, like special IPv6 versions of packages?

Yes, Ubuntu is IPv6 ready. 

If you want IPv6 connectivity to the outside world, use "sudo apt-get install miredo", and then visit [http://ipv6.google.com/](http://ipv6.google.com/)

HTH

---

### Post by Skaperen on 2010-02-01
I'm just wanting IPv6 within my LAN for now.  Any idea why none of these work?  It sure looks like they don't recognize that it is an IP (IPv6) address.```
euler/root/x1 /root 10# ping -n 'fe80::225:11ff:fe80:993c'
ping: unknown host fe80::225:11ff:fe80:993c
euler/root/x1 /root 11# ping -n '[fe80::225:11ff:fe80:993c]'
ping: unknown host [fe80::225:11ff:fe80:993c]
euler/root/x1 /root 12# ping6 -n 'fe80::225:11ff:fe80:993c'
connect: Invalid argument
euler/root/x1 /root 13# ping6 -n '[fe80::225:11ff:fe80:993c]'
unknown host
euler/root/x1 /root 14# ssh 'fe80::225:11ff:fe80:993c'
ssh: connect to host fe80::225:11ff:fe80:993c port 22: Invalid argument
euler/root/x1 /root 15# ssh '[fe80::225:11ff:fe80:993c]'
ssh: Could not resolve hostname [fe80::225:11ff:fe80:993c]: Name or service not known
euler/root/x1 /root 16# ssh -6 'fe80::225:11ff:fe80:993c'
ssh: connect to host fe80::225:11ff:fe80:993c port 22: Invalid argument
euler/root/x1 /root 17# ssh -6 '[fe80::225:11ff:fe80:993c]'
ssh: Could not resolve hostname [fe80::225:11ff:fe80:993c]: No address associated with hostname
euler/root/x1 /root 18# 
```

---

### Post by sanderj on 2010-02-01
Because it's not clear on which interface a fe80: address is, you have to specify the source interface. 

See below.



```

sander@athlon64:~$ ping6 -I eth0 fe80::21a:92ff:fe77:27ab
PING fe80::21a:92ff:fe77:27ab(fe80::21a:92ff:fe77:27ab) from fe80::21a:92ff:fe77:27ab eth0: 56 data bytes
64 bytes from fe80::21a:92ff:fe77:27ab: icmp_seq=1 ttl=64 time=0.060 ms
64 bytes from fe80::21a:92ff:fe77:27ab: icmp_seq=2 ttl=64 time=0.070 ms
^C
--- fe80::21a:92ff:fe77:27ab ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.060/0.065/0.070/0.005 ms
sander@athlon64:~$ ping6 ip6-localhost
PING ip6-localhost(localhost) 56 data bytes
64 bytes from localhost: icmp_seq=1 ttl=64 time=0.055 ms
64 bytes from localhost: icmp_seq=2 ttl=64 time=0.059 ms
^C
--- ip6-localhost ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.055/0.057/0.059/0.002 ms
sander@athlon64:~$ 
```

---

### Post by Skaperen on 2010-02-01
> **sanderj said:**
> Because it's not clear on which interface a fe80: address is, you have to specify the source interface. 

See below.
And how is this done with ssh?  How is this done with a web browser URL?  Or is this a problem specific to link-local addresses?

---

### Post by sanderj on 2010-02-01
Typing all those IPv6 addresses is cumbersome. On your LAN, avahi (zeroconf) can take of name resolution to local IPv6 addresses.

You only have change two lines in your configs. See [http://ipv6-or-no-ipv6.blogspot.com/2009/02/enabling-ipv6-support-in-avaha.html](http://ipv6-or-no-ipv6.blogspot.com/2009/02/enabling-ipv6-support-in-avaha.html)

Quote from that page:

```
make sure the /etc/avahi/avahi-daemon.conf file contains an active "use-ipv6=yes" line.

To enable m(ulticast)dns resolving of IPv6 addresses change the
"hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4"
line to
"hosts: files mdns_minimal [NOTFOUND=return] dns mdns"
in the /etc/nsswitch.conf file
```

After that, you will be in the IPv6 LAN Walhalla, and you can ping6 other Ubuntu (9.04+) machines on your LAN just by their <hostname> followed by ".local." (note the leading AND trailing dot):

```

sander@athlon64:~$ ping6 quirinius.local.
PING quirinius.local.(quirinius.local) 56 data bytes
64 bytes from quirinius.local: icmp_seq=1 ttl=64 time=12.0 ms
64 bytes from quirinius.local: icmp_seq=2 ttl=64 time=2.71 ms
64 bytes from quirinius.local: icmp_seq=3 ttl=64 time=3.16 ms
64 bytes from quirinius.local: icmp_seq=4 ttl=64 time=2.87 ms
^C
--- quirinius.local. ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3016ms
rtt min/avg/max/mdev = 2.716/5.202/12.045/3.954 ms
sander@athlon64:~$ 

```

---

### Post by Skaperen on 2010-02-01
If I need to specify which interface to source from (under the theory that my target IP address could be present in duplicate on more than one link), how is it that giving the target a hostname avoids the need to know the interface?  Is is that somehow included in a modified named lookup?

It seems link-local's semantics are too different in IPv6 to use it like I did in IPv4, and I should just exclusively go with a Unique Local Address.

---

### Post by Skaperen on 2010-02-01
It's working fine with a random Unique Local Address (see RFC4193).

---

### Post by sanderj on 2010-02-01
> **Skaperen said:**
> It's working fine with a random Unique Local Address (see RFC4193).

Did you activate RFC4193 IPv6 addresses on Ubuntu? If so, how?

---

### Post by Skaperen on 2010-02-02
> **sanderj said:**
> Did you activate RFC4193 IPv6 addresses on Ubuntu? If so, how?
Yes, I did. I wrote a couple scripts. One went in /etc/init.d and had /etc/rc[0-6].d symlinks to make it run very early, before any network daemons. That script ran the other, which was placed in /etc/network. In addition to configuring various IP aliases (v4 or v6), it also configures an RFC4193 Unique Local Address using a pre-determined and coded ULA prefix set in an environment variable named "ULA", and the following wide line of code:```
ifconfig | awk '{if(substr($0,1,1)!=" ")i=$1;if($1=="inet6"&&$2=="addr:"&&substr($3,1,6)=="fe80::"&&$4=="Scope:Link")printf "ifconfig %s add %s:%s\n",i,ENVIRON["ULA"],substr($3,7);}' | sh
```

I should recode this so the ULA prefix is obtained from a specific file like maybe "/etc/network/inet6_ula_prefix" and go from there. Then I can give away my script.

---

### Post by sanderj on 2010-02-02
Cool! Here's the output on my system (without actually running it through /bin/sh):

```
sander@quirinius:~$ ifconfig | awk '{if(substr($0,1,1)!=" ")i=$1;if($1=="inet6"&&$2=="addr:"&&substr($3,1,6)=="fe80::"&&$4=="Scope:Link")printf "ifconfig %s add %s:%s\n",i,ENVIRON["ULA"],substr($3,7);}'
ifconfig teredo add :ffff:ffff:ffff/64
ifconfig wlan1 add :224:2cff:fe6a:54ab/64
sander@quirinius:~$ 

```

(I've not defined ULA)

Let me check: you want to use IPv6 locally, but not the fe80:addresses, right? 
If you want to assign local addresses so that you don't have to specify the interface, you could also run 'radvd' on one system, with the RFC4193 prefix.


BTW: did you follow my advice on activating zeroconf with IPv6? That's very handy.

---

### Post by Skaperen on 2010-02-02
Well, I did want to use the fe80::/64 addresses. But they were not being handled in the expected way via applications like ping and ssh. When it was pointed out that ping6 worked, but needed the interface designation, I realized that assumptions were being made about the fe80 addresses that could be problematic for ordinary usage. So I chose to use the fc00:/7 (or more specifically the fd00:/8 part of it) addresses.

This might be better, since we may be installing routers at some point. I wanted to be sure everything would work autonomously first (which is why I first tried the link-local addresses). Later I might do router announcements (thanks for the reference to "radvd" ... didn't know that was there) to test that aspect to be sure everything handles it so it all works when a real router might do IPv6.

I generated an RFC4193 prefix via sha256 and registered it with [http://www.sixxs.net/tools/grh/ula/](http://www.sixxs.net/tools/grh/ula/)

I did not follow your advice that referred to miredo, because at this point in time, I do not have an interest in reaching the outside IPv6 world. I'm only doing setups so that I can test that all our internal network components and servers can do IPv6 for when that might be needed (which might be a VPN to a client before the public net).

Here is the script I'm using now:```
#!/bin/bash
#---------------------------------------------------------------------------------------------------
# file:         /etc/network/aliases-up
# purpose:      Configure alias IP addresses for all interfaces
# reads:        /etc/network/aliases is a sequence of ipv4alias or ipv6alias commands
#               /etc/network/inet6_ula_prefix is 10 hexadecimal digits only
#               /etc/network/inet6_ula_subnet is 1-4 hexadecimal digits only
#---------------------------------------------------------------------------------------------------
# license:      GPLv2
# author:       Phil Howard
# email:        echo cGhpbC5kLmhvd2FyZEBnbWFpbC5jb20K | mimencode -u
#---------------------------------------------------------------------------------------------------

#-----------------------------------------------------------------------------
# Add an IPv4 alias address to a specified interface.
#-----------------------------------------------------------------------------
# We should be able to just do "ifconfig <iface> add" but it does not work
# reliably for IPv4.
#-----------------------------------------------------------------------------
ipv4alias() {
        iface="${1}"
        shift
        addrp="${1}"
        shift
        ifopt=( "$@" )

        #------------------------------------------------------------------
        # Split address/prefix.
        #------------------------------------------------------------------
        addr=$( dirname "${addrp}" )
        pref=$( basename "${addrp}" )

        #------------------------------------------------------------------
        # If a prefix length is not given, make a default assumption.
        #------------------------------------------------------------------
        if [[ "${addr}" = "." ]] ; then
                addr="${pref}"
                case "x${addr}" in
                        ( x10.* | x44.* )                                       pref=8 ;;
                        ( x172.1[6-9].* | x172.2[0-9].* | x172.3[01].* )        pref=16 ;;
                        ( x192.168.* )                                          pref=24 ;;
                        ( * )
                                echo "Bad IPv4 alias needs a prefix length: '${addrp}'" 1>&2
                                return 1
                                ;;
                esac
        fi

        #------------------------------------------------------------------
        # Translate a prefix to a netmask.
        #------------------------------------------------------------------
        case "x${pref}" in
                ( x30 ) netmask=255.255.255.252 ;;
                ( x29 ) netmask=255.255.255.248 ;;
                ( x28 ) netmask=255.255.255.240 ;;
                ( x27 ) netmask=255.255.255.224 ;;
                ( x26 ) netmask=255.255.255.192 ;;
                ( x25 ) netmask=255.255.255.128 ;;
                ( x24 ) netmask=255.255.255.0   ;;
                ( x23 ) netmask=255.255.254.0   ;;
                ( x22 ) netmask=255.255.252.0   ;;
                ( x21 ) netmask=255.255.248.0   ;;
                ( x20 ) netmask=255.255.240.0   ;;
                ( x19 ) netmask=255.255.224.0   ;;
                ( x18 ) netmask=255.255.192.0   ;;
                ( x17 ) netmask=255.255.128.0   ;;
                ( x16 ) netmask=255.255.0.0     ;;
                ( x15 ) netmask=255.254.0.0     ;;
                ( x14 ) netmask=255.252.0.0     ;;
                ( x13 ) netmask=255.248.0.0     ;;
                ( x12 ) netmask=255.240.0.0     ;;
                ( x11 ) netmask=255.224.0.0     ;;
                ( x10 ) netmask=255.192.0.0     ;;
                ( x9 )  netmask=255.128.0.0     ;;
                ( x8 )  netmask=255.0.0.0       ;;
                ( * )   echo "Unusable IPv4 CIDR subnet prefix length '${pref}' in '${addrp}'" 1>&2 ; return 1 ;;
        esac

        #------------------------------------------------------------------
        # Do this with sequenced secondary interfaces.
        #------------------------------------------------------------------
        eval 'num=${num'"${iface}"'}'
        cmd=( ifconfig "${iface}:${num}" "${addr}" netmask "${netmask}" "${ifopt[@]}" )
        echo "Configuring IPv4 address on ${iface} as ${addrp} with" "${cmd[@]}"
        "${cmd[@]}"
        cs=$?
        eval 'num'"${iface}"'=$((num+1))'
        return $cs
}

#-----------------------------------------------------------------------------
# Add an IPv6 alias address to a specified interface.
#-----------------------------------------------------------------------------
# We can do "ifconfig <iface> add" with IPv6.
#-----------------------------------------------------------------------------
ipv6alias() {
        iface="${1}"
        shift
        addrp="${1}"
        shift
        ifopt=( "$@" )
        cmd=( ifconfig "${iface}" add "${addrp}" "${ifopt[@]}" )
        echo "Configuring IPv6 address on ${iface} as ${addrp} with" "${cmd[@]}"
        "${cmd[@]}"
        return $?
}

#-----------------------------------------------------------------------------
# Initialize sequence counter variables for each physical interface.
#-----------------------------------------------------------------------------
ifaces=( $( ifconfig -a | awk '{if(substr($0,1,1)!=" ")print $1;}' | fgrep -v : ) )
for iface in "${ifaces[@]}" ; do
        eval 'num'"${iface}"'=0'
done

#-----------------------------------------------------------------------------
# Generate IPv6 Unique Local Address (RFC 4193) for this host.
#-----------------------------------------------------------------------------
if [[ -f /etc/network/inet6_ula_prefix && -r /etc/network/inet6_ula_prefix ]] ; then
        prefix=$( cat /etc/network/inet6_ula_prefix )
        subnet='0000'
        if [[ -f /etc/network/inet6_ula_subnet && -r /etc/network/inet6_ula_subnet ]] ; then
                subnet=$( cat /etc/network/inet6_ula_subnet )
        fi
        export ULA="${prefix:0:2}:${prefix:2:4}:${prefix:6:4}:${subnet}"
        ifconfig | awk '{if(substr($0,1,1)!=" ")i=$1;if($1=="inet6"&&$2=="addr:"&&substr($3,1,6)=="fe80::"&&$4=="Scope:Link")printf "ifconfig %s add fd%s:%s\n",i,ENVIRON["ULA"],substr($3,7);}' | sh
fi

#-----------------------------------------------------------------------------
# Process the aliases file, which makes calls to ipv4alias or ipv6alias.
#-----------------------------------------------------------------------------
if [[ -f /etc/network/aliases && -r /etc/network/aliases ]] ; then
        source /etc/network/aliases
fi
```It also does my IP aliasing.

---

