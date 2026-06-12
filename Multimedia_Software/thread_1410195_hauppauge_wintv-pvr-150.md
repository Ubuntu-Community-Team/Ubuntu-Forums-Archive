---
title: "hauppauge wintv-pvr-150"
date: 2010-02-18
forum: Multimedia Software
---

### Post by markp1989 on 2010-02-18
I had this tv card working with ubuntu 9.04 a while back, and have just put it in my 9.10 pc. 

lspci doesnt seem to know what it is? 

and 

```
05:01.0 Non-VGA unclassified device: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```

and the ivtv module also seems to be confuzd about the card. 
```

mark@torrentslave:~$ dmesg | grep tv
[    8.013288] ivtv: Start initialization, version 1.4.1
[    8.013453] ivtv0: Initializing card 0
[    8.013455] ivtv0: Unknown card: vendor/device: [4444:0016]
[    8.013488] ivtv0:               subsystem vendor/device: [0000:0000]
[    8.013520] ivtv0:               cx23416 based
[    8.013550] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[    8.013581] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[    8.013616] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[    8.013649] ivtv0: Prefix your subject line with [UNKNOWN IVTV CARD].
[    8.013692] ivtv0: Cannot request encoder memory region.
[    8.013728] ivtv0: Error -5 on initialization
[    8.013765] ivtv: probe of 0000:05:01.0 failed with error -5
[    8.013774] ivtv: End initialization
mark@torrentslave:~$ 
```


any one got this card working under 9.10 i have searched around and all i can find are old threads.

thanks Markp1989

---

