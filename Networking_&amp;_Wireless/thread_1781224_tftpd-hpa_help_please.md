---
title: "tftpd-hpa help please"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by BignBald on 2011-06-13
I'm having problems getting tftp server up and running. I did have it working for a while but it stopped after a reboot, now I can't get it to serve at all!

I've installed (and removed and installed again!) tftpd-hpa ([FONT="Courier New"]sudo apt-get install tftp-hpa tftpd-hpa[/FONT])

My /etc/default/tftpd-hpa file contains:
[FONT="Courier New"]# /etc/default/tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure"[/FONT]

File /etc/services has a line
[FONT="Courier New"]tftp		69/udp
[/FONT]

File /etc/xinit.d/tftp contains
[FONT="Courier New"]service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = /var/lib/tftpboot
disable         = no
}[/FONT]


Other files are as per install.


When I do a [FONT="Courier New"]netstat -a [/FONT]there seem to be two instances of tftp, don't know if it's significant:
[FONT="Courier New"]netstat -a | grep tftp
udp        0      0 *:tftp                  *:*                                
udp        0      0 *:tftp                  *:*                                
[/FONT]

Requests to tftp on localhost (and over the network) fail with timeout:
[FONT="Courier New"]tftp localhost -c get testfile
Transfer timed out.[/FONT]

Please, any ideas? I'm sure it's something simple but I'm a bit of a newbie...

Cheers

---

### Post by gmargo on 2011-06-13
You should either run tftpd as a daemon, or on demand from xinit.  You are doing both.  Turn one of them off.

Here's a better netstat command to see what process(es) are trying to listen on port 69 (this is what my machine looks like when running the daemon.)
```

$ sudo netstat -tlnup | grep :69
udp        0      0 0.0.0.0:69              0.0.0.0:*                           1602/in.tftpd   

```

---

### Post by BignBald on 2011-06-14
> **gmargo said:**
> You should either run tftpd as a daemon, or on demand from xinit.  You are doing both.  Turn one of them off.

Here's a better netstat command to see what process(es) are trying to listen on port 69 (this is what my machine looks like when running the daemon.)
```

$ sudo netstat -tlnup | grep :69
udp        0      0 0.0.0.0:69              0.0.0.0:*                           1602/in.tftpd   

```

Thank you, gmargo, you nailed it.

A couple of questions, if you have time.

How is the xinet on-demand controlled? I've removed the file [FONT="Courier New"]tftp[/FONT] from [FONT="Courier New"]/etc/xinet.d/[/FONT] and also commented out the [FONT="Courier New"]RUN_DAEMON="yes"[/FONT] from the default file. Now I only have one instance of tftpd running.

What are the relative merits of running as a daemon and on demand?

Thanks again.

Cheers
John

---

### Post by amauk on 2011-06-14
Traditionally, in order for a machine to serve incoming client requests, the machine has to have all the active software servers running all the time

If you're providing a lot of services, this can take quite a lot of resources, and if the services are used infrequently this is not very efficient

So, the idea of super servers came about, where you'd only have a single super-server running. This super-server accepts all incoming requests (hence 'super'), and:
- Work out which software server should deal with the request
- Fire up the relevant server and hand it the request
- After a specified time of inactivity, kill the server

As to the pros & cons of dedicated server daemons vs. controlled via a super server, it's entirely dependant on the usage of the machine

Google around for comparisons

---

### Post by BignBald on 2011-06-17
Thanks guys for your help.

So much to learm, so little time... :)

Cheers
John

---

