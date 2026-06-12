---
title: "Ubuntu only allowing certain websites"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by greggorrell on 2012-08-13
Hey guys, I seem to have a problem with Ubuntu only allowing me to go to a few select websites.  Everything was working fine last night on wireless.  I brought the laptop to a friends house and it would only connect to Facebook.  I tried both Firefox and Chrome.  Attempting to go to sites in Chrome gives me "The webpage is no availible," and goes on further to say "the connection attempt was rejected."  This happens with all websites, other than this site, Facebook, and even dropbox works.  It seems anything in the ubuntu.com domain works also.  To the sites that don't work, Firefox gives and unable to connect error page.  I can't possibly figure out what the problem could be.  It is doing it on my own wifi, and also when plugged in via ethernet at any network.  And like I said, it was working fine, up til when I turned the laptop off and when to a friends last night.  Any ideas would be appreciated.

---

### Post by rukiaEnix on 2012-08-13
Did you set proxy settings at your friends house?

---

### Post by greggorrell on 2012-08-13
Nope.  All I did was reload the driver after I noticed no sites were working.  I'm figuring it has something to do with maybe Ubuntu's proxy settings, and I can't see any problems with those.  I don't get how it could only allow certain sites, and those sites don;t have anything in common.

---

### Post by rukiaEnix on 2012-08-13
Can you ping to the IP of one of the sites you can't see with the browsers?

---

### Post by sanderj on 2012-08-13
Use wget (on the command line) to see what is going on. Use a site that works in Chrome/Firefox, and a site that doesn't. So:


```
wget goodsite.com
wget badiste.com

```
Post the output here

---

