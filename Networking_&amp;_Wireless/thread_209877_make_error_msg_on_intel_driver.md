---
title: "make error msg on intel driver"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by jaden403 on 2006-07-05
I have been able to make and install all the appropriate files from sourceforge except for ipw3945-1.0.0.  I get the following error when I run make from that directory:

```

mkdir -p /home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/tmp/.tmp_versions
cp /lib/modules/2.6.15-25-386/net/ieee80211/.tmp_versions/*.mod /home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/tmp/.tmp_versions
make -C /lib/modules/2.6.15-25-386/build M=/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0 MODVERDIR=/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
  CC [M]  /home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.o
/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.c: In function ‘ipw_send_associate’:
/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.c:3874: error: too few arguments to function ‘ieee80211_tx_frame’
/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.c: In function ‘ipw_bg_daemon_cmd’:
/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.c:4319: error: too few arguments to function ‘ieee80211_tx_frame’
/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.c: In function ‘ipw_auth_work’:
/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.c:8698: error: too few arguments to function ‘ieee80211_tx_frame’
/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.c:8742: error: too few arguments to function ‘ieee80211_tx_frame’
/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.c: In function ‘ipw_handle_probe_request’:
/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.c:8813: error: too few arguments to function ‘ieee80211_tx_frame’
make[2]: *** [/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0/ipw3945.o] Error 1
make[1]: *** [_module_/home/joshua/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
make: *** [modules] Error 2

```

Any suggestions....

---

