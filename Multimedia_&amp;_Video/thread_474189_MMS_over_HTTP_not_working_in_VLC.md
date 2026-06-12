---
title: "MMS over HTTP not working in VLC"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by austin.lund on 2007-06-14
I know vlc player is not supported, but totem doesn't seem to play this stream either:

[http://DMZVIDEO2.aph.gov.au/HMS2V](http://DMZVIDEO2.aph.gov.au/HMS2V)

(somewhat important if you are a resident of Australia).

Getting support (from aph.gov.au) for anything other than windows media player is like pulling teeth. 

However, this stream works on mplayer perfectly, totem has a nice grey image (which is pretty useless), and vlc (my preferred player) doesn't connect at all.

It seems that it is the way in which VLC sends the request.  Below is a tcpdump of the VLC request for the media:

```
10:24:10.175248 IP lund-desktop-2.local.53457 > redvideo1.aph.gov.au.www: P 1:99
(98) ack 1 win 183 <nop,nop,timestamp 1404890 0>
        0x0000:  4500 0096 e014 4000 4006 340b 0a01 0103  E.....@.@.4.....
        0x0010:  ca0e 5130 d0d1 0050 f13a 8fde d19a 24a5  ..Q0...P.:....$.
        0x0020:  8018 00b7 9239 0000 0101 080a 0015 6fda  .....9........o.
        0x0030:  0000 0000 4745 5420 2f48 4d53 3256 2048  ....GET./HMS2V.H
        0x0040:  5454 502f 312e 300d 0a41 6363 6570 743a  TTP/1.0..Accept:
        0x0050:  202a 2f2a 0d0a 5573 6572 2d41 6765 6e74  .*/*..User-Agent
        0x0060:  3a20 4e53 506c 6179 6572 2f34 2e31 2e30  :.NSPlayer/4.1.0
        0x0070:  2e33 3835 360d 0a48 6f73 743a 2044 4d5a  .3856..Host:.DMZ
        0x0080:  5649 4445 4f32 2e61 7068 2e67 6f76 2e61  VIDEO2.aph.gov.a
        0x0090:  753a 3830 0d0a                           u:80..
10:24:10.330956 IP redvideo1.aph.gov.au.www > lund-desktop-2.local.53457: . ack 
99 win 65437 <nop,nop,timestamp 11661612 1404890>
        0x0000:  4530 0034 14c5 4000 7406 cb8c ca0e 5130  E0.4..@.t.....Q0
        0x0010:  0a01 0103 0050 d0d1 d19a 24a5 f13a 9040  .....P....$..:.@
        0x0020:  8010 ff9d a632 0000 0101 080a 00b1 f12c  .....2.........,
        0x0030:  0015 6fda                                ..o.
10:24:10.330990 IP lund-desktop-2.local.53457 > redvideo1.aph.gov.au.www: P 99:3
38(239) ack 1 win 183 <nop,nop,timestamp 1404929 11661612>
        0x0000:  4500 0123 e015 4000 4006 337d 0a01 0103  E..#..@.@.3}....
        0x0010:  ca0e 5130 d0d1 0050 f13a 9040 d19a 24a5  ..Q0...P.:.@..$.
        0x0020:  8018 00b7 5972 0000 0101 080a 0015 7001  ....Yr........p.
        0x0030:  00b1 f12c 5072 6167 6d61 3a20 6e6f 2d63  ...,Pragma:.no-c
        0x0040:  6163 6865 2c72 6174 653d 312e 3030 3030  ache,rate=1.0000
        0x0050:  3030 2c72 6571 7565 7374 2d63 6f6e 7465  00,request-conte
        0x0060:  7874 3d32 0d0a 5072 6167 6d61 3a20 7850  xt=2..Pragma:.xP
        0x0070:  6c61 7953 7472 6d3d 310d 0a50 7261 676d  layStrm=1..Pragm
        0x0080:  613a 2078 436c 6965 6e74 4755 4944 3d7b  a:.xClientGUID={
        0x0090:  6261 6261 6330 3031 2d62 6334 342d 3036  babac001-bc44-06
        0x00a0:  3536 2d33 3362 3039 3838 3331 3635 3834  56-33b0988316584
        0x00b0:  3266 387d 0d0a 5072 6167 6d61 3a20 7374  2f8}..Pragma:.st
        0x00c0:  7265 616d 2d73 7769 7463 682d 636f 756e  ream-switch-coun
        0x00d0:  743d 320d 0a50 7261 676d 613a 2073 7472  t=2..Pragma:.str
        0x00e0:  6561 6d2d 7377 6974 6368 2d65 6e74 7279  eam-switch-entry
        0x00f0:  3d66 6666 663a 313a 3020 6666 6666 3a32  =ffff:1:0.ffff:2
        0x0100:  3a30 2066 6666 663a 333a 3220 0d0a 436f  :0.ffff:3:2...Co
        0x0110:  6e6e 6563 7469 6f6e 3a20 436c 6f73 650d  nnection:.Close.
        0x0120:  0a0d 0a                                  ...
10:24:10.375862 IP redvideo1.aph.gov.au.www > lund-desktop-2.local.53457: P 1:26
5(264) ack 338 win 65198 <nop,nop,timestamp 11661612 1404929>
        0x0000:  4530 013c 14c9 4000 7406 ca80 ca0e 5130  E0.<..@.t.....Q0
        0x0010:  0a01 0103 0050 d0d1 d19a 24a5 f13a 912f  .....P....$..:./
        0x0020:  8018 feae e674 0000 0101 080a 00b1 f12c  .....t.........,
        0x0030:  0015 7001 4854 5450 2f31 2e30 2034 3030  ..p.HTTP/1.0.400
        0x0040:  2042 6164 2052 6571 7565 7374 0d0a 5365  .Bad.Request..Se
        0x0050:  7276 6572 3a20 436f 7567 6172 2f39 2e30  rver:.Cougar/9.0
        0x0060:  312e 3031 2e33 3831 340d 0a44 6174 653a  1.01.3814..Date:
        0x0070:  2046 7269 2c20 3135 204a 756e 2032 3030  .Fri,.15.Jun.200
        0x0080:  3720 3030 3a32 393a 3230 2047 4d54 0d0a  7.00:29:20.GMT..
        0x0090:  5072 6167 6d61 3a20 6e6f 2d63 6163 6865  Pragma:.no-cache
        0x00a0:  0d0a 5375 7070 6f72 7465 643a 2063 6f6d  ..Supported:.com
        0x00b0:  2e6d 6963 726f 736f 6674 2e77 6d2e 7372  .microsoft.wm.sr
        0x00c0:  7670 7061 6972 2c20 636f 6d2e 6d69 6372  vppair,.com.micr
        0x00d0:  6f73 6f66 742e 776d 2e73 7377 6974 6368  osoft.wm.sswitch
        0x00e0:  2c20 636f 6d2e 6d69 6372 6f73 6f66 742e  ,.com.microsoft.
        0x00f0:  776d 2e70 7265 6473 7472 6d2c 2063 6f6d  wm.predstrm,.com
        0x0100:  2e6d 6963 726f 736f 6674 2e77 6d2e 6661  .microsoft.wm.fa
        0x0110:  7374 6361 6368 652c 2063 6f6d 2e6d 6963  stcache,.com.mic
        0x0120:  726f 736f 6674 2e77 6d2e 7374 6172 7475  rosoft.wm.startu
        0x0130:  7070 726f 6669 6c65 0d0a 0d0a            pprofile....

```

and below is the fully functional tcpdump from mplayer:

```

10:05:29.692575 IP lund-desktop-2.local.43909 > redvideo1.aph.gov.au.www: P 1:27
7(276) ack 1 win 183 <nop,nop,timestamp 1124785 0>
        0x0000:  4500 0148 8fed 4000 4006 8380 0a01 0103  E..H..@.@.......
        0x0010:  ca0e 5130 ab85 0050 aad5 a64d 79a5 64ce  ..Q0...P...My.d.
        0x0020:  8018 00b7 66f6 0000 0101 080a 0011 29b1  ....f.........).
        0x0030:  0000 0000 4745 5420 2f48 4d53 3256 2048  ....GET./HMS2V.H
        0x0040:  5454 502f 312e 300d 0a41 6363 6570 743a  TTP/1.0..Accept:
        0x0050:  202a 2f2a 0d0a 5573 6572 2d41 6765 6e74  .*/*..User-Agent
        0x0060:  3a20 4e53 506c 6179 6572 2f34 2e31 2e30  :.NSPlayer/4.1.0
        0x0070:  2e33 3835 360d 0a48 6f73 743a 2044 4d5a  .3856..Host:.DMZ
        0x0080:  5649 4445 4f32 2e61 7068 2e67 6f76 2e61  VIDEO2.aph.gov.a
        0x0090:  753a 3830 0d0a 5072 6167 6d61 3a20 7843  u:80..Pragma:.xC
        0x00a0:  6c69 656e 7447 5549 443d 7b63 3737 6537  lientGUID={c77e7
        0x00b0:  3430 302d 3733 3861 2d31 3164 322d 3961  400-738a-11d2-9a
        0x00c0:  6464 2d30 3032 3061 6630 6133 3237 387d  dd-0020af0a3278}
        0x00d0:  0d0a 5072 6167 6d61 3a20 6e6f 2d63 6163  ..Pragma:.no-cac
        0x00e0:  6865 2c72 6174 653d 312e 3030 3030 3030  he,rate=1.000000
        0x00f0:  2c73 7472 6561 6d2d 7469 6d65 3d30 2c73  ,stream-time=0,s
        0x0100:  7472 6561 6d2d 6f66 6673 6574 3d30 3a30  tream-offset=0:0
        0x0110:  2c72 6571 7565 7374 2d63 6f6e 7465 7874  ,request-context
        0x0120:  3d31 2c6d 6178 2d64 7572 6174 696f 6e3d  =1,max-duration=
        0x0130:  300d 0a43 6f6e 6e65 6374 696f 6e3a 2043  0..Connection:.C
        0x0140:  6c6f 7365 0d0a 0d0a                      lose....
10:05:29.746740 IP redvideo1.aph.gov.au.www > lund-desktop-2.local.43909: . 1:13
69(1368) ack 277 win 65259 <nop,nop,timestamp 11650406 1124785>
        0x0000:  4530 058c 88cf 4000 7406 522a ca0e 5130  E0....@.t.R*..Q0
        0x0010:  0a01 0103 0050 ab85 79a5 64ce aad5 a761  .....P..y.d....a
        0x0020:  8010 feeb 89d7 0000 0101 080a 00b1 c566  ...............f
        0x0030:  0011 29b1 4854 5450 2f31 2e30 2032 3030  ..).HTTP/1.0.200
        0x0040:  204f 4b0d 0a43 6f6e 7465 6e74 2d54 7970  .OK..Content-Typ
        0x0050:  653a 2061 7070 6c69 6361 7469 6f6e 2f76  e:.application/v
        0x0060:  6e64 2e6d 732e 776d 732d 6864 722e 6173  nd.ms.wms-hdr.as
        0x0070:  6676 310d 0a53 6572 7665 723a 2043 6f75  fv1..Server:.Cou
        0x0080:  6761 722f 392e 3031 2e30 312e 3338 3134  gar/9.01.01.3814
        0x0090:  0d0a 436f 6e74 656e 742d 4c65 6e67 7468  ..Content-Length
        0x00a0:  3a20 3535 3230 0d0a 4461 7465 3a20 4672  :.5520..Date:.Fr
        0x00b0:  692c 2031 3520 4a75 6e20 3230 3037 2030  i,.15.Jun.2007.0
        0x00c0:  303a 3130 3a33 3920 474d 540d 0a50 7261  0:10:39.GMT..Pra
        0x00d0:  676d 613a 206e 6f2d 6361 6368 652c 2063  gma:.no-cache,.c
        0x00e0:  6c69 656e 742d 6964 3d33 3938 3830 3439  lient-id=3988049
        0x00f0:  3531 302c 2078 5265 7365 7453 7472 6d3d  510,.xResetStrm=
        0x0100:  312c 2066 6561 7475 7265 733d 2262 726f  1,.features="bro
        0x0110:  6164 6361 7374 220d 0a43 6163 6865 2d43  adcast"..Cache-C
        0x0120:  6f6e 7472 6f6c 3a20 6e6f 2d63 6163 6865  ontrol:.no-cache
        0x0130:  2c20 782d 776d 732d 7374 7265 616d 2d74  ,.x-wms-stream-t
        0x0140:  7970 653d 2262 726f 6164 6361 7374 220d  ype="broadcast".
        0x0150:  0a4c 6173 742d 4d6f 6469 6669 6564 3a20  .Last-Modified:.
        0x0160:  5361 742c 2033 3020 4465 6320 3138 3939  Sat,.30.Dec.1899
        0x0170:  2030 303a 3030 3a30 3020 474d 540d 0a53  .00:00:00.GMT..S
        0x0180:  7570 706f 7274 6564 3a20 636f 6d2e 6d69  upported:.com.mi
        0x0190:  6372 6f73 6f66 742e 776d 2e73 7276 7070  crosoft.wm.srvpp
        0x01a0:  6169 722c 2063 6f6d 2e6d 6963 726f 736f  air,.com.microso
        0x01b0:  6674 2e77 6d2e 7373 7769 7463 682c 2063  ft.wm.sswitch,.c
        0x01c0:  6f6d 2e6d 6963 726f 736f 6674 2e77 6d2e  om.microsoft.wm.
        0x01d0:  7072 6564 7374 726d 2c20 636f 6d2e 6d69  predstrm,.com.mi
        0x01e0:  6372 6f73 6f66 742e 776d 2e66 6173 7463  crosoft.wm.fastc
        0x01f0:  6163 6865 2c20 636f 6d2e 6d69 6372 6f73  ache,.com.micros
        0x0200:  6f66 742e 776d 2e73 7461 7274 7570 7072  oft.wm.startuppr
        0x0210:  6f66 696c 650d 0a0d 0a24 488c 1500 0000  ofile....$H.....
        0x0220:  0000 0c8c 1530 26b2 758e 66cf 11a6 d900  .....0&.u.f.....

```
and it goes on (cause it works).

Does anyone else have any idea about this?

I've tried replacing mms with mmsh but VLC in Fiesty doesn't seem to have this option.

Also why does totem give a poor grey image for this stream?

---

