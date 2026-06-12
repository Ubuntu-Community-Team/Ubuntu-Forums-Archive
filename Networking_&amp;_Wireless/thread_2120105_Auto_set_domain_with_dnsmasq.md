---
title: "Auto set domain with dnsmasq"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by ksteuber on 2013-02-25
I am currently trying to set up a router on an Ubuntu desktop machine. For the most part, I want it to behave much like my existing DD-WRT router.

Although most computers connect as expected, I have one laptop (Ubuntu) that stubbornly refuses to get a DNS server from the router. When I connect normally (to the DD-WRT router), /etc/resolve.conf contains:
```
nameserver 127.0.0.1
search [prefix removed].comcast.net

```
Strictly speaking, this is not what it should be doing. When I look at the DHCP ACK sent from the router to the client, it contains (among other things) these two options:
```
    Option: (t=6,l=4) Domain Name Server = 192.168.210.1
        Option: (6) Domain Name Server
        Length: 4
        Value: c0a8d201
    Option: (t=15,l=19) Domain Name = "[prefix removed].comcast.net"
        Option: (15) Domain Name
        Length: 19
        Value: [removed]
```
So really, it should be getting the router (192.168.210.1) as the DNS server, not Comcast. This, however, is not the problem I want to address. I am not particularly concerned with my laptop's behavior, what I really want is for any computer to connect without extra configuration, regardless of whether it handles the DNS as I would expect or not.

When I connect to the router I am building, no Domain Name is specified in the DHCP ACK. When connecting with the "problem laptop", resolve.conf contains only the line:
```
nameserver 127.0.0.1
```

I am using dnsmasq for the DNS and DHCP, which is the same program DD-WRT uses. I used ssh to access the DD-WRT router and discovered that its dnsmasq configuration file is stored in /tmp/dnsmasq.conf and contains:
```
interface=br0
resolv-file=/tmp/resolv.dnsmasq
all-servers
domain=[prefix removed].comcast.net.
dhcp-leasefile=/tmp/dnsmasq.leases
dhcp-lease-max=57
dhcp-option=lan,3,192.168.210.1
dhcp-authoritative
dhcp-range=lan,192.168.210.100,192.168.210.149,255.255.255.0,1440m
[dhcp-host statements removed]
stop-dns-rebind

```
So it seems that on the router, dnsmasq is somehow being configured to send that exact, literal domain name rather than dnsmasq determining what it should be. The resolv.conf on the router seems to be the same as it is when the "problem laptop" connects:
```
search [prefix removed].comcast.net.
nameserver 192.168.210.1

```

How can I configure dnsmasq to get the appropriate domain such that my "problem laptop" will connect properly? Do I want to make a script that runs at boot time that generates a dnsmasq.conf file in /tmp/ as it seems that maybe DD-WRT does? I would rather not just specify the literal domain name, causing me to have to change it when I connect the router to a different network.

---

### Post by ksteuber on 2013-03-08
bump? I feel like this shouldn't be a difficult issue but no one will even respond to this question anywhere I have posted.

Edit: Maybe I could edit /sbin/dhcpclient-script to update /etc/dnsmasq.conf when it receives a domain name? Am I on the right track?

---

### Post by SeijiSensei on 2013-03-08
Are you using isc-dhcp-server to handle DHCP requests?  If so, you can configure it to tell the clients what DNS server(s) to use.

Otherwise, you can edit /etc/dhcp/dhclient.conf and add the proper servers to the "prepend domain-name servers" directive then remove "domain-name servers" from the "request" directive.

---

### Post by ksteuber on 2013-03-09
That's the thing. I am using dnsmasq to handle DHCP requests. Since dnsmasq is configured to be used as the DNS server, it sends its own IP as the DNS server to its DHCP clients. I have confirmed with wireshark that dnsmasq is doing exactly this (also other computers use the router as the DNS as expected). However, my laptop is ignoring it. I really want the router to require no client computer configuration, so I want it to work as DD-WRT does: by sending the correct domain in addition to the DNS server. Since it seems that this functionality is not built in to dnsmasq, I think I need a way of modifying dnsmasq's configuration file when the domain changes. Since I am using dhclient3 to get the router's external IP address, and dhclient3 runs /sbin/dhcpclient-script and (I think) passes it information such as the domain, I though I could use this to call another script that could check if a new domain was sent and update /etc/dnsmasq.conf. Specifically, this section seems like it might set the "search" line of resolve.conf:
```
        if [ -n "$new_domain_search" ]; then
            if [ -n "$new_domain_name" ]; then
                domain_in_search_list=""
                for domain in $new_domain_search; do
                    if [ "$domain" = "${new_domain_name}" ] ||
                       [ "$domain" = "${new_domain_name}." ]; then
                        domain_in_search_list="Yes"
                    fi
                done
                if [ -z "$domain_in_search_list" ]; then
                    new_domain_search="$new_domain_name $new_domain_search"
                fi
            fi
            echo "search ${new_domain_search}"
        elif [ -n "$new_domain_name" ]; then
            echo "search ${new_domain_name}"
        fi
```

Since the domain name seems to be listed next to "search" in resolv.conf, I thought I could have this section call my script after the 'echo "search ${new_domain_name}" ' and 'echo "search ${new_domain_search}" ' line. Does this sound reasonable? Do you think this will cause any problems or get inaccurate information?

Edit: I feel like maybe I am only interested in the domain name, not the domain search. Does that sound right? Also, am I missing a better way to do this? I want to do this as cleanly as possible.

