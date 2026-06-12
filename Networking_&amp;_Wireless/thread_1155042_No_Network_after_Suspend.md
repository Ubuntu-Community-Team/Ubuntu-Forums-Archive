---
title: "No Network after Suspend"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by cottfcfan on 2009-05-10
I know this has been mentioned a number of times, but I really find the suspend feature useful.
 I hava a Dell Inspiron 531 compt. And use a Ralink RT2501USB Wireless adaptor, which worked "out of the box" in 9.04 with the native driver.
 But the only way to get network again after suspend is to remove and then replace the wireless card.
 Does anyone know if there is a workaround to this problem?

---

### Post by Crafty Kisses on 2009-05-10
You should see if the wireless module is being used when you come back from suspend and your network connection is not working. Try posting the results of the following command:
```
lsmod
```

---

### Post by cottfcfan on 2009-05-10
codename,
Thanx for your reply.
This is the output from lsmod, after suspend with no network.
 Does it mean anything to you?

Module                  Size  Used by 
usblp                  20224  0 
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96296  3 radeon 
agpgart                42696  1 drm 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge 
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video 
input_polldev          11912  0 
ipt_REJECT             11136  1 
ipt_LOG                13700  1 
xt_limit               10116  2 
xt_tcpudp              11008  9 
xt_state               10112  5 
ipt_addrtype           10496  4 
ip6table_filter        10624  1 
ip6_tables             20880  1 ip6table_filter 
nf_nat_irc             10240  0 
nf_conntrack_irc       13220  1 nf_nat_irc 
nf_nat_ftp             10752  0 
nf_nat                 25876  2 nf_nat_irc,nf_nat_ftp 
nf_conntrack_ipv4      21388  7 nf_nat 
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4 
nf_conntrack_ftp       15652  1 nf_nat_ftp 
nf_conntrack           72008  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp 
iptable_filter         10752  1 
ip_tables              19472  1 iptable_filter 
x_tables               23044  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables 
lp                     17156  0 
parport                42220  2 ppdev,lp 
arc4                    9856  2 
ecb                    10752  2 
rt73usb                33412  0 
crc_itu_t              10112  1 rt73usb 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi 
rt2500usb              27904  0 
rt2x00usb              18688  2 rt73usb,rt2500usb 
rt2x00lib              37888  3 rt73usb,rt2500usb,rt2x00usb 
led_class              12036  1 rt2x00lib 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
mac80211              217208  2 rt2x00usb,rt2x00lib 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
cfg80211               38032  2 rt2x00lib,mac80211 
pcspkr                 10496  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              15200  1 snd 
dcdbas                 15264  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm 
i2c_nforce2            14980  0 
k8temp                 12416  0 
usbhid                 42336  0 
psmouse                61972  0 
serio_raw              13316  0 
usb_storage            82880  0 
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon 
font                   16384  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit

---

### Post by Crafty Kisses on 2009-05-10
Alright here's what I want you to do, I see the modules in there, so that gives me a hint. Just for the record, if you're wondering what the RaLink modules are called, here they are:
```
rt73
rt73usb
```
So here's what I want you to do, or try at least. Next time you go into suspend, and the wireless isn't working, try running these commands:
```
sudo rmmod rt73
```
Then run this command after that one:
```
sudo modprobe rt73
```
Then try to reconnect and see if you can connect.

---

### Post by cottfcfan on 2009-05-10
Codename

Followed your instructions and got the following:

wayne@wayne-desktop:~$ sudo rmmod rt73 
[sudo] password for wayne: 
ERROR: Module rt73 does not exist in /proc/modules 
wayne@wayne-desktop:~$ sudo modprobe rt73 
FATAL: Module rt73 not found. 

Any Ideas?

---

### Post by Crafty Kisses on 2009-05-10
Oh ok sorry about that, try putting "usb" after "rt73" so do the following:
```
sudo rmmod rt73usb
```
Then obviously do:
```
sudo modprobe rt73usb
```

---

### Post by cottfcfan on 2009-05-10
Codename:

Ran the commands and I can now connect, by clicking the network icon and connecting to "Netgear"
 Any way to get this to work automatically?

---

### Post by Crafty Kisses on 2009-05-10
Not sure, but I remember in older distributions there was a configuration file somewhere within Power Management where you could add modules to load when started. This was on Ubuntu Brainstorm, [http://www.raiden.net/images/articles/wattos/disks.png](http://www.raiden.net/images/articles/wattos/disks.png). Now I'm not sure if there's anything like that, but that would work if there was. I also came across LongRun upon research, but this appears very old, but have a look at it. [https://help.ubuntu.com/community/LongRunHowTo](https://help.ubuntu.com/community/LongRunHowTo). Your other option is to find a script that would do it for you, ask somebody to make one for you, and I'm sure someone would be happy to make one.

---

### Post by cottfcfan on 2009-05-10
Thanks for your help codename.
 I`ll look at it again tommorrow.

---

### Post by Crafty Kisses on 2009-05-10
No problem, I'm glad I could help.

---

### Post by cottfcfan on 2009-05-11
SOLVED at last.
created a file and added a single line:
SUSPEND_MODULES=rt73usb
saved in etc/pm/config.d
Now network resumes automatically.
This has bugged me for weeks.

---

### Post by floborg on 2009-05-12
Did you name the file "madwifi?"  I have a similar problem, but I use the Inspiron 530's built-in ethernet card.  Never happened w/Hardy.  Apparently, the driver in use is "e1000e."

---

### Post by cottfcfan on 2009-05-12
I created the file madwifi & saved it in etc/pm/config.d.
 Check your driver by running lsmod in terminal.
 If your driver is "e1000e" then save the line:
SUSPEND_MODULES=e1000e  and save in that file. Or change the
"e1000" to whatever your driver is called.

---

### Post by floborg on 2009-05-12
That's what I figured.  I am not connecting wirelessly, and I think the fix they put into Jaunty was specifically for wireless.  I couldn't find any other bug reports for wired connections.

---

### Post by ed325i on 2009-05-20
My issue is with a wired connection.  Should my line be:

SUSPEND_MODULES=eth0

---

### Post by maxbur on 2009-05-20
> **ed325i said:**
> My issue is with a wired connection.  Should my line be:

SUSPEND_MODULES=eth0

It should probably be ```
SUSPEND_MODULES=forcedeth
``` if you're using Ubuntu's default ethernet driver. 

If you run ```
sudo lshw
``` from a terminal, you should be able to find the specifications for your network card, including the driver it's using.

---

