---
title: "Ubuntu can't reconnect to gmail after ISP restores access"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by dewdrop_world on 2010-12-31
Lately, my ISP has started making all Google sites inaccessible for a short time every afternoon (last 3-4 days now). I suspect some kind of DNS poisoning... access always comes back later in the afternoon.

When access does come back, non-Linux machines can connect basically right away, but my Ubuntu machine (the primary one I use) seems to need a reboot, as if wrong DNS information gets stuck in the session and the reboot clears it so that the machine can get the correct IP address.

I have not installed nscd, and IIUC the OS should not be persisting DNS cache information without that package. Every reference I can find online to clearing the DNS cache seems to depend on this package.

The objective is just to get back in touch with my Gmail without having to reboot (since e.g. OSX doesn't require a reboot for the same). What should I do?

Thanks,
James

---

### Post by PatchesTheCaveman on 2010-12-31
If your ISP is mucking about with your DNS servers, it might be better to use a different DNS server.  Google provides free public DNS servers that anyone can use.  Just right-click on the network icon, click Edit Connections, edit the connection you are using, switch to the IPv4 Settings tab, and change your DNS servers to 8.8.8.8 and 8.8.4.4.  Changing them on the Windows machine and possibly your router might also clear up the problem with Google services going down for hours a day.

For more information on the Google public DNS service, including how to configure it on other operating systems and devices, visit [http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

I personally find that they work better than my ISP's DNS servers.

---

### Post by dewdrop_world on 2010-12-31
Here in mainland China, it would surprise me if I could use Google's DNS. I think Gmail gets through mainly because of tourists and business travelers who would be P.O.'d if they couldn't get their mail :)

I may try OpenDNS. I used it back in the States. Yesterday when this happened, I changed the wireless connection to use OpenDNS, but it didn't make a difference (even after disconnecting and reconnecting). I'm not sure why that is. It's possible the ISP intercepted requests to OpenDNS, but I can't prove it. Or, the OS retained some bad DNS data and never asked OpenDNS for updates.

To tell the difference between those cases, it would be nice to have some command to wipe out any cached IP's that the OS might be holding in memory.

(Happened again just now... one reboot later, and it's all back to normal.)

Thanks,
James

---

### Post by PatchesTheCaveman on 2010-12-31
Everything I can find tells me Linux doesn't cache DNS records unless you use the aforementioned nscd daemon.  But obviously your computer is saving something that rebooting fixes, so that's weird.

Is this a wired connection?  If so, next time try
```
sudo ifdown eth0
sudo ifup eth0
```

That will reset your network connection.  That might be enough.

Also, if you want to figure out what's going on with your DNS, try running
```
dig mail.google.com
```
when it's working and save it and run it again when it's not and see if there's a difference.

Also, you can add IP address to hostname mappings in /etc/hosts if you think that might be helpful.

ETA:  Are you sure its not just the browser that's caching IPs?  Try just restarting Firefox next time.

---

### Post by dewdrop_world on 2011-01-02
> **PatchesTheCaveman said:**
> Everything I can find tells me Linux doesn't cache DNS records unless you use the aforementioned nscd daemon.  But obviously your computer is saving something that rebooting fixes, so that's weird.

I've got OpenDNS in place now, but the issue still occurs. (But, I don't have any confidence that the ISP/Great Firewall is not intercepting requests to known DNS IPs.)
> 
Is this a wired connection?  If so, next time try
```
sudo ifdown eth0
sudo ifup eth0
```That will reset your network connection.  That might be enough.

No, it's wireless. No problem from other machines (also connecting wirelessly).

>  Also, if you want to figure out what's going on with your DNS, try running
```
dig mail.google.com
```when it's working and save it and run it again when it's not and see if there's a difference.


Saved just now, will compare after I get the connection back up.

> Also, you can add IP address to hostname mappings in /etc/hosts if you think that might be helpful.


Hadn't tried that yet. Hmm.

> ETA:  Are you sure its not just the browser that's caching IPs?  Try just restarting Firefox next time.

 No, it's any application. CheckGmail breaks, as does wanderlust (IMAP  client). No problem with other sites (or apps like Skype). Disabling  networking and re-enabling it again through the network manager doesn't  make any difference.
 
 Next, I will try logging out and logging in again -- see if the bad  information goes away with the session. But to do that, I lose what I'm  typing now so... I'll be back :)
 
 James

---

### Post by dewdrop_world on 2011-01-02
One reboot later and... we're back. Logout/login did nothing.

Good and bad 'dig's look about the same.

Maybe it isn't DNS after all. Could CheckGmail be doing something fishy? I could try running without it for a few days.

James

('dig' with no contact -- 208.67.222.222 is an OpenDNS server)

```
; <<>> DiG 9.7.0-P1 <<>> mail.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64260
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.google.com.        IN    A

;; ANSWER SECTION:
mail.google.com.    602506    IN    CNAME    googlemail.l.google.com.
googlemail.l.google.com. 113    IN    A    74.125.71.18
googlemail.l.google.com. 113    IN    A    74.125.71.17
googlemail.l.google.com. 113    IN    A    74.125.71.19
googlemail.l.google.com. 113    IN    A    74.125.71.83

;; Query time: 338 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sun Jan  2 22:07:47 2011
;; MSG SIZE  rcvd: 124

```(dig with contact)

```
; <<>> DiG 9.7.0-P1 <<>> mail.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26640
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.google.com.        IN    A

;; ANSWER SECTION:
mail.google.com.    601519    IN    CNAME    googlemail.l.google.com.
googlemail.l.google.com. 29    IN    A    74.125.71.19
googlemail.l.google.com. 29    IN    A    74.125.71.18
googlemail.l.google.com. 29    IN    A    74.125.71.17
googlemail.l.google.com. 29    IN    A    74.125.71.83

;; Query time: 357 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sun Jan  2 22:24:15 2011
;; MSG SIZE  rcvd: 124

```

---

### Post by PatchesTheCaveman on 2011-01-02
AFAICT IP blocks are how they do business, so it's unlikely DNS is involved here.  Try running a *traceroute* when it isn't working for any of the computers, after it comes back and is just broken on your Ubuntu machine, and when it's working on the Ubuntu machine.  (I don't know about Lucid but Maverick doesn't come with the *traceroute* command.  Use *mtr* instead.)  That might indicate where things are going wrong.

As for why Gmail goes out intermittently:  you might be hitting their keyword filter.  They cut off the connection when they find a certain keyword in a TCP packet and then block the path between those two IPs for so many hours.

---

### Post by dewdrop_world on 2011-01-02
> **PatchesTheCaveman said:**
> As for why Gmail goes out intermittently:  you might be hitting their keyword filter.  They cut off the connection when they find a certain keyword in a TCP packet and then block the path between those two IPs for so many hours.

Now *that* makes sense.

At the moment, Google is behaving fine, but another website that I frequent was "down" earlier this morning, quite possibly because of a keyword hit. But I tried it again just now and it's working again, no reboot. I don't know if it's a server glitch on their side or if I waited long enough, but that gives me a little more confidence anyway.

Interesting, strange stuff :)

