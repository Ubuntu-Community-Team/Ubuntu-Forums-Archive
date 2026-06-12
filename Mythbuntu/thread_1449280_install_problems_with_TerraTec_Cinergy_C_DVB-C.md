---
title: "install problems with TerraTec Cinergy C DVB-C"
date: 2010-04-07
forum: Mythbuntu
---

### Post by jurgen69 on 2010-04-07
Hi All,

I'm building a HTPC and I have installed a fresh copy of Mythbuntu. I'm using a TerraTec Cinergy C DVB-C.

I have followed the instructions in the following link:

[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C]("http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C")

And I've also used tried this post:

[http://ubuntuforums.org/showthread.php?t=857524&highlight=cinergy+terratec]("http://ubuntuforums.org/showthread.php?t=857524&highlight=cinergy+terratec")

My problem is this, when I try to "make" the driver I get the following errors
```

root@hush-desktop:~/v4l-dvb# make all
make -C /root/v4l-dvb/v4l all
make[1]: Entering directory `/root/v4l-dvb/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/root/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/root/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/root/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/root/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.31-14-generic/build
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/root/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /root/v4l-dvb/v4l/firedtv-1394.o
/root/v4l-dvb/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/root/v4l-dvb/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/root/v4l-dvb/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/root/v4l-dvb/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/root/v4l-dvb/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/root/v4l-dvb/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/root/v4l-dvb/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/root/v4l-dvb/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list
/root/v4l-dvb/v4l/firedtv-1394.c:40: warning: its scope is only this definition or declaration, which is probably not what you want
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/root/v4l-dvb/v4l/firedtv-1394.c:56: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:57: error: implicit declaration of function 'hpsb_iso_n_ready'
/root/v4l-dvb/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:65: error: implicit declaration of function 'dma_region_i'
/root/v4l-dvb/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:65: error: expected expression before 'unsigned'
/root/v4l-dvb/v4l/firedtv-1394.c:66: warning: assignment makes pointer from integer without a cast
/root/v4l-dvb/v4l/firedtv-1394.c:67: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:71: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:85: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'node_of':
/root/v4l-dvb/v4l/firedtv-1394.c:90: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:90: warning: type defaults to 'int' in declaration of '__mptr'
/root/v4l-dvb/v4l/firedtv-1394.c:90: warning: initialization from incompatible pointer type
/root/v4l-dvb/v4l/firedtv-1394.c:90: error: invalid use of undefined type 'struct unit_directory'
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'node_lock':
/root/v4l-dvb/v4l/firedtv-1394.c:95: error: 'quadlet_t' undeclared (first use in this function)
/root/v4l-dvb/v4l/firedtv-1394.c:95: error: (Each undeclared identifier is reported only once
/root/v4l-dvb/v4l/firedtv-1394.c:95: error: for each function it appears in.)
/root/v4l-dvb/v4l/firedtv-1394.c:95: error: 'd' undeclared (first use in this function)
/root/v4l-dvb/v4l/firedtv-1394.c:96: warning: ISO C90 forbids mixed declarations and code
/root/v4l-dvb/v4l/firedtv-1394.c:98: error: implicit declaration of function 'hpsb_node_lock'
/root/v4l-dvb/v4l/firedtv-1394.c:99: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'node_read':
/root/v4l-dvb/v4l/firedtv-1394.c:107: error: implicit declaration of function 'hpsb_node_read'
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'node_write':
/root/v4l-dvb/v4l/firedtv-1394.c:112: error: implicit declaration of function 'hpsb_node_write'
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'start_iso':
/root/v4l-dvb/v4l/firedtv-1394.c:123: error: implicit declaration of function 'hpsb_iso_recv_init'
/root/v4l-dvb/v4l/firedtv-1394.c:123: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:125: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/root/v4l-dvb/v4l/firedtv-1394.c:127: warning: assignment makes pointer from integer without a cast
/root/v4l-dvb/v4l/firedtv-1394.c:134: error: implicit declaration of function 'hpsb_iso_recv_start'
/root/v4l-dvb/v4l/firedtv-1394.c:137: error: implicit declaration of function 'hpsb_iso_shutdown'
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'stop_iso':
/root/v4l-dvb/v4l/firedtv-1394.c:148: error: implicit declaration of function 'hpsb_iso_stop'
/root/v4l-dvb/v4l/firedtv-1394.c: At top level:
/root/v4l-dvb/v4l/firedtv-1394.c:163: warning: 'struct hpsb_host' declared inside parameter list
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'fcp_request':
/root/v4l-dvb/v4l/firedtv-1394.c:176: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'node_probe':
/root/v4l-dvb/v4l/firedtv-1394.c:191: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:191: warning: type defaults to 'int' in declaration of '__mptr'
/root/v4l-dvb/v4l/firedtv-1394.c:191: warning: initialization from incompatible pointer type
/root/v4l-dvb/v4l/firedtv-1394.c:191: error: invalid use of undefined type 'struct unit_directory'
/root/v4l-dvb/v4l/firedtv-1394.c:196: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:198: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/root/v4l-dvb/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:198: warning: assignment makes pointer from integer without a cast
/root/v4l-dvb/v4l/firedtv-1394.c: At top level:
/root/v4l-dvb/v4l/firedtv-1394.c:257: warning: 'struct unit_directory' declared inside parameter list
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'node_update':
/root/v4l-dvb/v4l/firedtv-1394.c:259: error: dereferencing pointer to incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c: At top level:
/root/v4l-dvb/v4l/firedtv-1394.c:267: error: variable 'fdtv_driver' has initializer but incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:268: error: unknown field 'name' specified in initializer
/root/v4l-dvb/v4l/firedtv-1394.c:268: warning: excess elements in struct initializer
/root/v4l-dvb/v4l/firedtv-1394.c:268: warning: (near initialization for 'fdtv_driver')
/root/v4l-dvb/v4l/firedtv-1394.c:269: error: unknown field 'id_table' specified in initializer
/root/v4l-dvb/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/root/v4l-dvb/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/root/v4l-dvb/v4l/firedtv-1394.c:270: error: unknown field 'update' specified in initializer
/root/v4l-dvb/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/root/v4l-dvb/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/root/v4l-dvb/v4l/firedtv-1394.c:271: error: unknown field 'driver' specified in initializer
/root/v4l-dvb/v4l/firedtv-1394.c:271: error: extra brace group at end of initializer
/root/v4l-dvb/v4l/firedtv-1394.c:271: error: (near initialization for 'fdtv_driver')
/root/v4l-dvb/v4l/firedtv-1394.c:274: warning: excess elements in struct initializer
/root/v4l-dvb/v4l/firedtv-1394.c:274: warning: (near initialization for 'fdtv_driver')
/root/v4l-dvb/v4l/firedtv-1394.c:277: error: variable 'fdtv_highlevel' has initializer but incomplete type
/root/v4l-dvb/v4l/firedtv-1394.c:278: error: unknown field 'name' specified in initializer
/root/v4l-dvb/v4l/firedtv-1394.c:278: warning: excess elements in struct initializer
/root/v4l-dvb/v4l/firedtv-1394.c:278: warning: (near initialization for 'fdtv_highlevel')
/root/v4l-dvb/v4l/firedtv-1394.c:279: error: unknown field 'fcp_request' specified in initializer
/root/v4l-dvb/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/root/v4l-dvb/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/root/v4l-dvb/v4l/firedtv-1394.c:286: error: implicit declaration of function 'hpsb_register_highlevel'
/root/v4l-dvb/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_protocol'
/root/v4l-dvb/v4l/firedtv-1394.c:290: error: implicit declaration of function 'hpsb_unregister_highlevel'
/root/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/root/v4l-dvb/v4l/firedtv-1394.c:297: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/root/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/root/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/root/v4l-dvb/v4l'
make: *** [all] Error 2

```

The output of lspci -v -s 00:09.0
```

root@hush-desktop:~/v4l-dvb# lspci -v -s 00:09.0
00:09.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)
        Subsystem: TERRATEC Electronic GmbH Device 1178
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f7f00000 (32-bit, prefetchable) [size=4K]

