---
title: "configuring wired network with 10.04"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by TeeSquare on 2011-02-14
Need help with entries for connecting to broadband. Was OK with ubuntu 8.04 which had boxes for DNS server, etc. The 10.04 asks for MAC address (?) and there is a space for "DHCP client ID". I don't understand these terms. I will appreciate some step-by-step instruction or example of how I may proceed, especially exact syntax for any command line work. I am in Chennai/Madras, and have a BSNL wired broadband connection to my Dell laptop. Thanks, =TeeSquare=

---

### Post by dineshs on 2011-02-15
Most of the BSNL modems are DHCP enabled by default.So the connection should work if your modem is configured in PPPoE mode(always ON mode where username and password are stored in the modem)).If you want to set IP manually ie if your modem is not DHCP enabled follow [this]("http://ubuntuforums.org/showpost.php?p=9467538&postcount=5")
If your modem is in bridge mode you need a dialler.Are you using such a dialler in windows?If yes follow [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9")

---

### Post by herdwick on 2011-02-15
Which tab are you using in Network manager - Wired or DSL ?

If the DSL box is a router you only need wired - may help if you can remember your previous settings in 8.04 and post them here.

---

### Post by TeeSquare on 2011-02-15
Thanks. In Ubuntu 8.04 there was a system> admin> network tab (missing in 10.04). In the connections tab "wired" was checked. The general tab had my computer name (tsq-laptop) for host, and a blank box for domain name. The DNS tab had 192.168.1.1 in the servers box (presumably my service provider BSNL), and nothing in search domains. The hosts tab had a list of IP addresses and aliases, the first few being:
127.0.0.1 - local host
127.0.1.1 - tsq-laptop
::1 - ip6 local host ip6 loopback
fe00:: - ip6 localnet, .... (and a few more such
I think most (or all) of these entries were generated automatically by the system, since I don't understand the jargon at all! I don't recall having any difficulties then, some two years back.
Before that I had major problems in using the internal modem for a dial-up connection, but got detailed help by e-mail/internet from some really knowledgeable people in Europe and elsewhere regarding linmodem configuration, which I followed blindly and it worked!
In 10.04 there is only the taskbar icon to edit settings, and it has a different structure. It asks for MAC address (example 00.11.22.33.44.55). Other info required is IPv4 settings, DHCP client ID, about routers and other stuff.
There may be other system settings to be made, which I can try with proper guidance. The help page gives very sketchy information, and the images are not clear at all. =TeeSquare=

---

### Post by toasterptc on 2011-02-24
> **TeeSquare said:**
> Thanks. In Ubuntu 8.04 there was a system> admin> network tab (missing in 10.04). In the connections tab "wired" was checked. The general tab had my computer name (tsq-laptop) for host, and a blank box for domain name. The DNS tab had 192.168.1.1 in the servers box (presumably my service provider BSNL), and nothing in search domains. The hosts tab had a list of IP addresses and aliases, the first few being:
127.0.0.1 - local host
127.0.1.1 - tsq-laptop
::1 - ip6 local host ip6 loopback
fe00:: - ip6 localnet, .... (and a few more such
I think most (or all) of these entries were generated automatically by the system, since I don't understand the jargon at all! I don't recall having any difficulties then, some two years back.
Before that I had major problems in using the internal modem for a dial-up connection, but got detailed help by e-mail/internet from some really knowledgeable people in Europe and elsewhere regarding linmodem configuration, which I followed blindly and it worked!
In 10.04 there is only the taskbar icon to edit settings, and it has a different structure. It asks for MAC address (example 00.11.22.33.44.55). Other info required is IPv4 settings, DHCP client ID, about routers and other stuff.
There may be other system settings to be made, which I can try with proper guidance. The help page gives very sketchy information, and the images are not clear at all. =TeeSquare=
what is that email!!?? I am trying to set up an internal modem on 10.04 and keep hitting dead  ends

---

### Post by TeeSquare on 2011-03-07
Hi toasterptc
I don't remember most of that old story. I have a Dell 1520 Inspiron laptop which came with an internal modem "alsa-driver-1.0.17-hda/alsa-kernel/pci/hda/hda_codec.c" (I don't know what this means - just copied/pasted from an old message!). There was a lot of exchange regarding Conexant and Linuxant. It was the Linmodems.org website which helped me, and I am quoting below from one of their long documents. The help consisted of running a 'package' which they sent that explored and extracted my system details, and reporting the output as a text file. They ran it through their own system and generated a set of files with detailed instructions on how exactly I was to apply them to my specific laptop. I was really impressed by the free help they provided. Of course it may be quite irrelevant if you have some other kind of system or modem! Hope you can check the website and see if it is useful for you. Sorry I'm totally ignorant in these matters.

QUOTE:
 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-19-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters. ... UNQUOTE

Sorry for the delay -- I wasn't checking this thread any more because I wasn't getting any useful advice, and had to look elsewhere to solve my broadband problem. =TeeSquare=

---

