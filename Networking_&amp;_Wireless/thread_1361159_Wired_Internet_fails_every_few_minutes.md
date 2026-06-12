---
title: "Wired Internet fails every few minutes"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by llamaSniper on 2009-12-21
Alright, so I have Ubuntu 9.10 installed on my computer, and am connecting to the internet via DSL modem in my basement, which is connected to a router, which is in turn connected to a switch, which is then connected to my Ethernet card. The card is a Realtek RTL8111/8168B. Here is the output I get from running lshw -C network, which seems to be something I should do.

chris@chris-desktop:~$ sudo lshw -C network
 *-network
      description: Ethernet interface
      product: RTL8111/8168B PCI Express Gigabit Ethernet controller
      vendor: Realtek Semiconductor Co., Ltd.
      physical id: 0
      bus info: pci@0000:06:00.0
      logical name: eth0
      version: 02
      serial: 00:25:11:3c:67:f3
      size: 1GB/s
      capacity: 1GB/s
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress msix vpd bus_master cap_list rom
ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd
autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=r8168
driverversion=8.015.00-NAPI duplex=full ip=192.168.1.103 latency=0
link=yes multicast=yes port=twisted pair speed=1GB/s
      resources: irq:29 ioport:e800(size=256) memory:fdfff000-fdffffff
memory:faff0000-faffffff(prefetchable)
memory:fdfc0000-fdfdffff(prefetchable)

When the connection fails, I restart, and sometimes that works. However, that is only sometimes. The rest of the time, I change IPv6 in the network manager to 'automatic' and then it still won't work, but if I restart with it set that way, then turn IPv6 to 'ignore', then it will connect. I have tried that without restarting, and it doesn't work. The connection will work sometimes right off of startup though...on a Wednesday, when it's exactly 67.2 degrees F, I'm doing a handstand, and the computer is tilted 0.0003 degrees east.

---

### Post by hugmenot on 2009-12-21
What makes you certain it is the card in you computer? Could it be one of: Modem, router, switch, cables? Did you try to eliminate alternative explanations and try to isolate the fault?

That the problem remains after restart argues against the PC being the problem.

---

### Post by hugmenot on 2009-12-21
Also, why do you play around with IPv6 at all?

---

### Post by llamaSniper on 2009-12-21
Well, I took the cat5e cable from my desktop, and put it in my laptop, and it was fine.  The idea for messing with the IPv6 settings came from another forum that said that it could be an IPv6 problem, and to disable it, but I already had it disabled, so, in frustration, I enabled it, restarted, disabled it, and it worked. I don't really know why, but it did.

---

### Post by llamaSniper on 2009-12-21
Might not be important, but Ubuntu 9.10, 9.04, and Haiku alpha live cds did the same thing...and I upgraded to a new motherboard about 2 weeks ago.

---

### Post by hugmenot on 2009-12-22
Do you also have something like Windows on that box? Does it also fail?

Other than that, what does the kernel say when it fails ("dmesg" oin terminal).
Or, what does NetworkManager say (var/log/syslog).

---

### Post by llamaSniper on 2009-12-22
No Windows, I haven't used it on this computer before, and have no intention of doing so. Next time it fails I'll post dmesg. I'm guessing that should be sometime in the next few hours.

---

### Post by llamaSniper on 2009-12-23
heres what dmesg put out.


