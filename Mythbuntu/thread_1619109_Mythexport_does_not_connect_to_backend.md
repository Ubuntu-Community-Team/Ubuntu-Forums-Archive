---
title: "Mythexport does not connect to backend"
date: 2010-11-11
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2010-11-11
So I'm trying out Mythexport (nuvexport?) and nothing is happening even though the mythexport web interface is running, shows the queued job and not reporting anything out of sorts.  Mythweb shows nothing out of sorts but the job queue is empty.

But mythexport's log give a little hint.

```
me@htpc:~$ tail /var/log/mythtv/mythexport.log
…
November 10 01:38:33 htpc /usr/bin/mythexport-daemon[1215]: Can't connect to MythTV: Couldn't communicate with 192.168.0.55 on port 6543:  IO::Socket::INET::MythTV: connect: Connection refused
 at line 88 in /usr/bin/mythexport-daemon

```

but remote and local mythfrontends have no problems connecting.  Backend port is the default.  Restarting backend did not help.

Any ideas, anyone?

_&c stuff_

Mythfrontend, backend, and mythexport running on Mythbuntu 10.10 upgraded from 10.04, with gnome desktop, running on dedicated HTPC. ([Hardware]("http://ubuntuforums.org/showthread.php?t=1587584"))   ([Install]("http://ubuntuforums.org/showthread.php?t=1594907")) 

```
me@htpc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:eb:d7:f3
          inet addr:192.168.0.55  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::92fb:a6ff:feeb:d7f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:51940316 (51.9 MB)  TX bytes:9146150 (9.1 MB)
          Interrupt:43 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3237464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3237464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:707850160 (707.8 MB)  TX bytes:707850160 (707.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:ef:0a:cc:8d
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

me@htpc:~$ ps -A | grep myth
 2211 ?        01:11:25 mythfrontend.re
 7135 ?        00:00:04 mythbuntu-contr
 7350 ?        00:00:33 mythbackend

me@htpc:~/.mythtv$ cat config.xml
<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>ee18236a-04c2-4d79-81f8-e3baa0fb5fa2</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>192.168.0.55</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>********</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

Please attach all output as a file in bug reports.
MythTV Version   : 26437
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.7.0
Options compiled in:
 linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libudev using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

```

---

### Post by hairfarmer88 on 2010-12-12
I've having the same issue also with Mythbuntu 10.10 which was upgraded from 10.04

Anyone have any suggested what to try and where to look for problems?

Thanks.

---

