---
title: "scp problem"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by bigvanilla2 on 2010-10-20
Sitting here and trying to scp to work.
 
Am using Ubuntu 9 (10.4) and 10 (10.10).
All computers are on the same network (local).
 
Have now tried different variations, only two virtual partitions in VMware where one party tone install OpenSSH and verified that it works and has started.
Connects the client to the SSH server without any problems.
 
What is the problem is that every time I should copy to or from the client (using scp) after I started running SSH, I get error message Connection Refuse. Tested to run with the-v flag and get no more info than just Connection Refuse, everything else looks good.
 
Have tried sftp and it went very well. (Both ways)
 
Installed WinSCP on my Windows partition 7 which both virutalbox and vmware is installed on. It was good to connect to a virtual linux ssh server, and to transfer files in both directions in the graphical interface.
But WinSCP is also a terminal window as I tried, but then I get permission denied. (Both ways)
 
Tests asedan to install virtual box and run only between it and a vmware linux. Same error here.
 
So I thought about it maybe had something with the virtual machines to do.
 
I have an old computer that I installed the new ubuntu (10.4) and install the OpenSSH server on it. On my windows machine, I dual boot, so I chose ubuntu (10:10) at startup.
And now tested between two non-virtual linux installations.
 
But with the same error. Can not understand what's wrong?
 
I also checked to klieneten sits and listens on port 22, and it was ok.
 
As a last resort, so I started a virtual linux ssh server and linked it up against a non-virtual ssh server. So both computers now have the ssh server running.
And now everything works perfectly to transfer files both ways.
 
 
Have surftat long to find a solution, but it goes bad. And now hope for your help.
 
What can be wrong and what should I do?
 
 
I'm not completely new to Linux, installing and running a bit sooner (most redhat, open suse and gentoo) but not so advanced. Ubuntu, I have only tried the last two months. Has also worked with Sun Solaris in my previous career.
 
 
[COLOR=#000]/ / Patrik[/COLOR]

---

### Post by marc.verwerft on 2010-10-20
Look in /etc/ssh/sshd_config to see where the server logs error messages. Probably it is in /var/log/syslog. If necessary set loglevel in the config file to 'info' like this:

# Logging
#SyslogFacility AUTH
SyslogFacility AUTHPRIV
LogLevel INFO

Maybe you see a hint at what's wrong there.

Regards,

Marc

---

### Post by bigvanilla2 on 2010-10-20
Thanks mark for your help.
 
I find the solution. I did the mistake that I did run the scp command in the same terminal windows I used to login to the SSH server.(also some syntax error in my scp code)
 
It do function now when I run scp from a new terminal window.
 
// Patrik

---

