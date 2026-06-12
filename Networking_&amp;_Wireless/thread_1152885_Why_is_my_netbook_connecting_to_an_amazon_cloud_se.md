---
title: "Why is my netbook connecting to an amazon cloud server?"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by slackthumbz on 2009-05-08
I just noticed that my netbook has a whole load of outgoing connections to ecs.amazonaws.co.uk... why? I'm only running thunderbird and screen with a couple of SSH sessions. I don't recall ever being asked if I wanted anything to do with amazons cloud. As far as I can tell from running a few checks with lsof and ps it's something to do with gvfs. What the hell is going on? How can I disable it?

Thanks in advance,
Slackthumbz

---

### Post by kerry_s on 2009-05-08
firefox/thunderbird plugins, the website stuff, update manager?

---

### Post by slackthumbz on 2009-05-08
As far as I'm aware none of those services require amazons cloud. I just kill -9'd all gvfs processes to stop it and I can see in conky that those connections have stopped. Specifically it was gvfsd-http that was doing it. I have update manager configured to use a local UK mirror, I didn't have firefox open and I don't have any extra plugins installed for thunderbird.

I was in the process of copying some sensitive data from my VPS to my laptop via sftp (using nautilus, but this shouldn't have anything to do with gvfsd-http as gvfsd-sftp was also running).

I find this disturbing, I don't like the idea of my machine connecting to systems that I neither know nor trust.

---

### Post by obreiro on 2009-05-08
you must to supply more information about youur supossed issue.
do a "[FONT="Courier New"]netstat -putall[/FONT]" to see all ip connections and attached PID's and the name of the process.

Table should be as:

[FONT="Courier New"][SIZE="3"][SIZE="1"][SIZE="3"]:~$ netstat -putall
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:7634          *:*                     LISTEN      -               
tcp        0      0 *:ssh                   *:*                     LISTEN      -               
tcp        0      0 localhost:ipp           *:*                     LISTEN      -               
tcp        0      0 Computador.local:41211  a92-122-188-18.depl:www ESTABLISHED 25146/firefox   
tcp        0      0 Computador.local:51690  by2msg3020112.phx.:msnp ESTABLISHED 3921/pidgin     
tcp        0      0 Computador.local:34023  ww-in-f113.google.c:www ESTABLISHED 25146/firefox   
tcp        0      0 Computador.local:37809  a92-122-188-56.depl:www ESTABLISHED 25146/firefox   
tcp        0      0 localhost:7634          localhost:58482         TIME_WAIT   -               
tcp        0      0 Computador.local:53698  64.4.9.254:www          ESTABLISHED 3921/pidgin     
tcp        0      0 Computador.local:36349  mg-in-f125.:xmpp-client ESTABLISHED 3921/pidgin     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      -               
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      -               
udp        0      0 *:37156                 *:*                                 -               
udp        0      0 *:bootpc                *:*                                 -               
udp        0      0 *:mdns                  *:*                                 -               
paulo@Computador:~$ [/SIZE][/SIZE][/SIZE][/FONT]

---

### Post by slackthumbz on 2009-05-15
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:9091                  *:*                     LISTEN      -               
tcp        0      0 localhost:10022         *:*                     LISTEN      20606/ssh       
tcp        0      0 localhost:10023         *:*                     LISTEN      20606/ssh       
tcp        0      0 localhost:10025         *:*                     LISTEN      20606/ssh       
tcp        0      0 localhost:10389         *:*                     LISTEN      20606/ssh       
tcp        0      0 *:51413                 *:*                     LISTEN      -               
tcp        0      0 localhost:3128          *:*                     LISTEN      20606/ssh       
tcp        0      0 guest096.wtgc.org:46544 holmes.freenode.ne:ircd ESTABLISHED 3780/irssi      
tcp        0      0 guest096.wtgc.org:60242 ecs.amazonaws.co.uk:www ESTABLISHED 2119/gvfsd-http 
tcp        1      0 guest096.wtgc.org:41568 ecs.amazonaws.co.uk:www CLOSE_WAIT  2119/gvfsd-http 
tcp        0      0 guest096.wtgc.org:34566 ssh.sanger.ac.uk:ssh    ESTABLISHED 20606/ssh       
tcp        1      0 guest096.wtgc.org:50687 199.93.57.125:www       CLOSE_WAIT  2119/gvfsd-http 
tcp        1      0 guest096.wtgc.org:44546 199.93.57.125:www       CLOSE_WAIT  2119/gvfsd-http 
tcp        1      0 guest096.wtgc.org:35849 s146633511.websiteh:www CLOSE_WAIT  2119/gvfsd-http 
tcp        0      0 guest096.wtgc.org:60241 ecs.amazonaws.co.uk:www ESTABLISHED 2119/gvfsd-http 
tcp        0      0 guest096.wtgc.org:60240 ecs.amazonaws.co.uk:www ESTABLISHED 2119/gvfsd-http 
tcp6       0      0 localhost:10022         [::]:*                  LISTEN      20606/ssh       
tcp6       0      0 localhost:10023         [::]:*                  LISTEN      20606/ssh       
tcp6       0      0 localhost:10025         [::]:*                  LISTEN      20606/ssh       
tcp6       0      0 localhost:10389         [::]:*                  LISTEN      20606/ssh       
tcp6       0      0 [::]:51413              [::]:*                  LISTEN      -               
tcp6       0      0 localhost:3128          [::]:*                  LISTEN      20606/ssh       
udp        0      0 *:46742                 *:*                                 -               
udp        0      0 *:bootpc                *:*                                 -               
udp        0      0 *:mdns                  *:*                                 -

---

### Post by krnlg on 2009-06-29
Do you use Rhythmbox at all?

There is a bug in gvfsd-http that causes it to leave old connections in CLOSE_WAIT instead of properly terminating. If you use Rhythmbox, it makes connections to amazon servers (I'm guessing for album art etc.). The connections it makes are through gvfsd-http and will remain in CLOSE_WAIT for ever, until either too many connections build up or the daemon is terminated.

So because of this bug, if its gvfs thats made the connections, they might have been initiated quite a while ago, especially if you don't log out very often.

---

