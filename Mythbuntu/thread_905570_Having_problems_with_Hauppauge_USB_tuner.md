---
title: "Having problems with Hauppauge USB tuner"
date: 2008-08-30
forum: Mythbuntu
---

### Post by SteveGodfrey on 2008-08-30
The tuner I'm currently using is a USB-Nova-TD. It's a USB twin DVB-T tuner.

After a day or so of uptime my mythtv backup is unable to record TV. There are no errors to indicate why - that I can see. Rebooting the box fixes the problem for another day! I don't want to set it to reboot every night, that's a windows thing!

The PC doesn'g get put into hibernate or standby it simply sits there 24 hours a day doing Myth stuff.

As fat as Myth is concerned the programme is being recorded but the recording file isn't being created. Live TV is also broken under these conditions. I've attached the messages.log and myth-backend.log plus a lsusb. 

I'm looking for suggestions as to what else I can check. If I use a PCI tuner Myth works flawlessly for weeks so I'm assuming there's a problem with the USB tuner.

Please any ideas then let me know, it's driving me mad! Thakns

DMESG

[13782.205673] usb 5-4.2: new low speed USB device using ehci_hcd and address 8
[13782.312970] usb 5-4.2: configuration #1 chosen from 1 choice
[13782.320175] input: Microsoft Microsoft IntelliMouse® Explorer as /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4.2/5-4.2:1.0/input/input9
[13782.373529] input,hidraw4: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse® Explorer] on usb-0000:00:1d.7-4.2
[13790.389772] [fglrx] interrupt source 10000000 successfully disabled!
[13790.389780] [fglrx] enable ID = 0x00000000
[13790.389785] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000005
[13790.389808] [fglrx] interrupt source 20008000 successfully disabled!
[13790.389813] [fglrx] enable ID = 0x00000000
[13790.389817] [fglrx] Receive disable interrupt message with irqEnableMask:20008000;dwIRQEnableId: 00000004
[13796.279106] [fglrx] PCIe has already been initialized. Reinitializing ...
[13796.296652] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[13796.296659] [fglrx] Reserve Block - 1 offset =  0X7fff000 length = 0X1000
[13796.296666] [fglrx] Reserve Block - 2 offset =  0X7fbf000 length = 0X40000
[13796.386666] [fglrx] interrupt source 20008000 successfully enabled
[13796.386674] [fglrx] enable ID = 0x00000004
[13796.386688] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[13796.386781] [fglrx] interrupt source 10000000 successfully enabled
[13796.386787] [fglrx] enable ID = 0x00000005
[13796.386794] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[21959.659102] MT2266 I2C read failed
[24634.825049] MT2266 I2C read failed
[25965.114954] MT2266 I2C read failed
[26944.134745] dib0700: Unknown remote controller key :  3 20
The above message gets repeated about 100 times so I've snipped it
[30767.989653] usb 5-4.2: USB disconnect, address 8
[42257.876498] MT2266 I2C read failed
[72892.318455] MT2266 I2C read failed
[88213.797917] MT2266 I2C write failed
[96426.814636] MT2266 I2C read failed
[96431.239067] MT2266 I2C read failed
[96437.266514] MT2266 I2C read failed
[96443.241885] MT2266 I2C read failed
[96529.076282] MT2266 I2C read failed
[96563.572287] MT2266 I2C read failed
[96583.150968] MT2266 I2C read failed
[96590.705229] MT2266 I2C read failed


/var/log/messages.log

Aug 30 00:41:05 M kernel: [42257.876498] MT2266 I2C read failed
Aug 30 07:58:03 M fsr[12197]: no rw xfs file systems inmtab:/etc/mtab 
Aug 30 07:58:09 M syslogd 1.5.0#1ubuntu1: restart.
Aug 30 09:12:03 M kernel: [72892.318455] MT2266 I2C read failed
Aug 30 13:27:36 M kernel: [88213.797917] MT2266 I2C write failed
Aug 30 15:44:35 M kernel: [96426.814636] MT2266 I2C read failed
Aug 30 15:44:40 M kernel: [96431.239067] MT2266 I2C read failed
Aug 30 15:44:46 M kernel: [96437.266514] MT2266 I2C read failed
Aug 30 15:44:52 M kernel: [96443.241885] MT2266 I2C read failed
Aug 30 15:46:17 M kernel: [96529.076282] MT2266 I2C read failed
Aug 30 15:46:52 M kernel: [96563.572287] MT2266 I2C read failed
Aug 30 15:47:12 M kernel: [96583.150968] MT2266 I2C read failed
Aug 30 15:47:19 M kernel: [96590.705229] MT2266 I2C read failed

