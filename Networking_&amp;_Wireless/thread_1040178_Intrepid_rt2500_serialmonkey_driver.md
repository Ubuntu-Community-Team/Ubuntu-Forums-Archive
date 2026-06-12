---
title: "Intrepid rt2500 serialmonkey driver"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by zanophol on 2009-01-15
I set out on a foolish quest to make a linux box all-in-one NAS/DHCP/DNS/Firewall/WirelessAP box. Guess which part doesn't yet work? The wireless AP part, of course.

I have this card:
00:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI

I have this kernel:
2.6.27-11-generic

The mainline kernel module will not allow this card to enter Master mode. The enhanced legacy rt61 driver from serialmonkey will not allow it to use Master mode either. Hence, my need to download and compile the rt2500 driver from serialmonkey. This is for two reasons.

The rt2500.tar.bz2 tarball in the repository is from 06/24/2008. It is now old, and it will not compile with this error:

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /usr/src/modules/rt2500/rtmp_main.o
  CC [M]  /usr/src/modules/rt2500/mlme.o
  CC [M]  /usr/src/modules/rt2500/connect.o
  CC [M]  /usr/src/modules/rt2500/sync.o
  CC [M]  /usr/src/modules/rt2500/assoc.o
  CC [M]  /usr/src/modules/rt2500/auth.o
  CC [M]  /usr/src/modules/rt2500/auth_rsp.o
  CC [M]  /usr/src/modules/rt2500/rtmp_data.o
  CC [M]  /usr/src/modules/rt2500/rtmp_init.o
  CC [M]  /usr/src/modules/rt2500/sanity.o
  CC [M]  /usr/src/modules/rt2500/rtmp_wep.o
  CC [M]  /usr/src/modules/rt2500/wpa.o
  CC [M]  /usr/src/modules/rt2500/md5.o
  CC [M]  /usr/src/modules/rt2500/rtmp_tkip.o
  CC [M]  /usr/src/modules/rt2500/rtmp_info.o
/usr/src/modules/rt2500/rtmp_info.c: In function ‘rt_ioctl_giwscan’:
/usr/src/modules/rt2500/rtmp_info.c:494: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:494: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:494: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/modules/rt2500/rtmp_info.c:494: error: too few arguments to function ‘iwe_stream_add_event’
/usr/src/modules/rt2500/rtmp_info.c:512: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:512: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:512: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/modules/rt2500/rtmp_info.c:512: error: too few arguments to function ‘iwe_stream_add_event’
/usr/src/modules/rt2500/rtmp_info.c:518: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:518: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:518: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:518: error: too few arguments to function ‘iwe_stream_add_point’
/usr/src/modules/rt2500/rtmp_info.c:526: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:526: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:526: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:526: error: too few arguments to function ‘iwe_stream_add_point’
/usr/src/modules/rt2500/rtmp_info.c:539: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:539: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:539: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/usr/src/modules/rt2500/rtmp_info.c:539: error: too few arguments to function ‘iwe_stream_add_value’
/usr/src/modules/rt2500/rtmp_info.c:550: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:550: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:550: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/modules/rt2500/rtmp_info.c:550: error: too few arguments to function ‘iwe_stream_add_event’
/usr/src/modules/rt2500/rtmp_info.c:562: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:562: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:562: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/modules/rt2500/rtmp_info.c:562: error: too few arguments to function ‘iwe_stream_add_event’
make[2]: *** [/usr/src/modules/rt2500/rtmp_info.o] Error 1
make[1]: *** [_module_/usr/src/modules/rt2500] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
rt2500.ko failed to build!
make: *** [module] Error 1

For this reason, I am trying to download the serialmonkey drivers. However, do to something with their instructions and Ubuntu, I cannot follow their overly complex method for grabbing cvs code. The webpage is [http://rt2x00.serialmonkey.com/wiki/index.php?title=Rt2x00_GIT_instructions](http://rt2x00.serialmonkey.com/wiki/index.php?title=Rt2x00_GIT_instructions). I have cogito and git installed from the repos. If I try Step 3 part 1 (cg clone git://git.kernel.org/pub/scm/linux/kernel/git/ivd/rt2x00.git/), I get this error:

cg clone git://git.kernel.org/pub/scm/linux/kernel/git/ivd/rt2x00.git/
error: No files to search found.

Can someone point me in the right direction for grabbing the latest driver?

---

### Post by zanophol on 2009-01-15
I should point out that I need the driver from the "Next-generation rt2x00 drivers" section. The "Enhanced Legacy driver" will not work for what I am trying to accomplish: master mode operation.

---

