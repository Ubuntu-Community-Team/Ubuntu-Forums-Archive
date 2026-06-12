---
title: "wineasio make command error PLEASE HELP!!"
date: 2009-05-29
forum: Multimedia Software
---

### Post by Affrikka on 2009-05-29
Hey everyone,

I’m a linux newbie and have been trying to figure this out for days. Every time I run the [make] command i get an error, summing it up to be ```
make: *** [asio.o] Error 1
```
I am still trying to figure out why it isn’t working, and my dad wanted to me figure it out on my own (honestly i don’t know if he can do it either :P) but I REALLY need this to work. I am running 8.04 on a 64bit AMD

just in case, i’ll post the rest of the error:
```

gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
In file included from /usr/include/features.h:354,
from /usr/include/fcntl.h:27,
from port.h:30,
from asio.c:22:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
asio.c:32:33: error: wine/windows/windef.h: No such file or directory
asio.c:33:34: error: wine/windows/winbase.h: No such file or directory
asio.c:34:34: error: wine/windows/objbase.h: No such file or directory
asio.c:35:35: error: wine/windows/mmsystem.h: No such file or directory
asio.c:41:26: error: wine/library.h: No such file or directory
asio.c:42:24: error: wine/debug.h: No such file or directory
asio.c:44:23: error: jack/jack.h: No such file or directory
asio.c:49: warning: data definition has no type or storage class
asio.c:49: warning: type defaults to ‘int’ in declaration of ‘WINE_DEFAULT_DEBUG_CHANNEL’
asio.c:49: warning: parameter names (without types) in function declaration
asio.c:52: error: expected ‘)’ before ‘nframes’
asio.c:55: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CALLBACK’
asio.c:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘const’
asio.c:98: warning: return type defaults to ‘int’
asio.c: In function ‘DECLARE_INTERFACE_’:
asio.c:99: warning: implicit declaration of function ‘STDMETHOD_’
asio.c:99: error: ‘HRESULT’ undeclared (first use in this function)
asio.c:99: error: (Each undeclared identifier is reported only once
asio.c:99: error: for each function it appears in.)
asio.c:99: error: ‘QueryInterface’ undeclared (first use in this function)
asio.c:99: error: ‘THIS_’ undeclared (first use in this function)
asio.c:99: error: expected ‘)’ before ‘REFIID’
asio.c:99: error: called object ‘STDMETHOD_(, )’ is not a function
asio.c:99: error: expected ‘;’ before ‘PURE’
asio.c:100: error: ‘ULONG’ undeclared (first use in this function)
asio.c:100: error: ‘AddRef’ undeclared (first use in this function)
asio.c:100: error: ‘THIS’ undeclared (first use in this function)
asio.c:100: error: called object ‘STDMETHOD_(, )’ is not a function
asio.c:100: error: expected ‘;’ before ‘PURE’
asio.c:101: error: ‘Release’ undeclared (first use in this function)
asio.c:101: error: called object ‘STDMETHOD_(, )’ is not a function
asio.c:101: error: expected ‘;’ before ‘PURE’
asio.c:102: error: expected expression before ‘ASIOBool’
asio.c:102: error: expected ‘)’ before ‘void’
asio.c:102: error: called object ‘STDMETHOD_()’ is not a function
asio.c:102: error: expected ‘;’ before ‘PURE’
asio.c:103: error: expected expression before ‘void’
asio.c:103: error: expected ‘)’ before ‘char’
asio.c:103: error: called object ‘STDMETHOD_()’ is not a function
asio.c:103: error: expected ‘;’ before ‘PURE’
asio.c:104: error: expected expression before ‘long’
asio.c:104: error: called object ‘STDMETHOD_()’ is not a function
asio.c:104: error: expected ‘;’ before ‘PURE’
asio.c:105: error: expected expression before ‘void’
asio.c:105: error: expected ‘)’ before ‘char’
asio.c:105: error: called object ‘STDMETHOD_()’ is not a function
asio.c:105: error: expected ‘;’ before ‘PURE’
asio.c:106: error: expected expression before ‘ASIOError’
asio.c:106: error: called object ‘STDMETHOD_()’ is not a function
asio.c:106: error: expected ‘;’ before ‘PURE’
asio.c:107: error: expected expression before ‘ASIOError’
asio.c:107: error: called object ‘STDMETHOD_()’ is not a function
asio.c:107: error: expected ‘;’ before ‘PURE’
asio.c:108: error: expected expression before ‘ASIOError’
asio.c:108: error: expected ‘)’ before ‘long’
asio.c:108: error: called object ‘STDMETHOD_()’ is not a function
asio.c:108: error: expected ‘;’ before ‘PURE’
asio.c:109: error: expected expression before ‘ASIOError’
asio.c:109: error: expected ‘)’ before ‘long’
asio.c:109: error: called object ‘STDMETHOD_()’ is not a function
asio.c:109: error: expected ‘;’ before ‘PURE’
asio.c:110: error: expected expression before ‘ASIOError’
asio.c:110: error: expected ‘)’ before ‘long’
asio.c:110: error: called object ‘STDMETHOD_()’ is not a function
asio.c:110: error: expected ‘;’ before ‘PURE’
asio.c:111: error: expected expression before ‘ASIOError’
asio.c:111: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:111: error: called object ‘STDMETHOD_()’ is not a function
asio.c:111: error: expected ‘;’ before ‘PURE’
asio.c:112: error: expected expression before ‘ASIOError’
asio.c:112: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:112: error: called object ‘STDMETHOD_()’ is not a function
asio.c:112: error: expected ‘;’ before ‘PURE’
asio.c:113: error: expected expression before ‘ASIOError’
asio.c:113: error: expected ‘)’ before ‘ASIOSampleRate’
asio.c:113: error: called object ‘STDMETHOD_()’ is not a function
asio.c:113: error: expected ‘;’ before ‘PURE’
asio.c:114: error: expected expression before ‘ASIOError’
asio.c:114: error: expected ‘)’ before ‘ASIOClockSource’
asio.c:114: error: called object ‘STDMETHOD_()’ is not a function
asio.c:114: error: expected ‘;’ before ‘PURE’
asio.c:115: error: expected expression before ‘ASIOError’
asio.c:115: error: expected ‘)’ before ‘long’
asio.c:115: error: called object ‘STDMETHOD_()’ is not a function
asio.c:115: error: expected ‘;’ before ‘PURE’
asio.c:116: error: expected expression before ‘ASIOError’
asio.c:116: error: expected ‘)’ before ‘ASIOSamples’
asio.c:116: error: called object ‘STDMETHOD_()’ is not a function
asio.c:116: error: expected ‘;’ before ‘PURE’
asio.c:117: error: expected expression before ‘ASIOError’
asio.c:117: error: expected ‘)’ before ‘ASIOChannelInfo’
asio.c:117: error: called object ‘STDMETHOD_()’ is not a function
asio.c:117: error: expected ‘;’ before ‘PURE’
asio.c:118: error: expected expression before ‘ASIOError’
asio.c:118: error: expected ‘)’ before ‘ASIOBufferInfo’
asio.c:118: error: called object ‘STDMETHOD_()’ is not a function
asio.c:118: error: expected ‘;’ before ‘PURE’
asio.c:119: error: expected expression before ‘ASIOError’
asio.c:119: error: called object ‘STDMETHOD_()’ is not a function
asio.c:119: error: expected ‘;’ before ‘PURE’
asio.c:120: error: expected expression before ‘ASIOError’
asio.c:120: error: called object ‘STDMETHOD_()’ is not a function
asio.c:120: error: expected ‘;’ before ‘PURE’
asio.c:121: error: expected expression before ‘ASIOError’
asio.c:121: error: expected ‘)’ before ‘long’
asio.c:121: error: called object ‘STDMETHOD_()’ is not a function
asio.c:121: error: expected ‘;’ before ‘PURE’
asio.c:122: error: expected expression before ‘ASIOError’
asio.c:122: error: called object ‘STDMETHOD_()’ is not a function
asio.c:122: error: expected ‘;’ before ‘PURE’
asio.c: At top level:
asio.c:139: error: expected specifier-qualifier-list before ‘jack_port_t’
asio.c:145: error: expected ‘:’, ‘,’, ‘;’, ‘}’ or ‘__attribute__’ before ‘*’ token
asio.c:200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c:210: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c:235: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WINAPI’
asio.c: In function ‘set_clientname’:
asio.c:278: error: ‘IWineASIOImpl’ has no member named ‘client_name’
asio.c: In function ‘read_config’:
asio.c:289: warning: implicit declaration of function ‘TRACE’
asio.c:308: warning: implicit declaration of function ‘isspace’
asio.c:315: error: ‘IWineASIOImpl’ has no member named ‘client_name’
asio.c: In function ‘get_numChannels’:
asio.c:338: error: ‘IWineASIOImpl’ has no member named ‘client_name’
asio.c: In function ‘set_portname’:
asio.c:355: error: ‘IWineASIOImpl’ has no member named ‘client_name’
asio.c: At top level:
asio.c:371: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_init’
asio.c:371: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_init’
asio.c:498: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getDriverName’
asio.c:498: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getDriverName’
asio.c:504: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getDriverVersion’
asio.c:504: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getDriverVersion’
asio.c:510: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getErrorMessage’
asio.c:510: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getErrorMessage’
asio.c: In function ‘get_targetname’:
asio.c:521: error: ‘IWineASIOImpl’ has no member named ‘client_name’
asio.c: At top level:
asio.c:533: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_start’
asio.c:533: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_start’
asio.c:643: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_stop’
asio.c:643: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_stop’
asio.c:682: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getChannels’
asio.c:682: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getChannels’
asio.c:698: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getLatencies’
asio.c:698: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getLatencies’
asio.c:712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getBufferSize’
asio.c:712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getBufferSize’
asio.c:734: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_canSampleRate’
asio.c:734: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_canSampleRate’
asio.c:745: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getSampleRate’
asio.c:745: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getSampleRate’
asio.c:758: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_setSampleRate’
asio.c:758: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_setSampleRate’
asio.c:769: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getClockSources’
asio.c:769: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getClockSources’
asio.c:788: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_setClockSource’
asio.c:788: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_setClockSource’
asio.c:803: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getSamplePosition’
asio.c:803: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getSamplePosition’
asio.c:825: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_getChannelInfo’
asio.c:825: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_getChannelInfo’
asio.c:860: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_disposeBuffers’
asio.c:860: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_disposeBuffers’
asio.c:894: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_createBuffers’
asio.c:894: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_createBuffers’
asio.c:1025: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_controlPanel’
asio.c:1025: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_controlPanel’
asio.c:1032: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_future’
asio.c:1032: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_future’
asio.c:1058: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘IWineASIOImpl_outputReady’
asio.c:1058: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wrapped_IWineASIOImpl_outputReady’
asio.c:1065: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WineASIO_Vtbl’
asio.c:1093: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘asioCreateInstance’
asio.c: In function ‘getNanoSeconds’:
asio.c:1114: warning: implicit declaration of function ‘timeGetTime’
asio.c: At top level:
asio.c:1119: error: expected ‘)’ before ‘nframes’
asio.c:1189: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CALLBACK’
make: *** [asio.o] Error 1

```

---

### Post by Affrikka on 2009-05-31
Bump.... does ANYONE know? :(

---

### Post by Affrikka on 2009-06-01
You all are the worst at answering questions. I've asked about 4 questions on this forum and none of them have ever been answered, ever. SO SOMEONE PLEASE ANSWER ME FOR ONCE!

---

### Post by lensman3 on 2009-06-01
You are missing "stubs-32.h".  Whatever that is:

/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory


The "make" couldn't find stubs-32.h which should be found in /usr/include/gnu/stubs.h.  It was trying to compile asio.c.  It looks like you might be missing some 32bit libraries that the 64bit gcc needs.

---

