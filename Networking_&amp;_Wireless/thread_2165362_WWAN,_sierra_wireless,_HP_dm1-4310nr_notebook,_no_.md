---
title: "WWAN, sierra wireless, HP dm1-4310nr notebook, no device created"
date: 2013-08-04
forum: Networking &amp; Wireless
---

### Post by Vasu_Muppalla on 2013-08-04
[COLOR=#000000][FONT=sans-serif]The notebook has a WWAN module that shows itself in lsusb as -[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Sierra Wireless Inc, HP hs2434 Mobile Broadband Module[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]but no device is getting attached. No /dev/ttyUSB* files are created. I tried modprobe sierra and it loads also the usb_wwan module but no devices are created. A[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]lso tried the qcserial module and again, no devices are created.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]The SIM card[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif] is activated and works ( verified in a phone) and installed into the notebook correctly. pertinent syslog lines reveal-

[/FONT][/COLOR]Aug  4 12:14:24 localhost kernel: [ 1970.140185] usb 1-3: new high-speed USB device number 10 using ehci-pci
Aug  4 12:14:24 localhost kernel: [ 1970.255924] usb 1-3: config 1 has an invalid interface number: 5 but max is 1
Aug  4 12:14:24 localhost kernel: [ 1970.255935] usb 1-3: config 1 has an invalid interface number: 6 but max is 1
Aug  4 12:14:24 localhost kernel: [ 1970.255939] usb 1-3: config 1 has an invalid interface number: 6 but max is 1
Aug  4 12:14:24 localhost kernel: [ 1970.255944] usb 1-3: config 1 has no interface number 0
Aug  4 12:14:24 localhost kernel: [ 1970.255947] usb 1-3: config 1 has no interface number 1
Aug  4 12:14:24 localhost kernel: [ 1970.256944] usb 1-3: New USB device found, idVendor=03f0, idProduct=4b1d
Aug  4 12:14:24 localhost kernel: [ 1970.256950] usb 1-3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
Aug  4 12:14:24 localhost kernel: [ 1970.256955] usb 1-3: Product: HP hs2434 Mobile Broadband Module
Aug  4 12:14:24 localhost kernel: [ 1970.256960] usb 1-3: Manufacturer: Sierra Wireless Inc
Aug  4 12:14:24 localhost kernel: [ 1970.259986] cdc_mbim 1-3:1.5: cdc-wdm0: USB WDM device
Aug  4 12:14:24 localhost kernel: [ 1970.260338] cdc_mbim 1-3:1.5 wwan0: register 'cdc_mbim' at usb-0000:00:12.2-3, CDC MBIM, 7e:65:98:ad:a8:a9
Aug  4 12:14:24 localhost mtp-probe: checking bus 1, device 10: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3"
Aug  4 12:14:24 localhost mtp-probe: bus: 1, device: 10 was not an MTP device
Aug  4 12:14:24 localhost NetworkManager[961]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.5/net/wwan0, iface: wwan0)
Aug  4 12:14:24 localhost NetworkManager[961]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.5/net/wwan0, iface: wwan0): no ifupdown configuration found.

Doesn't look like usb modeswitch is happening for this device.

---

