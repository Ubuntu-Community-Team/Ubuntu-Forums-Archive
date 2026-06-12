---
title: "Changing DNS in Ubuntu 12.10 and 12.04"
date: 2012-10-30
forum: Networking &amp; Wireless
---

### Post by w1ll1am on 2012-10-30
Okay so I was in the process of making Firefox perform Google searches from the address bar and realised that I was being redirected to my ISP's page not found screen. This I determined was because of the DNS that was set by default in Ubuntu to 127.0.1.1 or 127.0.0.1. I went to change this to Googles DNS 8.8.8.8 and 8.8.4.4. To do this in previous releases  ```
 gksudo gedit /etc/resolv.conf
```Change this:
```
nameserver 127.0.1.1
```to this:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```This no longer works in Ubuntu 12.10 maybe not 12.04 either the only way that I found around this was to:
```
 gksudo gedit /etc/resolvconf/resolv.conf.d/head 
```and to add this:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```at the bottom. Then run this code to update the resolv.conf file
```
 sudo resolvconf -u
```If there is a better way to do this please let me know as I am sure others would appreciate it was well.

---

### Post by jdthood on 2012-10-31
The recommended way of configuring DNS is to add nameserver addresses and search domain names via your interface configurer: ifup or NetworkManager.

If you are using ifup, edit /etc/network/interfaces.  If you have, for example, one interface eth0 over which you can access nameservers with addresses 1.2.3.4 and 5.6.7.8, add a "dns-nameservers" option such that the stanza looks like the following.
[INDENT]auto eth0
iface eth0 inet static
    [INDENT]address ...
        netmask ...
        gateway ...
        dns-nameservers 1.2.3.4 5.6.7.8[/INDENT]
[/INDENT]
If the interface is configured using the dhcp method then you can still add the dns-nameservers option but the addresses received from the DHCP server take precedence. It is possible to change this by editing the /etc/resolvconf/interface-order configuration file.

If you are using NetworkManager, enter the addresses in the field network-indicator | Edit Connections... | <connection-name> | Edit... | IPv4 Settings | Additional DNS Servers. If you don't want to use the DHCP-supplied nameserver addresses then on the same tab change the Method from "Automatic (DHCP)" to "Automatic (DHCP) addresses only".

---

### Post by w1ll1am on 2012-11-02
> **jdthood said:**
> The recommended way of configuring DNS is to add nameserver addresses and search domain names via your interface configurer: ifup or NetworkManager.

If you are using ifup, edit /etc/network/interfaces.  If you have, for example, one interface eth0 over which you can access nameservers with addresses 1.2.3.4 and 5.6.7.8, add a "dns-nameservers" option such that the stanza looks like the following.[INDENT]auto eth0
iface eth0 inet static[INDENT]address ...
        netmask ...
        gateway ...
        dns-nameservers 1.2.3.4 5.6.7.8[/INDENT][/INDENT]If the interface is configured using the dhcp method then you can still add the dns-nameservers option but the addresses received from the DHCP server take precedence. It is possible to change this by editing the /etc/resolvconf/interface-order configuration file.

If you are using NetworkManager, enter the addresses in the field network-indicator | Edit Connections... | <connection-name> | Edit... | IPv4 Settings | Additional DNS Servers. If you don't want to use the DHCP-supplied nameserver addresses then on the same tab change the Method from "Automatic (DHCP)" to "Automatic (DHCP) addresses only".

Awesome I will give that a try thanks for the reply hope it helps others. sounds much simpler lol.

---

### Post by w1ll1am on 2012-11-05
Well today I was at school using my laptop with the provided google DNS and it was set up with the method that I first mentioned. I could not access my schools home page and I was not sure why. 

I though back to what I had changed recently and the only thing was the DNS. I change all the settings back to default and then set up the DNS with the method in the second post and all worked good. So method two is a better choice.

I believe that method one will work in a home network and with a desktop that is set on the same ISP at all times. Any other computer should probably use the second method.

---

### Post by dewapur on 2013-03-19
Last night same problems happened to me. The network manager, connection information showed the DNS addresses but still the browser unable to show the pages. So I add the nameservers in /etc/resolvconf/resolv.cond.d/base. And it works. In my understanding that /etc/resolv.conf is not manually configured again but it is driven by resolvconf.

I tried the second post way with change the eth0 to wlan0 (I use wireless network) and it make my wireless won't work. It seem the second post way is only for cable network. So may it helps other with wireless network

---

### Post by jdthood on 2013-03-20
When using NetworkManager to configure interfaces the correct way to add nameserver addresses is not to put them in /etc/resolvconf/resolv.conf.d/base but to enter them into the field Edit Connections | <connection-name> | Edit... | IPv4 Settings | Additional DNS servers.

---

### Post by alej0 on 2013-03-27
> **w1ll1am said:**
> I though back to what I had changed recently and the only thing was the DNS. I change all the settings back to default and then set up the DNS with the method in the second post and all worked good. So method two is a better choice.

I believe that method one will work in a home network and with a desktop that is set on the same ISP at all times. Any other computer should probably use the second method.

Method two doesn't work. What you have done is removing the DNS from your wireless connection and then added them to you wired connection. So even without step two and a clean setup you are able to reach you schools home page because they give you a DNS when you connect to their network.

---

### Post by alej0 on 2013-03-27
```
 gksudo gedit /etc/resolvconf/resolv.conf.d/head 
