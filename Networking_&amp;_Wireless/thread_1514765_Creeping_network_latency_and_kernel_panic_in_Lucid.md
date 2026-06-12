---
title: "Creeping network latency and kernel panic in Lucid Lynx server"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by HonoredMule on 2010-06-21
After a recent upgrade for my gateway from Hardy Heron on old 32-bit hardware to Lucid Lynx on much newer AMD hardware (which was previously running OpenSolaris-based Nexenta elsewhere), I started having an occasional problem where internet latency would spike to 1-3 seconds.  Restarting networking fixes the issue, but I'm running several group and public services on this box and can't have it slowing down like that when I'm not around to notice.

----

The network card involved is the 100 megabit one included in the motherboard, which was previously working fine in Nexenta.  I don't know if the additional PCI GBit card that connects the network is affected (never thought to ping a local address; SSH remains snappy), but it was working fine installed in the old 32-bit gateway.  I'm using kernel 2.6.32-22-server, and have tried the previous version as well.

I can't find any actual problems anywhere--memory usage remains consistent and well under half of what's available, the number of open connections is not unusual or even high, bandwidth usage is low when the problem appears, all services continue functioning fine, and no hardware or other performance issues become evident...just slow browsing from inside the network (or on that machine using CLI tools) when it happens at random (so far around once every week or two).  Next time it happens, I'll try to determine if the issue is specific to communications not part of an already established TCP connection (by pinging local network addresses) or to the NIC handling internet traffic (which gets the public IP via DHCP from a modem/router that assigns it the DMZ).  But the NIC should be fine, having worked flawlessly before (and since restarting networking solves the issue).  Beyond that, I've no idea how to further debug.

I also had one kernel panic, and was surprised that the server edition does not reboot automatically by default (fixed now).  I haven't a single clue to follow with that either, though it reinforces my hunch that my network issue is in the networking stack itself.

I took snapshots of the screen output, which contains the following possibly-useful tidbits:
```

Call Trace:
 <IRQ>
 [<ffffffff81487260>] ? eth_type_trans+0x40/0x140
 ...
 ...
 ...                    nv_nic_irq_optimized ... [forcedeth]
 
 ...
 
RIP ... skb_over_panic ...
 RSP ...
[drm] noveau 0000:00:12.0: Setting dpms mode 0 on tmds encoder (output 1)
---[ end trace fe2f................
Kernel panic - not syncing: Fatal exception in interrupt
Pid: 0, comm: swapper Tainted: G       D  2.6.32-22-server #36-Ubuntu
```

Full screenshot available at [http://honoredsoft.com/kp.jpg]("http://honoredsoft.com/kp.jpg"), since it exceeds resolution restrictions for upload, yet is already a little hard to read.

Has anyone else encountered this issue?  What should I try next?  I've been unable to find any other reported cases like this, and have no idea what to try next.  I don't have any other networking cards to try, nor indeed any free PCI slots to put them anyway (the board has only two).

---

### Post by HonoredMule on 2010-06-21
More information:

lsmod:
```
Module                  Size  Used by
ipt_MASQUERADE          1863  2
xt_tcpudp               2667  21
xt_recent               8186  2
xt_state                1490  2
ipt_REJECT              2384  2
iptable_nat             5219  1
nf_nat                 19501  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      12980  5 iptable_nat,nf_nat
nf_conntrack           73934  5 ipt_MASQUERADE,xt_state,iptable_nat,nf_nat,nf_co                 nntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
iptable_mangle          3315  0
iptable_filter          2791  1
ip_tables              18358  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22429  7 ipt_MASQUERADE,xt_tcpudp,xt_recent,xt_state,ipt_                 REJECT,iptable_nat,ip_tables
fbcon                  39270  71
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0
vgastate                9857  1 vga16fb
arc4                    1473  2
nls_cp437               6351  3
cifs                  278532  4
nfsd                  304055  13
exportfs                4202  1 nfsd
nfs                   309988  0
lockd                  75015  2 nfsd,nfs
nfs_acl                 2709  2 nfsd,nfs
auth_rpcgss            44452  2 nfsd,nfs
sunrpc                228031  12 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
nouveau               515131  1
ath5k                 134108  0
mac80211              243309  1 ath5k
ath                    10345  1 ath5k
ttm                    60815  1 nouveau
drm_kms_helper         30710  1 nouveau
ppdev                   6375  0
amd64_edac_mod         20456  0
asus_atk0110           10033  0
cfg80211              152987  3 ath5k,mac80211,ath
led_class               3732  1 ath5k
parport_pc             29958  1
edac_core              45423  3 amd64_edac_mod
edac_mce_amd            9214  1 amd64_edac_mod
drm                   198226  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
k8temp                  3912  0
i2c_nforce2             6099  0
lp                      9336  0
parport                37160  3 ppdev,parport_pc,lp
usb_storage            49801  0
r8169                  39650  0
mii                     5237  1 r8169
forcedeth              55592  0
ahci                   37646  0
pata_amd               11962  3
```

Motherboard:
M2N-VM DVI

Full text of the kernel panic is NOT in /var/log/messages

It also appears to recur more frequently if repaired by restarting networking instead of the whole computer.  Today I had complete packet loss (as opposed to the usual 25% when problem occurs) a second time in the same day after restarting networking.  The LAN interface remained fully functional and ping-responsive, and the router in front of the gateway (as always) remains fully responsive.  Further research has revealed that the NIC on this motherboard is notoriously bad, so I guess I'm going to have to replace it...hopefully not having to go through the ordeal of a fresh install and configuration all over again for the dozens of services it runs.

---

