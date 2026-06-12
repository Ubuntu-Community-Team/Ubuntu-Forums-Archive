---
title: "How to share filtered internet"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by Abhi Kalyan on 2009-01-12
[LEFT][LEFT][SIZE=2]**The Problem:**[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]To create an internet gateway through which all my Windows clients gain access to the internet, but with the following specifications:[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]1.The proxy should be transparent[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]2.Client machines should not be able to override Dansguardian by manual proxy setting.[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]3.Should be able to add remove exclusions from clients through a browser[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]**Necessary applications:**[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]1.Apache[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]2.PHP[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]3.Webmin[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]4.Squid[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]5.Dansguardian[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]6.Dansguardian Module for webmin[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]Please install in the above given sequence. [/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]**Configuration:**[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]1.Apache: No configuration necessary[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]2.PHP: You might get an insufficient memory error, don&#8217;t worry, check the .ini file and change the memory to at least 24 MB, default is around 16 MB.[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]3.Webmin: No configuration necessary[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]4.Squid: We need to make this transparent and we should allow squid to listen only to local host, thus stopping manual override. [(i.e.) users cannot give the gateway IP and 3128 port and access internet without going through Dansguardian content filter.][/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]a.GOTO> /etc/squid/squid.conf[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]b.Search for: http_port 3128[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]c.Change it to : http_port 127.0.0.1:3128 transparent[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]d.Save file[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]e.Restart squid[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]f.Now squid is transparent and listens only to the localhost and not on any eth![/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]5.Dansguardian[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]a.GOTO> /etc/Dansguardian/ Dansguardian.conf[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]b.Search for: UNCONFIGURED[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]c.Comment it out by placing a # in front of this word[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]d.Change filterip = <the IP where you want your clients to listen> [this is the gateway IP that you give to your client, either through DHCP or through manual configuration][/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]e.Filterport can be left alone[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]f.Change proxyip=127.0.0.1 [we have already configured squid to be available only at this IP][/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]g.Proxyport can be left alone unless you have configured squid otherwise[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]h.Restart Dansguardian[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]i.Now when you set your clients proxy to <gateway IP> and port:8080, you should not be able to access offensive sites.[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]6.Now please download Dansguardian module for webmin from [http://www.webmin.com/](http://www.webmin.com/)[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]7.Install this module in webmin[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]**The final step:**[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]Here we will direct all traffic from client machine to TCP:80 to 8080:
I initially got the procedure from here:
[http://ubuntuforums.org/showthread.php?t=320733&highlight=bmathis](http://ubuntuforums.org/showthread.php?t=320733&highlight=bmathis)
But the data has been editied and is now available here:
[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]1.Use the procedure given here: [http://ubuntuforums.org/showthread.php?t=91370&highlight=transparent%2C+squid%2C](http://ubuntuforums.org/showthread.php?t=91370&highlight=transparent%2C+squid%2C)
[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]A beautiful HOWTO by bmathis that actually laid out the foundation for the current HOWTO that you are reading (Thank you [Bmathis]("http://ubuntuforums.org/member.php?u=73443")!!)
[/SIZE][COLOR=Purple]
Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

    # ifconfig ethX ip      

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

    # iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE       

where ethX is the network card that the Internet is coming from 

    # echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get: 

    # apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

    # /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

    # dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

    # gedit /etc/sysctl.conf

8. Reboot. (Optional)
[/COLOR]                 
[/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]2.GOTO>Webmin>Linux firewall>NAT>add rule[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2][IMG]http://ubuntuforums.org/attachment.php?attachmentid=103310&stc=1&d=1234594740[/IMG][/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]a.Please make sure that you replace the given networks with your own!![/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]Now even without manually configuring your clients they should be able to get internet connectivity that is filtered through Dansguardian.[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]**WATCH OUT:**[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]I made some mistakes that frustrated me beyond words, am adding them here so that it can save you a load of frustration.[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]1.Please set your gateway and primary DNS server to the Linux box where Dansguardian runs[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]2.Please restart all applications after each configuration change[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]3.Please restart the Linux box after completion of all settings before commencing testing[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]4.Please see that in your browser the proxy setting is set to no proxy[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]5.Please see that your Ethernet card is configured properly[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]6.Please be relaxed, cause &#8220;if it has to go wrong it will&#8221;[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]**Example demonstration:**[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]In my case I have a windows 2003 server as AD with close to 200 clients. This server is named &#8220;mango&#8221;. Have a separate Linux box for serving internet; I call it &#8220;tango&#8221;.[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]Tango has 2 Ethernet cards, eth0 and eth1.[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]1.Eth0: is connected to a broadband router directly and carries an IP of 192.168.0.1[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]2.Eth1: is connected to the LAN  switch with a IP of 10.0.0.2[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]3.Then I went the bmathis way[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]4.Then configured the applications[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]5.Then set the firewall[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]6.Then restarted everything in sequence[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]7.Then restarted the computer/system[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]8.Then repaired clients IP[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]9.Waited for some 15 minutes[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]It was only after this that I could get the client to surf the internet safely through a filter.[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=2]**Thank you**[/SIZE]
[SIZE=3][COLOR=Orange][SIZE=1][FONT=Arial]Note: AM very sorry for not completing this HOWTO before, am indebted to many people in this forum and the organization that hosts this forum. I had started in some places but failed miserable and could not complete them
I request the forum admins to 
[/FONT][/SIZE][/COLOR][/SIZE]
[SIZE=3][COLOR=Orange][SIZE=1][FONT=Arial]please delete my thread: [http://ubuntuforums.org/showthread.php?t=638762](http://ubuntuforums.org/showthread.php?t=638762)
This thread I started, but could not finish.[/FONT][/SIZE]
[/COLOR][/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=3]Now that it&#8217;s finished your welcome to test this out.[/SIZE][/LEFT]
[/LEFT]
  [LEFT][LEFT][SIZE=3]**All the very best**[/SIZE][/LEFT]
[/LEFT]

---

### Post by Abhi Kalyan on 2009-02-14
At last i completed this post!!

---

### Post by arapozo on 2009-02-14
Than you for this great post. I would like to ask you a question.

Remember as we talked in the other thread about how to do this, I have problems setting Linux in dual NIC. It sets two default gateways and that is wrong. It should be default gateway for internet traffic and a static route for LAN traffic, since i have more than one network on the LAN side. Did you have this problem?

Is there a rule to make the Firewall reject all incoming traffic from other machines to dansguardian, I only want Linux machine to be able to browse and nobody else.

---

### Post by Abhi Kalyan on 2009-02-14
> **arapozo said:**
> Than you for this great post. I would like to ask you a question.

Remember as we talked in the other thread about how to do this, I have problems setting Linux in dual NIC. It sets two default gateways and that is wrong. It should be default gateway for internet traffic and a static route for LAN traffic, since i have more than one network on the LAN side. Did you have this problem?

Is there a rule to make the Firewall reject all incoming traffic from other machines to dansguardian, I only want Linux machine to be able to browse and nobody else.

Please feel free to correct me if am wrong.
1. you have dual NIC,
1a. The one that connects to the internet router needs a gateway
1b. the one that is connected to the local LAN [B]should not have a gateway assigned to it.
[/B]2. each seperate networks will have seperate gateways, onlt those that have the intrenet providing computers ip as a gateway will be able to access the internet.

Am still not too clear with the question, could you please give me more clarity *if the above suggestion is not helping you?*

---

### Post by arapozo on 2009-02-14
This is the general Idea:

Internet - Firewall - **Linux** - LAN

What I'm going to do is have the users connect with Nomachine NX client to FreeNX on the linux mahcine and run firefox. This machine will also have squid + dansguardian for filtering. But people cannot use the Linux directly as a proxy even through dansguardian. The internet browsing will only be available if you connect to the remote session on the linux machine.

That's why I only want the Linux machine to accept incoming connections on port 22 and maybe port 1000 for webmin. And all outgoing blocked except for HTTP, HTTPS and FTP.

I've got FreeNX ready and squid + dansguardian is working but I'm missing the blocking part. Also for testing I was using a machine with two nics, one with static address and one with dhcp. The problem was that when I enabled the one with dhcp linux automatically configured two default gateways one on each nic.

---

### Post by HermanAB on 2009-02-14
Hmm, Mandriva has wizards for Connection sharing and Squid-Cache with Dan's Guardian - clicketyclick - done.  Getting it all to work manually can be quite a chore.

I'm not sure what you want the Free NX thing for?  Squid should act as a transparent proxy to all machines behind it.

Cheers,

Herman

---

### Post by arapozo on 2009-02-16
I just gave up on the routing of the traffic and just added a couple of rules on iptables to drop traffic based on the user that requested it. The only downside is that the users have to manually configure the proxy settings.

Now I want to ask you about updating the blacklists for dansguardian, what lists do you use and how do you go about updating them.

Thanks for the howto.

---

### Post by Abhi Kalyan on 2009-02-17
> **arapozo said:**
> I just gave up on the routing of the traffic and just added a couple of rules on iptables to drop traffic based on the user that requested it. The only downside is that the users have to manually configure the proxy settings.

Now I want to ask you about updating the blacklists for dansguardian, what lists do you use and how do you go about updating them.

Thanks for the howto.

Sorry for not replying immediatly yesterday.

If your requirement is as below:
1. only the linus box should be able to browse internet and not any other machine.

All you have to do is change the listening IP to the local port,
open: /etc/dansguardian/dansguardian.conf
change filterip to 127.0.0.1

Now your dansguardian will only listen to the local system and not anything else,
If you followed the howto above, then squid too is listening only to the local system
and the iptables moves all data thaat is coming from TCP 80, outside to 8080 on your external ip.
You can leave that rule as it will not affect anything now, if it does then direct all traffic in the above rule to a non existent port, probably the port on whihc your local apache is listening.

Now in the current setup no external systems except your linux box will be able to access internet.

and even if it does it will be through dansguardian!!

---

### Post by arapozo on 2009-02-17
Thank you very much for your help, I'm almost ready to deploy this solution, only one thing that's missing is the updating of the blacklists, phrases and general housekeeping of dansguardian.
I tried the webmin module but it doesn't work that good, How do you do it, I mean, which blacklists you download and import into dansguardian and how you go about adding sites and stuff.
I know how to add a blacklisted site manually but I want to add freely available blacklists like the ones on squidguard.org.

---

### Post by Abhi Kalyan on 2009-02-17
> **arapozo said:**
> Thank you very much for your help, I'm almost ready to deploy this solution, only one thing that's missing is the updating of the blacklists, phrases and general housekeeping of dansguardian.
I tried the webmin module but it doesn't work that good, How do you do it, I mean, which blacklists you download and import into dansguardian and how you go about adding sites and stuff.
I know how to add a blacklisted site manually but I want to add freely available blacklists like the ones on squidguard.org.

Am sorry about that one:
You might want to read this link.
[http://dansguardian.org/?page=blacklist](http://dansguardian.org/?page=blacklist)
[http://urlblacklist.com/](http://urlblacklist.com/)

I have'nt yet updated my blacklisting,
Once i get around that point i will def load the date to the HOWTO!
Cheers

---

### Post by arapozo on 2009-02-17
Maybe somebody that sees this thread can help us with that.
What you get from most blacklist sites is a tar file with all the lists, maybe a little help on importing them to dansguardian. Squidguard.org has a couple.

---

### Post by arapozo on 2009-02-20
I don't know if any of you have tried it but when I look at the dansguardian logs, it doesn't show the username that requested a page.
Any idea why? The users are all linux users browsing locally.

---

### Post by Abhi Kalyan on 2009-02-20
> **arapozo said:**
> I don't know if any of you have tried it but when I look at the dansguardian logs, it doesn't show the username that requested a page.
Any idea why? The users are all linux users browsing locally.

Well you try out the following:
connect the linux box to a ADS
or RUN ADS using SAMBA
or RUN DNS and DHCP on this server so that others get the ips from your system
or you could have this linux box autheticate other users.
These methods a bit tough, but not impossible, been trying to do the same

---

### Post by arapozo on 2009-02-20
The users are authenticating in the linux box, but when I check the logs squid and dansguardian the user field is empty.

---