```and to add this:

What about this line in this file?

```

#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

```

---

### Post by alej0 on 2013-03-27
This should be the right way to change the DNS servers without loosing the dnsmaq functionality, making it global for all you connections through dhcp and keeping NetworkManager aware of which DNS servers are you using.

Editing the file
```
sudo gedit /etc/dhcp/dhclient.conf
```

Adding your DNS(s) server(s) here.
```
prepend domain-name-servers x.x.x.x, y.y.y.y;
```

Source:

[http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf](http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf)

---

### Post by jdthood on 2013-03-28
Adding
```

prepend domain-name-servers x.x.x.x, y.y.y.y;

```
to /etc/dhcp/dhclient.conf is one of several possible ways to add nameserver addresses. This way causes x.x.x.x and y.y.y.y always to be prepended to the list of DHCP-obtained nameserver addresses, no matter what the network. If you only ever connect to one network then that's fine, otherwise it's less than ideal.

If you connect to different networks then it's better to use the features of either NetworkManager of ifupdown that support different configurations for different networks. In the NetworkManager case you use the Connection Editor to define multiple "connections"; for each connection you can enter nameserver addresses in the "Additional DNS Servers" field as I described earlier. In the ifupdown case you define multiple "logical interfaces" in /etc/network/interfaces; in each iface stanza you can enter nameserver addresses on a "dns-nameservers" line as I described earlier.

Cheers!

---

### Post by Voliax on 2013-04-24
When i restart my laptop DNS thing removes. Are there any way to make it persistent?

---

### Post by jdthood on 2013-04-24
In Ubuntu 12.04 and later you shouldn't edit /etc/resolv.conf. Instead you enter nameserver information into the tool that configures your network interfaces.

On Ubuntu Desktop (which uses NetworkManager to configure network interfaces) add a nameserver address to the field: network-indicator | Edit Connections... | <name> | Edit... | IPv4 Settings | DNS servers

On Ubuntu Server (which configures network interfaces with ifupdown) add a nameserver address on a "dns-nameservers" option line in the stanza starting with "iface <name> inet ...". E.g.,

    iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        gateway 192.168.0.1
        dns-nameservers 192.168.0.244

Reboot after making changes.

---

### Post by quantalq on 2013-05-17
I am using ubuntu 12.10 desktop version with PPPOE connection. (dual mode with windows8)
I am not able to access some of the websites like
[www.taxila.bits-pilani.ac.in]("http://www.taxila.bits-pilani.ac.in") and [www.thepiratebay.org]("https://www.google.co.in/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&sqi=2&ved=0CDgQjBAwAQ&url=https%3A%2F%2Fthepiratebay.sx%2Ftag%2Fthepiratebay.org&ei=kDKWUa77LMLTrQeu1IGAAg&usg=AFQjCNEWoCdTj_UmkiAzcIlcv1Q-xZkjUQ&sig2=RpjxzJ64b3qtWZeAIhigGA&bvm=bv.46751780,d.bmk")

ping command also doesn't work for these sites.

3521:~$ ping taxila.bits-pilani.ac.in
PING taxila.bits-pilani.ac.in (202.78.175.231) 56(84) bytes of data.
^C
--- taxila.bits-pilani.ac.in ping statistics ---
42 packets transmitted, 0 received, 100% packet loss, time 41327ms
3521:~$ 

I tried adding DNS server 8.8.8.8 and 8.8.4.4 but it is not working.
but when I use windows8 these websites works fine.

Should I upgrade ubuntu to 13.04?
kindly suggest some workaround.

---

### Post by charliehagies on 2013-05-20
How I resolved my DNS problem, luckily I have 6 PC's/Laptops running Ubuntu in my Office to compare different configurations. I decided to upgrade 2 systems from 12.04 to 12.10. I have been continually upgrading for a number of years so I suspect that maybe where the problem stems from the fact that the machines have been upgraded and not had a "Vanilla Installation".

Problem ... DNS resolution ceases to work after upgrading to Ubuntu 12.10

Reading many posts and not finding a satisfactory explanation in any post. I compared the working DNS system on my old system and found the following on a working system "/etc/resolv.conf" was blank and secondly was a link to /run/resolvconf/resolv.conf, on the faulty system /etc/resolv.conf was blank and a file not a link, the following steps were followed to resolve the problem!

Step by Step Resolution
[LIST=1]
[*]Open a Terminal
[*]gksu nautilus (you need to be root to change the settings in "/etc and /run" folders)
[*]navigate to /run/resolvconf/resolv.conf, highlight the file (don't open the file)
[*]right click on the /run/resolconf/resolv.conf
[*]click "Make Link"
[*]A file called "link to resolv.conf" will be created in the /run/resolvconf/resolv.conf folder
[*]After creation of the file, right click on the created link and cut the file from the folder for later use
[*]Navigate to /etc and rename /etc/resolv.conf to resolvold.conf (make sure you are in the /etc before commencing)
[*]After completing the rename, right click and paste "link to resolv.conf"
[*]Rename "link to resolv.conf" to "resolv.conf"
[*]Close all apps and open your browser and test your Internet name resolution
[/LIST]

Summary
If a link does not exist from /etc/resolv.conf to /run/resolvconf/resolv.conf create one!

This resolved the problem I had and my upgraded system works smoothly, hope it helps! :)

---

### Post by jdthood on 2013-05-20
> **charliehagies said:**
> I compared the working DNS system on my old system and found the following on a working system "/etc/resolv.conf" was blank and secondly was a link to /run/resolvconf/resolv.conf, on the faulty system /etc/resolv.conf was blank and a file not a link


Hi. You are not the first to experience this. Please report your experience with as many relevant details as possible to bug #1000244.

* [https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244)

See my comment #121 for a summary of known causes of this phenomenon.

* [https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/121](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/121)

Even though there are many known causes for the absent symlink, it is still possible that there is a bug in the resolvconf package, so the resolvconf maintainers are very interested to hear about your case.

> **charliehagies said:**
> 
the following steps were followed to resolve the problem!

Step by Step Resolution
[LIST=1]
[*]Open a Terminal
[*]gksu nautilus (you need to be root to change the settings in "/etc and /run" folders)
[*]navigate to /run/resolvconf/resolv.conf, highlight the file (don't open the file)
[*]right click on the /run/resolconf/resolv.conf
[*]click "Make Link"
[*]A file called "link to resolv.conf" will be created in the /run/resolvconf/resolv.conf folder
[*]After creation of the file, right click on the created link and cut the file from the folder for later use
[*]Navigate to /etc and rename /etc/resolv.conf to resolvold.conf (make sure you are in the /etc before commencing)
[*]After completing the rename, right click and paste "link to resolv.conf"
[*]Rename "link to resolv.conf" to "resolv.conf"
[*]Close all apps and open your browser and test your Internet name resolution
[/LIST]

Summary
If a link does not exist from /etc/resolv.conf to /run/resolvconf/resolv.conf create one!

This resolved the problem I had and my upgraded system works smoothly, hope it helps! :)

Another way to recreate the symbolic link is to open a Terminal window and run the following command.
```