James

---

### Post by PatchesTheCaveman on 2011-01-03
Apparently you can also improve your situation by lowering your MTU (which reduces the maximum size of TCP packets), but Google failed me in finding a value that is effective for your purposes.

To adjust it, run:
```
sudo ifconfig eth0 mtu <size>
```

All mine seem to be 1500 as a frame of reference.

Also, apparently using IPv6 is a good solution for those sites that support it.  I know you can use normal Google search over IPv6 at [http://ipv6.google.com/](http://ipv6.google.com/) but probably not Gmail.  (That bastion of social networking they seem to hate also works by a similar construction.)  All you have to do to get IPv6 connectivity working via Teredo tunneling is:
```
sudo apt-get install miredo
```

If your router supports 6to4 or DD-WRT you can get that going for your whole network too.

---

### Post by sanderj on 2011-01-03
> **dewdrop_world said:**
> Now *that* makes sense.

At the moment, Google is behaving fine, but another website that I frequent was "down" earlier this morning, quite possibly because of a keyword hit. But I tried it again just now and it's working again, no reboot. I don't know if it's a server glitch on their side or if I waited long enough, but that gives me a little more confidence anyway.

Interesting, strange stuff :)

James

Do you use https on your gmail connection all the time? Because, with a https-connection, a man-in-the-middle can't see any keywords ...

