---
title: "Ubuntu 10.04 can NOT READ DVDs!"
date: 2010-09-22
forum: Multimedia Software
---

### Post by uprise on 2010-09-22
My Vaio has a standard DVD-RW which used to be working well under 10.04. After formatting my computer, i have having problems with DVDs (no problem with CDs)
Icannot see the DVD at all. No files, nothing...

---

### Post by sanderd17 on 2010-09-22
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Please read more than the "click here". You need to install the restricet formats first, but afterwards, you need to install libdvdread.

---

### Post by uprise on 2010-09-22
done it years ago!
man, i have been googling this all day!
it is not the vlc or sth, my problem is i cannot see in the media any folder, no files anywhere at all!

other than that, should i see it in hte fstab, what is the device name for dvd-w in the folder /dev?

---

### Post by cchhrriiss121212 on 2010-09-22
You should see any CD/DVD in /media.

---

### Post by uprise on 2010-09-26
The thing is, i can read cds. They came up on the desktop, but i have no folders in /media, never.

---

### Post by uprise on 2010-09-26
A usb flashdisk, or harddisk, I can see in /media.
But nothing for CDs and DVDs. If it is an archive DVD, I cannot read it.

---

### Post by Yellow Pasque on 2010-09-26
Put a DVD in the drive and wait a few seconds. Then check:
```
dmesg
cat ~/.xsession-errors
```
Also, can you post the relevant portion of:
```
sudo lshw -C disk
```

---

