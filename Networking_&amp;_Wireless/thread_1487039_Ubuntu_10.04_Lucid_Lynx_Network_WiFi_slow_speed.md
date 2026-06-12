---
title: "Ubuntu 10.04 Lucid Lynx Network WiFi slow speed"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by JohnDoe365 on 2010-05-18
A lot of people  have the problem to find themselves with Lucid Lynx 10.04 and experience  massive issues when connecting to wireless - me too.

As a service, here some relevant links which promise relief:

Disable IPv6
[http://www.webupd8.org/2010/05/how-t...untu-1004.html]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html")
Disable IPv6 in firefox
[http://ubuntuforums.org/showthread.p...t=disable+ipv6]("http://ubuntuforums.org/showthread.php?t=1472356&highlight=disable+ipv6")
manually disable auto bandwith mediation of WiFi
[B]sudo iwconfig wlan0 rate 54M
(replace wlan0 with your actual WiFi device)
[/B]Disable 802.11n on your router

I tried all of them, and none reliably worked. Every solution which  required re-association wtih the AP helped for some time, but nothing  helped for long.
First, don't let yourself fool by the disable IPv6 trap - while it is  "enabled" it is acutally not used by Lucid!

I have a clean install of Kubuntu 10.04 on an AMD64 Laptop with Broadcom  STA driver:
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n  (rev 03)

However I can reliably stabilize my connection for some time either by  manually disabling WiFi with the hardware switch or disabling WiFi by  software means and re-activating. This brings speed at par with Kubuntu  9.10 until some time.

Can anybody confirm this behaviour?

I already filed a bug @ launchpad: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936)

---

### Post by erictm on 2010-05-18
I have the same issue on my Macbook 3,1. I already have slow internet at my location and when I attempt to load a webpage it literally takes 15 minutes or more. I switched back to OSX to confirm that the internet was simply being slow, but I'm able to load webpages far more quickly.

---

### Post by ashwinhgtx on 2010-05-20
Same problem here. :(

---

### Post by lgalicki on 2010-05-21
Hey guys!

I'm also experiencing the same problem, but I'm still using 9.10. My internet connection is 10 Mb/s, and the max speed I've got during the bursts of speed I experience when I restart the wireless connection was around 4 Mb/s. Then things start to go downhill until the bottom is hit and it goes as fast as 0.5 Mb/s. :-(

If anyone find out the fix, do not forget to post it here for us!

PS.: Wired connection is ok and my PS3 downloads at max speed using wireless connection.

Regards!

---

### Post by LeChuck on 2010-05-28
Exactly the same behaviour here. Have been away for some days without problems, but for some mysterious reasons I recognize wlan slowed down in lucid.

I remember having a similar problem when upgrading to karmic, but could solve it by using the opendns server. But as they're still in use it must be something else.

---

### Post by nDrewPJ on 2010-05-31
I've openned a ticket both in Launchpad for Ubuntu 10.04 and in the bugtracker for Archlinux because it seems that this is a kernel(wifi driver) issues.

I have also opnned a bug ticket. Going to merge it with JohnDoe365's

([https://bugs.launchpad.net/ubuntu/+bug/587454](https://bugs.launchpad.net/ubuntu/+bug/587454))

---

### Post by jamaisvu on 2010-06-01
I believe this is related to [this bug](https://bugs.launchpad.net/ubuntu/+bug/572777). The wading-through-treacle behavior only seems to happen with WPA -- it's fine with WEP in my experience. The solution in the 35th reply to that bug -- viz replacing wpasupplicant and two libs with the versions from Debian Sid -- should do the trick.

---

### Post by cincinnatus13 on 2010-06-01
@jamaisvu
I tried that and it didn't seem to work. I am running a Realtek card but that didn't help at all after rebooting. I can't even get to the point of installing wicd, which seemed to help somewhat on my other comp (Tosh Satellite with XP and a Realtek card as well.)

---

### Post by madnux on 2010-06-03
Same here on a PC in my office.

---

### Post by moodle on 2010-06-04
> **jamaisvu said:**
> I believe this is related to [this bug]("https://bugs.launchpad.net/ubuntu/+bug/572777"). The wading-through-treacle behavior only seems to happen with WPA -- it's fine with WEP in my experience. The solution in the 35th reply to that bug -- viz replacing wpasupplicant and two libs with the versions from Debian Sid -- should do the trick.

This didn't work for me.  My wireless is still painfully slow loading most webpages.

---

### Post by epolin on 2010-06-08
I have the same issue with two old AMD Turion TL-50 machines (either w/ a 32 or 64 bits Ubuntu), but not at all with my Intel i7-950. I am using Wep.

Clearly, it is not related to Firefox, as it also happens w/ Epiphany, Synaptic, etc.. So, it has to do w/ the networking layers. More specifically, it seems to be linked to the Wi-Fi, as the network works fine when wired.

The behaviour while reloading the directories in Synaptic shows that the downloads are intrinsically fast but are interrupted by very long breaks. Maybe it is related to the negotiation of the speed with the Wi-Fi router and subsequent communication failures with the old Wi-Fi cards. Could not get any convincing impact by using wondershaper, though...

---

### Post by teilnehmer on 2010-06-10
I didn't run into the problem the last 2 days. 

Updated Packages (according to Synaptic History): 
```

brasero (2.30.0-0ubuntu1) to 2.30.1-0ubuntu2
brasero-common (2.30.0-0ubuntu1) to 2.30.1-0ubuntu2
gnome-keyring (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
gnome-panel (1:2.30.0-0ubuntu1) to 1:2.30.0-0ubuntu2
gnome-panel-data (1:2.30.0-0ubuntu1) to 1:2.30.0-0ubuntu2
libbrasero-media0 (2.30.0-0ubuntu1) to 2.30.1-0ubuntu2
libcairomm-1.0-1 (1.8.0-1build2) to 1.8.4-0ubuntu1
libgcr0 (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
libgp11-0 (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
libmysqlclient16 (5.1.41-3ubuntu12.1) to 5.1.41-3ubuntu12.3
libpam-gnome-keyring (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
libpanel-applet2-0 (1:2.30.0-0ubuntu1) to 1:2.30.0-0ubuntu2
mysql-client-core-5.1 (5.1.41-3ubuntu12.1) to 5.1.41-3ubuntu12.3
mysql-common (5.1.41-3ubuntu12.1) to 5.1.41-3ubuntu12.3
mysql-server-core-5.1 (5.1.41-3ubuntu12.1) to 5.1.41-3ubuntu12.3
openoffice.org-base-core (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-calc (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-common (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-core (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-draw (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-emailmerge (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-gnome (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-gtk (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-impress (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-math (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-style-human (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-writer (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
python-papyon (0.4.6-0ubuntu2) to 0.4.8-0ubuntu1
python-uno (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
rhythmbox (0.12.8-0ubuntu5) to 0.12.8-0ubuntu6
rhythmbox-plugin-cdrecorder (0.12.8-0ubuntu5) to 0.12.8-0ubuntu6
rhythmbox-plugins (0.12.8-0ubuntu5) to 0.12.8-0ubuntu6
telepathy-butterfly (0.5.8-1ubuntu1) to 0.5.9-0ubuntu1
ttf-opensymbol (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
tzdata (2010i-1) to 2010j-0ubuntu0.10.04
tzdata-java (2010i-1) to 2010j-0ubuntu0.10.04
uno-libs3 (1.6.0+OOo3.2.0-7ubuntu4) to 1.6.0+OOo3.2.0-7ubuntu4.1
ure (1.6.0+OOo3.2.0-7ubuntu4) to 1.6.0+OOo3.2.0-7ubuntu4.1

```

Also, the linux headers have of course been updated some days before that (6/6/10). Maybe I didn't realise it was better then...

Could any of these packages be related? Is anyone else experiencing better wi-fi connectivity?

**UPDATE**
The good behavior continued until 2 days ago... For those of you who know more of this stuff, these are the updated packages (two updates within one hour, I think I updated the package list after the first). Again, maybe a package is related to the bug. Maybe someone can confirm the changed behaviour. I have linux-backports-modules-wireless-lucid-generic installed, as proposed in the [bug report]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936").

```

cups (1.4.3-1ubuntu1) to 1.4.3-1ubuntu1.2
cups-bsd (1.4.3-1ubuntu1) to 1.4.3-1ubuntu1.2
cups-client (1.4.3-1ubuntu1) to 1.4.3-1ubuntu1.2
cups-common (1.4.3-1ubuntu1) to 1.4.3-1ubuntu1.2
evolution (2.28.3-0ubuntu9) to 2.28.3-0ubuntu10
evolution-common (2.28.3-0ubuntu9) to 2.28.3-0ubuntu10
evolution-data-server (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
evolution-data-server-common (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
evolution-plugins (2.28.3-0ubuntu9) to 2.28.3-0ubuntu10
fglrx-modaliases (2:8.723.1-0ubuntu3) to 2:8.723.1-0ubuntu4
gstreamer0.10-plugins-good (0.10.21-1ubuntu2) to 0.10.21-1ubuntu3
gstreamer0.10-plugins-ugly-multiverse (0.10.14-0ubuntu1) to 0.10.14-0ubuntu2
gstreamer0.10-pulseaudio (0.10.21-1ubuntu2) to 0.10.21-1ubuntu3
kdepimlibs-data (4:4.4.2-0ubuntu2) to 4:4.4.2-0ubuntu2.1
kdepimlibs5 (4:4.4.2-0ubuntu2) to 4:4.4.2-0ubuntu2.1
kpackagekit (0.5.4-0ubuntu4) to 0.5.4-0ubuntu4.1
libcamel1.2-14 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libcups2 (1.4.3-1ubuntu1) to 1.4.3-1ubuntu1.2
libcupscgi1 (1.4.3-1ubuntu1) to 1.4.3-1ubuntu1.2
libcupsdriver1 (1.4.3-1ubuntu1) to 1.4.3-1ubuntu1.2
libcupsimage2 (1.4.3-1ubuntu1) to 1.4.3-1ubuntu1.2
libcupsmime1 (1.4.3-1ubuntu1) to 1.4.3-1ubuntu1.2
libcupsppdc1 (1.4.3-1ubuntu1) to 1.4.3-1ubuntu1.2
libebackend1.2-0 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libebook1.2-9 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libecal1.2-7 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedata-book1.2-2 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedata-cal1.2-6 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedataserver1.2-11 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libedataserverui1.2-8 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libegroupwise1.2-13 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libexchange-storage1.2-3 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libgdata-google1.2-1 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libgdata1.2-1 (2.28.3.1-0ubuntu2) to 2.28.3.1-0ubuntu3
libgnomekbd-common (2.30.0-0ubuntu2) to 2.30.1-0ubuntu1
libgnomekbd4 (2.30.0-0ubuntu2) to 2.30.1-0ubuntu1
libgssapi-krb5-2 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libido-0.1-0 (0.1.5-0ubuntu1) to 0.1.6-0ubuntu1
libk5crypto3 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libkrb5-3 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libkrb5support0 (1.8.1+dfsg-2) to 1.8.1+dfsg-2ubuntu0.1
libpoppler-glib4 (0.12.4-0ubuntu4) to 0.12.4-0ubuntu5
libpoppler5 (0.12.4-0ubuntu4) to 0.12.4-0ubuntu5
libsdl1.2debian (1.2.14-4ubuntu1) to 1.2.14-4ubuntu1.1
libsdl1.2debian-pulseaudio (1.2.14-4ubuntu1) to 1.2.14-4ubuntu1.1
libtiff4 (3.9.2-2) to 3.9.2-2ubuntu0.3
nvidia-current (195.36.15-0ubuntu3) to 195.36.24-0ubuntu1~10.04
nvidia-current-modaliases (195.36.15-0ubuntu3) to 195.36.24-0ubuntu1~10.04
poppler-utils (0.12.4-0ubuntu4) to 0.12.4-0ubuntu5
software-center (2.0.4) to 2.0.5
spideroak (9658) to 9667
telepathy-butterfly (0.5.9-0ubuntu1) to 0.5.11-0ubuntu1
udisks (1.0.1-1build1) to 1.0.1-1ubuntu1
xserver-common (2:1.7.6-2ubuntu7) to 2:1.7.6-2ubuntu7.1
xserver-xorg-core (2:1.7.6-2ubuntu7) to 2:1.7.6-2ubuntu7.1

```
```

evolution-data-server (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
evolution-data-server-common (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libcamel1.2-14 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libebackend1.2-0 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libebook1.2-9 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libecal1.2-7 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libedata-book1.2-2 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libedata-cal1.2-6 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libedataserver1.2-11 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libedataserverui1.2-8 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libegroupwise1.2-13 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libexchange-storage1.2-3 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libgdata-google1.2-1 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4
libgdata1.2-1 (2.28.3.1-0ubuntu3) to 2.28.3.1-0ubuntu4

```

---

### Post by fantastic_id on 2010-07-05
I didn't realized the wireless problem until a brainwave yesterday night. Here is what I have experienced:

Platform: Ubuntu 1004 on MBP 6,1
1. Install bcm-kernal-source
2. Enable sound
3. Connect to my office's vpn server
4. Join the conference call either with twinkle/ekiga

Problem:

My microphone works fine and my collegues are able to hear me quite well, however the voice from the meeting I heard is extremely intermittent. I have been thinking there's a problem with pulseaudio or alsa since I didn't have this problem in my PC running Ubuntu 1004. I tried a lot for sound device tuning but gave up after 1 week tries ;(

Yesterday I suddenly thought it is possbile that the wireless brings loss of voice frames... So I attempted a direct cable connection as my last hope. And the voice then sounds working very well with cable connection.

So, yes, probably we are in the same situation.

---

### Post by doctornikesh on 2010-07-26
TRY THESE TWO  ( as fixing these two files worked for me like charm)
**1. The Debian Avahi (nss-mdns) Bug**
There is a known bug doing the rounds in Debian based distros, this includes  Ubuntu.
The problem is in the nsswitch.conf file where wins mdns causes a slowdown of DNS resolution on some machines.
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940)
A simple workaround for this problem is to remove mdns4_minimal entry from the nsswitch.conf file, or change mdns4_minimal to just mdns4 (whichever works best for you):
Edit this file- /etc/nsswitch.conf
Scroll down to the entry which says:
hosts: files dns wins mdns4_minimal
and delete the mdns4_minimal entry. (I removed wins as well), s it looks like this:
hosts: files dns
**2. Check your DNS in resolv.conf**
You should only have two entries (usually) which are your Internet Service Provider&#8217;s DNS servers.
Check and/or edit your dns servers:
gksudo scite /etc/resolv.conf
It should look something like this:
search my.isp.com
nameserver 4.4.2.2
nameserver 4.4.2.4
You may have an extra IP address there, possibly your router (192.168.1.1), and if you haven&#8217;t got dns servers configured in your router config, this may cause a problem/slowdown as well. EG:
search my.isp.com
nameserver 192.168.1.1
nameserver 4.4.2.2
nameserver 4.4.2.4
Just remove the first one and leave the two ISP DNS server IP&#8217;s.

---

### Post by mrpaulo99 on 2010-08-06
I had experimented very slow speed when I watch some youtube videos and accessing to hotmail. They were fixed changing the MTU of the network interface, in may case wlan0. Something like that:

sudo ifconfig wlan0 mtu 1480

It did work for me.

---

### Post by joseph_e2 on 2010-08-12
> **doctornikesh said:**
> TRY THESE TWO  ( as fixing these two files worked for me like charm)
**1. The Debian Avahi (nss-mdns) Bug**
...
**2. Check your DNS in resolv.conf**
...

I was having a similar problem, with web sites taking forever to load. This quick change and a Firefox restart later, and I'm back up to speed. Hopefully it will stay this way! Thanks!

Question, though: what should I get when running```
 gksudo scite /etc/resolv.conf
```

On my machine, it did nothing. I was able to open resolv.conf in gedit and make the change. Sure enough, my router's IP address was listed.

---

### Post by ipk on 2010-08-20
> **doctornikesh said:**
> 
**1. The Debian Avahi (nss-mdns) Bug**

That did it for me, too. 1000 thanks. I spent the better of the night trying to get a stable wlan, with connection speed first soso allright and deteriorating until unusable, until i would re-start it again.

This is with a TP-link USB stick.

Thanks and Cheers

Ingo

---

### Post by ntropia on 2010-09-16
Hi guys,

same problem here (10.04, EeePc 1001HA Atheros Wifi AR9285), but without success.
I've tried the approach suggested by doctornikesh, as well as all the possible combinations to disable the IPv6:
 - modify GRUB2 default options,
 - blacklist the module [useless since new kernels, right?]
 - change the sysctl.conf settings
 - disable IPv6 in all browsers

The behavior is quite weird to me, since I can see some packets being sent and received, but then the connection hangs (i.e. apt-get update downloads the first 3-5% chuncks of any repo list, then endless wait until a timeout, then another chunk...).

Also, pretty upsetting that my sister's laptop with 9.04 works very well. I've configured both myself, and I've double-checked that config files are identical... 


My laptop works well at work, but when I'm connected to my home router it goes bananas...


I'm unable to find other solutions even after intense googling and forum searches, so I'm lost.
Although, I don't want to have to downgrade to the 9.04, so any hints will be more than welcome.


Thank you,

N

---

### Post by ntropia on 2010-09-16
Update: I've made couple of tests, and these are the findings:

-no errors reported on dmesg
-MTU windows are identical on 9.04 and 10.04
-hangs occur every ~4K received
-IPv6 is disabled on boot (as from dmesg).
-identical problems with cabled ethernet to the router 


I've had a look at the complete bug-report list on launchpad, but none of them seems to suite my case...

Again, hints are welcome.


N

---

### Post by ntropia on 2010-09-18
I've found who was the culprit of the incredibly slow connection speed. 

In the sysctl.conf I've disabled TCP the window scaling uncommenting the first line and adding the other two:

```
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_window_scaling = 0
net.ipv4.tcp_ecn = 0
```

and I'm getting the same good performances with both Lucid 10.04 and Jaunty 9.04. But why this discrepancy in first place? The defaults changed from the old 9.04 to the 10.04, so by default (I assume) the window scaling is on.
Apparently this is a major issue with some modems like the Pirelli W Gate shipped with the Alice internet connection found in some european countries.

I can't judge the usefulness of this parameter, but from my experience I can tell that adding window scaling is a limitation more than an advantage, since without it you could browse without problems everywere.


I hope it can help someone with similar problems...


eNjoy

[EDIT] The problem could be more likely related to the ECN (Explicit Congestion Notification), an option to deal with congestioned networks. It seems many firewalls (and routers) are shamelessly unable to deal with them despite it's in the TCP standard.

---

### Post by fmelo on 2010-10-01
Thanks ntropia! It did work to me. I indeed have a Alice router which was very slow. Is there any security issue I should worry about with these changes?
Thanks.

---

### Post by rafaelenr on 2010-10-17
This worked for me:

[http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html](http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html)

---

### Post by efd on 2011-04-23
> **doctornikesh said:**
> TRY THESE TWO  ( as fixing these two files worked for me like charm)
**1. The Debian Avahi (nss-mdns) Bug**
There is a known bug doing the rounds in Debian based distros, this includes  Ubuntu.
The problem is in the nsswitch.conf file where wins mdns causes a slowdown of DNS resolution on some machines.
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940)
A simple workaround for this problem is to remove mdns4_minimal entry from the nsswitch.conf file, or change mdns4_minimal to just mdns4 (whichever works best for you):
Edit this file- /etc/nsswitch.conf
Scroll down to the entry which says:
hosts: files dns wins mdns4_minimal
and delete the mdns4_minimal entry. (I removed wins as well), s it looks like this:
hosts: files dns
**2. Check your DNS in resolv.conf**
You should only have two entries (usually) which are your Internet Service Provider’s DNS servers.
Check and/or edit your dns servers:
gksudo scite /etc/resolv.conf
It should look something like this:
search my.isp.com
nameserver 4.4.2.2
nameserver 4.4.2.4
You may have an extra IP address there, possibly your router (192.168.1.1), and if you haven’t got dns servers configured in your router config, this may cause a problem/slowdown as well. EG:
search my.isp.com
nameserver 192.168.1.1
nameserver 4.4.2.2
nameserver 4.4.2.4
Just remove the first one and leave the two ISP DNS server IP’s.

This worked.  TYVM!

---

### Post by theteju on 2011-05-09
I am running on same boat. In fact I thought I screwed up my system so I did fresh install 10.04 last night but still my XP is more faster than ubuntu. 

Is there intel wireless networkcard driver issue anyone know of?

I am confuse to edit resolv.conf file because, I have same three DNS servers entry on my router's admin page. My router is pretty latest linksys E-3000. I know you should have only two dns servers but is it something new these days?

I haven't tried editing nsswitch.conf file yet, but just to confirm, disabling ipv6 does not solve the problem. 

My internet is not horrible slow but its slower than it used to be. and certainly fast under XP.

my problem is not solved yet. thanks all.

---

### Post by theteju on 2011-05-09
OKey to add further, 

I just read the sticky on the forum about supported wireless cards on ubuntu where my particular card intel 5300 abgn should have driver "iwlwifi" while my system is using the driver "iwlagn" 

How to confirm what driver is loaded for sure and how to install iwlwifi driver if  there. I know in the recent kernel the driver is merged from intel. 

So is it possible that its not used on my system?

any help appreciated.

thanks.

This is what I found,,, Hope that helps an expert to answer my question. as I dont understand much...

theteju@ubuntu:/etc/modprobe.d$ locate iwlwifi | grep 2.6.32-31
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/iwlwifi
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
/usr/src/linux-headers-2.6.32-31/drivers/net/wireless/iwlwifi
/usr/src/linux-headers-2.6.32-31/drivers/net/wireless/iwlwifi/Kconfig
/usr/src/linux-headers-2.6.32-31/drivers/net/wireless/iwlwifi/Makefile
/usr/src/linux-headers-2.6.32-31-generic/include/config/iwlwifi
/usr/src/linux-headers-2.6.32-31-generic/include/config/iwlwifi.h
/usr/src/linux-headers-2.6.32-31-generic/include/config/iwlwifi/leds.h
theteju@ubuntu:/etc/modprobe.d$ 

I understand, that iwlwifi is driver but is it the one being used on my system or iwlagn and iwlwifi are both same drivers? I am damm confused.

---

### Post by theteju on 2011-05-10
I edited nsswitch.conf file accordingly and not much difference. 

I hate to say that but, windows 7 is out performing ubuntu now. new IE 9 is Amazingly fast/faster/fastest currently at this moment.

Do something guys. .I hate loggin in windows still I have to.

---

### Post by cctsim on 2011-06-27
I had the same problem with Lucid and none of the above solutions worked.

The only solution that worked for me was to either compile and install the compatibility drivers manually 

compat-wireless-2.6.38.2-2.tar.bz2

downloaded from

[http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.38_stable_releases](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.38_stable_releases)



or recently to install the deb package:

linux-backports-modules-compat-wireless-2.6.38-2.6.32-32-generic_2.6.32-32.32_i386.deb

downloaded from 

[https://launchpad.net/ubuntu/lucid/i386/linux-backports-modules-compat-wireless-2.6.38-2.6.32-32-generic/2.6.32-32.32](https://launchpad.net/ubuntu/lucid/i386/linux-backports-modules-compat-wireless-2.6.38-2.6.32-32-generic/2.6.32-32.32)


The latter is the easiest method I guess. Now I get the max speed offered by my ISP.

---

### Post by pudlo on 2011-12-05
The solution for me was to disable power management functions by calling:

iwconfig wlan0 power off


Cheers :)

---

