---
title: "Mythbuntu 10.10 LIRC not working on boot but works after restarting LIRC"
date: 2011-04-27
forum: Mythbuntu
---

### Post by acrowe on 2011-04-27
Hi All,
 
Running Mythbuntu 10.10 with LIRC configured using the Linux Input Layer and the remote on a Winfast DTV2000DS. (/dev/input/event4)
 
The remote works and has been configured however I have the following issue:
 
When the PC boots (and goes straight into MythTV) the remote does not work. To get the remote to work I have to:
 
1) Exit MythTV
2) Restart LIRC (sudo /etc/ionit.d/lirc restart)
3) Restart MythTV
 
After doing this the remote works well.
 
If I do a cold boot, exit MythTV and run 'irw' the remote codes work fine.
If I then re-enter MythTV it still doesn't work. If I restart LIRC BEFORE re-entering MythTV then it works.
 
Upon boot the /var/log/syslog entries have:
 
Apr 27 17:50:40 myth1 lircd-0.8.7-pre3[1035]: lircd(devinput) ready, using /var/run/lirc/lircd
Apr 27 17:50:40 myth1 inputlircd: Started
 
My mythwelcome log has:
 
2011-04-27 17:50:50.679 LIRC: Successfully initialized '/dev/lircd' using '/home/crowe/.mythtv/lircrc' config

After restarting LIRC I get the following additional entries in syslog:
 
Apr 27 18:00:58 myth1 lircd-0.8.7-pre3[1035]: caught signal
Apr 27 18:00:58 myth1 lircd-0.8.7-pre3[2430]: lircd(devinput) ready, using /var/run/lirc/lircd

and the following entries in the mythwelcome log:
 
2011-04-27 18:04:20.575 LIRC: Successfully initialized '/dev/lircd' using '/home/crowe/.mythtv/lircrc' config
 
Can't see any entries relevant in the logs for mythfrontend or mythbackend 
All of this looks quite normal - can anyone shed any possible light on thir or anywhere else I should be looking to troubleshoot this issue?
 
Cheers

---

### Post by phroman on 2011-04-27
Hi, the Winfast is your capture card correct?  What kind of remote control are you using?

---

### Post by acrowe on 2011-04-27
Hi,
 
Using the remote control that comes with the WinFAST cards.
I know the remote works and LIRC works because after a restart of the LIRC service after a boot it works perfectly. I'm just trying to work out what happens upon booting that is causing it not to work.

---

### Post by acrowe on 2011-04-27
I was thinking restarting LIRC seems to work so I could try restarting LIRC before MythTV loads
 
It appears you can modify /usr/bin/mythfrontend to add additional commands before loading the front end (I have added a sleep command in here to delay the startup)
 
I was going to try and add a lirc restart command here to restart LIRC before the mythfrontend loads however normally you have to be sudo to restart the LIRC service (/etc/init.d/lirc restart)
 
I tried adding /etc/init.d/lirc to the sudoers file to allow my user account to restart LIRC but satill get errors.
 
visudo has: (crowe is the standard account that is auto-logged in with)
%crowe ALL = NOPASSWD: /etc/init.d/lirc, /dev/lircd, /var/run/lirc/lircd.pid
 
When starting LIRC under the crowe account I still get:
[EMAIL="crowe@myth1:/$"]crowe@myth1:/$[/EMAIL] /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [fail]
rm: cannot remove `/dev/lircd': Permission denied
 * Loading LIRC modules                                                  [ OK ]
 * Starting remote control daemon(s) : LIRC                                     lircd: can't open or create /var/run/lirc/lircd.pid
lircd: Permission denied
                                                                         [fail]

any assistance on how I can fix this? (Thinking maybe folder permissions?)

---

### Post by klc5555 on 2011-04-28
The way I handle a similar issue on two Slackware boxes where lirc has to be killed and restarted immediately before mythbackend starts, is to have a small script that looks something like the following:

killall lircd
sleep 3
/usr/bin/lircd
sleep 3
exit

I make the script executable, put it under  /etc/rc.d (which Slack uses instead of /etc/init.d) as "rc.killlirc" and then symlink it at each runlevel where the mythbackend startup is symlinked, but to run immediately before the backend startup. 

So that in the runlevel if there is something like @S72mythbackend, which symlinks to an rc.mythbackend, the above script is symlinked as  @S71killlirc to run immediately before the backend starts.  

Something similar to this could be composed for use on Ubuntu as readily as on Slack. Startup scripts run as root; there's no "sudo" to worry about.

You can't use rc.local for something like this because it appears that the backend starts before rc.local executes.

---

