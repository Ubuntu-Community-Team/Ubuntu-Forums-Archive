---
title: "Cannot Get Martian Driver to Compile"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by gamgee911 on 2009-01-11
I am having some difficulty in compiling the maritan driver for my
winmodem.  Can anyone make any sense of this?  Thanks in advance

```
claybo91@ubuntu:~/Desktop/martian-full-20080407$ sudo make all
[sudo] password for claybo91:
make -C kmodule/ modules
make[1]: Entering directory
`/home/claybo91/Desktop/martian-full-20080407/kmodule'
make -C /lib/modules/2.6.27-7-generic/build
M="/home/claybo91/Desktop/martian-full-20080407/kmodule"  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
 CC [M]  /home/claybo91/Desktop/martian-full-20080407/kmodule/martian.o
In file included from
/home/claybo91/Desktop/martian-full-20080407/kmodule/kmartian.h:12,
                from
/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.c:62:
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:18:
error: expected declaration specifiers or '...' before '*' token
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:18:
error: 'fastcall' declared as function returning a function
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:18:
warning: function declaration isn't a prototype
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:18:
error: field 'fastcall' declared as a function
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:19:
error: expected declaration specifiers or '...' before '*' token
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:19:
error: 'fastcall' declared as function returning a function
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:19:
warning: function declaration isn't a prototype
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:19:
error: field 'fastcall' declared as a function
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:21:
error: expected declaration specifiers or '...' before '(' token
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:21:
warning: function declaration isn't a prototype
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:21:
error: field 'FASTCALL' declared as a function
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:22:
error: expected declaration specifiers or '...' before '(' token
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:22:
warning: function declaration isn't a prototype
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:22:
error: field 'FASTCALL' declared as a function
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:19:
error: duplicate member 'fastcall'
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:22:
error: duplicate member 'FASTCALL'
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h: In
function 'mfifo_next':
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:45:
error: 'struct mfifo_ops' has no member named 'wrap'
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h: In
function 'mfifo_put':
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:52:
error: 'struct mfifo_ops' has no member named 'set'
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:54:
error: 'struct mfifo_ops' has no member named 'wrap'
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h: In
function 'mfifo_full':
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:62:
error: 'struct mfifo_ops' has no member named 'space'
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h: In
function 'mfifo_get':
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:78:
error: 'struct mfifo_ops' has no member named 'get'
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:81:
error: 'struct mfifo_ops' has no member named 'wrap'
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h: In
function 'mfifo_lastwr':
/home/claybo91/Desktop/martian-full-20080407/kmodule/mfifo.h:87:
error: 'struct mfifo_ops' has no member named 'wrap'
In file included from
/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.c:64:
/home/claybo91/Desktop/martian-full-20080407/kmodule/marsio.h: At top level:
/home/claybo91/Desktop/martian-full-20080407/kmodule/marsio.h:8:
error: expected ')' before '(' token
/home/claybo91/Desktop/martian-full-20080407/kmodule/marsio.h:9:
error: expected ')' before '(' token
/home/claybo91/Desktop/martian-full-20080407/kmodule/marsio.h:10:
error: expected ')' before '(' token
/home/claybo91/Desktop/martian-full-20080407/kmodule/marsio.h:11:
error: expected ')' before '(' token
/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.c: In
function 'martian_isr':
/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.c:119:
error: implicit declaration of function 'mars_read_register'
/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.c:131:
error: implicit declaration of function 'mars_write_register'
/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.c:139:
error: implicit declaration of function 'mars_write_word'
/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.c:160:
error: implicit declaration of function 'process_stream'
/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.c:160:
warning: value computed is not used
/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.c: In
function 'martian_add':
/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.c:664:
warning: passing argument 2 of 'request_irq' from incompatible pointer
type
make[3]: *** [/home/claybo91/Desktop/martian-full-20080407/kmodule/martian.o]
Error 1
make[2]: *** [_module_/home/claybo91/Desktop/martian-full-20080407/kmodule]
Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory
`/home/claybo91/Desktop/martian-full-20080407/kmodule'
make: *** [all] Error 2

```

---

