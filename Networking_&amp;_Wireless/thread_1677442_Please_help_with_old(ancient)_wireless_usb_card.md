---
title: "Please help with old(ancient) wireless usb card"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by lellyville on 2011-01-28
so i was googeling on how to get this gigafast usb card to work
 
so i downloaded the zd1211 driver from sourceforge and followed the steps here 
[https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211](https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211)

but when I do makefile i get a bunch of errors similar to 
[http://ubuntuforums.org/showthread.php?t=77584](http://ubuntuforums.org/showthread.php?t=77584) back in 2005

[I]"
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6380: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_ioctl_setrts&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6448: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_ioctl_setfrag&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6469: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_ioctl_getfrag&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6494: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_ioctl_getrate&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6518: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_ioctl_setpower&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6640: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_ioctl_getpower&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6669: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_ioctl_setmode&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6699: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205wext_giwfreq&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6801: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205wext_giwmode&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6817: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205wext_giwrts&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6863: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205wext_commit&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6983: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205wext_siwscan&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:6997: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_translate_scan&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7125: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
include/net/iw_handler.h:517: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7125: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
include/net/iw_handler.h:517: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7125: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;unsigned int&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7125: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7135: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7135: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7135: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;U8 *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7135: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7147: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
include/net/iw_handler.h:517: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7147: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
include/net/iw_handler.h:517: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7147: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;unsigned int&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7147: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7160: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
include/net/iw_handler.h:517: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7160: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
include/net/iw_handler.h:517: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7160: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;unsigned int&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7160: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7183: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;U32&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7183: warning: unknown conversion type character &#8216;,&#8217; in format
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7183: warning: spurious trailing &#8216;%&#8217; in format
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7185: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7185: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7185: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7185: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7196: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7196: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7196: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;U8 *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7196: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7214: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
include/net/iw_handler.h:569: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7214: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
include/net/iw_handler.h:569: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7214: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast
include/net/iw_handler.h:569: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;unsigned int&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7214: error: too few arguments to function &#8216;iwe_stream_add_value&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7223: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
include/net/iw_handler.h:569: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7223: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
include/net/iw_handler.h:569: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7223: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast
include/net/iw_handler.h:569: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;unsigned int&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7223: error: too few arguments to function &#8216;iwe_stream_add_value&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7239: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7239: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7239: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7239: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7258: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7258: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7258: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7258: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7270: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_request_info *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7270: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;char *&#8217; but argument is of type &#8216;struct iw_event *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7270: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
include/net/iw_handler.h:542: note: expected &#8216;struct iw_event *&#8217; but argument is of type &#8216;char *&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7270: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205wext_giwscan&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7284: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_list_bss&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7388: warning: format &#8216;%2d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;U32&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7388: warning: spurious trailing &#8216;%&#8217; in format
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1211_set_auth_param&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7531: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_ioctl&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:7763: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_init&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:8517: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_setup_next_send&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:8962: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_rx_ind&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9390: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9403: error: implicit declaration of function &#8216;eth_copy_and_sum&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_status_notify&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9438: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;chal_tout_cb&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9538: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;scan_tout_cb&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9549: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;asoc_tout_cb&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9560: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;auth_tout_cb&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9571: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_start_timer&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9581: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_stop_timer&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9628: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_dis_intr&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9654: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_set_intr_mask&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9671: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_check_tcb_avail&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9700: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_delay_us&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9723: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_AcquireDoNotSleep&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9757: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zdcb_ReleaseDoNotSleep&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:9763: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;CalculateQuality&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:10074: warning: unused variable &#8216;rxOffset&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;ChangeMacMode&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:10361: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:10362: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: In function &#8216;zd1205_iw_getstats&#8217;:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:10384: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c: At top level:
/home/yan/Downloads/zd1211-driver-r83/src/zd1205.c:10395: fatal error: opening dependency file /home/yan/Downloads/zd1211-driver-r83/src/.zd1205.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/yan/Downloads/zd1211-driver-r83/src/zd1205.o] Error 1
make[1]: *** [_module_/home/yan/Downloads/zd1211-driver-r83] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-22-generic'
make: *** [all] Error 2
"[/I]

How do i install this beast? 

i did build essential and made sure everything is updated, btw i'm running 9.10 or 9.04 dont recall on my parent's PC.


Please Help!

Thanks:popcorn:

---

### Post by chili555 on 2011-01-28
May we take a look at:```
uname -r
modinfo zd1211rw |  grep -i version
lsusb
```Maybe we can find an easier way.

---

### Post by lellyville on 2011-01-29
hey this is what i get after running those commands

yan@yan-desktop:~$ uname -r
2.6.31-22-generic
yan@yan-desktop:~$ modinfo zd1211rw |  grep -i version
version:        1.0
srcversion:     891EB6D7C8EF72E1D24FD0E
vermagic:       2.6.31-22-generic SMP mod_unload modversions 586 
yan@yan-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


also tried

[http://ubuntuforums.org/showthread.php?t=283254](http://ubuntuforums.org/showthread.php?t=283254)

still failed :(

---

### Post by chili555 on 2011-01-29
> $ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubThere is nothing here that is a USB wireless device? Did you have it inserted at the time or is it electrically defective?

---

### Post by lellyville on 2011-01-30
i inserted it when i did lsusb 

i'm confused why it's not detecting :(

---

### Post by chili555 on 2011-01-30
I suspect that either the card or the USB port is defective. You might look over:```
sudo lsusb -v
```See if there are any obvious signs of distress. Did you try a different USB slot?

You might also look at:```
sudo tail -f /var/log/syslog
```Leave the terminal open as you remove and reinsert the device. Any signs of activity?

---

### Post by andrez1 on 2011-02-07
As said chili555, You might also look at: sudo tail -f /var/log/syslog.

[Info about Wireless USB Card]("http://wirelessusbcard.net")

---

