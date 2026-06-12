---
title: "install libmlt++0.2.3 in feisty (need idiot's guide)"
date: 2008-06-29
forum: Multimedia Software
---

### Post by uncleclinto on 2008-06-29
Okay,

So I want to install Kdenlive in feisty, but I keep running up against this libmlt++0.2.3 crap, and I can't find it anywhere.  I find all of this upstream jargon on the Internet, but while I know enough about Linux to be dangerous at this point, I'm still not seeing what this salmon spawning reference has to do with satisfying my missing dependency. 

Can anyone give me an idiots guide to installing libmlt++0.2.3.  I downloaded the source package, but this is what I get when I run ./configure and make on it:

Configuring framework:
Configuring modules:
Configuring modules/avformat:
avformat: No build environment found. 
          Try configuring mlt with --avformat-svn.
Configuring modules/core:
Configuring modules/dv:
Configuring modules/feeds:
Configuring modules/fezzik:
Configuring modules/gtk2:
No GTK2 components found - disabling
Configuring modules/inigo:
Configuring modules/kdenlive:
Configuring modules/lumas:
Configuring modules/plus:
Configuring modules/sdl:
Configuring modules/sox:
Configuring modules/valerie:
Configuring modules/vmfx:
Configuring modules/vorbis:
Configuring modules/westley:
Configuring inigo:
Configuring valerie:
Configuring miracle:
GPL Components are disabled


__________________________________________________________

