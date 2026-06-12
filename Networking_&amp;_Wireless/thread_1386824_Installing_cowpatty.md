---
title: "Installing cowpatty"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by alewis on 2010-01-21
Hi

I'm having problems installing Cowpatty

running make produces

cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o md5.o md5.c
md5.c:20:25: error: openssl/md5.h: No such file or directory
md5.c: In function ‘md5_mac’:
md5.c:28: error: ‘MD5_CTX’ undeclared (first use in this function)
md5.c:28: error: (Each undeclared identifier is reported only once
md5.c:28: error: for each function it appears in.)
md5.c:28: error: expected ‘;’ before ‘context’
md5.c:29: warning: implicit declaration of function ‘MD5_Init’
md5.c:29: error: ‘context’ undeclared (first use in this function)
md5.c:30: warning: implicit declaration of function ‘MD5_Update’
md5.c:33: warning: implicit declaration of function ‘MD5_Final’
md5.c: In function ‘hmac_md5_vector’:
md5.c:40: error: ‘MD5_CTX’ undeclared (first use in this function)
md5.c:40: error: expected ‘;’ before ‘context’
md5.c:48: error: ‘context’ undeclared (first use in this function)
make: *** [md5.o] Error 1


Any ideas? Running Ubuntu 9.10 (i386) with latest patches from update manager. If I try using the 4.2 archive I get the same result.

I have similar problems with aircrack-ng suite, but I'll leave that until later!

TVMIA
Alan

---

### Post by kiranmurari on 2010-01-21
Hi,

You need to install libssl-dev package which will install the md5.h header in /usr/include/openssl.
You also need to install libpcap-dev package as cowpatty-4.3/util.c will complain about "pcap.h: No such file or directory"
       
Hope this helps.

---

### Post by alewis on 2010-01-21
To a degree... I know getthis
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o md5.o md5.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o sha1.o sha1.c
In file included from /usr/include/string.h:640,
                 from sha1.c:32:
In function ‘memcpy’,
    inlined from ‘hmac_sha1_vector’ at sha1.c:111:
/usr/include/bits/string3.h:52: warning: call to __builtin___memcpy_chk will always overflow destination buffer
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o utils.o utils.c
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o cowpatty.o cowpatty.c
cowpatty.c: In function ‘main’:
cowpatty.c:912: warning: dereferencing pointer ‘eapkeypacket’ does break strict-aliasing rules
cowpatty.c:909: note: initialized from here
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb   -c -o genpmk.o genpmk.c
genpmk.c: In function ‘main’:
genpmk.c:215: warning: ignoring return value of ‘fopen’, declared with attribute warn_unused_result
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb cowpatty.c -o cowpatty utils.o md5.o sha1.o -lpcap -lcrypto
cowpatty.c: In function ‘main’:
cowpatty.c:912: warning: dereferencing pointer ‘eapkeypacket’ does break strict-aliasing rules
cowpatty.c:909: note: initialized from here
cc -pipe -Wall -DOPENSSL  -O2 -g3 -ggdb genpmk.c -o genpmk utils.o sha1.o -lpcap -lcrypto
genpmk.c: In function ‘main’:
genpmk.c:215: warning: ignoring return value of ‘fopen’, declared with attribute warn_unused_result


Stuck!!!

---

### Post by stim on 2010-01-21
See if you can find relevant information here:

[http://ubuntuforums.org/showthread.php?t=913318]("http://ubuntuforums.org/showthread.php?t=913318")


(search is your friend!)

---

### Post by alewis on 2010-01-21
Indeed it is, but often after a while you need to be able to search the results too.

Anyway, I've got it working using the additional packages in that thread... but I don't know "why" they worked. Ah well, I'll leave that for the next decade!

Thanks for the pointers folks.

---

### Post by alewis on 2010-01-21
solved, cheers

---

