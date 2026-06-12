---
title: "Dynamic DNS Updates over HTTP with NAT"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by Centrist on 2009-04-11
Hello, All! I had a lot of difficulty setting up dynamic DNS on my computers with my Namecheap service. Inadyn and ddclient were both painful and didn't offer enough customization. So I came up with the guide below to get this working.

My solution for NAT is to dynamically update A records for both the computer's IP (e.g., 10.1.1.1) and the router's external IP. This way, clients within the local network can communicate using local IP addresses, and you can route the 10 network to that router for remote connections. Since each client has it's own gateway record to update, you should be able to route to it from anywhere. If the client gets a public IP, then both A records will show that ip address.

It seems to me that most dynamic DNS setups are very insecure. The URL contains a password for the updated domain, and it's very easy to see which URLs someone has requested if they go through your network (or if you can listen in). So dynamic DNS should only be relied on for remote management. I would never use it for file or printer sharing.


**1: Create a new text file in /etc named ddns-script.sh with the following text:**

```
#!/bin/bash
PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin
#this gets the local ip:
IP=$(ifconfig | grep "inet addr:" | grep -v "127.0.0.1" | cut -d: -f2 | awk '{ print $1}')
#this gets the local host name:
HOST=$(hostname)
# (optional) the name of a gateway dns entry just for this host:
GW="${HOST}-gw"
# this is the URL to send HTTP updates to:
DDNS_URL="http://dynamicdns.park-your-domain.com/update"
#this is the update data for the host A record.
DDNS_UPDATE="domain=example.org&password=2lhjg52k4hj5gk42jh5g24kjh5g245hj&ip=${IP}&host=${HOST}"
# (optional) this is the update data for this host's gateway A record.
#the ip is left out because namecheap will automatically get the public/external IP address.
DDNS_GW_UPDATE="domain=example.org&password=2lhjg52k4hj5gk42jh5g24kjh5g245hj&host=${GW}"
#Now send the info to namecheap (note we are using HTTP GET and not POST)
wget --output-file=/var/log/ddns.log --output-document=/var/log/ddns.html --no-cookies --no-http-keep-alive ${DDNS_URL}?${DDNS_UPDATE}
wget --output-file=/var/log/ddns-gw.log --output-document=/var/log/ddns-gw.html --no-cookies --no-http-keep-alive ${DDNS_URL}?${DDNS_GW_UPDATE}
```

**2. Make sure to update the text in this script with the right URLs, domain, and password for your site.** If you are using Namecheap, then you only need to update the domain and password. The gateway update URL does not include an IP because the remote server will use your public or translated IP by default.

**3. Set the execute bit on the script**
```
sudo chmod +x /etc/ddns-script.sh
```

**4. Export your root cron job list with a text editor.** I used root because I wanted to output logs to /var/logs - that's really the only reason this account is needed.
```
sudo cronjob -e
```

**5. Paste in the following cron job entry to run the script each minute:**
```
* * * * * bash /etc/ddns-script.sh
```

Now give it a minute to run and check the logs to see if it worked. You should be able to ping yourhost.example.org now. For your admin computers, you might want to add example.org to your /etc/resolv.conf file so you don't have to type example.org. For example,
```
search example.org
```
I hope someone finds this useful. This is my first bash script, so please comment if you see something that could be done better. I tested on Ubuntu 8.10 32 and 64-bit computers, but I think it's simple enough to work on pretty much anything.

---

### Post by Centrist on 2009-04-11
And here is how you can do the same thing on Windows. :D

**1. Create a file named c:\ddns.vbs and add the following text to it:**

```
option explicit
'change these values here for your setup:
Const ddns_url = "http://dynamicdns.park-your-domain.com/update"
Const domain = "example.org"
Const password = "2lhjg52k4hj5gk42jh5g24kjh5g245hj"
Dim FileSystem, client, ddns_log, ddns_gw_log, ddns_update, ddns_gw_update, ip_address, _
hostname, List, Config, WMI, Comp
'get WMI connection - nothing special.
Set WMI = GetObject("winmgmts:\\.\root\cimv2")
'get the hostname of the computer.
Set List = WMI.ExecQuery("Select * from Win32_ComputerSystem")
For Each Comp in List
    hostname = Trim(LCase(Comp.Name))
Next
'Get the first IP address on the last interface.
Set List = WMI.ExecQuery("select IPAddress from Win32_NetworkAdapterConfiguration where IPEnabled=true")
For each Config in List
    If Not IsNull(Config.IPAddress) Then ip_address = Config.IPAddress(0)
Next
'set up URLs:
ddns_update = ddns_url & "?domain=" & domain & "&password=" & password & "&ip=" & ip_address & "&host=" & hostname
ddns_gw_update = ddns_url & "?domain=" & domain & "&password=" & password & "&host=" & hostname & "-gw"
'create our log files.
Set FileSystem = CreateObject("Scripting.FileSystemObject")
Set ddns_log = FileSystem.OpenTextFile("c:\ddns.log", 2, true)
Set ddns_gw_log = FileSystem.OpenTextFile("c:\ddns-gw.log", 2, true)
'Create our XML object (we won't use XML though)
Set client = CreateObject("Microsoft.XMLHTTP")
'Open the update url and output the response to a log.
client.Open "GET", ddns_update, False
client.Send
ddns_log.WriteLine client.responseText
ddns_log.Close
'Open the update gateway url and output the response to a log.
client.Open "GET", ddns_gw_update, False
client.Send
ddns_gw_log.WriteLine client.responseText
ddns_gw_log.Close
```

**2. Replace the URLs, domain, and password in the VBS with your own information.** If you're using Namecheap, just change the domain and password.

**3. Create a new scheduled task to run every minute.**
```
schtasks /create /ru "" /tn "DDNS" /sc minute /tr "wscript.exe c:\ddns.vbs"
```

Now wait a minute and check your logs to see if it worked. You may also want to add example.org to your DNS search suffix list. I tested this script on Windows XP SP3, and I'm not sure how it works on 2000 and Vista. It should work I think with a recent version of MSXML. Also, Kaspersky flagged this as trojan on my computer. I had to add the script to its exceptions list.

---

