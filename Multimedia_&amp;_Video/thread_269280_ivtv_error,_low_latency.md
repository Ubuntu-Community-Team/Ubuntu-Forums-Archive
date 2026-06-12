---
title: "ivtv error, low latency"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by Jon &quot;Yogi&quot; on 2006-10-01
I'm trying to install the ivtv files for a hauppauge 250.  When I do dmesg |g[SIZE=3]rep ivt[/SIZE]vI get the following error:

[FONT=Verdana][SIZE=1][/SIZE][/FONT][SIZE=1][47057.398444] ivtv:  ==================== START INIT IVTV ====================
[47057.398587] ivtv:  version 0.4.7 (tagged release) loading
[47057.398682] ivtv:  Linux version: 2.6.15-27-amd64-generic SMP preempt gcc-4.0[47057.398795] ivtv:  In case of problems please include the debug info between
[47057.398905] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[47057.399012] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[47057.399423] ivtv0: Autodetected WinTV PVR 250 card (cx23416 based)
[47057.399747] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[47057.361504] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[47057.399373] tuner 5-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[47057.399378] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[47057.509661] saa7115 5-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[47057.558107] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[47057.526384] ivtv0: i2c attach to card #0 ok [client=MSP4448G-B3, addr=40]
[47057.590776] tda9887 5-0043: chip found @ 0x86 (ivtv i2c driver #0)
[47057.590781] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[47057.849829] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[47057.948870] ivtv0: Encoder revision: 0x02050032
[47057.949342] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[47057.950231]        <ffffffff889b8639>{:ivtv:ivtv_init_buffer+105} <ffffffff889b90db>{:ivtv:ivtv_init_queues_nolock+107}
[47057.950438]        <ffffffff889b978a>{:ivtv:ivtv_stream_alloc+490} <ffffffff889c1f9f>{:ivtv:ivtv_streams_setup+1151}
[47057.950649]        <ffffffff889bc603>{:ivtv:ivtv_probe+7139} <ffffffff80315b42>{thread_return+82}
[47057.951519]        <ffffffff889ba4d7>{:ivtv:module_start+247} <ffffffff8015ce91>{sys_init_module+257}
[47057.960539] ivtv0 warning: No memory on buffer alloc!
[47057.960612] ivtv0 warning: Buffer alloc failed!
[47057.960689] ivtv0: Couldn't allocate buffers for encoder MPEG stream
[47057.960952] ivtv0: Error -12 setting up streams
[47058.016035] ivtv0: Error -12 on initialization
[47058.016043] ivtv: probe of 0000:05:07.0 failed with error -12
[47058.016051] ivtv:  ====================  END INIT IVTV  ====================
[/SIZE]
 Anyone have any ideas?

Jon

---

