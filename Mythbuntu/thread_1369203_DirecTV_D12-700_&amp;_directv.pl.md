---
title: "DirecTV D12-700 &amp; directv.pl"
date: 2009-12-31
forum: Mythbuntu
---

### Post by AlanBryant on 2009-12-31
Hi everyone,

I have a MythTV network at my house that I have been using mainly for sharing movies hosted on the backend to remote frontends.

I have two DirecTV receivers hooked up to my backend via two PVR-150's. The model #'s are D12-100 & D12-700.

I can change channels on the D12-100 receiver via directv.pl on the command line (haven't tried in MythTV), but the D12-700 times out no matter what command is sent. I have both of them hooked up via identical pl2303 chipset serial 2 usb adapters with a null modem adapter in between. Again, the hook up is identical and the D12-100 works with no issues.

Here is an output from the CLI with the D12-700 with the directv3.pl script floating around:

```
alan@server:~$ ./directv3.pl port /dev/D12-700 box_type D11 verbose get_channel
Initializing Serial Port... done!
SEND: 0xFA [&#65533;] 0x87 [&#65533;] 
RECV: Timeout Error


Retry Thu Dec 31 14:28:30 2009
SEND: 0xFA [&#65533;] 0x87 [&#65533;] 
RECV: Timeout Error


Retry Thu Dec 31 14:28:32 2009
SEND: 0xFA [&#65533;] 0x87 [&#65533;] 
RECV: Timeout Error


Retry Thu Dec 31 14:28:34 2009
SEND: 0xFA [&#65533;] 0x87 [&#65533;] 
RECV: Timeout Error


Retry Thu Dec 31 14:28:36 2009
Error excessive retries
alan@server:~$
```

Here is output from the directv.pl script:

```
alan@server:~$ /usr/local/bin/directva.pl port /dev/D12-700 box_type D11 verbose setup_channel 299
SEND: 0xFA [&#65533;] 0x82 [&#65533;] 0x0 [] 
RECV: Timeout Error


SEND: 0xFA [&#65533;] 0x82 [&#65533;] 0x0 [] 
RECV: Timeout Error


SEND: 0xFA [&#65533;] 0x82 [&#65533;] 0x0 [] 
RECV: Timeout Error


SEND: 0xFA [&#65533;] 0x82 [&#65533;] 0x0 [] 
RECV: Timeout Error


Error excessive retries
alan@server:~$
```

Output from directv.pl with D12-100:

```
alan@server:~$ /usr/local/bin/directvb.pl port /dev/D12-100 box_type D11 verbose setup_channel 299
SEND: 0xFA [&#65533;] 0x82 [&#65533;] 0x0 [] 
RECV: 0xF0[START PKT] 0xF4[END PKT] 

SEND: 0xFA [&#65533;] 0xA5 [&#65533;] 0x0 [] 0x1 [ ] 0xE2 [&#65533;] 0x0 [] 
RECV: 0xF0[START PKT] 0xF2[GOT EXTENDED] 0xF4[END PKT] 

SEND: 0xFA [&#65533;] 0xA5 [&#65533;] 0x0 [] 0x1 [ ] 0xE9 [&#65533;] 0x0 [] 
RECV: 0xF0[START PKT] 0xF2[GOT EXTENDED] 0xF4[END PKT] 

SEND: 0xFA [&#65533;] 0xA5 [&#65533;] 0x0 [] 0x1 [ ] 0xE9 [&#65533;] 0x0 [] 
RECV: 0xF0[START PKT] 0xF2[GOT EXTENDED] 0xF4[END PKT] 

SEND: 0xFA [&#65533;] 0xA5 [&#65533;] 0x0 [] 0x1 [ ] 0xA0 [&#65533;] 0x0 [] 
RECV: 0xF0[START PKT] 0xF2[GOT EXTENDED] 0xF4[END PKT] 

SEND: 0xFA [&#65533;] 0xA5 [&#65533;] 0x0 [] 0x1 [ ] 0xD4 [&#65533;] 0x0 [] 
RECV: 0xF0[START PKT] 0xF2[GOT EXTENDED] 0xF4[END PKT] 

SEND: 0xFA [&#65533;] 0x87 [&#65533;] 0x0 [] 
RECV: 0xF0[START PKT] 0x01(  1) 0x2B( 43) 0xFF(255) 0xFF(255) 0xF4[END PKT] 

alan@server:~$
```

Anyone got any ideas? I have not even found anyone posting anything about a D12-700 box with MythTV yet.

---

### Post by AlanBryant on 2009-12-31
I have somehow fixed the problem.

With recommendations from the MythTV Mailing List I switched the cable set at the receivers and voila, they both work.

I'm not so much convinced it was switching the cables as much as re-initializing the USB ports on the receivers, maybe?

In any case, we now know that D12-700 receivers do in fact work with the directv.pl script.

---

