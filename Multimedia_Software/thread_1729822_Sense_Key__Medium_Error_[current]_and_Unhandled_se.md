---
title: "Sense Key : Medium Error [current] and Unhandled sense code"
date: 2011-04-15
forum: Multimedia Software
---

### Post by Max303 on 2011-04-15
:KSSOLUTION:KS: sudo hdparm -E 0 /dev/sr[01] :KS

System: Ubuntu 10.04 (fully patched upto april 15th with stable-only patches)

So since the command above fixes this completely, where should I report this as a bug (kernel/dvd driver/ubuntu)?:

I was getting a lot of errors like this (dmesg / /var/log/messages) while I KNEW that the disc was ok AND I tried multiple dvd drives and discs:

Apr 15 18:08:44 system kernel: [ 2931.568659] Info fld=0x3b0720
Apr 15 18:08:44 system kernel: [ 2931.568663] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
Apr 15 18:08:44 system kernel: [ 2931.568675] sr 5:0:0:0: [sr1] CDB: Read(10): 28 00 00 3b 07 20 00 00 02 00
Apr 15 18:09:38 system kernel: [ 2985.683634] sr 5:0:0:0: [sr1] Unhandled sense code
Apr 15 18:09:38 system kernel: [ 2985.683644] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:09:38 system kernel: [ 2985.683653] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
Apr 15 18:09:38 system kernel: [ 2985.683665] sr 5:0:0:0: [sr1] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:09:38 system kernel: [ 2985.683677] sr 5:0:0:0: [sr1] CDB: Read(10): 28 00 00 01 92 d0 00 00 02 00
Apr 15 18:10:27 system kernel: [ 3034.611969] sr 5:0:0:0: [sr1] Unhandled sense code
Apr 15 18:10:27 system kernel: [ 3034.611973] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:10:27 system kernel: [ 3034.611977] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current] 
Apr 15 18:10:27 system kernel: [ 3034.611982] sr 5:0:0:0: [sr1] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:10:27 system kernel: [ 3034.611987] sr 5:0:0:0: [sr1] CDB: Read(10): 28 00 00 01 92 d0 00 00 02 00
Apr 15 18:11:41 system kernel: [ 3109.268038] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:11:41 system kernel: [ 3109.268052] sr 5:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Apr 15 18:11:41 system kernel: [ 3109.268064] sr 5:0:0:0: [sr1] Add. Sense: Read of scrambled sector without authentication
Apr 15 18:11:41 system kernel: [ 3109.268081] sr 5:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
Apr 15 18:11:42 system kernel: [ 3109.383148] sr 5:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:11:42 system kernel: [ 3109.383162] sr 5:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Apr 15 18:11:42 system kernel: [ 3109.383174] sr 5:0:0:0: [sr1] Add. Sense: Read of scrambled sector without authentication
Apr 15 18:11:42 system kernel: [ 3109.383190] sr 5:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
Apr 15 18:13:07 system kernel: [ 3195.160525] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:13:07 system kernel: [ 3195.160533] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:13:07 system kernel: [ 3195.160543] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:13:07 system kernel: [ 3195.160554] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:13:07 system kernel: [ 3195.160566] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 38 00 00 40 00
Apr 15 18:13:35 system kernel: [ 3223.162654] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:13:35 system kernel: [ 3223.162662] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:13:35 system kernel: [ 3223.162672] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:13:35 system kernel: [ 3223.162683] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:13:35 system kernel: [ 3223.162695] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 78 00 00 40 00
Apr 15 18:13:35 system kernel: [ 3223.162731] __ratelimit: 22 callbacks suppressed
Apr 15 18:13:43 system kernel: [ 3230.789551] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:13:43 system kernel: [ 3230.789560] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:13:43 system kernel: [ 3230.789569] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:13:43 system kernel: [ 3230.789580] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:13:43 system kernel: [ 3230.789592] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:13:43 system kernel: [ 3230.789628] __ratelimit: 22 callbacks suppressed
Apr 15 18:14:01 system kernel: [ 3249.278911] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:14:01 system kernel: [ 3249.278920] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:14:01 system kernel: [ 3249.278929] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:14:01 system kernel: [ 3249.278940] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:14:01 system kernel: [ 3249.278952] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:14:18 system kernel: [ 3265.868242] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:14:18 system kernel: [ 3265.868250] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:14:18 system kernel: [ 3265.868260] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:14:18 system kernel: [ 3265.868271] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:14:18 system kernel: [ 3265.868284] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 08 00
Apr 15 18:14:24 system kernel: [ 3271.872595] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:14:24 system kernel: [ 3271.872604] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:14:24 system kernel: [ 3271.872614] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:14:24 system kernel: [ 3271.872625] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:14:24 system kernel: [ 3271.872637] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:14:44 system kernel: [ 3291.757262] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:14:44 system kernel: [ 3291.757270] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:14:44 system kernel: [ 3291.757280] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:14:44 system kernel: [ 3291.757292] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:14:44 system kernel: [ 3291.757304] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:15:00 system kernel: [ 3308.126609] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:15:00 system kernel: [ 3308.126618] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:15:00 system kernel: [ 3308.126628] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:15:00 system kernel: [ 3308.126639] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:15:00 system kernel: [ 3308.126651] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:15:24 system kernel: [ 3331.405388] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:15:24 system kernel: [ 3331.405397] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:15:24 system kernel: [ 3331.405407] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:15:24 system kernel: [ 3331.405418] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:15:24 system kernel: [ 3331.405430] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 08 be d0 00 00 02 00
Apr 15 18:15:42 system kernel: [ 3350.044419] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:15:42 system kernel: [ 3350.044427] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:15:42 system kernel: [ 3350.044436] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:15:42 system kernel: [ 3350.044447] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:15:42 system kernel: [ 3350.044459] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:16:03 system kernel: [ 3370.343395] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:16:03 system kernel: [ 3370.343403] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:16:03 system kernel: [ 3370.343413] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:16:03 system kernel: [ 3370.343425] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:16:03 system kernel: [ 3370.343438] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:16:21 system kernel: [ 3388.466762] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:16:21 system kernel: [ 3388.466770] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:16:21 system kernel: [ 3388.466780] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:16:21 system kernel: [ 3388.466791] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:16:21 system kernel: [ 3388.466803] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:16:41 system kernel: [ 3408.591140] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:16:41 system kernel: [ 3408.591148] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:16:41 system kernel: [ 3408.591158] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:16:41 system kernel: [ 3408.591169] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:16:41 system kernel: [ 3408.591181] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:16:58 system kernel: [ 3426.329926] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:16:58 system kernel: [ 3426.329934] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:16:58 system kernel: [ 3426.329944] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:16:58 system kernel: [ 3426.329955] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:16:58 system kernel: [ 3426.329967] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:17:15 system kernel: [ 3442.809028] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:17:15 system kernel: [ 3442.809036] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:17:15 system kernel: [ 3442.809046] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:17:15 system kernel: [ 3442.809057] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:17:15 system kernel: [ 3442.809070] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:17:34 system kernel: [ 3461.467601] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:17:34 system kernel: [ 3461.467609] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:17:34 system kernel: [ 3461.467619] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:17:34 system kernel: [ 3461.467630] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:17:34 system kernel: [ 3461.467642] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:17:51 system kernel: [ 3478.366465] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:17:51 system kernel: [ 3478.366473] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:17:51 system kernel: [ 3478.366483] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:17:51 system kernel: [ 3478.366494] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:17:51 system kernel: [ 3478.366507] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:18:14 system kernel: [ 3501.884709] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:18:14 system kernel: [ 3501.884718] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:18:14 system kernel: [ 3501.884727] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:18:14 system kernel: [ 3501.884739] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:18:14 system kernel: [ 3501.884751] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 16 3f b0 00 00 02 00
Apr 15 18:18:34 system kernel: [ 3521.857653] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:18:34 system kernel: [ 3521.857661] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:18:34 system kernel: [ 3521.857671] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:18:34 system kernel: [ 3521.857682] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:18:34 system kernel: [ 3521.857694] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:18:54 system kernel: [ 3541.741579] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:18:54 system kernel: [ 3541.741587] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:18:54 system kernel: [ 3541.741597] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:18:54 system kernel: [ 3541.741609] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:18:54 system kernel: [ 3541.741621] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:19:12 system kernel: [ 3560.330026] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:19:12 system kernel: [ 3560.330034] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:19:12 system kernel: [ 3560.330044] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:19:12 system kernel: [ 3560.330055] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:19:12 system kernel: [ 3560.330068] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:19:30 system kernel: [ 3577.648569] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:19:30 system kernel: [ 3577.648577] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:19:30 system kernel: [ 3577.648587] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:19:30 system kernel: [ 3577.648598] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:19:30 system kernel: [ 3577.648611] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:19:47 system kernel: [ 3595.077015] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:19:47 system kernel: [ 3595.077019] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:19:47 system kernel: [ 3595.077022] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:19:47 system kernel: [ 3595.077027] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:19:47 system kernel: [ 3595.077033] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:20:03 system kernel: [ 3610.415694] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:20:03 system kernel: [ 3610.415703] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:20:03 system kernel: [ 3610.415713] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:20:03 system kernel: [ 3610.415724] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:20:03 system kernel: [ 3610.415736] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:20:19 system kernel: [ 3626.954271] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:20:19 system kernel: [ 3626.954280] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:20:19 system kernel: [ 3626.954290] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:20:19 system kernel: [ 3626.954301] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:20:19 system kernel: [ 3626.954313] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 20 00 90 00 00 02 00
Apr 15 18:20:36 system kernel: [ 3643.762672] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:20:36 system kernel: [ 3643.762675] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:20:36 system kernel: [ 3643.762680] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:20:36 system kernel: [ 3643.762685] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:20:36 system kernel: [ 3643.762690] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:20:56 system kernel: [ 3663.810800] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:20:56 system kernel: [ 3663.810809] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:20:56 system kernel: [ 3663.810820] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:20:56 system kernel: [ 3663.810831] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:20:56 system kernel: [ 3663.810843] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:21:13 system kernel: [ 3681.199168] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:21:13 system kernel: [ 3681.199176] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:21:13 system kernel: [ 3681.199186] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:21:13 system kernel: [ 3681.199197] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:21:13 system kernel: [ 3681.199209] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:21:30 system kernel: [ 3698.127512] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:21:30 system kernel: [ 3698.127521] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:21:30 system kernel: [ 3698.127531] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:21:30 system kernel: [ 3698.127543] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:21:30 system kernel: [ 3698.127555] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:21:53 system kernel: [ 3721.103841] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:21:53 system kernel: [ 3721.103850] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:21:53 system kernel: [ 3721.103859] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:21:53 system kernel: [ 3721.103870] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:21:53 system kernel: [ 3721.103882] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 27 5e 60 00 00 02 00
Apr 15 18:22:12 system kernel: [ 3739.833330] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:22:12 system kernel: [ 3739.833338] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:22:12 system kernel: [ 3739.833348] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:22:12 system kernel: [ 3739.833359] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:22:12 system kernel: [ 3739.833371] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:22:32 system kernel: [ 3759.731291] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:22:32 system kernel: [ 3759.731300] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:22:32 system kernel: [ 3759.731309] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:22:32 system kernel: [ 3759.731321] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:22:32 system kernel: [ 3759.731333] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:22:51 system kernel: [ 3778.409323] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:22:51 system kernel: [ 3778.409331] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:22:51 system kernel: [ 3778.409341] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:22:51 system kernel: [ 3778.409352] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:22:51 system kernel: [ 3778.409364] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00
Apr 15 18:23:11 system kernel: [ 3798.681814] sr 0:0:0:0: [sr0] Unhandled sense code
Apr 15 18:23:11 system kernel: [ 3798.681822] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 18:23:11 system kernel: [ 3798.681833] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 15 18:23:11 system kernel: [ 3798.681844] sr 0:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Apr 15 18:23:11 system kernel: [ 3798.681856] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 83 60 00 00 02 00

---

