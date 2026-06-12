---
title: "Unable to ping UBUNTU dns server host name from xp client(s)"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by pangeh on 2013-05-07
Hi,

I am trying to set up a local network in an office Using an Ubuntu 12.04 server as the primary dns server in preparation for setting up a Samba pdc. I have done this before successfully on Ubuntu 10.04 but cannot get this to work. I know I am doing something stupid so any assistance to help me see what I have done wrong is greatly appreciated.

For now I was just testing this out in virtual box using an ubuntu 12.04 server with the no recomends ubuntu desktop gui installed and an xp client vm.

The problem that I am having is that I can ping the Ubuntu server fine from the XP client howver when I ping by hostname it times out. When I do nslookup from the xp machine it sees the ip address but says server is unknown. 

On the Ubuntu machine I have setup Bind9 and set the server with a static IP address in the network interfaces. Also under the /etc/networkmanager/networkmanager.conf file under the [ifupdown] section the setting is: managed = false.

I'm not worried about getting onto the internet at this stage as I just want the machines to talk locally for now. 

I'm not sure what I have done wrong but think something is either wrong or missing from my zone files. Lastly the xp client is using dhcp and the server is using a static IP address.

    [SIZE=4]_Bind DNS configuration_[/SIZE]
 

 _Named.conf.local_
 

 #Forward lookup zone - holds A records and maps host names to IP addresses
 

 zone "westar.local" IN {

    type master;

     file "/etc/bind/zones/westar.local.db";

 };

 

 

 #Reverse lookup zone - holds pointer (PTR) records

 #Maps IP addresses to host names

 

 zone "0.168.192.in-addr.arpa" IN {

     type master;

     file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";

 };

 

 _/etc/bind/zones/westar.local.db_
 

 $TTL 3D
 @ IN SOA wsrv1.westar.local. admin.westar.local. (

 2007031001;
 28800;
 3600;
 604800;
 38400
 );
 

 westar.local.    IN    NS    wsrv1.westar.local.
 wsrv1        IN    A    192.168.0.2
 

 

 _/etc/bind/zones/rev.0.168.192.in-addr.arpa_
 

 $TTL 3D
 @ IN SOA wsrv1.westar.local. admin.westar.local. (
 2007031001;
 28800;
 604800;
 604800;
 86400
 );
 

     IN    NS    wsrv1.westar.local.
 2    IN    PTR    westar.local.
 

Many thanks kindly in advance.

Regards
p

---

### Post by SeijiSensei on 2013-05-07
Is Windows configured to use your BIND server? From this observation:
> The problem that I am having is that I can ping the Ubuntu server fine from the XP client howver when I ping by hostname it times out. When I do nslookup from the xp machine it sees the ip address but says server is unknown. 
I suspect it's using a different DNS server.  In Windows, open a command prompt by running cmd.exe and type the command "ipconfig /all" to see the complete details on each network interface.

---

### Post by pangeh on 2013-05-07
Hi Seiji,

Thanks for your reply.

Under the lan settings of the XP client I set the ip address to be obtained automatically but manually set the ip address of the primary DNS server as that of the Ubuntu box (192.168.0.2). When I did Ipconfig /all on the xp xlient it shows the dns server as being the correct one - 192.168.0.2. I left the secondary server blank for now.

Not sure what is causing this - I cant see what is wrong in my zone files. Just had a thought while typing this however, will disable the firewall on the server and then try pinging the server by host name from the xp client and see what happens.

---

### Post by pangeh on 2013-05-07
Hi All,

Just a quick update - finally got this working. There was nothing wrong with the Bind setup on the Ubuntu 12.04 box server after all. When I disabled the firewall it worked fine. I just needed to enable the correct port for bind, which is from terminal: sudo ufw allow 53, in order for the connection to work.