### Post by uprise on 2010-09-27
dmesg:
```
[ 3021.960827] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3021.960836] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3021.960845] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3021.960855] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3021.960864] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3021.960886] end_request: I/O error, dev sr0, sector 0
[ 3021.960896] __ratelimit: 9 callbacks suppressed
[ 3021.960902] Buffer I/O error on device sr0, logical block 0
[ 3049.468711] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3049.468720] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3049.468729] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3049.468739] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3049.468748] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3049.468770] end_request: I/O error, dev sr0, sector 0
[ 3049.468780] Buffer I/O error on device sr0, logical block 0
[ 3076.928452] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3076.928462] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3076.928471] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3076.928481] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3076.928491] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3076.928512] end_request: I/O error, dev sr0, sector 0
[ 3076.928523] Buffer I/O error on device sr0, logical block 0
[ 3104.361182] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3104.361192] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3104.361201] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3104.361212] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3104.361221] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3104.361270] end_request: I/O error, dev sr0, sector 0
[ 3104.361281] Buffer I/O error on device sr0, logical block 0
[ 3131.917213] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3131.917222] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3131.917247] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3131.917257] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3131.917266] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3131.917288] end_request: I/O error, dev sr0, sector 0
[ 3131.917299] Buffer I/O error on device sr0, logical block 0
[ 3145.636205] sr 5:0:0:0: [sr0] Device not ready
[ 3145.636214] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3145.636223] sr 5:0:0:0: [sr0] Sense Key : Not Ready [current] 
[ 3145.636234] sr 5:0:0:0: [sr0] Add. Sense: Medium not present
[ 3145.636245] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3145.636266] end_request: I/O error, dev sr0, sector 0
[ 3145.636276] Buffer I/O error on device sr0, logical block 0
[ 3145.764611] sr 5:0:0:0: [sr0] Device not ready
[ 3145.764621] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3145.764631] sr 5:0:0:0: [sr0] Sense Key : Not Ready [current] 
[ 3145.764641] sr 5:0:0:0: [sr0] Add. Sense: Medium not present
[ 3145.764653] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3145.764674] end_request: I/O error, dev sr0, sector 0
[ 3145.764685] Buffer I/O error on device sr0, logical block 0
[ 3145.849429] sr 5:0:0:0: [sr0] Device not ready
[ 3145.849434] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3145.849439] sr 5:0:0:0: [sr0] Sense Key : Not Ready [current] 
[ 3145.849443] sr 5:0:0:0: [sr0] Add. Sense: Medium not present
[ 3145.849448] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3145.849457] end_request: I/O error, dev sr0, sector 0
[ 3145.849464] Buffer I/O error on device sr0, logical block 0
[ 3259.515330] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3259.515338] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3259.515347] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3259.515358] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3259.515367] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3259.515388] end_request: I/O error, dev sr0, sector 0
[ 3259.515398] Buffer I/O error on device sr0, logical block 0
[ 3287.146460] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3287.146468] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3287.146473] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3287.146480] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3287.146486] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3287.146498] end_request: I/O error, dev sr0, sector 0
[ 3287.146507] Buffer I/O error on device sr0, logical block 0
[ 3315.166829] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3315.166834] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3315.166839] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3315.166844] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3315.166849] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3315.166860] end_request: I/O error, dev sr0, sector 0
[ 3315.166867] Buffer I/O error on device sr0, logical block 0
[ 3338.102816] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3338.102820] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3338.102824] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3338.102829] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3338.102832] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3338.102840] end_request: I/O error, dev sr0, sector 0
[ 3338.102845] Buffer I/O error on device sr0, logical block 0
[ 3362.017457] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3362.017462] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3362.017467] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3362.017472] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3362.017477] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3362.017491] end_request: I/O error, dev sr0, sector 0
[ 3362.017496] Buffer I/O error on device sr0, logical block 0
[ 3386.446846] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3386.446851] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3386.446856] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3386.446861] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3386.446866] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3386.446877] end_request: I/O error, dev sr0, sector 0
[ 3386.446882] Buffer I/O error on device sr0, logical block 0
[ 3409.298253] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3409.298262] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3409.298272] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3409.298282] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3409.298291] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3409.298313] end_request: I/O error, dev sr0, sector 0
[ 3409.298323] Buffer I/O error on device sr0, logical block 0
[ 3430.153348] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3430.153358] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3430.153367] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3430.153378] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3430.153388] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3430.153409] end_request: I/O error, dev sr0, sector 0
[ 3430.153421] Buffer I/O error on device sr0, logical block 0
[ 3451.204614] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3451.204619] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3451.204624] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3451.204630] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3451.204634] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3451.204643] end_request: I/O error, dev sr0, sector 0
[ 3451.204650] Buffer I/O error on device sr0, logical block 0
[ 3477.404207] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3477.404211] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3477.404215] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3477.404220] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3477.404223] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3477.404232] end_request: I/O error, dev sr0, sector 0
[ 3477.404237] Buffer I/O error on device sr0, logical block 0
[ 3480.430081] INFO: task vlc:2836 blocked for more than 120 seconds.
[ 3480.430084] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3480.430086] vlc           D ffff8800bc1c7aa8     0  2836      1 0x00000000
[ 3480.430090]  ffff88003db1dc18 0000000000000082 0000000000015bc0 0000000000015bc0
[ 3480.430095]  ffff880037c003c0 ffff88003db1dfd8 0000000000015bc0 ffff880037c00000
[ 3480.430098]  0000000000015bc0 ffff88003db1dfd8 0000000000015bc0 ffff880037c003c0
[ 3480.430102] Call Trace:
[ 3480.430111]  [<ffffffff81542d77>] __mutex_lock_slowpath+0xe7/0x170
[ 3480.430114]  [<ffffffff81542c6b>] mutex_lock+0x2b/0x50
[ 3480.430118]  [<ffffffff811744a0>] __blkdev_get+0x60/0x3d0
[ 3480.430121]  [<ffffffff81174830>] ? blkdev_open+0x0/0xc0
[ 3480.430123]  [<ffffffff81174820>] blkdev_get+0x10/0x20
[ 3480.430126]  [<ffffffff811748a1>] blkdev_open+0x71/0xc0
[ 3480.430130]  [<ffffffff81141cb3>] __dentry_open+0x113/0x370
[ 3480.430133]  [<ffffffff8125401f>] ? security_inode_permission+0x1f/0x30
[ 3480.430137]  [<ffffffff8114e04f>] ? inode_permission+0xaf/0xd0
[ 3480.430140]  [<ffffffff81142027>] nameidata_to_filp+0x57/0x70
[ 3480.430143]  [<ffffffff8115228a>] do_filp_open+0x2da/0xba0
[ 3480.430147]  [<ffffffff81058690>] ? finish_task_switch+0x50/0xe0
[ 3480.430151]  [<ffffffff8115de0a>] ? alloc_fd+0x10a/0x150
[ 3480.430154]  [<ffffffff81141a29>] do_sys_open+0x69/0x170
[ 3480.430156]  [<ffffffff81141b70>] sys_open+0x20/0x30
[ 3480.430160]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
[ 3504.932982] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3504.932991] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3504.933001] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3504.933011] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3504.933020] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 0e 00 00 02 00
[ 3504.933041] end_request: I/O error, dev sr0, sector 56
[ 3504.933052] Buffer I/O error on device sr0, logical block 7
[ 3533.135231] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3533.135241] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3533.135250] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3533.135260] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3533.135270] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3533.135293] end_request: I/O error, dev sr0, sector 0
[ 3533.135304] Buffer I/O error on device sr0, logical block 0
[ 3560.612634] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3560.612644] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3560.612653] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3560.612663] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3560.612673] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3560.612694] end_request: I/O error, dev sr0, sector 0
[ 3560.612704] Buffer I/O error on device sr0, logical block 0
[ 3588.492001] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3588.492012] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3588.492021] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3588.492031] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3588.492041] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3588.492062] end_request: I/O error, dev sr0, sector 0
[ 3588.492074] Buffer I/O error on device sr0, logical block 0
[ 3600.439137] INFO: task lshw:2845 blocked for more than 120 seconds.
[ 3600.439145] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3600.439152] lshw          D 0000000000000000     0  2845   2528 0x00000000
[ 3600.439163]  ffff88003af37c18 0000000000000086 0000000000015bc0 0000000000015bc0
[ 3600.439175]  ffff880088e883c0 ffff88003af37fd8 0000000000015bc0 ffff880088e88000
[ 3600.439184]  0000000000015bc0 ffff88003af37fd8 0000000000015bc0 ffff880088e883c0
[ 3600.439195] Call Trace:
[ 3600.439215]  [<ffffffff81542d77>] __mutex_lock_slowpath+0xe7/0x170
[ 3600.439224]  [<ffffffff81542c6b>] mutex_lock+0x2b/0x50
[ 3600.439234]  [<ffffffff811744a0>] __blkdev_get+0x60/0x3d0
[ 3600.439242]  [<ffffffff81174830>] ? blkdev_open+0x0/0xc0
[ 3600.439249]  [<ffffffff81174820>] blkdev_get+0x10/0x20
[ 3600.439256]  [<ffffffff811748a1>] blkdev_open+0x71/0xc0
[ 3600.439265]  [<ffffffff81141cb3>] __dentry_open+0x113/0x370
[ 3600.439276]  [<ffffffff8125401f>] ? security_inode_permission+0x1f/0x30
[ 3600.439285]  [<ffffffff8114e04f>] ? inode_permission+0xaf/0xd0
[ 3600.439293]  [<ffffffff81142027>] nameidata_to_filp+0x57/0x70
[ 3600.439301]  [<ffffffff8115228a>] do_filp_open+0x2da/0xba0
[ 3600.439308]  [<ffffffff81151de2>] ? user_path_at+0x62/0xa0
[ 3600.439318]  [<ffffffff8115f8e0>] ? mntput_no_expire+0x30/0x110
[ 3600.439326]  [<ffffffff8115de0a>] ? alloc_fd+0x10a/0x150
[ 3600.439334]  [<ffffffff81141a29>] do_sys_open+0x69/0x170
[ 3600.439342]  [<ffffffff81141b70>] sys_open+0x20/0x30
[ 3600.439352]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
[ 3616.347250] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3616.347256] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3616.347261] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3616.347266] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3616.347271] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3616.347283] end_request: I/O error, dev sr0, sector 0
[ 3616.347289] Buffer I/O error on device sr0, logical block 0
[ 3644.247035] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3644.247044] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3644.247054] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3644.247064] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3644.247073] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3644.247095] end_request: I/O error, dev sr0, sector 0
[ 3644.247105] Buffer I/O error on device sr0, logical block 0
[ 3671.753873] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3671.753883] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3671.753893] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3671.753903] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3671.753912] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3671.753934] end_request: I/O error, dev sr0, sector 0
[ 3671.753945] Buffer I/O error on device sr0, logical block 0
[ 3699.334142] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3699.334150] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3699.334159] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3699.334170] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3699.334179] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3699.334200] end_request: I/O error, dev sr0, sector 0
[ 3699.334210] Buffer I/O error on device sr0, logical block 0
[ 3727.136418] sr 5:0:0:0: [sr0] Unhandled sense code
[ 3727.136426] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3727.136435] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 3727.136445] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[ 3727.136454] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 3727.136475] end_request: I/O error, dev sr0, sector 0
[ 3727.136486] Buffer I/O error on device sr0, logical block 0

```