Edit: Actually, maybe I am only interested in the domain search, because this part of dhcpclient-script:
```
        {
        if [ -n "$new_domain_name" ]; then
            echo domain ${new_domain_name%% *}
        fi
```
seems to indicate that if the domain was being passed in by $new_domain_name, the line "domain [domain name]" would be added to resolv.conf, which it is not. Does this mean I want $new_domain_search?

---

### Post by SeijiSensei on 2013-03-09
> **ksteuber said:**
> That's the thing. I am using dnsmasq to handle DHCP requests.

I've never used anything other than isc-dhcp-server as a DHCP server.  Works like a charm.

---

### Post by ksteuber on 2013-03-09
Will it detect the domain seen by the DHCP client and pass it on to its own clients or do I have to enter one manually like with dnsmasq?

---

### Post by SeijiSensei on 2013-03-09
I'm having a hard time answering these questions since I don't use dnsmasq, and usually remove it from any Ubuntu systems these days.

The DHCP protocol lets the server send the client a wide array of information including the "domain search" list.  Clients can ignore or override the proferred information as you can see in the dhclient.conf "request" statement.  I suggest you take a look at the man page for [dhcpd.conf]("http://linux.die.net/man/5/dhcpd.conf") for more details.  The basic answer to your question is yes, you configure isc-dhcp-server by manually editing the dhcpd.conf configuration file and specifying the information you want to pass to the clients.

---

### Post by ksteuber on 2013-03-09
So the man page for dhcpd.conf indicates you can use '[COLOR=#000000]option domain-name "isc.org";' to indicate the domain name, but this is not the functionality I am looking for. I want it to pass the same domain-name that it received when it connected to my ISP with DHCP and I don't want to have to update this value manually when moving the router. I think that this is how a home router should behave, right? It seems to be how DD-WRT behaves. Is this behavior available in isc-dhcp-server? If it is I cannot figure out how to do it.

Edit: I would use any DHCP server that supports this functionality. I am not particularly attached to dnsmasq, I just want the router to send this information in a way that allows clients to work without any extra configuration. This includes clients like my weird laptop which I have not reconfigured to ignore the passed DNS server, it just does it anyways for some reason.[/COLOR]

---

### Post by SeijiSensei on 2013-03-10
So you want the clients behind the router to be in the "comcast.net" domain if the router is connected to Comcast?  Why?  Those machines are not actually in the comcast.net domain; they don't have legitimate host.comcast.net domain names; and, they are not reachable anyway.  Why does it matter what the ISP's domain is?

I'm sorry, I just don't understand why you want to do this.

---

### Post by ksteuber on 2013-03-10
As it is, the new router sends a DNS server but no domain in the DHCP responses. This makes a fair amount of sense to me, but my laptop is ignoring it. When I connect to DD-WRT, it still ignores the DNS passed, but adds "search [domain]" to resolv.conf, which makes the DNS work on the computer. I want any computer connected to the network to work with no extra configuration, like they do when connecting to DD-WRT. If there is a better way to solve this problem than the solution DD-WRT provides, please tell me and I will use it. 

Literally the only thing I want is for any computer, even misbehaving laptops like mine, to connect properly and be able to look up DNS information successfully without extra configuration. This would be easier for me to fix if I had any understanding of why this is my laptop's default behavior. Since I don't really understand, I am just trying to emulate DD-WRT's actions so that I can achieve DD-WRT's ease of use.

Edit: I am just sort of assuming it is the "search [domain]" line in resolv.conf that is making the DNS work since it is the only difference I can find between the working configuration and the non-working configuration. I am not exactly an expert in Linux DNS.

Edit: I have a dynamic DNS account. Could I specify my dynamic DNS address as the domain? I still am a little unclear on what the domain is even used for in this context. I only understand the part where it seems to change whether the DNS works. It seems though, that if I did that, it would contact the router for DNS queries like it is supposed to. Maybe?

Edit: Wait, none of this makes any sense. How can it be using a url for DNS? How can it resolve the URL without DNS? Am I completely wrong about my assumption that the one line in resolv.conf is making DNS work? If so, what is making DNS work?

---

### Post by SeijiSensei on 2013-03-10
The domain-search function applies a preset domain or domains to the end of hostnames to create a fully-qualified domain name.  So if you had "search example.com" in resolv.conf, then typed the command "ping freddy", the resolver would append "example.com" to "freddy" then look up the IP address for "freddy.example.com".  I don't see how that would have any relationship to the problems you're having.

---

### Post by ksteuber on 2013-03-10
Are there other files that affect how DNS is resolved? As I mentioned in my first post, the working configuration when connected to DD-WRT has these resolv.conf contents:
```
[LEFT][COLOR=#000000][FONT=Ubuntu Mono]nameserver 127.0.0.1
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]search [domain][/FONT][/COLOR][/LEFT]

```
If the "search" line only has to do with what domain name to append to unqualified host names, it would seem that this configuration file does not provide enough information for correct DNS operation. Is this correct? If this is the case, why does it work? Is there another configuration file that plays into this?

---

### Post by ksteuber on 2013-03-11
Hmm. Well I cannot figure out what I have changed, but it seems to be working now. I am extremely confused, but the laptop's DNS is clearly working, so I guess my problem is solved for now. I will post again if I can reproduce the problem again. Thank you for all your help SeijiSensei. Does this forum have a thanks button or something?

Also btw, I discovered that apparently that resolv.conf is not being used (or something) and DNS can be looked up with "nmcli dev list iface eth0 | grep IP4"

---