```

And the output of lspci -vvn -s 00:09.0
```

root@hush-desktop:~/v4l-dvb#  lspci -vvn -s 00:09.0
00:09.0 0480: 1822:4e35 (rev 01)
        Subsystem: 153b:1178
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (2000ns min, 63750ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at f7f00000 (32-bit, prefetchable) [size=4K]

```

I've also tried this:
[http://jusst.de/hg/mantis/archive/08f27ef99d74.tar.bz2]("http://jusst.de/hg/mantis/archive/08f27ef99d74.tar.bz2")
But still no luck.

Many thanks in advance.

---

### Post by ian dobson on 2010-04-08
Hi,

Are you sure you have the linux-headers installed?

It looks as if the firedtv-1394 driver doesn't compile. Maybe try manually editing the Makefile to exclude the firedtv driver.

Regards
Ian Dobson

---

### Post by jurgen69 on 2010-04-08
Hi,

Thanks for you reply.

> 
Are you sure you have the linux-headers installed?

Sorry I don't know what linux-headers are

Do you mean the Make file in the "v4l-dvb" directory, if so I  don't know how to do that, here is the Makefile:
```

BUILD_DIR := $(shell pwd)/v4l
TMP ?= /tmp
REPO_PULL := http://linuxtv.org/hg/v4l-dvb

ifeq ($(EDITOR),)
  ifeq ($(VISUAL),)
        EDITOR := vi
  else
        EDITOR := $(VISUAL) -w
  endif
endif

all:

install:
        $(MAKE) -C $(BUILD_DIR) install

# Hmm, .PHONY does not work with wildcard rules :-(
SPECS = media-specs

.PHONY: $(SPECS)

$(SPECS):
        $(MAKE) -C $(BUILD_DIR) $(MAKECMDGOALS)

%::
        $(MAKE) -C $(BUILD_DIR) $(MAKECMDGOALS)

commit cvscommit hgcommit change changes changelog:: whitespace
        @cd $(BUILD_DIR); scripts/cardlist; scripts/do_commit.sh $(EDITOR) $(TMP)/v4l_hg_whitespace; cd ..

qrefresh: Q=q
qrefresh:: whitespace
        cd $(BUILD_DIR); scripts/cardlist; cd ..
        v4l/scripts/prep_commit_msg.pl -q $(TMP)/v4l_hg_whitespace > \
                $(TMP)/v4l_hg_commit.msg
        $(EDITOR) $(TMP)/v4l_hg_commit.msg
        grep -v '^#' $(TMP)/v4l_hg_commit.msg | hg qrefresh -g -l -

pull update v4l-update::
        @echo "Pulling changes from master repository $(REPO_PULL)"
        -hg pull -u $(REPO_PULL)

push::
        @echo "Pushing changes to master repository"
        -hg push
whitespace whitespaces:
        @echo "Cleaning bad whitespaces"
        @v4l/scripts/strip-trailing-whitespaces.sh $(Q)fast | \
                tee $(TMP)/v4l_hg_whitespace | patch -p0

```

I can't see any mention of  firedtv-1394.
Sorry if I'm being thick here
Many thanks

---

### Post by ian dobson on 2010-04-08
Hi,

To install the linux header just go the terminal and enter
sudo apt-get install linux-headers-$(uname -r) build-essential

Maybe try deleteing /root/v4l-dvb/v4l/firedtv-1394.c as that driver seems to be blowing up when compiling for some reason.

Regards
Ian Dobson

---

### Post by jurgen69 on 2010-04-13
Hi Ian,

Thanks for your help, The firedtv-1394.c driver was the problem.

I found the solution in his post. [http://ubuntuforums.org/showthread.php?t=1305228](http://ubuntuforums.org/showthread.php?t=1305228)

Now the the whole thing compiles, I still have not managed to get Mythtv working, but I'm getting closer.

BTW does anyone know where the channels.conf is located.

I've tried to search for it using this code:
> 
find / -name channels.conf

but no luck.

---

### Post by ian dobson on 2010-04-13
Hi,

You need to create a channels.conf. I usually use w_scan (wscan) to scan my DVB-C channels that I can then import into mythtv.

Regards
Ian Dobson

---

### Post by jalyst on 2010-04-22
Are you in a region where encryption is used on your payTV service?
How are you approaching/dealing with that?

I'm in Australia using Foxtel, where NDS (VideoGuard2) is used.
There seems to be several different approaches one can take, and I'm overwhelmed by which way to go!

> **jurgen69 said:**
> Hi All,

I'm building a HTPC and I have installed a fresh copy of Mythbuntu. I'm using a TerraTec Cinergy C DVB-C.

I have followed the instructions in the following link:

[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C]("http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C")

And I've also used tried this post:

[http://ubuntuforums.org/showthread.php?t=857524&highlight=cinergy+terratec]("http://ubuntuforums.org/showthread.php?t=857524&highlight=cinergy+terratec")

My problem is this, when I try to "make" the driver I get the following errors
[code]
root@hush-desktop:~/v4l-dvb# make all


---

### Post by jalyst on 2010-04-24
Anyone? Thank-you.

I've started a dedicated thread here
[http://www.austech.info/satellite-tv-general/35842-best-card-server-related-apps-me.html#post289253](http://www.austech.info/satellite-tv-general/35842-best-card-server-related-apps-me.html#post289253)

And for any gungho admins....
What I'm proposing has nothing to do with breaking any law in Australia.
So before shooting, ask questions!

Thank-you.

---

### Post by jalyst on 2010-05-03
I don't suppose I could get some thoguhts on this? thank-you.

---

