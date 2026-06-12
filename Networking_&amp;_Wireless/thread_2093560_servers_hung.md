---
title: "servers hung"
date: 2012-12-11
forum: Networking &amp; Wireless
---

### Post by alterpub on 2012-12-11
I have server which hung every 2-5 days.
dmesg show following situation:
```
kernel: [490894.231753] INFO: task munin-html:10187 blocked for more than 120 seconds.
kernel: [490894.231799] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
kernel: [490894.231843] munin-html    D 0000000000000000     0 10187   9796 0x00000000
kernel: [490894.231878]  ffff88063174b968 0000000000000082 ffff88063174b8d8 0000000000015b80
kernel: [490894.231930]  ffff88063174bfd8 0000000000015b80 ffff88063174bfd8 ffff88062fe644d0
kernel: [490894.231982]  0000000000015b80 0000000000015b80 ffff88063174bfd8 0000000000015b80
kernel: [490894.232033] Call Trace:
kernel: [490894.232059]  [<ffffffff8117fce0>] ? sync_buffer+0x0/0x50
kernel: [490894.232089]  [<ffffffff815a1f13>] io_schedule+0x73/0xc0
kernel: [490894.232115]  [<ffffffff8117fd25>] sync_buffer+0x45/0x50
kernel: [490894.232143]  [<ffffffff815a258f>] __wait_on_bit+0x5f/0x90
kernel: [490894.232170]  [<ffffffff8117fce0>] ? sync_buffer+0x0/0x50
kernel: [490894.232197]  [<ffffffff815a2638>] out_of_line_wait_on_bit+0x78/0x90
kernel: [490894.232227]  [<ffffffff81080250>] ? wake_bit_function+0x0/0x40
kernel: [490894.232255]  [<ffffffff8117fcd6>] __wait_on_buffer+0x26/0x30
kernel: [490894.232288]  [<ffffffffa00131be>] squashfs_read_data+0x1be/0x520 [squashfs]
kernel: [490894.232320]  [<ffffffff8114f0f1>] ? __mem_cgroup_try_charge+0x71/0x450
kernel: [490894.232350]  [<ffffffffa0013963>] squashfs_cache_get+0x1c3/0x320 [squashfs]
kernel: [490894.232381]  [<ffffffffa00136eb>] ? squashfs_copy_data+0x10b/0x130 [squashfs]
kernel: [490894.232426]  [<ffffffff815a3dbe>] ? _raw_spin_lock+0xe/0x20
kernel: [490894.232454]  [<ffffffffa0013b68>] ? squashfs_read_metadata+0x48/0xf0 [squashfs]
kernel: [490894.232499]  [<ffffffffa0013ae1>] squashfs_get_datablock+0x21/0x30 [squashfs]
kernel: [490894.232544]  [<ffffffffa0015026>] squashfs_readpage+0x436/0x4a0 [squashfs]
kernel: [490894.232575]  [<ffffffff8111a375>] ? __inc_zone_page_state+0x35/0x40
kernel: [490894.232606]  [<ffffffff8110d072>] __do_page_cache_readahead+0x172/0x210
kernel: [490894.232636]  [<ffffffff8110d131>] ra_submit+0x21/0x30
kernel: [490894.232662]  [<ffffffff811045f3>] filemap_fault+0x3f3/0x450
kernel: [490894.232691]  [<ffffffff812bd156>] ? prio_tree_insert+0x256/0x2b0
kernel: [490894.232726]  [<ffffffffa009225d>] aufs_fault+0x11d/0x170 [aufs]
kernel: [490894.232755]  [<ffffffff8111f6d4>] __do_fault+0x54/0x560
kernel: [490894.232782]  [<ffffffff81122f39>] handle_mm_fault+0x1b9/0x440
kernel: [490894.232811]  [<ffffffff811286f5>] ? do_mmap_pgoff+0x335/0x380
kernel: [490894.232840]  [<ffffffff815a7af5>] do_page_fault+0x125/0x350
kernel: [490894.232867]  [<ffffffff815a4675>] page_fault+0x25/0x30
```

```
cat /etc/issue.net 
Ubuntu 10.04.2 LTS
```

```
uname -a
Linux Shard1Host3 2.6.35-32-server #68~lucid1-Ubuntu SMP Wed Mar 28 18:33:00 UTC 2012 x86_64 GNU/Linux
```

