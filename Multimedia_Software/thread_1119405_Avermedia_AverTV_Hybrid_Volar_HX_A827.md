---
title: "Avermedia AverTV Hybrid Volar HX A827"
date: 2009-04-07
forum: Multimedia Software
---

### Post by wiresquire on 2009-04-07
Hi

I bought the A827 USB stick, and noticed the other day, that it had **[announced linux support](http://www.avermedia.com/AVerTV/Press/NewsDetail.aspx?Id=271)**. 

I am running Hardy 8.04 x64, and downloaded the **[drivers](http://www.avermedia.com/avertv/Support/Download.aspx?Type=Software&id=293&tab=APDriver)** from their website. Install went fine, but when I insert the card, I get an error and Ubuntu becomes unstable.
```

[  1180.932326] DVB: registering frontend 0 (A827[0] ATSC)...
[  1180.932390] usbcore: registered new interface driver AVerTV Volar HX/AX/MAX
[  1186.784559] Unable to handle kernel NULL pointer dereference at 0000000000000000 RIP: 
[  1186.784571]  [<ffffffff88af46dd>] :snd_pcm:snd_pcm_open_substream+0x4d/0x90
[  1186.784597] PGD 1330ee067 PUD 133106067 PMD 0 
[  1186.784604] Oops: 0000 [1] SMP 
[  1186.784610] CPU 0 
[  1186.784613] Modules linked in: h826d(PF) averusbh826d dvb_core binfmt_misc rfcomm l2cap bluetooth ipt_MASQUERADE xt_state ipt_REJECT xt_tcpudp kvm_intel kvm ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_conservative cpufreq_userspace cpufreq_ondemand freq_table sbs sbshc dock container af_packet bridge sbp2 parport_pc lp parport snd_hda_intel joydev ipv6 snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi iwl4965 snd_seq_midi_event uvcvideo iwlwifi_mac80211 snd_seq compat_ioctl32 snd_timer videodev sdhci snd_seq_device v4l1_compat iTCO_wdt v4l2_common cfg80211 serio_raw pcspkr psmouse dcdbas mmc_core snd iTCO_vendor_support evdev nvidia(P) i2c_core soundcore video output wmi_acer intel_agp battery ac button shpchp pci_hotplug dm_multipath dm_mod iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack iptable_mangle iptable_filter ip_tables x_tables ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi usbhid hid ata_generic ahci ata_piix libata scsi_mod ohci1394 ieee1394 tg3 ehci_hcd uhci_hcd usbcore thermal processor fan fuse vesafb fbcon tileblit font bitblit softcursor
[  1186.784770] Pid: 6782, comm: pulseaudio Tainted: PF       2.6.24-23-generic #1
[  1186.784775] RIP: 0010:[<ffffffff88af46dd>]  [<ffffffff88af46dd>] :snd_pcm:snd_pcm_open_substream+0x4d/0x90
[  1186.784796] RSP: 0018:ffff81013315dd48  EFLAGS: 00010246
[  1186.784800] RAX: 0000000000000000 RBX: 0000000000000000 RCX: ffff810115574390
[  1186.784805] RDX: 0000000000000000 RSI: 0000000000000002 RDI: ffff81012a643260
[  1186.784809] RBP: ffff81013315ddb0 R08: 00000000000f4240 R09: 0000000000000011
[  1186.784814] R10: 0000000000000000 R11: 0000000000000000 R12: ffff81010c018400
[  1186.784818] R13: ffff8101155c9240 R14: ffff81013315ddb0 R15: 0000000000000001
[  1186.784824] FS:  00007fba158c96f0(0000) GS:ffffffff805b9000(0000) knlGS:0000000000000000
[  1186.784829] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  1186.784833] CR2: 0000000000000000 CR3: 00000001331ba000 CR4: 00000000000026e0
[  1186.784838] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  1186.784842] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  1186.784848] Process pulseaudio (pid: 6782, threadinfo ffff81013315c000, task ffff8101395557d0)
[  1186.784852] Stack:  0000000000000246 ffffffff80253f9c ffff81012a643260 00000000fffffff2
[  1186.784862]  ffff81010c018568 ffffffff88af4845 ffff81013845b700 ffff81010c018580
[  1186.784871]  ffffffff00000000 ffff8101395557d0 ffffffff80234090 ffff81010c018588
[  1186.784878] Call Trace:
[  1186.784892]  [<ffffffff80253f9c>] add_wait_queue+0x1c/0x60
[  1186.784917]  [<ffffffff88af4845>] :snd_pcm:snd_pcm_open+0x125/0x200
[  1186.784936]  [<ffffffff80234090>] default_wake_function+0x0/0x10
[  1186.784948]  [<ffffffff80467b59>] mutex_lock+0x9/0x20
[  1186.784970]  [<ffffffff802b6290>] chrdev_open+0x0/0x1d0
[  1186.784989]  [<ffffffff889d65f5>] :snd:snd_open+0x95/0x190
[  1186.785007]  [<ffffffff802b6351>] chrdev_open+0xc1/0x1d0
[  1186.785031]  [<ffffffff802b10bb>] __dentry_open+0xdb/0x200
[  1186.785053]  [<ffffffff802b12ea>] do_filp_open+0x3a/0x50
[  1186.785089]  [<ffffffff802b0f27>] get_unused_fd_flags+0x77/0x120
[  1186.785112]  [<ffffffff802b135a>] do_sys_open+0x5a/0xf0
[  1186.785130]  [<ffffffff8020c39e>] system_call+0x7e/0x83
[  1186.785166] 
[  1186.785169] 
[  1186.785170] Code: ff 10 85 c0 89 c3 78 29 48 8b 44 24 10 80 88 80 01 00 00 01 
[  1186.785190] RIP  [<ffffffff88af46dd>] :snd_pcm:snd_pcm_open_substream+0x4d/0x90
[  1186.785209]  RSP <ffff81013315dd48>
[  1186.785212] CR2: 0000000000000000
[  1186.785219] ---[ end trace 2cfc11bf6962285e ]---

```

The stick works fine under windows. Does anyone have it working, or have any tips?

TIA
ws

---

### Post by marcuskoze on 2009-05-07
Have you tried following the "troubleshooting" in the text files from the archive ?

---

### Post by wiresquire on 2009-05-20
Yes, I looked at the trouble shooting file. There's nothing in it that has any relevance to the errors above.

Why they claim it works for Ubuntu 8.04 on their website and in press releases, I don't know.

ws

---

### Post by marcuskoze on 2009-05-24
heck, i've tried it too under Jaunty Jackalope 9.04 and failed with this:

```
FATAL: Error inserting h826d (/lib/modules/2.6.28-11-generic/kernel/driv)
```

will update this post if i find any fixes ... sad thing though ...

---

### Post by cbsim on 2009-05-29
It is working fine with the latest 0.07 beta driver at [http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=293&tab=APDriver](http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=293&tab=APDriver)

---

### Post by wiresquire on 2009-05-31
Still same problems as in my original post with 8.04 x64 and 0.07Beta :(

ws

---

### Post by wuxing on 2009-07-06
Any updates on this issue?
The avermedia driver just don't work. :?

---

### Post by wbee on 2009-07-06
((Following this with interest because I want to upgrade from an analog card to a digital card and the user feedback on Tiger Direct is excellent for a product similar to yours.))

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3867990&CatId=1427](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3867990&CatId=1427)

Wiresquire,

Consider sending an an e mail to the manufacturer,asking that they include the drivers in the Synaptic Manager.

((edit.....I stopped reading your terminal output when it said your Pulse Audio was tainted....don't get me started.:-) ))

---

### Post by wiresquire on 2009-08-07
- I never had any success with any driver version with 8.04 x64.
- I have had success with 0.06Beta and 0.07Beta with Ubuntu 9.04 x64.
- The latest 0.08Beta does not work with x64. A similar driver crash to the above :(

ws

---

### Post by wiresquire on 2009-09-18
The latest 0.09Beta driver is working for me on 9.04 x64.

ws

---

### Post by walidus on 2009-10-13
I have 0.09Beta driver on 9.04 x686 and I have a problem.
In setup with my configuration there are channels found, but live Tv don't work.
In system status tuner is unavailable.
In tvtime video is working. For sound i use "arecord -D hw:1,0 -r 48000 -c 2 -f S16_LE | aplay -" .

---

### Post by walidus on 2009-10-13
My log:

==> /var/log/mythtv/mythbackend.log <==
2009-10-13 13:12:29.624 Channel(/dev/video1)::Open(): Can't open video device, error "Permission denied"
2009-10-13 13:12:29.720 DVBChan(2:0) Error: Opening DVB frontend device failed.
            eno: Permission denied (13)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-10-13 13:12:30.448 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-10-13 13:12:30.980 Main::Registering HttpStatus Extension
2009-10-13 13:12:31.310 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-10-13 13:12:31.608 Enabled verbose msgs:  important general
2009-10-13 13:12:31.919 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 13:13:50.294 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 13:28:50.622 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 13:43:50.717 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 13:58:50.806 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 14:13:50.898 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 14:28:51.073 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 14:43:51.321 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 14:58:51.394 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 15:13:51.469 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 15:28:51.740 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 15:43:51.878 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 15:58:51.965 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 16:13:52.245 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 16:28:52.413 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 16:43:52.533 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 16:58:52.640 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 17:13:52.717 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 17:28:52.971 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 17:43:53.336 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 17:58:53.481 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 18:13:53.566 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 18:28:54.244 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 18:43:54.370 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 18:54:56.261 Using runtime prefix = /usr
2009-10-13 18:54:56.304 Empty LocalHostName.
2009-10-13 18:54:56.348 Using localhost value of walidus-laptop
2009-10-13 18:54:56.426 New DB connection, total: 1
2009-10-13 18:54:56.476 Connected to database 'mythconverg' at host: localhost
2009-10-13 18:54:56.516 Closing DB connection named 'DBManager0'
2009-10-13 18:54:56.560 Connected to database 'mythconverg' at host: localhost
2009-10-13 18:54:56.605 New DB connection, total: 2
2009-10-13 18:54:56.649 Connected to database 'mythconverg' at host: localhost
2009-10-13 18:54:56.695 Current Schema Version: 1214
Starting up as the master server.
2009-10-13 18:54:56.906 Channel(/dev/video1)::Open(): Can't open video device, error "Permission denied"
2009-10-13 18:54:56.961 DVBChan(2:0) Error: Opening DVB frontend device failed.
            eno: Permission denied (13)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-10-13 18:54:57.130 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-10-13 18:54:57.171 Main::Registering HttpStatus Extension
2009-10-13 18:54:57.249 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-10-13 18:54:57.293 Enabled verbose msgs:  important general
2009-10-13 18:54:57.339 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 18:58:41.651 Using runtime prefix = /usr
2009-10-13 18:58:41.777 Empty LocalHostName.
2009-10-13 18:58:41.885 Using localhost value of walidus-laptop
2009-10-13 18:58:42.014 New DB connection, total: 1
2009-10-13 18:58:42.122 Connected to database 'mythconverg' at host: localhost
2009-10-13 18:58:42.185 Closing DB connection named 'DBManager0'
2009-10-13 18:58:42.267 Connected to database 'mythconverg' at host: localhost
2009-10-13 18:58:42.361 New DB connection, total: 2
2009-10-13 18:58:42.472 Connected to database 'mythconverg' at host: localhost
2009-10-13 18:58:42.618 Current Schema Version: 1214
Starting up as the master server.
2009-10-13 18:58:42.855 Channel(/dev/video1)::Open(): Can't open video device, error "Permission denied"
2009-10-13 18:58:42.973 DVBChan(2:0) Error: Opening DVB frontend device failed.
            eno: Permission denied (13)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-10-13 18:58:43.238 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-10-13 18:58:43.283 Main::Registering HttpStatus Extension
2009-10-13 18:58:43.361 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-10-13 18:58:43.450 Enabled verbose msgs:  important general
2009-10-13 18:58:43.529 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 18:59:05.141 MainServer::HandleAnnounce Monitor
2009-10-13 18:59:05.221 adding: walidus-laptop as a client (events: 0)
2009-10-13 18:59:05.260 MainServer::HandleAnnounce Monitor
2009-10-13 18:59:05.303 adding: walidus-laptop as a client (events: 1)
2009-10-13 19:00:03.243 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 19:03:59.449 MainServer::HandleAnnounce Monitor
2009-10-13 19:03:59.491 adding: walidus-laptop as a client (events: 0)
2009-10-13 19:03:59.535 MainServer::HandleAnnounce Monitor
2009-10-13 19:03:59.579 adding: walidus-laptop as a client (events: 1)
2009-10-13 19:15:03.384 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 19:30:03.492 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 19:45:03.711 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 19:55:24.236 MainServer::HandleAnnounce Monitor
2009-10-13 19:55:24.285 adding: walidus-laptop as a client (events: 0)
2009-10-13 19:55:24.330 MainServer::HandleAnnounce Monitor
2009-10-13 19:55:24.407 adding: walidus-laptop as a client (events: 1)
2009-10-13 19:55:24.471 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2009-10-13 19:55:24.537 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
2009-10-13 19:55:25.467 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2009-10-13 19:55:25.508 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
2009-10-13 20:00:03.838 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-13 20:07:20.150 MainServer::HandleAnnounce Monitor
2009-10-13 20:07:20.217 adding: walidus-laptop as a client (events: 0)
2009-10-13 20:07:20.251 MainServer::HandleAnnounce Monitor
2009-10-13 20:07:20.296 adding: walidus-laptop as a client (events: 1)

==> /var/log/mythtv/mythfrontend.log <==
2009-10-12 11:33:12.846 Primary screen 0.
2009-10-12 11:33:12.846 Using screen 0, 1280x1024 at 0,0
2009-10-12 11:33:12.847 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-12 11:33:12.847 Switching to square mode (G.A.N.T)
2009-10-12 11:33:12.915 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-10-12 11:33:12.943 lirc_init failed for mythtv, see preceding messages
2009-10-12 11:33:12.957 JoystickMenuClient Error: Joystick disabled - Failed to read /home/walidus/.mythtv/joystickmenurc
2009-10-12 11:33:14.335 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-10-12 11:33:14.514 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-10-12 11:33:14.613 Registering Internal as a media playback plugin.
2009-10-12 11:33:15.228 MythMusic adding CD-Writer: 1,0,0 -- DVD RW AD-7530B 
2009-10-12 11:33:15.357 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-10-12 11:33:15.406 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-12 11:33:27.996 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
2009-10-12 11:33:28.591 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-12 11:33:28.669 Using protocol version 40
2009-10-12 11:34:28.186 Deleting UPnP client...
Starting mythfrontend.real..
2009-10-13 19:03:47.259 New DB connection, total: 2
2009-10-13 19:03:47.259 Connected to database 'mythconverg' at host: localhost
2009-10-13 19:03:47.279 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-10-13 19:03:47.279 Enabled verbose msgs:  important general
2009-10-13 19:03:49.153 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-13 19:03:49.155 Total desktop dim: 1280x1824, over 2 screen[s].
2009-10-13 19:03:49.155 Screen 0 dim: 1280x1024.
2009-10-13 19:03:49.155 Screen 1 dim: 1280x800.
2009-10-13 19:03:49.155 Primary screen 0.
2009-10-13 19:03:49.156 Using screen 0, 1280x1024 at 0,0
2009-10-13 19:03:49.156 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-13 19:03:49.157 Switching to square mode (G.A.N.T)
2009-10-13 19:03:49.185 Using the Qt painter
2009-10-13 19:03:49.187 JoystickMenuClient Error: Joystick disabled - Failed to read /home/walidus/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-10-13 19:03:49.187 lirc_init failed for mythtv, see preceding messages
2009-10-13 19:03:50.290 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-10-13 19:03:50.392 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-10-13 19:03:50.473 Registering Internal as a media playback plugin.
2009-10-13 19:03:51.012 MythMusic adding CD-Writer: 1,0,0 -- DVD RW AD-7530B 
2009-10-13 19:03:51.137 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-10-13 19:03:51.179 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-13 19:03:59.448 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-13 19:03:59.449 Using protocol version 40
2009-10-13 19:04:01.166 Deleting UPnP client...
Starting mythfrontend.real..
2009-10-13 19:55:13.714 New DB connection, total: 2
2009-10-13 19:55:13.715 Connected to database 'mythconverg' at host: localhost
2009-10-13 19:55:13.716 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-10-13 19:55:13.716 Enabled verbose msgs:  important general
2009-10-13 19:55:15.099 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-13 19:55:15.101 Total desktop dim: 1280x1824, over 2 screen[s].
2009-10-13 19:55:15.101 Screen 0 dim: 1280x1024.
2009-10-13 19:55:15.101 Screen 1 dim: 1280x800.
2009-10-13 19:55:15.101 Primary screen 0.
2009-10-13 19:55:15.102 Using screen 0, 1280x1024 at 0,0
2009-10-13 19:55:15.102 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-13 19:55:15.102 Switching to square mode (G.A.N.T)
2009-10-13 19:55:15.137 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-10-13 19:55:15.137 lirc_init failed for mythtv, see preceding messages
2009-10-13 19:55:15.140 JoystickMenuClient Error: Joystick disabled - Failed to read /home/walidus/.mythtv/joystickmenurc
2009-10-13 19:55:16.151 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-10-13 19:55:16.287 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-10-13 19:55:16.341 Registering Internal as a media playback plugin.
2009-10-13 19:55:16.893 MythMusic adding CD-Writer: 1,0,0 -- DVD RW AD-7530B 
2009-10-13 19:55:17.092 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-10-13 19:55:17.139 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-13 19:55:23.572 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
2009-10-13 19:55:24.236 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-13 19:55:24.236 Using protocol version 40
2009-10-13 19:55:29.250 Deleting UPnP client...
Starting mythfrontend.real..
2009-10-13 20:07:14.824 New DB connection, total: 2
2009-10-13 20:07:14.824 Connected to database 'mythconverg' at host: localhost
2009-10-13 20:07:14.826 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-10-13 20:07:14.826 Enabled verbose msgs:  important general
2009-10-13 20:07:15.164 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-13 20:07:15.165 Total desktop dim: 1280x1824, over 2 screen[s].
2009-10-13 20:07:15.166 Screen 0 dim: 1280x1024.
2009-10-13 20:07:15.166 Screen 1 dim: 1280x800.
2009-10-13 20:07:15.166 Primary screen 0.
2009-10-13 20:07:15.166 Using screen 0, 1280x1024 at 0,0
2009-10-13 20:07:15.166 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-13 20:07:15.167 Switching to square mode (G.A.N.T)
2009-10-13 20:07:15.195 Using the Qt painter
2009-10-13 20:07:15.195 JoystickMenuClient Error: Joystick disabled - Failed to read /home/walidus/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-10-13 20:07:15.248 lirc_init failed for mythtv, see preceding messages
2009-10-13 20:07:16.164 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-10-13 20:07:16.294 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-10-13 20:07:16.339 Registering Internal as a media playback plugin.
2009-10-13 20:07:16.440 MythMusic adding CD-Writer: 1,0,0 -- DVD RW AD-7530B 
2009-10-13 20:07:16.580 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-10-13 20:07:16.591 No theme dir: /home/walidus/.mythtv/themes/G.A.N.T
2009-10-13 20:07:20.149 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-13 20:07:20.149 Using protocol version 40

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Oct 13 20:00:01 walidus-laptop /USR/SBIN/CRON[27047]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Oct 13 20:00:01 walidus-laptop /USR/SBIN/CRON[27069]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 13 20:00:20 walidus-laptop pulseaudio[25296]: module-alsa-sink.c: Increasing wakeup watermark to 72,83 ms
Oct 13 20:00:22 walidus-laptop nullmailer[3564]: Rescanning queue.
Oct 13 20:00:22 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1254894049.9813
Oct 13 20:00:22 walidus-laptop nullmailer[27116]: smtp: Failed: Connect failed
Oct 13 20:00:22 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:00:22 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241009.8431
Oct 13 20:00:22 walidus-laptop nullmailer[27117]: smtp: Failed: Connect failed
Oct 13 20:00:22 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:00:22 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241021.8707
Oct 13 20:00:22 walidus-laptop nullmailer[27118]: smtp: Failed: Connect failed
Oct 13 20:00:22 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:00:22 walidus-laptop nullmailer[3564]: Delivery complete, 3 message(s) remain.
Oct 13 20:01:03 walidus-laptop pulseaudio[25296]: module-alsa-sink.c: Increasing wakeup watermark to 72,83 ms
Oct 13 20:01:22 walidus-laptop nullmailer[3564]: Rescanning queue.
Oct 13 20:01:22 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1254894049.9813
Oct 13 20:01:22 walidus-laptop nullmailer[27121]: smtp: Failed: Connect failed
Oct 13 20:01:22 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:01:22 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241009.8431
Oct 13 20:01:22 walidus-laptop nullmailer[27122]: smtp: Failed: Connect failed
Oct 13 20:01:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:01:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241021.8707
Oct 13 20:01:23 walidus-laptop nullmailer[27123]: smtp: Failed: Connect failed
Oct 13 20:01:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:01:23 walidus-laptop nullmailer[3564]: Delivery complete, 3 message(s) remain.
Oct 13 20:01:28 walidus-laptop dhclient: DHCPREQUEST of 192.168.241.141 on eth0 to 192.168.240.1 port 67
Oct 13 20:01:28 walidus-laptop dhclient: DHCPACK of 192.168.241.141 from 192.168.240.1
Oct 13 20:01:28 walidus-laptop dhclient: bound to 192.168.241.141 -- renewal in 392 seconds.
Oct 13 20:02:23 walidus-laptop nullmailer[3564]: Rescanning queue.
Oct 13 20:02:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1254894049.9813
Oct 13 20:02:23 walidus-laptop nullmailer[27128]: smtp: Failed: Connect failed
Oct 13 20:02:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:02:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241009.8431
Oct 13 20:02:23 walidus-laptop nullmailer[27129]: smtp: Failed: Connect failed
Oct 13 20:02:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:02:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241021.8707
Oct 13 20:02:23 walidus-laptop nullmailer[27130]: smtp: Failed: Connect failed
Oct 13 20:02:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:02:23 walidus-laptop nullmailer[3564]: Delivery complete, 3 message(s) remain.
Oct 13 20:03:17 walidus-laptop pulseaudio[25296]: module-alsa-sink.c: Increasing wakeup watermark to 72,83 ms
Oct 13 20:03:23 walidus-laptop nullmailer[3564]: Rescanning queue.
Oct 13 20:03:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1254894049.9813
Oct 13 20:03:23 walidus-laptop nullmailer[27135]: smtp: Failed: Connect failed
Oct 13 20:03:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:03:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241009.8431
Oct 13 20:03:23 walidus-laptop nullmailer[27136]: smtp: Failed: Connect failed
Oct 13 20:03:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:03:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241021.8707
Oct 13 20:03:23 walidus-laptop nullmailer[27137]: smtp: Failed: Connect failed
Oct 13 20:03:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:03:23 walidus-laptop nullmailer[3564]: Delivery complete, 3 message(s) remain.
Oct 13 20:03:27 walidus-laptop kernel: [24709.539417] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Oct 13 20:04:23 walidus-laptop nullmailer[3564]: Rescanning queue.
Oct 13 20:04:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1254894049.9813
Oct 13 20:04:23 walidus-laptop nullmailer[27195]: smtp: Failed: Connect failed
Oct 13 20:04:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:04:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241009.8431
Oct 13 20:04:23 walidus-laptop nullmailer[27196]: smtp: Failed: Connect failed
Oct 13 20:04:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:04:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241021.8707
Oct 13 20:04:23 walidus-laptop nullmailer[27197]: smtp: Failed: Connect failed
Oct 13 20:04:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:04:23 walidus-laptop nullmailer[3564]: Delivery complete, 3 message(s) remain.
Oct 13 20:05:01 walidus-laptop /USR/SBIN/CRON[27216]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Oct 13 20:05:23 walidus-laptop nullmailer[3564]: Rescanning queue.
Oct 13 20:05:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1254894049.9813
Oct 13 20:05:23 walidus-laptop nullmailer[27260]: smtp: Failed: Connect failed
Oct 13 20:05:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:05:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241009.8431
Oct 13 20:05:23 walidus-laptop nullmailer[27261]: smtp: Failed: Connect failed
Oct 13 20:05:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:05:24 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241021.8707
Oct 13 20:05:24 walidus-laptop nullmailer[27262]: smtp: Failed: Connect failed
Oct 13 20:05:24 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:05:24 walidus-laptop nullmailer[3564]: Delivery complete, 3 message(s) remain.
Oct 13 20:06:17 walidus-laptop avahi-daemon[3959]: Invalid query packet.
Oct 13 20:06:18 walidus-laptop last message repeated 2 times
Oct 13 20:06:23 walidus-laptop nullmailer[3564]: Rescanning queue.
Oct 13 20:06:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1254894049.9813
Oct 13 20:06:23 walidus-laptop nullmailer[27266]: smtp: Failed: Connect failed
Oct 13 20:06:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:06:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241009.8431
Oct 13 20:06:23 walidus-laptop nullmailer[27267]: smtp: Failed: Connect failed
Oct 13 20:06:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:06:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241021.8707
Oct 13 20:06:23 walidus-laptop nullmailer[27268]: smtp: Failed: Connect failed
Oct 13 20:06:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:06:23 walidus-laptop nullmailer[3564]: Delivery complete, 3 message(s) remain.
Oct 13 20:07:23 walidus-laptop nullmailer[3564]: Rescanning queue.
Oct 13 20:07:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1254894049.9813
Oct 13 20:07:23 walidus-laptop nullmailer[27299]: smtp: Failed: Connect failed
Oct 13 20:07:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:07:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241009.8431
Oct 13 20:07:23 walidus-laptop nullmailer[27300]: smtp: Failed: Connect failed
Oct 13 20:07:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:07:23 walidus-laptop nullmailer[3564]: Starting delivery: protocol: smtp host: mail. file: 1255241021.8707
Oct 13 20:07:23 walidus-laptop nullmailer[27301]: smtp: Failed: Connect failed
Oct 13 20:07:23 walidus-laptop nullmailer[3564]: Sending failed:  Host not found
Oct 13 20:07:24 walidus-laptop nullmailer[3564]: Delivery complete, 3 message(s) remain.

==> /var/log/Xorg.0.log <==
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "pl"
(**) AT Translated Set 2 keyboard: xkb_layout: "pl"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device   USB Keyboard
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event6"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**)   USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**)   USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "pl"
(**)   USB Keyboard: xkb_layout: "pl"
(II) config/hal: Adding input device   USB Keyboard
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event7"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**)   USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**)   USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "pl"
(**)   USB Keyboard: xkb_layout: "pl"
(II) config/hal: Adding input device A4Tech PS/2+USB Mouse
(**) A4Tech PS/2+USB Mouse: always reports core events
(**) A4Tech PS/2+USB Mouse: Device: "/dev/input/event8"
(II) A4Tech PS/2+USB Mouse: Found 8 mouse buttons
(II) A4Tech PS/2+USB Mouse: Found x and y relative axes
(II) A4Tech PS/2+USB Mouse: Configuring as mouse
(**) A4Tech PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
(**) A4Tech PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "A4Tech PS/2+USB Mouse" (type: MOUSE)
(**) A4Tech PS/2+USB Mouse: (accel) keeping acceleration scheme 1
(**) A4Tech PS/2+USB Mouse: (accel) filter chain progression: 2.00
(**) A4Tech PS/2+USB Mouse: (accel) filter stage 0: 20.00 ms
(**) A4Tech PS/2+USB Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event9"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "pl"
(**) Video Bus: xkb_layout: "pl"
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.99.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event11"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+0+1024"
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II)   USB Keyboard: Device reopened after 1 attempts.
(II)   USB Keyboard: Device reopened after 1 attempts.
(II) A4Tech PS/2+USB Mouse: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.

==> /home/walidus/.xsession-errors <==
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
 * Stopping MythTV server: mythbackend 
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated  from sets import ImmutableSet
/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/changer.py:48: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  from popen2 import Popen3
 Czytanie list pakietów... 0%  Czytanie list pakietów... 100%  Czytanie list pakietów... Gotowe 
 Budowanie drzewa zale&#380;no&#347;ci... 0%  Budowanie drzewa zale&#380;no&#347;ci... 0%  Budowanie drzewa zale&#380;no&#347;ci... 50%  Budowanie drzewa zale&#380;no&#347;ci... 50%  Budowanie drzewa zale&#380;no&#347;ci        
 Odczyt informacji o stanie... 0%  Odczyt informacji o stanie... 0%  Odczyt informacji o stanie... Gotowe 

(mythbuntu-control-centre:24641): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(mythbuntu-control-centre:24641): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
 * Stopping MythTV server: mythbackend 
   ...done.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
kdeinit4: preparing to launch /usr/bin/knotify4
INFO     Nothing to save
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-10-13 19:03:47.095 Using runtime prefix = /usr
2009-10-13 19:03:47.186 XScreenSaver support enabled
2009-10-13 19:03:47.186 DPMS is active.
2009-10-13 19:03:47.187 Empty LocalHostName.
2009-10-13 19:03:47.187 Using localhost value of walidus-laptop
2009-10-13 19:03:47.195 New DB connection, total: 1
2009-10-13 19:03:47.201 Connected to database 'mythconverg' at host: localhost
2009-10-13 19:03:47.203 Closing DB connection named 'DBManager0'
2009-10-13 19:03:47.205 Total desktop dim: 1280x1824, over 2 screen[s].
2009-10-13 19:03:47.205 Screen 0 dim: 1280x1024.
2009-10-13 19:03:47.205 Screen 1 dim: 1280x800.
2009-10-13 19:03:47.205 Primary screen 0.
2009-10-13 19:03:47.205 Connected to database 'mythconverg' at host: localhost
2009-10-13 19:03:47.206 Using screen 0, 1280x1024 at 0,0
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
Uruchomione tvtime 1.0.2.
Czytanie konfiguracji z /etc/tvtime/tvtime.xml
Czytanie konfiguracji z /home/walidus/.tvtime/tvtime.xml
INFO     The content has been saved to /home/walidus/.rednotebook/data
INFO     The content has been saved to /home/walidus/.rednotebook/data
INFO     Nothing to save
INFO     Nothing to save
Dziekujemy za u&#380;ywanie tvtime.
INFO     Nothing to save
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-10-13 19:55:13.431 Using runtime prefix = /usr
2009-10-13 19:55:13.476 XScreenSaver support enabled
2009-10-13 19:55:13.477 DPMS is active.
2009-10-13 19:55:13.478 Empty LocalHostName.
2009-10-13 19:55:13.478 Using localhost value of walidus-laptop
2009-10-13 19:55:13.535 New DB connection, total: 1
2009-10-13 19:55:13.576 Connected to database 'mythconverg' at host: localhost
2009-10-13 19:55:13.662 Closing DB connection named 'DBManager0'
2009-10-13 19:55:13.668 Total desktop dim: 1280x1824, over 2 screen[s].
2009-10-13 19:55:13.668 Screen 0 dim: 1280x1024.
2009-10-13 19:55:13.668 Screen 1 dim: 1280x800.
2009-10-13 19:55:13.668 Primary screen 0.
2009-10-13 19:55:13.668 Connected to database 'mythconverg' at host: localhost
2009-10-13 19:55:13.669 Using screen 0, 1280x1024 at 0,0
INFO     Nothing to save
Bad UTF-8 in startup notification message
Bad UTF-8 in startup notification message
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-10-13 20:07:14.759 Using runtime prefix = /usr
2009-10-13 20:07:14.780 XScreenSaver support enabled
2009-10-13 20:07:14.780 DPMS is active.
2009-10-13 20:07:14.780 Empty LocalHostName.
2009-10-13 20:07:14.780 Using localhost value of walidus-laptop
2009-10-13 20:07:14.787 New DB connection, total: 1
2009-10-13 20:07:14.792 Connected to database 'mythconverg' at host: localhost
2009-10-13 20:07:14.806 Closing DB connection named 'DBManager0'
2009-10-13 20:07:14.807 Total desktop dim: 1280x1824, over 2 screen[s].
2009-10-13 20:07:14.807 Screen 0 dim: 1280x1024.
2009-10-13 20:07:14.807 Screen 1 dim: 1280x800.
2009-10-13 20:07:14.807 Primary screen 0.
2009-10-13 20:07:14.808 Connected to database 'mythconverg' at host: localhost
2009-10-13 20:07:14.809 Using screen 0, 1280x1024 at 0,0

==> lsb_release -a <==
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

==> df -h <==
System plików            rozm. u&#380;yte dost. %u&#380;. zamont. na
/dev/sda3              83G   72G   11G  88% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  420K 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  184K 1007M   1% /dev
tmpfs                1007M  3,5M 1003M   1% /dev/shm
lrm                  1007M  2,2M 1005M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda1             111M   26M   79M  25% /boot
/dev/sda6              30G   21G  8,6G  71% /home/walidus/DANE
//192.168.242.237/walidus
                      218G  192G   22G  90% /home/walidus/NONSZALANCJA_walidus
//192.168.242.237/walidus
                      218G  192G   22G  90% /home/walidus/NONSZALANCJA_walidus
//192.168.242.237/nonszalancja_MASX
                      466G  456G   11G  98% /home/walidus/MASX

==> uname -a <==
Linux walidus-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
06:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:09.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

==> lsusb <==
Bus 002 Device 002: ID 07ca:a827 AVerMedia Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 006 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a111 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/registry <==
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegistryDwords: ""

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 

==> /proc/driver/nvidia/warnings <==
Model:          GeForce 8600M GS
IRQ:            16
Video BIOS:      60.86.39.00.16
Card Type:      PCI-E
DMA Size:      40 bits
DMA Mask:      0xffffffffff
Bus Location:      01.00.0

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2012MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: [REMOVED]
          size: 1333MHz
          capacity: 1333MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600M GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8055 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 12
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=[REMOVED] latency=0 module=sky2 multicast=yes
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:06:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 9.1
                bus info: pci@0000:06:09.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:06:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 9.3
                bus info: pci@0000:06:09.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=57 maxlatency=4 mingnt=7 module=sdhci_pci
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by wiresquire on 2010-05-26
Just in case anyone is considering this card, the Avermedia proprietary driver currently does not support 10.04. Mine seems to be working OK most of the time, though I have had some crashes. Of course, as they don't officially support it, if there's a change in Ubuntu it could make the A827 driver not work, exactly the same as what happened with 8.04.

I can't understand why they have no support for either of the Ubuntu LT versions. They originally had support for 8.04 and then withdrew it, and now no 10.04. 

Lesson learned. Next time I'll be looking for a TV card with open source drivers....

ws

---

### Post by kecinzer on 2010-06-10
Hi.
I have Volar HX TV USB card (A827) succesfuly installed on Ubuntu 10.04, but I have problems with analog TV.
I using it to watch thru set-top-box (composite), but TVTime writes on terminal some errors.
I can turn on screen, but no sound. I tried some thinks, but nothink helps :(.
I already wrote on czech forums, but no reply.

---

### Post by wiresquire on 2010-07-14
I have not tried tvtime, but have been able to get analog to work with mplayer. I mainly use Me-Tv for DVB-T because it has easier recording and channel information, for analog, mplayer.

Once you have mplayer installed, the command to use is:
```

mplayer tv:// -vf pp=lb -tv driver=v4l2:device=/dev/video1:alsa:adevice=hw.1,0:amode=1:audiorate=48000:forceaudio:volume=100:immediatemode=0:normid=0:freq=209250:outfmt=YUY2

```

* obviously freq= is important to get right! That's the channel!
* normid is the video std, eg 0 is PAL-BG. Australia uses BG. 12 is NTSC (see audio-test.sh for complete list).
* tv-player.c shows VIDIOC_S_INPUT is 0 for Analog, 1 for Composite and 2 for S-Video. Mplayer also shows this as input. Should be able to select via tv://0, tv://1, tv://2 etc

I've also had success in the past with Composite/S-Video input and also with radio, though it seems mplayer is no longer compiled with radio support.

Good luck!
ws

---

