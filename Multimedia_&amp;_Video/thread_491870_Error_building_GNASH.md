---
title: "Error building GNASH"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by mahingupta on 2007-07-04
Hi all,
I am getting following error  when I try to build GNash 0.8.0

make[2]: Entering directory `/root/gnash-0.8.0/utilities'
/bin/sh ../libtool --tag=CXX --mode=link g++  -g -O2 -pthread     -W     -Wall     -Wcast-align     -Wcast-qual     -Wpointer-arith     -Wreturn-type      -ldl -lltdl  -lxml2 -lz -lm  -lcurl -L/usr/local/lib -lboost_date_time-gcc-mt -lboost_thread-gcc-mt -lpthread   -o gparser -export-dynamic -lltdl parser.o ../server/libgnashserver.la ../libbase/libgnashbase.la ../backend/libgnashbackend.la ../libamf/libgnashamf.la   -lglib-2.0     -lrt -lm
g++ -g -O2 -pthread -W -Wall -Wcast-align -Wcast-qual -Wpointer-arith -Wreturn-type -o .libs/gparser parser.o -Wl,--export-dynamic  -L/usr/local/lib ../server/.libs/libgnashserver.so ../libbase/.libs/libgnashbase.so ../backend/.libs/libgnashbackend.so /root/gnash-0.8.0/server/.libs/libgnashserver.so /root/gnash-0.8.0/libamf/.libs/libgnashamf.so /root/gnash-0.8.0/libgeometry/.libs/libgnashgeo.so /usr/lib/libxml2.so /usr/lib/libSDL.so -L/usr/X11R6/lib -lX11 -lXext -lpangox-1.0 -lpango-1.0 -latk-1.0 -lgobject-2.0 -lgmodule-2.0 ../libamf/.libs/libgnashamf.so /root/gnash-0.8.0/libbase/.libs/libgnashbase.so /usr/lib/libjpeg.so /usr/local/lib/libcurl.so -lssl -lcrypto -lz /usr/lib/libltdl.so -ldl -lboost_date_time-gcc-mt -lboost_thread-gcc-mt -lpthread -lglib-2.0 -lrt -lm -Wl,--rpath -Wl,/usr/local/lib
../backend/.libs/libgnashbackend.so: undefined reference to `agg::vcgen_stroke::add_vertex(double, double, unsigned)'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::g_elder_bit_table'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::vcgen_stroke::remove_all()'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::curve4_div::init(double, double, double, double, double, double, double, double)'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::curve3_div::init(double, double, double, double, double, double)'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::curve3_inc::init(double, double, double, double, double, double)'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::curve3_inc::vertex(double*, double*)'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::curve4_inc::vertex(double*, double*)'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::trans_affine::multiply(agg::trans_affine const&)'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::g_sqrt_table'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::vcgen_stroke::vertex(double*, double*)'
../server/.libs/libgnashserver.so: undefined reference to `xmlReadIO'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::trans_affine::invert()'
../server/.libs/libgnashserver.so: undefined reference to `xmlReadMemory'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::curve4_inc::init(double, double, double, double, double, double, double, double)'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::vcgen_stroke::rewind(unsigned)'
../backend/.libs/libgnashbackend.so: undefined reference to `agg::vcgen_stroke::vcgen_stroke[in-charge]()'
../server/.libs/libgnashserver.so: undefined reference to `xmlGetLastError'
collect2: ld returned 1 exit status
make[2]: *** [gparser] Error 1
make[2]: Leaving directory `/root/gnash-0.8.0/utilities'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/gnash-0.8.0'
make: *** [all] Error 2


I am building it with Agg 2.5

Thanks in advance.

---