### Post by robmatic2 on 2013-08-06
> **Vasu_Muppalla said:**
> [COLOR=#000000][FONT=sans-serif]The notebook has a WWAN module that shows itself in lsusb as -[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Sierra Wireless Inc, HP hs2434 Mobile Broadband Module[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]but no device is getting attached. No /dev/ttyUSB* files are created. I tried modprobe sierra and it loads also the usb_wwan module but no devices are created. A[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]lso tried the qcserial module and again, no devices are created.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]The SIM card[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif] is activated and works ( verified in a phone) and installed into the notebook correctly. pertinent syslog lines reveal-
[/FONT][/COLOR]...
Doesn't look like usb modeswitch is happening for this device.

Hi,

I am in the same situation as you, and might maybe be in a position to help. I have some driver experience, but not in this area. I would be willing to spend some time on this if you think it could be something relatively simple that needs fixing. 

Also, did you have to do anything special to get the notebook sim to work in a phone? I've been trying everything, but I get no data. It seems to authenticate and connect just fine, the 4g icon lights up on my phone, but I get absolutely no data, not even a ping. I've verified the phone with another 4g sim and it works ok. And I know the notebook sim is good because I can boot up Win8 and use the wwan network just fine.

Thanks.

---

### Post by Vasu_Muppalla on 2013-08-07
> **robmatic2 said:**
> Hi,

I am in the same situation as you, and might maybe be in a position to help. I have some driver experience, but not in this area. I would be willing to spend some time on this if you think it could be something relatively simple that needs fixing. 

Also, did you have to do anything special to get the notebook sim to work in a phone? I've been trying everything, but I get no data. It seems to authenticate and connect just fine, the 4g icon lights up on my phone, but I get absolutely no data, not even a ping. I've verified the phone with another 4g sim and it works ok. And I know the notebook sim is good because I can boot up Win8 and use the wwan network just fine.

Thanks.

I didn't have to do anything special. I got the SIM # from the card, IMEI from the box it came in ( verified by opening the bottom and looking at the wwan module). Then I called tmobile customer service and activated over the phone. Put it in a tmobile branded smartphone and verified. It is possible that your phone doesn't have AWS band and that is probably what the SIM card connects with.

I would appreciate if you can get it working and post it here. Even getting the ttyUSB* devices created ( if modeswitch happens) would be great.

---

### Post by robmatic2 on 2013-08-18
I looked at a few drivers briefly. First, drivers/usb/serial/sierra.c, which looks like it could be the right one, since it appears to support other similar devices, such as "HP hs2300 a.k.a MC8775", which is a [COLOR=#333333][FONT=Arial]HSDPA/UMTS module. So I tried simply adding this to the usb_device_id table:
 [/FONT][/COLOR]        { USB_DEVICE(0x03F0, 0x4B1D) }, /* HP hs2434 */
And I actually get to:
  
[   21.562693] usb 1-3: Sierra USB modem converter now attached to ttyUSB0
[   21.574605] sierra 1-3:1.6: Sierra USB modem converter detected
  ...
[   26.570696] usb 1-3: Sierra USB modem converter now attached to ttyUSB1
[   26.570946] usbcore: registered new interface driver cdc_mbim
 ...
But then:
[   26.845366] sierra ttyUSB0: sierra_submit_rx_urbs: submit urb failed: -8
[   26.845446] sierra ttyUSB0: sierra_submit_rx_urbs: submit urb failed: -8
[   26.845508] sierra ttyUSB0: sierra_submit_rx_urbs: submit urb failed: -8
[   26.845569] sierra ttyUSB0: sierra_submit_rx_urbs: submit urb failed: -8
[   26.845630] sierra ttyUSB0: sierra_submit_rx_urbs: submit urb failed: -8
[   26.845691] sierra ttyUSB0: sierra_submit_rx_urbs: submit urb failed: -8
[   26.845811] sierra ttyUSB0: sierra_submit_rx_urbs: submit urb failed: -8
[   26.845875] sierra ttyUSB0: sierra_submit_rx_urbs: submit urb failed: -8

And a little while later...
[  245.576660] INFO: task modem-manager:894 blocked for more than 120 seconds.
[  245.576674] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  245.576681] modem-manager   D 0000000000000000     0   894      1 0x00000000
[  245.576694]  ffff8801e33179d8 0000000000000082 ffff8801e33179f8 ffffffff8107dd7b
[  245.576706]  ffff8801e9204530 ffff8801e3317fd8 ffff8801e3317fd8 ffff8801e3317fd8
[  245.576716]  ffff8801fdb72e20 ffff8801e9204530 ffff8801e9204530 ffff8801e2f21ea8
[  245.576725] Call Trace:
[  245.576745]  [<ffffffff8107dd7b>] ? pick_next_task_fair+0x6b/0x150
[  245.576756]  [<ffffffff8168dff9>] schedule+0x29/0x70
[  245.576765]  [<ffffffff8168e2de>] schedule_preempt_disabled+0xe/0x10
[  245.576776]  [<ffffffff8168c5d2>] __mutex_lock_slowpath+0x112/0x1b0
[  245.576786]  [<ffffffff8168c14a>] mutex_lock+0x2a/0x50
[  245.576820]  [<ffffffffa01229f4>] sierra_close+0x54/0x110 [sierra]
[  245.576833]  [<ffffffffa0122f55>] sierra_open+0x145/0x1a0 [sierra]
[  245.576850]  [<ffffffffa0112327>] serial_port_activate+0x77/0xa0 [usbserial]
[  245.576860]  [<ffffffff813e5e47>] ? tty_port_tty_set+0x67/0x80
[  245.576869]  [<ffffffff813e5eec>] tty_port_open+0x8c/0xd0
[  245.576878]  [<ffffffff813dc07e>] ? tty_init_dev+0xae/0x1d0
[  245.576892]  [<ffffffffa0112732>] serial_open+0x22/0x30 [usbserial]
[  245.576899]  [<ffffffff813dcae3>] tty_open+0x2a3/0x5c0
[  245.576910]  [<ffffffff8117cb2e>] chrdev_open+0x9e/0x190
[  245.576919]  [<ffffffff8117ca90>] ? cdev_put+0x30/0x30
[  245.576929]  [<ffffffff81175bd6>] do_dentry_open+0x226/0x2a0
[  245.576938]  [<ffffffff81175ea5>] finish_open+0x35/0x50
[  245.576947]  [<ffffffff81186cae>] do_last+0x72e/0xef0
[  245.576955]  [<ffffffff811837d8>] ? inode_permission+0x18/0x50
[  245.576963]  [<ffffffff8118387c>] ? link_path_walk+0x6c/0x8d0
[  245.576971]  [<ffffffff81187528>] path_openat+0xb8/0x4a0
[  245.576980]  [<ffffffff811880a2>] do_filp_open+0x42/0xa0
[  245.576989]  [<ffffffff81194265>] ? __alloc_fd+0x45/0x110
[  245.576997]  [<ffffffff8117723e>] do_sys_open+0xfe/0x1e0

So I'm not sure I'm on the right track here.

Another driver I looked at was drivers/net/usb/sierra_net.c, which looked interesting because of this
in the usb_device_id table:
        DIRECT_IP_DEVICE(0x1199, 0x68A3), /* Sierra Wireless USB-to-WWAN modem */

And "usb to wwan modem" sounds much closer to what we've got here, so I added this:

        DIRECT_IP_DEVICE(0x03F0, 0x4B1D), /* HP hs2434 USB-to-WWAN modem */

This gets me to here:
# ifconfig wwan0
wwan0     Link encap:Ethernet  HWaddr 5e:84:b2:XX:YY:XX  
          BROADCAST NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I think this is progress... but I'm not sure what to do next. Maybe figure out how to activate wwan0? Any ideas?

---

### Post by robmatic2 on 2013-08-18
Just noticed that sierra_net isn't even loaded at the moment, so I got that ifconfig wwan0 output without really doing anything. I suppose that you get the same thing?

---

### Post by bmork on 2013-08-19
> **Vasu_Muppalla said:**
> [COLOR=#000000][FONT=sans-serif]T[/FONT][/COLOR]Aug  4 12:14:24 localhost kernel: [ 1970.256955] usb 1-3: Product: HP hs2434 Mobile Broadband Module
Aug  4 12:14:24 localhost kernel: [ 1970.256960] usb 1-3: Manufacturer: Sierra Wireless Inc
Aug  4 12:14:24 localhost kernel: [ 1970.259986] cdc_mbim 1-3:1.5: cdc-wdm0: USB WDM device
Aug  4 12:14:24 localhost kernel: [ 1970.260338] cdc_mbim 1-3:1.5 wwan0: register 'cdc_mbim' at usb-0000:00:12.2-3, CDC MBIM, 


You already got the correct driver for this modem, so looking for other drivers is pointless.

Now, what you need is the userspace application able to configure and connect it.  MBIM is a pretty new protocol, primarily used by Windows8 at the momemt.  The good news is that there is already fully functional Linux support in the latest ModemManager.  The bad news is that this version isn't yet packaged for Ubuntu, and it includes a new interface which requires a new NetworkManager as well.

If you want to play with it now, then take a look at 
[http://www.freedesktop.org/wiki/Software/libmbim/](http://www.freedesktop.org/wiki/Software/libmbim/)
and [http://cgit.freedesktop.org/ModemManager/ModemManager/](http://cgit.freedesktop.org/ModemManager/ModemManager/)

Some skills are currently required... You need to build these libraries and applications yourself, and all available user interfaces are CLI.


Based on experience with Sierra MBIM devices so far (MC7710), it is also likely that the driver must work around one or more firmware problems on this device.  I'd really appreciate it if anyone is able to test it and report back to me. The behaviour to look out for is a connection which only works for very small packets at low rate.

---

### Post by robmatic2 on 2013-08-19
Thanks for the pointers. I will take a look. 

And user interfaces are CLI? Nothing could make me happier.

---

### Post by robmatic2 on 2013-08-19
OK, got libmbib built and installed. One problem immediately: In the mbim-network script, you've got "source xxxx" in functions load_profile() and load_state(). I think that 'source' works in bash (and csh of course) but not in bourne shell or dash, which is linked to by my /bin/sh. So I changed those to ". xxx" which I think works in all shells derived from bourne.

That being said, I've got progress! "mbim-network /dev/cdc-wdm0 connect" reports that it activated the interface!

Then I ran dhclient wwan0, and that worked also. ifconfig wwan0 gives me:

wwan0     Link encap:Ethernet  HWaddr XX:YY... 
          inet addr:100.241.182.28  Bcast:100.241.182.31  Mask:255.255.255.252
          inet6 addr: fe80::d866:c5ff:fe84:fccb/64 Scope:Link
          UP BROADCAST RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:640 (640.0 B)  TX bytes:105775 (105.7 KB)

However, no data is getting through, and I got this on the console:

[66253.122095] WARNING: at drivers/usb/core/urb.c:327 usb_submit_urb+0x335/0x350()
[66253.122101] URB ffff8801e2ceb000 submitted while active
[66253.122106] Modules linked in: ums_realtek usb_storage parport_pc ppdev rfcomm bnep arc4 ath9k mac80211 ath9k_common snd_hda_codec_idt snd_hda_codec_hdmi radeon ath9k_hw snd_hda_intel snd_hda_codec cdc_mbim cdc_ncm usbnet cdc_wdm snd_hwdep usbserial ath snd_pcm ttm snd_seq_midi btusb snd_rawmidi joydev snd_seq_midi_event snd_seq nfsd bluetooth kvm_amd psmouse snd_timer hp_accel drm_kms_helper snd_seq_device lis3lv02d cfg80211 kvm snd drm k10temp soundcore serio_raw snd_page_alloc video microcode mac_hid i2c_piix4 input_polldev i2c_algo_bit wmi nfs_acl auth_rpcgss oid_registry nfs fscache lockd sunrpc lp parport r8169 [last unloaded: sierra]
[66253.122240] CPU: 0 PID: 0 Comm: swapper/0 Not tainted 3.10.7 #2
[66253.122247] Hardware name: Hewlett-Packard HP Pavilion dm1 Notebook PC/18D4, BIOS F.13 09/11/2012
[66253.122253]  ffffffff81a65aeb ffff880206c03bd8 ffffffff81688abb ffff880206c03c18
[66253.122265]  ffffffff81043b60 ffff880206c03c78 ffff8801fce9b200 ffff8801e2cebe40
[66253.122274]  ffff8801f9e66bc0 ffff8801fd856284 0000000000000000 ffff880206c03c78
[66253.122284] Call Trace:
[66253.122289]  <IRQ>  [<ffffffff81688abb>] dump_stack+0x19/0x1b
[66253.122312]  [<ffffffff81043b60>] warn_slowpath_common+0x70/0xa0
[66253.122322]  [<ffffffff81043c46>] warn_slowpath_fmt+0x46/0x50
[66253.122332]  [<ffffffff814bcb95>] usb_submit_urb+0x335/0x350
[66253.122346]  [<ffffffffa036680d>] wdm_int_callback+0x1fd/0x210 [cdc_wdm]
[66253.122355]  [<ffffffff814ba434>] usb_hcd_giveback_urb+0x64/0xe0
[66253.122366]  [<ffffffff814ccef6>] ehci_urb_done+0x76/0xb0
[66253.122375]  [<ffffffff814cfbfc>] qh_completions+0x35c/0x430
[66253.122385]  [<ffffffff814d1bc7>] ehci_work+0x197/0x900
[66253.122394]  [<ffffffff81072058>] ? __wake_up_common+0x58/0x90
[66253.122404]  [<ffffffff814d25e8>] ehci_irq+0x218/0x2b0
[66253.122414]  [<ffffffff810db201>] ? rcu_report_qs_rnp+0xc1/0x130
[66253.122422]  [<ffffffff814b985e>] usb_hcd_irq+0x2e/0x50
[66253.122432]  [<ffffffff810d4145>] handle_irq_event_percpu+0x55/0x210
[66253.122441]  [<ffffffff810d4342>] handle_irq_event+0x42/0x70
[66253.122451]  [<ffffffff810d7519>] handle_fasteoi_irq+0x59/0x100
[66253.122459]  [<ffffffff810041d2>] handle_irq+0x22/0x40
[66253.122469]  [<ffffffff81698ffa>] do_IRQ+0x5a/0xe0
[66253.122478]  [<ffffffff8168f4ea>] common_interrupt+0x6a/0x6a
[66253.122482]  <EOI>  [<ffffffff8106d4cf>] ? __hrtimer_start_range_ns+0x18f/0x440
[66253.122500]  [<ffffffff815346cb>] ? cpuidle_enter_state+0x5b/0xe0
[66253.122508]  [<ffffffff815346c7>] ? cpuidle_enter_state+0x57/0xe0
[66253.122517]  [<ffffffff81534810>] cpuidle_idle_call+0xc0/0x210
[66253.122527]  [<ffffffff8100ac3e>] arch_cpu_idle+0xe/0x30
[66253.122536]  [<ffffffff81094b7e>] cpu_startup_entry+0xce/0x290
[66253.122547]  [<ffffffff8166f1c7>] rest_init+0x77/0x80
[66253.122556]  [<ffffffff81cfee5b>] start_kernel+0x3d3/0x3e0
[66253.122564]  [<ffffffff81cfe888>] ? repair_env_string+0x5a/0x5a
[66253.122573]  [<ffffffff81cfe5a6>] x86_64_start_reservations+0x2a/0x2c
[66253.122581]  [<ffffffff81cfe68d>] x86_64_start_kernel+0xe5/0xec
[66253.122587] ---[ end trace 2872eb40b68e7379 ]---
[66255.801874] cdc_mbim 1-3:1.5: unknown notification 42 received: index 5 len 8
[66779.464738] cdc_mbim 1-3:1.5: unknown notification 42 received: index 5 len 8

Is this related to the f/w problem that you mention?

I am willing to help debug, and do have some 'skill', but I do need guidance as I have little experience in this area.

---

### Post by robmatic2 on 2013-08-19
More progress... I tried connecting again, and kept getting an error from dhclient, so I rebooted. Then when I connected again, dhclient worked, and I got data!

Very slow data, around 100 kbs, but now this is looking very promising. Please tell me more about the f/w issues and what needs to be done to get full speed.

---

### Post by robmatic2 on 2013-08-19
Is it the ZLP stuff? Or something else?

---

### Post by bmork on 2013-08-20
> **robmatic2 said:**
> OK, got libmbib built and installed. One problem immediately: In the mbim-network script, you've got "source xxxx" in functions load_profile() and load_state(). I think that 'source' works in bash (and csh of course) but not in bourne shell or dash, which is linked to by my /bin/sh. So I changed those to ". xxx" which I think works in all shells derived from bourne.

That being said, I've got progress! "mbim-network /dev/cdc-wdm0 connect" reports that it activated the interface!

Then I ran dhclient wwan0, and that worked also. ifconfig wwan0 gives me:

wwan0     Link encap:Ethernet  HWaddr XX:YY... 
          inet addr:100.241.182.28  Bcast:100.241.182.31  Mask:255.255.255.252
          inet6 addr: fe80::d866:c5ff:fe84:fccb/64 Scope:Link
          UP BROADCAST RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:640 (640.0 B)  TX bytes:105775 (105.7 KB)


Great!  Looking good so far.

> 
However, no data is getting through, and I got this on the console:

[66253.122095] WARNING: at drivers/usb/core/urb.c:327 usb_submit_urb+0x335/0x350()
[66253.122101] URB ffff8801e2ceb000 submitted while active
[66253.122106] Modules linked in: ums_realtek usb_storage parport_pc ppdev rfcomm bnep arc4 ath9k mac80211 ath9k_common snd_hda_codec_idt snd_hda_codec_hdmi radeon ath9k_hw snd_hda_intel snd_hda_codec cdc_mbim cdc_ncm usbnet cdc_wdm snd_hwdep usbserial ath snd_pcm ttm snd_seq_midi btusb snd_rawmidi joydev snd_seq_midi_event snd_seq nfsd bluetooth kvm_amd psmouse snd_timer hp_accel drm_kms_helper snd_seq_device lis3lv02d cfg80211 kvm snd drm k10temp soundcore serio_raw snd_page_alloc video microcode mac_hid i2c_piix4 input_polldev i2c_algo_bit wmi nfs_acl auth_rpcgss oid_registry nfs fscache lockd sunrpc lp parport r8169 [last unloaded: sierra]
[66253.122240] CPU: 0 PID: 0 Comm: swapper/0 Not tainted 3.10.7 #2
[66253.122247] Hardware name: Hewlett-Packard HP Pavilion dm1 Notebook PC/18D4, BIOS F.13 09/11/2012
[66253.122253]  ffffffff81a65aeb ffff880206c03bd8 ffffffff81688abb ffff880206c03c18
[66253.122265]  ffffffff81043b60 ffff880206c03c78 ffff8801fce9b200 ffff8801e2cebe40
[66253.122274]  ffff8801f9e66bc0 ffff8801fd856284 0000000000000000 ffff880206c03c78
[66253.122284] Call Trace:
[66253.122289]  <IRQ>  [<ffffffff81688abb>] dump_stack+0x19/0x1b
[66253.122312]  [<ffffffff81043b60>] warn_slowpath_common+0x70/0xa0
[66253.122322]  [<ffffffff81043c46>] warn_slowpath_fmt+0x46/0x50
[66253.122332]  [<ffffffff814bcb95>] usb_submit_urb+0x335/0x350
[66253.122346]  [<ffffffffa036680d>] wdm_int_callback+0x1fd/0x210 [cdc_wdm]
[66253.122355]  [<ffffffff814ba434>] usb_hcd_giveback_urb+0x64/0xe0
[66253.122366]  [<ffffffff814ccef6>] ehci_urb_done+0x76/0xb0
[66253.122375]  [<ffffffff814cfbfc>] qh_completions+0x35c/0x430
[66253.122385]  [<ffffffff814d1bc7>] ehci_work+0x197/0x900
[66253.122394]  [<ffffffff81072058>] ? __wake_up_common+0x58/0x90
[66253.122404]  [<ffffffff814d25e8>] ehci_irq+0x218/0x2b0
[66253.122414]  [<ffffffff810db201>] ? rcu_report_qs_rnp+0xc1/0x130
[66253.122422]  [<ffffffff814b985e>] usb_hcd_irq+0x2e/0x50
[66253.122432]  [<ffffffff810d4145>] handle_irq_event_percpu+0x55/0x210
[66253.122441]  [<ffffffff810d4342>] handle_irq_event+0x42/0x70
[66253.122451]  [<ffffffff810d7519>] handle_fasteoi_irq+0x59/0x100
[66253.122459]  [<ffffffff810041d2>] handle_irq+0x22/0x40
[66253.122469]  [<ffffffff81698ffa>] do_IRQ+0x5a/0xe0
[66253.122478]  [<ffffffff8168f4ea>] common_interrupt+0x6a/0x6a
[66253.122482]  <EOI>  [<ffffffff8106d4cf>] ? __hrtimer_start_range_ns+0x18f/0x440
[66253.122500]  [<ffffffff815346cb>] ? cpuidle_enter_state+0x5b/0xe0
[66253.122508]  [<ffffffff815346c7>] ? cpuidle_enter_state+0x57/0xe0
[66253.122517]  [<ffffffff81534810>] cpuidle_idle_call+0xc0/0x210
[66253.122527]  [<ffffffff8100ac3e>] arch_cpu_idle+0xe/0x30
[66253.122536]  [<ffffffff81094b7e>] cpu_startup_entry+0xce/0x290
[66253.122547]  [<ffffffff8166f1c7>] rest_init+0x77/0x80
[66253.122556]  [<ffffffff81cfee5b>] start_kernel+0x3d3/0x3e0
[66253.122564]  [<ffffffff81cfe888>] ? repair_env_string+0x5a/0x5a
[66253.122573]  [<ffffffff81cfe5a6>] x86_64_start_reservations+0x2a/0x2c
[66253.122581]  [<ffffffff81cfe68d>] x86_64_start_kernel+0xe5/0xec
[66253.122587] ---[ end trace 2872eb40b68e7379 ]---
[66255.801874] cdc_mbim 1-3:1.5: unknown notification 42 received: index 5 len 8
[66779.464738] cdc_mbim 1-3:1.5: unknown notification 42 received: index 5 len 8

Is this related to the f/w problem that you mention?

No, this is a brand new one :-)

I do not have an immediate explanation for the WARNING.  That's definitely a driver bug regardless of what trigged it.  Looks like the driver somehow resubmitted the interrupt URB before the previous one was finished.  I'll go look at the driver and try to figure out how that could happen.

However, I believe this does no real harm, so you can ignore the warning for now. Or does MBIM commands (e.g disconnect) fail after this warning?  

The two last lines are interesting. 42 is USB_CDC_NOTIFY_SPEED_CHANGE, which is an optional part of the MBIM spec. I haven't seen any MBIM device reporting it before, but it does look like we should add support to prevent that message.  Not that there is anything useful we can do with it.

The reason it is unsupported is that we reuse an pre-existing driver (cdc-wdm) for all handling everything related to the interrupt endpoint, and by ignoring optional MBIM notifications we could avoid adding any new hooks in that existing driver.  Well, that was obviously bound to come back andd bite :-)  Like it did now.

Hmm, thinking about this and looking at the above, I am pretty sure the two issues are related.  There is probably something buggy about how cdc-wdm handle unknown notifications.  Fixing that is priority #1. Fixing the "unknown notification" requires an API change, which will take some time to get into the kernel.

> 
I am willing to help debug, and do have some 'skill', but I do need guidance as I have little experience in this area.

You have already helped a lot, pointing out issues we definitely need to fix.

Luckily, I don't think any of those issues should prevent the device from working. So based on your description I do suspect the ZLP issue.  But pinging with default payload size (56 bytes) and interval (1 second) should still work in that case.  Does it?

Unfortunately, you have to build a patched driver to test a fix for the ZLP issue.  I guess I should come up with some nice way to test such changes without having to do that... Anyway, If you look at the driver at around line 400:

[http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/net/usb/cdc_mbim.c?id=HEAD#n400](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/net/usb/cdc_mbim.c?id=HEAD#n400)

you will see this entry for USB device 1199:68a2:
```

        /* Sierra Wireless MC7710 need ZLPs */
    { USB_DEVICE_AND_INTERFACE_INFO(0x1199, 0x68a2, USB_CLASS_COMM, USB_CDC_SUBCLASS_MBIM, USB_CDC_PROTO_NONE),
      .driver_info = (unsigned long)&cdc_mbim_info_zlp,
    },

```

You need to add a similar entry for your device ID, either right before or right after the MC7710 entry.

Note that you can rebuild just this driver for your running kernel if you install the matching kernel headers package and run something like

```

make -C /lib/modules/`uname -r`/build SUBDIRS=/your/modified/kernelsource/drivers/net/usb cdc_mbim.ko
```

For example:

```

bjorn@nemi:~$ make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/local/src/git/linux/drivers/net/usb cdc_mbim.ko
make: Entering directory `/usr/src/linux-headers-3.11.0-rc6+'
  CC [M]  /usr/local/src/git/linux/drivers/net/usb/cdc_mbim.o
  MODPOST 1 modules
  CC      /usr/local/src/git/linux/drivers/net/usb/cdc_mbim.mod.o
  LD [M]  /usr/local/src/git/linux/drivers/net/usb/cdc_mbim.ko
make: Leaving directory `/usr/src/linux-headers-3.11.0-rc6+'
```

You can then unload the default driver and temporaily load your modified version by doing
```

rmmod cdc_mbim
insmod /usr/local/src/git/linux/drivers/net/usb/cdc_mbim.ko
```

---

### Post by robmatic2 on 2013-08-20
[IMG]http://i.imgur.com/J5l7HSx.png[/IMG]

---

### Post by robmatic2 on 2013-08-20
Still seeing the "unknown notification 42" messages, but hard to care much about that in light of the speed I'm getting now with that ZLP mod. BTW posted that image via the mobile broadband connection, no problem.

---

### Post by robmatic2 on 2013-08-20
Bjorn,

Thanks so very much for your help! Where may I send a patch for this fix?

Rob

---

### Post by bmork on 2013-08-21
> **robmatic2 said:**
> Bjorn,

Thanks so very much for your help! Where may I send a patch for this fix?

Rob

That would be the netdev mailing list, with a CC to the linux-usb list.  Both lists are @vger.kernel.org

Please make it clear that this is intended for the "net" tree (i.e destined for v3.11), and that it should be applied to stable trees as well.  Do not use the normal Cc stable.  The net maintainer prefer to batch stable patches himself, and will include it in his queue as long as you make it clear.  A subject prefix like "[PATCH net,stable]" will do.


Note that I believe your test proves my initial assumption that the ZLP bug applies to (at least) all Sierra MBIM devices.  So I am probably going to follow up with a patch to change these entries to a vendor match for all 3(!) Sierra Wireless vendor IDs.

But I fear that it could in reality apply to all Qualcomm firmware based devices, which would make the exception list unmanagable.  In which case I am going to question whether we should apply this fix for all devices.  It has a theoretical performance impact for devices not needing it, but that's not going to be user measurable.  And our priority should be making devices work.  In the real world, that means dealing with firmware bugs even if the workaround can cause theoretical problems.

Thanks so much for your testing. Linux device support depend on users like you to get these things sorted out as early as possible.

---

### Post by robmatic2 on 2013-08-22
Glad I could help you out, especially as you have done much much more to help me. I'll get the patch sent out over the weekend when I get a free moment.

---

### Post by Vasu_Muppalla on 2013-08-30
OK, I made the change to cdc_mbim.c, built and deployed. Then I built/deployed libmbim-1.4 and using mbim-network, got the connection to work.

I notice two odd things -

1) sometimes the interface comes up as wwan0 but sometimes it comes up as a wierd named interface. But doing a dhclient on that interface also works.
2) After a certain time, the link appears to go down. ifconfig still shows the interface with IP and all but pinging to known public IPs doesn't work. Tmobile tech says they see nothing on their end.

Are you experiencing the same disconnection problem ? My data speeds are about the same as you posted using speedtest.

Also, since modemmanager is out of the loop, this interface cannot be managed by networkmanager, correct ?

---

### Post by robmatic2 on 2013-08-30
> **Vasu_Muppalla said:**
> 
1) sometimes the interface comes up as wwan0 but sometimes it comes up as a wierd named interface. But doing a dhclient on that interface also works.

