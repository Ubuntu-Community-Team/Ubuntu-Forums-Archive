---
title: "FF is slow resolving URLs, but IE running in a VM is not!?"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by Shadal on 2010-01-12
Hi all,

Fairly new to Linux, I have been using  Ubuntu on and off over the past few years, but never as my primary OS until a few weeks ago.

I searched, but cannot find anyone with this problem I'm experiencing...

When I first installed Ubuntu, internet in FireFox seemed quick.
Well sometime after the upgrade to 9.10, the time it takes FF to resolve URLs takes roughly 30+ seconds before connecting to the website. Until today I thought this was simply my poor wireless connection, but after installing Windows XP inside VirtualBox, and realizing that when browsing the net using IE, pages load instantly...
I believe this problem also applies to apt-get, as every time I try to install software using it OR Ubuntu's Add/Remove Applications, I receive a lot of 'Connection Timed Out', usually when apt-get tries accessing sourceforge...

Any Ideas?

I've checked and double checked all of my network settings, everything seems correct, no auto-proxy searching or anything going on that I can find.

---

### Post by adam814 on 2010-01-12
It's a bug in Karmic.  Firefox tries to resolve through IPv6 first and you probably need to disable IPv6 in Firefox.  I've seen quite a few forum threads about it.

---

### Post by Shadal on 2010-01-12
I did check that.. IPv6 is disabled in my wireless settings.
Thx tho ;)

---

### Post by adam814 on 2010-01-12
Did you do all these things? [http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html)

I guess I lucked out, I upgraded from Jaunty and never had this issue or troubles with sound servers.

If that doesn't fix it then it's sort of a generic slow DNS problem.  Although I can't imagine how XP in a VM is using different DNS servers than you are unless of course you configured it that way.

---

### Post by Shadal on 2010-01-12
Ohhh, Disable it In** FIREFOX**

Sorry, I overlooked that :D

The first suggestion in the link you provided (using about:config and toggling network.dns.disableIPv6) seems to have worked wonders!

Thanks Adam!! (a bit cold there in Gainsville? I'm just over the state line, these past few weeks have sucked!) :P

---

### Post by Shadal on 2010-01-12
Ahh - I went back and disabled IPv6 system-wide, as I was still getting the 'connection timeout's' when using apt-get, but this does not seem to have solved that problem.

Below is my term output when trying to '*sudo apt-get install ttf-mscorefonts-installer*'. You'll see I get a lot of 'Unable To Resolve Host' and 'Connection Timed Out' errors... 

ben@Quagmire:~$ sudo apt-get install ttf-mscorefonts-installer
[sudo] password for ben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ttf-mscorefonts-installe
ben@Quagmire:~$ sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-01-12 14:40:43--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-12 14:40:53--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `switch.dl.sourceforge.net'
--2010-01-12 14:41:03--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2010-01-12 14:41:13--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving dfn.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2010-01-12 14:41:23--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net) [following]
--2010-01-12 14:41:23--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-12 14:41:33--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2010-01-12 14:41:43--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net) [following]
--2010-01-12 14:41:44--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-12 14:41:54--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2010-01-12 14:42:04--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving internode.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2010-01-12 14:42:14--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving voxel.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2010-01-12 14:42:24--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2010-01-12 14:42:34--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internap.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
ben@Quagmire:~$

---

### Post by adam814 on 2010-01-12
Yeah, it's been a lot colder than Florida should be.

Are you able to resolve those addresses from the command line? (i.e. does "nslookup internap.dl.sourceforge.net" return a valid address or an error message?)

If it gives you an address are you able to wget the file manually? (they might have moved things around, although it's unlikely).

---

### Post by JBAlaska on 2010-01-12
@Shadal, You might try using openDNS or better still (for me anyway) use google's dns servers, they are blazing fast in my location.
8.8.8.8
8.8.4.4

---

### Post by Shadal on 2010-01-12
ok, tried nslookup on a few addresses, they all seemed to return their IPs pretty instant.

So now I've run 'wget [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)' and it DID successfully download... so now what do I do? :-D

---

### Post by adam814 on 2010-01-12
Ok, so your DNS is working and you're able to download these files manually...

Are you able to install other packages through apt-get?  Have you tried apt-get update recently?

---

### Post by Shadal on 2010-01-12
I have tried other packages, mscorefonts was just my example.
Most (although not all) packages fail to install when trying to apt-get recently.

Sometimes I am able to use ubuntu's Add/Remove Applications, it will error out at the end, but still have installed the pkg, like when I installed kdenlive and Amarok using add/remove, they both errored at the end, but both still installed successfully.

I ran apt-get update, tried again but still the same.

---

### Post by warfacegod on 2010-01-12
Make sure you have the recommended driver activated in: System> Admin.> Hardware Drivers. It sounds like your wireless signal strength might be part of the issue. You can also use your router's network summary to boost it's broadcast power. Try reading this link to improve Firefox performance.

[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by sxmaxchine on 2010-01-12
my simple solution that wil speed up ur internet and give u a better look is to download and install opera

---

