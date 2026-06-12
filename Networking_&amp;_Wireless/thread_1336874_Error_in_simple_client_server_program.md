---
title: "Error in simple client server program"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by shariefbe on 2009-11-24
Hi i downloaded a simple client server program. when i try to compile that program using makefile i am getting following error. I dont know what it is. Can anyone help me

```

sharief@sharief-desktop:~/Desktop/simple program$ make
gcc -g -c echosrv.c
echosrv.c: In function &#8216;main&#8217;:
echosrv.c:47: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echosrv.c:58: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echosrv.c:66: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echosrv.c:73: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echosrv.c:84: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echosrv.c:92: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echosrv.c:100: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echosrv.c:111: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echosrv.c:119: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echosrv.c:145: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
echosrv.c:149: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echosrv.c:166: warning: passing argument 2 of &#8216;accept&#8217; from incompatible pointer type
echosrv.c:172: warning: passing argument 2 of &#8216;accept&#8217; from incompatible pointer type
echosrv.c:186: warning: passing argument 2 of &#8216;accept&#8217; from incompatible pointer type
echosrv.c: In function &#8216;RequestType&#8217;:
echosrv.c:415: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
echosrv.c: In function &#8216;BufferPortResponse&#8217;:
echosrv.c:476: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
echosrv.c:564: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
gcc -g -o echosrv echosrv.o
gcc -g -c echoclnt.c
echoclnt.c: In function &#8216;main&#8217;:
echoclnt.c:34: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:41: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:48: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:55: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:62: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:73: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:80: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:91: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:98: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c: In function &#8216;SetServerOptions&#8217;:
echoclnt.c:133: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:143: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:148: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
echoclnt.c:153: warning: passing argument 2 of &#8216;connect&#8217; from incompatible pointer type
echoclnt.c:155: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:159: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
echoclnt.c:161: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
echoclnt.c:164: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:170: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:181: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:187: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:198: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:204: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:215: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:221: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c: In function &#8216;TalkToUDPServer&#8217;:
echoclnt.c:247: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:257: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:262: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
echoclnt.c:266: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
echoclnt.c:278: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:283: error: too many arguments to function &#8216;recv&#8217;
echoclnt.c:286: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c: In function &#8216;TalkToTCPServer&#8217;:
echoclnt.c:327: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:337: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:342: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
echoclnt.c:347: warning: passing argument 2 of &#8216;connect&#8217; from incompatible pointer type
echoclnt.c:349: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:353: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
echoclnt.c:363: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
echoclnt.c:370: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make: *** [echoclnt.o] Error 1
sharief@sharief-desktop:~/Desktop/simple program$ 

```
Please help me

---

