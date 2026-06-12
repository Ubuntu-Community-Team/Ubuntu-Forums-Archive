---
title: "Connecting to WPA 1 network fails and blocks all further network access on machine"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by jebus_beler on 2011-10-16
Hi,

I just installed 11.10 on a macbook air following instructions on the wiki:

[https://help.ubuntu.com/community/MacBookAir4-2#preview](https://help.ubuntu.com/community/MacBookAir4-2#preview)

But am now having some very serious network problems that I do not believe are MBA related.  While the instructions above involve customizing the installation a lot I'm pretty sure I recall seeing similar problems on the live-usb insaller.  I'll try to run that later to check.

Namely when I try to access my WPA1 encrypted wireless the network manager fails but more seriously it messes up the whole system.

dmesg produces a series of:

wpa_supplicant:936: blocked for more than 120 seconds
...
irqbalance:1035 blocked for more than 120 seconds


What's more any program that has anything remotely to do with the network just hangs.  "ifconfig" at the terminal just blocks and not even control-c will bring back the terminal.

This is quite drastic because somehow "sudo" seems to also try to access the network (can anyone explain that to me?) so basically once this happens I can no longer sudo at all!

I'm not sure if this is a wireless driver issue or a networkmanager issue.  For reference I think the following modules are being used:

cfg80211, mac80211, brcmsmac

---

### Post by jebus_beler on 2011-10-16
Well I can confirm a few things:

- This exact same problem happens on a live-boot usb stick (11.10 amd 64 desktop with mac additions) so its not anything I've done on my install.
- The problem also occurred for an unencrypted network broadcast by router.

The problem seemed specific to my router which is a Freebox (v4 I think):

[www.free.fr](www.free.fr)

But very strangely the problem went away after rebooting the router.  That's in itself ok, routers often have problems connecting to a particular machine and might require a reboot.  But what's strange is how much this messed up my machine.  There is still probably a relevant bug hiding under this though I don't know if I can reproduce it.  If anyone has any ideas please let me know.

---

### Post by luk156 on 2011-11-25
i've the same problem, but i'm not at home and i can't know witch model is the router.
I use the pc over different wifi also encrypted without problem

---

### Post by jebus_beler on 2011-11-28
@luk156: did you get anywhere with this?  I can connect to many encrypted networks but with some others I get this problem.

I'd like to bump this post again because the problem has persisted but I'm not sure its a WPA1 problem but rather just seems to occur randomly on various encrypted networks.  

The wireless drivers I'm using are:

brcmsmac
mac80211
cfg80211

Some relevant log output is:

```

Nov 24 11:28:48 sliver kernel: [88782.761016] INFO: task NetworkManager:1073 blocked for more than 120 seconds.
Nov 24 11:28:48 sliver kernel: [88782.761026] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov 24 11:28:48 sliver kernel: [88782.761032] NetworkManager  D 0000000000000003     0  1073      1 0x00000000
Nov 24 11:28:48 sliver kernel: [88782.761043]  ffff8801687abcc8 0000000000000086 ffff8801687abd88 ffffffff81112dae
Nov 24 11:28:48 sliver kernel: [88782.761053]  ffff8801687abfd8 ffff8801687abfd8 ffff8801687abfd8 0000000000012a40
Nov 24 11:28:48 sliver kernel: [88782.761062]  ffff88014d8b0000 ffff880166355c80 ffff8801687abd08 ffffffff81a8c700
Nov 24 11:28:48 sliver kernel: [88782.761071] Call Trace:
Nov 24 11:28:48 sliver kernel: [88782.761086]  [<ffffffff81112dae>] ? __alloc_pages_nodemask+0x10e/0x7f0
Nov 24 11:28:48 sliver kernel: [88782.761100]  [<ffffffff815e8e27>] __mutex_lock_slowpath+0xd7/0x150
Nov 24 11:28:48 sliver kernel: [88782.761109]  [<ffffffff81186710>] ? mntput_no_expire+0x30/0xf0
Nov 24 11:28:48 sliver kernel: [88782.761121]  [<ffffffff815aaa10>] ? call_commit_handler+0x40/0x40
Nov 24 11:28:48 sliver kernel: [88782.761130]  [<ffffffff815e8a3a>] mutex_lock+0x2a/0x50
Nov 24 11:28:48 sliver kernel: [88782.761140]  [<ffffffff814e6e75>] rtnl_lock+0x15/0x20
Nov 24 11:28:48 sliver kernel: [88782.761149]  [<ffffffff815aa4b9>] wext_ioctl_dispatch+0x59/0xb0
Nov 24 11:28:48 sliver kernel: [88782.761156]  [<ffffffff815ab670>] ? iw_handler_get_private+0x60/0x60
Nov 24 11:28:48 sliver kernel: [88782.761165]  [<ffffffff815aabc6>] wext_handle_ioctl+0x46/0xa0
Nov 24 11:28:48 sliver kernel: [88782.761174]  [<ffffffff814db426>] dev_ioctl+0xe6/0x3b0
Nov 24 11:28:48 sliver kernel: [88782.761184]  [<ffffffff812b696c>] ? apparmor_file_alloc_security+0x2c/0x60
Nov 24 11:28:48 sliver kernel: [88782.761193]  [<ffffffff814c122a>] sock_ioctl+0x10a/0x2f0
Nov 24 11:28:48 sliver kernel: [88782.761201]  [<ffffffff8117939a>] do_vfs_ioctl+0x8a/0x340
Nov 24 11:28:48 sliver kernel: [88782.761208]  [<ffffffff811796e1>] sys_ioctl+0x91/0xa0
Nov 24 11:28:48 sliver kernel: [88782.761216]  [<ffffffff814c3480>] ? sys_socket+0x40/0x70
Nov 24 11:28:48 sliver kernel: [88782.761227]  [<ffffffff815f22c2>] system_call_fastpath+0x16/0x1b
Nov 24 11:28:48 sliver kernel: [88782.761236] INFO: task wpa_supplicant:1185 blocked for more than 120 seconds.
Nov 24 11:28:48 sliver kernel: [88782.761240] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov 24 11:28:48 sliver kernel: [88782.761245] wpa_supplicant  D 0000000000000001     0  1185      1 0x00000000
Nov 24 11:28:48 sliver kernel: [88782.761253]  ffff880167ad38f8 0000000000000082 0000000000000282 ffff880167ad3908
Nov 24 11:28:48 sliver kernel: [88782.761262]  ffff880167ad3fd8 ffff880167ad3fd8 ffff880167ad3fd8 0000000000012a40
Nov 24 11:28:48 sliver kernel: [88782.761271]  ffff880164028000 ffff880167abae40 ffff880167ad38d8 ffff880168f77160
Nov 24 11:28:48 sliver kernel: [88782.761279] Call Trace:
Nov 24 11:28:48 sliver kernel: [88782.761288]  [<ffffffff815e8e27>] __mutex_lock_slowpath+0xd7/0x150
Nov 24 11:28:48 sliver kernel: [88782.761327]  [<ffffffffa0196d3f>] ? nl80211_trigger_scan+0xff/0x500 [cfg80211]
Nov 24 11:28:48 sliver kernel: [88782.761337]  [<ffffffff815e8a3a>] mutex_lock+0x2a/0x50
Nov 24 11:28:48 sliver kernel: [88782.761361]  [<ffffffffa01e026e>] ieee80211_request_scan+0x2e/0x60 [mac80211]
Nov 24 11:28:48 sliver kernel: [88782.761387]  [<ffffffffa01ee7e9>] ieee80211_scan+0x69/0x90 [mac80211]
Nov 24 11:28:48 sliver kernel: [88782.761410]  [<ffffffffa0197081>] nl80211_trigger_scan+0x441/0x500 [cfg80211]
Nov 24 11:28:48 sliver kernel: [88782.761424]  [<ffffffff81503565>] genl_rcv_msg+0x1d5/0x250
Nov 24 11:28:48 sliver kernel: [88782.761431]  [<ffffffff81503390>] ? genl_rcv+0x40/0x40
Nov 24 11:28:48 sliver kernel: [88782.761438]  [<ffffffff81502e29>] netlink_rcv_skb+0xa9/0xd0
Nov 24 11:28:48 sliver kernel: [88782.761444]  [<ffffffff81503375>] genl_rcv+0x25/0x40
Nov 24 11:28:48 sliver kernel: [88782.761451]  [<ffffffff81502720>] netlink_unicast+0x2b0/0x300
Nov 24 11:28:48 sliver kernel: [88782.761459]  [<ffffffff814ce457>] ? memcpy_fromiovec+0x67/0xb0
Nov 24 11:28:48 sliver kernel: [88782.761466]  [<ffffffff81502a3a>] netlink_sendmsg+0x2ca/0x360
Nov 24 11:28:48 sliver kernel: [88782.761474]  [<ffffffff814c06ce>] sock_sendmsg+0x10e/0x130
Nov 24 11:28:48 sliver kernel: [88782.761482]  [<ffffffff814c053d>] ? sock_recvmsg+0x11d/0x140
Nov 24 11:28:48 sliver kernel: [88782.761491]  [<ffffffff810329b9>] ? default_spin_lock_flags+0x9/0x10
Nov 24 11:28:48 sliver kernel: [88782.761499]  [<ffffffff8105726e>] ? try_to_wake_up+0x18e/0x200
Nov 24 11:28:48 sliver kernel: [88782.761508]  [<ffffffff814c2f51>] ? move_addr_to_kernel+0x71/0x80
Nov 24 11:28:48 sliver kernel: [88782.761515]  [<ffffffff814ce756>] ? verify_iovec+0x56/0xd0
Nov 24 11:28:48 sliver kernel: [88782.761524]  [<ffffffff814c342e>] __sys_sendmsg+0x3ae/0x3c0
Nov 24 11:28:48 sliver kernel: [88782.761531]  [<ffffffff8117af54>] ? core_sys_select+0x344/0x370
Nov 24 11:28:48 sliver kernel: [88782.761541]  [<ffffffff81074432>] ? set_current_blocked+0x52/0x70
Nov 24 11:28:48 sliver kernel: [88782.761551]  [<ffffffff8100a6cb>] ? handle_signal+0xdb/0x1a0
Nov 24 11:28:48 sliver kernel: [88782.761561]  [<ffffffff81014194>] ? restore_user_xstate+0x54/0xa0
Nov 24 11:28:48 sliver kernel: [88782.761570]  [<ffffffff814c43c9>] sys_sendmsg+0x49/0x90


```

---