...producer_westley.c:1080: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1082: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1082: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1082: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1082: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1082: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1082: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1084: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1084: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1084: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1084: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1084: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1084: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1086: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1086: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1086: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1086: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1086: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1086: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1088: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1088: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1088: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1088: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1088: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1088: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1090: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1090: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1090: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1090: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1090: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1090: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1092: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1092: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1092: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1092: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1092: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1092: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c: In function ‘on_end_element’:
producer_westley.c:1103: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1103: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1103: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1103: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1103: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1103: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1105: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1105: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1105: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1105: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1105: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1105: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1107: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1109: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1109: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1109: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1109: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1109: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1109: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1111: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1111: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1111: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1111: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1111: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1111: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1113: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1113: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1113: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1113: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1113: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1113: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1115: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1115: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1115: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1115: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1115: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1115: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1117: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1119: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1119: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1119: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1119: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1119: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1119: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1121: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1121: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1121: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
producer_westley.c:1121: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1121: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c:1121: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
producer_westley.c: In function ‘params_to_entities’:
producer_westley.c:1182: warning: pointer targets in passing argument 2 of ‘mlt_properties_get’ differ in signedness
producer_westley.c: In function ‘on_get_entity’:
producer_westley.c:1227: warning: pointer targets in passing argument 2 of ‘xmlCreateIntSubset’ differ in signedness
producer_westley.c:1227: warning: pointer targets in passing argument 3 of ‘xmlCreateIntSubset’ differ in signedness
producer_westley.c:1227: warning: pointer targets in passing argument 4 of ‘xmlCreateIntSubset’ differ in signedness
producer_westley.c:1228: warning: pointer targets in assignment differ in signedness
producer_westley.c:1229: warning: pointer targets in assignment differ in signedness
producer_westley.c: In function ‘producer_westley_init’:
producer_westley.c:1397: warning: pointer targets in passing argument 1 of ‘xmlNewDoc’ differ in signedness
producer_westley.c: In function ‘on_start_entry’:
producer_westley.c:672: warning: ‘parent_type’ may be used uninitialized in this function
producer_westley.c: In function ‘on_end_transition’:
producer_westley.c:914: warning: ‘parent_type’ may be used uninitialized in this function
producer_westley.c: In function ‘on_end_filter’:
producer_westley.c:839: warning: ‘parent_type’ may be used uninitialized in this function
producer_westley.c: In function ‘on_end_element’:
producer_westley.c:761: warning: ‘parent_type’ may be used uninitialized in this function
producer_westley.c:718: warning: ‘entry_type’ may be used uninitialized in this function
cc -shared -o ../libmltwestley.so factory.o consumer_westley.o producer_westley.o `xml2-config --libs` -L../../framework -lmlt
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/westley'
make[2]: Entering directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/fezzik'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o factory.o factory.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o producer_fezzik.o producer_fezzik.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o producer_hold.o producer_hold.c
cc -shared -o ../libmltfezzik.so factory.o producer_fezzik.o producer_hold.o  -L../../framework -lmlt
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/fezzik'
make[2]: Entering directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/valerie'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../../    -c -o factory.o factory.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../../    -c -o consumer_valerie.o consumer_valerie.c
cc -shared -o ../libmltvalerie.so factory.o consumer_valerie.o -L../../valerie -lvalerie -L../../framework -lmlt
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/valerie'
make[2]: Entering directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/lumas'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread    luma.c   -o luma
[: 45: ==: unexpected operator
[: 45: ==: unexpected operator
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/lumas'
make[2]: Entering directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/kdenlive'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o factory.o factory.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_boxblur.o filter_boxblur.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_wave.o filter_wave.c
filter_wave.c: In function ‘filter_get_image’:
filter_wave.c:79: warning: pointer targets in passing argument 4 of ‘DoWave’ differ in signedness
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o producer_framebuffer.o producer_framebuffer.c
cc -shared -o ../libmltkdenlive.so factory.o filter_boxblur.o filter_wave.o producer_framebuffer.o -lm -L../../framework -lmlt
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/kdenlive'
make[2]: Entering directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/plus'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o factory.o factory.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_affine.o filter_affine.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_charcoal.o filter_charcoal.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_invert.o filter_invert.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_sepia.o filter_sepia.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o transition_affine.o transition_affine.c
transition_affine.c: In function ‘transition_get_image’:
transition_affine.c:513: warning: value computed is not used
cc -shared -o ../libmltplus.so factory.o filter_affine.o filter_charcoal.o filter_invert.o filter_sepia.o transition_affine.o -L../../framework -lmlt
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/plus'
make[2]: Entering directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/core'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o factory.o factory.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o producer_colour.o producer_colour.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o producer_noise.o producer_noise.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o producer_ppm.o producer_ppm.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_brightness.o filter_brightness.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_channelcopy.o filter_channelcopy.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_data_feed.o filter_data_feed.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_data_show.o filter_data_show.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_gamma.o filter_gamma.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_greyscale.o filter_greyscale.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_luma.o filter_luma.c
filter_luma.c: In function ‘filter_get_image’:
filter_luma.c:61: warning: passing argument 1 of ‘mlt_properties_get_int’ from incompatible pointer type
filter_luma.c:61: warning: passing argument 1 of ‘mlt_properties_get_int’ from incompatible pointer type
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_mirror.o filter_mirror.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_mono.o filter_mono.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_obscure.o filter_obscure.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_region.o filter_region.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_rescale.o filter_rescale.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_resize.o filter_resize.c
filter_resize.c: In function ‘filter_get_image’:
filter_resize.c:124: warning: passing argument 3 of ‘mlt_properties_set’ makes pointer from integer without a cast
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_transition.o filter_transition.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_watermark.o filter_watermark.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o transition_composite.o transition_composite.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o transition_luma.o transition_luma.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o transition_mix.o transition_mix.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o transition_region.o transition_region.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o consumer_null.o consumer_null.c
cc -shared -o ../libmltcore.so factory.o producer_colour.o producer_noise.o producer_ppm.o filter_brightness.o filter_channelcopy.o filter_data_feed.o filter_data_show.o filter_gamma.o filter_greyscale.o filter_luma.o filter_mirror.o filter_mono.o filter_obscure.o filter_region.o filter_rescale.o filter_resize.o filter_transition.o filter_watermark.o transition_composite.o transition_luma.o transition_mix.o transition_region.o consumer_null.o  -L../../framework -lmlt
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/core'
make[2]: Entering directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/inigo'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o factory.o factory.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o producer_inigo.o producer_inigo.c
cc -shared -o ../libmltinigo.so factory.o producer_inigo.o  -L../../framework -lmlt
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/inigo'
make[2]: Entering directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/feeds'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/feeds'
make[2]: Entering directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/vmfx'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o factory.o factory.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_chroma.o filter_chroma.c
filter_chroma.c: In function ‘filter_get_image’:
filter_chroma.c:66: warning: value computed is not used
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_chroma_hold.o filter_chroma_hold.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_mono.o filter_mono.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o filter_shape.o filter_shape.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -I../..   -c -o producer_pgm.o producer_pgm.c
cc -shared -o ../libmltvmfx.so factory.o filter_chroma.o filter_chroma_hold.o filter_mono.o filter_shape.o producer_pgm.o -L../../framework -lmlt
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/vmfx'
make[2]: Entering directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/sox'
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread `libst-config --cflags` -I../../    -c -o factory.o factory.c
cc -Wall -fPIC -DPIC   -O4 -pipe -fomit-frame-pointer -ffast-math -DUSE_MMX -g -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread `libst-config --cflags` -I../../    -c -o filter_sox.o filter_sox.c
cc -shared -o ../libmltsox.so factory.o filter_sox.o  -lst `libst-config --libs` -L../../framework -lmlt
/usr/bin/ld: cannot find -lmad
collect2: ld returned 1 exit status
make[2]: *** [../libmltsox.so] Error 1
make[2]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules/sox'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/clint/downloaded_apps/mlt-0.2.3/src/modules'
make: *** [all] Error 1

---

### Post by uncleclinto on 2008-06-30
Okay,

Does anyone have this "http://download128.mediafire.com/ottzmktnmlyg/ammoqj12nzn/kdenlive_mlt_ubuntu.zip" or know where I can get it???  It was apparently there because every how to and tutorial I find points me to it.  It is gone, however.  Does anyone happen to have it floating around on their machine???  I would really appreciate it.  I want to follow this [guide,]("http://ubuntuforums.org/showthread.php?t=322916") but I need this file.

Arrgh!  Why do all of these resources have to be so darn temporal?

---

### Post by xc3RnbFO8P on 2008-06-30
Check if this helps:
[http://pt.wikibooks.org/wiki/Kdenlive/Obtendo_e_Instalando]("http://pt.wikibooks.org/wiki/Kdenlive/Obtendo_e_Instalando")

---

### Post by uncleclinto on 2008-06-30
> **Ringi said:**
> Check if this helps:
[http://pt.wikibooks.org/wiki/Kdenlive/Obtendo_e_Instalando]("http://pt.wikibooks.org/wiki/Kdenlive/Obtendo_e_Instalando")



Thanks, but that site points to the same file that's no longer there....:confused:

---

### Post by xc3RnbFO8P on 2008-06-30
Did you search in Synaptic Package Manager **[COLOR="SeaGreen"]libmlt++[/COLOR]**

---

### Post by uncleclinto on 2008-06-30
That's how I satisfied all of the other dependencies... libmlt++ isn't there in any version.  If someone could hook me up with what repository to add to get it, that would help too.

---

