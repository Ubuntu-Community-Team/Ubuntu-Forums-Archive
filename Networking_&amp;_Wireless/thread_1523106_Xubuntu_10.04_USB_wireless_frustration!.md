---
title: "Xubuntu 10.04 USB wireless frustration!"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by 23senick on 2010-07-03
Hi, please help Linux newbie who wants it to work! I've loaded Xubuntu 10.04 onto Dell Dimension LR800. All works, except Belkin USB wireless (which does work with XP). The Belkin is probably F5D7050v.4000. 

In many ways it seems to work, but I can't actually get connection to web. I can see wireless networks, and it does spot my router (though for some reason only by checking hidden networks). I get message to say it's connected. But Firefox says it can't connect, and neither will updater. 

I've been checking all sorts to make it work.  In firefox I went into about:config and toggled IPv6. I checked the drivers and the firmware appears to be in place. Not sure if these are clues but on running thru the ubuntu wireless troubleshoot in the terminal it resulted in wireless USB state is "disconnected", & "access point: not-associated" 

Any help gratefully received:)

---

### Post by roosh on 2010-07-03
please post the output of
```
lsusb
```

---

### Post by 23senick on 2010-07-09
Roosh, sorry, for some reason didn't see your post.  The output you asked for is below.  It seems very close to working, can see router and seems to connect - says it's active (though no signal strength/quality info).  Any help gratefully received!:p

  	 	 	 	 	 	  [LEFT] [COLOR=#000000][FONT=Times New Roman][SIZE=3]Bus 004 Device 002: ID 07b5:9904 Mega World International, Ltd [/SIZE][/FONT][/COLOR] [/LEFT]
 [LEFT] [COLOR=#000000][FONT=Times New Roman][SIZE=3]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Times New Roman][SIZE=3]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Times New Roman][SIZE=3]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Times New Roman][SIZE=3]Bus 001 Device 002: ID 050d:705c Belkin Components 802.11bg[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Times New Roman][SIZE=3]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT][/COLOR][/LEFT]

---

### Post by Jose Catre-Vandis on 2010-07-09
Does [this thread]("http://newyork.ubuntuforums.org/showthread.php?t=1195306") help? seems its in the kernel, you just need to enable wireless. If all else fails, try installing **wicd**

---

### Post by 23senick on 2010-07-09
Thanks [Jose Catre-Vandis]("http://ubuntuforums.org/member.php?u=78483") afraid that doesn't lead me far.  I just can't work out how to get the thing working.  Seems to be a shortcvoming of xubuntu - disappointing they can't sort this - or can anyone suggest anything else?

---

### Post by roosh on 2010-07-09
OK I've looked around a bit and came up with this guide: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29)

It's a little old, and it is possible that you won't need to compile a new driver so before going through it, try this:

Run ```
lsmod
``` in a terminal and post it here.

If you're impatient (I know I'd be) look for the entry in the output of lsmod: zd1211rw

If you can't see it run: ```
sudo modprobe zd1211rw
```

See if that works. In any case, post back.

---

### Post by 23senick on 2010-07-10
Thanks, here's the output from lsmod, the zd reference is there about 3 times 	 	 	 	 	     	 	 	 	 	 	  [LEFT] [COLOR=#000000][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]Module                  Size  Used by[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]ipt_MASQUERADE          1407  1 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]xt_state                1098  1 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]ipt_REJECT              1928  2 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]xt_tcpudp               2011  4 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]iptable_filter          2271  1 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_nat_h323             5077  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_conntrack_h323      46926  1 nf_nat_h323[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_nat_pptp             1920  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_conntrack_pptp       4413  1 nf_nat_pptp[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_nat_proto_gre        1259  1 nf_nat_pptp[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_nat_tftp              716  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_conntrack_tftp       2893  1 nf_nat_tftp[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_nat_sip              5108  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_conntrack_sip       15389  1 nf_nat_sip[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_nat_irc              1124  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_conntrack_irc        3332  1 nf_nat_irc[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_nat_ftp              1836  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_conntrack_ftp        5381  1 nf_nat_ftp[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]iptable_nat             4414  1 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_conntrack           61583  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nf_defrag_ipv4          1073  1 nf_conntrack_ipv4[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]ip_tables               9991  2 iptable_filter,iptable_nat[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]i810                   16400  2 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]drm                   162471  3 i810[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_ens1371            18814  6 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]gameport                9089  1 snd_ens1371[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_ac97_codec        100646  1 snd_ens1371[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]ac97_bus                1002  1 snd_ac97_codec[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_pcm_oss            35308  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_mixer_oss          13746  3 snd_pcm_oss[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_pcm                70662  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_seq_dummy           1338  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_seq_oss            26726  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_seq_midi            4557  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]arc4                    1153  2 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_rawmidi            19056  2 snd_ens1371,snd_seq_midi[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]zd1211rw               42217  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_timer              19098  2 snd_pcm,snd_seq[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]fbcon                  35102  71 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]mac80211              204922  1 zd1211rw[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]tileblit                2031  1 fbcon[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]font                    7557  1 fbcon[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd                    54148  18 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]bitblit                 4707  1 fbcon[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]cfg80211              126485  2 zd1211rw,mac80211[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]soundcore               6620  3 snd[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]dell_wmi                1793  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]softcursor              1189  1 bitblit[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]intel_agp              24177  1 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]snd_page_alloc          7076  1 snd_pcm[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]ppdev                   5259  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]psmouse                63245  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]lp                      7028  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]vga16fb                11385  1 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]dcdbas                  5422  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]parport_pc             25962  1 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]agpgart                31724  3 drm,intel_agp[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]shpchp                 28820  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]serio_raw               3978  0 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]vgastate                8961  1 vga16fb[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]parport                32635  3 ppdev,lp,parport_pc[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nls_iso8859_1           3249  1 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]nls_cp437               4919  1 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]vfat                    8901  1 [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]fat                    47767  1 vfat[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=1][COLOR=#000000]floppy                 53016  0[/COLOR][/SIZE][/FONT][/LEFT]

---

### Post by xMatterx on 2010-07-10
I have this exact same problem but with a different adapter

---

### Post by roosh on 2010-07-10
Hmm, I don't know what to say now. It looks like your driver is loading fine. Does it show in network manager that wireless is enabled (as Jose mentioned in [http://newyork.ubuntuforums.org/showthread.php?t=1195306)?](http://newyork.ubuntuforums.org/showthread.php?t=1195306)?)

Also, try running ```
iwconfig
```

---

### Post by Jose Catre-Vandis on 2010-07-11
Maybe [this]("http://ubuntuforums.org/showthread.php?t=1528695") will also help

---

### Post by 23senick on 2010-07-11
Thanks guys.  I'll try the steps in the link, just can't get to the computer at present.  Here's the output from iwconfig

iiwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
         Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Power Management:off

 Wireless is enabled.  It's a bit of a mystery, my wifi is grey (if it appears at all - sometimes have to go thru hidden wireless network).  It sees the router, just doesn't show speed or signal strength).  

I'll post again once i've tried the steps...

---

### Post by 23senick on 2010-07-11
tried [B]sudo gedit /etc/NetworkManager/nm-system-settings.conf but it wouldn't accept the command "sudo gedit"

Sorry but my lack of experience with Linux...can't see if I'm doing anything wrong.
[/B]

---

### Post by roosh on 2010-07-12
gedit is for Ubuntu.

I belive Xubuntu uses mousepad. Try running ```
sudo mousepad /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by 23senick on 2010-07-18
[LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]Thanks, didn't realise this was to help me overcome the sudo gedit problem.  On entering in the terminal “sudo mousepad /etc/NetworkManager/nm-system-settings.conf”[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]this is the output (along with many warnings about damaging the system)....[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]# This file is installed into /etc/NetworkManager, and is loaded by [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]# NetworkManager by default.  To override, specify: '--config file' [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]# during NM startup.  This can be done by appending to DAEMON_OPTS in [/COLOR][/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]# the file:[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]#[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]# /etc/default/NetworkManager[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]#[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000][main][/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]plugins=ifupdown,keyfile[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000][ifupdown][/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]managed=false[/COLOR][/SIZE][/FONT][/LEFT]
 [LEFT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT] [/LEFT]
 [LEFT] [FONT=Arial][SIZE=2][COLOR=#000000]Does that tell us anything?  Should I be doing something with this? [/COLOR][/SIZE][/FONT] [/LEFT]

---

### Post by 23senick on 2010-07-20
Thanks to all who tried to help.  I solved this by buying new USB wireless device - Sparklan.  Worked out of box.  So maybe Belkin devices are a bit of an issue.  One tip I didn't get round to trying - plug the PC in and get updates - there's a chance this could have resolved it.

---

