---
title: "Problem with Updates and FTP :("
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by bLiZz247 on 2009-06-12
I have this strange problem and am hoping someone here will have an idea or at least shoot me in the right direction. 

I am having a problem where when an Ubuntu machine updates or downloads something from synaptic package manager, it downloads VERY slow. It will download for about 3-5 seconds and then stop for about 5 minutes or so. It will then start again but only for about 3-5 seconds. This takes a long time for something to download.

I found out that another employee has a problem while trying to download his software updates for his Mac computer. However his Mac downloads a small part and then completely times out. 
He is also connecting to and external FTP server and cannot get past the directory listing the majority of the time. I think this might be related. This all started happening about two months ago.

If anyone can help me at all or has any ideas please do. Thanks!

Gateway:
Linksys Dual-WAN VPN Router (Set for load balance - Has port 443 using only WAN1)
Internet Browsing and direct downloading work just fine.

---

### Post by jonobr on 2009-06-13
Given the OS independence of the problem, it sounds as if this is a problem with your service provider,

Have you  tried checking download speeds on something like dslreports.com??

However, I think the only way you can be sure where the problem is is to do some file transfer internally and do this as OS independently as possible, then try using different OS to download stuff externally.

I think from your description, you need ot just gather eveidence to present to your ISP.....

---

### Post by bLiZz247 on 2009-06-15
Thank you for your response. The download seems to be fine. 

[[IMG]http://www.speedtest.net/result/496208641.png[/IMG]](http://www.speedtest.net)

I did the speed test while under normal work use. I think you are correct in this being an OS independent problem. Internal FTP works just fine. Next I am going to see if I can figure out which ISP we are having the problem with.

---

### Post by jonobr on 2009-06-15
Hello

Coould you try another transfer protocol like scp to compare?

---

### Post by bLiZz247 on 2009-06-16
I am not very familiar with scp, but with some help I could try. I don't think it is an ISP problem though. If I use WAN1 or WAN2 without load balancing, FTP seems to work fine. However the software updates and downloads through synaptic manager still have problems. I am going to see if there is a firmware update for the router after we close.  I can't mess with it now or I'll have some very unhappy people after me.

Edit:
By the way, I am not using any software firewalls. The only firewall that should be in place is SPI in the router.

---

### Post by jonobr on 2009-06-16
mmmm.. from your test it doesn't sound like a isp issue,

If disabling the load balancing on your access method to the internet results in better speeds then that smell is definitely a rat.:D

How is the load balancing accomplished?
Is it done per session or other?
I.e. streams or sessions are handled via different wan link based on usage, or is it like Multilink PPP where the who thing is tunneled and spread/balanced across the two links?

Are you sure its load balanced and not a virtual IP giving a high availability IP address?

What are your wan links are they ISDN bundled or something of that nature?

It almost sounds as if the aggregation on your end is definitely messing things up.

I think the best thing to do, is understand if its is definitely load balancing thats being done, and if so, check the make and model of your access device and search for updates addressing this issue.

---

### Post by jonobr on 2009-06-16
By the way, should have also mentioned,

scp is easy 
from a windows box to ubuntu you can use winscp which is a gui to make things really easy,

or from ubuntu to ubuntu, you can use a gui or just use command line like so,
to put a file called file in your home dir desktop on ubuntu from the local machine it would be

```
scp file username@<hostname/ipaddress>:~/Desktop
```

To copy a file from the target it would be this 

```
scp username@<hostname/ipaddress>:~/Desktop/file .
```

note the dot at the end indicating copy to this directory.

Using scp over ftp makes for a very secure connection.
FTP if traced can be easily read.

---

### Post by bLiZz247 on 2009-06-16
The load balancing is done using weighted round robin via a Linksys RV082 small business router.
> If Load Balance (Auto Mode) is selected, it will be automatically computing the max bandwidth of WAN1 and WAN2 by using Weighted Round Robin to balance the loading.

The WANs are from two separate ISPs in case one were to fail. I have them set up with load balancing to take advantage of the extra bandwidth. If one WAN were to go down, it will just use the one that is still up.

I updated the router with the latest firmware update and it seems to be working.... that is for now. I will do some more testing tomorrow to see if the problem is gone.

---

### Post by bLiZz247 on 2009-06-17
jonobr: It appears the problem has been fixed. I find it odd to suddenly give me problems when it has been working fine for so long. Thank you very much for your time and effort!

---

### Post by jonobr on 2009-06-17
Great to hear its working.

I however, am a glass half full type of person:-(

Hopefully there was something in the update that resolved an issue which occurs over time....

Cheers

Jonobr

---

