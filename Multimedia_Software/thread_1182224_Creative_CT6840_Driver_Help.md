---
title: "Creative CT6840 Driver Help"
date: 2009-06-08
forum: Multimedia Software
---

### Post by illbashu on 2009-06-08
I tried to install the [http://alpha.dyndns.org/ov511/](http://alpha.dyndns.org/ov511/) drivers but i just get an error. Is there any drivers in the repo for this cam? 

```
 
ov511.c:429: error: &#8216;PAGE_SIZE&#8217; undeclared (first use in this function)
ov511.c:430: warning: implicit declaration of function &#8216;__pa&#8217;
ov511.c: In function &#8216;rvmalloc&#8217;:
ov511.c:440: error: &#8216;PAGE_SIZE&#8217; undeclared (first use in this function)
ov511.c:448: warning: implicit declaration of function &#8216;mem_map_reserve&#8217;
ov511.c: In function &#8216;rvfree&#8217;:
ov511.c:466: warning: implicit declaration of function &#8216;mem_map_unreserve&#8217;
ov511.c:467: error: &#8216;PAGE_SIZE&#8217; undeclared (first use in this function)
ov511.c: In function &#8216;reg_w&#8217;:
ov511.c:865: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:877: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;reg_r&#8217;:
ov511.c:897: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:900: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov518_reg_w32&#8217;:
ov511.c:948: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:962: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov511_upload_quan_tables&#8217;:
ov511.c:976: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov518_upload_quan_tables&#8217;:
ov511.c:1016: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_reset&#8217;:
ov511.c:1056: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1062: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov518_i2c_write_internal&#8217;:
ov511.c:1085: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov511_i2c_write_internal&#8217;:
ov511.c:1110: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1137: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov518_i2c_read_internal&#8217;:
ov511.c:1169: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov511_i2c_read_internal&#8217;:
ov511.c:1202: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1225: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1232: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;i2c_w_slave&#8217;:
ov511.c:1369: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;i2c_r_slave&#8217;:
ov511.c:1397: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;write_regvals&#8217;:
ov511.c:1436: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;dump_i2c_range&#8217;:
ov511.c:1452: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;dump_i2c_regs&#8217;:
ov511.c:1459: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;dump_reg_range&#8217;:
ov511.c:1470: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov511_dump_regs&#8217;:
ov511.c:1477: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1479: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1481: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1483: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1486: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1488: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1491: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov518_dump_regs&#8217;:
ov511.c:1503: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1505: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1507: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1509: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1511: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1513: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1515: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1517: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1519: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1521: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_stop&#8217;:
ov511.c:1533: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_restart&#8217;:
ov511.c:1547: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_wait_frames_inactive&#8217;:
ov511.c:1564: error: &#8216;current&#8217; undeclared (first use in this function)
ov511.c: In function &#8216;ov51x_clear_snapshot&#8217;:
ov511.c:1576: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1578: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;init_ov_sensor&#8217;:
ov511.c:1639: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov511_set_packet_size&#8217;:
ov511.c:1661: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1674: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1678: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1682: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1688: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov518_set_packet_size&#8217;:
ov511.c:1724: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1728: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1732: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1744: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov511_init_compression&#8217;:
ov511.c:1778: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov518_init_compression&#8217;:
ov511.c:1797: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_contrast&#8217;:
ov511.c:1816: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1860: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_get_contrast&#8217;:
ov511.c:1909: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1913: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_brightness&#8217;:
ov511.c:1927: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1956: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_get_brightness&#8217;:
ov511.c:1992: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:1996: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_saturation&#8217;:
ov511.c:2010: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2040: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_get_saturation&#8217;:
ov511.c:2088: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2092: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_hue&#8217;:
ov511.c:2106: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2142: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_get_hue&#8217;:
ov511.c:2183: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2187: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_picture&#8217;:
ov511.c:2200: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_get_picture&#8217;:
ov511.c:2231: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_led_control&#8217;:
ov511.c:2341: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_light_freq&#8217;:
ov511.c:2365: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2372: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2396: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2399: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_banding_filter&#8217;:
ov511.c:2422: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2426: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_auto_brightness&#8217;:
ov511.c:2450: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2454: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_auto_exposure&#8217;:
ov511.c:2476: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2492: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2495: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_backlight&#8217;:
ov511.c:2514: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2536: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2539: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;sensor_set_mirror&#8217;:
ov511.c:2551: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2563: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2566: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov_sensor_mode_setup&#8217;:
ov511.c:2821: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2860: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2880: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2885: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov511_mode_init_regs&#8217;:
ov511.c:2905: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2918: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2925: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:2930: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov518_mode_init_regs&#8217;:
ov511.c:2998: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3002: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3007: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3014: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;mode_init_regs&#8217;:
ov511.c:3157: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_set_default_params&#8217;:
ov511.c:3221: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;decoder_set_input&#8217;:
ov511.c:3242: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;decoder_set_norm&#8217;:
ov511.c:3286: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;request_decompressor&#8217;:
ov511.c:3614: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3623: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3626: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3629: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3633: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3636: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3639: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3642: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3651: warning: implicit declaration of function &#8216;__MOD_INC_USE_COUNT&#8217;
ov511.c: In function &#8216;release_decompressor&#8217;:
ov511.c:3674: warning: implicit declaration of function &#8216;__MOD_DEC_USE_COUNT&#8217;
ov511.c:3683: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;decompress&#8217;:
ov511.c:3694: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3705: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3698: warning: unused variable &#8216;ret&#8217;
ov511.c:3715: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3708: warning: unused variable &#8216;ret&#8217;
ov511.c:3717: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;deinterlace&#8217;:
ov511.c:3844: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3847: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:3852: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_postprocess_yuv420&#8217;:
ov511.c:3974: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_postprocess&#8217;:
ov511.c:4020: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4039: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov511_move_data&#8217;:
ov511.c:4075: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4095: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4122: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4124: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4131: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4138: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4144: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4155: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4174: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4182: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4211: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4055: warning: unused variable &#8216;pnum&#8217;
ov511.c: In function &#8216;ov518_move_data&#8217;:
ov511.c:4236: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4241: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4245: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4257: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4289: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4291: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4296: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4301: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4319: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4329: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4362: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_isoc_irq&#8217;:
ov511.c:4378: error: &#8216;struct urb&#8217; has no member named &#8216;context&#8217;
ov511.c:4379: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4383: error: &#8216;struct urb&#8217; has no member named &#8216;context&#8217;
ov511.c:4387: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4392: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4396: error: &#8216;struct urb&#8217; has no member named &#8216;status&#8217;
ov511.c:4396: error: &#8216;struct urb&#8217; has no member named &#8216;status&#8217;
ov511.c:4397: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4401: error: &#8216;struct urb&#8217; has no member named &#8216;status&#8217;
ov511.c:4401: error: &#8216;struct urb&#8217; has no member named &#8216;status&#8217;
ov511.c:4402: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4407: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4409: error: &#8216;struct urb&#8217; has no member named &#8216;number_of_packets&#8217;
ov511.c:4412: error: &#8216;struct urb&#8217; has no member named &#8216;iso_frame_desc&#8217;
ov511.c:4413: error: &#8216;struct urb&#8217; has no member named &#8216;iso_frame_desc&#8217;
ov511.c:4416: error: &#8216;struct urb&#8217; has no member named &#8216;iso_frame_desc&#8217;
ov511.c:4417: error: &#8216;struct urb&#8217; has no member named &#8216;iso_frame_desc&#8217;
ov511.c:4419: error: &#8216;struct urb&#8217; has no member named &#8216;transfer_buffer&#8217;
ov511.c:4420: error: &#8216;struct urb&#8217; has no member named &#8216;iso_frame_desc&#8217;
ov511.c:4423: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4428: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4436: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4444: error: &#8216;struct urb&#8217; has no member named &#8216;dev&#8217;
ov511.c:4450: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_init_isoc&#8217;:
ov511.c:4467: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4476: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4486: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4495: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4499: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4508: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4515: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4522: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4534: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4538: error: &#8216;struct urb&#8217; has no member named &#8216;dev&#8217;
ov511.c:4539: error: &#8216;struct urb&#8217; has no member named &#8216;context&#8217;
ov511.c:4540: error: &#8216;struct urb&#8217; has no member named &#8216;pipe&#8217;
ov511.c:4542: error: &#8216;struct urb&#8217; has no member named &#8216;transfer_flags&#8217;
ov511.c:4546: error: &#8216;struct urb&#8217; has no member named &#8216;transfer_buffer&#8217;
ov511.c:4547: error: &#8216;struct urb&#8217; has no member named &#8216;complete&#8217;
ov511.c:4548: error: &#8216;struct urb&#8217; has no member named &#8216;number_of_packets&#8217;
ov511.c:4549: error: &#8216;struct urb&#8217; has no member named &#8216;transfer_buffer_length&#8217;
ov511.c:4550: error: &#8216;struct urb&#8217; has no member named &#8216;interval&#8217;
ov511.c:4552: error: &#8216;struct urb&#8217; has no member named &#8216;iso_frame_desc&#8217;
ov511.c:4553: error: &#8216;struct urb&#8217; has no member named &#8216;iso_frame_desc&#8217;
ov511.c:4560: error: &#8216;struct urb&#8217; has no member named &#8216;dev&#8217;
ov511.c:4567: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_stop_isoc&#8217;:
ov511.c:4596: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_new_frame&#8217;:
ov511.c:4614: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4630: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_do_dealloc&#8217;:
ov511.c:4668: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4703: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4705: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_alloc&#8217;:
ov511.c:4717: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4745: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4760: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4766: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4771: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_dealloc&#8217;:
ov511.c:4778: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4782: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_v4l1_open&#8217;:
ov511.c:4799: warning: implicit declaration of function &#8216;video_devdata&#8217;
ov511.c:4799: warning: initialization makes pointer from integer without a cast
ov511.c:4801: error: dereferencing pointer to incomplete type
ov511.c:4809: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4851: error: &#8216;struct file&#8217; has no member named &#8216;private_data&#8217;
ov511.c: In function &#8216;ov51x_v4l1_close&#8217;:
ov511.c:4876: error: &#8216;struct file&#8217; has no member named &#8216;private_data&#8217;
ov511.c:4878: error: dereferencing pointer to incomplete type
ov511.c:4880: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4920: error: &#8216;struct file&#8217; has no member named &#8216;private_data&#8217;
ov511.c: In function &#8216;ov51x_v4l1_ioctl_internal&#8217;:
ov511.c:4935: error: &#8216;struct file&#8217; has no member named &#8216;private_data&#8217;
ov511.c:4936: error: dereferencing pointer to incomplete type
ov511.c:4938: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4948: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4967: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4970: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:4988: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5002: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5007: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5025: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5042: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5051: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5058: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5068: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5082: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5091: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5122: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5162: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5171: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5192: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5197: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5203: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5209: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5214: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5219: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5229: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5253: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5264: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5270: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5283: error: &#8216;current&#8217; undeclared (first use in this function)
ov511.c:5324: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5334: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5365: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_v4l1_ioctl&#8217;:
ov511.c:5449: error: &#8216;struct file&#8217; has no member named &#8216;private_data&#8217;
ov511.c:5450: error: dereferencing pointer to incomplete type
ov511.c:5456: warning: implicit declaration of function &#8216;video_usercopy&#8217;
ov511.c: In function &#8216;ov51x_v4l1_read&#8217;:
ov511.c:5472: error: &#8216;struct file&#8217; has no member named &#8216;private_data&#8217;
ov511.c:5473: error: &#8216;struct file&#8217; has no member named &#8216;f_flags&#8217;
ov511.c:5476: error: dereferencing pointer to incomplete type
ov511.c:5483: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5520: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5534: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5535: error: &#8216;current&#8217; undeclared (first use in this function)
ov511.c:5542: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5543: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5547: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5549: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5558: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5562: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5577: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5589: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5590: warning: implicit declaration of function &#8216;copy_to_user&#8217;
ov511.c:5591: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5597: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5609: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5614: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_v4l1_mmap&#8217;:
ov511.c:5639: error: &#8216;struct file&#8217; has no member named &#8216;private_data&#8217;
ov511.c:5644: error: dereferencing pointer to incomplete type
ov511.c:5650: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:5654: error: &#8216;PAGE_SIZE&#8217; undeclared (first use in this function)
ov511.c:5664: warning: implicit declaration of function &#8216;remap_page_range&#8217;
ov511.c:5665: error: &#8216;PAGE_SHARED&#8217; undeclared (first use in this function)
ov511.c: At top level:
ov511.c:5705: warning: initialization from incompatible pointer type
ov511.c:5711: error: variable &#8216;vdev_template&#8217; has initializer but incomplete type
ov511.c:5712: error: unknown field &#8216;owner&#8217; specified in initializer
ov511.c:5712: warning: excess elements in struct initializer
ov511.c:5712: warning: (near initialization for &#8216;vdev_template&#8217;)
ov511.c:5713: error: unknown field &#8216;name&#8217; specified in initializer
ov511.c:5713: warning: excess elements in struct initializer
ov511.c:5713: warning: (near initialization for &#8216;vdev_template&#8217;)
ov511.c:5714: error: unknown field &#8216;type&#8217; specified in initializer
ov511.c:5714: warning: excess elements in struct initializer
ov511.c:5714: warning: (near initialization for &#8216;vdev_template&#8217;)
ov511.c:5715: error: unknown field &#8216;hardware&#8217; specified in initializer
ov511.c:5715: error: &#8216;VID_HARDWARE_OV511&#8217; undeclared here (not in a function)
ov511.c:5715: warning: excess elements in struct initializer
ov511.c:5715: warning: (near initialization for &#8216;vdev_template&#8217;)
ov511.c:5716: error: unknown field &#8216;fops&#8217; specified in initializer
ov511.c:5716: warning: excess elements in struct initializer
ov511.c:5716: warning: (near initialization for &#8216;vdev_template&#8217;)
ov511.c: In function &#8216;ov7xx0_configure&#8217;:
ov511.c:6056: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6059: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6060: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6061: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6062: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6063: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6065: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6072: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6075: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6080: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6082: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6092: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6095: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6100: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6104: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov6xx0_configure&#8217;:
ov511.c:6260: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6263: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6264: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6267: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6274: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6280: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6283: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6286: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6289: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6305: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6309: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ks0127_configure&#8217;:
ov511.c:6326: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6331: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6334: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6336: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6339: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6343: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;saa7111a_configure&#8217;:
ov511.c:6407: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6416: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6419: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6428: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov511_configure&#8217;:
ov511.c:6470: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6474: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6478: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6480: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6483: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6484: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6485: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6486: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6504: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6515: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6522: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6529: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6536: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6543: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6549: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6553: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6559: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6564: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6569: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6575: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6583: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov518_configure&#8217;:
ov511.c:6639: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6642: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6662: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6670: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6677: warning: initialization from incompatible pointer type
ov511.c:6678: error: &#8216;struct usb_host_endpoint&#8217; has no member named &#8216;wMaxPacketSize&#8217;
ov511.c:6716: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6719: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6724: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6730: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6745: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_probe&#8217;:
ov511.c:6775: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6782: warning: assignment from incompatible pointer type
ov511.c:6828: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6871: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6875: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6881: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6896: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6940: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
ov511.c:6949: warning: implicit declaration of function &#8216;video_register_device&#8217;
ov511.c:6949: error: &#8216;VFL_TYPE_GRABBER&#8217; undeclared (first use in this function)
ov511.c:6962: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:6967: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:7006: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:7017: error: invalid storage class for function &#8216;ov51x_disconnect&#8217;
ov511.c: In function &#8216;ov51x_disconnect&#8217;:
ov511.c:7030: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:7045: warning: implicit declaration of function &#8216;video_unregister_device&#8217;
ov511.c:7047: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:7083: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_probe&#8217;:
ov511.c:7088: error: unknown field &#8216;owner&#8217; specified in initializer
ov511.c:7088: warning: initialization from incompatible pointer type
ov511.c:7096: error: initializer element is not constant
ov511.c:7096: error: (near initialization for &#8216;ov511_driver.disconnect&#8217;)
ov511.c: In function &#8216;ov511_register_decomp_module&#8217;:
ov511.c:7110: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:7111: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:7112: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:7119: error: &#8216;cpu_has_mmx&#8217; undeclared (first use in this function)
ov511.c:7120: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c:7152: error: &#8216;MOD_INC_USE_COUNT&#8217; undeclared (first use in this function)
ov511.c: In function &#8216;ov511_deregister_decomp_module&#8217;:
ov511.c:7179: error: &#8216;MOD_DEC_USE_COUNT&#8217; undeclared (first use in this function)
ov511.c: In function &#8216;ov51x_probe&#8217;:
ov511.c:7186: error: invalid storage class for function &#8216;usb_ov511_init&#8217;
ov511.c: In function &#8216;usb_ov511_init&#8217;:
ov511.c:7201: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_probe&#8217;:
ov511.c:7208: error: invalid storage class for function &#8216;usb_ov511_exit&#8217;
ov511.c: In function &#8216;usb_ov511_exit&#8217;:
ov511.c:7210: error: expected &#8216;)&#8217; before &#8216;KBUILD_MODNAME&#8217;
ov511.c: In function &#8216;ov51x_probe&#8217;:
ov511.c:7215: error: invalid storage class for function &#8216;__inittest&#8217;
ov511.c:7215: warning: &#8216;alias&#8217; attribute ignored
ov511.c:7216: error: invalid storage class for function &#8216;__exittest&#8217;
ov511.c:7216: warning: &#8216;alias&#8217; attribute ignored
ov511.c:7219: error: expected declaration or statement at end of input
make: *** [ov511.o] Error 1

```

---

### Post by illbashu on 2009-06-09
bump!!!!!!!!!!!!

---

### Post by 484northern on 2009-06-21
This post is for a different model but I was able to get my ct6840 to work [http://ubuntuforums.org/showthread.php?t=1128335]("http://ubuntuforums.org/showthread.php?t=1128335")

---

### Post by sohail.1979 on 2010-02-21
do you want [creative ct6840 driver xp]("http://www.driversbag.com/creative%20webcam%20driver%20ct6840.htm") please visit the url

---