---

### Post by dewdrop_world on 2011-01-03
> **sanderj said:**
> Do you use https on your gmail connection all the time? Because, with a https-connection, a man-in-the-middle can't see any keywords ...

Well, the issue happened again today and I was not using gmail on the web at all. My preferred way to read my mail is wanderlust, an IMAP client for Emacs (which I use because it's the only thing I found that does local message caching in any sort of reasonable way).

When I do use Gmail on the web, it's https.

It happened right before I was heading out the door, didn't have time for any diagnostics. After a reboot, I see this address in netstat.

pw-in-f109.1e100.:imaps

Pinging imap.gmail.com connects to pz-in-f109.1e100.net (74.125.127.109), basically the same except z instead of w (not surprising since they use address blocks).

From "imaps" I gather that communications to the IMAP server are encrypted. Outgoing messages hit smpt.gmail.com via STARTTLS -- that's encrypted also? I think?

James*

---

### Post by PatchesTheCaveman on 2011-01-03
I forgot about that.  The keyword filter shouldn't be a problem for you on encrypted connections.  (Gmail requires an encrypted connection for both IMAP and SMTP, so if it's working, it's secure.)  Perhaps they're just trying to annoy Gmail users so they switch to a local service.  :evil:

Your ping behavior seems okay.  I just queried Google's nameservers via *dig*on my machine and got the same IP address (74.125.127.109).  As long as the domain ends in 1e100.net you're getting real Google server.

---

### Post by dewdrop_world on 2011-01-04
Just broke again... I wasn't doing anything with google before, honest!

netstat says (irrelevant ones deleted):

```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      1 dlm-laptop.local:48214  hx-in-f138.1e100.ne:www SYN_SENT   
tcp        0      1 dlm-laptop.local:55736  hx-in-f102.1e100.ne:www SYN_SENT
```

"imaps" connection is gone.

Also:

```
dlm@dlm-laptop:~$ tracepath imap.gmail.com
 1:  dlm-laptop.local (192.168.100.103)                     0.101ms pmtu 1500
 1:  no reply
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply
```

I tried ```
sudo ifdown wlan0
``` per an earlier recommendation -- would have brought it up again (ifup) except...

```
dlm@dlm-laptop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
```

Rather stymied. What next? I can *ping* google services, just not *use* them.

```
dlm@dlm-laptop:~$ ping imap.gmail.com
PING gmail-imap.l.google.com (74.125.53.109) 56(84) bytes of data.
64 bytes from pw-in-f109.1e100.net (74.125.53.109): icmp_seq=1 ttl=43 time=507 ms
64 bytes from pw-in-f109.1e100.net (74.125.53.109): icmp_seq=2 ttl=43 time=536 ms
64 bytes from pw-in-f109.1e100.net (74.125.53.109): icmp_seq=3 ttl=43 time=516 ms
64 bytes from pw-in-f109.1e100.net (74.125.53.109): icmp_seq=4 ttl=43 time=536 ms
64 bytes from pw-in-f109.1e100.net (74.125.53.109): icmp_seq=5 ttl=43 time=560 ms
64 bytes from pw-in-f109.1e100.net (74.125.53.109): icmp_seq=6 ttl=43 time=588 ms
^C
--- gmail-imap.l.google.com ping statistics ---
7 packets transmitted, 6 received, 14% packet loss, time 10856ms
rtt min/avg/max/mdev = 507.411/540.815/588.566/27.167 ms
```

Thanks!
James

---

### Post by dewdrop_world on 2011-01-04
Moved over to the mac for some other tests. Google access is fine on the mac.

Traceroute is blocked. Same output for both imap.gmail.com and [www.microsoft.com](www.microsoft.com) (wanted to test also against a site that would certainly not be blocked).

```
ddw:~ dewdrop$ traceroute www.microsoft.com
traceroute to toggle.www.ms.akadns.net (65.55.12.249), 64 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
```

I let imap.gmail.com get up to 24 * * * before killing it.

So it seems I can't even get any useful information from a working system.

AGH!!! :)

James

---

### Post by PatchesTheCaveman on 2011-01-04
I think something's going on with your router that's preventing traceroutes from working.  Even if The Man was doing something to block traceroutes, you should still at least get a ping on your router.  Look in your router configuration and see if there's any ICMP blocking going on.

