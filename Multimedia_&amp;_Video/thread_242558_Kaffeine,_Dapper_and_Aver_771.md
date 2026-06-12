---
title: "Kaffeine, Dapper and Aver 771"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by master_b on 2006-08-23
Hi all,

Dapper finds my Dvico Fusion HDTV DVB-T card fine. Kaffeine grabs channels ( Sydney Australia) and just works,

One of my other PCs has an Avermedia 771 DVB-T card and kaffeine under Dapper fails to see it.

Other Distros, Debian based or otherwise ( ie MythDora) see it fine.

Question - does Dapper include support for this card in its kernel or not?3

I have enabled DVB in Kaffeine and corrected the Broadcast IP for my LAN.

I want to get it working under Kubuntu Dapper so that I have the same distro on all of my PCs.

Thanks for any info/advice

Bill

---

### Post by master_b on 2006-08-24
Anybody?

Surely somebody has an Avermedia 771 dvb-t card?

bill

---

### Post by darklord on 2006-08-27
hi

I have an avermedia 771 and i posted the following solution.

please look at the bottom of the following link:-

[http://www.pvrweb.com/bbs/index.php?showtopic=5052](http://www.pvrweb.com/bbs/index.php?showtopic=5052)

in brief:-
just add the following modules to the file /etc/modules
dvb-bt8xx
mt352

then either
sudo modprobe dvb-bt8xx
sudo modprobe mt352

or reboot

and use kaffeine to tune the card, it will download the necessary data for you. (you may need a codec to view the stream tho).

ps: if anyone knows how to get a trust 320 spacecam working under LTS please drop me a mail. 

I think im stuck on creating a node to the cammera and not the tv card

---

### Post by master_b on 2006-08-28
Thanks DarkLord.

Shame that the tvcard setup script from Kanotix is not included in Ubuntu.
Makes it so easy.

Maybe something similar could be added to EasyUbuntu or Automatix

Bill

---

### Post by datdat on 2007-01-07
Any successfully got avermedia 771 to work under Edgy ? 
I'm having problem that it can't detect the tuner.

---

