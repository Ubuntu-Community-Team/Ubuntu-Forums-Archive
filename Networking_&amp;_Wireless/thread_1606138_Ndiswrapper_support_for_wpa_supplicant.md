---
title: "Ndiswrapper support for wpa_supplicant"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by tstngry on 2010-10-26
[INDENT]I've been working on this problem for a couple days now, and I almost have it figured out, which makes asking for help at this point even more frustrating.[/INDENT]
[INDENT]I did a clean install of 10.10 on my laptop, and everything is peachy, my wireless and everything else works. At first my wireless card was using the B43 driver, which worked well enough. Just for kicks I thought I would try the STA driver as well and it worked too. The only problem with either driver was that they did not work @ the same speed that I was getting in windows xp. So I tried the ndiswrapper gui to install my windows driver for the card, which also worked, and @ full speed. I thought I had my problem solved when i tried to connect to my home network, which is protected with wpa personal and it would not allow me to do so.[/INDENT]
[INDENT]I have narrowed the problem down to wpa_supplicant which currently (under fresh install) does not support the ndiswrapper driver. I have tried to compile wpa_supplicant to include support for ndiswrapper with a custom .config, however this is where i am stuck. Every time i try to compile wpa_supplicant i get the following error:[/INDENT]
```
cc  -o wpa_supplicant config.o notify.o bss.o eap_register.o ../src/utils/common.o ../src/utils/wpa_debug.o ../src/utils/wpabuf.o ../src/utils/os_unix.o ../src/utils/eloop.o config_file.o ../src/rsn_supp/wpa.o ../src/rsn_supp/preauth.o ../src/rsn_supp/pmksa_cache.o ../src/rsn_supp/peerkey.o ../src/rsn_supp/wpa_ie.o ../src/common/wpa_common.o ../src/crypto/crypto_openssl.o ../src/crypto/tls_none.o  ../src/crypto/aes-unwrap.o ../src/crypto/md5.o ctrl_iface.o ctrl_iface_unix.o  ../src/utils/base64.o ../src/crypto/sha1.o ../src/crypto/sha1-pbkdf2.o  wpa_supplicant.o events.o blacklist.o wpas_glue.o scan.o main.o ../src/drivers/driver_ndiswrapper.o ../src/drivers/driver_wext.o  ../src/drivers/drivers.o ../src/l2_packet/l2_packet_linux.o  -lcrypto  
../src/drivers/driver_wext.o: In function `wpa_driver_wext_set_operstate':
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:2159: undefined reference to `netlink_send_oper_ifla'
../src/drivers/driver_wext.o: In function `wpa_driver_wext_set_mode':
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:2055: undefined reference to `linux_set_iface_flags'
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:2063: undefined reference to `linux_set_iface_flags'
../src/drivers/driver_wext.o: In function `wpa_driver_wext_deinit':
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:823: undefined reference to `netlink_send_oper_ifla'
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:824: undefined reference to `netlink_deinit'
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:829: undefined reference to `linux_set_iface_flags'
../src/drivers/driver_wext.o: In function `wpa_driver_wext_finish_drv_init':
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:755: undefined reference to `linux_set_iface_flags'
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:795: undefined reference to `netlink_send_oper_ifla'
../src/drivers/driver_wext.o: In function `wpa_driver_wext_init':
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:728: undefined reference to `netlink_init'
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:744: undefined reference to `netlink_deinit'
../src/drivers/driver_wext.o: In function `wpa_driver_wext_event_rtm_newlink':
/home/rageone/wpa_supplicant-0.7.3/wpa_supplicant/../src/drivers/driver_wext.c:646: undefined reference to `netlink_send_oper_ifla'
collect2: ld returned 1 exit status
make: *** [wpa_supplicant] Error 1
```
[INDENT]I have read a couple people say this was because they didn't have libssl or openssl installed, both of which i installed without any luck. Perhaps i am not building the software correctly, i do no have too much expirience in this area. Or perhaps i am missing some dependecies, however i cannot find any website that lists the correct ones to have installed, and synaptic has no problem re-installing wpa_supplicant.[/INDENT]
[INDENT]Can anyone lay out the exact steps to compile wpa_supplicant with support for ndiswrapper?[/INDENT]
[INDENT]Can anyone tell me which missing dependencies might be causing my compiling problem?[/INDENT]
[INDENT]Finally does anyone know a more simple way to accomplish ndiswrapper support for wpa_supplicant?[/INDENT]
[INDENT]Any help with this problem or any tips that would point me in the right direction would be greatly appreciated. I know many people post problems here, I hope this is not a stupid question, I really have spent hours on this. Thank you in advance.[/INDENT]

---

### Post by tstngry on 2010-10-26
Don't mean to bug, but does anyone know about this, or should i just give up? Is this question even in the right forum, mabey this is more a compiling question idk? Help!?

---

### Post by Der Ritter on 2010-10-26
> **tstngry said:**
> Don't mean to bug, but does anyone know about this, or should i just give up? Is this question even in the right forum, mabey this is more a compiling question idk? Help!?

If the problem is easily solvable it is with dependencies -- the error messages look like you are missing at least libnl1. 

Run ```
sudo apt-get build-dep wpasupplicant
```which should install all necessary dependencies and see if it compiles then.

If you have more issues this forum is probably too general, you could try your luck at the [ndiswrapper forum]("http://sourceforge.net/projects/ndiswrapper/forums/forum/323168").

---

### Post by tstngry on 2010-10-27
I am going to boot into ubuntu right now and try the package that you suggested that I install. I did however get an earlier version to compile (0.6.10), so it seems strange to me that one version would have everything it needs to compile and one would not. Thank you for your help and I will look into the ndiswrapper forum.

---

