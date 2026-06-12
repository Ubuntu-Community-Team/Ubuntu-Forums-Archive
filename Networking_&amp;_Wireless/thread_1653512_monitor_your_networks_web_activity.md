---
title: "monitor your networks web activity"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by philipballew on 2010-12-27
i need to have the ability as network administrator to see what everyone connected to our internet is doing, the sites their visiting and emails being sent. how can i do this?

---

### Post by philipballew on 2010-12-27
anybody?

---

### Post by sasa.net on 2010-12-27
Things you want to do are called WLAN hacking metods  depend of what do you want to do there are several tools included in Backtrack 4 R2.  or you can install these tools manually in ubuntu with apt-get install command...  if you have WLAN network created you have to use these tools: ettercap, urlsnarf, driftnet, nmap, wireshark, msfconsole, ssl strip etc (there are many of them)  if you have multiple clients on your WLAN network connected you can hack them with just a little knoweledge.  if you want to hack their facebook, gmail, yahoo or any other account which uses https protocol you can do this by using ettercap and sslstrip.  if you want to capture all the pictures, audio and video media they are looking for you can capture them by using driftnet tool  if you want only to capture url adresses they are wisiting you will use urlsnarf tool  if you want to hack into your client computer under command shell or if you want to see your's clients desktop and do what ever you want you will use msfconsole and exploits  if you want to send an trojan to your victim client you will use msfconsole ad well  if you want keylog your victims client keyboard you will use key_scan command under interpreter access  if you want set an backdoor to your clients machine you will use netcat or similar tool.  if you want to hack WLAN network you will use aircrack-ng and other ***-ng tools   ok enough ....  THE MOST EASY WAY IS TO INSTALL BACKTRACK 4 R2  and use these tools  tell us what do you want to do exactly and you will get the answer :)

---

### Post by philipballew on 2010-12-28
i need to know what sites are being visited and what items are being downloaded

---

### Post by tgalati4 on 2010-12-28
etherape

driftnet

For email, it depends on what machine is hosting the mail handler.  You can normally just go into /var/spool/mail and read the mail with admin privileges.

Since you are in California, you should understand California Labor Law as it pertains to employee notification/handbook/policies concerning computer privacy and company-provided computer assets.

---

### Post by sasa.net on 2010-12-28
ex:  urlsnarf -i wlan0  assuming your interface is wlan0 to check out type this command:  iwconfig  this command will sniff wisited url-s on your network  ex: driftnet -a -d /root/images -s -p -i wlan0   (where /root/images must exist as temporary directory) this command will sniff downloaded images and audio, and will save them into /root/images  press driftnet -h for more options and help  ex: ettercap -TqM ARP -i wlan0 // //  this command will sniff packets from all the hosts on your WLAN network NOTE: if you want to sniff packets from particular hosts you will use following command then: ettercap -TqM ARP -i wlan0 /192.168.1.1/ /192.168.1.23/  192.168.1.1 is your gateway ip address 192.168.1.23 is your victims ip address  to find out what ip address your victim has you will use nmap tool ex:  nmap 192.168.1.1/32  this command will scan for all host being up on the WLAN it will ping your hosts, send SYN packets to them and scan for open ports from 1-1000 autput will be something like this:  nmap 192.168.1.1/32  Starting Nmap 5.35DC1 ( [http://nmap.org](http://nmap.org) ) at 2010-12-28 18:54 CET Nmap scan report for 192.168.1.1 Host is up (0.0021s latency). Not shown: 999 filtered ports PORT    STATE SERVICE 443/tcp open  https  Nmap done: 1 IP address (1 host up) scanned in 5.71 seconds  if you want skip pingin your host use this:  nmap 192.168.1.1/32 -sP  to fin out wha OS your vivtm has use this  192.168.1.23 -O  (if this is his adrress)

---

### Post by SeijiSensei on 2010-12-28
> **philipballew said:**
> i need to know what sites are being visited and what items are being downloaded

Look into [transparent proxying with the Squid proxy cache]("http://www.deckle.co.za/squid-users-guide/Transparent_Caching/Proxy").  If you run it on a Linux router sitting between the Internet and your local network, you can push all HTTP requests through it via iptables.  Squid will keep a log of every object downloaded by date and IP address.  You can get summaries of the logs with [SARG]("http://sarg.sourceforge.net/").

---