Note that even when it's working, you won't be able to complete a traceroute to microsoft.com.  A lot of networks are configured such that it doesn't work.  However, in my experience, you can usually complete a traceroute to Google servers.

Maybe something is going on with the routing table on your Ubuntu box.  Next time it's broken, try running
```
ip route show
```
and copy/paste the result.  For comparison, you can also run that on your Mac.

---

### Post by dewdrop_world on 2011-01-06
```
dlm@dlm-laptop:~$ ip route show
192.168.100.0/24 dev wlan0  proto kernel  scope link  src 192.168.100.103  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via 192.168.100.100 dev wlan0  proto static 
```

Will post the working "ip route" after I reboot in just a moment. I think it's about the same.

"ip" is not installed in OSX 10.4.11.

In a previous post, someone suggested taking down the network using ifdown/ifup, but the example command was for eth0 and I'm using wireless.

**sudo ifdown wlan0**

... was not successful: "ifdown: interface wlan0 not configured." Is this still worthwhile to try? If so, I don't know how to change the command to make it work. Or if not, I'd like to know so that I can forget about that idea.

Will post again soon...
James

---

### Post by dewdrop_world on 2011-01-06
ip route after reboot:

```
192.168.100.0/24 dev wlan0  proto kernel  scope link  src 192.168.100.103  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via 192.168.100.100 dev wlan0  proto static 
```

Seems like it must be local. No other machine in the house is affected. And, it's not always like I have an active TCP connection to Google something-or-other and it gets cut, and everything breaks after that. Sometimes it barfs on the first access after resuming the session, and then the only thing that works is to reboot.

Another thing that changed recently is that I'm running Skype most of the time now, which I did only rarely before. I can't imagine why that would be related, but computers are strange creatures.

Also, I recently switched to the latest real-time kernel compatible with 10.04, 2.6.33-29-realtime. (I needed that to get my audio configuration to work smoothly.) That's really far-fetched for a networking issue but any detail might help.

Thanks,
James

---

### Post by PatchesTheCaveman on 2011-01-06
Well that's okay.  Do you use NetworkManager, wicd, or manual configuration for your wireless connection?

---

### Post by dewdrop_world on 2011-01-06
> **PatchesTheCaveman said:**
> Well that's okay.  Do you use NetworkManager, wicd, or manual configuration for your wireless connection?
Network manager. It's an "auto" connection but I modified it to use DHCP for addresses only (so I could put the OpenDNS server IPs into the right field).

---

### Post by PatchesTheCaveman on 2011-01-06
Give *wicd* a shot.  A lot of people find it glitches less than NetworkManager.

All you have to do is:
```
sudo apt-get remove network-manager
sudo apt-get install wicd
```

Sometimes you have to reboot to get NetworkManager completely off and *wicd* operational.

---

### Post by thefix0r on 2011-01-06
EASY SOLUTION

if your isps dns servers are unreliable, use different ones

4.2.2.1
4.2.2.2 both work

---

### Post by dewdrop_world on 2011-01-08
Well, I'm hoping this point is moot. Had to move to another apartment suddenly. Maybe connecting from a different location will avoid the glitches.

@ thefixor, I already tried OpenDNS but it didn't help.

---

### Post by dewdrop_world on 2011-01-10
> **PatchesTheCaveman said:**
> Give *wicd* a shot.  A lot of people find it glitches less than NetworkManager.

All you have to do is:
```
sudo apt-get remove network-manager
sudo apt-get install wicd
```Sometimes you have to reboot to get NetworkManager completely off and *wicd* operational.

I'm sorry to say, but there was a wee small detail missing from your instructions.

**After removing network manager, all my internet connections are gone.** So it's a wee little bit difficult to apt-get wicd...

So I will now collect as much info as I can on ifconfig so I can set up the wired connection, long enough to install wicd.

---

### Post by dewdrop_world on 2011-01-10
I've reinstalled network manager, after getting a wired connection going with the help of the #ubuntu folks.

Will come back to wicd later, don't know when. I can't afford much downtime these days.

---

