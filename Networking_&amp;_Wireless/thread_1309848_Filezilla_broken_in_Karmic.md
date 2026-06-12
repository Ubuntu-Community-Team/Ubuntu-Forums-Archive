---
title: "Filezilla broken in Karmic?"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by Jim_in_Germany on 2009-11-01
Hi,
I just upgraded to 9.10 (yay!) with a fresh install.
Everything is working well, except Filezilla.
Whenever I try to connect to a remote site  I get the message "connection timed out".
When I run the connection wizard I get as far as the "test" part, however when I push the test button to test the connection, I get the error message:

```
Connecting to probe.filezilla-project.org
Response: 220 FZ router and firewall tester ready
USER FileZilla
Response: 331 Give any password.
PASS 3.2.7.2
Response: 230 logged on.
Checking for correct external IP address
IP 192.168.2.103 bjc-bgi-c-bad
Response: 510 Mismatch. Your IP is 80.xxx.xxx.xxx, ia-bec-bah-ceg
Wrong external IP address
Connection closed
```

I have tried every possible combination of settings in the wizard (active / passive mode etc)

When I enter the external ip of my router (instead of "ask OS for external ip") I still cannot connect to a remote site and my router crashes, needing a hard reset.

I have just downloaded and installed gftp and that works fine, so I can exclude the fact that it is a problem with my configuration.

Can anyone help?

---

### Post by yeleek on 2009-11-01
Are you using exactly the same hostname in the other ftp client?

[http://forum.winhost.com/showthread.php?p=560](http://forum.winhost.com/showthread.php?p=560)

---

### Post by Jim_in_Germany on 2009-11-01
Yup, everything is absolutely identical.
I also had all of my sites saved in an xml config file, so following the new install I could import everything at the touch of a button (also eliminating the possibility I mistyped something).

Also, for anyone else who looks at the link you posted, "probe.filezilla-project.org"  is the address that the connection wizard automatically tries to connect to, so as to establish connectivity.

Thanks for your help

---

### Post by Jim_in_Germany on 2009-11-01
Update.
I also have Vista Business running in VirtualBox on my Karmic install.
I just downloaded FileZilla Portable (same version), imported my settings and everything works fine.
Really seems to be a Karmic issue ...

---

### Post by yeleek on 2009-11-02
Not that it helps you but just installed filezilla.  Created new site, specified host, username, password and connected straight away.  Didn't even specify the port.

Take it you've tried a new site only specifying these three items?

---

### Post by Jim_in_Germany on 2009-11-02
Yup, unfortunately that was the first thing I tried.
Same result:

Resolving address of www-whatever...
Error:	Connection timed out
Error:	Could not connect to server
Status:	Waiting to retry...
Status:	Resolving address of www-whatever...
Error:	Connection timed out
Error:	Could not connect to server

:(

I've also noticed that Thunderbird, Firefox and SSH are all extremely sluggish after the upgrade.

FF I fixed by edditing about:config and changing the following entries from false to true:

network.dns.disableIPv6
network.http.pipelining
network.http.proxy.pipelining

Is there maybe anywhere else on my system that I could tweak to speed things up?

Am grateful for any advice.

---

### Post by yeleek on 2009-11-02
Hmm

Silly and may mean nothing whatsoever, but I've disabled IP6 all together.

[http://ubuntuforums.org/showthread.php?t=1306301](http://ubuntuforums.org/showthread.php?t=1306301)

And I'm having no issues with Karmic + Filezilla...

---

### Post by Jim_in_Germany on 2009-11-02
Hi,
Thanks a lot for that.
I just disabled IPv6 and had mixed results.
Thunderbird is back to its usual fast self :D
Unfortunately SSH and Filezilla still remain sluggish and broken (in that order).
Nonetheless, speeding up T.bird improves my life no end, so thanks again!
BTW are you using Karmic 64 bit?

---

### Post by yeleek on 2009-11-02
Nah sorry 32-bit.  This is a strange one...  Will be interested to hear the outcome - can you let me know pls?  I'm afraid I'm outta ideas.

---

### Post by slakkie on 2009-11-02
I'm running 32 bit + filezilla, no problems here. Try to export your sites and import them into a different filezilla, see if you have the same issue..

---

### Post by Jim_in_Germany on 2009-11-02
I also asked for help on the Filezilla forum and got told that the problem was with my router:
[http://forum.filezilla-project.org/viewtopic.php?f=2&t=13672&p=52964#p52964](http://forum.filezilla-project.org/viewtopic.php?f=2&t=13672&p=52964#p52964)
As I agreed there I will get hold of a new router and see if that makes a difference.
Of course I will post back the answers here, but it may be a while as I am off on holiday for one week.
In the meantime I would be glad to hear from someone running FileZilla with no problems on a 64bit install of Karmic Koala.

---

### Post by yeleek on 2009-11-03
Your router?  When another FTP client works?  That seems to 'smell' a bit as a reason...  hope you get it sorted.

---

### Post by Jim_in_Germany on 2009-11-10
Hi,
I fixed the problem, sort of ...
As I mentioned before, I had also noticed that SSH had become a bit sluggish, so I increased the timeout on Filezilla (Edit -> Settings -> Transfer) and now Filezilla can connect to remote sites (it was just timing out too soon).
Although this solves the Filezilla problem for now I am still not 100% satisfied with the network connectivity situation under Karmic.
I'll have to have a think about things and maybe I'll start a new thread if I can't figure out why this is happening.

---

### Post by burstweb on 2009-11-16
I also had the same problem after updating to 9.10. The solution of increasing the time out time worked. Would be nice to find a solution to speed the resolving of the domain up.

---

### Post by Jim_in_Germany on 2009-11-19
Update:
I gave my PC a static ip address and then entered the addresess of the two name servers that the router was using into /etc/resolv.conf
This solved the problem completely.
I was beginning to think that the DNS server in the router was broken (like the nice folks in the Filezilla forum were saying), so thanks for sharing that burstweb.
Has anyone else been having any trouble with FTP / SSH / HTTP and (64 bit) Karmic Koala??

---

### Post by utnubuuser on 2009-12-16
Hello jim_in_germany

Any chance you might post an exact how-to here?  Like how do you "give" your computer a static ip address, and how do you add that to which file?

Thanks

---

### Post by Jim_in_Germany on 2009-12-16
Hi,

Yeah, it was pretty easy. I unfortunately don't have Karmic installed any more, but I'll explain what I did anyway.

First of all find your ISP's DNS servers.
For me, my ISP is Deutsche Telekom and my router is a Speedport W 502V.

I logged on to my router and looked at Status -> Details -> Internet Connection. There I found the IP addresses of two DNS servers.

After that I did the following to set a static ip:
1. Rightclick on the Network-Manager-Applet in the Panel
2. Click on "Edit Connections"
3. Create a new wired one and name it as whatever 
4. go to IPv4 Tab
5. Enter the following:
Method - Manual
Address - desired static ip
Netmask - 255.255.255.0
Gateway - router ip (e.g. 192.168.2.1)
DNS Server - ip of your providers DNS servers
Search domain - router ip (not too sure what this is)

Click ok, 
type "sudo ifconfig eth0 down" 
followed by "sudo ifconfig eth0 up" (presuming eth0 is your current lan port) and that's it.
(I'm sure there's a better command along the lines of init.d restart networking, but I couldn't remember this off the top of my head).

As a point of interest, I tried setting a static ip via  /etc/network/interfaces, but this had absolutely no effect - I even deleted everything out of this file and Karmic Koala still got its IP from the router. 

Oh well. Hope this helps.

---