cat ~/.xsession-errors
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-jZ4X8U
GNOME_KEYRING_CONTROL=/tmp/keyring-jZ4X8U
GNOME_KEYRING_CONTROL=/tmp/keyring-jZ4X8U
SSH_AUTH_SOCK=/tmp/keyring-jZ4X8U/ssh

(polkit-gnome-authentication-agent-1:1559): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1559): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: adding killswitch idx 1 state 1
** Message: killswitch 1 is 1
** Message: killswitches state 1
** Message: killswitch 1 is 1
** Message: killswitches state 1

(gnome-power-manager:1560): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x1040eb0'

(gnome-settings-daemon:1536): GLib-GObject-WARNING **: IA__g_object_notify: object class `GkbdStatus' has no property named `name'
** (nm-applet:1571): DEBUG: old state indicates that this was not a disconnect 0
Starting gtk-window-decorator

** (gnome-screensaver:1602): WARNING **: screensaver already running in this session
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I/O warning : failed to load external entity "/home/saad/.compiz/session/1074b93f924723a3e6128556877112797900000014860026"
evolution-alarm-notify-Message: Setting timeout for 63197 1285632000 1285568803
evolution-alarm-notify-Message:  Tue Sep 28 03:00:00 2010

evolution-alarm-notify-Message:  Mon Sep 27 09:26:43 2010

