---
title: "UBUDSL works in ubuntu 9.10"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by ham4ever on 2009-11-11
hey all,
after i had problem with make my sagem fast 800 works in ubuntu 9.10 , 
we all know that UBUDSL won't work in  ubuntu 9.10
so this is how i made it work, ( i am not professional in lunix , i just found solution today and i wanted to share it )
[CENTER] 


FIRST download UBUDSL that work for ubuntu 9.04 from [here ]("http://www.ubudsl.com/en/download.php")
 INSTALL UBUDSL  " double click " 
now let's make UBUDSL works in ubuntu 9.10
OPEN terminal and do this command
> gksu gedit /usr/share/ubudsl/configs/system.iniand add this in first
> 
[Ubuntu_9.10] 
package_manager=apt 
basic_from_cd= 
devel_from_cd=build-essentialSAVE and exit

now configure UBUDSL like normal  from :
System  => Administration =>UbuDsl -connection configuration 

do your  username and password and all needed
 for now everything works good

let's change some stuff in ubudsl configuration and Daemon

OPEn Terminal and do this command 
> gksu gedit /usr/share/ubudsl/logs/UbuDSL_Configuration.logand past this in last 
> 23-10-2009 18:27:41 UbuDSL_Configuration::debugHandler: UbuDSL Configurator run: "23-10-2009 18:27:41." 
23-10-2009 18:27:48 UbuDSL_Configuration::debugHandler: Unsupported system: "Ubuntu 9.10" save and exit

OPEN terminal again and do this command :

> gksu gedit /usr/share/ubudsl/logs/UbuDSL_Daemon.logand delete all what is inside and past this :


