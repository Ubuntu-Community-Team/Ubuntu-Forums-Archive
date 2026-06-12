---
title: "Compiling BlackGold Linux Drivers"
date: 2013-05-27
forum: Multimedia Software
---

### Post by daniel.pool on 2013-05-27
Hey,

On May 21st BlackGold managed to finally get past the proprietary blocks they had on releasing the source for their drivers on Linux (prior to this they just had some binary drivers for specific Kernel versions that they would release from time to time).

I've been trying to compile these drivers today with not very much luck; I wonder that it may be because my server is using kernel version 3.2.0.44 (12.04 LTS) and gcc 4.6.3 whereas BGT have tested this on kernel version 3.9.1 and gcc 4.7.3. That said the error I'm getting looks more like a code error:

```

$ make -j4

make -C firmware prep
creating symbolic links...
make[1]: Entering directory `/home/daniel/bgt-linux-pcie-drv/v4l/firmware'
make[1]: Leaving directory `/home/daniel/bgt-linux-pcie-drv/v4l/firmware'
make -C firmware
make[1]: Entering directory `/home/daniel/bgt-linux-pcie-drv/v4l/firmware'
make[1]: Nothing to be done for `default'.
make[1]: Leaving directory `/home/daniel/bgt-linux-pcie-drv/v4l/firmware'
Kernel build directory is /lib/modules/3.2.0-44-generic/build
make -C /lib/modules/3.2.0-44-generic/build SUBDIRS=/home/daniel/bgt-linux-pcie-drv/v4l CFLAGS="-I/usr/include -D__KERNEL__ -I/include -DEXPORT_SYMTAB" modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-44-generic'
  CC [M]  /home/daniel/bgt-linux-pcie-drv/v4l/tuner-simple.o
  CC [M]  /home/daniel/bgt-linux-pcie-drv/v4l/tuner-types.o
  CC [M]  /home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.o
  CC [M]  /home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_c.o
/home/daniel/bgt-linux-pcie-drv/v4l/tuner-types.c:1871:3: error: 'TUNER_XC5000C' undeclared here (not in a function)
/home/daniel/bgt-linux-pcie-drv/v4l/tuner-types.c:1871:2: error: array index in initializer not of integer type
/home/daniel/bgt-linux-pcie-drv/v4l/tuner-types.c:1871:2: error: (near initialization for 'tuners')
make[2]: *** [/home/daniel/bgt-linux-pcie-drv/v4l/tuner-types.o] Error 1
make[2]: *** Waiting for unfinished jobs....
In file included from /home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_priv.h:26:0,
                 from /home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:22:
/home/daniel/bgt-linux-pcie-drv/v4l/dvb_frontend.h:358:23: error: field 'interleaving' has incomplete type
In file included from /home/daniel/bgt-linux-pcie-drv/v4l/tuner-simple.h:21:0,
                 from /home/daniel/bgt-linux-pcie-drv/v4l/tuner-simple.c:14:
/home/daniel/bgt-linux-pcie-drv/v4l/dvb_frontend.h:358:23: error: field 'interleaving' has incomplete type
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: In function 'cxd2820r_set_frontend':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:262:7: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:262:7: note: each undeclared identifier is reported only once for each function it appears in
In file included from /home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_priv.h:26:0,
                 from /home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_c.c:22:
/home/daniel/bgt-linux-pcie-drv/v4l/dvb_frontend.h:358:23: error: field 'interleaving' has incomplete type
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: In function 'cxd2820r_read_status':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:294:7: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: In function 'cxd2820r_get_frontend':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:322:7: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: In function 'cxd2820r_read_ber':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:347:7: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_c.c: In function 'cxd2820r_set_frontend_c':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_c.c:57:32: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_c.c:57:32: note: each undeclared identifier is reported only once for each function it appears in
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: In function 'cxd2820r_read_signal_strength':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:372:7: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: In function 'cxd2820r_read_snr':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:397:7: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: In function 'cxd2820r_read_ucblocks':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:422:7: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: In function 'cxd2820r_sleep':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:452:7: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: In function 'cxd2820r_get_tune_settings':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:478:7: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: In function 'cxd2820r_search':
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:524:7: error: 'SYS_DVBC_ANNEX_A' undeclared (first use in this function)
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c: At top level:
/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.c:641:35: error: 'SYS_DVBC_ANNEX_A' undeclared here (not in a function)
make[2]: *** [/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_c.o] Error 1
make[2]: *** [/home/daniel/bgt-linux-pcie-drv/v4l/cxd2820r_core.o] Error 1
make[2]: *** [/home/daniel/bgt-linux-pcie-drv/v4l/tuner-simple.o] Error 1
make[1]: *** [_module_/home/daniel/bgt-linux-pcie-drv/v4l] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-44-generic'
make: *** [default] Error 2

