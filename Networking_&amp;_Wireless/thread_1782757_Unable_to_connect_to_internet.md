---
title: "Unable to connect to internet"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by sandy0594 on 2011-06-15
Hi all,i am a bit new to Linux platform.Today,i happen to update something in Ubuntu 10.10 when update manager showed that there are new updates.However,after updating i happen to loose my n/w connections.To my knowledge,the updates were not Linux-Headers,as i have updated them a week ago.So,what would it be the problem that i lost my n/w connections and someone kindly suggest me as of how to configure the n/w connection.

here are some details

```

sandy@ubuntu:~/Desktop/AR$ uname -a
Linux ubuntu 2.6.35-30-generic #54-Ubuntu SMP Tue Jun 7 18:40:23 UTC 2011 i686 GNU/Linux

sandy@ubuntu:~/Desktop/AR$ dpkg -s pppoeconf
Package: pppoeconf
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 340
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 1.19ubuntu1
Depends: whiptail-provider | whiptail, ppp (>= 2.4.2+20040428-2) | pppoe (>= 3.0), ppp (>= 2.4.1.uus2-4), gettext-base (>= 0.13), sed (>= 3.95)
Recommends: locales
Suggests: xdialog
Description: configures PPPoE/ADSL connections
 User-friendly tool for initial configuration of a DSL (PPPoE) connection.
Original-Maintainer: Gregory Colpart <reg@debian.org>

sandy@ubuntu:~/Desktop/AR$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

If i am trying to edit the connection,it is asking for device MAC Address which i don't know.I didn't face this problem earlier.It simply used to connect automatically as soon as i give my usename and password

---

### Post by dandnsmith on 2011-06-15
I'm not sure what's happening (what are n/w connections?)
ifconfig shows noting but the loopback, which isn't enough to communicate outside the box.
Normally I'd say get the MAC from ifconfig - but that won't work as you'r not seeing it.

There should be some logs created on bootup which show interfaces and problems (amongst other things) - access via dmesg or look in /var/log/messages or try sudo lshw |less (check for eth?)

---

### Post by sandy0594 on 2011-06-16
I tried seeing the messages /var/log/messages.Below are the last lines of it

```

