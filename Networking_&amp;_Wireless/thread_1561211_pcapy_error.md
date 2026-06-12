---
title: "pcapy error"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by quis00 on 2010-08-25
Sup,
  So I've been triying to install the python module pcapy since about 6 this evening getting nowhere and keep side tracking to other subjects so last resort is post on forums.

I am running ubuntu 9.10 and have libpcap-1.1.1 installed but pcapy-0.10.5 will not import
the error i receive is
import error:libpcap.so.1: cannot open shared object file: No such file or directory
upon trying to import pcapy

I am a Net sec. majaor with an assoc. degree and been studyin python for under a year and am trying to do some work with the impacket module. Before deciding to post this I already looked up some info already hear and there was one similar post regarding a cbm installation error ( I think) and the solution was to symbolicly link it to another shared object , I tried that (in fact i linked every version of libpcap.so in every different variation I could think of just for kicks:p) My last thought was to see where exactly pcapy is looking for libpcap.so.1 but the pcapy module is no where to be found only the pcapy.so appears and also I can't use the locate cmd to find pcapy (wtf is going on) 

With this issue I am officialy humble if there is anyone out there that can point me in the right place. Tomorrow morning I plan on researching some more into shared objects and the compilation process through uninstalling and logging a new install and seeing what I can find as that is the last thing I can think of on my own....Cant wait:rolleyes:

---

### Post by quis00 on 2010-08-25
I forgot to mention since I am new to the ubuntu version of linux is there suppose to be 2 seperate paths of the python folder eg.. /usr/local/lib/pythonx.x and /usr/lib/pythonx.x

---