sudo dpkg-reconfigure resolvconf

```

Thanks!

---

### Post by alvinmoneypit on 2013-06-09
I'm trying to stabilize my DNS service as it seems to disappear.  Apparently, this is a known phenomena, as it has been posted on "[Open DNS]("https://store.opendns.com/")", my dns provider.  I recently reset my DNS and appears to be working after rebooting my 12.04.2 install.  What I'm wondering about is [this set of instructions]("https://store.opendns.com/setup/operatingsystem/ubuntu") from Open DNS:
8. NOTE:

To avoid having your settings get revoked after reboots, or after periods of inactivity, you may need to make the following changes via the command line:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    NOTE: The dhclient.conf location may vary depending on you linux distribution.

    To locate the correct file you can use:
    $ sudo find /etc -name dhclient.conf

    $ gksudo gedit /etc/dhcp3/dhclient.conf
    # add the following line to the document before the 'require subnet-mask' command

    supersede domain-name-servers 208.67.222.222,208.67.220.220;

    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name."

I tried working through these, but they didn't seem to be working as is often the case when you find solutions on the internet.  I'm not Ubuntu savvy enough to know if these are the correct commands or not - does anyone know what is the correct way to stabilize my DNS so it doesn't keep disappearing?  Please be specific as I'm not really up to speed on terminal commands and knowing how they work.   I followed the instructions (I think) in post #12, but after simply adding the server addresses in network edit, when I noticed slow connectivity and decided to check, the server addresses  were gone.Thanks.

---

### Post by lovevn on 2013-06-25
well thank you a lot, @w1ll1am (what does your name mean? it seems complex :D )
ISP has prevented some websites so I need change DNS to log in them. :(

---

### Post by archeryguru2000 on 2013-09-06
YEAH!  I had a similar issue with a recent install of 12.04.  I could ping 173.194.70.101, but I could not ping google.com.  I realized this was probably a DNS issue and executing the following command resolved this.

```

sudo dpkg-reconfigure resolvconf

```

Thanks jdthood!

---

