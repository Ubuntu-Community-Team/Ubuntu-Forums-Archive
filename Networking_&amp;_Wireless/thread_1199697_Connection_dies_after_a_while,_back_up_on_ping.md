---
title: "Connection dies after a while, back up on ping"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by mzr on 2009-06-29
I am facing a strange problem that the connection on my ubuntu machines (server 9.04 edition) automatically dies after a while - I am unable to access anything hosted on those servers from outside the network. 

If I just ping from within the server to anything outside, the net seems to be up again and I can access from outside. (Weirdly, before the ping I am still able to access the server from within the same network but it seems to be dead for anything otuside the network. After the ping it is up for all). 

Restarting networking (/etc/ini.d/netowrking retstart) also brings it back up.

Any help will be well appreciated.
Thanks,
mZr

---

### Post by computer13137 on 2009-06-29
I could possibly be of help if I knew more about your network infrastructure and where the server is sitting.

I suppose it could be a bad switch or router or something... is this server plugged into the internal network somewhere, or is it the router between the web and the LAN?

If it's on an internal network, are other computers inside the network also experiencing this problem?  I have wireless Internet service which uses polling, and allocates bandwidth to active connections.  Hence, I leave a ping running to my web server (offsite) at all times, because I have a theory that it keeps my connection faster and more stable. :P

You may consider doing the same if it keeps your problem from surfacing... a ping hardly uses any bandwidth at all.

However that doesn't fix the underlying problem with your network, so I'd go around with a laptop, plugging into switches and routers between your system and the Internet, and see if that system has the same problem.  If the problem stops happening somewhere along the way, check the configuration of the piece of hardware where the last failure occurred.

I suppose this could be a bad router configuration, bad switch, bad cable... or maybe it's a problem with your Internet service, in which case, plug directly into the Internet and see if you have the problem... if you do, call your ISP.

I've tried to cover all the bases- but it's difficult to answer an ambiguous question like this...

I'm subscribing to this thread in case you reply, since I think I might be able to assist you further if I have more details.

-Kirk

---

### Post by jordey24 on 2009-06-29
I have a similar problem so hopefully theres a solution for it:p

---

### Post by computer13137 on 2009-06-29
> **jordey24 said:**
> I have a similar problem so hopefully theres a solution for it:p
Come on guys... network maps and stuff!  We can't help you very well with vague text descriptions.

I'd be glad to try to help you out too, but we need more information.

-Kirk

---

### Post by mzr on 2009-06-30
hey Kirk,

Thanks for the reply. The exact setup is this.

We use 2 net connections at office say A and B.

A is earmarked for servers, B for office usage.

Following is a rough network diagram

[LIST]
[*]DSL Router 1 (for connection A)
[LIST]
[*]Ethernet Hub (D-LINK DFE 932RX)
[LIST]
[*]Server 1 (Apache2/Tomcat6/Php5)
[*]Server 2 (Apache2/Tomcat6/Php5)
[*]Wireless Router A (Linksys WRT54G)
[/LIST]
[/LIST]
[/LIST]

[LIST]
[*]DSL Router 2 (for connection B)
[LIST]
[*]Wireless Router B (Cisco Aironet 1200 AG)
[LIST]
[*]File Server (A simple ubuntu machine with ftp access)
[/LIST]
[/LIST]
[/LIST]
Leaving the ping on does solve the problem but it eats up a lot of data transfer so I wouldn't prefer doing that. Do let me know if you want me to give any more details.

Thanks,
mZr

---

### Post by mzr on 2009-06-30
Also, once the connection dies after a little while, if I ping from connection B, I am unable to reach the servers. If I ping from any machine through connection A (whether from one server to the other or from any machine on my wireless router), the ping goes through.

I have setup a basic  workaround for the time being - pinging an external site every 5 minutes by doing this:

Login as root or sudo for following:

```
crontab -e
```

Following line pings externalSite once every 5 minutes
```
*/5 * * * * ping -c 1 externalSite.com
```

Logs for cron are available in /var/log/syslog

This isn't a permanent solution but it keeps the connection alive till something can be figured out.

---

### Post by computer13137 on 2009-07-02
Hmm, sorry for the late reply... I've been busy and ended up not having Internet at work on Tuesday... and I usually do the Ubuntu Forums when I'm bored at work, keeps the mind running. :P

Hmm, that's an odd problem.  Also, I don't know what kind of link you have speed wise, but I honestly don't see how running a ping is going to eat up bandwidth.  I'm not saying "don't look into possible hardware or software problems" but I run 4 pings at home constantly.  I have wireless Internet service to my house, and my theory is that since polling determines which connection to give the bandwidth to - I like to keep my link active. :)  Those 4 pings only use like 1KB/s both ways solid... and some of that might be antenna polling.  I think that running a solid ping is a good way to keep your network quick and responsive - but that's me.

