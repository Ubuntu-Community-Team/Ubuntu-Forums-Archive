---
title: "Networking problems since apt-get update"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by pyro-ns on 2011-09-18
Hi guys :)

I've been searching and querying the poor souls on #ubuntu about this one since yesterday and am so far having no luck.

I'm pretty sure the problems started happening after an apt-get update that I did yesterday afternoon. I was trying to get nVidia drivers working and after doing an apt-get update, all of a sudden there was 200mb of files to be updated. I did the update because I thought they were all nVidia related (I think I added a new repository as part of the nVidia attempt, I'll have to have a look at that now that I think about it) and since then (or perhaps since a restart after that), I've been having these problems.

**Problems are as follows:**

[LIST]
[*]I randomly can't open certian websites. I can't open mail.google.com, but can open google.com for example. (I generally can't open a link from any of the search results either). I'd say 99% of the internet is no longer available to me. I normally get a 200 OK and load the favicon, but then the rest of the site sits and "tries" to load for ages and then eventually times out (this can be 10-15 mins or more). This is independant of browser (Chrome and Firefox do exactly the same thing) and is not happening on the other machines on the network (I'm posting through the windows machine and connecting to sites through my phone on wi-fi still works fine).
[*]I can't connect to IRC through a client (and I can't load webchat.freenode.net through a browser).
[*]Can't connect to my mailservers through Thunderbird.
[*]Can no longer see ubuntu machine from other (Windows) machines on the network. I can't even ping the machine. Therefore, I also cannot access Samba shares.
[*]CANNOT ACCESS MY LOCALHOST ENTRIES! Despite these entries being loaded in the hosts file I can't get to anything on localhost! It just does the same loading thing that it does for all the other (WAN) websites that I can't load.
[/LIST]

Pretty much everything network related is dead :(

**What I've tried:**

[LIST]
[*]Multiple sudo apt-get update 's. I've also noticed, however that in a terminal session, apt-get update will tell me that there's duplicate repository updates and that I should run apt-get update (again?). Running apt-get update doesn't give me the duplicate message the second time around, but if I close the terminal and open another terminal, then apt-get update again, i get the same duplicate message. Should I manually edit the conf? Or leave it alone since I've screwed so much other stuff up? :D
[*]nslookup on google and mail.google.com. They resolve to exaclty the same as my windows machine: google.com 74.125.237.48 - .52 mail.google.com (googlemail.l.google.com) 74.125.237.21 - .24.
[*]Setting my DNS entries on the network config itself. They were previously set on the router, with all machines referencing the router for DNS. Setting DNS on the Ubuntu box didn't change anything, so i reverted aback to the router.
[*]Setting non IPV6 DNS on Firefox. Of course, didn't work, but it was part of the to-do list.
[*]There was something that I did last night for troubleshooting, can't remember what it was, but I kept getting "Malformed packet request sent from user. Connection closed by host" or something to that effect.
[*]Tried a few tutorials to revert the packages to their original state, but they were all synaptic (GUI) based and in my history, there are no entried for the last few weeks. As a result, I can't find what the name of the packages were. Is there a log file or message file somewhere that will tell me this?
[*]Dump cache on both browsers. Of course, didn't work, but tried it anyway.
[*]Google :(
[/LIST]
I'm a Ubuntu noob (less than a month running it so far), so I apologise in advance if there's something totally obvious that I have missed.

Also an off-topic question. My NIC seems to go to sleep/disconnect if it's idle for a long time (ie, long enough for the machine to lock and prompt for pw to get back in). Originally I thought it was relted to the machine going to sleep, so I left a torrent on over night and the NIC was still active when I logged back in next morning. Is there a way to prevent this? The Ubuntu machine is now my file/media server, so I can't have it going to sleep on me :P

Thank you all in advance for any help you can offer me :) My ubuntu experience has been pretty smooth thus far and I'm really linking tbh. I had an install of OpenSyse before this that I just wan't gel-ing with at all. Ubuntu seems to be easier out of the box, coming from Windows :)

Cheers :)
Josh

P.s A kind soul on IRC has just informed me that I should check dpkg.log's in /var/log. I'll do this tomorrow when I've got my wits about me a little better and see if i can find the particular packages that were part of that apt-get update.

---

### Post by idlemind324 on 2011-09-18
> There was something that I did last night for troubleshooting, can't  remember what it was, but I kept getting "Malformed packet request sent  from user. Connection closed by host" or something to that effect.

What I had him try last night was:

```
telnet mail.google.com 80
GET index.html
```It should have returned HTTP/1.0 302 Found. Why this wouldn't work in his telnet is rather odd. What makes it worse is his Windows machine is able to get the 302 so it eliminates the ISP.

