---
title: "ERROR: getaddrinfo: Name or service not known"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Jeff_Illingworth on 2009-01-19
Hello,

     I have recently begun experience problems with my remote desktop connection to all Windows XP and Windows Server 2003 computers that I deal with here at work. I first ran into this problem this past Thursday (15 January 2009) and have been unable to resolve it. I keep getting an error message that states "ERROR: getaddrinfo: Name or service not known". This error message occurs regardless of what GUI rdc interface I use (e.g. grdesktop). I have had no trouble using the various Windows OS computers to connect with each other, only when going from my Ubuntu 8.10 to them. Any help will be appreciated.

Jeff.

---

### Post by Jeff_Illingworth on 2009-01-22
I have discovered that if I enter the remote computers IP address, I can connect. However, for whatever reason, using their network names (e.g. bobs_computer or A-0101987) still no longer works.

---

### Post by Jeff_Illingworth on 2009-02-02
bump

---

### Post by jfgauthier on 2010-01-19
Me too!

Just got the same issue here. Cannot log in with the computer name. I'm connecting my Ubuntu9.10 laptop to a Windows Embedded machine that has no screen with a crossover cable and the only available info i've got on that WINXPe is the computer name.

When i boot my same laptop under WINXP, i can remotely desktop without problems.

The problem lies under Ubuntu . I would like to see a solution to that problem also .

Best regards,
JF

---

### Post by gcbzzzz on 2010-05-24
this is your program's way of telling you that it can't find a ip for that name, even though a DNS entry does exist.

```

partearth$ dig hub.yahoo.com

; <<>> DiG 9.3.6-P1-RedHat-9.3.6-4.P1.el5 <<>> hub.yahoo.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50293
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;hub.yahoo.com.                 IN      A

;; AUTHORITY SECTION:
yahoo.com.              600     IN      SOA     ns1.yahoo.com. hostmaster.yahoo-inc.com. 2010052406 3600 300 1814400 600

;; Query time: 1 msec
;; SERVER: 66.228.178.11#53(66.228.178.11)
;; WHEN: Mon May 24 10:17:48 2010
;; MSG SIZE  rcvd: 92

```

see, there's an A record, but no IP.

partearth$ nc hub.yahoo.com 80
nc: getaddrinfo: Name or service not known

I'm clueless as to the internals here. but that's the cause :)

---

### Post by wnoisephx on 2011-05-17
Sorry for bumping a  year+ old thread, but i found this thread by  searching the error on Google.  I have a bit more of an possible answer  and I want to minimize the searching of others.

There are a couple of reasons for this error.   It is most likely caused  by avahi.   Avahi implements the zeroconf/Bonjour.  Avahi is installed  and turned on by default in most of the recent versions of ubuntu.    Avahi uses .local by default ([see http://linux.die.net/man/5/avahi-daemon.conf]("http://ubuntuforums.org/see%20http://linux.die.net/man/5/avahi-daemon.conf")  also [http://forum.pfsense.org/index.php?topic=23255.0]("http://http//forum.pfsense.org/index.php?topic=23255.0") ) It has also became a common practice to use .local for internal networks. 

The simplest test would be check if avahi is running and turn it off if it is, and then try and connect using the name.

ps ax | grep avahi
service avahi-daemon stop
rdesktop myserver.mydomain.local

if you can now connect you have a name conflict between your internal name, and avahi.
if you don't need it you can turn it off, however you loose some of the cool features (automatic service discovery)

If you want to use avahi, then things get a bit more tricky
you can change your internal DNS domain from mydomain.local to something  like mydomain.private.  However if you have even a moderate size  network, then the likely hood of things breaking is quite high.

Here is avahi's page with work arounds
[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

I changed the avahi.conf file to .alocal but that didn';t work so I  changed /etc/nsswitch.conf.   I located the hosts line and put dns in  front of the mdns stuff, like so
hosts:      files dns mdns4_minimal [NOTFOUND=return]

after that I could start avahi, and still do .local lookups

Hope this helps.

---

### Post by Inder on 2011-08-22
I am getting the same error message, so I tried your solution (stopping avahi), but doesn't work:

$ service avahi-daemon stop
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.88" (uid=1000 pid=4670 comm="stop avahi-daemon ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

---

### Post by Dejevic on 2011-10-11
Hi guys,

Sorry if this is already closed or anything, but I have similar problem.

When I am connected to network with cable, I can connect to my working desktop. When I connect to network with wireless, I get the 'ERROR: getaddrinfo: Name or service not known'. 

Then I connect back to network with cable and I can still access my desktop session. This is on my workplace, there are several hundred computers on it. Windows client doesn't have wireless connection problem. If anyone can help, that would be great.

Thanks

---

### Post by Puma1337 on 2011-10-13
> **Inder said:**
> I am getting the same error message, so I tried your solution (stopping avahi), but doesn't work:

$ service avahi-daemon stop
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.88" (uid=1000 pid=4670 comm="stop avahi-daemon ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

try:

$ sudo service avahi-daemon stop

---

### Post by douglasbrooksjr on 2011-11-09
So, I tried the suggested method of stopping avahi, but I still get the same error.  The exact output is:

Autoselected keyboard map en-us
ERROR: getaddrinfo: Name or service not known

---

### Post by d4m1r on 2011-11-14
Just seeing this today recently too...trying to connect to my XP machine @ work. My VPN connection to my works internal network connects fine but terminal server client presents this exact error when trying to connect. Have been using these same settings for 2-3 months and it has been working just fine up till now..

---

### Post by jossl on 2012-06-24
Hi,

It seems that I had the same problem: I was trying to connect with to a windows machine from wheezy with rdesktop 1.7.1:

   rdesktop -d my.domain.com MYMACHINE

and got the following error message:
   Autoselected keyboard map en-us
   ERROR: getaddrinfo: Name or service not known

But I could successfully connect either providing the IP address, or the fully qualified domain name (as explained in [http://superuser.com/questions/52109/why-does-remote-desktop-not-work-for-me-by-computer-name-and-only-by-ip](http://superuser.com/questions/52109/why-does-remote-desktop-not-work-for-me-by-computer-name-and-only-by-ip))

   rdesktop -d my.domain.com MYMACHINE.my.domain.com

Hope this helps also someone else!

---

