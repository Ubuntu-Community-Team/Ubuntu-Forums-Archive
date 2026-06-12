---
title: "Able to ping IP address but not domain names"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by mjason1 on 2010-06-15
Since two days i m not able to browse websites using the domain names but able to ping/browse using IP addressed.  I have done the following:

1. Using wireless i m able to get IP address of DNS (8.8.8.8), Gateway, localhost & router ip address
2. Disabled wireless and connected ETH0 but still the same problem
3. not able to edit resolv.conf

sudo gedit resolv.conf

** (gedit:4179): WARNING **: Hit unhandled case 0 (Error opening file: Input/output error) in parse_error.

4.  cat /etc/network/interfaces
auto lo
iface lo inet loopback

5. below is the status for ping, 

ubuntu@ubuntu:/etc$ ping [www.google.com]("http://www.google.com")
ping: unknown host [www.google.com]("http://www.google.com")
ubuntu@ubuntu:/etc$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=243 time=67.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=243 time=67.8 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=243 time=68.1 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 67.222/67.755/68.160/0.447 ms
ubuntu@ubuntu:/etc$ ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=64 time=0.867 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=0.595 ms
64 bytes from 10.0.0.1: icmp_seq=3 ttl=64 time=1.49 ms
^C
--- 10.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.595/0.985/1.495/0.378 ms
ubuntu@ubuntu:/etc$ dig +short [www.google.com]("http://www.google.com")
^Cubuntu@ubuntu:/etc

6.

ubuntu@ubuntu:/etc$ dig +short @208.67.222.222 [www.google.com]("http://www.google.com")
google.navigation.opendns.com.
208.67.216.231
208.67.216.230
ubuntu@ubuntu:/etc$ nc -z -v 74.125.95.103 80
74.125.95.103: inverse host lookup failed: Unknown host
(UNKNOWN) [74.125.95.103] 80 (www) open

7. ifconfig output

