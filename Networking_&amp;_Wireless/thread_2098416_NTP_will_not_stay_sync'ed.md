---
title: "NTP will not stay sync'ed"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by nj7p on 2012-12-26
**I am using both Ubuntu 11.10 and 12.04.  I have a minimal ntp.conf file which consists of only some pool servers and two located near by.  I have stopped ntp and used ntpdate to sync the local clock to tick.uh.edu.  Then I restart ntp.  Here is a few minutes of ntpq -p:**

root@ns4:/etc# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 d7.hotfile.com  64.147.116.229   2 u    4   64    1   70.746  -903.78   0.000
 200.140.8.72.in 64.147.116.229   2 u    4   64    1   54.942  -1005.5   0.000
 sisdb01.muskego 128.118.25.5     2 u    4   64    1  126.251  -1072.0   0.000
 x2la01.hostigat 63.145.169.2     3 u    4   64    1   44.871  -1185.6   0.000
 pneumatix.linoc 192.12.19.20     2 u    1   64    1   55.886  -1277.6 178.198
 time-1.egr.unlv 134.121.64.220   3 u    -   64    1   48.055  -1550.7 182.616
*LOCAL(0)        .LOCL.           5 l    1   64    1    0.000    0.000   0.000
root@ns4:/etc# ntpq -p

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 d7.hotfile.com  64.147.116.229   2 u   50   64    1   70.746  -903.78   0.000
 200.140.8.72.in 64.147.116.229   2 u   49   64    1   54.942  -1005.5   0.000
 sisdb01.muskego 128.118.25.5     2 u   48   64    1  126.251  -1072.0   0.000
 x2la01.hostigat 63.145.169.2     3 u   47   64    1   44.871  -1185.6   0.000
*pneumatix.linoc 192.12.19.20     2 u   36   64    1   54.564  -2003.7 453.727
+time-1.egr.unlv 134.121.64.220   3 u   35   64    1   47.192  -2279.0 604.865
 LOCAL(0)        .LOCL.           5 l   44   64    1    0.000    0.000   0.000

**here we have sync'ed up**.

root@ns4:/etc# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 d7.hotfile.com  64.147.116.229   2 u   60   64  377   66.428  -126008 17342.4
 200.140.8.72.in 64.147.116.229   2 u   63   64  377   37.996  -113947 14737.6
 sisdb01.muskego 128.118.25.5     2 u   62   64  377  115.697  -125634 17267.3
 x2la01.hostigat 63.145.169.2     3 u   63   64  377   35.013  -96510. 26204.4
 pneumatix.linoc 192.12.19.20     2 u    5   64  377   50.695  -130555 18071.3
 time-1.egr.unlv 134.121.64.220   3 u   16   64  377   39.878  -117392 15330.7
*LOCAL(0)        .LOCL.           5 l   26   64  377    0.000    0.000   0.000

[B]Here we have lost it.  Note horrible offset and jitter.

[/B]root@ns4:/etc# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 d7.hotfile.com  64.147.116.229   2 u   38   64  377   66.428  -126008 14943.6
 200.140.8.72.in 64.147.116.229   2 u   42   64  377   37.996  -113947 21488.0
 sisdb01.muskego 128.118.25.5     2 u   44   64  377  115.697  -125634 14881.9
 x2la01.hostigat 63.145.169.2     3 u   45   64  377   35.286  -125745 14772.7
 pneumatix.linoc 192.12.19.20     2 u   49   64  377   49.939  -149073 27572.8
 time-1.egr.unlv 134.121.64.220   3 u   61   64  377   39.878  -117392 17908.2
*LOCAL(0)        .LOCL.           5 l   11   64  377    0.000    0.000   0.000

root@ns4:/etc# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 d7.hotfile.com  64.147.116.229   2 u   43   64  377   66.428  -126008 21626.1
 200.140.8.72.in 64.147.116.229   2 u   45   64  377   38.002  -125656 21753.3
 sisdb01.muskego 128.118.25.5     2 u   45   64  377  115.697  -125634 21663.6
 x2la01.hostigat 63.145.169.2     3 u   48   64  377   35.286  -125745 21466.3
 pneumatix.linoc 192.12.19.20     2 u   50   64  377   49.939  -149073 18015.7
 time-1.egr.unlv 134.121.64.220   3 u   57   64  377   39.878  -117392 27453.6
*LOCAL(0)        .LOCL.           5 l   17   64  377    0.000    0.000   0.000

root@ns4:/etc# ntpdc -p
     remote           local      st poll reach  delay   offset    disp
=======================================================================
*LOCAL(0)        127.0.0.1        5   64  377 0.00000  0.000000 0.03043
=200.140.8.72.in 192.168.11.31    2   64  377 0.04086 -161.6000 0.06038
=time-1.egr.unlv 192.168.11.31    3   64  377 0.04553 -166.7793 0.13936
=x2la01.hostigat 192.168.11.31    3   64  377 0.03700 -149.4387 0.06389
=d7.hotfile.com  192.168.11.31    2   64  377 0.06378 -179.4827 0.04507
=pneumatix.linoc 192.168.11.31    2   64  377 0.04993 -149.0730 0.06622
=sisdb01.muskego 192.168.11.31    2   64  377 0.11940 -161.5829 0.06380
root@ns4:

[B]This is Ubuntu running in a VirtualBox VM on a Dell 1950 server.  I am seeing the same thing on a Fedora 16 VM as well.  I have a DSL and a Cable modem connection and the problem persists on either.  

Any help would be appreciated.  I have read older posts to this and other forums and found no fix.

Bill
[/B]

---

