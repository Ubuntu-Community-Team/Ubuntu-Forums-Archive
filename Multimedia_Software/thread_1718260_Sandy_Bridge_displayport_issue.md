---
title: "Sandy Bridge displayport issue"
date: 2011-03-31
forum: Multimedia Software
---

### Post by mebunto on 2011-03-31
Hello, I'm running Maverick kernel 2.38 and xorg drivers with a Sandy bridge motherboard.  I would like to run a Dell 2560x1600 resolution monitor from the displayport, but, if I connect the monitor to the displayport with an adaptor when booting I get a display issue (doesn't display at all) and I get dmesg logs saying:
```
[   93.736330] [drm:intel_dp_i2c_aux_ch] *ERROR* too many retries, giving up
[   93.739261] [drm:intel_dp_i2c_aux_ch] *ERROR* too many retries, giving up
[   93.742292] [drm:intel_dp_i2c_aux_ch] *ERROR* too many retries, giving up
[   93.745318] [drm:intel_dp_i2c_aux_ch] *ERROR* too many retries, giving up
[   93.823346] [drm:intel_dp_i2c_aux_ch] *ERROR* too many retries, giving up
[   93.826373] [drm:intel_dp_i2c_aux_ch] *ERROR* too many retries, giving up
[   93.829398] [drm:intel_dp_i2c_aux_ch] *ERROR* too many retries, giving up
[   93.832424] [drm:intel_dp_i2c_aux_ch] *ERROR* too many retries, giving up
```

however I'm working around this issue by disconnecting the displayport adaptor on boot, and running a second monitor from the VGA output.  This allows the computer to boot with the vga screen on, then I connect the displayport adaptor, and the big monitor springs into life, full 2560x1600 resolution and everything is wonderful.

It's a real annoyance to crawl on the floor and disconnect the displayport and usb at boot time, then reconnect.

Can anything be done?

Thanks for reading ....

---

### Post by mebunto on 2011-04-01
Anyone out there who's able to help please?  Might this be fixed in Natty?

OK, some more information .... I've found a thread where it looks as though it's been patched, how do I incorporate the patch into my kernel or find an appropriately patched deb?

> linux-image-2.6.37-02063706-generic_2.6.37-02063706.201103281005_amd64.deb

Here's the thread ...

```
The DisplayPort standard (1.1a) states that:
  The I2C-over-AUX Reply field is valid only when Native AUX CH Reply
  field is AUX_ACK (00). When Native AUX CH Reply field is not 00, then,
  I2C-over-AUX Reply field must be 00 and be ignored.

This fixes broken EDID reading when using an active DisplayPort to
duallink DVI converter.  If the AUX CH replier chooses to defer the
transaction, a short read occurs and erroneous data is returned as
the i2c reply due to a lack of length checking and failure to check
for AUX ACK.

As a result, broken EDIDs can look like:
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f    0123456789abcdef
00: bc bc bc ff bc bc bc ff bc bc bc ac bc bc bc 45    ???.???.???????E
10: bc bc bc 10 bc bc bc 34 bc bc bc ee bc bc bc 4c    ???????4???????L
20: bc bc bc 50 bc bc bc 00 bc bc bc 40 bc bc bc 00    ???P???.???@???.
30: bc bc bc 01 bc bc bc 01 bc bc bc a0 bc bc bc 40    ???????????????@
40: bc bc bc 00 bc bc bc 00 bc bc bc 00 bc bc bc 55    ???.???.???.???U
50: bc bc bc 35 bc bc bc 31 bc bc bc 20 bc bc bc fc    ???5???1??? ????
60: bc bc bc 4c bc bc bc 34 bc bc bc 46 bc bc bc 00    ???L???4???F???.
70: bc bc bc 38 bc bc bc 11 bc bc bc 20 bc bc bc 20    ???8??????? ???
80: bc bc bc ff bc bc bc ff bc bc bc ff bc bc bc ff    ???.???.???.???.
...

which can lead to:
[drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder
[drm:drm_edid_block_valid] *ERROR* Raw EDID:
<3>30 30 30 30 30 30 30 32 38 32 30 32 63 63 31 61  000000028202cc1a
<3>28 00 02 8c 00 00 00 00 18 00 00 00 00 00 00 00  (...............
<3>20 4c 61 73 74 20 62 65 61 63 6f 6e 3a 20 33 32   Last beacon: 32
<3>32 30 6d 73 20 61 67 6f 46 00 05 8c 00 00 00 00  20ms agoF.......
<3>36 00 00 00 00 00 00 00 00 0c 57 69 2d 46 69 20  6.........Wi-Fi
<3>52 6f 75 74 65 72 01 08 82 84 8b 96 24 30 48 6c  Router......$0Hl
<3>03 01 01 06 02 00 00 2a 01 00 2f 01 00 32 04 0c  .......*../..2..
<3>12 18 60 dd 09 00 10 18 02 00 00 01 00 00 18 00  ..`.............

