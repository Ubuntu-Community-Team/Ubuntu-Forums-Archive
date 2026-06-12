---
title: "LIRC and mythtv mystery  when adding new button"
date: 2011-09-18
forum: Mythbuntu
---

### Post by mrlitsta on 2011-09-18
I've got a little predicament here that I was hoping someone here could help me solve.  I've got a working mythbuntu setup with LIRC 0.8.7-pre on Ubuntu 10.10 and mythtv 0.24.1 (from the mythbuntu repos).

LIRC is working just fine with my remote (ati_remote_wonder_rf), but when I tried to add another key on my remote to pull up the mythtv program guide, I discovered that absolutely no change I made to ~/.mythtv/lircrc or ~/.lircrc/mythtv seemed to make any difference to LIRC at all, including moving ~/.lircrc and the ~/.lirc/ directory entirely.

In fact, when I did move the ~/.lirc/ directory and ~/.lircrc file and restared LIRC, mythtv and LIRC behaved normally.  I have no idea where LIRC is picking up the configuration mapping between my remote and mythtv, but it's driving me nuts.  Does anyone know how this is happening?

The button I am trying to map shows up in irw, and remapping an existing button doesn't take any effect, either. 

Supposedly running lirc with these arguments will tell me which configuration files lirc is loading:
sudo /usr/sbin/lircd  --logfile=~/lircd.log -D7 -n --output=/var/run/lirc/lircd --driver=atilibusb
but that gives me:
/usr/sbin/lircd: unrecognized option '--logfile=~/lircd.log'
Usage: lircd [options] [config-file]

Is the manpage wrong!?
       "-L --logfile=file
              daemon log file"

Lirc runs as root when I start it using /etc/init.d/lirc, but there is no ~/.lirc directory in /root/

Any ideas?  I have no idea where LIRC is getting its mythtv mappings from.

---

### Post by mrlitsta on 2012-04-12
Well,  After getting no answer and being busy, I'm back again.  I discovered tonight that there was some sort of incestuous interplay between mythtv, lirc, and irexec (so my wife can restart myth if/when the frontend crashes).  It turns out if I make config file changes and the **restart X**, I **finally ** get my changes to stick.  So far so good.  Although it makes no sense that no amount of LIRC restarts got it to see my changes.

But I'm no closer to my goal:
Mythtv is halfway decent at recording, LIRC remote working
Boxee is really good for other media but unusable till remote works

To make sure LIRC can talk to other applications, I tried to get VLC controls working, ironically, despite mythbuntu generating a vlc LIRC file, no one tells you to start vlc with the "--control lirc" flag.  It worked after that.

When I start Boxee or XBMC, I get this helpful message in syslog:
Apr 11 23:48:37 antec lircd-0.8.7-pre3[23405]: accepted new client on /var/run/lirc/lircd
Apr 11 23:48:54 antec lircd-0.8.7-pre3[23405]: removed client

I mash remote buttons for a while, do some Googling, and give up.

Can **anyone** explain why/how the old lircrc format and the new lircmap.xml format play with each other?  Or how applications can magically connect to LIRC but not send anything?

Bizarre outstanding issues:
lirc 0.8.3 **insists** that it doesn't understand --logfile!?  What?
vlc LIRC controls also control mythtv simultaneously.  Not ideal.

---

