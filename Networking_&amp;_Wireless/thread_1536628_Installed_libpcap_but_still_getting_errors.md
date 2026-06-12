---
title: "Installed libpcap but still getting errors"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by bramier1981 on 2010-07-22
Good afternoon,

I am trying to install Wireshark but am getting build errors from it. Libpcap seemed to config/make/install fine, so I'm a little baffled as far as what to do now. I AM using a wireless usb adapter, so that might be what's giving me problems [at least that's my logical guess]

lign -Wformat-security -I/usr/local/include -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -I/usr/local/include -MT wireshark-capture-pcap-util.o -MD -MP -MF ".deps/wireshark-capture-pcap-util.Tpo" -c -o wireshark-capture-pcap-util.o `test -f 'capture-pcap-util.c' || echo './'`capture-pcap-util.c; \
    then mv -f ".deps/wireshark-capture-pcap-util.Tpo" ".deps/wireshark-capture-pcap-util.Po"; else rm -f ".deps/wireshark-capture-pcap-util.Tpo"; exit 1; fi
capture-pcap-util.c:399: error: static declaration of ‘pcap_datalink_name_to_val’ follows non-static declaration
/usr/local/include/pcap/pcap.h:326: note: previous declaration of ‘pcap_datalink_name_to_val’ was here
capture-pcap-util.c:414: error: static declaration of ‘pcap_datalink_val_to_name’ follows non-static declaration
/usr/local/include/pcap/pcap.h:327: note: previous declaration of ‘pcap_datalink_val_to_name’ was here
make[2]: *** [wireshark-capture-pcap-util.o] Error 1
make[2]: Leaving directory `/home/doug/Downloads/wireshark-1.2.9'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/doug/Downloads/wireshark-1.2.9'
make: *** [install] Error 2


Thanks for any help

---