```

If there is anyone else out there trying to get these drivers working, I'd appreciate some help.

Cheers,
~Dan

---

### Post by daniel.pool on 2013-05-28
So, I've tried it on a VM running 13.04 and it compiles fine; didn't work on 12.10 though. I'm guessing that some changes were made to video4linux which haven't been backported into the 12.04 kernel ... as I couldn't be bothered to spend time trying to figure that out, I just upgraded my server to 13.04 for now. It isn't a mission critical machine, just a PVR, so I can live with that.

For anyone else looking to compile, you will need at least Kernel version 3.8.0. Also note that you'll need to chmod all the scripts in the v4l/scripts folder so that you have execute permissions on them. You'll also need to run the menuconfig as sudo otherwise you'll get a permission denied error.

I'll provide more updates as I progress ... It's late now, but I have yet to install the new modules and attempt a scan with the card.

---

### Post by daniel.pool on 2013-05-31
Right, update.

I have attempted to install the compiled modules, but I don't think that this has worked. I get this:
```

$ dmesg | grep dvb
[   17.353654] dvb_core: disagrees about version of symbol module_layout

```

If I try to run a w_scan I get a whole load of i/o errors; so I'm guessing that something isn't right. a [question]("http://stackoverflow.com/questions/2720177/module-layout-version-incompatibility") I've found on stackoverflow suggests that this is something to do with configuration options.
> Note that even if the running kernel and kernel source have the same  numerical value (e.g. both are 2.6.31-20-server), if the two use  different configuration options, you may see this error

I'm a little out of my depth with resolving this issue. I'm hoping the solution is not to push my Kernel version to 3.9.1 (the kernel version BlackGold have verified this module working with) as that isn't officially supported by Ubuntu and I don't want to deal with the quirks of that on a server. Can anyone give any hints on how to get to the bottom of this?

Thanks,

---

### Post by Halfwit on 2013-06-22
Hi Daniel,
Did you ever get this working?
I too have a Blackgold tuner and would like to try it with MythTV.
Thanks.

---

### Post by daniel.pool on 2013-06-26
> **Halfwit said:**
> Hi Daniel,
Did you ever get this working?
I too have a Blackgold tuner and would like to try it with MythTV.
Thanks.

Hey Halfwit,

I haven't gotten this working yet, to be honest though it fell to the bottom of my priorities for other reasons.

I discovered that the dmesg error was because Ubuntu appeared to be loading the old dvb_core module rather than the newly compiled one. I tried an update-initramfs -u which didn't seem to fix the problem, but running a make install after reboot seems to cause no issues.

I was able to successfully scan for channels including freeview HD channels, however I am unable to tune into the channels with the card returning a "no input error". This was the last I managed to achieve, before various other things have crept in the way.

Have you tried anything yourself?

---

### Post by Halfwit on 2013-07-01
I’ve never used Linux before now, so this is all very new to me (although I know my way around a PC pretty well in windows and written applications).

I didn’t get very far trying to build the drivers with Ubuntu, so I installed Kubuntu instead, since that is what BlackGold say they used to test the drivers, so that’s bound to work :)

I failed to get it to build with this either. The errors I’m getting are different to those in your original post, but happen around the same place.

```