[162348.079143] r8168: eth0: link up
[162348.438050] r8168: eth0: link down
[162352.685370] r8168: eth0: link up
[162353.054803] r8168: eth0: link down
[162355.964442] r8168: eth0: link up
[162356.060720] r8168: eth0: link up
[162356.832626] r8168: eth0: link down
[162357.060722] r8168: eth0: link down
[162359.274564] r8168: eth0: link up
[162360.060727] r8168: eth0: link up
[162360.214574] r8168: eth0: link down
[162361.060723] r8168: eth0: link down
[162362.650747] r8168: eth0: link up
[162363.060723] r8168: eth0: link up
[162363.156084] r8168: eth0: link down
[162364.060725] r8168: eth0: link down
[162365.650862] r8168: eth0: link up
[162366.060720] r8168: eth0: link up
[162367.772840] r8168: eth0: link down
[162368.060727] r8168: eth0: link down
[162373.651178] r8168: eth0: link up
[162374.060723] r8168: eth0: link up
[162384.786889] r8168: eth0: link down
[162385.060721] r8168: eth0: link down
[162387.147317] r8168: eth0: link up
[162388.060740] r8168: eth0: link up
[162389.128816] r8168: eth0: link down
[162390.060718] r8168: eth0: link down
[162391.580283] r8168: eth0: link up
[162392.060722] r8168: eth0: link up
[162392.338757] r8168: eth0: link down
[162393.060722] r8168: eth0: link down
[162394.813780] r8168: eth0: link up
[162395.060729] r8168: eth0: link up
[162400.349179] r8168: eth0: link down
[162401.060719] r8168: eth0: link down
[162402.795091] r8168: eth0: link up
[162403.060726] r8168: eth0: link up
[162403.726819] r8168: eth0: link down
[162404.060723] r8168: eth0: link down
[162406.306629] r8168: eth0: link up
[162406.918411] r8168: eth0: link down
[162409.445980] r8168: eth0: link up
[162410.060730] r8168: eth0: link up
[162410.259370] r8168: eth0: link down
[162411.060721] r8168: eth0: link down
[162412.754448] r8168: eth0: link up
[162413.060731] r8168: eth0: link up
[162413.741819] r8168: eth0: link down
[162414.060728] r8168: eth0: link down
[162416.193911] r8168: eth0: link up
[162416.815496] r8168: eth0: link down
[162419.257500] r8168: eth0: link up
[162419.815801] r8168: eth0: link down
[162422.315043] r8168: eth0: link up
[162422.711294] r8168: eth0: link down
[162425.379674] r8168: eth0: link up
[162426.060721] r8168: eth0: link up
[162429.353896] r8168: eth0: link down
[162430.060736] r8168: eth0: link down
[162431.751734] r8168: eth0: link up
[162432.060734] r8168: eth0: link up
[162432.210086] r8168: eth0: link down
[162433.060725] r8168: eth0: link down
[162434.810842] r8168: eth0: link up
[162435.060226] r8168: eth0: link up
[162435.220872] r8168: eth0: link down
[162436.060723] r8168: eth0: link down
[162437.993842] r8168: eth0: link up
[162438.060721] r8168: eth0: link up
[162438.559192] r8168: eth0: link down
[162439.060722] r8168: eth0: link down
[162441.116354] r8168: eth0: link up
[162441.968288] r8168: eth0: link down
[162444.429819] r8168: eth0: link up
[162445.060228] r8168: eth0: link up
[162445.228012] r8168: eth0: link down
[162446.060718] r8168: eth0: link down
[162447.634400] r8168: eth0: link up
[162448.052749] r8168: eth0: link down
[162450.736903] r8168: eth0: link up
[162451.060721] r8168: eth0: link up
[162451.260066] r8168: eth0: link down
[162452.060722] r8168: eth0: link down
[162453.786552] r8168: eth0: link up
[162454.060719] r8168: eth0: link up
[162454.813273] r8168: eth0: link down
[162455.060728] r8168: eth0: link down
[162457.298880] r8168: eth0: link up
[162458.060730] r8168: eth0: link up
[162479.869103] r8168: eth0: link down
[162480.060732] r8168: eth0: link down
[162482.287345] r8168: eth0: link up
[162483.060734] r8168: eth0: link up
[162483.094763] r8168: eth0: link down
[162484.060722] r8168: eth0: link down
[162485.581869] r8168: eth0: link up
[162486.060716] r8168: eth0: link up
[162487.012197] r8168: eth0: link down
[162487.060726] r8168: eth0: link down
[162489.668935] r8168: eth0: link up
[162490.060749] r8168: eth0: link up
[162490.169721] r8168: eth0: link down
[162491.060720] r8168: eth0: link down
[162492.723551] r8168: eth0: link up
[162493.060731] r8168: eth0: link up
[162494.865401] r8168: eth0: link down
[162495.060723] r8168: eth0: link down
[162497.525320] r8168: eth0: link up
[162498.060726] r8168: eth0: link up
[162498.256140] r8168: eth0: link down
[162499.060728] r8168: eth0: link down
[162500.719883] r8168: eth0: link up
[162501.060732] r8168: eth0: link up
[162501.073021] r8168: eth0: link down
[162502.060733] r8168: eth0: link down
[162503.593552] r8168: eth0: link up
[162504.060219] r8168: eth0: link up
[162505.221041] r8168: eth0: link down
[162506.060721] r8168: eth0: link down
[162507.591702] r8168: eth0: link up
[162507.985518] r8168: eth0: link down
[162510.635279] r8168: eth0: link up
[162511.060730] r8168: eth0: link up
[162511.284547] r8168: eth0: link down
[162512.060727] r8168: eth0: link down
[162513.772800] r8168: eth0: link up
[162514.060739] r8168: eth0: link up
[162514.245552] r8168: eth0: link down
[162515.060722] r8168: eth0: link down
[162516.837445] r8168: eth0: link up
[162517.060739] r8168: eth0: link up
[162517.272060] r8168: eth0: link down
[162518.060724] r8168: eth0: link down
[162521.620225] r8168: eth0: link up
[162522.060223] r8168: eth0: link up
[162522.672622] r8168: eth0: link down
[162523.060733] r8168: eth0: link down
[162525.083626] r8168: eth0: link up
[162526.060723] r8168: eth0: link up
[162526.341109] r8168: eth0: link down
[162527.060727] r8168: eth0: link down
[162528.766925] r8168: eth0: link up
[162529.060724] r8168: eth0: link up
[162529.516977] r8168: eth0: link down
[162530.060721] r8168: eth0: link down
[162531.954418] r8168: eth0: link up
[162532.060717] r8168: eth0: link up
[162532.357443] r8168: eth0: link down
[162533.060740] r8168: eth0: link down
[162535.012996] r8168: eth0: link up
[162535.060725] r8168: eth0: link up
[162535.509728] r8168: eth0: link down
[162536.060722] r8168: eth0: link down
[162538.136542] r8168: eth0: link up
[162538.947637] r8168: eth0: link down
[162541.371109] r8168: eth0: link up
[162541.738316] r8168: eth0: link down
[162544.229776] r8168: eth0: link up
[162544.688826] r8168: eth0: link down
[162547.198411] r8168: eth0: link up
[162547.613151] r8168: eth0: link down
[162550.195984] r8168: eth0: link up
[162550.579394] r8168: eth0: link down
[162553.314545] r8168: eth0: link up
[162553.708098] r8168: eth0: link down
[162556.380749] r8168: eth0: link up
[162557.060735] r8168: eth0: link up
[162557.077874] r8168: eth0: link down
[162558.060717] r8168: eth0: link down
[162559.441708] r8168: eth0: link up
[162559.962881] r8168: eth0: link down
[162562.455320] r8168: eth0: link up
[162563.060720] r8168: eth0: link up
[162563.385064] r8168: eth0: link down
[162564.060718] r8168: eth0: link down
[162565.828768] r8168: eth0: link up
[162566.060737] r8168: eth0: link up
[162566.642170] r8168: eth0: link down
[162567.060750] r8168: eth0: link down
[162572.688150] r8168: eth0: link up
[162573.060716] r8168: eth0: link up
[162573.910544] r8168: eth0: link down
[162574.060715] r8168: eth0: link down
[162576.313308] r8168: eth0: link up
[162577.060724] r8168: eth0: link up
[162582.192390] r8168: eth0: link down
[162583.060739] r8168: eth0: link down
[162584.563626] r8168: eth0: link up
[162584.989699] r8168: eth0: link down
[162587.623748] r8168: eth0: link up
[162588.060715] r8168: eth0: link up
[162588.667902] r8168: eth0: link down
[162589.060731] r8168: eth0: link down
[162591.063869] r8168: eth0: link up
[162591.525521] r8168: eth0: link down
[162597.014099] r8168: eth0: link up
[162597.060723] r8168: eth0: link up
[162598.142601] r8168: eth0: link down
[162599.060733] r8168: eth0: link down
[162600.623191] r8168: eth0: link up
[162601.021187] r8168: eth0: link down
[162603.712951] r8168: eth0: link up
[162604.060718] r8168: eth0: link up
[162604.072805] r8168: eth0: link down
[162605.060730] r8168: eth0: link down
[162606.748433] r8168: eth0: link up
[162607.060716] r8168: eth0: link up
[162608.471969] r8168: eth0: link down
[162609.060723] r8168: eth0: link down
[162610.938570] r8168: eth0: link up
[162611.060716] r8168: eth0: link up
[162612.580121] r8168: eth0: link down
[162613.060216] r8168: eth0: link down
[162614.938734] r8168: eth0: link up
[162615.060717] r8168: eth0: link up
[162616.449696] r8168: eth0: link down
[162617.060725] r8168: eth0: link down
[162618.829941] r8168: eth0: link up
[162619.060713] r8168: eth0: link up
[162620.057108] r8168: eth0: link down
[162620.060731] r8168: eth0: link down
[162625.495196] r8168: eth0: link up
[162625.853608] r8168: eth0: link down
[162628.314266] r8168: eth0: link up
[162628.923572] r8168: eth0: link down
[162634.375554] r8168: eth0: link up
[162634.751536] r8168: eth0: link down
[162637.440656] r8168: eth0: link up
[162638.060726] r8168: eth0: link up
[162638.718140] r8168: eth0: link down
[162639.060714] r8168: eth0: link down
[162641.250806] r8168: eth0: link up
[162641.955883] r8168: eth0: link down
[162644.374879] r8168: eth0: link up
[162644.771555] r8168: eth0: link down
[162647.501043] r8168: eth0: link up
[162648.060721] r8168: eth0: link up
[163025.861815] r8168: eth0: link down
[163026.060747] r8168: eth0: link down
[163028.236726] r8168: eth0: link up
[163029.060725] r8168: eth0: link up
[163031.244099] r8168: eth0: link down
[163032.060723] r8168: eth0: link down
[163033.671938] r8168: eth0: link up
[163034.060717] r8168: eth0: link up
[163034.390103] r8168: eth0: link down
[163035.060733] r8168: eth0: link down
[163036.922062] r8168: eth0: link up
[163037.060441] r8168: eth0: link up
[163037.289664] r8168: eth0: link down
[163038.060731] r8168: eth0: link down
[163039.872165] r8168: eth0: link up
[163040.060715] r8168: eth0: link up
[163061.852055] r8168: eth0: link down
[163062.060724] r8168: eth0: link down
[163070.233343] r8168: eth0: link up
[163071.060723] r8168: eth0: link up
[163078.506180] r8168: eth0: link down
[163079.060720] r8168: eth0: link down
[163080.986176] r8168: eth0: link up
[163081.060723] r8168: eth0: link up
[163968.458168] r8168: eth0: link down
[163969.060716] r8168: eth0: link down
[163970.889907] r8168: eth0: link up
[163971.060723] r8168: eth0: link up
[163972.561080] r8168: eth0: link down
[163973.060744] r8168: eth0: link down
[163974.982432] r8168: eth0: link up
[163975.060724] r8168: eth0: link up
[163975.549782] r8168: eth0: link down
[163976.060748] r8168: eth0: link down
[163977.984121] r8168: eth0: link up
[163978.060228] r8168: eth0: link up
[163979.298764] r8168: eth0: link down
[163980.060722] r8168: eth0: link down
[163981.733742] r8168: eth0: link up
[163982.060721] r8168: eth0: link up
[163982.250763] r8168: eth0: link down
[163983.060724] r8168: eth0: link down
[163984.807820] r8168: eth0: link up
[163985.060725] r8168: eth0: link up
[163985.187029] r8168: eth0: link down
[163986.060714] r8168: eth0: link down
[163987.857919] r8168: eth0: link up
[163988.060728] r8168: eth0: link up
[163993.784534] usb 2-2: new high speed USB device using ehci_hcd and address 2
[163993.948747] usb 2-2: configuration #1 chosen from 1 choice
[163994.142933] Initializing USB Mass Storage driver...
[163994.143107] scsi8 : SCSI emulation for USB Mass Storage devices
[163994.143220] usbcore: registered new interface driver usb-storage
[163994.143223] USB Mass Storage support registered.
[163994.143511] usb-storage: device found at 2
[163994.143513] usb-storage: waiting for device to settle before scanning
[163999.163235] usb-storage: device scan complete
[163999.186018] scsi 8:0:0:0: CD-ROM            TSSTcorp CDDVDW SE-S084B  TS01 PQ: 0 ANSI: 0
[163999.282540] sr1: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[163999.282785] sr 8:0:0:0: Attached scsi CD-ROM sr1
[163999.282927] sr 8:0:0:0: Attached scsi generic sg2 type 5
[164044.428827] r8168: eth0: link down
[164045.060720] r8168: eth0: link down
[164046.860198] r8168: eth0: link up
[164047.060730] r8168: eth0: link up
[164047.619396] r8168: eth0: link down
[164048.060757] r8168: eth0: link down
[164050.017919] r8168: eth0: link up
[164050.060718] r8168: eth0: link up
[164063.173734] r8168: eth0: link down
[164064.060722] r8168: eth0: link down
[164065.626971] r8168: eth0: link up
[164066.060724] r8168: eth0: link up
[164066.172933] r8168: eth0: link down
[164067.060718] r8168: eth0: link down
[164068.629183] r8168: eth0: link up
[164069.060715] r8168: eth0: link up
[164070.026774] r8168: eth0: link down
[164070.060716] r8168: eth0: link down
[164072.486170] r8168: eth0: link up
[164073.060724] r8168: eth0: link up
[164074.536046] r8168: eth0: link down
[164075.060718] r8168: eth0: link down
[164076.986339] r8168: eth0: link up
[164077.060715] r8168: eth0: link up
[164079.666646] r8168: eth0: link down
[164080.060729] r8168: eth0: link down
[164082.231540] r8168: eth0: link up
[164083.060721] r8168: eth0: link up
[164084.112991] r8168: eth0: link down
[164085.060724] r8168: eth0: link down
[164086.486723] r8168: eth0: link up
[164086.981092] r8168: eth0: link down
[164089.486811] r8168: eth0: link up
[164090.060716] r8168: eth0: link up
[164094.958829] r8168: eth0: link down
[164095.060716] r8168: eth0: link down
[164097.377122] r8168: eth0: link up
[164098.060723] r8168: eth0: link up
[164102.042563] r8168: eth0: link down
[164102.060729] r8168: eth0: link down
[164104.607398] r8168: eth0: link up
[164105.060716] r8168: eth0: link up
[164105.424509] r8168: eth0: link down
[164106.060726] r8168: eth0: link down
[164107.862531] r8168: eth0: link up
[164108.060713] r8168: eth0: link up
[164108.308352] r8168: eth0: link down
[164109.060714] r8168: eth0: link down
[164110.862635] r8168: eth0: link up
[164111.060715] r8168: eth0: link up
[164111.886918] r8168: eth0: link down
[164112.060715] r8168: eth0: link down
[164114.362770] r8168: eth0: link up
[164114.920189] r8168: eth0: link down
[164117.482881] r8168: eth0: link up
[164118.060261] r8168: eth0: link up
[164134.375575] r8168: eth0: link down
[164135.060726] r8168: eth0: link down
[164136.738634] r8168: eth0: link up
[164137.060723] r8168: eth0: link up
[164137.348545] r8168: eth0: link down
[164138.060715] r8168: eth0: link down
[164139.753757] r8168: eth0: link up
[164140.060724] r8168: eth0: link up
[164140.195672] r8168: eth0: link down
[164141.060715] r8168: eth0: link down
[164142.754913] r8168: eth0: link up
[164143.060723] r8168: eth0: link up
[164148.621707] r8168: eth0: link down
[164149.060717] r8168: eth0: link down
[164150.990216] r8168: eth0: link up
[164151.060715] r8168: eth0: link up
[164152.179335] r8168: eth0: link down
[164153.060720] r8168: eth0: link down
[164154.659307] r8168: eth0: link up
[164155.060714] r8168: eth0: link up
[164197.809421] r8168: eth0: link down
[164198.060725] r8168: eth0: link down
[164200.346063] r8168: eth0: link up
[164200.999978] r8168: eth0: link down
[164203.412769] r8168: eth0: link up
[164204.060726] r8168: eth0: link up
[164205.949693] r8168: eth0: link down
[164206.060714] r8168: eth0: link down
[164208.426393] r8168: eth0: link up
[164209.060236] r8168: eth0: link up
[164209.677706] r8168: eth0: link down
[164210.060724] r8168: eth0: link down
[164213.842129] r8168: eth0: link up
[164214.060731] r8168: eth0: link up
[164214.905316] r8168: eth0: link down
[164215.060752] r8168: eth0: link down
[164217.369345] r8168: eth0: link up
[164218.060715] r8168: eth0: link up
[164219.847150] r8168: eth0: link down
[164220.060729] r8168: eth0: link down
[164222.271906] r8168: eth0: link up
[164223.060722] r8168: eth0: link up
[164224.691983] r8168: eth0: link down
[164225.060714] r8168: eth0: link down
[164227.117102] r8168: eth0: link up
[164228.060716] r8168: eth0: link up
[164234.040847] r8168: eth0: link down
[164234.060716] r8168: eth0: link down
[164236.492447] r8168: eth0: link up
[164237.060715] r8168: eth0: link up
[164237.577470] r8168: eth0: link down
[164238.060713] r8168: eth0: link down
[164239.992582] r8168: eth0: link up
[164240.060714] r8168: eth0: link up
[164248.035296] r8168: eth0: link down
[164248.060720] r8168: eth0: link down
[164250.494555] r8168: eth0: link up
[164251.060732] r8168: eth0: link up
[164251.451324] r8168: eth0: link down
[164252.060716] r8168: eth0: link down
[164254.048117] r8168: eth0: link up
[164254.060731] r8168: eth0: link up
[164254.610435] r8168: eth0: link down
[164255.060723] r8168: eth0: link down
[164257.238245] r8168: eth0: link up
[164258.060717] r8168: eth0: link up
[164258.225715] r8168: eth0: link down
[164259.060716] r8168: eth0: link down
[164260.618372] r8168: eth0: link up
[164261.033523] r8168: eth0: link down
[164263.619559] r8168: eth0: link up
[164264.060732] r8168: eth0: link up
[164266.282100] r8168: eth0: link down
[164267.060723] r8168: eth0: link down
[164268.744752] r8168: eth0: link up
[164269.060725] r8168: eth0: link up
[164294.551530] r8168: eth0: link down
[164295.060720] r8168: eth0: link down
[164296.995809] r8168: eth0: link up
[164297.060715] r8168: eth0: link up
[164305.321329] r8168: eth0: link down
[164306.060713] r8168: eth0: link down
[164307.746222] r8168: eth0: link up
[164308.060743] r8168: eth0: link up
[164308.121273] r8168: eth0: link down
[164309.060719] r8168: eth0: link down
[164310.745282] r8168: eth0: link up
[164311.060728] r8168: eth0: link up
[164312.043276] r8168: eth0: link down
[164312.060724] r8168: eth0: link down
[164314.496480] r8168: eth0: link up
[164315.060717] r8168: eth0: link up
[164315.577288] r8168: eth0: link down
[164316.060729] r8168: eth0: link down
[164318.056674] r8168: eth0: link up
[164318.060725] r8168: eth0: link up
[164318.411306] r8168: eth0: link down
[164319.060723] r8168: eth0: link down
[164320.902261] r8168: eth0: link up
[164321.060722] r8168: eth0: link up
[164321.381653] r8168: eth0: link down
[164322.060730] r8168: eth0: link down
[164323.870784] r8168: eth0: link up
[164324.060721] r8168: eth0: link up
[164324.265495] r8168: eth0: link down
[164325.060749] r8168: eth0: link down
[164326.871962] r8168: eth0: link up
[164327.060717] r8168: eth0: link up
[164330.394940] r8168: eth0: link down
[164331.060720] r8168: eth0: link down
[164332.992190] r8168: eth0: link up
[164333.060719] r8168: eth0: link up
[164333.375782] r8168: eth0: link down
[164334.060742] r8168: eth0: link down
[164336.117305] r8168: eth0: link up
[164336.498182] r8168: eth0: link down
[164339.121377] r8168: eth0: link up
[164340.026942] r8168: eth0: link down
[164342.497548] r8168: eth0: link up
[164343.036622] r8168: eth0: link down
[164345.496620] r8168: eth0: link up
[164345.888992] r8168: eth0: link down
[164348.498324] r8168: eth0: link up
[164348.922262] r8168: eth0: link down
[164355.123031] r8168: eth0: link up
[164356.060715] r8168: eth0: link up
[164358.501825] r8168: eth0: link down
[164359.060716] r8168: eth0: link down
[164360.933263] r8168: eth0: link up
[164361.060731] r8168: eth0: link up
[164361.453826] r8168: eth0: link down
[164362.060719] r8168: eth0: link down
[164363.997336] r8168: eth0: link up
[164364.060725] r8168: eth0: link up
[164364.990455] r8168: eth0: link down
[164365.060347] r8168: eth0: link down
[164367.373508] r8168: eth0: link up
[164368.060760] r8168: eth0: link up
[164368.215105] r8168: eth0: link down
[164369.060734] r8168: eth0: link down
[164370.742584] r8168: eth0: link up
[164371.060728] r8168: eth0: link up
[164371.219533] r8168: eth0: link down
[164372.060720] r8168: eth0: link down
[164373.868769] r8168: eth0: link up
[164374.060720] r8168: eth0: link up
[164374.580502] r8168: eth0: link down
[164375.060722] r8168: eth0: link down
[164376.998874] r8168: eth0: link up
[164377.060729] r8168: eth0: link up
[164377.529879] r8168: eth0: link down
[164378.060722] r8168: eth0: link down

