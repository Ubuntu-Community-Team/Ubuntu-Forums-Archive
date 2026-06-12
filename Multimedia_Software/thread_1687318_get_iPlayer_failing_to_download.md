---
title: "get_iPlayer failing to download"
date: 2011-02-13
forum: Multimedia Software
---

### Post by chome4 on 2011-02-13
Installed v2.79. Went OK

When trying to download a program, I get:

INFO: 1 Matching Programmes
INFO: Checking existence of default version
ERROR: Failed to get iphone URL from iplayer site

INFO: No specified modes (iphone) available for this programme with version 'default' (try using --modes=flashhigh,flashlow,flashstd,flashvhigh,n95_3g,n95_wifi,rtsphigh,rtsplow,rtspstd,rtspvhigh,subtitles)
ERROR: Failed to record 'Young, Jobless and Living at Home - - (b00yk31l)'
=======================================================

What do I need to do to get this to work?

Thanks in advance.

---

### Post by ron999 on 2011-02-13
Show your command please.

---

### Post by chome4 on 2011-02-13
I type: get_iplayer --get 912

That works in my Windows XP I've got running.

---

### Post by ron999 on 2011-02-13
What happens when you enter:-
```
rtmpdump
```

---

### Post by chome4 on 2011-02-13
rtmpdump
bash: rtmpdump: command not found

---

### Post by ron999 on 2011-02-14
> **chome4 said:**
> rtmpdump
bash: rtmpdump: command not found
OK, you need to install **RTMPDump v2.3**.
The iPhone feeds aren't available any more (as it said in the error report).
We have to download the flash feeds instead.
So we need rtmpdump to do this.
The Windows version of get_iplayer installs rtmpdump automatically - that's why your commands work ok with Windows.

---

### Post by chome4 on 2011-02-14
I've downloaded it to the same directory as get_iplayer. How do I configure it?

---