Signed-off-by: David Flynn
---
 drivers/gpu/drm/i915/intel_dp.c |   27 +++++++++++++++++++++++----
 1 files changed, 23 insertions(+), 4 deletions(-)

diff --git a/drivers/gpu/drm/i915/intel_dp.c b/drivers/gpu/drm/i915/intel_dp.c
index c8e0055..186cdc7 100644
--- a/drivers/gpu/drm/i915/intel_dp.c
+++ b/drivers/gpu/drm/i915/intel_dp.c
@@ -482,6 +482,7 @@ intel_dp_i2c_aux_ch(struct i2c_adapter *adapter, int mode,
 	int msg_bytes;
 	int reply_bytes;
 	int ret;
+	unsigned retry;
 
 	/* Set up the command byte */
 	if (mode & MODE_I2C_READ)
@@ -513,7 +514,7 @@ intel_dp_i2c_aux_ch(struct i2c_adapter *adapter, int mode,
 		break;
 	}
 
-	for (;;) {
+	for (retry = 5; retry; retry--) {
 	  ret = intel_dp_aux_ch(intel_dp,
 				msg, msg_bytes,
 				reply, reply_bytes);
@@ -521,6 +522,21 @@ intel_dp_i2c_aux_ch(struct i2c_adapter *adapter, int mode,
 			DRM_DEBUG_KMS("aux_ch failed %d\n", ret);
 			return ret;
 		}
+		switch (reply[0] & AUX_NATIVE_REPLY_MASK) {
+		case AUX_NATIVE_REPLY_ACK:
+			/* I2C-over-AUX Reply field is only valid when paired with AUX ACK.*/
+			break;
+		case AUX_NATIVE_REPLY_NACK:
+			DRM_DEBUG_KMS("aux_ch nack\n");
+			return -EREMOTEIO;
+		case AUX_NATIVE_REPLY_DEFER:
+			udelay(100);
+			continue;
+		default:
+			DRM_ERROR("aux_ch invalid reply 0x%02x\n", reply[0]);
+			return -EREMOTEIO;
+		}
+
 		switch (reply[0] & AUX_I2C_REPLY_MASK) {
 		case AUX_I2C_REPLY_ACK:
 			if (mode == MODE_I2C_READ) {
@@ -528,17 +544,20 @@ intel_dp_i2c_aux_ch(struct i2c_adapter *adapter, int mode,
 			}
 			return reply_bytes - 1;
 		case AUX_I2C_REPLY_NACK:
-			DRM_DEBUG_KMS("aux_ch nack\n");
+			DRM_DEBUG_KMS("aux_i2c nack\n");
 			return -EREMOTEIO;
 		case AUX_I2C_REPLY_DEFER:
-			DRM_DEBUG_KMS("aux_ch defer\n");
+			DRM_DEBUG_KMS("aux_i2c defer\n");
 			udelay(100);
 			break;
 		default:
-			DRM_ERROR("aux_ch invalid reply 0x%02x\n", reply[0]);
+			DRM_ERROR("aux_i2c invalid reply 0x%02x\n", reply[0]);
 			return -EREMOTEIO;
 		}
 	}
+
+	DRM_ERROR("too many retries, giving up\n");
+	return -EREMOTEIO;
 }
 
 static int
-- 
1.7.1
```

Thanks

---

### Post by mebunto on 2011-04-03
Added more info in previous post, can anyone help please?

Thanks

---

### Post by mebunto on 2011-05-04
Won't be fixed so I'm closing it.
natty doesn't work (yet)

---

