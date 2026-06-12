---
title: "The upload speed rate problems about the USB modem"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by huananhu on 2008-12-30
I have a USB modem, it can reach the download speed up to 7.2Mbps and the upload speed up to 5.76Mpbs.

  On the OpenSUSE 11.0, kernel version 2.6.25.5, the system will load the USB serial driver /lib/.../drivers/usb/serial/option.ko for my USB modem device.

  And after dialing up with baud rate 115200, I can get the download speed to be 7.2Mpbs, but however, I can only get the upload speed to be 1.5Mpbs. 

  I modified the option.c code, and changed the out queue length and size as follows:
     
	/* per port private data */
	#define N_IN_URB 4
	-#define N_OUT_URB 1
	+#define N_OUT_URB 4
	#define IN_BUFLEN 4096
	-#define OUT_BUFLEN 128
	+#define OUT_BUFLEN 4096

   Then reload the new option.ko driver for my USB modem, but however, the upload speed is still keeping 1.5Mpbs.
   I don't know why, and I also don't know where the upload speed is limited.

   Can who can tell me why it is? Is it the problems of the kernel driver? Or is it the problems of the system settings?
   Wait for the help urgently!

---

### Post by huananhu on 2008-12-31
My USB modem is a 3G HSUPA data card modem.

The 3G network can support the upload speed up to be 5.76Mpbs, and I can reach this upload speed on Windows XP,
so I think that the network environment will be well.

But on the Ubuntu 8.10 or other Linux system, I can always get the upload speed to be 1.5Mpbs.

So is it perhaps the limits by the Linux system or its kernel?

---

