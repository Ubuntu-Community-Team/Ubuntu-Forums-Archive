---
title: "how to install TOSSIM simulator"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by ribidi on 2012-02-26
Hi,
im a bigenner on Ubuntu 10.04 Lucid and i got a lot of problems when installing TOSSIM simulator. the links i fallowed are here :
[http://www.developerstation.org/2010/09/installing-tinyos-on-ubuntu-104.html]("http://www.developerstation.org/2010/09/installing-tinyos-on-ubuntu-104.html") 
and
[http://pjpramod.blogspot.com/2009/01/installing-tinyos-2x-in-ubuntu-intrepid.html]("http://pjpramod.blogspot.com/2009/01/installing-tinyos-2x-in-ubuntu-intrepid.html")

:confused::confused:

when i tape on the shell's prompt : make micaz sim 


mkdir -p simbuild/micaz
make: python2.5-config : commande introuvable
make: python2.5-config : commande introuvable
make: python2.5-config : commande introuvable
  placing object files in simbuild/micaz
  writing XML schema to app.xml
  compiling BlinkAppC to object file sim.o
ncc -c -shared -fPIC -o simbuild/micaz/sim.o -g -O0 -tossim -fnesc-nido-tosnodes=1000 -fnesc-simulate -fnesc-nido-motenumber=sim_node\(\) -fnesc-gcc=gcc -Wall -Wshadow -Wnesc-all -target=micaz -fnesc-cfile=simbuild/micaz/app.c -board=micasb -DDEFINED_TOS_AM_GROUP=0x22 --param max-inline-insns-single=100000 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"hamza\" -DIDENT_HOSTNAME=\"hamza-laptop\" -DIDENT_USERHASH=0xd7162298L -DIDENT_TIMESTAMP=0x4f4a1352L -DIDENT_UIDHASH=0xe49b00fdL -Wno-nesc-data-race BlinkAppC.nc   -fnesc-dump=components -fnesc-dump=variables -fnesc-dump=constants -fnesc-dump=typedefs -fnesc-dump=interfacedefs -fnesc-dump=tags -fnesc-dumpfile=app.xml
  compiling Python support and C libraries into pytossim.o, tossim.o, and c-support.o
g++ -c  -shared -fPIC -o simbuild/micaz/pytossim.o -g -O0 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"hamza\" -DIDENT_HOSTNAME=\"hamza-laptop\" -DIDENT_USERHASH=0xd7162298L -DIDENT_TIMESTAMP=0x4f4a1352L -DIDENT_UIDHASH=0xe49b00fdL /opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx -I/include/python2.5 -I/opt/tinyos-2.1.1/tos/lib/tossim -DHAVE_CONFIG_H 
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:139:20: error: Python.h: Aucun fichier ou dossier de ce type
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:2501:4: error: #error "This python version requires swig to be run with the '-classic' option"
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:744: error: expected initializer before ‘*’ token
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:799: error: expected initializer before ‘*’ token
/opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:820: error: expected initializer before ‘*’ token
In file included from /usr/include/c++/4.4/stdexcept:38,
                 from /opt/tinyos-2.1.1/tos/lib/tossim/tossim_wrap.cxx:2520:
/usr/include/c++/4.4/exception:35: error: expected declaration before end of line
make: *** [sim-exe] Erreur 1
:confused::confused::confused:
please some help and thank you.
i'm sorry for my bad english

---

### Post by ribidi on 2012-02-27
:(:(:(:(:(:(:(:

---