### Post by PatchesTheCaveman on 2011-01-10
Sorry about that!  I'm used to providing that instruction for people whose wireless connections aren't working at all, and thus are already connected via a wire.  Ubuntu will keep a wired connection after NetworkManager uninstalls but apparently it won't keep a wireless one.  It is safe to reverse the operations.

Did your impromptu move correct your previous problems?

---

### Post by dewdrop_world on 2011-01-11
No, unfortunately it hasn't helped.

I'm on vacation soon and I'll have a chance to try this out in a different city (I'm not sure if it's a different ISP -- telecom remains one of the state-run industries -- but most likely a different route), with a different WiFi router.

If I can't reproduce it over there, then it's something about the environment. That could have to do with the way the ISP works in the different cities, or it could be the kind of hacky way people share Internet connections to save money (router plugged into router plugged into router and so on). Where I'll be on vacation, the router has a direct PPPoE connection. If it's fine there, I could try wicd after coming back but there probably isn't much more I could do.

But if it does persist, it would mean the issue is almost certainly machine and OS specific. (Well, I guess to be really sure of that, I should come back to the US for a few weeks and try there.)

Re: the problem the other night -- stupidly, I'd already rebooted before plugging in the wired connection. So I had to run ifup and dhclient manually before I could do anything. Anyway, fixed now :)

James

---

### Post by dewdrop_world on 2011-01-13
No idea yet on Google stability from Zhuhai, but I did switch to wicd anyway. For some reason, my system does not like to connect to the WiFi router here after waking up from sleep -- sporadically -- it worked the first couple of times after arriving, but then failed the WPA authentication midafternoon. NM also didn't want to connect to the wired network without help (had to run dhclient manually again). That's too many strikes for one afternoon, so NM is out.

Currently wicd is reading it loud and clear. I just rebooted 10 minutes ago, so it'll be another day or two before I have an idea about Gmail etc.

Thanks for all the suggestions,
James

---

### Post by dewdrop_world on 2011-02-16
Back in Guangzhou now, experiencing the same failures with Google as before. On vacation in Zhuhai, no apparent outages.

So:

- wicd did not solve the problem.

- *sudo modprobe -r ath9k*, followed by *sudo modprobe ath9k*, also did not solve the problem.

Still, my Mac is unaffected. Only my Ubuntu machine craps out on Google after a day or so, and only in this city. (Note also, I had not been accessing any Google pages or services for a good hour or two before I lost the connection.)

No idea what to do next. I can't shake the feeling that some corrupt Internet routing information is being cached in memory and that the faulty information is cleared on reboot. As we've already discussed, that's not "supposed" to happen but it fits the facts...

I guess the only other thing I could try is to get an extra long  ethernet cable and use the wired connection for several days, see if it  happens that way.

Should I take this up with canonical?

Thanks.
James

---

### Post by dewdrop_world on 2011-02-19
> **dewdrop_world said:**
> I guess the only other thing I could try is to get an extra long  ethernet cable and use the wired connection for several days, see if it  happens that way.

Ha! I was actually able to stretch an ethernet cable over to my desk and... lost Google access again. So all that WiFi stuff was a red herring -- it also happens with the wired connection.

So if it isn't IP routing information in RAM on my system (cleared on reboot)... well, I don't know how else to explain the symptoms. If it were something amiss in the router, I'd expect all machines in the house to be affected (but it's only Ubuntu) and I'd expect to have to reset the router to fix it (not necessary) -- for that matter, if the problem were *anywhere* upstream, it should kill Google access on all machines but it doesn't. So it must be local on my Ubuntu box. General failure of the networking subsystem should make everything inaccessible, but it's only Google.

So we can at least rule out a lot of things:


[LIST]
[*]Can't be purely an ISP problem (only one machine is affected) -- but, the problem doesn't happen in other physical locations.
[*]Can't be a router problem (rebooting fixes it, without resetting the router).
[*]Can't be a WiFi problem (also happens wired).
[*]Can't be that the networking layer in Ubuntu goes down (other sites are fine).
[*]Can't be a misconfiguration persisted on disk (if it were, wouldn't it happen right after rebooting too?).
[*]Can't be a browser issue -- two browsers are affected, plus CheckGMail and wanderlust.
[/LIST]

That leaves... invisible stuff. My *favorite*. :confused::confused::confused::confused::confused:

Thanks.
James

---