I'm afraid I don't have a whole lot of suggestions besides the ones I have made.  Start plugging laptops in at various points and see where the failure stops... and if it stops somewhere, the hardware further down the network is probably the problem.

If you find anything out, I'll continue to be subscribed to this thread.

-Kirk

---

### Post by mzr on 2009-07-07
Thanks Kirk. It is on ping at the moment. I haven't yet been able to figure anything else out! Bahhh...

---

### Post by Conky2000 on 2009-07-27
Hi,

I have a similar problem :(. I did not have the problem on ubuntu server 8.10 but since I installed server 9.04 the problem has surfaced. iirc I used the same settings on 8.04.

I have 9.04 server running on a laptop with wifi setup as follows:
```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid default
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk *mypsk*

```

```
 iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"default"
          Mode:Managed  Frequency:2.412 GHz  Access Point: blah
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=72/100  Signal level:-46 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

My network is setup as follows:
WRT54G router with Tomato
[LIST]
[*]Windows Vista box wired connection
[*]Windows XP wireless on eeepc 701
[*]Ubuntu 9.04 desktop wireless
[*]Ubuntu 9.04 server wireless with dlink DWL-G122
[/LIST]

All computers get their IPs from tomato with static DHCP

I have my crontab set up to ping all the computers 1/min because otherwise they cannot connect to the 9.04 server.

Any ideas? :D

---

### Post by chrisinspace on 2009-07-27
> **mzr said:**
> I am facing a strange problem that the connection on my ubuntu machines (server 9.04 edition) automatically dies after a while - I am unable to access anything hosted on those servers from outside the network. 

If I just ping from within the server to anything outside, the net seems to be up again and I can access from outside. (Weirdly, before the ping I am still able to access the server from within the same network but it seems to be dead for anything otuside the network. After the ping it is up for all). 

Restarting networking (/etc/ini.d/netowrking retstart) also brings it back up.

Any help will be well appreciated.
Thanks,
mZr


I am experiencing the exact same problem.  I didn't find this thread when I searched the forums, so I started my own a couple of days ago.  I've posted a couple of updates to it as I get more information, but no one has responded yet.

[http://ubuntuforums.org/showthread.php?t=1222119](http://ubuntuforums.org/showthread.php?t=1222119)

The machine I'm having a problem with is a VMWare virtual server.  Its NIC is attached to my DMZ.  So, I have an internal private network for most of the workstations and servers and a DMZ for a couple of servers I expose to the internet.  When the connection drops, I cannot access the server in question from my internal network, from another computer in the DMZ, or from a computer completely outside of my network.  I have another Ubuntu server running in my private network and I never have issues connecting to it.  Both are 9.04.

Just as you described, if I initiate a ping from the server, all connections are restored.  Restarting the interface brings it back up, as well.

---

### Post by Conky2000 on 2009-08-01
i think this guy has the same problem:
[http://ubuntuforums.org/showthread.php?t=1155263](http://ubuntuforums.org/showthread.php?t=1155263)

i wrote a perl script to ping all my machines because the cron job was cluttering up my syslog.

```
#!/usr/bin/perl

$net='192.168.1.';
@ips=(1,117,124,122);

while(0!=1){
        foreach $ip(@ips)
        {
                system "/bin/ping $net$ip -w1 -c1 -s1 2>&1 > /dev/null";
        }
        sleep(60);
}

```

I put the script in rc.local.

It's not really a big deal but I am still interested in solving this problem. Can anyone can give me a hint as to what to try or which logs to check?

---

### Post by mzr on 2009-08-07
I don't have much knowledge on the perl. What does this do (how often does it ping and pings what?) I guess it pings once every 60 seconds?

Also, if I create this script - I have to make it executable before putting it in rc.local right?

> **Conky2000 said:**
> i think this guy has the same problem:
[http://ubuntuforums.org/showthread.php?t=1155263](http://ubuntuforums.org/showthread.php?t=1155263)

i wrote a perl script to ping all my machines because the cron job was cluttering up my syslog.

```
#!/usr/bin/perl

$net='192.168.1.';
@ips=(1,117,124,122);

while(0!=1){
        foreach $ip(@ips)
        {
                system "/bin/ping $net$ip -w1 -c1 -s1 2>&1 > /dev/null";
        }
        sleep(60);
}

```I put the script in rc.local.

It's not really a big deal but I am still interested in solving this problem. Can anyone can give me a hint as to what to try or which logs to check?

---

### Post by Conky2000 on 2009-08-21
I just put this in the file /etc/rc.local:

*/usr/bin/perl /home/username/ping.pl &*

and the code goes into the file */home/username/ping.pl*

No need to make the script executable.

It loops through all the numbers in @ips, adds each one to $net and pings them every 60sec.

---

