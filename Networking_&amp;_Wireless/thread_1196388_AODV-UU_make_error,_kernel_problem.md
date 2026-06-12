---
title: "AODV-UU make error, kernel problem"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by renaldy on 2009-06-24
hello guys i need help in this, im having problem in compiling AODV-UU (version 0.9.5)
 
below is the code i got when issue the "make" command
 
 
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o main.o main.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o list.o list.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o debug.o debug.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o timer_queue.o timer_queue.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_socket.o aodv_socket.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_hello.o aodv_hello.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_neighbor.o aodv_neighbor.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_timeout.o aodv_timeout.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o routing_table.o routing_table.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o seek_list.o seek_list.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_rreq.o aodv_rreq.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_rrep.o aodv_rrep.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o aodv_rerr.o aodv_rerr.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o nl.o nl.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -c -o locality.o locality.c
gcc -Wall -O3 -g -DDEBUG -DCONFIG_GATEWAY  -DDEBUG -o aodvd main.o list.o debug.o timer_queue.o aodv_socket.o aodv_hello.o aodv_neighbor.o aodv_timeout.o routing_table.o seek_list.o aodv_rreq.o aodv_rrep.o aodv_rerr.o nl.o locality.o 
make -C /home/meshtb06/Desktop/aodv-uu-0.9.5/lnx KERNEL_DIR=/lib/modules/2.6.24-24-generic/build KCC=gcc XDEFS=-DDEBUG
make[1]: Entering directory `/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx'
make -C /lib/modules/2.6.24-24-generic/build SUBDIRS=/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  CC [M]  /home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.o
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c: In function &#8216;kaodv_hook&#8217;:
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c:273: warning: passing argument 1 of &#8216;ip_route_me_harder&#8217; from incompatible pointer type
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c: At top level:
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c:321: warning: initialization from incompatible pointer type
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c:330: warning: initialization from incompatible pointer type
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c:339: warning: initialization from incompatible pointer type
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c: In function &#8216;kaodv_init&#8217;:
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c:391: warning: passing argument 1 of &#8216;dev_get_by_name&#8217; from incompatible pointer type
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c:391: error: too few arguments to function &#8216;dev_get_by_name&#8217;
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c:402: error: implicit declaration of function &#8216;proc_net_create&#8217;
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c: In function &#8216;kaodv_exit&#8217;:
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c:432: warning: passing argument 1 of &#8216;proc_net_remove&#8217; from incompatible pointer type
/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.c:432: error: too few arguments to function &#8216;proc_net_remove&#8217;
make[3]: *** [/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx/kaodv-mod.o] Error 1
make[2]: *** [_module_/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make[1]: *** [kaodv.ko] Error 2
make[1]: Leaving directory `/home/meshtb06/Desktop/aodv-uu-0.9.5/lnx'
make: *** [kaodv] Error 2

 
side info im currently using ubuntu 8.04 and kernel version is 2.6.24-24-generic, thanks a lot in advance!

---

### Post by MaindotC on 2009-06-24
Difficult to tell w/o going through the source and readme file and checking dependencies.  They have a .deb repo - why don't you just add that and install the package that way?

---

### Post by renaldy on 2009-06-24
> **strAlan said:**
> Difficult to tell w/o going through the source and readme file and checking dependencies. They have a .deb repo - why don't you just add that and install the package that way?
 
erm sorry im very new to this i dont know what u mean, would you mind explaining to me? sorry mate

---

### Post by MaindotC on 2009-06-24
There are [directions](http://debian.azertyfab.net/HOWTO.txt) on their site for adding a [repository](http://en.wikipedia.org/wiki/Software_repository).  Add the repository and follow the instructions for installing the package from their repository.  Let us know if you have difficulty understanding and specify EXACTLY what you do not understand.

---

### Post by renaldy on 2009-06-25
> **strAlan said:**
> There are [directions]("http://debian.azertyfab.net/HOWTO.txt") on their site for adding a [repository]("http://en.wikipedia.org/wiki/Software_repository"). Add the repository and follow the instructions for installing the package from their repository. Let us know if you have difficulty understanding and specify EXACTLY what you do not understand.
 
i did add the lines into /etc/apt/sources.list : 

   ---> deb [http://debian.azertyfab.net](http://debian.azertyfab.net) etch main contrib non-free
   ---> deb-src [http://debian.azertyfab.net](http://debian.azertyfab.net) etch main contrib non-free

and do a update, however i am still unable to find aodvd-uu and aodv-uu-source when attempt to download from the repository, what am i missing? its written in other language i cant really understand the language,lol

---

### Post by MaindotC on 2009-06-25
C'mon bro - start thinking of what tools you have available: [http://is.gd/1d8tU](http://is.gd/1d8tU)

---

### Post by renaldy on 2009-06-25
> **strAlan said:**
> C'mon bro - start thinking of what tools you have available: [http://is.gd/1d8tU](http://is.gd/1d8tU)
 
 
ohh,ok, that should settle the problem, i will try it with my company's laptop tomorrow, thx a lot

---

### Post by Rashini on 2012-02-27
These days I am doing wasn related subjects in my university(UCSC). I also faced your problem and 
when try to solve it I saw this forum. Then doing some change I got the right answer and I though it is very help for future followers if mentioned it here.

There is a problem of installing aodv in ubuntu old version as well as latest versions.  But it is clearly running on the ubuntu 10.04. I couldn't find any reasons for that.But I could able to do my works by changing the ubuntu installation to 10.04.

---

### Post by guri033 on 2013-04-18
hey can anybody give me the source code for AODV protocol in NS2??

---

### Post by wildmanne39 on 2013-04-18
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