I have never seen anything but wwan0 show up.

> 2) After a certain time, the link appears to go down. ifconfig still shows the interface with IP and all but pinging to known public IPs doesn't work. Tmobile tech says they see nothing on their end.

That is exactly the behavior I saw prior to applying the driver patch. So are you absolutely positively sure you're running the code you think you are? I got very reliable performance after the patch. When you say "after a certain time", what are you talking about? Minutes, hours, days? I never ran the connection for very long.

Also, I noticed there have been driver changes in general, so it may be worth trying an updated driver or kernel. I'm running 3.11.0-rc6+, which is extremely recent. ;)

BTW I also do dhclient -r before shutting down the connection.

> Also, since modemmanager is out of the loop, this interface cannot be managed by networkmanager, correct ?

Yeah, I just skipped modemmanager altogether, so it's not nearly as nice as the Win8 interface, but I'm happy to just have the data working.

I'll do more experiments next week, but right now I am not in reach of a T-mobile network.

---

### Post by Vasu_Muppalla on 2013-09-17
I see that your kernel patch is accepted in 3.11 release.

I was having too much grief with kubuntu on the GPT/EFI partition boot so I installed opensuse 12.3, and kernel 3.11 from stable. I also installed libmbim-1.4. Now I am getting the wwan0 device consistently. 