---

### Post by lisati on 2009-12-23
> **hugmenot said:**
> What makes you certain it is the card in you computer? **Could it be one of: Modem, router, switch, cables?** Did you try to eliminate alternative explanations and try to isolate the fault?

That the problem remains after restart argues against the PC being the problem.

+1 I'm in a grumpy mood about my internet connection going up and down like a yo-yo as well...

<aside>In my home network there seems to be a connection with which router/modem I'm using. The new one, an ADSL2+ capable Thomson speedtouch, seems to need to be manually reconnected every few minutes, while the older D-link beast (plain old boring ADSL only, none of the 2+ stuff) seems to be working perfectly. I might have to get in touch with my ISP, which supplied both. Can't be bothered dealing with help-desks at the moment, let alone explaining that I use Ubuntu....</aside>

---

### Post by llamaSniper on 2009-12-23
[  945.803312] r8169: eth0: link up
[  946.435787] r8169: eth0: link down
[  948.913406] r8169: eth0: link up
[  968.525554] hda-intel: Too big adjustment 32
[  972.401678] hda-intel: Too big adjustment 32
[ 1005.922687] hda-intel: Too big adjustment 32
[ 1704.031290] r8169: eth0: link down
[ 1710.192296] r8169: eth0: link up
[ 1710.630016] r8169: eth0: link down