Jun 16 08:58:40 ubuntu kernel: [   15.764769] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jun 16 08:58:40 ubuntu kernel: [   15.894782] Console: switching to colour frame buffer device 128x48
Jun 16 08:58:40 ubuntu kernel: [   15.896914] fb0: inteldrmfb frame buffer device
Jun 16 08:58:40 ubuntu kernel: [   15.896916] drm: registered panic notifier
Jun 16 08:58:40 ubuntu kernel: [   15.896918] Slow work thread pool: Starting up
Jun 16 08:58:40 ubuntu kernel: [   15.897491] Slow work thread pool: Ready
Jun 16 08:58:40 ubuntu kernel: [   15.897515] No ACPI video bus found
Jun 16 08:58:40 ubuntu kernel: [   15.897554] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jun 16 08:58:40 ubuntu kernel: [   15.897591] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jun 16 08:58:40 ubuntu kernel: [   15.978671] hda_codec: ALC887-VD: BIOS auto-probing.
Jun 16 08:58:40 ubuntu kernel: [   16.407974] Adding 261116k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261116k 
Jun 16 08:58:40 ubuntu kernel: [   16.424159] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
Jun 16 08:58:40 ubuntu kernel: [   16.504453] type=1400 audit(1308194920.622:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1116 comm="apparmor_parser"
Jun 16 08:58:40 ubuntu kernel: [   16.505211] type=1400 audit(1308194920.622:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1116 comm="apparmor_parser"
Jun 16 08:58:40 ubuntu kernel: [   16.522897] type=1400 audit(1308194920.638:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1141 comm="apparmor_parser"
Jun 16 08:58:40 ubuntu kernel: [   16.523040] type=1400 audit(1308194920.638:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1142 comm="apparmor_parser"
Jun 16 08:58:40 ubuntu kernel: [   16.523536] type=1400 audit(1308194920.638:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1142 comm="apparmor_parser"
Jun 16 08:58:40 ubuntu kernel: [   16.523807] type=1400 audit(1308194920.638:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1142 comm="apparmor_parser"
Jun 16 08:58:40 ubuntu kernel: [   16.558659] ppdev: user-space parallel port driver
Jun 16 08:58:42 ubuntu kernel: [   18.379591] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
Jun 16 09:05:50 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1098" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

```

I think Ubuntu installed IPV6,earlier it was IPV4(may be this is causing up this messup)..It's just a hunch
Kindly someone say me what to do,i am really having tough time with configuring Ubuntu n/w connections

---

### Post by dandnsmith on 2011-06-16
Have a look under the System Admin stuff for Network Tools - that should give you data for anything configured at the time.

The ip6_tables entry you show may be a net filtering thing (look at the name), But doesn't account for the lack of entries in ifconfig. Did you try iwconfig?

You didn't explain the meaning you associate with n/w connections - is this network-wired network-wireless or what>

---

### Post by sandy0594 on 2011-06-16
My bad...It's wired.But i have been using Ubuntu from past 2 months.I have updated kernels say like 4-5 times.Every time i update them,i need to configure my n/w connections,i mean patching my n/w drivers and things like that.But this particular update 2 days back was something to do with n/w connection(IPV6 my guess).Many times these forums came to my rescue,i hope this time too i will get you people's help.

Mine is DSL Connection,i used to right-click on the network notification area=>edit connection=>add  new, using PPPoE method and user name and pass from the ISP.But,the notification area is changed completely and more confusing.

Thanks in advance.

---

### Post by dandnsmith on 2011-06-16
Sandy,
I'm sorry to say that you've got out of my knowledge zone now.
I'm using 10.04 (as I prefer the LTS versions), so don't know about 10.10 differences, also I connect either from my desktop via an external modem/router, or from a laptop using a wireless connection to a router.

The only thing I can now guess at is that you want to use IP4, not IP6, as most equipment and web sites are IP4. My connections are such that I can pick IP4 or IP6, so I have just disabled IP6 so that it cannot interfere.

I hope this little bit might help, or possibly, someone else can help you set up the connection. Have you looked at the tutorial section of these forums to see if there is anything there?

---

### Post by dandnsmith on 2011-06-16
Just been having a search "dsl pppoe" and think [this one](http://ubuntuforums.org/showthread.php?t=1743086) might be of interest to you

---

### Post by sandy0594 on 2011-06-16
Don't know what did the trick..Followed this trick [http://ubuntuforums.org/showthread.php?t=1630023](http://ubuntuforums.org/showthread.php?t=1630023).I don't know if that would have helped me coz i reinstalled my n/w drivers..

Anyhow,thanks for all your replies.

But one thing that is bothering me is why Ubuntu is not supporting ip6

---

### Post by dandnsmith on 2011-06-17
As far as I know, it is supporting IP6 - but very little else is, so it's ove very little practical help when accessing the world at large

---

### Post by itsmeman on 2011-06-17
I use a shared computer and was quite happy  with ubuntu 10.10. I was getting internet through a 2g usb stick (huwai) . Today when I opened the computer it was found that the network manager icon is disappeared from the tab and there is no response when usb stick is inserted into the port. I don't know whether my co-users done it unknowingly.when I gone to installed soft wares, it indicates that network manager is already installed.Please help me to solve the problem

---

### Post by itsmeman on 2011-06-18
I use a shared computer and was quite happy with ubuntu 10.10. I was getting internet through a 2g usb stick (huwai) . Today when I opened the computer it was found that the network manager icon is disappeared from the tab and there is no response when usb stick is inserted into the port. I don't know whether my co-users done it unknowingly.when I gone to installed soft wares, it indicates that network manager is already installed.Please help me to solve the problem

---