mbim-network /dev/cdc-wdm0 start
dhclient wwan0

gets me connected at decent hspa speeds but in about 30-40 minutes, the network doesn't do anything- even ping doesn't work. The network settings have not changed- ifconfig still shows same settings and resolv.conf is also unchanged.

If I disconnect and reconnect, I am back in business for another 30 minutes or so.

Perhaps its something in opensuse. Earlier I had also tried opensuse factory with identical results.

---

### Post by ubuforum2 on 2013-11-07
> **robmatic2 said:**
> 

Yeah, I just skipped modemmanager altogether, so it's not nearly as nice as the Win8 interface, but I'm happy to just have the data working.

I'll do more experiments next week, but right now I am not in reach of a T-mobile network.

Or, instead, ask Ubuntu to upgrade both ModemManager and NetworkManager to newer releases. ModemManager has supported MBIM devices out of the box since version 1.0.

---

### Post by bmork on 2013-11-08
> **ubuforum2 said:**
> Or, instead, ask Ubuntu to upgrade both ModemManager and NetworkManager to newer releases. ModemManager has supported MBIM devices out of the box since version 1.0.

They've been on to that for a while already:
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/1102343](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/1102343)

But please realise that this transition is all but trivial. The interface between MM and NM is completely replaced, and there are several new external library dependencies added.

---

