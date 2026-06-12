---
title: "mplayer plugin + opera = a headache"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by sauyeeluo on 2007-03-11
well, i have every lugin for opera working except for mplayer. whenever i encouter a wmp, qt, or rm media it'll display a white box where the video is supposed to be played. all codecs required have been installed as well as every developmental library that i can think of. in addition, the linking of the already pre comiled ubuntu mplayer-pluging failed. i do not believe this plugin was compiled for opera. 

i have followed the instructions to do the "./configure --x" and what not from the following websites
[http://www.opera.com/linux/docs/plugins/install/](http://www.opera.com/linux/docs/plugins/install/)
[http://mplayerplug-in.sourceforge.net/faq.php](http://mplayerplug-in.sourceforge.net/faq.php)
[http://ubuntuforums.org/showthread.php?t=256485](http://ubuntuforums.org/showthread.php?t=256485) <- and all other links in this thread

i am exhausted and quite frustrated...so i have enclosed the output from my attempts to build the plugin below. i will thank you ahead of time for taking your time to read it.

> sauyee@quagmire:~/tmp/blowup/mplayerplug-in$ ./configure --enable-x --with-gecko-sdk=/usr/local/gecko-sdk
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for egrep... grep -E
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
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking X11/Xlib.h usability... yes
checking X11/Xlib.h presence... yes
checking for X11/Xlib.h... yes
checking X11/Intrinsic.h usability... yes
checking X11/Intrinsic.h presence... yes
checking for X11/Intrinsic.h... yes
checking X11/StringDefs.h usability... yes
checking X11/StringDefs.h presence... yes
checking for X11/StringDefs.h... yes
checking for sys/stat.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for pid_t... yes
checking for size_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for memset... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strncasecmp... yes
checking for strstr... yes
checking for strrchr... yes
checking for snprintf... yes
checking for mkfifo... yes
checking for dup2... yes
checking for gettimeofday... yes
checking for strerror... yes
checking for strtol... yes
checking for mkdir... yes
checking for setlocale... yes
checking for memmem... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking return type of signal handlers... void
checking X11/xpm.h usability... yes
checking X11/xpm.h presence... yes
checking for X11/xpm.h... yes
checking for DPMSQueryExtension in -lXdpms... no
checking for X11/extensions/dpms.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile
config.status: creating install.sh
config.status: creating uninstall.sh
config.status: creating config.h
**************************************************************
         ARE YOU SURE YOU WANT TO BUILD WITHOUT GTK?
 BECAUSE mplayerplug-in WITHOUT GTK TAKES AWAY FUNCITIONALITY
**************************************************************
sauyee@quagmire:~/tmp/blowup/mplayerplug-in$ make
g++ -c -o plugin.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk -I/usr/local/gecko-sdk/xpcom/include  -I/usr/local/gecko-sdk/nspr/include -I/usr/local/gecko-sdk/string/include  -I/usr/local/gecko-sdk/plugin/include -I/usr/local/gecko-sdk/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API    -DX_ENABLED   Source/plugin.cpp
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsISupportsBase.h:80: warning: &#8216;class nsISupports&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: &#8216;class nsIScriptableWMPPlugin&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: &#8216;class nsIScriptableMplayerPlugin&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIProgrammingLanguage.h:32: warning: &#8216;class nsIProgrammingLanguage&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIClassInfo.h:33: warning: &#8216;class nsIClassInfo&#8217; has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: &#8216;class nsClassInfoMixin&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIServiceManager.h:40: warning: &#8216;class nsIServiceManager&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIMemory.h:54: warning: &#8216;class nsIMemory&#8217; has virtual functions but non-virtual destructor
Source/plugin.cpp: In function &#8216;NPError NS_PluginInitialize()&#8217;:
Source/plugin.cpp:101: warning: dereferencing type-punned pointer will break strict-aliasing rules
g++ -c -o nsScriptablePeer.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk -I/usr/local/gecko-sdk/xpcom/include  -I/usr/local/gecko-sdk/nspr/include -I/usr/local/gecko-sdk/string/include  -I/usr/local/gecko-sdk/plugin/include -I/usr/local/gecko-sdk/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API    -DX_ENABLED  Source/nsScriptablePeer.cpp
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsISupportsBase.h:80: warning: &#8216;class nsISupports&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: &#8216;class nsIScriptableWMPPlugin&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: &#8216;class nsIScriptableMplayerPlugin&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIProgrammingLanguage.h:32: warning: &#8216;class nsIProgrammingLanguage&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIClassInfo.h:33: warning: &#8216;class nsIClassInfo&#8217; has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: &#8216;class nsClassInfoMixin&#8217; has virtual functions but non-virtual destructor
g++ -c -o npp_gate.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk -I/usr/local/gecko-sdk/xpcom/include  -I/usr/local/gecko-sdk/nspr/include -I/usr/local/gecko-sdk/string/include  -I/usr/local/gecko-sdk/plugin/include -I/usr/local/gecko-sdk/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API    -DX_ENABLED  plugingate/npp_gate.cpp
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual functions but non-virtual destructor
g++ -c -o np_entry.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk -I/usr/local/gecko-sdk/xpcom/include  -I/usr/local/gecko-sdk/nspr/include -I/usr/local/gecko-sdk/string/include  -I/usr/local/gecko-sdk/plugin/include -I/usr/local/gecko-sdk/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API    -DX_ENABLED  plugingate/np_entry.cpp
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual functions but non-virtual destructor
g++ -c -o npn_gate.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk -I/usr/local/gecko-sdk/xpcom/include  -I/usr/local/gecko-sdk/nspr/include -I/usr/local/gecko-sdk/string/include  -I/usr/local/gecko-sdk/plugin/include -I/usr/local/gecko-sdk/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API    -DX_ENABLED  plugingate/npn_gate.cpp
g++ -c -o plugin-support.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk -I/usr/local/gecko-sdk/xpcom/include  -I/usr/local/gecko-sdk/nspr/include -I/usr/local/gecko-sdk/string/include  -I/usr/local/gecko-sdk/plugin/include -I/usr/local/gecko-sdk/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API    -DX_ENABLED   Source/plugin-support.cpp
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsISupportsBase.h:80: warning: &#8216;class nsISupports&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: &#8216;class nsIScriptableWMPPlugin&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: &#8216;class nsIScriptableMplayerPlugin&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIProgrammingLanguage.h:32: warning: &#8216;class nsIProgrammingLanguage&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIClassInfo.h:33: warning: &#8216;class nsIClassInfo&#8217; has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: &#8216;class nsClassInfoMixin&#8217; has virtual functions but non-virtual destructor
g++ -c -o plugin-setup.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk -I/usr/local/gecko-sdk/xpcom/include  -I/usr/local/gecko-sdk/nspr/include -I/usr/local/gecko-sdk/string/include  -I/usr/local/gecko-sdk/plugin/include -I/usr/local/gecko-sdk/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API    -DX_ENABLED   -DSTD Source/plugin-setup.cpp
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsISupportsBase.h:80: warning: &#8216;class nsISupports&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: &#8216;class nsIScriptableWMPPlugin&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: &#8216;class nsIScriptableMplayerPlugin&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIProgrammingLanguage.h:32: warning: &#8216;class nsIProgrammingLanguage&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIClassInfo.h:33: warning: &#8216;class nsIClassInfo&#8217; has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: &#8216;class nsClassInfoMixin&#8217; has virtual functions but non-virtual destructor
g++ -c -o plugin-list.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk -I/usr/local/gecko-sdk/xpcom/include  -I/usr/local/gecko-sdk/nspr/include -I/usr/local/gecko-sdk/string/include  -I/usr/local/gecko-sdk/plugin/include -I/usr/local/gecko-sdk/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API    -DX_ENABLED   Source/plugin-list.cpp
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsISupportsBase.h:80: warning: &#8216;class nsISupports&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: &#8216;class nsIScriptableWMPPlugin&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: &#8216;class nsIScriptableMplayerPlugin&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIProgrammingLanguage.h:32: warning: &#8216;class nsIProgrammingLanguage&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIClassInfo.h:33: warning: &#8216;class nsIClassInfo&#8217; has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: &#8216;class nsClassInfoMixin&#8217; has virtual functions but non-virtual destructor
g++ -c -o plugin-ui.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk -I/usr/local/gecko-sdk/xpcom/include  -I/usr/local/gecko-sdk/nspr/include -I/usr/local/gecko-sdk/string/include  -I/usr/local/gecko-sdk/plugin/include -I/usr/local/gecko-sdk/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API    -DX_ENABLED  Source/plugin-ui.cpp
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsISupportsBase.h:80: warning: &#8216;class nsISupports&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: &#8216;class nsIScriptableWMPPlugin&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: &#8216;class nsIScriptableMplayerPlugin&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIProgrammingLanguage.h:32: warning: &#8216;class nsIProgrammingLanguage&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIClassInfo.h:33: warning: &#8216;class nsIClassInfo&#8217; has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: &#8216;class nsClassInfoMixin&#8217; has virtual functions but non-virtual destructor
g++ -c -o plugin-threads.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/local/gecko-sdk -I/usr/local/gecko-sdk/xpcom/include  -I/usr/local/gecko-sdk/nspr/include -I/usr/local/gecko-sdk/string/include  -I/usr/local/gecko-sdk/plugin/include -I/usr/local/gecko-sdk/java/include -DGECKOSDK_ENABLED -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API    -DX_ENABLED  Source/plugin-threads.cpp
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsISupportsBase.h:80: warning: &#8216;class nsISupports&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: &#8216;class nsIScriptableWMPPlugin&#8217; has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: &#8216;class nsIScriptableMplayerPlugin&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIProgrammingLanguage.h:32: warning: &#8216;class nsIProgrammingLanguage&#8217; has virtual functions but non-virtual destructor
/usr/local/gecko-sdk/xpcom/include/nsIClassInfo.h:33: warning: &#8216;class nsIClassInfo&#8217; has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: &#8216;class nsClassInfoMixin&#8217; has virtual functions but non-virtual destructor
Source/plugin-threads.cpp: In function &#8216;PlayResult* playNode(ThreadData*, Node*, char*, int, int*, int*, int*)&#8217;:
Source/plugin-threads.cpp:1071: error: &#8216;gtkgui_setvolumetip&#8217; was not declared in this scope
Source/plugin-threads.cpp:1071: error: &#8216;g_idle_add&#8217; was not declared in this scope
make: *** [plugin-threads.o] Error 1
sauyee@quagmire:~/tmp/blowup/mplayerplug-in$ 

from what it looks like the ./configure stage went fine and theres a snafu with the make. 

if anyone can help i would greatly appreciate it. and sorry for the rather gross  text arrangement. after going nearly 26 hours without sleep i should know better then to stay up and try to get mplayer working on opera.

---

### Post by Colonel Kilkenny on 2007-03-12
You could have better luck with mozplugger or vlc-plugin or xine-plugin. Mplayerplugin worked for me at one point but then it stopped (probably because I did something) and I couldn't make it work any longer even though I compiled it again. Maybe the version was wrong or something.

Hopefully Opera really starts implementing native support for videos, those plugins just don't seem to work.

---

### Post by sauyeeluo on 2007-03-12
mozplugger has also failed...

with it i still get the grey/white box where the media controls are supposed to be.

---

### Post by Colonel Kilkenny on 2007-03-12
> **sauyeeluo said:**
> mozplugger has also failed...

with it i still get the grey/white box where the media controls are supposed to be.

Are you sure that Opera used mozplugger? I think that if it finds both mplayerplugin and mozplugger it will use mplayerplugin as a default.

Maybe you should check [http://my.opera.com/forums](http://my.opera.com/forums)

---

### Post by sauyeeluo on 2007-03-12
yes. i uninstalled mplayer-plugin and purged every trace of it prior to installing mozplugger. 

the results.

i did achieve some poor embedded playback. low framerate/buffering issues are suspected for reasons unknown. was able to have movie trailers play at full speed with no hiccups by pointing mplayer to the url in konsole.  

i did not achieve the ability to stream audio. the internet radio stations which i have tried show the same symptoms as before. the grey or white box shows up where the mplayer controls are supposed to be and nothing else happens.

i greatly appreciate your help.

---

### Post by sauyeeluo on 2007-03-12
2007.03.13
well one day later it seems that i've made some progress? maybe? but here goes...i got the "Build without GTK error to dissappear" but now im left with more lines of erros and *i do not have a  clue where to begin*. a lot of the headers that are said to be missing are located in the directory where gecko sdk 1.6 is installed. if the check phase passed shouldn't the compile see the headers in that specific path when compiling.

> sauyee@quagmire:~/tmp/blowup/mplayerplug-in$ sudo ./configure --enable-x --with-gecko-sdk=/usr/local/gecko-sdk
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
Using new (v1.7+) gecko-sdk
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for egrep... grep -E
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
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking X11/Xlib.h usability... yes
checking X11/Xlib.h presence... yes
checking for X11/Xlib.h... yes
checking X11/Intrinsic.h usability... yes
checking X11/Intrinsic.h presence... yes
checking for X11/Intrinsic.h... yes
checking X11/StringDefs.h usability... yes
checking X11/StringDefs.h presence... yes
checking for X11/StringDefs.h... yes
checking for sys/stat.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for pid_t... yes
checking for size_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for memset... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strncasecmp... yes
checking for strstr... yes
checking for strrchr... yes
checking for snprintf... yes
checking for mkfifo... yes
checking for dup2... yes
checking for gettimeofday... yes
checking for strerror... yes
checking for strtol... yes
checking for memmem... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking return type of signal handlers... void
checking X11/xpm.h usability... yes
checking X11/xpm.h presence... yes
checking for X11/xpm.h... yes
checking for DPMSQueryExtension in -lXdpms... no
checking for X11/extensions/dpms.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
sauyee@quagmire:~/tmp/blowup/mplayerplug-in$ dufo make
bash: dufo: command not found
sauyee@quagmire:~/tmp/blowup/mplayerplug-in$ sudo make
g++ -c -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -Iusr/local/gecko-sdk -Iusr/local/gecko-sdk/include -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API   -DX_ENABLED  Source/plugin.cpp
In file included from include/pluginbase.h:41,
                 from Source/plugin.h:53,
                 from Source/plugin.cpp:37:
include/npplat.h:41:19: error: npapi.h: No such file or directory
include/npplat.h:42:19: error: npupp.h: No such file or directory
In file included from Source/nsScriptablePeer.h:48,
                 from Source/plugin.h:54,
                 from Source/plugin.cpp:37:
Source/nsIScriptableMplayerPlugin.h:10:25: error: nsISupports.h: No such file or directory
In file included from Source/plugin.h:54,
                 from Source/plugin.cpp:37:
Source/nsScriptablePeer.h:49:26: error: nsIClassInfo.h: No such file or directory
Source/plugin.cpp:38:31: error: nsIServiceManager.h: No such file or directory
Source/plugin.cpp:39:23: error: nsIMemory.h: No such file or directory
Source/plugin.cpp:40:74: error: nsISupportsUtils.h: No such file or directory
include/pluginbase.h:45: error: &#8216;NPP&#8217; does not name a type
include/pluginbase.h:46: error: &#8216;NPMIMEType&#8217; does not name a type
include/pluginbase.h:47: error: &#8216;uint16&#8217; does not name a type
include/pluginbase.h:48: error: &#8216;int16&#8217; does not name a type
include/pluginbase.h:51: error: ISO C++ forbids declaration of &#8216;NPSavedData&#8217; with no type
include/pluginbase.h:51: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
include/pluginbase.h:59: error: &#8216;NPBool&#8217; does not name a type
include/pluginbase.h:61: error: &#8216;NPBool&#8217; does not name a type
include/pluginbase.h:65: error: &#8216;NPError&#8217; does not name a type
include/pluginbase.h:66: error: &#8216;NPError&#8217; does not name a type
include/pluginbase.h:68: error: &#8216;NPError&#8217; does not name a type
include/pluginbase.h:69: error: &#8216;NPStream&#8217; has not been declared
include/pluginbase.h:70: error: &#8216;int32&#8217; does not name a type
include/pluginbase.h:71: error: &#8216;int32&#8217; does not name a type
include/pluginbase.h:73: error: &#8216;NPPrint&#8217; has not been declared
include/pluginbase.h:74: error: &#8216;uint16&#8217; does not name a type
include/pluginbase.h:75: error: &#8216;NPReason&#8217; has not been declared
include/pluginbase.h:77: error: &#8216;NPError&#8217; does not name a type
include/pluginbase.h:78: error: &#8216;NPError&#8217; does not name a type
include/pluginbase.h:55: warning: &#8216;class nsPluginInstanceBase&#8217; has virtual functions but non-virtual destructor
include/pluginbase.h:88: error: &#8216;NPError&#8217; does not name a type
include/pluginbase.h:93: error: &#8216;NPError&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:25: error: expected class-name before &#8216;{&#8217; token
Source/nsIScriptableMplayerPlugin.h:28: error: expected identifier before &#8216;{&#8217; token
Source/nsIScriptableMplayerPlugin.h:28: error: expected `)' before &#8216;{&#8217; token
Source/nsIScriptableMplayerPlugin.h:28: error: ISO C++ forbids declaration of &#8216;NS_DEFINE_STATIC_IID_ACCESSOR&#8217; with no type
Source/nsIScriptableMplayerPlugin.h:28: error: expected unqualified-id before &#8216;)&#8217; token
Source/nsIScriptableMplayerPlugin.h:34: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:37: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h: In member function &#8216;int nsIScriptableWMPPlugin::NS_DEFINE_STATIC_IID_ACCESSOR(int)&#8217;:
Source/nsIScriptableMplayerPlugin.h:28: warning: left-hand operand of comma has no effect
Source/nsIScriptableMplayerPlugin.h:28: warning: right-hand operand of comma has no effect
Source/nsIScriptableMplayerPlugin.h:28: error: expected primary-expression before &#8216;{&#8217; token
Source/nsIScriptableMplayerPlugin.h:28: error: expected `;' before &#8216;{&#8217; token
Source/nsIScriptableMplayerPlugin.h:28: warning: no return statement in function returning non-void
Source/nsIScriptableMplayerPlugin.h: At global scope:
Source/nsIScriptableMplayerPlugin.h:120: error: expected class-name before &#8216;{&#8217; token
Source/nsIScriptableMplayerPlugin.h:123: error: expected identifier before &#8216;{&#8217; token
Source/nsIScriptableMplayerPlugin.h:123: error: expected `)' before &#8216;{&#8217; token
Source/nsIScriptableMplayerPlugin.h:123: error: ISO C++ forbids declaration of &#8216;NS_DEFINE_STATIC_IID_ACCESSOR&#8217; with no type
Source/nsIScriptableMplayerPlugin.h:123: error: expected unqualified-id before &#8216;)&#8217; token
Source/nsIScriptableMplayerPlugin.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:132: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:135: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:138: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:141: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:144: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:147: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:150: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:153: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:156: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:159: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:162: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:165: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:168: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:171: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:174: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:177: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:180: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:183: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:186: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:189: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:192: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:195: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:198: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:201: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:204: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:205: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:208: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:209: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:212: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:213: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:216: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:217: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:220: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h:223: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsIScriptableMplayerPlugin.h: In member function &#8216;int nsIScriptableMplayerPlugin::NS_DEFINE_STATIC_IID_ACCESSOR(int)&#8217;:
Source/nsIScriptableMplayerPlugin.h:123: warning: left-hand operand of comma has no effect
Source/nsIScriptableMplayerPlugin.h:123: warning: right-hand operand of comma has no effect
Source/nsIScriptableMplayerPlugin.h:123: error: expected primary-expression before &#8216;{&#8217; token
Source/nsIScriptableMplayerPlugin.h:123: error: expected `;' before &#8216;{&#8217; token
Source/nsIScriptableMplayerPlugin.h:123: warning: no return statement in function returning non-void
Source/nsScriptablePeer.h: At global scope:
Source/nsScriptablePeer.h:56: error: expected class-name before &#8216;{&#8217; token
Source/nsScriptablePeer.h:59: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:62: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:68: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:71: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:75: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:78: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:81: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:84: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:97: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:98: error: &#8216;nsrefcnt&#8217; has not been declared
Source/nsScriptablePeer.h:98: error: ISO C++ forbids declaration of &#8216;NS_IMETHOD_&#8217; with no type
Source/nsScriptablePeer.h:98: error: expected &#8216;;&#8217; before &#8216;AddRef&#8217;
Source/nsScriptablePeer.h:99: error: &#8216;nsrefcnt&#8217; has not been declared
Source/nsScriptablePeer.h:99: error: ISO C++ forbids declaration of &#8216;NS_IMETHOD_&#8217; with no type
Source/nsScriptablePeer.h:99: error: expected &#8216;;&#8217; before &#8216;Release&#8217;
Source/nsScriptablePeer.h:102: error: &#8216;nsrefcnt&#8217; does not name a type
Source/nsScriptablePeer.h:106: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:106: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:106: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:120: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:121: error: &#8216;nsrefcnt&#8217; has not been declared
Source/nsScriptablePeer.h:121: error: ISO C++ forbids declaration of &#8216;NS_IMETHOD_&#8217; with no type
Source/nsScriptablePeer.h:121: error: expected &#8216;;&#8217; before &#8216;AddRef&#8217;
Source/nsScriptablePeer.h:122: error: &#8216;nsrefcnt&#8217; has not been declared
Source/nsScriptablePeer.h:122: error: ISO C++ forbids declaration of &#8216;NS_IMETHOD_&#8217; with no type
Source/nsScriptablePeer.h:122: error: expected &#8216;;&#8217; before &#8216;Release&#8217;
Source/nsScriptablePeer.h:125: error: &#8216;nsrefcnt&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/nsScriptablePeer.h:129: error: &#8216;NS_IMETHOD&#8217; does not name a type
Source/plugin-setup.h:133: error: &#8216;NPError&#8217; does not name a type
Source/plugin-setup.h:149: error: &#8216;NPP&#8217; was not declared in this scope
Source/plugin-setup.h:149: error: expected primary-expression before &#8216;int&#8217;
Source/plugin-setup.h:149: error: expected primary-expression before &#8216;int&#8217;
Source/plugin-setup.h:149: error: initializer expression list treated as compound expression
Source/plugin.h:69: error: expected `)' before &#8216;aInstance&#8217;
Source/plugin.h:72: error: &#8216;NPBool&#8217; does not name a type
Source/plugin.h:74: error: &#8216;NPBool&#8217; does not name a type
Source/plugin.h:75: error: &#8216;NPError&#8217; does not name a type
Source/plugin.h:77: error: &#8216;NPError&#8217; does not name a type
Source/plugin.h:78: error: &#8216;NPError&#8217; does not name a type
Source/plugin.h:79: error: &#8216;int32&#8217; does not name a type
Source/plugin.h:80: error: &#8216;int32&#8217; does not name a type
Source/plugin.h:90: error: &#8216;PRInt32&#8217; has not been declared
Source/plugin.h:96: error: &#8216;PRBool&#8217; has not been declared
Source/plugin.h:97: error: &#8216;PRBool&#8217; has not been declared
Source/plugin.h:98: error: &#8216;PRBool&#8217; has not been declared
Source/plugin.h:99: error: &#8216;PRBool&#8217; has not been declared
Source/plugin.h:100: error: &#8216;PRBool&#8217; has not been declared
Source/plugin.h:101: error: &#8216;PRBool&#8217; has not been declared
Source/plugin.h:102: error: &#8216;PRBool&#8217; has not been declared
Source/plugin.h:103: error: &#8216;PRBool&#8217; has not been declared
Source/plugin.h:104: error: &#8216;PRBool&#8217; has not been declared
Source/plugin.h:105: error: &#8216;PRBool&#8217; has not been declared
Source/plugin.h:111: error: &#8216;NPError&#8217; does not name a type
Source/plugin.h:117: error: &#8216;NPP&#8217; does not name a type
Source/plugin.h:118: error: &#8216;NPBool&#8217; does not name a type
Source/plugin.h:129: error: &#8216;uint16&#8217; does not name a type
Source/plugin.h:130: error: &#8216;uint32&#8217; does not name a type
Source/plugin.h:131: error: &#8216;uint32&#8217; does not name a type
Source/plugin.h:132: error: &#8216;uint32&#8217; does not name a type
Source/plugin.h:133: error: &#8216;uint32&#8217; does not name a type
Source/plugin.h:134: error: &#8216;uint32&#8217; does not name a type
Source/plugin.h:135: error: &#8216;uint32&#8217; does not name a type
Source/plugin.h:162: error: &#8216;uint32&#8217; does not name a type
Source/plugin.cpp:54: error: &#8216;int32&#8217; does not name a type
Source/plugin.cpp:58: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
Source/plugin.cpp:69: error: &#8216;NPError&#8217; does not name a type
Source/plugin.cpp:79: error: &#8216;NPError&#8217; does not name a type
Source/plugin.cpp: In function &#8216;void NS_PluginShutdown()&#8217;:
Source/plugin.cpp:103: error: &#8216;gServiceManager&#8217; was not declared in this scope
Source/plugin.cpp:103: error: &#8216;NS_IF_RELEASE&#8217; was not declared in this scope
Source/plugin.cpp: In function &#8216;nsPluginInstanceBase* NS_NewPluginInstance(nsPluginCreateData*)&#8217;:
Source/plugin.cpp:118: error: &#8216;struct nsPluginCreateData&#8217; has no member named &#8216;instance&#8217;
Source/plugin.cpp: At global scope:
Source/plugin.cpp:134: error: expected `)' before &#8216;aInstance&#8217;
Source/plugin.cpp: In destructor &#8216;virtual nsPluginInstance::~nsPluginInstance()&#8217;:
Source/plugin.cpp:288: error: &#8216;mInstance&#8217; was not declared in this scope
Source/plugin.cpp:289: error: &#8216;mInitialized&#8217; was not declared in this scope
Source/plugin.cpp:292: error: &#8216;class nsControlsScriptablePeer&#8217; has no member named &#8216;Release&#8217;
Source/plugin.cpp:293: error: &#8216;NS_IF_RELEASE&#8217; was not declared in this scope
Source/plugin.cpp:299: error: &#8216;NS_IF_RELEASE&#8217; was not declared in this scope
Source/plugin.cpp: At global scope:
Source/plugin.cpp:303: error: &#8216;NPBool&#8217; does not name a type
Source/plugin.cpp: In member function &#8216;virtual void nsPluginInstance::shut()&#8217;:
Source/plugin.cpp:330: error: &#8216;mInitialized&#8217; was not declared in this scope
Source/plugin.cpp:444: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:449: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:454: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:459: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:464: error: &#8216;NPN_MemFree&#8217; was not declared in this scope
Source/plugin.cpp:469: error: &#8216;NPN_MemFree&#8217; was not declared in this scope
Source/plugin.cpp:474: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:479: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:484: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:489: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:494: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:498: error: &#8216;nQtNext&#8217; was not declared in this scope
Source/plugin.cpp:501: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:506: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:518: error: &#8216;NPN_MemFree&#8217; was not declared in this scope
Source/plugin.cpp:523: error: &#8216;NPN_MemFree&#8217; was not declared in this scope
Source/plugin.cpp:528: error: &#8216;NPN_MemFree&#8217; was not declared in this scope
Source/plugin.cpp: At global scope:
Source/plugin.cpp:553: error: &#8216;NPBool&#8217; does not name a type
Source/plugin.cpp:558: error: &#8216;NPError&#8217; does not name a type
Source/plugin.cpp:1035: error: &#8216;NPError&#8217; does not name a type
Source/plugin.cpp:1065: error: &#8216;NPError&#8217; does not name a type
Source/plugin.cpp:1280: error: &#8216;int32&#8217; does not name a type
Source/plugin.cpp:1393: error: &#8216;int32&#8217; does not name a type
Source/plugin.cpp:1840: error: variable or field &#8216;GetPlayState&#8217; declared void
Source/plugin.cpp:1840: error: &#8216;int nsPluginInstance::GetPlayState&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:1840: error: &#8216;PRInt32&#8217; was not declared in this scope
Source/plugin.cpp:1840: error: &#8216;playstate&#8217; was not declared in this scope
Source/plugin.cpp:1841: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp: In member function &#8216;void nsPluginInstance::SetFilename(const char*)&#8217;:
Source/plugin.cpp:1897: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:1902: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:1907: error: &#8216;free&#8217; was not declared in this scope
Source/plugin.cpp:1916: error: &#8216;mInstance&#8217; was not declared in this scope
Source/plugin.cpp:1916: error: &#8216;NPN_GetURL&#8217; was not declared in this scope
Source/plugin.cpp: At global scope:
Source/plugin.cpp:1925: error: variable or field &#8216;GetShowControls&#8217; declared void
Source/plugin.cpp:1925: error: &#8216;int nsPluginInstance::GetShowControls&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:1925: error: &#8216;PRBool&#8217; was not declared in this scope
Source/plugin.cpp:1925: error: &#8216;_retval&#8217; was not declared in this scope
Source/plugin.cpp:1926: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp:1931: error: variable or field &#8216;SetShowControls&#8217; declared void
Source/plugin.cpp:1931: error: &#8216;int nsPluginInstance::SetShowControls&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:1931: error: &#8216;PRBool&#8217; was not declared in this scope
Source/plugin.cpp:1932: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp:1986: error: variable or field &#8216;GetFullscreen&#8217; declared void
Source/plugin.cpp:1986: error: &#8216;int nsPluginInstance::GetFullscreen&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:1986: error: &#8216;PRBool&#8217; was not declared in this scope
Source/plugin.cpp:1986: error: &#8216;_retval&#8217; was not declared in this scope
Source/plugin.cpp:1987: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp:1992: error: variable or field &#8216;SetFullscreen&#8217; declared void
Source/plugin.cpp:1992: error: &#8216;int nsPluginInstance::SetFullscreen&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:1992: error: &#8216;PRBool&#8217; was not declared in this scope
Source/plugin.cpp:1993: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp:2441: error: variable or field &#8216;GetShowlogo&#8217; declared void
Source/plugin.cpp:2441: error: &#8216;int nsPluginInstance::GetShowlogo&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:2441: error: &#8216;PRBool&#8217; was not declared in this scope
Source/plugin.cpp:2441: error: &#8216;_retval&#8217; was not declared in this scope
Source/plugin.cpp:2442: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp:2447: error: variable or field &#8216;SetShowlogo&#8217; declared void
Source/plugin.cpp:2447: error: &#8216;int nsPluginInstance::SetShowlogo&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:2447: error: &#8216;PRBool&#8217; was not declared in this scope
Source/plugin.cpp:2448: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp:2460: error: variable or field &#8216;GetAutoPlay&#8217; declared void
Source/plugin.cpp:2460: error: &#8216;int nsPluginInstance::GetAutoPlay&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:2460: error: &#8216;PRBool&#8217; was not declared in this scope
Source/plugin.cpp:2460: error: &#8216;_retval&#8217; was not declared in this scope
Source/plugin.cpp:2461: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp:2466: error: variable or field &#8216;SetAutoPlay&#8217; declared void
Source/plugin.cpp:2466: error: &#8216;int nsPluginInstance::SetAutoPlay&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:2466: error: &#8216;PRBool&#8217; was not declared in this scope
Source/plugin.cpp:2467: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp:2471: error: variable or field &#8216;GetLoop&#8217; declared void
Source/plugin.cpp:2471: error: &#8216;int nsPluginInstance::GetLoop&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:2471: error: &#8216;PRBool&#8217; was not declared in this scope
Source/plugin.cpp:2471: error: &#8216;_retval&#8217; was not declared in this scope
Source/plugin.cpp:2472: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp:2477: error: variable or field &#8216;SetLoop&#8217; declared void
Source/plugin.cpp:2477: error: &#8216;int nsPluginInstance::SetLoop&#8217; is not a static member of &#8216;class nsPluginInstance&#8217;
Source/plugin.cpp:2477: error: &#8216;PRBool&#8217; was not declared in this scope
Source/plugin.cpp:2478: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
Source/plugin.cpp:2497: error: &#8216;NPError&#8217; does not name a type
Source/plugin.cpp: In member function &#8216;nsScriptablePeer* nsPluginInstance::getScriptablePeer()&#8217;:
Source/plugin.cpp:2543: error: &#8216;NS_ADDREF&#8217; was not declared in this scope
Source/plugin.cpp:2546: error: &#8216;NS_ADDREF&#8217; was not declared in this scope
Source/plugin.cpp: In member function &#8216;nsControlsScriptablePeer* nsPluginInstance::getControlsScriptablePeer()&#8217;:
Source/plugin.cpp:2557: error: &#8216;NS_ADDREF&#8217; was not declared in this scope
Source/plugin.cpp:2560: error: &#8216;NS_ADDREF&#8217; was not declared in this scope
make: *** [plugin.o] Error 1
sauyee@quagmire:~/tmp/blowup/mplayerplug-in$     

thanks again to anyone whose able to help.

---

### Post by sauyeeluo on 2007-03-13
well  the snafu with compiling was caused by me. after very careful reviw of the instructions i forgot the '/' behind usr/local/gecko-sdk. turns out i had done everything correctly and that was the reason why i was getting failed builds last night. 

what i've found (may not be true for everyone)
1. moving gecko sdk from a tmp folder in home to usr/local seemed make the ./configure stage smoother (dk if thats all a valid reason but it did the trick)
2. after the plugin is built put it in the /usr/lib/opera/plugins folder. then in the tools->pref->adv.->content->plugins control uncheck both the mozilla and firefox library and click check new. and restart opera.

the fact that i had opera set to look in those folders seems to have confused it when loading plugins as it was seeing the mozilla-mplayer pulgin. doing that and restarting the app after appears (so far) to remedy the problem. 


needless to say, a novice mistake caused two days of hell.

---

### Post by Sladi on 2007-04-30
Where can I download the source of Gecko 1.6 SDK? 


Regards, 
Sladi

---