### Post by ron999 on 2011-02-14
Hi
RTMPDump needs to be compiled first.
This is the method that I used:-[http://art.ubuntuforums.org/showpost.php?p=9626752&postcount=6]("http://art.ubuntuforums.org/showpost.php?p=9626752&postcount=6")
And this is another method:-[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9772706&postcount=7]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9772706&postcount=7")

---

### Post by chome4 on 2011-02-14
Now getting: INFO: No specified modes (iphone) available for this programme with version 'default' (try using --modes=flashhigh,flashlow,flashstd,flashvhigh,n95_3g,n95_wifi,rtsphigh,rtsplow,rtspstd,rtspvhigh,subtitles)
ERROR: Failed to record 'World Business Report - 08/02/2011 (b00yfkzh)'

The second method give:

p@p:~$ sudo apt-get -y install build-essential checkinstall libssl-dev && \ wget [http://rtmpdump.mplayerhq.hu/download/rtmpdump-2.3.tgz](http://rtmpdump.mplayerhq.hu/download/rtmpdump-2.3.tgz) && \ tar xvf rtmpdump-2.3.tgz && cd rtmpdump-2.3 && \ make SYS=posix && \ sudo checkinstall && sudo ldconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8g-15ubuntu3) but 0.9.8g-15ubuntu3.6 is to be installed
E: Broken packages

---

### Post by ron999 on 2011-02-14
> **chome4 said:**
> 
The second method give:

The following packages have unmet dependencies.
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8g-15ubuntu3) but 0.9.8g-15ubuntu3.6 is to be installed
E: Broken packages

Try the first method instead.

---

### Post by chome4 on 2011-02-14
The first part of the first method gives:

p@p:~/rtmpdump-2.3$ make SYS=posix
make[1]: Entering directory `/home/p/rtmpdump-2.3/librtmp'
gcc -Wall   -DRTMPDUMP_VERSION=\"v2.3\" -DUSE_OPENSSL  -O2 -fPIC   -c -o rtmp.o rtmp.c
rtmp.c:40:25: error: openssl/ssl.h: No such file or directory
rtmp.c:41:25: error: openssl/rc4.h: No such file or directory
rtmp.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from rtmp.c:126:
handshake.h:63:25: error: openssl/sha.h: No such file or directory
handshake.h:64:26: error: openssl/hmac.h: No such file or directory
handshake.h:67:2: error: #error Your OpenSSL is too old, need 0.9.8 or newer with SHA256
In file included from rtmp.c:126:
handshake.h:73: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from handshake.h:83,
                 from rtmp.c:126:
dh.h:125:24: error: openssl/bn.h: No such file or directory
dh.h:126:24: error: openssl/dh.h: No such file or directory
In file included from handshake.h:83,
                 from rtmp.c:126:
dh.h:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from handshake.h:83,
                 from rtmp.c:126:
dh.h:155: error: expected ‘)’ before ‘y’
dh.h:205: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
dh.h:238: error: expected ‘)’ before ‘*’ token
dh.h:272: error: expected ‘)’ before ‘*’ token
dh.h:308: error: expected ‘)’ before ‘*’ token
In file included from rtmp.c:126:
handshake.h:113: error: expected declaration specifiers or ‘...’ before ‘RC4_handle’
handshake.h:113: error: expected declaration specifiers or ‘...’ before ‘RC4_handle’
handshake.h: In function ‘InitRC4Encryption’:
handshake.h:115: error: ‘SHA256_DIGEST_LENGTH’ undeclared (first use in this function)
handshake.h:115: error: (Each undeclared identifier is reported only once
handshake.h:115: error: for each function it appears in.)
handshake.h:117: error: ‘HMAC_CTX’ undeclared (first use in this function)
handshake.h:117: error: expected ‘;’ before ‘ctx’
handshake.h:119: error: ‘rc4keyIn’ undeclared (first use in this function)
handshake.h:119: error: ‘RC4_KEY’ undeclared (first use in this function)
handshake.h:120: error: ‘rc4keyOut’ undeclared (first use in this function)
handshake.h:122: warning: implicit declaration of function ‘HMAC_CTX_init’
handshake.h:122: error: ‘ctx’ undeclared (first use in this function)
handshake.h:122: warning: implicit declaration of function ‘HMAC_Init_ex’
handshake.h:122: warning: implicit declaration of function ‘EVP_sha256’
handshake.h:123: warning: implicit declaration of function ‘HMAC_Update’
handshake.h:124: warning: implicit declaration of function ‘HMAC_Final’
handshake.h:124: warning: implicit declaration of function ‘HMAC_CTX_cleanup’
handshake.h:129: warning: implicit declaration of function ‘RC4_set_key’
handshake.h:115: warning: unused variable ‘digest’
handshake.h: In function ‘HMACsha256’:
handshake.h:266: error: ‘HMAC_CTX’ undeclared (first use in this function)
handshake.h:266: error: expected ‘;’ before ‘ctx’
handshake.h:268: error: ‘ctx’ undeclared (first use in this function)
handshake.h: In function ‘CalculateDigest’:
handshake.h:279: error: ‘SHA256_DIGEST_LENGTH’ undeclared (first use in this function)
handshake.h:280: warning: unused variable ‘message’
handshake.h: In function ‘VerifyDigest’:
handshake.h:294: error: ‘SHA256_DIGEST_LENGTH’ undeclared (first use in this function)
handshake.h:294: warning: unused variable ‘calcDigest’
handshake.h: In function ‘HandShake’:
handshake.h:369: error: ‘RC4_handle’ undeclared (first use in this function)
handshake.h:369: error: expected ‘;’ before ‘keyIn’
handshake.h:370: error: expected ‘;’ before ‘keyOut’
handshake.h:438: warning: implicit declaration of function ‘DHInit’
handshake.h:438: warning: assignment makes pointer from integer without a cast
handshake.h:449: warning: implicit declaration of function ‘DHGenerateKey’
handshake.h:456: warning: implicit declaration of function ‘DHGetPublicKey’
handshake.h:472: error: ‘SHA256_DIGEST_LENGTH’ undeclared (first use in this function)
handshake.h:559: warning: implicit declaration of function ‘DHComputeSharedSecretKey’
handshake.h:573: error: ‘keyIn’ undeclared (first use in this function)
handshake.h:573: error: ‘keyOut’ undeclared (first use in this function)
handshake.h:573: error: too many arguments to function ‘InitRC4Encryption’
handshake.h:513: warning: unused variable ‘digestResp’
handshake.h:719: warning: implicit declaration of function ‘RC4’
handshake.h:651: warning: unused variable ‘digest’
handshake.h:650: warning: unused variable ‘signature’
handshake.h: In function ‘SHandShake’:
handshake.h:747: error: ‘RC4_handle’ undeclared (first use in this function)
handshake.h:747: error: expected ‘;’ before ‘keyIn’
handshake.h:748: error: expected ‘;’ before ‘keyOut’
handshake.h:830: warning: assignment makes pointer from integer without a cast
handshake.h:865: error: ‘SHA256_DIGEST_LENGTH’ undeclared (first use in this function)
handshake.h:947: error: ‘keyIn’ undeclared (first use in this function)
handshake.h:947: error: ‘keyOut’ undeclared (first use in this function)
handshake.h:947: error: too many arguments to function ‘InitRC4Encryption’
handshake.h:884: warning: unused variable ‘digestResp’
handshake.h:1013: warning: unused variable ‘digest’
handshake.h:1012: warning: unused variable ‘signature’
rtmp.c: In function ‘RTMP_TLS_Init’:
rtmp.c:219: warning: implicit declaration of function ‘SSL_load_error_strings’
rtmp.c:220: warning: implicit declaration of function ‘SSL_library_init’
rtmp.c:221: warning: implicit declaration of function ‘OpenSSL_add_all_digests’
rtmp.c:222: error: ‘RTMP_TLS_ctx’ undeclared (first use in this function)
rtmp.c:222: warning: implicit declaration of function ‘SSL_CTX_new’
rtmp.c:222: warning: implicit declaration of function ‘SSLv23_method’
rtmp.c:223: warning: implicit declaration of function ‘SSL_CTX_set_options’
rtmp.c:223: error: ‘SSL_OP_ALL’ undeclared (first use in this function)
rtmp.c:224: warning: implicit declaration of function ‘SSL_CTX_set_default_verify_paths’
rtmp.c: In function ‘RTMP_Init’:
rtmp.c:245: error: ‘RTMP_TLS_ctx’ undeclared (first use in this function)
rtmp.c: In function ‘RTMP_Connect1’:
rtmp.c:859: warning: implicit declaration of function ‘SSL_new’
rtmp.c:859: error: ‘RTMP_TLS_ctx’ undeclared (first use in this function)
rtmp.c:859: warning: assignment makes pointer from integer without a cast
rtmp.c:860: warning: implicit declaration of function ‘SSL_set_fd’
rtmp.c:861: warning: implicit declaration of function ‘SSL_connect’
rtmp.c: In function ‘RTMP_Close’:
rtmp.c:3464: warning: implicit declaration of function ‘DH_free’
rtmp.c: In function ‘RTMPSockBuf_Fill’:
rtmp.c:3494: warning: implicit declaration of function ‘SSL_read’
rtmp.c: In function ‘RTMPSockBuf_Send’:
rtmp.c:3537: warning: implicit declaration of function ‘SSL_write’
rtmp.c: In function ‘RTMPSockBuf_Close’:
rtmp.c:3553: warning: implicit declaration of function ‘SSL_shutdown’
rtmp.c:3554: warning: implicit declaration of function ‘SSL_free’
make[1]: *** [rtmp.o] Error 1
make[1]: Leaving directory `/home/p/rtmpdump-2.3/librtmp'
make: *** [librtmp/librtmp.a] Error 2
===============================================================================================
The second part of the method gives:

p@p:~/rtmpdump-2.3$ sudo make install
[sudo] password for p: 
make[1]: Entering directory `/home/p/rtmpdump-2.3/librtmp'
gcc -Wall   -DRTMPDUMP_VERSION=\"v2.3\" -DUSE_OPENSSL  -O2 -fPIC   -c -o rtmp.o rtmp.c
rtmp.c:40:25: error: openssl/ssl.h: No such file or directory
rtmp.c:41:25: error: openssl/rc4.h: No such file or directory
rtmp.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from rtmp.c:126:
handshake.h:63:25: error: openssl/sha.h: No such file or directory
handshake.h:64:26: error: openssl/hmac.h: No such file or directory
handshake.h:67:2: error: #error Your OpenSSL is too old, need 0.9.8 or newer with SHA256
In file included from rtmp.c:126:
handshake.h:73: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from handshake.h:83,
                 from rtmp.c:126:
dh.h:125:24: error: openssl/bn.h: No such file or directory
dh.h:126:24: error: openssl/dh.h: No such file or directory
In file included from handshake.h:83,
                 from rtmp.c:126:
dh.h:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from handshake.h:83,
                 from rtmp.c:126:
dh.h:155: error: expected ‘)’ before ‘y’
dh.h:205: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
dh.h:238: error: expected ‘)’ before ‘*’ token
dh.h:272: error: expected ‘)’ before ‘*’ token
dh.h:308: error: expected ‘)’ before ‘*’ token
In file included from rtmp.c:126:
handshake.h:113: error: expected declaration specifiers or ‘...’ before ‘RC4_handle’
handshake.h:113: error: expected declaration specifiers or ‘...’ before ‘RC4_handle’
handshake.h: In function ‘InitRC4Encryption’:
handshake.h:115: error: ‘SHA256_DIGEST_LENGTH’ undeclared (first use in this function)
handshake.h:115: error: (Each undeclared identifier is reported only once
handshake.h:115: error: for each function it appears in.)
handshake.h:117: error: ‘HMAC_CTX’ undeclared (first use in this function)
handshake.h:117: error: expected ‘;’ before ‘ctx’
handshake.h:119: error: ‘rc4keyIn’ undeclared (first use in this function)
handshake.h:119: error: ‘RC4_KEY’ undeclared (first use in this function)
handshake.h:120: error: ‘rc4keyOut’ undeclared (first use in this function)
handshake.h:122: warning: implicit declaration of function ‘HMAC_CTX_init’
handshake.h:122: error: ‘ctx’ undeclared (first use in this function)
handshake.h:122: warning: implicit declaration of function ‘HMAC_Init_ex’
handshake.h:122: warning: implicit declaration of function ‘EVP_sha256’
handshake.h:123: warning: implicit declaration of function ‘HMAC_Update’
handshake.h:124: warning: implicit declaration of function ‘HMAC_Final’
handshake.h:124: warning: implicit declaration of function ‘HMAC_CTX_cleanup’
handshake.h:129: warning: implicit declaration of function ‘RC4_set_key’
handshake.h:115: warning: unused variable ‘digest’
handshake.h: In function ‘HMACsha256’:
handshake.h:266: error: ‘HMAC_CTX’ undeclared (first use in this function)
handshake.h:266: error: expected ‘;’ before ‘ctx’
handshake.h:268: error: ‘ctx’ undeclared (first use in this function)
handshake.h: In function ‘CalculateDigest’:
handshake.h:279: error: ‘SHA256_DIGEST_LENGTH’ undeclared (first use in this function)
handshake.h:280: warning: unused variable ‘message’
handshake.h: In function ‘VerifyDigest’:
handshake.h:294: error: ‘SHA256_DIGEST_LENGTH’ undeclared (first use in this function)
handshake.h:294: warning: unused variable ‘calcDigest’
handshake.h: In function ‘HandShake’:
handshake.h:369: error: ‘RC4_handle’ undeclared (first use in this function)
handshake.h:369: error: expected ‘;’ before ‘keyIn’
handshake.h:370: error: expected ‘;’ before ‘keyOut’
handshake.h:438: warning: implicit declaration of function ‘DHInit’
handshake.h:438: warning: assignment makes pointer from integer without a cast
handshake.h:449: warning: implicit declaration of function ‘DHGenerateKey’
handshake.h:456: warning: implicit declaration of function ‘DHGetPublicKey’
handshake.h:472: error: ‘SHA256_DIGEST_LENGTH’ undeclared (first use in this function)
handshake.h:559: warning: implicit declaration of function ‘DHComputeSharedSecretKey’
handshake.h:573: error: ‘keyIn’ undeclared (first use in this function)
handshake.h:573: error: ‘keyOut’ undeclared (first use in this function)
handshake.h:573: error: too many arguments to function ‘InitRC4Encryption’
handshake.h:513: warning: unused variable ‘digestResp’
handshake.h:719: warning: implicit declaration of function ‘RC4’
handshake.h:651: warning: unused variable ‘digest’
handshake.h:650: warning: unused variable ‘signature’
handshake.h: In function ‘SHandShake’:
handshake.h:747: error: ‘RC4_handle’ undeclared (first use in this function)
handshake.h:747: error: expected ‘;’ before ‘keyIn’
handshake.h:748: error: expected ‘;’ before ‘keyOut’
handshake.h:830: warning: assignment makes pointer from integer without a cast
handshake.h:865: error: ‘SHA256_DIGEST_LENGTH’ undeclared (first use in this function)
handshake.h:947: error: ‘keyIn’ undeclared (first use in this function)
handshake.h:947: error: ‘keyOut’ undeclared (first use in this function)
handshake.h:947: error: too many arguments to function ‘InitRC4Encryption’
handshake.h:884: warning: unused variable ‘digestResp’
handshake.h:1013: warning: unused variable ‘digest’
handshake.h:1012: warning: unused variable ‘signature’
rtmp.c: In function ‘RTMP_TLS_Init’:
rtmp.c:219: warning: implicit declaration of function ‘SSL_load_error_strings’
rtmp.c:220: warning: implicit declaration of function ‘SSL_library_init’
rtmp.c:221: warning: implicit declaration of function ‘OpenSSL_add_all_digests’
rtmp.c:222: error: ‘RTMP_TLS_ctx’ undeclared (first use in this function)
rtmp.c:222: warning: implicit declaration of function ‘SSL_CTX_new’
rtmp.c:222: warning: implicit declaration of function ‘SSLv23_method’
rtmp.c:223: warning: implicit declaration of function ‘SSL_CTX_set_options’
rtmp.c:223: error: ‘SSL_OP_ALL’ undeclared (first use in this function)
rtmp.c:224: warning: implicit declaration of function ‘SSL_CTX_set_default_verify_paths’
rtmp.c: In function ‘RTMP_Init’:
rtmp.c:245: error: ‘RTMP_TLS_ctx’ undeclared (first use in this function)
rtmp.c: In function ‘RTMP_Connect1’:
rtmp.c:859: warning: implicit declaration of function ‘SSL_new’
rtmp.c:859: error: ‘RTMP_TLS_ctx’ undeclared (first use in this function)
rtmp.c:859: warning: assignment makes pointer from integer without a cast
rtmp.c:860: warning: implicit declaration of function ‘SSL_set_fd’
rtmp.c:861: warning: implicit declaration of function ‘SSL_connect’
rtmp.c: In function ‘RTMP_Close’:
rtmp.c:3464: warning: implicit declaration of function ‘DH_free’
rtmp.c: In function ‘RTMPSockBuf_Fill’:
rtmp.c:3494: warning: implicit declaration of function ‘SSL_read’
rtmp.c: In function ‘RTMPSockBuf_Send’:
rtmp.c:3537: warning: implicit declaration of function ‘SSL_write’
rtmp.c: In function ‘RTMPSockBuf_Close’:
rtmp.c:3553: warning: implicit declaration of function ‘SSL_shutdown’
rtmp.c:3554: warning: implicit declaration of function ‘SSL_free’
make[1]: *** [rtmp.o] Error 1
make[1]: Leaving directory `/home/p/rtmpdump-2.3/librtmp'
make: *** [librtmp/librtmp.a] Error 2

---

### Post by ron999 on 2011-02-14
> **chome4 said:**
> The first part of the first method gives:

p@p:~/rtmpdump-2.3$ make SYS=posix
make[1]: Entering directory `/home/p/rtmpdump-2.3/librtmp'
gcc -Wall   -DRTMPDUMP_VERSION=\"v2.3\" -DUSE_OPENSSL  -O2 -fPIC   -c -o rtmp.o rtmp.c
rtmp.c:40:25: error: openssl/ssl.h: No such file or directory
rtmp.c:41:25: error: openssl/rc4.h: No such file or directory
rtmp.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from rtmp.c:126:
handshake.h:63:25: error: openssl/sha.h: No such file or directory
handshake.h:64:26: error: openssl/hmac.h: No such file or directory
handshake.h:67:2: error: #error [COLOR="Red"]Your OpenSSL is too old[/COLOR], need 0.9.8 or newer with SHA256

Hi
It looks like the version of OpenSSL that is included with Jaunty is too old to compile RTMPDump.

I've attached the deb for the RTMPDump that I compiled with _Karmic_.
See if it will install for you.

---

### Post by chome4 on 2011-02-14
Worked perfectly and smoothly!!

Thanks.

---

