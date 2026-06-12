---
title: "Creating a whitelist?"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by Ryzol on 2010-10-08
Is there a way to block the entire internet except for a few sites that I have manually added? I waste way too much time on the internet. Normally I would throw away my computer, but I have to use it for my work.

---

### Post by gzarkadas on 2010-10-10
You can use the following steps to create a whitelist. The process is a bit involved but allows to expand and easily maintain the whitelist up to the order of thousands of entries.

1. Create a file listing your white-listed websites (see example). Name it as you whish (example name: /usr/local/etc/whitelist - requires to run `[gk]sudo your-editor'). 

Note that you must insert there all other sites that your sites use. For example ubuntuforums.org uses yui.yahooapis.com. An easy way to find needed sites is to load your target site in your browser and see at the browser's status bar which url it waits indefinitely (or, if the reject scheme below is used, for some time). Add this to your whitelist, update the ipset (see below) and refresh the page until it loads ok.

Sample whitelist:
```

ubuntuforums.org
yui.yahooapis.com
www.gnu.org
www.fsf.org
static.fsf.org
www.wikipedia.org
upload.wikimedia.org
bits.wikimedia.org
www.tldp.org
www.google.com

```2. Issue `dig' to get the ip addresses of the sites, followed by `grep' to clean output from host names:

```

dig +short -f /usr/local/etc/whitelist | grep '^[0-9.]*$' > /tmp/iplist

```3. Run `ipset' to create an IP hash set from the ip addresses; this is to save using a bunch of iptables rules and also to apply the rules more efficiently if the list grows large. Another nice feature is that once you have set-up your iptables rules to use set(s), you only need to change the set(s) to modify your whitelist.

To do this you have first to build ipset module from source with module-assistant (this has been tested on Karmic 9.10):

```

sudo -i
apt-get install ipset ipset_source
module-assistant prepare
module-assistant build ipset
# check output to verify there are no errors
module-assistant install ipset
exit

```Now you are ready to create your ip set:

```

sudo -i
ipset --create whitelist iphash
while read ip ; do ipset -A whitelist $ip ; done < /tmp/iplist
exit

```4. Run `iptables' to drop by default all outgoing packets (by setting policy) and add only one rule for the ipset and a few more rules for your DNS to work. I include the rules for my network setup (DNS server is my router and avahi is on port 5353); yours may be different, so you will have to tweak a little. To be sure it will work, flush existing rules just before of this.

```

sudo -i
iptables -F OUTPUT
iptables -P OUTPUT DROP
iptables -A OUTPUT -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT
iptables -A OUTPUT -p udp -d 192.168.1.254 --dport 53 -J ACCEPT
iptables -A OUTPUT --match set --match-set whitelist dst -j ACCEPT
exit

```An alternative setup, that uses REJECT messages to make browser more responsive on failures is:
```

sudo -i
iptables -F OUTPUT
iptables -P OUTPUT DROP
iptables -A OUTPUT -p icmp -j ACCEPT 
iptables -A OUTPUT -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT
iptables -A OUTPUT -p udp -d 192.168.1.254 --dport 53 -J ACCEPT
iptables -A OUTPUT --match set --match-set whitelist dst -j ACCEPT
iptables -A OUTPUT -j REJECT --reject-with icmp-port-unreachable
exit

```You may want to add a -j LOG rule (as last or just before the -j REJECT, depending on the setup chosen) to test things before deploying them as permanent. Then use a `tail -f /var/log/messages' in a terminal. Watch the terminal's output as you use your browser, to identify possible blocking of connections that you want to keep. If this is the case, put appropriate -j ACCEPT rules in your OUTPUT chain.

5. Automate all of this to load at startup. This depend on your preferences and your fire-walling software, so I will just give some generic hints:
[INDENT]a. You need to recreate the ipset at startup. Use the two lines above to make a startup script that will execute just before your firewall.
[/INDENT][INDENT]b. You should create an executable script (with the #!/bin/sh line and the dig... line) in /usr/local/bin to refresh the contents of the ips on demand. This is to ease the whitelist administration; not a necessity. Name it as you wish.
[/INDENT][INDENT]c.1. If you prefer to not perform a bunch of DNS queries at boot time, put the files with the IPs (/tmp/iplist) in a permanent location; I recommend /usr/local/etc/whitelist-ip. Then you just manually refresh it whenever it seems fit.
[/INDENT][INDENT]c.2. If you want to perform the DNS queries at boot time (to be sure ips are always current), then you can use a temporary file and your startup script could then just call the update script in b) above and the update ipset code in a) in one step.
[/INDENT][INDENT]d. You need (of course) to modify your firewall so that it loads the rules above for the OUTPUT chain. Alternatively you can make another startup script that will run after your firewall and will contain the above (tweaked for your case) iptables commands.
[/INDENT]

---

### Post by phuonghanu on 2011-03-17
Dear gzarkadas,

I've read ur reply about creatin whitelist. I see that it just can be applied for such known domains. 

here is my post on ubuntu4rum:

[http://ubuntuforums.org/showthread.php?p=10569382#post10569382](http://ubuntuforums.org/showthread.php?p=10569382#post10569382)

hope to see ur help asap ^^

best regards

---