This system load via ltsp and hasn't harddrives also it has a lot of memory 24Gb.
```
free -m
             total       used       free     shared    buffers     cached
Mem:         24152      17090       7061          0         50        494
-/+ buffers/cache:      16545       7607
Swap:            0          0          0

```

I put vmstat info here but I think it won't give results after reboot
```
vmstat 1 30
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0 7231156  52196 506400    0    0     0     0  172  143  7  0 92  0
 1  0      0 7231024  52196 506400    0    0     0     0 7859 16233  5  0 94  0
 0  0      0 7231024  52196 506400    0    0     0     0 7870 16446  2  0 98  0
 0  0      0 7230900  52196 506400    0    0     0     0 7308 15661  5  0 95  0
 0  0      0 7231100  52196 506400    0    0     0     0 7960 16543  6  0 94  0
 0  0      0 7231100  52196 506400    0    0     0     0 7542 16047  5  1 94  0
 3  0      0 7231100  52196 506400    0    0     0     0 7709 16621  3  0 96  0
 0  0      0 7231220  52196 506400    0    0     0     0 7857 16552  4  0 96  0
 0  0      0 7231220  52196 506400    0    0     0     0 7192 15491  6  0 94  0
 0  0      0 7231220  52196 506400    0    0     0     0 7423 15792  5  1 94  0
 1  0      0 7231260  52196 506404    0    0     0     0 7686 16296  2  0 98  0
 0  0      0 7231260  52196 506404    0    0     0     0 6976 15183  5  0 95  0
 0  0      0 7231260  52196 506404    0    0     0     0 7303 15600  4  0 95  0
 0  0      0 7231320  52196 506404    0    0     0     0 7967 16241  1  0 98  0
 0  0      0 7231444  52196 506404    0    0     0     0 6948 15113  6  0 94  0
 0  0      0 7231444  52196 506404    0    0     0     0 7931 16181  6  0 94  0
 1  0      0 7231516  52196 506404    0    0     0     0 7715 15829  6  0 94  0
 0  0      0 7231516  52196 506404    0    0     0     0 7771 16036  2  0 97  0
 0  0      0 7231268  52196 506404    0    0     0     0 7782 16202  6  0 94  0
 1  0      0 7231212  52196 506404    0    0     0     0 7457 15622  4  0 96  0
 0  0      0 7231212  52196 506404    0    0     0     0 7573 16045  2  0 98  0
 2  0      0 7231216  52196 506404    0    0     0     0 7689 16076  6  0 94  0
 0  0      0 7231424  52196 506404    0    0     0     0 7429 15650  4  0 95  0
 3  0      0 7231424  52196 506404    0    0     0     0 7534 16168  3  0 97  0
 1  0      0 7230548  52196 506404    0    0     0     0 8559 15926  7  1 92  0
 0  0      0 7230672  52196 506404    0    0     0     0 7720 15905  2  0 98  0
 0  0      0 7230548  52196 506404    0    0     0     0 7677 16313  5  0 95  0
 1  0      0 7230676  52196 506404    0    0     0     0 7209 15432  5  0 95  0
 0  0      0 7230800  52196 506404    0    0     0     0 7522 15861  2  0 98  0
 0  0      0 7230552  52196 506404    0    0     0     0 7760 16661  5  0 95  0
```


In the munin(monitoring system) graphs I see(before server hung):
Disk(nbd0) IOs per device:
read: 289m but avg by week 2.09m

Disk(nbd0) throughput per device:
read: 4.73k but avg by week 108.76

Disk(nbd0) utilization per device:
100% but avg by week 1.2%

Eth0 traffic was low:
in/out only 2Mbps

Number of threads increased to 566 usually 392

Fork rate 1.08 but usually 2.82

VMStat(processes state)
Increased to 17.77(from 0 as far as I could see in the graph)

CPU usage
iowait 880.46% when usually 6.67%



It'll be great if somebody help me to understand what's up.

PS: I have checked dmesg on the machines with ltsp image and nfs server - they are good(without any records for current date).

---

### Post by alterpub on 2012-12-17
Solution:
1) change network card
2) change NFSv3 to NFSv4

Now, all is ok, I think that it was issue with network card.

---

