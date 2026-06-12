---
title: "LIRC odd repeat on release problem"
date: 2010-09-12
forum: Multimedia Software
---

### Post by EricDP on 2010-09-12
I have two remotes, a samsung and a motorola. I created lircd.conf files for each of them. When I use them separately, they each work perfectly but when I merge the two configs, the samsung repeats upon releasing the key. As example, here's the output of irw when pressing the "1" key a single time and holding it for a second:
```
00000198133f817e 00 1 lircd.samsung.homemade
00000198133f817e 01 1 lircd.samsung.homemade
00000198133f817e 02 1 lircd.samsung.homemade
00000198133f817e 03 1 lircd.samsung.homemade
00000198133f817e 04 1 lircd.samsung.homemade
00000198133f817e 05 1 lircd.samsung.homemade
00000198133f817e 06 1 lircd.samsung.homemade
00000198133f817e 00 1 lircd.samsung.homemade
```Notice the count resets to "00" at the end, which causes my applications to interpret this as a second pressing of the button.

The samsung config is:
```
begin remote

  name  lircd.samsung.homemade
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       9103  4378
  one           638  1580
  zero          638   469
  ptrail        644
  repeat       9078  4390
  pre_data_bits   26
  pre_data       0x198133F
  gap          107614
  toggle_bit_mask 0x0

      begin codes
          1                        0x817E
          2                        0x41BE
          3                        0xC13E
          4                        0x21DE
          5                        0xA15E
          6                        0x619E
          7                        0xE11E
          8                        0x11EE
          9                        0x916E
          0                        0x01FE
          left                     0x59A6
          right                    0x9966
          up                       0xE916
          down                     0x19E6
          select                   0xD926
          ent                      0xE51A
          play/pause               0x05FA
          stop                     0x45BA
          exit                     0x25DA
          menu                     0x29D6
          info                     0xF10E
          guide                    0xC53A
          ch+                      0x857A
          ch-                      0xF906
          mode-                    0xC936
          rear+                    0xA956
          rear-                    0x718E
          prevchan                 0x31CE
          rew                      0x39C6
          ff                       0x7986
          on/off                   0x8976
          +10                      0x51AE
          mode+                    0xB946
          sub+                     0x15EA
          sub-                     0xB14E
          ctr+                     0x35CA
          ctr-                     0x6996
      end codes

end remote
```The motorola config is:

```
begin remote

  name  lircd.motorola.homemade
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       9103  4368
  one           587  4391
  zero          587  2151
  ptrail        594
  repeat       9099  2145
  gap          99446
  toggle_bit_mask 0x0

      begin codes
          power                    0x5006
          ok                       0x8807
          ch+                      0xD00A
          ch-                      0x3002
          1                        0x800F
          2                        0x4007
          3                        0xC00B
          4                        0x2003
          5                        0xA00D
          6                        0x6005
          7                        0xE009
          8                        0x1001
          9                        0x900E
          0                        0x0000
          asterisk                 0x6809
          pound                    0x0203
          right                    0xEC06
          left                     0x6C0E
          up                       0x2C09
          down                     0xAC01
          info                     0xCC05
          settings                 0x9806
          guide                    0x0C0B
          page+                    0x5C0C
          page-                    0xDC04
          day+                     0x1C0A
          day-                     0x9C02
          exit                     0x480B
      end codes

end remote
```Any ideas how to stop the repeat-on-release?

---

### Post by EricDP on 2010-09-20
Turns out it was a bug. Christoph was nice enough to make me a patch for 0.8.7 code. If anybody else has a similar problem, here it is:
```
Index: daemons/receive.c
===================================================================
RCS file: /cvsroot/lirc/lirc/daemons/receive.c,v
retrieving revision 5.43
diff -u -u -r5.43 receive.c
--- daemons/receive.c        13 Apr 2010 16:28:10 -0000        5.43
+++ daemons/receive.c        20 Sep 2010 17:49:49 -0000
@@ -57,9 +57,23 @@
         {
                 if(rec_buffer.wptr<RBUF_SIZE)
                 {
-                        lirc_t data;
+                        lirc_t data = 0;
+                        unsigned long elapsed = 0;
                         
-                        data=hw.readdata(maxusec);
+                        if(timerisset(&rec_buffer.last_signal_time))
+                        {
+                                struct timeval current;
+                                
+                                gettimeofday(&current, NULL);
+                                elapsed = time_elapsed
+                                        (&rec_buffer.last_signal_time,
+                                         &current);
+                                
+                        }
+                        if(elapsed < maxusec)
+                        {
+                                data=hw.readdata(maxusec - elapsed);
+                        }
                         if(!data)
                         {
                                 LOGPRINTF(3,"timeout: %u", maxusec);
@@ -76,6 +90,7 @@
                                 return 0;
                         }
 
+                        gettimeofday(&rec_buffer.last_signal_time, NULL);
                         rec_buffer.data[rec_buffer.wptr]=data;
                         if(rec_buffer.data[rec_buffer.wptr]==0) return(0);
                         rec_buffer.sum+=rec_buffer.data[rec_buffer.rptr]
@@ -121,6 +136,7 @@
 {
         int move,i;
 
+        timerclear(&rec_buffer.last_signal_time);
         if(hw.rec_mode==LIRC_MODE_LIRCCODE)
         {
                 unsigned char buffer[sizeof(ir_code)];
Index: daemons/receive.h
===================================================================
RCS file: /cvsroot/lirc/lirc/daemons/receive.h,v
retrieving revision 5.7
diff -u -u -r5.7 receive.h
--- daemons/receive.h        30 May 2010 11:43:35 -0000        5.7
+++ daemons/receive.h        20 Sep 2010 17:49:51 -0000
@@ -33,6 +33,7 @@
         lirc_t pendingp;
         lirc_t pendings;
         lirc_t sum;
+        struct timeval last_signal_time;
 };
 
 static inline lirc_t receive_timeout(lirc_t usec)
```

---