---

### Post by varunendra on 2011-09-19
For me it is a situation I have never handled myself before, but I think I have seen a few similar situations long ago (apart from [the one]("http://ubuntuforums.org/showthread.php?t=1844817") you posted this thread's link in, following which I reached here). One of them was fixed by changing MTU to a lower value, and a couple of others were kernel-firmware compatibility related. Regardless of whether yours a similar situation or not, I would like to have a look at the basic details first. Accordingly, please open a terminal, enter the following commands and post back their outputs here:

```

sudo lshw -C network
ifconfig -a
lsmod
```

assuming it is a wireless interface, also this:
```
iwconfig
```

Please wrap the outputs in [ code]....[ /code] tags as explained [here]("http://ubuntuforums.org/misc.php?do=bbcode#code") for better readability.

---

### Post by pyro-ns on 2011-09-19
> **varunendra said:**
> For me it is a situation I have never handled myself before, but I think I have seen a few similar situations long ago (apart from [the one]("http://ubuntuforums.org/showthread.php?t=1844817") you posted this thread's link in, following which I reached here). One of them was fixed by changing MTU to a lower value, and a couple of others were kernel-firmware compatibility related. Regardless of whether yours a similar situation or not, I would like to have a look at the basic details first. Accordingly, please open a terminal, enter the following commands and post back their outputs here:

```

sudo lshw -C network
ifconfig -a
lsmod
```assuming it is a wireless interface, also this:
```
iwconfig
```Please wrap the outputs in [ code]....[ /code] tags as explained [here]("http://ubuntuforums.org/misc.php?do=bbcode#code") for better readability.


Not a problem at all and thank you for posting :) This isn't a wireless interface by the way, wired only.

sudo lshw -C network results:
```

  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:8c:b8:e8:9e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:fe9fc000-fe9fffff ioport:c800(size=256) memory:fe9c0000-fe9dffff

```ifconfig -a results:
```

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:b8:e8:9e  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:feb8:e89e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30095 (30.0 KB)  TX bytes:29768 (29.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4672 (4.6 KB)  TX bytes:4672 (4.6 KB)

```lsmod results:
```

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
xt_tcpudp              12531  3 
nf_conntrack_ipv4      19024  2 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_state               12514  2 
nf_conntrack           69744  2 nf_conntrack_ipv4,xt_state
xt_mark                12499  4 
xt_NFQUEUE             12611  2 
ipt_REJECT             12512  2 
nfnetlink_queue        17409  2 
nfnetlink              13983  3 nfnetlink_queue
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
nvidia               7098106  34 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
iptable_filter         12706  1 
ip_tables              18125  1 iptable_filter
x_tables               21907  7 xt_tcpudp,xt_state,xt_mark,xt_NFQUEUE,ipt_REJECT,iptable_filter,ip_tables
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
psmouse                73312  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_atk0110           17664  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
usbhid                 41704  0 
floppy                 60032  0 
hid                    77084  1 usbhid
sky2                   49172  0 
crc_itu_t              12627  1 firewire_core
pata_marvell           12756  0 

```also, the contents for dpkg.log for that day (I can't see any problems, but just in case):
```

2011-09-17 13:17:53 startup archives unpack
2011-09-17 13:18:01 install nvidia-173 <none> 173.14.30-0ubuntu1
2011-09-17 13:18:01 status half-installed nvidia-173 173.14.30-0ubuntu1
2011-09-17 13:18:06 status triggers-pending man-db 2.5.9-4
2011-09-17 13:18:06 status half-installed nvidia-173 173.14.30-0ubuntu1
2011-09-17 13:18:06 status unpacked nvidia-173 173.14.30-0ubuntu1
2011-09-17 13:18:06 status unpacked nvidia-173 173.14.30-0ubuntu1
2011-09-17 13:18:06 trigproc man-db 2.5.9-4 2.5.9-4
2011-09-17 13:18:06 status half-configured man-db 2.5.9-4
2011-09-17 13:18:08 status installed man-db 2.5.9-4
2011-09-17 13:18:08 startup packages configure
2011-09-17 13:18:08 configure nvidia-173 173.14.30-0ubuntu1 <none>
2011-09-17 13:18:08 status unpacked nvidia-173 173.14.30-0ubuntu1
2011-09-17 13:18:09 status half-configured nvidia-173 173.14.30-0ubuntu1
2011-09-17 13:18:43 status installed nvidia-173 173.14.30-0ubuntu1
2011-09-17 13:18:43 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2011-09-17 13:18:43 status triggers-awaited nvidia-173 173.14.30-0ubuntu1
2011-09-17 13:18:43 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2011-09-17 13:18:44 status triggers-awaited nvidia-173 173.14.30-0ubuntu1
2011-09-17 13:18:44 trigproc python-gmenu 2.30.5-0ubuntu3 <none>
2011-09-17 13:18:44 status half-configured python-gmenu 2.30.5-0ubuntu3
2011-09-17 13:18:44 status installed python-gmenu 2.30.5-0ubuntu3
2011-09-17 13:18:44 status triggers-pending python-support 1.0.10ubuntu3
2011-09-17 13:18:44 trigproc bamfdaemon 0.2.90-0ubuntu3 <none>
2011-09-17 13:18:44 status half-configured bamfdaemon 0.2.90-0ubuntu3
2011-09-17 13:18:44 status installed nvidia-173 173.14.30-0ubuntu1
2011-09-17 13:18:44 status installed bamfdaemon 0.2.90-0ubuntu3
2011-09-17 13:18:44 trigproc python-support 1.0.10ubuntu3 <none>
2011-09-17 13:18:44 status half-configured python-support 1.0.10ubuntu3
2011-09-17 13:18:48 status installed python-support 1.0.10ubuntu3
2011-09-17 13:18:50 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2011-09-17 13:18:50 status not-installed fakepackage <none>
2011-09-17 13:18:50 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2011-09-17 13:18:50 status not-installed fakepackage <none>
2011-09-17 13:18:50 startup packages configure
2011-09-17 13:18:50 trigproc python-gmenu 2.30.5-0ubuntu3 <none>
2011-09-17 13:18:50 status half-configured python-gmenu 2.30.5-0ubuntu3
2011-09-17 13:18:50 status installed python-gmenu 2.30.5-0ubuntu3
2011-09-17 13:18:50 status triggers-pending python-support 1.0.10ubuntu3
2011-09-17 13:18:50 trigproc bamfdaemon 0.2.90-0ubuntu3 <none>
2011-09-17 13:18:50 status half-configured bamfdaemon 0.2.90-0ubuntu3
2011-09-17 13:18:51 status installed bamfdaemon 0.2.90-0ubuntu3
2011-09-17 13:18:51 trigproc python-support 1.0.10ubuntu3 <none>
2011-09-17 13:18:51 status half-configured python-support 1.0.10ubuntu3
2011-09-17 13:18:51 status installed python-support 1.0.10ubuntu3
2011-09-17 22:42:23 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2011-09-17 22:42:23 status not-installed fakepackage <none>
2011-09-17 22:42:23 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2011-09-17 22:42:23 status not-installed fakepackage <none>
2011-09-17 22:42:23 startup packages configure
2011-09-17 22:42:23 trigproc python-gmenu 2.30.5-0ubuntu3 <none>
2011-09-17 22:42:23 status half-configured python-gmenu 2.30.5-0ubuntu3
2011-09-17 22:42:24 status installed python-gmenu 2.30.5-0ubuntu3
2011-09-17 22:42:24 status triggers-pending python-support 1.0.10ubuntu3
2011-09-17 22:42:24 trigproc bamfdaemon 0.2.90-0ubuntu3 <none>
2011-09-17 22:42:24 status half-configured bamfdaemon 0.2.90-0ubuntu3
2011-09-17 22:42:24 status installed bamfdaemon 0.2.90-0ubuntu3
2011-09-17 22:42:24 trigproc python-support 1.0.10ubuntu3 <none>
2011-09-17 22:42:24 status half-configured python-support 1.0.10ubuntu3
2011-09-17 22:42:28 status installed python-support 1.0.10ubuntu3

```Thanks to everyone for their help thus far :)

---

### Post by pyro-ns on 2011-09-20
Well. I have absolutely no idea what's happened, but my Ubuntu machine is working fine again... It's sharing files fine, it's browsing the web fine, I'm downloading my latest emails now.

I haven't done anything to it except run banshee and shutdown/startup maybe twice? (No point having it on when I can't do anything with it). It's just magically come good :S

I know that means that it can probably fail at any given moment, but while I've got it, I'm going to finish this bloody client work :P

Should I set this as solved?

A bit thanks again to you guys for trying to help out :)

---

### Post by praseodym on 2011-09-20
Do you really need the firewall? You may uninstall it or punch appropriate holes into it. In Ubuntu all ports are closed by default, only allowed ports will be opened by choice, in contrast to Windows, where all ports are open by default. So you need a firewall there, in Ubuntu for home use it is not neccessary.

Glad it worked, though :popcorn:

---

### Post by pyro-ns on 2011-09-21
I guess the best question to ask is, What firewall? Haha. Where in that list did you see it? I didn't know that I had one...

I also noticed something strange last night. If i turn off my wired network just by clicking the network icon and disconnecting it, my localhost stops working as well...

---

