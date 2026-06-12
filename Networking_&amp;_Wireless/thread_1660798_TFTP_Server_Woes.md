---
title: "TFTP Server Woes"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by osmosys8 on 2011-01-05
Ubuntu is great. I love it, but sometimes there is something wrong with it that I just can't fix. This pains me because I would like to think that Ubuntu is something I can always fix. The reason is because life is full of so many difficult situations that don't always have an obvious solution. Should I look for a new job? Is she into me? Should I lift weights tonight or would that lead to over training? If John Lennon hadn't been shot would the Beattles have gotten back together?
 
**Here's the pain:**
 
I've got a 2620xm (you know those old routers nobody uses anymore?) plugged into my ubuntu laptop (Asus eeepc). There's a TFTP server running on the laptop. Both devices are plugged into each other with a cross over cable. ( I also have a patch cable I tried)
 
I couldn't copy my IOS from the 2620xm to the laptop (I get a error opening tftp://192.168.3.4/cisco-config (timed out)), so I tested the tftp on the laptop by having it connect to itself:
 
tftp 192.168.3.4
put test.txt
Transfer timed out.
 
my tftp config is:
{
protocol = udp
port = 69
socket_type = dgram
wait = yes
user = root
server = /usr/sbin/in.ftpd
server_args = -u root -c -s -r blksize /tftpboot
disable = no
flags = IPv4
}
 
my /etc/hosts.allow has:
in.tftpd : 192.168.3.3
in.tftpd : 192.168.3.4
 
I've restarted xinetd a number of times...
 
user "nobody" owns the /tftpboot directory and its been chmod 777.
user "nobody" also owns test.txt and its been chmod 777.
 
I read somewhere about tftp having some weird authentication hole:
"Note that tftp has NO built-in authentication. Therefore, in order to avoid a huge security hole, they made the hole a bit smaller by refusing to work if the data directory is writeable."
 
[[COLOR=#006699]http://ubuntuforums.org/showthread.php?t&#8230;[/COLOR]]("http://ubuntuforums.org/showthread.php?t&#8230;")
 
**I believe TFTP is listening**:
 
sudo netstat -aunp | grep ":69"
udp 0 0 0.0.0.0:69 0.0.0.0:* 1040/xinetd
 
 
**I also turned off the firewall:**
 
sudo ufw disable
 
And nothing!
 
 
Maybe the Beattles wouldn't have gotten back together :confused:

---