myth-backend.log
2008-08-30 07:59:41.624 Reschedule requested for id -1.
2008-08-30 07:59:41.965 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 08:02:44.536 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 08:02:47.651 Reschedule requested for id -1.
2008-08-30 08:02:47.991 Scheduled 89 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 08:06:02.770 Reschedule requested for id -1.
2008-08-30 08:06:03.102 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 08:11:04.209 Reschedule requested for id -1.
2008-08-30 08:11:04.544 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 08:16:40.626 Reschedule requested for id -1.
2008-08-30 08:16:40.955 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 08:17:44.582 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 08:21:10.429 Reschedule requested for id -1.
2008-08-30 08:21:10.763 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 08:22:59.629 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 08:22:59.635 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 08:26:08.623 Reschedule requested for id -1.
2008-08-30 08:26:08.958 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 08:30:01.867 Reschedule requested for id -1.
2008-08-30 08:30:02.285 Scheduled 89 items in 0.4 = 0.01 match + 0.40 place
2008-08-30 08:32:44.627 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 08:33:02.622 Reschedule requested for id -1.
2008-08-30 08:33:02.956 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 08:36:06.536 Reschedule requested for id -1.
2008-08-30 08:36:06.876 Scheduled 89 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 08:41:03.977 Reschedule requested for id -1.
2008-08-30 08:41:04.316 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 08:43:44.350 Reschedule requested for id -1.
2008-08-30 08:43:44.686 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 08:47:44.669 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 08:48:03.775 Reschedule requested for id -1.
2008-08-30 08:48:04.111 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 08:51:59.937 Reschedule requested for id -1.
2008-08-30 08:52:00.351 Scheduled 89 items in 0.4 = 0.08 match + 0.33 place
2008-08-30 08:53:04.637 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 08:53:04.643 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 08:56:09.706 Reschedule requested for id -1.
2008-08-30 08:56:10.049 Scheduled 89 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 08:58:30.056 Reschedule requested for id 0.
2008-08-30 08:58:30.384 Scheduled 89 items in 0.3 = 0.00 match + 0.33 place
2008-08-30 08:58:59.421 TVRec(1): ASK_RECORDING 1 29 0 0
2008-08-30 08:58:59.701 TVRec(3): ASK_RECORDING 3 29 0 0
2008-08-30 08:59:07.582 Reschedule requested for id -1.
2008-08-30 08:59:07.921 Scheduled 89 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 08:59:32.098 TVRec(1): Changing from None to RecordingOnly
2008-08-30 08:59:32.111 TVRec(1): HW Tuner: 1->1
2008-08-30 08:59:32.278 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-30 08:59:32.285 Started recording: What Happened to the Hindenburg? "Secrets of the Dead": channel 1012 on cardid 1, sourceid 1
2008-08-30 08:59:49.073 JobQueue: Commercial Flagging Starting for What Happened to the Hindenburg? "Secrets of the Dead" recorded from channel 1012 at Sat Aug 30 09:00:00 2008
2008-08-30 08:59:49.312 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-30 08:59:49.318 Empty LocalHostName.
2008-08-30 08:59:49.318 Using localhost value of M
2008-08-30 08:59:49.327 New DB connection, total: 1
2008-08-30 08:59:49.331 Connected to database 'mythconverg' at host: localhost
2008-08-30 08:59:49.333 Closing DB connection named 'DBManager0'
2008-08-30 08:59:49.335 Connected to database 'mythconverg' at host: localhost
2008-08-30 08:59:49.340 New DB connection, total: 2
2008-08-30 08:59:49.341 Connected to database 'mythconverg' at host: localhost
2008-08-30 08:59:49.360 Connecting to backend server: 172.16.0.10:6543 (try 1 of 5)
2008-08-30 08:59:49.363 Using protocol version 40
2008-08-30 08:59:49.363 MainServer::HandleAnnounce Monitor
2008-08-30 08:59:49.365 adding: M as a client (events: 0)
2008-08-30 08:59:49.366 MainServer::HandleAnnounce Monitor
2008-08-30 08:59:49.367 adding: M as a client (events: 1)
2008-08-30 09:00:31.642 AFD: Opened codec 0x8211330, id(MPEG2VIDEO) type(Video)
2008-08-30 09:00:31.646 AFD: codec MP3 has 2 channels
2008-08-30 09:00:31.647 AFD: Opened codec 0x8211920, id(MP3) type(Audio)
2008-08-30 09:00:31.647 AFD: Opened codec 0x8211f10, id(DVB_SUBTITLE) type(Subtitle)
2008-08-30 09:00:31.648 AFD: codec MP3 has 0 channels
2008-08-30 09:00:31.649 AFD: Opened codec 0x8212500, id(MP3) type(Audio)
2008-08-30 09:02:44.718 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-30 09:03:04.838 Reschedule requested for id -1.
2008-08-30 09:03:05.177 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 09:08:05.126 Reschedule requested for id -1.
2008-08-30 09:08:05.457 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 09:08:35.348 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:08:43.576 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:08:57.245 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:09:05.525 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:09:19.243 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:09:27.513 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:09:41.141 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:09:49.405 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:10:03.489 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:10:11.733 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:10:25.442 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:10:33.670 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:10:47.448 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:10:55.659 [mpeg2video @ 0xb7378b88]warning: first frame is no keyframe
2008-08-30 09:11:03.600 Reschedule requested for id -1.
2008-08-30 09:11:04.072 Scheduled 89 items in 0.5 = 0.02 match + 0.45 place
2008-08-30 09:13:22.896 [mpeg2video @ 0xb7378b88]ac-tex damaged at 42 11
2008-08-30 09:13:22.901 [mpeg2video @ 0xb7378b88]Warning MVs not available
2008-08-30 09:13:22.920 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 12
2008-08-30 09:13:22.920 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 13
2008-08-30 09:13:22.921 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 14
2008-08-30 09:13:22.922 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 15
2008-08-30 09:13:22.922 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 16
2008-08-30 09:13:22.923 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 17
2008-08-30 09:13:22.924 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 18
2008-08-30 09:13:22.924 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 19
2008-08-30 09:13:22.925 [mpeg2video @ 0xb7378b88]skipped MB in I frame at 1 20
2008-08-30 09:13:22.926 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 21
2008-08-30 09:13:22.926 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 22
2008-08-30 09:13:22.927 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 23
2008-08-30 09:13:22.928 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 24
2008-08-30 09:13:22.928 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 25
2008-08-30 09:13:22.929 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 26
2008-08-30 09:13:22.930 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 27
2008-08-30 09:13:22.931 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 28
2008-08-30 09:13:22.931 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 29
2008-08-30 09:13:22.932 [mpeg2video @ 0xb7378b88]ac-tex damaged at 1 30
2008-08-30 09:13:22.933 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 31
2008-08-30 09:13:22.934 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 32
2008-08-30 09:13:22.935 [mpeg2video @ 0xb7378b88]ac-tex damaged at 0 33
2008-08-30 09:13:22.936 [mpeg2video @ 0xb7378b88]invalid mb type in I Frame at 0 34
2008-08-30 09:13:22.936 [mpeg2video @ 0xb7378b88]invalid mb type in I Frame at 0 35
2008-08-30 09:13:22.937 [mpeg2video @ 0xb7378b88]Warning MVs not available
2008-08-30 09:14:54.136 [mpeg2video @ 0xb7378b88]ac-tex damaged at 14 32
2008-08-30 09:14:54.139 [mpeg2video @ 0xb7378b88]Warning MVs not available
2008-08-30 09:16:08.570 Reschedule requested for id -1.
2008-08-30 09:16:08.940 Scheduled 89 items in 0.4 = 0.01 match + 0.36 place
2008-08-30 09:16:22.670 MainServer::HandleAnnounce Monitor
2008-08-30 09:16:22.677 adding: M as a client (events: 0)
2008-08-30 09:16:28.125 MainServer::HandleAnnounce Monitor
2008-08-30 09:16:28.128 adding: M as a client (events: 0)
2008-08-30 09:16:28.563 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-30 09:16:28.600 Empty LocalHostName.
2008-08-30 09:16:28.608 Using localhost value of M
2008-08-30 09:16:28.640 New DB connection, total: 1
2008-08-30 09:16:28.671 Connected to database 'mythconverg' at host: localhost
2008-08-30 09:16:28.673 Closing DB connection named 'DBManager0'
2008-08-30 09:16:28.674 Connected to database 'mythconverg' at host: localhost
2008-08-30 09:16:28.676 New DB connection, total: 2
2008-08-30 09:16:28.678 Connected to database 'mythconverg' at host: localhost
2008-08-30 09:16:28.680 Current Schema Version: 1214
2008-08-30 09:16:28.889 AFD: Opened codec 0x82b0040, id(MPEG2VIDEO) type(Video)
2008-08-30 09:16:28.891 AFD: codec MP3 has 2 channels
2008-08-30 09:16:28.892 AFD: Opened codec 0x82b0630, id(MP3) type(Audio)
2008-08-30 09:16:28.892 AFD: Opened codec 0x82b0c20, id(DVB_SUBTITLE) type(Subtitle)
2008-08-30 09:16:28.893 AFD: codec MP3 has 0 channels
2008-08-30 09:16:28.894 AFD: Opened codec 0x82b1210, id(MP3) type(Audio)
2008-08-30 09:16:29.020 Preview: Grabbed preview '/media/500/tv/1012_20080830090000.mpg' 720x576@94s
2008-08-30 09:16:43.149 MainServer::HandleAnnounce Monitor
2008-08-30 09:16:43.154 adding: M as a client (events: 0)
2008-08-30 09:17:44.780 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-30 09:21:04.908 Reschedule requested for id -1.
2008-08-30 09:21:05.245 Scheduled 89 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 09:22:58.697 [mpeg2video @ 0xb7378b88]Warning MVs not available
2008-08-30 09:23:05.645 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 09:23:05.650 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 09:26:14.755 Reschedule requested for id -1.
2008-08-30 09:26:15.106 Scheduled 89 items in 0.3 = 0.01 match + 0.34 place
2008-08-30 09:31:05.917 Reschedule requested for id -1.
2008-08-30 09:31:06.283 Scheduled 89 items in 0.4 = 0.02 match + 0.34 place
2008-08-30 09:32:44.846 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-30 09:32:59.733 [mpeg2video @ 0xb7378b88]ac-tex damaged at 25 17
2008-08-30 09:32:59.739 [mpeg2video @ 0xb7378b88]Warning MVs not available
2008-08-30 09:36:07.114 Reschedule requested for id -1.
2008-08-30 09:36:07.457 Scheduled 89 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 09:38:00.590 [mpeg2video @ 0xb7378b88]ac-tex damaged at 34 7
2008-08-30 09:43:13.265 Reschedule requested for id -1.
2008-08-30 09:43:13.615 Scheduled 89 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 09:46:04.791 Reschedule requested for id -1.
2008-08-30 09:46:05.148 Scheduled 89 items in 0.4 = 0.01 match + 0.35 place
2008-08-30 09:47:44.914 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-30 09:48:01.777 [mpeg2video @ 0xb7378b88]ac-tex damaged at 28 33
2008-08-30 09:48:01.782 [mpeg2video @ 0xb7378b88]Warning MVs not available
2008-08-30 09:50:06.416 Reschedule requested for id -1.
2008-08-30 09:50:06.766 Scheduled 89 items in 0.3 = 0.01 match + 0.34 place
2008-08-30 09:52:50.463 Reschedule requested for id -1.
2008-08-30 09:52:50.828 Scheduled 89 items in 0.4 = 0.02 match + 0.34 place
2008-08-30 09:53:03.141 [mpeg2video @ 0xb7378b88]ac-tex damaged at 11 28
2008-08-30 09:53:03.146 [mpeg2video @ 0xb7378b88]Warning MVs not available
2008-08-30 09:53:11.653 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 09:53:11.699 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 10:01:05.804 Reschedule requested for id -1.
2008-08-30 10:01:06.167 Scheduled 89 items in 0.4 = 0.02 match + 0.34 place
2008-08-30 10:01:30.075 TVRec(1): Changing from RecordingOnly to None
2008-08-30 10:01:30.129 Finished recording What Happened to the Hindenburg? "Secrets of the Dead": channel 1012
2008-08-30 10:01:30.161 Reschedule requested for id 0.
2008-08-30 10:01:30.225 Finished recording What Happened to the Hindenburg? "Secrets of the Dead": channel 1012
2008-08-30 10:01:30.618 Scheduled 88 items in 0.5 = 0.01 match + 0.44 place
2008-08-30 10:01:30.659 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-30 10:01:30.720 Empty LocalHostName.
2008-08-30 10:01:30.724 Using localhost value of M
2008-08-30 10:01:30.756 New DB connection, total: 1
2008-08-30 10:01:30.761 Connected to database 'mythconverg' at host: localhost
2008-08-30 10:01:30.764 Closing DB connection named 'DBManager0'
2008-08-30 10:01:30.765 Connected to database 'mythconverg' at host: localhost
2008-08-30 10:01:30.767 New DB connection, total: 2
2008-08-30 10:01:30.768 Connected to database 'mythconverg' at host: localhost
2008-08-30 10:01:30.771 Current Schema Version: 1214
2008-08-30 10:01:33.358 AFD: Opened codec 0x82b0020, id(MPEG2VIDEO) type(Video)
2008-08-30 10:01:33.360 AFD: codec MP3 has 2 channels
2008-08-30 10:01:33.360 AFD: Opened codec 0x82b0610, id(MP3) type(Audio)
2008-08-30 10:01:33.361 AFD: Opened codec 0x82b0c00, id(DVB_SUBTITLE) type(Subtitle)
2008-08-30 10:01:33.362 AFD: codec MP3 has 0 channels
2008-08-30 10:01:33.362 AFD: Opened codec 0x82b11f0, id(MP3) type(Audio)
2008-08-30 10:01:33.541 Preview: Grabbed preview '/media/500/tv/1012_20080830090000.mpg' 720x576@94s
2008-08-30 10:01:50.424 [mpeg2video @ 0xb7378b88]ac-tex damaged at 43 6
2008-08-30 10:01:50.425 [mpeg2video @ 0xb7378b88]Warning MVs not available
2008-08-30 10:01:51.175 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-30 10:01:51.179 Empty LocalHostName.
2008-08-30 10:01:51.180 Using localhost value of M
2008-08-30 10:01:51.189 New DB connection, total: 1
2008-08-30 10:01:51.193 Connected to database 'mythconverg' at host: localhost
2008-08-30 10:01:51.195 Closing DB connection named 'DBManager0'
2008-08-30 10:01:51.196 Connected to database 'mythconverg' at host: localhost
2008-08-30 10:01:51.198 New DB connection, total: 2
2008-08-30 10:01:51.199 Connected to database 'mythconverg' at host: localhost
2008-08-30 10:01:51.202 Current Schema Version: 1214
2008-08-30 10:01:53.675 AFD: Opened codec 0x82b0020, id(MPEG2VIDEO) type(Video)
2008-08-30 10:01:53.677 AFD: codec MP3 has 2 channels
2008-08-30 10:01:53.677 AFD: Opened codec 0x82b0610, id(MP3) type(Audio)
2008-08-30 10:01:53.678 AFD: Opened codec 0x82b0c00, id(DVB_SUBTITLE) type(Subtitle)
2008-08-30 10:01:53.679 AFD: codec MP3 has 0 channels
2008-08-30 10:01:53.679 AFD: Opened codec 0x82b11f0, id(MP3) type(Audio)
2008-08-30 10:01:53.812 Preview: Grabbed preview '/media/500/tv/1012_20080830090000.mpg' 720x576@94s
2008-08-30 10:02:44.971 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 10:03:35.977 Reschedule requested for id -1.
2008-08-30 10:03:36.310 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 10:07:10.646 Reschedule requested for id -1.
2008-08-30 10:07:11.020 Scheduled 88 items in 0.4 = 0.01 match + 0.36 place
2008-08-30 10:11:04.175 Reschedule requested for id -1.
2008-08-30 10:11:04.509 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 10:17:45.022 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 10:18:15.795 Reschedule requested for id -1.
2008-08-30 10:18:16.132 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 10:23:11.701 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 10:23:11.705 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 10:23:36.402 Reschedule requested for id -1.
2008-08-30 10:23:36.734 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 10:29:53.509 Reschedule requested for id -1.
2008-08-30 10:29:53.881 Scheduled 88 items in 0.4 = 0.01 match + 0.36 place
2008-08-30 10:32:45.067 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 10:33:16.865 Reschedule requested for id -1.
2008-08-30 10:33:17.207 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 10:36:24.750 Reschedule requested for id -1.
2008-08-30 10:36:25.086 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 10:41:03.894 Reschedule requested for id -1.
2008-08-30 10:41:04.232 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 10:44:39.776 Reschedule requested for id -1.
2008-08-30 10:44:40.113 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 10:47:45.124 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 10:47:49.948 Reschedule requested for id -1.
2008-08-30 10:47:50.290 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 10:51:05.500 Reschedule requested for id -1.
2008-08-30 10:51:05.841 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 10:53:13.707 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 10:53:13.711 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 10:54:30.574 Reschedule requested for id -1.
2008-08-30 10:54:30.907 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 10:58:21.573 Reschedule requested for id -1.
2008-08-30 10:58:21.909 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 11:00:57.704 Reschedule requested for id -1.
2008-08-30 11:00:58.039 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 11:02:45.169 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 11:03:49.178 Reschedule requested for id -1.
2008-08-30 11:03:49.516 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 11:08:22.175 Reschedule requested for id -1.
2008-08-30 11:08:22.511 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 11:11:03.422 Reschedule requested for id -1.
2008-08-30 11:11:03.761 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 11:14:45.225 Reschedule requested for id -1.
2008-08-30 11:14:45.561 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 11:17:45.214 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 11:23:20.713 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 11:23:20.719 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 11:30:08.422 Reschedule requested for id -1.
2008-08-30 11:30:08.827 Scheduled 88 items in 0.4 = 0.08 match + 0.33 place
2008-08-30 11:32:45.258 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 11:33:24.827 Reschedule requested for id -1.
2008-08-30 11:33:25.162 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 11:36:04.544 Reschedule requested for id -1.
2008-08-30 11:36:04.886 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 11:46:14.542 Reschedule requested for id -1.
2008-08-30 11:46:14.873 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 11:47:45.340 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 11:53:05.488 Reschedule requested for id -1.
2008-08-30 11:53:05.824 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 11:53:20.721 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 11:53:20.726 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 11:56:09.916 Reschedule requested for id -1.
2008-08-30 11:56:10.251 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 12:00:58.992 Reschedule requested for id -1.
2008-08-30 12:00:59.337 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 12:02:45.381 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 12:03:37.585 Reschedule requested for id -1.
2008-08-30 12:03:37.922 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 12:08:31.091 Reschedule requested for id -1.
2008-08-30 12:08:31.443 Scheduled 88 items in 0.4 = 0.01 match + 0.34 place
2008-08-30 12:11:34.279 Reschedule requested for id -1.
2008-08-30 12:11:34.618 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 12:15:00.520 Reschedule requested for id -1.
2008-08-30 12:15:00.854 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 12:17:45.426 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 12:20:28.722 Reschedule requested for id -1.
2008-08-30 12:20:29.058 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 12:23:21.728 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 12:23:21.733 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 12:27:28.787 Reschedule requested for id -1.
2008-08-30 12:27:29.238 Scheduled 88 items in 0.4 = 0.12 match + 0.33 place
2008-08-30 12:29:58.962 Reschedule requested for id -1.
2008-08-30 12:29:59.294 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 12:32:29.433 Reschedule requested for id -1.
2008-08-30 12:32:29.843 Scheduled 88 items in 0.4 = 0.08 match + 0.33 place
2008-08-30 12:32:45.466 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 12:35:52.037 Reschedule requested for id -1.
2008-08-30 12:35:52.449 Scheduled 88 items in 0.4 = 0.08 match + 0.33 place
2008-08-30 12:38:33.072 Reschedule requested for id -1.
2008-08-30 12:38:33.407 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 12:41:05.475 Reschedule requested for id -1.
2008-08-30 12:41:05.814 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 12:44:58.446 Reschedule requested for id -1.
2008-08-30 12:44:58.778 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 12:47:45.508 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 12:47:53.449 Reschedule requested for id -1.
2008-08-30 12:47:53.791 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 12:53:20.488 Reschedule requested for id -1.
2008-08-30 12:53:20.819 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 12:53:26.735 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 12:53:26.739 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 13:01:55.527 Reschedule requested for id -1.
2008-08-30 13:01:55.867 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 13:02:45.553 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 13:09:47.944 Reschedule requested for id -1.
2008-08-30 13:09:48.276 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 13:15:16.592 Reschedule requested for id -1.
2008-08-30 13:15:16.934 Scheduled 88 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 13:17:45.600 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 13:23:28.741 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 13:23:28.749 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 13:24:08.377 Reschedule requested for id -1.
2008-08-30 13:24:08.713 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 13:30:38.229 Reschedule requested for id -1.
2008-08-30 13:30:38.639 Scheduled 88 items in 0.4 = 0.08 match + 0.33 place
2008-08-30 13:32:45.647 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 13:36:03.319 Reschedule requested for id -1.
2008-08-30 13:36:03.644 Scheduled 88 items in 0.3 = 0.01 match + 0.31 place
2008-08-30 13:42:40.011 Reschedule requested for id -1.
2008-08-30 13:42:40.344 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 13:46:05.672 Reschedule requested for id -1.
2008-08-30 13:46:06.006 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 13:47:45.690 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 13:53:28.751 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 13:53:28.755 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 13:53:36.077 Reschedule requested for id -1.
2008-08-30 13:53:36.412 Scheduled 88 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 14:00:01.427 Reschedule requested for id -1.
2008-08-30 14:00:01.759 Scheduled 87 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 14:02:45.735 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 14:04:33.431 Reschedule requested for id -1.
2008-08-30 14:04:33.769 Scheduled 87 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 14:10:01.605 Reschedule requested for id -1.
2008-08-30 14:10:01.993 Scheduled 87 items in 0.4 = 0.01 match + 0.37 place
2008-08-30 14:15:30.250 Reschedule requested for id -1.
2008-08-30 14:15:30.587 Scheduled 87 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 14:17:45.778 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 14:21:05.729 Reschedule requested for id -1.
2008-08-30 14:21:06.068 Scheduled 87 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 14:23:31.756 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 14:23:31.763 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 14:26:50.341 Reschedule requested for id -1.
2008-08-30 14:26:50.685 Scheduled 87 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 14:29:53.312 Reschedule requested for id -1.
2008-08-30 14:29:53.649 Scheduled 87 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 14:32:45.821 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 14:37:25.253 Reschedule requested for id -1.
2008-08-30 14:37:25.592 Scheduled 87 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 14:40:12.829 Reschedule requested for id -1.
2008-08-30 14:40:13.164 Scheduled 87 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 14:42:55.465 Reschedule requested for id -1.
2008-08-30 14:42:55.808 Scheduled 87 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 14:46:05.436 Reschedule requested for id -1.
2008-08-30 14:46:05.768 Scheduled 87 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 14:47:45.977 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 14:50:21.317 Reschedule requested for id -1.
2008-08-30 14:50:21.654 Scheduled 87 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 14:53:32.765 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 14:53:32.771 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 14:53:50.637 Reschedule requested for id -1.
2008-08-30 14:53:50.973 Scheduled 87 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 14:58:50.837 Reschedule requested for id -1.
2008-08-30 14:58:51.178 Scheduled 87 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 15:01:28.541 Reschedule requested for id -1.
2008-08-30 15:01:28.877 Scheduled 86 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 15:02:46.052 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 15:07:02.714 Reschedule requested for id -1.
2008-08-30 15:07:03.052 Scheduled 86 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 15:13:55.109 Reschedule requested for id -1.
2008-08-30 15:13:55.445 Scheduled 86 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 15:17:46.103 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 15:18:53.332 Reschedule requested for id -1.
2008-08-30 15:18:53.668 Scheduled 86 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 15:22:45.868 MainServer::HandleAnnounce Monitor
2008-08-30 15:22:45.873 adding: M as a client (events: 0)
2008-08-30 15:22:49.764 Reschedule requested for id -1.
2008-08-30 15:22:50.166 Scheduled 86 items in 0.4 = 0.08 match + 0.33 place
2008-08-30 15:22:53.151 MainServer::HandleAnnounce Monitor
2008-08-30 15:22:53.154 adding: M as a client (events: 0)
2008-08-30 15:23:08.035 MainServer::HandleAnnounce Monitor
2008-08-30 15:23:08.037 adding: M as a client (events: 0)
2008-08-30 15:23:37.774 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 15:23:37.777 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 15:28:55.372 Reschedule requested for id -1.
2008-08-30 15:28:55.705 Scheduled 86 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 15:32:46.145 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 15:33:53.948 Reschedule requested for id -1.
2008-08-30 15:33:54.285 Scheduled 86 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 15:38:54.190 Reschedule requested for id -1.
2008-08-30 15:38:54.532 Scheduled 86 items in 0.3 = 0.01 match + 0.33 place
2008-08-30 15:42:05.128 Reschedule requested for id -1.
2008-08-30 15:42:05.557 Scheduled 86 items in 0.4 = 0.05 match + 0.37 place
2008-08-30 15:46:06.238 Reschedule requested for id -1.
2008-08-30 15:46:06.569 Scheduled 86 items in 0.3 = 0.01 match + 0.32 place
2008-08-30 15:47:46.192 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 15:53:43.780 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 15:53:43.789 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 16:02:46.247 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 16:17:46.298 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 16:23:43.791 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 16:23:43.793 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 16:32:46.351 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 16:47:46.403 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 16:53:47.795 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 16:53:47.798 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 17:02:46.452 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 17:17:46.503 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 17:23:50.800 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 17:23:50.806 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 17:32:46.551 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 17:47:46.601 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 17:53:57.808 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-30 17:53:57.814 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-30 18:02:46.653 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 18:13:12.232 MainServer::HandleAnnounce Monitor
2008-08-30 18:13:12.239 adding: M as a client (events: 0)
2008-08-30 18:13:14.611 MainServer::HandleAnnounce Monitor
2008-08-30 18:13:14.615 adding: M as a client (events: 0)
2008-08-30 18:13:16.367 MainServer::HandleAnnounce Monitor
2008-08-30 18:13:16.370 adding: M as a client (events: 0)
2008-08-30 18:13:23.937 MainServer::HandleAnnounce Monitor
2008-08-30 18:13:23.938 adding: M as a client (events: 0)
2008-08-30 18:13:24.046 Reschedule requested for id 25.
2008-08-30 18:13:24.369 Scheduled 86 items in 0.3 = 0.01 match + 0.31 place
2008-08-30 18:13:24.375 TVRec(1): ASK_RECORDING 1 0 0 0
2008-08-30 18:13:24.585 TVRec(1): Changing from None to RecordingOnly
2008-08-30 18:13:24.592 TVRec(1): HW Tuner: 1->1
2008-08-30 18:13:25.105 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-30 18:13:25.118 Started recording: Last Choir Standing: channel 5161 on cardid 1, sourceid 1
2008-08-30 18:13:25.234 TVRec(3): ASK_RECORDING 3 0 0 0
2008-08-30 18:13:27.652 MainServer::HandleAnnounce Monitor
2008-08-30 18:13:27.652 adding: M as a client (events: 0)
2008-08-30 18:13:35.495 MainServer::HandleAnnounce Monitor
2008-08-30 18:13:35.497 adding: M as a client (events: 0)
2008-08-30 18:13:35.677 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/M/5161_20080830181300.mpg'
2008-08-30 18:13:35.678 MainServer: Failed to make preview image.
2008-08-30 18:13:35.686 Preview Error: Run() file not local: '5161_20080830181300.mpg'
2008-08-30 18:13:43.878 MainServer::HandleAnnounce Monitor
2008-08-30 18:13:43.881 adding: M as a client (events: 0)
2008-08-30 18:13:44.053 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/M/5161_20080830181300.mpg'
2008-08-30 18:13:44.055 MainServer: Failed to make preview image.
2008-08-30 18:13:46.465 MainServer::HandleAnnounce Monitor
2008-08-30 18:13:46.466 adding: M as a client (events: 0)
2008-08-30 18:13:46.601 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/M/5161_20080830181300.mpg'
2008-08-30 18:13:46.602 MainServer: Failed to make preview image.
2008-08-30 18:13:49.029 MainServer::HandleAnnounce Monitor
2008-08-30 18:13:49.032 adding: M as a client (events: 0)
2008-08-30 18:13:49.169 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/M/5161_20080830181300.mpg'
2008-08-30 18:13:49.171 MainServer: Failed to make preview image.
2008-08-30 18:14:16.363 MainServer::HandleAnnounce Monitor
2008-08-30 18:14:16.364 adding: M as a client (events: 0)
2008-08-30 18:14:16.491 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/M/5161_20080830181300.mpg'
2008-08-30 18:14:16.492 MainServer: Failed to make preview image.
2008-08-30 18:14:19.474 MainServer::HandleAnnounce Monitor
2008-08-30 18:14:19.477 adding: M as a client (events: 0)
2008-08-30 18:14:19.616 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/M/5161_20080830181300.mpg'
2008-08-30 18:14:19.617 MainServer: Failed to make preview image.
2008-08-30 18:14:29.985 MainServer::HandleAnnounce Monitor
2008-08-30 18:14:29.987 adding: M as a client (events: 0)
2008-08-30 18:14:30.124 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/M/5161_20080830181300.mpg'
2008-08-30 18:14:30.125 MainServer: Failed to make preview image.
2008-08-30 18:14:30.132 Preview Error: Run() file not local: '5161_20080830181300.mpg'
2008-08-30 18:17:10.517 MainServer::HandleAnnounce Monitor
2008-08-30 18:17:10.521 adding: M as a client (events: 0)
2008-08-30 18:17:10.642 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/M/5161_20080830181300.mpg'
2008-08-30 18:17:10.643 MainServer: Failed to make preview image.
2008-08-30 18:17:13.756 MainServer::HandleAnnounce Monitor
2008-08-30 18:17:13.758 adding: M as a client (events: 0)
2008-08-30 18:17:13.895 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/M/5161_20080830181300.mpg'
2008-08-30 18:17:13.896 MainServer: Failed to make preview image.
2008-08-30 18:17:46.712 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min