> [23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): ctor invoked.
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): PKG_INFO: 1.0.0.300-7jaunty
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: DNS = 
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: VCI = 35
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: VPI = 0
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: connect_at_boot = true
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: connect_at_modem_plug = true
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: idleness = 1
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: modem = Sagem F@st 800
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: product_id = 36897
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: protocol = PPPoA
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: service = Neostrada TP
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: udi = /org/freedesktop/Hal/devices/usb_device_1110_9021_00604C732DE5
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: vendor_id = 4368
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): daemon.ini: version = 100277
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): ubudsl.conf exists.
[23-10-2009 18:44:55] UbudslDaemon::UbudslDaemon(): successfully connected to DBus.
[23-10-2009 18:44:55] UbuDSL_Daemon::initModemsMap(): called.
[23-10-2009 18:44:55] UbuDSL_Daemon::initModemsMap(): finished.
[23-10-2009 18:44:55] ConnectThread::ConnectThread(): called.
[23-10-2009 18:44:55] ConnectThread::ConnectThread(): finished.
[23-10-2009 18:44:55] DisconnectThread::DisconnectThread(): called.
[23-10-2009 18:44:55] DisconnectThread::DisconnectThread(): finished.
[23-10-2009 18:44:55] initDaemon 
[23-10-2009 18:44:55] UbuDSL_Daemon::getIsModemPlugged(): called.
[23-10-2009 18:44:55] UbuDSL_Daemon::getIsModemPlugged(): modem is plugged.
[23-10-2009 18:44:55] UbuDSL_Daemon::getIsModemPlugged(): finished.
[23-10-2009 18:44:55] CompilerThread::testDriver(): called.
[23-10-2009 18:44:55] CompilerThread::testDriver(): finished.
[23-10-2009 18:44:55] UbuDSL_Daemon::init(): modem is plugged in, connect at boot.
[23-10-2009 18:44:55] UbuDSL_Daemon::establishConnection(): called.
[23-10-2009 18:44:55] UbuDSL_Daemon::getModemState(): called.
[23-10-2009 18:44:55] UbuDSL_Daemon::getModemState(): modem is synchronised.
[23-10-2009 18:44:57] UbuDSL_Daemon::establishConnection(): finished.
[23-10-2009 18:44:57] UbuDSL_Daemon::getModemState(): called.
[23-10-2009 18:44:57] ConnectThread::run(): called.
[23-10-2009 18:44:57] UbuDSL_Daemon::getModemState(): called.
[23-10-2009 18:44:57] UbuDSL_Daemon::getModemState(): modem is synchronised.
[23-10-2009 18:44:57] ConnectThread::waitForSynchronisation(): modem synchronised.
[23-10-2009 18:44:57] UbuDSL_Daemon::getModemState(): idx < 0!
[23-10-2009 18:44:57] cmd: "pppd debug linkname ubudsl lock noipdefault defaultroute hide-password lcp-echo-interval 20 lcp-echo-failure 3 connect /bin/true noauth persist mtu 1492 noaccomp holdoff 4 default-asyncmap plugin pppoatm.so 0.35 user "d9qxqpP@neostrada.pl"" 
[23-10-2009 18:44:57] UbuDSL_Daemon::debugConnecting(): process message: Plugin pppoatm.so loaded.
[23-10-2009 18:44:57] UbuDSL_Daemon::debugConnecting(): process message: PPPoATM plugin_init
[23-10-2009 18:44:57] UbuDSL_Daemon::debugConnecting(): process message: PPPoATM setdevname_pppoatm - SUCCESS:0.35
[23-10-2009 18:44:57] UbuDSL_Daemon::debugConnecting(): process message: using channel 1
[23-10-2009 18:44:57] UbuDSL_Daemon::debugConnecting(): process message: Using interface ppp0
[23-10-2009 18:44:57] UbuDSL_Daemon::debugConnecting(): process message: Connect: ppp0 <--> 0.35
[23-10-2009 18:44:57] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x1 <magic 0xfb1553eb>]
[23-10-2009 18:45:00] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x1 <magic 0xfb1553eb>]
[23-10-2009 18:45:03] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x1 <magic 0xfb1553eb>]
[23-10-2009 18:45:06] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x1 <magic 0xfb1553eb>]
[23-10-2009 18:45:09] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x1 <magic 0xfb1553eb>]
[23-10-2009 18:45:12] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x1 <magic 0xfb1553eb>]
[23-10-2009 18:45:15] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x1 <magic 0xfb1553eb>]
[23-10-2009 18:45:18] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x1 <magic 0xfb1553eb>]
[23-10-2009 18:45:21] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x1 <magic 0xfb1553eb>]
[23-10-2009 18:45:24] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x1 <magic 0xfb1553eb>]
[23-10-2009 18:45:27] UbuDSL_Daemon::debugConnecting(): process message: LCP: timeout sending Config-Requests
[23-10-2009 18:45:27] UbuDSL_Daemon::debugConnecting(): process message: Connection terminated.
[23-10-2009 18:45:27] UbuDSL_Daemon::debugConnecting(): process message: Modem hangup
[23-10-2009 18:45:27] UbuDSL_Daemon::debugConnecting(): modem hangup (1)
[23-10-2009 18:45:30] UbuDSL_Daemon::getIsModemPlugged(): called.
[23-10-2009 18:45:30] UbuDSL_Daemon::getIsModemPlugged(): modem is plugged.
[23-10-2009 18:45:30] UbuDSL_Daemon::getIsModemPlugged(): finished.
[23-10-2009 18:45:31] UbuDSL_Daemon::debugConnecting(): process message: using channel 2
[23-10-2009 18:45:31] UbuDSL_Daemon::debugConnecting(): process message: Using interface ppp0
[23-10-2009 18:45:31] UbuDSL_Daemon::debugConnecting(): process message: Connect: ppp0 <--> 0.35
[23-10-2009 18:45:31] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x2 <magic 0x8013f937>]
[23-10-2009 18:45:32] UbuDSL_Daemon::getIsModemPlugged(): called.
[23-10-2009 18:45:32] UbuDSL_Daemon::getIsModemPlugged(): modem is plugged.
[23-10-2009 18:45:33] UbuDSL_Daemon::getIsModemPlugged(): finished.
[23-10-2009 18:45:34] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x2 <magic 0x8013f937>]
[23-10-2009 18:45:37] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x2 <magic 0x8013f937>]
[23-10-2009 18:45:40] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x2 <magic 0x8013f937>]
[23-10-2009 18:45:43] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x2 <magic 0x8013f937>]
[23-10-2009 18:45:46] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x2 <magic 0x8013f937>]
[23-10-2009 18:45:49] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x2 <magic 0x8013f937>]
[23-10-2009 18:45:52] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x2 <magic 0x8013f937>]
[23-10-2009 18:45:55] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x2 <magic 0x8013f937>]
[23-10-2009 18:45:58] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x2 <magic 0x8013f937>]
[23-10-2009 18:46:01] UbuDSL_Daemon::debugConnecting(): process message: LCP: timeout sending Config-Requests
[23-10-2009 18:46:01] UbuDSL_Daemon::debugConnecting(): process message: Connection terminated.
[23-10-2009 18:46:01] UbuDSL_Daemon::debugConnecting(): process message: Modem hangup
[23-10-2009 18:46:01] UbuDSL_Daemon::debugConnecting(): modem hangup (2)
[23-10-2009 18:46:05] UbuDSL_Daemon::debugConnecting(): process message: using channel 3
[23-10-2009 18:46:05] UbuDSL_Daemon::debugConnecting(): process message: Using interface ppp0
[23-10-2009 18:46:05] UbuDSL_Daemon::debugConnecting(): process message: Connect: ppp0 <--> 0.35
[23-10-2009 18:46:05] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x3 <magic 0xe27cde9c>]
[23-10-2009 18:46:08] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x3 <magic 0xe27cde9c>]
[23-10-2009 18:46:11] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x3 <magic 0xe27cde9c>]
[23-10-2009 18:46:14] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x3 <magic 0xe27cde9c>]
[23-10-2009 18:46:17] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x3 <magic 0xe27cde9c>]
[23-10-2009 18:46:20] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x3 <magic 0xe27cde9c>]
[23-10-2009 18:46:23] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x3 <magic 0xe27cde9c>]
[23-10-2009 18:46:26] UbuDSL_Daemon::debugConnecting(): process message: sent [LCP ConfReq id=0x3 <magic 0xe27cde9c>]
[23-10-2009 18:46:27] ConnectThread::run(): pppd->waitForFinished() returned false, killing the process...
[23-10-2009 18:46:27] QProcess: Destroyed while process is still running.
[23-10-2009 18:46:27] ConnectThread::run(): finished.save and exit 