make -j4
make -C firmware prep
creating symbolic links...
make[1]: Entering directory `/home/cliff/bgt-linux-pcie-drv/v4l/firmware'
make[1]: Leaving directory `/home/cliff/bgt-linux-pcie-drv/v4l/firmware'
make -C firmware
make[1]: Entering directory `/home/cliff/bgt-linux-pcie-drv/v4l/firmware'
make[1]: Nothing to be done for `default'.
make[1]: Leaving directory `/home/cliff/bgt-linux-pcie-drv/v4l/firmware'
Kernel build directory is /lib/modules/3.8.0-19-generic/build
make -C /lib/modules/3.8.0-19-generic/build SUBDIRS=/home/cliff/bgt-linux-pcie-drv/v4l CFLAGS="-I/usr/include -D__KERNEL__ -I/include -DEXPORT_SYMTAB" modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/cliff/bgt-linux-pcie-drv/v4l/tuner-simple.o
  CC [M]  /home/cliff/bgt-linux-pcie-drv/v4l/cxd2820r_core.o
  CC [M]  /home/cliff/bgt-linux-pcie-drv/v4l/cxd2820r_c.o
  CC [M]  /home/cliff/bgt-linux-pcie-drv/v4l/cxd2820r_t.o
In file included from /home/cliff/bgt-linux-pcie-drv/v4l/cxd2820r_priv.h:26:0,
                 from /home/cliff/bgt-linux-pcie-drv/v4l/cxd2820r_c.c:22:
/home/cliff/bgt-linux-pcie-drv/v4l/dvb_frontend.h:398:22: error: field 'strength' has incomplete type
/home/cliff/bgt-linux-pcie-drv/v4l/dvb_frontend.h:399:22: error: field 'cnr' has incomplete type
/home/cliff/bgt-linux-pcie-drv/v4l/dvb_frontend.h:400:22: error: field 'pre_bit_error' has incomplete type
/home/cliff/bgt-linux-pcie-drv/v4l/dvb_frontend.h:401:22: error: field 'pre_bit_count' has incomplete type
/home/cliff/bgt-linux-pcie-drv/v4l/dvb_frontend.h:402:22: error: field 'post_bit_error' has incomplete type
/home/cliff/bgt-linux-pcie-drv/v4l/dvb_frontend.h:403:22: error: field 'post_bit_count' has incomplete type
/home/cliff/bgt-linux-pcie-drv/v4l/dvb_frontend.h:404:22: error: field 'block_error' has incomplete type
/home/cliff/bgt-linux-pcie-drv/v4l/dvb_frontend.h:405:22: error: field 'block_count' has incomplete type
 <snip>
make[2]: *** [/home/cliff/bgt-linux-pcie-drv/v4l/cxd2820r_c.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[2]: *** [/home/cliff/bgt-linux-pcie-drv/v4l/cxd2820r_t.o] Error 1
make[2]: *** [/home/cliff/bgt-linux-pcie-drv/v4l/cxd2820r_core.o] Error 1
make[2]: *** [/home/cliff/bgt-linux-pcie-drv/v4l/tuner-simple.o] Error 1
make[1]: *** [_module_/home/cliff/bgt-linux-pcie-drv/v4l] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [default] Error 2
MyKubuntu:~/bgt-linux-pcie-drv/v4l$  

```


I’ve either done something wrong, or I didn’t install the exact same version of Kubuntu.

I’m not entirely sure what versions I’ve installed and haven’t yet discovered how to find out.

Anyway I’m stuck now, but I will continue to chip away at it.

I wanted to try this because I have had enough of windows media center (which is where the tuner cards are currently being used).

---

### Post by daniel.pool on 2013-07-18
> **Halfwit said:**
> I’ve never used Linux before now, so this is all very new to me (although I know my way around a PC pretty well in windows and written applications).

I didn’t get very far trying to build the drivers with Ubuntu, so I installed Kubuntu instead, since that is what BlackGold say they used to test the drivers, so that’s bound to work :)

I failed to get it to build with this either. The errors I’m getting are different to those in your original post, but happen around the same place.

<snip> ... </snip>


I’ve either done something wrong, or I didn’t install the exact same version of Kubuntu.

I’m not entirely sure what versions I’ve installed and haven’t yet discovered how to find out.

Anyway I’m stuck now, but I will continue to chip away at it.

I wanted to try this because I have had enough of windows media center (which is where the tuner cards are currently being used).

Hey Halfwit,

I'm really sorry that I never got back to you; I've had some serious internet problems which has resulted in my completely replacing routers/modems etc. Needless to say my major UK internet provider bent over backwards to help with the issue ... *"Oh, you've been without internet because the router we provided doesn't work? So sad. Your connection rate has been busted down to slower than dial-up because of that faulty router? Shame. That'll be £45 for a month of no internet, and no we aren't going to replace or fix the hardware we provided*".

Anyway, rant over.

The only way I found I could fix these similar compilation issues was to update to the latest version of Ubuntu (in my case 13.04). Type:

```
uname -r
```

Into a console window and tell me what is output; I get "3.8.0-23-generic", which seemed to be the minimum version that is required to compile. The instructions from the BGT suggest that they had used an even newer Kernel version, but that would require manually updating your Kernel, which is something that I haven't been willing to do.

Unfortunately as I mentioned before I haven't got the card working; it'll scan, but it won't tune to any channel, I haven't looked into this any further and it is still at the bottom of my to do list (which certain ISPs haven't made shorter). I don't know if in the mean time you have managed to get any further, I'd like to know if you have.

~Dan

---

