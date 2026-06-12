---
title: "Compile ac3jack on x86 9.10 Karmic Koala"
date: 2009-11-25
forum: Multimedia Software
---

### Post by kwasibengt on 2009-11-25
Hi folks!

Im currently trying to compile ac3jack 2.03 on x86 9.10 Karmic Koala
without success. I have gone through the dependency requirements found here [http://www.essej.net/ac3jack/]("http://www.essej.net/ac3jack/") several times and apt-get installed everyone with even slightest resemblance.

boost is "apt-get source -b" and then dpkg -i with every built package.
aften is "apt-get install aften" but "aften -version" tells me version SVN, maybe its to old? should be 0.08 and should i go for compiling source?
can the gcc version 4.4 be the problem? "checking dependency style of g++... gcc3" have tried with 4.2 too and same error. cant find 3.4 in the repositories anymore.

jack_audio_driver.cpp:440: error: ‘stderr’ was not declared in this scope
jack_audio_driver.cpp:440: error: ‘fprintf’ was not declared in this scope

./configure
root@amenemhet:~/Downloads/ac3jack-2.0.3# ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for --with-macosx-sdk... 
checking for --with-macosx-version-min... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for JACK... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking sys/mkdev.h usability... no
checking sys/mkdev.h presence... no
checking for sys/mkdev.h... no
checking sys/sysmacros.h usability... yes
checking sys/sysmacros.h presence... yes
checking for sys/sysmacros.h... yes
checking for string.h... (cached) yes
checking for memory.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking sys/ndir.h usability... no
checking sys/ndir.h presence... no
checking for sys/ndir.h... no
checking ndir.h usability... no
checking ndir.h presence... no
checking for ndir.h... no
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking /System/Library/Frameworks/CoreAudio.framework/Headers/CoreAudio.h usability... no
checking /System/Library/Frameworks/CoreAudio.framework/Headers/CoreAudio.h presence... no
checking for /System/Library/Frameworks/CoreAudio.framework/Headers/CoreAudio.h... no
checking aften/aften.h usability... yes
checking aften/aften.h presence... yes
checking for aften/aften.h... yes
checking for aften_encode_init in -laften... yes
checking for SIGCPP... yes
checking for LOSC... yes
checking for XML... yes
WXCONFIG IS ""
checking for wx-config-2.6... no
checking for wxgtk2-2.5-config... no
checking for wxgtk2-2.4-config... no
checking for wxgtk-2.4-config... no
checking for wx-config... /usr/bin/wx-config
checking whether byte ordering is bigendian... no
checking whether sys/types.h defines makedev... yes
checking for working alloca.h... yes
checking for alloca... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for struct stat.st_blocks... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking whether closedir returns void... no
checking for mkfifo... yes
checking for mknod... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating version.h
config.status: creating src/Makefile
config.status: creating src/gui/Makefile
config.status: creating src/coreaudio/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
root@amenemhet:~/Downloads/ac3jack-2.0.3#

root@amenemhet:~/Downloads/ac3jack-2.0.3# make
make  all-recursive
make[1]: Entering directory `/home/amenemhet/Downloads/ac3jack-2.0.3'
Making all in src
make[2]: Entering directory `/home/amenemhet/Downloads/ac3jack-2.0.3/src'
Making all in .
make[3]: Entering directory `/home/amenemhet/Downloads/ac3jack-2.0.3/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/local/include   -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2   -I/usr/local/include  -I/opt/local/include -pthread    -g -O2 -MT engine.o -MD -MP -MF ".deps/engine.Tpo" -c -o engine.o engine.cpp; \
	then mv -f ".deps/engine.Tpo" ".deps/engine.Po"; else rm -f ".deps/engine.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/local/include   -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2   -I/usr/local/include  -I/opt/local/include -pthread    -g -O2 -MT audio_driver.o -MD -MP -MF ".deps/audio_driver.Tpo" -c -o audio_driver.o audio_driver.cpp; \
	then mv -f ".deps/audio_driver.Tpo" ".deps/audio_driver.Po"; else rm -f ".deps/audio_driver.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/local/include   -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2   -I/usr/local/include  -I/opt/local/include -pthread    -g -O2 -MT encoder.o -MD -MP -MF ".deps/encoder.Tpo" -c -o encoder.o encoder.cpp; \
	then mv -f ".deps/encoder.Tpo" ".deps/encoder.Po"; else rm -f ".deps/encoder.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/local/include   -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2   -I/usr/local/include  -I/opt/local/include -pthread    -g -O2 -MT file_writer.o -MD -MP -MF ".deps/file_writer.Tpo" -c -o file_writer.o file_writer.cpp; \
	then mv -f ".deps/file_writer.Tpo" ".deps/file_writer.Po"; else rm -f ".deps/file_writer.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/local/include   -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2   -I/usr/local/include  -I/opt/local/include -pthread    -g -O2 -MT thread_writer.o -MD -MP -MF ".deps/thread_writer.Tpo" -c -o thread_writer.o thread_writer.cpp; \
	then mv -f ".deps/thread_writer.Tpo" ".deps/thread_writer.Po"; else rm -f ".deps/thread_writer.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/local/include   -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2   -I/usr/local/include  -I/opt/local/include -pthread    -g -O2 -MT control_osc.o -MD -MP -MF ".deps/control_osc.Tpo" -c -o control_osc.o control_osc.cpp; \
	then mv -f ".deps/control_osc.Tpo" ".deps/control_osc.Po"; else rm -f ".deps/control_osc.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/local/include   -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2   -I/usr/local/include  -I/opt/local/include -pthread    -g -O2 -MT alsa_spdif_writer.o -MD -MP -MF ".deps/alsa_spdif_writer.Tpo" -c -o alsa_spdif_writer.o alsa_spdif_writer.cpp; \
	then mv -f ".deps/alsa_spdif_writer.Tpo" ".deps/alsa_spdif_writer.Po"; else rm -f ".deps/alsa_spdif_writer.Tpo"; exit 1; fi
rm -f libac3jack_core.a
ar cru libac3jack_core.a engine.o audio_driver.o encoder.o file_writer.o thread_writer.o control_osc.o alsa_spdif_writer.o  
ranlib libac3jack_core.a
if g++ -DHAVE_CONFIG_H -I. -I. -I..    -I/usr/local/include   -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2   -I/usr/local/include  -I/opt/local/include -pthread    -g -O2 -MT jack_audio_driver.o -MD -MP -MF ".deps/jack_audio_driver.Tpo" -c -o jack_audio_driver.o jack_audio_driver.cpp; \
	then mv -f ".deps/jack_audio_driver.Tpo" ".deps/jack_audio_driver.Po"; else rm -f ".deps/jack_audio_driver.Tpo"; exit 1; fi
jack_audio_driver.cpp: In member function ‘int AC3JACK::JackAudioDriver::connect_to_jack()’:
jack_audio_driver.cpp:156: error: ‘snprintf’ was not declared in this scope
jack_audio_driver.cpp:167: error: ‘snprintf’ was not declared in this scope
jack_audio_driver.cpp: In member function ‘virtual bool AC3JACK::JackAudioDriver::connect_input_port(port_id_t, const char*)’:
jack_audio_driver.cpp:375: error: ‘stderr’ was not declared in this scope
jack_audio_driver.cpp:376: error: ‘fprintf’ was not declared in this scope
jack_audio_driver.cpp: In member function ‘virtual bool AC3JACK::JackAudioDriver::connect_output_port(port_id_t, const char*)’:
jack_audio_driver.cpp:389: error: ‘stderr’ was not declared in this scope
jack_audio_driver.cpp:390: error: ‘fprintf’ was not declared in this scope
jack_audio_driver.cpp: In member function ‘virtual bool AC3JACK::JackAudioDriver::disconnect_input_port(port_id_t, const char*)’:
jack_audio_driver.cpp:406: error: ‘stderr’ was not declared in this scope
jack_audio_driver.cpp:406: error: ‘fprintf’ was not declared in this scope
jack_audio_driver.cpp: In member function ‘virtual bool AC3JACK::JackAudioDriver::disconnect_output_port(port_id_t, const char*)’:
jack_audio_driver.cpp:440: error: ‘stderr’ was not declared in this scope
jack_audio_driver.cpp:440: error: ‘fprintf’ was not declared in this scope
make[3]: *** [jack_audio_driver.o] Error 1
make[3]: Leaving directory `/home/amenemhet/Downloads/ac3jack-2.0.3/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/amenemhet/Downloads/ac3jack-2.0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/amenemhet/Downloads/ac3jack-2.0.3'
make: *** [all] Error 2
root@amenemhet:~/Downloads/ac3jack-2.0.3# 

any help/input on this subject would be very appreciated.
/Richard

---

### Post by kwasibengt on 2009-11-25
The file src/jack_audio_driver.cpp was lacking

#include <stdio.h>

add it and it will compile just fine if you have installed the right dependencies.

cheeers!

---

### Post by Pagnol on 2010-01-18
How did you manage to compile AC3Jack? I always end up getting a compile error:

```

make  all-recursive
make[1]: Entering directory `/home/Pagnol/ac3jack-2.0.3'
Making all in src
make[2]: Entering directory `/home/Pagnol/ac3jack-2.0.3/src'
Making all in .
make[3]: Entering directory `/home/Pagnol/ac3jack-2.0.3/src'
g++ -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2   -I/usr/local/include  -I/opt/local/include -pthread    -g -O2  -L/usr/local/lib  -o ac3jack_cli  ac3jack.o libac3jack_drivers.a libac3jack_core.a   -lsigc-1.2   -L/usr/local/lib -laften  -L/opt/local/lib -lboost_thread  -llo -lpthread   
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::get_transport_info(AC3JACK::TransportInfo&) const':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:543: undefined reference to `jack_transport_query'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::disconnect_output_port(unsigned int, char const*)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:442: undefined reference to `jack_port_name'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:442: undefined reference to `jack_disconnect'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:451: undefined reference to `jack_port_get_connections'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:454: undefined reference to `jack_port_name'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:454: undefined reference to `jack_disconnect'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::disconnect_input_port(unsigned int, char const*)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:408: undefined reference to `jack_port_name'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:408: undefined reference to `jack_disconnect'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:418: undefined reference to `jack_port_get_connections'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:421: undefined reference to `jack_port_name'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:421: undefined reference to `jack_disconnect'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::connect_output_port(unsigned int, char const*)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:391: undefined reference to `jack_port_name'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:391: undefined reference to `jack_connect'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:393: undefined reference to `jack_port_name'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::connect_input_port(unsigned int, char const*)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:377: undefined reference to `jack_port_name'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:377: undefined reference to `jack_connect'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:379: undefined reference to `jack_port_name'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::destroy_input_port(unsigned int)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:332: undefined reference to `jack_port_unregister'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::destroy_output_port(unsigned int)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:317: undefined reference to `jack_port_unregister'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::connect_to_jack()':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:120: undefined reference to `jack_set_error_function'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:160: undefined reference to `jack_client_new'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:168: undefined reference to `jack_client_new'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:184: undefined reference to `jack_set_xrun_callback'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:185: undefined reference to `jack_on_shutdown'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:186: undefined reference to `jack_set_graph_order_callback'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:171: undefined reference to `jack_client_new'
libac3jack_drivers.a(jack_audio_driver.o): In function `~JackAudioDriver':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:45: undefined reference to `jack_deactivate'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:46: undefined reference to `jack_client_close'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:45: undefined reference to `jack_deactivate'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:46: undefined reference to `jack_client_close'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:45: undefined reference to `jack_deactivate'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:46: undefined reference to `jack_client_close'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::create_output_port(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, unsigned int&)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:289: undefined reference to `jack_port_register'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::create_input_port(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, unsigned int&)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:267: undefined reference to `jack_port_register'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::activate()':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:86: undefined reference to `jack_activate'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::deactivate()':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:100: undefined reference to `jack_deactivate'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::initialize(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:63: undefined reference to `jack_get_sample_rate'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:64: undefined reference to `jack_get_buffer_size'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:66: undefined reference to `jack_set_process_callback'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:71: undefined reference to `jack_set_buffer_size_callback'
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:75: undefined reference to `jack_set_port_registration_callback'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::get_input_connections(unsigned int, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:471: undefined reference to `jack_port_get_connections'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::get_output_connectable_ports(std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:524: undefined reference to `jack_get_ports'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::get_input_connectable_ports(std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:506: undefined reference to `jack_get_ports'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::get_output_connections(unsigned int, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:487: undefined reference to `jack_port_get_connections'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::get_output_port_latency(unsigned int)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:370: undefined reference to `jack_port_get_total_latency'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::get_input_port_latency(unsigned int)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:362: undefined reference to `jack_port_get_total_latency'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::get_output_port_buffer(unsigned int, unsigned int)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:354: undefined reference to `jack_port_get_buffer'
libac3jack_drivers.a(jack_audio_driver.o): In function `AC3JACK::JackAudioDriver::get_input_port_buffer(unsigned int, unsigned int)':
/home/Pagnol/ac3jack-2.0.3/src/jack_audio_driver.cpp:345: undefined reference to `jack_port_get_buffer'
collect2: ld returned 1 exit status
make[3]: *** [ac3jack_cli] Error 1
make[3]: Leaving directory `/home/Pagnol/ac3jack-2.0.3/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/Pagnol/ac3jack-2.0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/Pagnol/ac3jack-2.0.3'
make: *** [all] Error 2

```

libjack-dev etc. are installed.

I greatly appreciate your help.

---

