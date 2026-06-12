---
title: "Saving public IP address to variable or file"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by ChrisRChamberlain on 2010-12-26
Hi all

Wish to get the public IP address of a Ubuntu server running on a LAN and either save it to a file or a variable for use in a CRONTAB script

The command used is:-

```
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 'S/<.*$//'
``` 

This displays the IP address in the command window.

By saving it to either a file or variable, it would mean that a suitable script might be created to check for changes to a dynamic IP address. 

If a change is detected, the DNS servers at ZoneEdit.com could be updated.

I am aware of ddclient and have been using it, but for some reason it no longer works on either my main or backup server.

Any ideas would be appreciated.

TIA

---

### Post by jimbothigpen on 2010-12-27
In ddclient.conf, in the zoneedit stanza, replace [www.zoneedit.com](www.zoneedit.com) with legacy.zoneedit.com. Zoneedit is migrating to a new web layout, but this solved the issue for me.

---

### Post by Cheesehead on 2010-12-27
To work in Ubuntu, I needed to replace "-e 'S/<.*$//' " with "-e 's/<.*$//' ".

```
# To a File
wget -q -O /tmp/ip_address checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//' 
cat /tmp/ip_address    # Show the file


# To a variable
IPAddress=$(wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//')
echo $IPAddress     # Show the variable

```

There are also simpler services to get your public IP. I like sed, but I find it hard to maintain:
```
wget -q -O /tmp/ip_address http://www.whatismyip.com/automation/n09230945.asp
IPAddress=$(wget -q -O - http://www.whatismyip.com/automation/n09230945.asp
```

---