### Post by greggorrell on 2012-08-13
greg@greg-laptop:~$ wget facebook.com
--2012-08-13 16:03:49--  [http://facebook.com/](http://facebook.com/)
Resolving facebook.com (facebook.com)... 66.220.158.11, 69.171.224.37, 69.171.229.11, ...
Connecting to facebook.com (facebook.com)|66.220.158.11|:80... failed: Connection refused.
Connecting to facebook.com (facebook.com)|69.171.224.37|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://facebook.com/](https://facebook.com/) [following]
--2012-08-13 16:03:49--  [https://facebook.com/](https://facebook.com/)
Connecting to facebook.com (facebook.com)|69.171.224.37|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [https://www.facebook.com/](https://www.facebook.com/) [following]
--2012-08-13 16:03:50--  [https://www.facebook.com/](https://www.facebook.com/)
Resolving [www.facebook.com](www.facebook.com) ([www.facebook.com](www.facebook.com))... 69.171.234.37, 2a03:2880:10:1f03:face:b00c:0:25
Connecting to [www.facebook.com](www.facebook.com) ([www.facebook.com)|69.171.234.37|:443](www.facebook.com)|69.171.234.37|:443)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.facebook.com/unsupportedbrowser](http://www.facebook.com/unsupportedbrowser) [following]
--2012-08-13 16:03:50--  [http://www.facebook.com/unsupportedbrowser](http://www.facebook.com/unsupportedbrowser)
Connecting to [www.facebook.com](www.facebook.com) ([www.facebook.com)|69.171.234.37|:80](www.facebook.com)|69.171.234.37|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                   ] 18,482      --.-K/s   in 0.1s    

2012-08-13 16:03:50 (189 KB/s) - `index.html' saved [18482]



greg@greg-laptop:~$ wget google.com
--2012-08-13 16:03:55--  [http://google.com/](http://google.com/)
Resolving google.com (google.com)... 74.125.228.104, 74.125.228.105, 74.125.228.110, ...
Connecting to google.com (google.com)|74.125.228.104|:80... failed: Connection refused.
Connecting to google.com (google.com)|74.125.228.105|:80... failed: Connection refused.
Connecting to google.com (google.com)|74.125.228.110|:80... failed: Connection refused.
Connecting to google.com (google.com)|74.125.228.96|:80... failed: Connection refused.
Connecting to google.com (google.com)|74.125.228.97|:80... failed: Connection refused.
Connecting to google.com (google.com)|74.125.228.98|:80... failed: Connection refused.
Connecting to google.com (google.com)|74.125.228.99|:80... failed: Connection refused.
Connecting to google.com (google.com)|74.125.228.100|:80... failed: Connection refused.
Connecting to google.com (google.com)|74.125.228.101|:80... failed: Connection refused.
Connecting to google.com (google.com)|74.125.228.102|:80... failed: Connection refused.
Connecting to google.com (google.com)|74.125.228.103|:80... failed: Connection refused.
Connecting to google.com (google.com)|2607:f8b0:4004:803::1000|:80... failed: Network is unreachable.

---

### Post by greggorrell on 2012-08-13
pinging tells me destination port unreachable

---

### Post by rukiaEnix on 2012-08-13
Can you please post the result of:

```

iptables -L

```

---

### Post by sanderj on 2012-08-13
Weird.

Are you on a normal PC, a normal LAN and a normal Internet connection? Not a corporate LAN/WAN, or a China Internet connection?

And: no firewall activated on your PC?

Can you run

```
mtr -nrc5 74.125.228.104

```
Here's mine:

```
$ mtr -nrc5 74.125.228.104
HOST: R540                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.1.254              0.0%     5    6.0   2.7   1.4   6.0   1.9
  2.|-- 82.70.59.254              0.0%     5   20.0  21.3  18.6  26.5   3.0
  3.|-- 195.9.145.100             0.0%     5   23.3  21.6  20.5  23.3   1.1
  4.|-- 209.5.254.90              0.0%     5   24.7  79.4  21.3 306.1 126.7
  5.|-- 209.85.255.70              0.0%     5   27.0  68.9  21.3 205.9  79.0
  6.|-- 209.85.243.32              0.0%     5   26.6  49.2  26.6 115.3  37.5
  7.|-- 209.85.253.95              0.0%     5   40.7  34.3  26.5  47.3   9.3
  8.|-- 216.239.43.6               0.0%     5  105.2 105.3 103.8 108.0   1.7
  9.|-- 72.14.238.253              0.0%     5  105.3 105.7 104.4 107.2   1.3
 10.|-- 74.125.228.104            20.0%     5  106.8 108.5 103.5 112.2   4.1
sander@R540:~$

```

---

### Post by greggorrell on 2012-08-13
greg@greg-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
pgl_in     all  --  anywhere             anywhere             state NEW mark match ! 0x14

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
pgl_fwd    all  --  anywhere             anywhere             state NEW mark match ! 0x14

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
pgl_out    all  --  anywhere             anywhere             state NEW mark match ! 0x14

Chain pgl_fwd (1 references)
target     prot opt source               destination         
RETURN     all  --  192.168.0.0/24       192.168.0.0/24      
RETURN     all  --  anywhere             localhost           
DROP       all  --  anywhere             anywhere             mark match 0xa
NFQUEUE    all  --  anywhere             anywhere             NFQUEUE num 92

Chain pgl_in (1 references)
target     prot opt source               destination         
RETURN     all  --  192.168.0.0/24       anywhere            
RETURN     all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere             mark match 0xa
NFQUEUE    all  --  anywhere             anywhere             NFQUEUE num 92

Chain pgl_out (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             192.168.0.0/24      
RETURN     all  --  anywhere             localhost           
RETURN     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere             mark match 0xa reject-with icmp-port-unreachable
NFQUEUE    all  --  anywhere             anywhere             NFQUEUE num 92

---

### Post by greggorrell on 2012-08-13
I get nothing.  I am on my regular network, but like I said it is acting the same on two different wireless networks, and also plugged into ethernet.

greg@greg-laptop:~$ mtr -nrc5 74.125.228.104
HOST: greg-laptop                 Loss%   Snt   Last   Avg  Best  Wrst StDev


> **sanderj said:**
> Weird.

Are you on a normal PC, a normal LAN and a normal Internet connection? Not a corporate LAN/WAN, or a China Internet connection?

And: no firewall activated on your PC?

Can you run

```
mtr -nrc5 74.125.228.104

```
Here's mine:

```
$ mtr -nrc5 74.125.228.104
HOST: R540                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.1.254              0.0%     5    6.0   2.7   1.4   6.0   1.9
  2.|-- 82.70.59.254              0.0%     5   20.0  21.3  18.6  26.5   3.0
  3.|-- 195.9.145.100             0.0%     5   23.3  21.6  20.5  23.3   1.1
  4.|-- 209.5.254.90              0.0%     5   24.7  79.4  21.3 306.1 126.7
  5.|-- 209.85.255.70              0.0%     5   27.0  68.9  21.3 205.9  79.0
  6.|-- 209.85.243.32              0.0%     5   26.6  49.2  26.6 115.3  37.5
  7.|-- 209.85.253.95              0.0%     5   40.7  34.3  26.5  47.3   9.3
  8.|-- 216.239.43.6               0.0%     5  105.2 105.3 103.8 108.0   1.7
  9.|-- 72.14.238.253              0.0%     5  105.3 105.7 104.4 107.2   1.3
 10.|-- 74.125.228.104            20.0%     5  106.8 108.5 103.5 112.2   4.1
sander@R540:~$

```

---

### Post by rukiaEnix on 2012-08-13
Please flush all your IPTABLES rules as root or with sudo like this:

```

iptables --flush

```

---

### Post by underdog512 on 2012-08-13
I would be interested in seeing a packet capture of this issue occurring.  

If you don't mind, head on over to the Software center and search/install Wireshark.  Once installed, you will need to run it as root so press alt+F2  and type "geksudo wireshark."  There should be a list of interfaces on the left side of the page when you first open wireshark.  Simply click on the necessary interface to start the trace. WiFi is usually eth1.  

Once the trace starts, minimize Wireshark, pull your browser up, and make a few attempts.  After this, you can stop the trace, save the pcap, and attach it to this thread.

---

### Post by rukiaEnix on 2012-08-13
I think he won't be able to install it like that.. as he doesn't have a full Internet connection, if you can't install software like that download it from other computer.

---

### Post by greggorrell on 2012-08-13
Looks like flushing iptables worked.. I should have known better to try that in the first place.  Thanks for the help, and if it happens to occur again, I will run a packet capture.

---

### Post by rukiaEnix on 2012-08-13
Happy to hear it worked! Looks like someone wrote those rules. 
Maybe a joke from your friends?

Just in case search for a file were those rules may be written. Check your interfaces file to see if it loads a file with IPTABLES rules at boot time.

Then if that's all please change the thread as solved :D

---