---

### Post by DemonBob on 2008-08-30
What motherboard do you have? 

[http://www.mail-archive.com/linux-dvb@linuxtv.org/msg30137.html](http://www.mail-archive.com/linux-dvb@linuxtv.org/msg30137.html)

Seems that if your motherboard has the same southbridge chipset you might be having this issues. In which case a USB PCI card would most likely resolve the issue.

---

### Post by SteveGodfrey on 2008-08-30
I have a FIC motherboard P4M915GD1 using an Intel P4 chip.

---

### Post by SteveGodfrey on 2008-08-30
Just been reading the LinuxTV wiki and there's a new version of the firmware. (see below) Any ideas how I can replace the existing firmware?

The one it's currently using is

dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
 
But that file doesn't exist on the system anywhere, so where is it coming from?

steve@M:/lib/firmware$ sudo locate dib7000
[sudo] password for steve:
/lib/modules/2.6.24-19-generic/kernel/drivers/media/dvb/frontends/dib7000m.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/media/dvb/frontends/dib7000p.ko
/usr/src/linux-headers-2.6.24-19/drivers/media/dvb/frontends/dib7000m.h
/usr/src/linux-headers-2.6.24-19/drivers/media/dvb/frontends/dib7000p.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/dvb/dib7000m.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/dvb/dib7000p.h
steve@M:/lib/firmware$



August 21, 2008 - New firmware file fixing the last cause for i2c errors and disconnects and providing a new, more modular i2c request formatting.

You will need the dvb-usb-dib0700-1.20.fw firmware file in /lib/firmware or the relevant place for your distribution.

You may need to change the name of the file to dvb-usb-dib0700-1.10.fw or create a link until the driver code reflects that change.

For archival purposes: dvb-usb-dib0700-1.10.fw firmware file

August 29,2008 - Issues with Firmware 1.20. Some issues have been found with the latest version of the firmware. Users may wish to continue to use 1.10 unless thay have patched their v4l-dvb code with dib0700_new_i2c_api.patch.

---