this is something new from dmesg...

---

### Post by hugmenot on 2009-12-24
This looks like the Link Detection from the NIC.
I would really suggest to thoroughly check the cabling.
Otherwise I&#8217;m out of ideas.

---

### Post by Iowan on 2009-12-24
> **llamaSniper said:**
> Might not be important, but Ubuntu 9.10, 9.04, and Haiku alpha live cds did the same thing...and I upgraded to a new motherboard about 2 weeks ago.Is NIC onboard, or add-in? (Has chipset changed between old/new)? I suspect a bug (since there have been several similar threads), but I haven't (yet) investigated.

---

### Post by llamaSniper on 2009-12-24
As of about 3 hours ago, I have determined that Windows XP has the same problem

---

### Post by Hanto on 2009-12-24
I suspect a bug (since there have been several similar threads), but I haven't (yet) investigated.

  [SIZE=4]And I suspect you're right Iowan, as I suffer the same problem on two different boxes in either 9.04 or 9.10 using network manager. Can re-initialize networking including wireless with ' sudo restart network-manager ' and get it all going again, but it doesn't answer why it happens to begin with.  Networking is 4.0 perfect in Vista and Win 7 on the same boxes, yes I dual boot on both. [/SIZE]

---

### Post by llamaSniper on 2009-12-25
Well, the networking thing (chipset?) is an onboard one, and I had recently gotten this motherboard, but had done a clean install on it.

---