ubuntu@ubuntu:/etc$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:99:06:3b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4667 (4.6 KB)  TX bytes:4667 (4.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:06:9d:38  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe06:9d38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54407 (54.4 KB)  TX bytes:67574 (67.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-06-9D-38-30-36-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

8. route -n output

ubuntu@ubuntu:/etc$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0

If anyone can provide some pointers/info on how to get this fixed it would be greatly appreciated.

Thanks in advance.

---

### Post by bigmojo74 on 2010-06-15
Assuming it's not a permissions issue and just a corrupt file, I'd back up the current resolv.conf (out of habit more than anything), remove it, then recreate it.

This is what the resolv.conf looks like on my server, small file.

> domain biergarten
search biergarten
nameserver 192.168.2.1

Pretty sure you'd want to sudo /etc/init.d/networking restart for the new file to take affect.

---

### Post by mjason1 on 2010-06-15
unable to remove the file using the following command

ubuntu@ubuntu:/etc$ rm resolv.conf
rm: cannot remove `resolv.conf': Input/output error

ubuntu@ubuntu:/etc$ sudo rm resolv.conf
rm: cannot remove `resolv.conf': Input/output error

resolv.conf.tmp has the content that i require.

---

### Post by beowulf1416 on 2010-06-15
the input/output error you're getting might mean the file is corrupted. i had this happen to me when my disk crashed. try checking that.

---

### Post by mjason1 on 2010-06-15
How do i get the file corruption issue fixed?
I m running ubuntu remix from a USB drive

and when i run fsck /dev/sda, i get the following message:

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.16
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  90:fa/33, 91:fc/c9, 92:31/8e, 93:c0/d1, 94:8e/bc, 95:d0/f4, 96:bc/7b
  , 97:b4/8e, 98:7b/c1, 99:06/8e, 100:57/d9, 101:8e/bd, 102:c0/00, 103:b9/7c
  , 104:08/88, 105:00/4e, 106:bf/02, 107:b4/8a, 108:7b/56, 109:f3/40
  , 110:a5/b4, 111:8e/08, 112:d8/cd, 113:bb/13, 114:78/73, 115:00/05
  , 116:0f/b9, 117:b4/ff, 118:37/ff, 119:0f/8a, 120:a0/f1, 121:56/66
  , 122:88/0f, 123:16/b6, 124:21/c6, 125:28/40, 126:20/66, 127:d2/0f
  , 128:78/b6, 129:15/d1, 130:b1/80, 131:06/e2, 132:89/3f, 133:3f/f7
  , 134:89/e2, 135:47/86, 136:02/cd, 137:f3/c0, 138:64/ed, 139:a5/06
  , 140:8a/41, 141:0e/66, 142:18/0f, 143:7c/b7, 144:88/c9, 145:4d/66
  , 146:f8/f7, 147:cd/e1, 148:13/66, 149:eb/89, 150:27/46, 151:f6/f8
  , 152:45/83, 153:f0/7e, 154:7f/16, 155:75/00, 156:08/75, 157:66/38
  , 158:8b/83, 159:45/7e, 160:f8/2a, 161:66/00, 162:a3/77, 163:1c/32
  , 164:7c/66, 165:b4/8b, 166:08/46, 167:cd/1c, 168:13/66, 169:72/83
  , 170:13/c0, 171:20/0c, 172:e4/bb, 173:75/00, 174:0f/80, 175:c1/b9
  , 176:ea/01, 177:08/00, 178:42/e8, 179:89/2b, 180:16/00, 181:1a/e9
  , 182:7c/48, 183:83/03, 184:e1/a0, 185:3f/fa, 186:89/7d, 187:0e/b4
  , 188:18/7d, 189:7c/8b, 190:fb/f0, 191:bb/ac, 192:aa/84, 193:55/c0
  , 194:b4/74, 195:41/17, 196:8a/3c, 197:16/ff, 198:21/74, 199:28/09
  , 200:cd/b4, 201:13/0e, 202:72/bb, 203:10/07, 204:81/00, 205:fb/cd
  , 206:55/10, 207:aa/eb, 208:75/ee, 209:0a/a0, 210:f6/fb, 211:c1/7d
  , 212:01/eb, 213:74/e5, 214:05/a0, 215:c6/f9, 216:06/7d, 217:02/eb
  , 218:7d/e0, 219:00/98, 220:66/cd, 221:a1/16, 222:f8/cd, 223:7d/19
  , 224:bb/66, 225:00/60, 226:7e/66, 227:e8/3b, 228:10/46, 229:00/f8
  , 230:66/0f, 231:81/82, 232:3e/4a, 233:24/00, 234:7e/66, 235:d4/6a
  , 236:6c/00, 237:78/66, 238:74/50, 239:0f/06, 240:85/53, 241:c3/66
  , 242:00/68, 243:e9/10, 244:3a/00, 245:02/01, 246:bd/00, 247:01/80
  , 248:00/7e, 249:66/02, 250:03/00, 251:06/0f, 252:1c/85, 253:7c/20
  , 254:66/00, 255:31/b4, 256:d2/41, 257:eb/bb, 258:4f/aa, 260:e8/8a
  , 261:d5/56, 262:00/40, 263:66/cd, 264:0f/13, 265:b7/0f, 266:fd/82
  , 267:b9/1c, 268:10/00, 269:00/81, 270:66/fb, 271:52/55, 272:66/aa
  , 273:50/0f, 274:06/85, 275:53/14, 276:57/00, 277:6a/f6, 278:10/c1
  , 279:89/01, 280:e6/0f, 281:66/84, 282:60/0d, 283:8a/00, 284:16/fe
  , 285:21/46, 286:28/02, 287:1e/b4, 288:16/42, 289:1f/8a, 290:b4/56
  , 291:42/40, 292:cd/8b, 293:13/f4, 294:1f/cd, 295:66/13, 296:61/b0
  , 297:8d/f9, 298:64/66, 299:10/58, 300:72/66, 301:10/58, 302:5d/66
  , 303:66/58, 304:01/66, 305:f8/58, 306:29/eb, 307:fd/2a, 308:c1/66
  , 309:e7/33, 310:09/d2, 311:01/66, 312:fb/0f, 313:21/b7, 314:ed/4e
  , 315:75/18, 316:c6/66, 317:c3/f7, 318:66/f1, 319:60/fe, 320:31/c2
  , 321:c0/8a, 322:8a/ca, 323:16/66, 324:21/8b, 325:28/d0, 326:cd/66
  , 327:13/c1, 328:66/ea, 329:61/10, 330:e2/f7, 331:c2/76, 332:c6/1a
  , 333:06/86, 334:02/d6, 335:7d/8a, 336:4f/56, 337:5d/40, 338:66/8a
  , 339:52/e8, 340:66/c0, 341:50/e4, 342:55/06, 343:53/0a, 344:66/cc
  , 345:0f/b8, 346:b7/01, 347:36/02, 348:18/cd, 349:7c/13, 351:0f/61
  , 352:b7/0f, 353:3e/82, 354:1a/54, 355:7c/ff, 356:66/81, 357:f7/c3
  , 358:f6/00, 359:31/02, 360:c9/66, 361:87/40, 362:ca/49, 363:66/0f
  , 364:f7/85, 365:f7/71, 366:e8/ff, 367:6b/c3, 368:00/4e, 369:29/54
  , 370:ce/4c, 371:39/44, 372:f5/52, 373:76/20, 374:02/20, 375:89/20
  , 376:f5/20, 377:c0/20, 378:e4/20, 379:06/00, 380:41/00, 381:08/00
  , 382:e1/00, 383:88/00, 384:c5/00, 385:88/00, 386:d6/00, 387:8a/00
  , 388:16/00, 389:21/00, 390:28/00, 391:95/00, 392:b4/00, 393:02/00
  , 394:bd/00, 395:10/00, 397:66/00, 398:60/00, 399:cd/00, 400:13/00
  , 401:66/00, 402:61/00, 403:72/00, 404:17/00, 405:66/00, 406:0f/00
  , 407:b6/00, 408:c8/00, 409:c1/00, 410:e0/00, 411:09/00, 412:5b/00
  , 413:01/00, 414:c3/00, 415:5d/00, 416:66/00, 417:58/00, 418:66/00
  , 419:5a/00, 420:66/00, 421:01/00, 422:c8/00, 423:29/00, 424:cd/00
  , 425:75/00, 426:a7/00, 427:c3/00, 428:4d/0d, 429:75/0a, 430:de/52
  , 431:95/65, 432:d1/6d, 433:2e/6f, 434:fc/76, 435:7d/65, 436:75/20
  , 437:df/64, 438:31/69, 439:f6/73, 440:8e/6b, 441:d6/73, 442:bc/20
  , 443:b0/6f, 444:7b/72, 445:8e/20, 446:de/6f, 447:66/74, 448:8f/68
  , 449:06/65, 450:78/72, 451:00/20, 452:be/6d, 453:e7/65, 454:7d/64
  , 455:ac/69, 456:20/61, 457:c0/2e, 458:74/ff, 459:09/0d, 460:b4/0a
  , 461:0e/44, 462:bb/69, 463:07/73, 464:00/6b, 465:cd/20, 466:10/65
  , 467:eb/72, 468:f2/72, 469:98/6f, 470:cd/72, 471:16/ff, 472:cd/0d
  , 473:19/0a, 474:eb/50, 475:fe/72, 476:3b/65, 477:2e/73, 478:fc/73
  , 479:7d/20, 480:76/61, 481:04/6e, 482:8b/79, 483:2e/20, 484:fc/6b
  , 485:7d/65, 486:c3/79, 487:42/20, 488:6f/74, 490:74/20, 491:20/72
  , 493:72/73, 494:72/74, 495:6f/61, 497:0d/74, 498:0a/0d, 499:00/0a
  , 505:3d/ac, 506:00/cb, 507:00/d8, 508:7f/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
/dev/sda1: 238 files, 960678/996445 clusters

---