Lol, now I have a new problem where by when adding the ap client to the domain, it asks for a username and password and upon entering the credentials gives an error saying the domain could not be contacted! Received this with the firewall disconnected so dont think a firewall issue but will enable samba ports on ufw and see what happens. smb.conf below:

   _smb.conf_
 

 [global]
 

 workgroup = westar.local
 

 security = user
 

 netbios name = wsrv1
 

 passdb backend = tdbsam
 

 wins support = yes
 

 printcap name = cups
 

 server string = %h server (Samba, Ubuntu)
 

 encrypt passwords = true
 

 

 

 add user script = /usr/sbin/useradd -m %u
 

 delete user script = /usr/sbin/userdel -r %u
 

 add group script = /usr/sbin/groupadd %g
 

 delete group script = /usr/sbin/groupdel %g
 

 add user to group script = /user/sbin/groupmod -R %u %g
 

 add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u
 

 

 

 #logon script = scripts\logon.bat
 

 logon path = \\wsrv1\westar_data_share\westar_user_profiles\%U\%a
 

 logon drive = H:
 

 logon home = \\%L\westar_data_share\westar_user_home\%u
 

 

 domain logons = yes
 

 os level = 35
 

 preferred master = yes
 

 domain master = yes
 

 local master = yes
 

 

 idmap uid = 15000-20000
 

 idmap gid = 15000 - 20000
 

 

 [home]
 

 comment = home directories
 

 path = /data/westar_user_home/%u
 

 valid users = %S
 

 read only = No
 

 browseable = No
 

 writeable = yes
 

 

 

 [netlogon]
 

 comment = Network Logon Service
 

 path = /var/lib/samba/netlogon
 

 admin users = root

 

 guest ok = No
 

 browseable = No
 

 writeable = yes
 

 

 [profiles]
 

 comment = Roaming profiles share
 

 path = /data/westar/westar_profiles/westar_user_profiles
 

 read only = No
 

 #profile acls = Yes
 

 writeable = yes
 

 

 

 [westar_data_share]
 

 comment = data share
 

 path = /data/westar
 

 guest ok = no
 

 browseable = yes
 

 create mask = 0770
 

 writeable = yes
 

 directory mask = 0770

---

### Post by pangeh on 2013-05-07
I enabled samba on the Ubuntu server firewall, from terminal:

sudo ufw allow proto udp from 192.168.1.0/24 to any port 137
sudo ufw allow proto udp from 192.168.1.0/24 to any port 138
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 139
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 445

On the XP client, I can access the shares if I go to "start" and then click on "run" and type in the server ip address e.g. \\192.168.0.2\

However, when I try to add the XP client to the domain I get a message saying that the domain cannot be found. Will try to disable the firewall on the XP client and then add to the domain. Maybe there is something I am meant to do client side, although I dont remember having to do anything on the last 2 networks I setup in Ubuntu 9.10 server and 10.04 server.

P.

---

### Post by pangeh on 2013-05-07
Disconnecting the firewall on the xp client made no difference. It still says that the domain does not exist when trying to add the computer to the domain. I can however connect to shares via IP address as well as the fqdn of the server. I can additionally ping the fqdn of the server and get the IP address returned so DNS is now working properly.

The odd thing is that when I try to add the xp xclient to the domain via "my computer - properties" and type in domain, it does pop up asking for a username and password. It is only after typing in a username and password that I get the error. The way that I am typing in the username is both alone and via server/username.

Not sure what is causing this issue. Any ideas/pointers would be greatly appreciated.

---

### Post by pangeh on 2013-05-08
Ok,

This thread is predominantly a testament to the pitfalls of oversight. After looking at everything more carefully, but by taking a step back and looking at the whole process and not just re-examining my zone files and smb.conf, account permissions etc, I managed to resolve the issues experienced and get everything working.

The initial problem with not being able to ping the Ubuntu DNS server from the xp xlient by FQDN was caused by not opening the correct port on the UFW firewall for BIND as stated earlier. The second problem of the xp client saying the domain does not exist when trying to add was caused by not setting the wins server in the XP client lan settings. (An obvious mistake - but overlooked).

So in summary, for others: When something goes wrong check all of your config files, test them with the utillities and if everything is ok take a step back and look at the overall process to identify where the issue is falling over. In this case it was an issue with name resolution which can be caused by more than incorrect zone files and samba settings as seen from these silly mistakes that I made. I guess it is always helpful to have a checklist and run through everything.

Thank you all for taking the time to look at this post and and trying to assist.

Kind regards,
P.

---

### Post by pangeh on 2013-05-08
Another stupid question - This thread is now solved but I cannot find the option to mark it as solved. Any help would be appreciated. I looked under thread tools and nothing there and tried to edit post > advanced > but no option to change prefix.

Is this because I started the thread?

cheers
P.

---

