---
title: "Why VOD server sends RTSP ANNOUNCE 2401 Ticket Expired event to client?"
date: 2011-11-25
forum: Multimedia Software
---

### Post by grashmi13 on 2011-11-25
HI,

See below pcap logs. As per pcap, describe completed successfully and then SETUP also completed within 1 second. STB sent acknowledgement to server for SETUP reply packet. After this STB didnt process reply(could be waiting for response from SDK layer). and after 60 seconds VOD server sent an Announcement to STB saying "Ticket Expired". 

My question is: when VOD server send Ticket Expired to STB?

Viewing rights are available to STB, because if STB again tries to play same movie on this server, it plays successfully.










See these Pcap logs:
----------------------------------------------------------------xxxxxxxxxxxxxx-----------------------------------------------
20111122-DSL-WAN_capture-shows_failover
----------------------------------------------------------------xxxxxxxxxxxxxx-----------------------------------------------
Thread:4288] Control thread at select()\n
  17419 125.411906  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:34 softCCDaemon: [SoftCCDaemon] clear CC screen\n
  17420 125.414996  10.11.180.86          172.30.10.67          TCP      42028 > rtsp [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=2710504 TSER=0 WS=5
  17421 125.480590  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:34 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17422 125.572012  172.30.10.67          10.11.180.86          TCP      rtsp > 42028 [SYN, ACK] Seq=0 Ack=1 Win=16384 Len=0 MSS=1460 WS=0 TSV=0 TSER=0
  17423 125.572485  10.11.180.86          172.30.10.67          TCP      42028 > rtsp [ACK] Seq=1 Ack=1 Win=5856 Len=0 TSV=2710662 TSER=0
  17424 125.573814  10.11.180.86          172.30.10.67          RTSP     DESCRIBE rtsp://172.30.10.67:554/BestMotoringJapan_11032011_USA_tr_375.mpg RTSP/1.0
  17425 125.589720  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:34 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17426 125.612326  172.30.10.67          10.11.180.86          RTSP/SDP Reply: RTSP/1.0 200 OK, with session description
  17427 125.612800  10.11.180.86          172.30.10.67          TCP      42028 > rtsp [ACK] Seq=123 Ack=515 Win=6912 Len=0 TSV=2710702 TSER=192461857
  17428 125.681668  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:34 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17429 125.685322  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:34 myrioi: Thread: SystemDefaultThreadPool 58: shutting down orphaned rtspclient: rtsp-client(listener-th=rtsp-listener-26, ka-th=rtsp-keep-alive-26,req-handler-th=rtsp-req-handler-26)\n
  17430 125.685327  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:34 myrioi: rtspclient for connId: 172.30.10.67:554 not found. Creating new rtspclient\n
  17431 125.689857  10.11.180.86          172.30.10.67          TCP      42029 > rtsp [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=2710779 TSER=0 WS=5
  17432 125.692824  10.11.180.86          172.30.10.67          TCP      42028 > rtsp [FIN, ACK] Seq=123 Ack=515 Win=6912 Len=0 TSV=2710782 TSER=192461857
  17433 125.725169  172.30.10.67          10.11.180.86          TCP      rtsp > 42029 [SYN, ACK] Seq=0 Ack=1 Win=16384 Len=0 MSS=1460 WS=0 TSV=0 TSER=0
  17434 125.725575  10.11.180.86          172.30.10.67          TCP      42029 > rtsp [ACK] Seq=1 Ack=1 Win=5856 Len=0 TSV=2710815 TSER=0
  17435 125.726974  10.11.180.86          172.30.10.67          RTSP     SETUP rtsp://172.30.10.67:554/BestMotoringJapan_11032011_USA_tr_375.mpg RTSP/1.0
  17436 125.726979  172.30.10.67          10.11.180.86          TCP      rtsp > 42028 [ACK] Seq=515 Ack=124 Win=65413 Len=0 TSV=192461858 TSER=2710782
  17437 125.726982  172.30.10.67          10.11.180.86          TCP      rtsp > 42028 [FIN, ACK] Seq=515 Ack=124 Win=65413 Len=0 TSV=192461858 TSER=2710782
  17438 125.727806  10.11.180.86          172.30.10.67          TCP      42028 > rtsp [ACK] Seq=124 Ack=516 Win=6912 Len=0 TSV=2710817 TSER=192461858
  17439 125.790628  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:34 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17440 125.882539  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:34 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17441 125.946886  172.30.10.67          10.11.180.86          TCP      rtsp > 42029 [ACK] Seq=1 Ack=186 Win=65350 Len=0 TSV=192461861 TSER=2710816
  17442 125.991601  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:34 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17443 126.058305  Entone_37:aa:c4       ZhoneTec_49:10:6c     ARP      Who has 10.11.183.254?  Tell 10.11.180.62
  17444 126.083626  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:35 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17445 126.089049  ZhoneTec_49:10:6c     Entone_37:aa:c4       ARP      10.11.183.254 is at 00:01:47:49:10:6c
  17446 126.192603  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:35 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17447 126.281959  172.30.10.67          10.11.180.86          RTSP     Reply: RTSP/1.0 200 OK
  17448 126.282345  10.11.180.86          172.30.10.67          TCP      42029 > rtsp [ACK] Seq=186 Ack=222 Win=6912 Len=0 TSV=2711372 TSER=192461864
  17449 126.284577  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:35 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17450 126.395715  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:35 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17451 126.485595  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:35 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17452 126.596498  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:35 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17453 126.686620  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:35 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17454 126.797860  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:35 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17455 126.887720  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:35 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17456 126.998696  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:35 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17457 127.088568  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:36 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17458 127.199683  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:36 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17459 127.289632  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:36 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17460 127.400546  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:36 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17461 127.490564  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:36 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17462 127.601674  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:36 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17463 127.691680  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:36 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17464 127.694274  10.11.180.62          225.2.2.7             IGMP     V2 Membership Report / Join group 225.2.2.7
  17465 127.802560  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:36 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17466 127.892562  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:36 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17467 128.003671  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:36 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17468 128.093970  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:37 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17469 128.204608  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:37 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17470 128.294768  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:37 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17471 128.405551  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:37 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17472 128.495646  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:37 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17473 128.606536  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:37 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17474 128.696936  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:37 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17475 128.807644  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:37 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17476 128.897578  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:37 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17477 129.008600  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:37 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17478 129.098669  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:38 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17479 129.209565  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:38 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17480 129.299505  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:38 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17481 129.411389  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:38 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17482 129.500703  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:38 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17483 129.611644  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:38 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17484 129.701482  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:38 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17485 129.812667  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:38 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17486 129.902513  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:38 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17487 130.013666  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:38 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17488 130.103506  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:39 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17489 130.214600  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:39 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17490 130.304580  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:39 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17491 130.415587  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:39 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17492 130.505583  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:39 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17493 130.616731  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:39 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17494 130.706588  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:39 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17495 130.817740  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:39 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17496 130.907610  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:39 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17497 131.018801  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:39 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17498 131.108608  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:40 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17499 131.219661  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:40 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17500 131.309557  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:40 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17501 131.420633  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:40 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17502 131.510591  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:40 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17503 131.621640  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:40 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17504 131.711590  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:40 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17505 131.822623  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:40 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17506 131.912685  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:40 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17507 132.023660  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:41 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17508 132.114007  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:41 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17509 132.224672  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:41 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17510 132.314650  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:41 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17511 132.425549  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:41 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17512 132.515607  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:41 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17513 132.626690  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:41 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17514 132.716494  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:41 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17515 132.827605  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:41 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17516 132.917834  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:41 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17517 133.028602  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:42 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17518 133.118614  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:42 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17519 133.229651  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:42 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17520 133.319830  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:42 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17521 133.430988  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:42 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17522 133.520598  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:42 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17523 133.631670  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:42 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17524 133.721587  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:42 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17525 133.832597  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:42 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17526 133.922501  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:42 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17527 134.033656  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:43 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17528 134.123565  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:43 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17529 134.234602  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:43 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17530 134.324567  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:43 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17531 134.435634  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:43 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17532 134.525524  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:43 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17533 134.636703  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:43 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17534 134.726741  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:43 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17535 134.837707  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:43 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17536 134.927652  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:43 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17537 135.038578  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17538 135.128622  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17539 135.239700  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17540 135.329542  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17541 135.440571  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17542 135.530584  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17543 135.641693  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17544 135.704688  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 myrioi: rtspclient for connId: 172.30.1.220:554 not found. Creating new rtspclient\n
  17545 135.707407  10.11.180.86          172.30.1.220          TCP      35518 > rtsp [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=2720797 TSER=0 WS=5
  17546 135.731536  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17547 135.736133  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 myrioi: Thread: Thread-119: shutting down orphaned rtspclient: rtsp-client(listener-th=NONE, ka-th=rtsp-keep-alive-27,req-handler-th=rtsp-req-handler-27)\n
  17548 135.756692  172.30.1.220          10.11.180.86          TCP      rtsp > 35518 [SYN, ACK] Seq=0 Ack=1 Win=16384 Len=0 MSS=1460 WS=0 TSV=0 TSER=0
  17549 135.757062  10.11.180.86          172.30.1.220          TCP      35518 > rtsp [ACK] Seq=1 Ack=1 Win=5856 Len=0 TSV=2720846 TSER=0
  17550 135.758470  10.11.180.86          172.30.1.220          RTSP     DESCRIBE rtsp://172.30.1.220:554/BestMotoringJapan_11032011_USA_tr_375.mpg RTSP/1.0
  17551 135.842663  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17552 135.852307  172.30.1.220          10.11.180.86          RTSP/SDP Reply: RTSP/1.0 200 OK, with session description
  17553 135.852755  10.11.180.86          172.30.1.220          TCP      35518 > rtsp [ACK] Seq=123 Ack=515 Win=6912 Len=0 TSV=2720942 TSER=90934854
  17554 135.899102  10.11.180.86          172.30.1.220          TCP      35518 > rtsp [FIN, ACK] Seq=123 Ack=515 Win=6912 Len=0 TSV=2720988 TSER=90934854
  17555 135.922716  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 myrioi: Thread: SystemDefaultThreadPool 58: shutting down orphaned rtspclient: rtsp-client(listener-th=rtsp-listener-28, ka-th=rtsp-keep-alive-28,req-handler-th=rtsp-req-handler-28)\n
  17556 135.922723  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 myrioi: rtspclient for connId: 172.30.1.220:554 not found. Creating new rtspclient\n
  17557 135.926353  10.11.180.86          172.30.1.220          TCP      35519 > rtsp [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=2721016 TSER=0 WS=5
  17558 135.932596  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:44 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17559 135.947104  172.30.1.220          10.11.180.86          TCP      rtsp > 35518 [ACK] Seq=515 Ack=124 Win=65413 Len=0 TSV=90934855 TSER=2720988
  17560 135.947108  172.30.1.220          10.11.180.86          TCP      rtsp > 35518 [FIN, ACK] Seq=515 Ack=124 Win=65413 Len=0 TSV=90934855 TSER=2720988
  17561 135.947685  10.11.180.86          172.30.1.220          TCP      35518 > rtsp [ACK] Seq=124 Ack=516 Win=6912 Len=0 TSV=2721037 TSER=90934855
  17562 135.976897  172.30.1.220          10.11.180.86          TCP      rtsp > 35519 [SYN, ACK] Seq=0 Ack=1 Win=16384 Len=0 MSS=1460 WS=0 TSV=0 TSER=0
  17563 135.977399  10.11.180.86          172.30.1.220          TCP      35519 > rtsp [ACK] Seq=1 Ack=1 Win=5856 Len=0 TSV=2721067 TSER=0
  17564 135.979347  10.11.180.86          172.30.1.220          RTSP     SETUP rtsp://172.30.1.220:554/BestMotoringJapan_11032011_USA_tr_375.mpg RTSP/1.0
  17565 136.043744  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17566 136.133487  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17567 136.226746  172.30.1.220          10.11.180.86          TCP      rtsp > 35519 [ACK] Seq=1 Ack=186 Win=65350 Len=0 TSV=90934858 TSER=2721068
  17568 136.244614  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17569 136.334615  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17570 136.445612  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17571 136.535551  10.11.180.62          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 entone_mediaplayer: (1219)[control.c empControlThread:4288] Control thread at select()\n
  17572 136.551892  172.30.1.220          10.11.180.86          RTSP     Reply: RTSP/1.0 200 OK
  17573 136.552228  10.11.180.86          172.30.1.220          TCP      35519 > rtsp [ACK] Seq=186 Ack=222 Win=6912 Len=0 TSV=2721641 TSER=90934861
  17574 136.612194  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 siege[1196]: [essHAL_sendVideoCmds]: stream_id =7071784, requesed dec_id=0, consumerFromEmp: 0, routeFromEmp: 0 transport type: 0\n
  17575 136.613212  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 siege[1196]: [essHAL_sendVideoCmds]: found stream ID with consumer type set to Decode and main route\n
  17576 136.613219  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 siege[1196]: [MpegTsOpenSource] (1321972185.591613) IN,  idx=0, fname=udp://0.0.0.0:2014, tpbuf_thresh=0, ca_id=NULL, secCode=0\n
  17577 136.613223  10.11.180.86          172.30.1.233          Syslog   USER.EMERG: Nov 22 14:29:45 siege[1196]: [MpegTsOpenSource] IN: idx=0, fname=udp://0.0.0.0:2014, tpbuf_thresh=0, ca_id=NULL, secCode=0\n
  17578 136.613227  10.11.180.86          172.30.1.233          Syslog   USER.NOTICE: Nov 22 14:29:45 siege[1196]: [evcOpenSrc]\n
  17579 136.613583  10.11.180.86          172.30.1.233          Syslog   USER.INFO: Nov 22 14:29:45 siege[1196]: [mcastOpenSrc]\n
  17580 136.613589  10.11.180.86          172.30.1.233          Syslog   USER.INFO: Nov 22 14:29:45 siege[1196]: [openVidSource]\n
  17581 136.613594  10.11.180.86          172.30.1.233          Syslog   USER.INFO: Nov 22 14:29:45 siege[1196]: EnVideoCtl: switching channel to udp://0.0.0.0:2014\n
  17582 136.613603  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 siege[1196]: [sendVideoPlayerCommand]: opcode: 0 send with stream_id=7071784\n
  17583 136.613935  10.11.180.86          172.30.1.233          Syslog   USER.INFO: Nov 22 14:29:45 siege[1196]: [sendVideoPlayerCommand] wait response from play_entone, message.opcode = 0\n
  17584 136.613942  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 myrioi: +getSubscriberIDHash\n
  17585 136.614267  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 myrioi: -getSubscriberIDHash: OPjWrvMePeIxiuOysKRqCOmTl6A=\n
  17586 136.614275  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 myrioi: IDKTRACE: >>> FillSecurityArray pSecCodes[0], secType = 1, secOption = 0\n
  17587 136.614608  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 myrioi: IDKTRACE: >>> MpegTsOpenSource_v2(idx=0, fname=udp://0.0.0.0:2014, thresh=0, secArrayLen = 1, requestedSecCodes = 0xb415e8, pri = 1 \n
  17588 136.614615  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 myrioi: native side type = 1, option = 0 \n
  17589 136.614620  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 myrioi: [MpegTsOpenSource_v2] IP: 0.0.0.0 port: 2014\n
  17590 136.614625  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 myrioi: [mcastOpenSrc]: IN\n
  17591 136.615058  10.11.180.86          172.30.1.233          Syslog   USER.ERR: Nov 22 14:29:45 myrioi: [openVidSource] i am in broadcom openVidSource now, s->type: 12\n






SETUP rtsp://172.30.10.67:554/BestMotoringJapan_11032011_USA_tr_375.mpg RTSP/1.0
CSeq: 70
Transport: MP2T/H2221/UDP;client_port=2012;destination=10.11.180.86;unicast
x-mayNotify:

RTSP/1.0 200 OK
CSeq: 70
Session: 20383488
Range: npt=0.000-
Transport: MP2T/H2221/UDP;unicast;client=10.11.180.86;control_address=10.11.180.86;destination=10.11.180.86:2012;bandwidth=3760000
x-OVSExtensions: 1.1

ANNOUNCE rtsp:/BestMotoringJapan_11032011_USA_tr_375.mpg RTSP/1.0
CSeq: 1
Session: 20383488
x-notice: 2401 "Ticket Expired" event-date=20111122T143035.26







Regards,
rashmi

---