VLC media player 1.0.6 Goldeneye
[0x15864b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x19e2378] pulse audio output: No. of Audio Channels: 2
[1794:1835:84362308:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[1794:1835:84362475:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[1794:1835:84362537:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[1794:1835:84362593:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[1794:1835:84362649:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[1794:1835:84362705:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[1794:1835:84362762:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
[1794:1835:84362824:ERROR:chrome/browser/sync/notifier/registration_manager.cc(127)] Registration failed with code: 12
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
** (update-notifier:1905): DEBUG: Skipping reboot required
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
[1794:1794:1791142571:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[1794:1794:1793522952:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[1794:1794:1800491780:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[1794:1794:1802611708:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[1794:1794:1823979028:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[1794:1794:1825163403:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[1794:1794:1827922630:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[1794:1794:1876107624:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[1794:1794:1878622112:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[1794:1794:1963970243:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[1794:1794:1966130159:ERROR:chrome/app/chrome_dll_main.cc(248)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(gnome-terminal:2526): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
** Message: RFKILL event: idx 1 type 2 op 2 soft 1 hard 0

** Message: updating killswitch status 1
** Message: killswitch 1 is 0
** Message: killswitches state 0
** Message: killswitch 1 is 0
** Message: killswitches state 0
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
libdvdread: Using libdvdcss version 1.2.10 for DVD access

```


One DVD gave this:
sudo lshw -C disk
```
 *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7560A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DS03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=**nodisc**

```
Checked with another dvd, the laptop kept spinning it, and 
"sudo lshw -C disk" just waited, gave nothing.

---