now run UbuDSl Applet from :
Applications => Internet => UbuDsl Applet 
and connect 
your connection should work fine like mine :)

=====================================
in that file i did  u see smiley  and is annoying
coz original is " :: Disconnect"

without  space between  "::"   and   "Disconnect"

==============================

sorry about my  English ;)
and i am not expert in Lunix :P
[/CENTER]

---

### Post by Ahadiel on 2009-11-11
You probably don't **need** to modify the log.

---

### Post by ham4ever on 2009-11-11
i just did like that  and UbuDSL works fine for me

---

### Post by logari81 on 2009-12-16
For Ubuntu 9.10 you can use the ubudsl package from my ppa
[https://launchpad.net/~logari81/+archive/ppa/](https://launchpad.net/~logari81/+archive/ppa/)

ham4ever: Perhaps you can add this information to your initial post, since this method will be easier for new users

---

### Post by Shooree on 2009-12-17
Has the entire ubudsl site been taken offline? It certainly appears to have been.

Thanks for the ppa, mate. Only thing is, I'm on an XP box right now, with my Ubuntu Karmic running lappie unable to connect to the internet, which equals being uable to get to your ppa. How do I go around this? I hoped I that I'll be able to download a tarball or something and put it on the lappie via a flash drive, set ipt up and give it a go.

Any help as to how I should proceed with this is most welcome.

EDIT: It would be great if someone could tell me whether the version on sourceforge is worth downloading ([http://sourceforge.net/projects/ubudsl/files](http://sourceforge.net/projects/ubudsl/files))
There's an even older one on Softpedia...

---

### Post by logari81 on 2009-12-21
You can download the deb package corresponding to your architecture from the ppa:
[https://launchpad.net/~logari81/+archive/ppa/+files/ubudsl_1.0.0.300-7karmic_i386.deb](https://launchpad.net/~logari81/+archive/ppa/+files/ubudsl_1.0.0.300-7karmic_i386.deb)
[https://launchpad.net/~logari81/+archive/ppa/+files/ubudsl_1.0.0.300-7karmic_amd64.deb](https://launchpad.net/~logari81/+archive/ppa/+files/ubudsl_1.0.0.300-7karmic_amd64.deb)

---

### Post by Shooree on 2009-12-21
Thanks for the link logari81. Unfortunately, I'm still not able to connect my laptop to the Sagem Fast 800 modem in question, even with your .deb. It reports failing to sync, although at one point it reported a wrong username/pw instead. When I inputted the correct username, it went on to reporting "modem hang up", whatever that may mean. I'm including the logs, if anyone cares to have a looksee.

I'm just thoroughly disappointed with karmic. A friend still clings on to 8.10 Xubuntu for dear life. He got UbuDSL working on it and wouldn't change it for anything. Sadly, I understand him completely now. No internet on an Ubuntu system = being laughed at by Win lusers who just p'n'p.

---

### Post by logari81 on 2009-12-22
I am not a ubudsl-expert but your logs seem quite harmless. Are you sure there is no DNS issue or similar? try to ping a well known address e.g.:
```
ping 209.85.229.99
```

anyway I wouldn't classify your problem as karmic-specific.

---

### Post by joannesfdo on 2010-01-17
Hay [logari81]("http://georgia.ubuntuforums.org/member.php?u=264832") i already try to install ubudsl in ubuntu 9.10 and im able to install it but ZTE 852 modem is not synchronizing can u help me on this pls :)

---

### Post by logari81 on 2010-01-20
could you give us the results from:
```
lsusb
dmesg
```
?

---

### Post by joannesfdo on 2010-02-13
Bro i need the ubudsl with unicorn versions 2 driver

---

### Post by logari81 on 2010-02-14
could you give a link of this unicorn driver version?

---

### Post by joannesfdo on 2010-02-15
[http://ubuntuforums.org/showthread.php?t=1303485&page=2](http://ubuntuforums.org/showthread.php?t=1303485&page=2)

check this ASAP.

---

### Post by logari81 on 2010-02-22
this patch has already been included but not published in the karmic repo of my ppa. See my post in the other thread.

---

### Post by joannesfdo on 2010-02-22
[COLOR=Blue]Thanks bro ill check this today.......[/COLOR]

---

### Post by joannesfdo on 2010-02-25
Bro i try to install it on ubuntu 9.10 but its not working

---

### Post by MichaelSM on 2010-02-27
Hello. I've tried a few things including recently that workaround with the logfile. No good.

OK. I.m running Linux Mint 8 on a laptop. 

First off, I did the ppa thing and installed ubudsl from Synaptic. Looked good.

But THEN, and every time SINCE; whenever I go to System>Administration>Ubudsl Connection Configuration and enter my password when requested, I get a little box which says;

'Your system (8) is currently unsupported. Application will now quit.'

And that's it. 

Frustrating, because I assume I've missed something important. And yes I registered the key.

Any help greatly appreciated.

Mike.

PS modem is Speedtouch Stingray and its lights are on.

PPS that smiley is an 8 in brackets. I forgot to disable smileys ...

---

### Post by logari81 on 2010-03-01
> **MichaelSM said:**
> .
Frustrating, because I assume I've missed something important...

no you don't, the package simply doesn't support mint, if you give me the result from
```
cat /etc/lsb-release
```

I can add it in the next package version. Otherwise you can apply the method of the first post in this thread.

---

### Post by MichaelSM on 2010-03-01
Here you go:

DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=8
RELEASE_NOTES_URL=http://www.linuxmint.com/rel_helena.php
DISTRIB_CODENAME=helena
DISTRIB_DESCRIPTION="Linux Mint 8 Helena - Main Edition"

As I said, I followed the first post, but could not get into ubudsl connection configuration. 

Looking forward to your assistance. Thank you.

Mike.

---

### Post by logari81 on 2010-03-09
The package from here
[https://launchpad.net/~ubudsl-maintainers/+archive/ubudsl](https://launchpad.net/~ubudsl-maintainers/+archive/ubudsl)
should support LinuxMint as well. Try it and give me some feedback please.

---

### Post by MichaelSM on 2010-03-09
Logari81

Still same error 

'System (8) not supported...' etc.

Perhaps there are previous versions and entries which I need to remove?

I have run sudo apt-get remove ubudsl* 

re-booted, then installed your latest from synaptic.

Which is ubudsl 1.0.0.301-2karmic0

I'm completely aware that I may have made some mistakes.

Cheers,

Mike.

---

### Post by MichaelSM on 2010-03-14
In the end, I re-installed usbadslmodemmanager 0.5.8 and fiddled with stuff until it worked. There were two sets of four speedtch.bin entries in /lib/firmware so I deleted the second lot.

MANY reboots later and after having to sign in as root the thing lit up properly and I'm using it now as I write.
I have only two hints which are entirely nonsensical:

1) Only seems to work properly when laptop is running on external power supply.
2) Only fires up properly after total shutdown and restart.

Compaq CQ61-210tu Celeron 1.9 CoreDuo 2g RAM dual boot Win Vista Home Premium/Linux Mint 8.

Cheers,

Mike.

---

### Post by MichaelSM on 2010-07-17
To Logari81

Sorry to be a pest....

I have been playing with PCLinuxOS 2010 and installed ubudsl-1.0.0.277-6.1.i586.rpm
with 'system not supported' the result, which is fair enough.
Any chance of a script which will allow it to run?
PCLinuxOS is weird because it purports to support Speedtouch modems, but it is almost impossible to make them work!

Cheers,
Michael.

---

