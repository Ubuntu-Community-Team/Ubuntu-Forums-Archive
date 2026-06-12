---
title: "Flash 9 + Soundstorm help"
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by ashakeandfrys on 2007-08-30
Using this guide [here]("http://ubuntuforums.org/showpost.php?p=1716845&postcount=61"), I get stuck at step 5. I receive the following errors from step 5 :```
 jess@jess-desktop:~$ cd /tmp
jess@jess-desktop:/tmp$ cc -shared -O2 -Wall -Werror -licuuc -lssl flashsupport.c -o libflashsupport.so
flashsupport.c:158:25: error: openssl/ssl.h: No such file or directory
cc1: warnings being treated as errors
flashsupport.c: In function ‘FPX_Init’:
flashsupport.c:245: warning: implicit declaration of function ‘SSL_library_init’
flashsupport.c: At top level:
flashsupport.c:268: error: expected specifier-qualifier-list before ‘SSL’
flashsupport.c: In function ‘FPX_SSLSocket_Create’:
flashsupport.c:278: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:278: warning: implicit declaration of function ‘SSL_CTX_new’
flashsupport.c:278: warning: implicit declaration of function ‘TLSv1_client_method’
flashsupport.c:280: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:280: warning: implicit declaration of function ‘SSL_new’
flashsupport.c:280: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:282: warning: implicit declaration of function ‘SSL_set_fd’
flashsupport.c:282: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:286: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:287: warning: implicit declaration of function ‘SSL_shutdown’
flashsupport.c:287: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:290: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:291: warning: implicit declaration of function ‘SSL_CTX_free’
flashsupport.c:291: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c: In function ‘FPX_SSLSocket_Destroy’:
flashsupport.c:305: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:306: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:309: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:310: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c: In function ‘FPX_SSLSocket_Connect’:
flashsupport.c:326: warning: implicit declaration of function ‘SSL_connect’
flashsupport.c:326: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c: In function ‘FPX_SSLSocket_Receive’:
flashsupport.c:338: warning: implicit declaration of function ‘SSL_read’
flashsupport.c:338: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c: In function ‘FPX_SSLSocket_Send’:
flashsupport.c:350: warning: implicit declaration of function ‘SSL_write’
flashsupport.c:350: error: ‘struct SSL_Instance’ has no member named ‘ssl’
```

after that, I type in ```
sudo cp libflashsupport.so /usr/lib

```

and get : ```
jess@jess-desktop:/tmp$ sudo cp libflashsupport.so /usr/lib
cp: cannot stat `libflashsupport.so': No such file or directory
```

any help would be appreciated..

---

### Post by robertchahine on 2008-05-29
this maybe help.

download the flashplayer from here [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

then extract the package.
then click alt+F2 and browse for the installer (it's in the folder that we extracted).

this will install the flash player with no problems (i think so ) ;)

---

