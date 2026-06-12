---
title: "wirless network not connecting in ubuntu ,whereas in windows 7 its works fine"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by stinghawk on 2012-08-26
hi guys i am new to ubuntu and linux . i installed ubuntu long time back with help of my friend . its maverick 10.10 version

ubuntu was installed via windows

my wireless modem is not connecting with ubuntu ?

its asking for wap or wap2 password encryption ?

i asked the customer care of isp and they told me to type the bsk key hexcode written on modem to enter .

i entered the key but it its still not working .:confused: i changed its password (connecting the modem via lan) . and typing the new password i can log on to internet in windows 7 but still not in ubuntu:confused:

when i have asked the isp they said tat i should configure ubuntu to link dynamically (i honestly dont know what they are talking)

i honestly dont know whether my connection is static or dynamic :frown:

i tried to search in net and came up with a video to make connection dynamic 

i had to install dhcp3-server

but when i typed sudo apt-get install dhcp3-server i am getting errors


 root@sree-Satellite-L650:/etc# sudo apt-get install dhcp3-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dhcp3-client dhcp3-common
Suggested packages:
  resolvconf dhcp3-server-ldap
The following NEW packages will be installed:
  dhcp3-server
The following packages will be upgraded:
  dhcp3-client dhcp3-common
2 upgraded, 1 newly installed, 0 to remove and 349 not upgraded.
Need to get 1,007kB of archives.
After this operation, 930kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  dhcp3-client dhcp3-common dhcp3-server
Install these packages without verification [y/N]? y
](*,)Err [http://ubuntu.pesat.net.id/archive/](http://ubuntu.pesat.net.id/archive/) maverick-security/main dhcp3-client amd64 3.1.3-2ubuntu6.2
  Something wicked happened resolving 'ubuntu.pesat.net.id:http' (-5 - No address associated with hostname)
Err [http://ubuntu.pesat.net.id/archive/](http://ubuntu.pesat.net.id/archive/) maverick-security/main dhcp3-common amd64 3.1.3-2ubuntu6.2
  Something wicked happened resolving 'ubuntu.pesat.net.id:http' (-5 - No address associated with hostname)
Err [http://ubuntu.pesat.net.id/archive/](http://ubuntu.pesat.net.id/archive/) maverick-security/main dhcp3-server amd64 3.1.3-2ubuntu6.2
  Something wicked happened resolving 'ubuntu.pesat.net.id:http' (-5 - No address associated with hostname)
Failed to fetch [http://ubuntu.pesat.net.id/archive/pool/main/d/dhcp3/dhcp3-client_3.1.3-2ubuntu6.2_amd64.deb](http://ubuntu.pesat.net.id/archive/pool/main/d/dhcp3/dhcp3-client_3.1.3-2ubuntu6.2_amd64.deb)  Something wicked happened resolving 'ubuntu.pesat.net.id:http' (-5 - No address associated with hostname)
Failed to fetch [http://ubuntu.pesat.net.id/archive/pool/main/d/dhcp3/dhcp3-common_3.1.3-2ubuntu6.2_amd64.deb](http://ubuntu.pesat.net.id/archive/pool/main/d/dhcp3/dhcp3-common_3.1.3-2ubuntu6.2_amd64.deb)  Something wicked happened resolving 'ubuntu.pesat.net.id:http' (-5 - No address associated with hostname)
Failed to fetch [http://ubuntu.pesat.net.id/archive/pool/main/d/dhcp3/dhcp3-server_3.1.3-2ubuntu6.2_amd64.deb](http://ubuntu.pesat.net.id/archive/pool/main/d/dhcp3/dhcp3-server_3.1.3-2ubuntu6.2_amd64.deb)  Something wicked happened resolving 'ubuntu.pesat.net.id:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@sree-Satellite-L650:/etc# cat hostname-




-------------------------------------------


my hostname


sree-Satellite-L650
root@sree-Satellite-L650:/etc# hostname -f
sree-Satellite-L650
root@sree-Satellite-L650:/etc# hostname -i
::1 127.0.1.1 117.196.141.188
root@sree-Satellite-L650:/etc# hostname -I
10.42.43.1 
root@sree-Satellite-L650:/etc# 

----------------------------------------------------


root@sree-Satellite-L650:/etc# cd /etc/network
root@sree-Satellite-L650:/etc/network# ls
if-down.d  if-post-down.d  if-pre-up.d  if-up.d  interfaces

root@sree-Satellite-L650:/etc/network# cat interfaces 
auto lo
iface lo inet loopback
root@sree-Satellite-L650:/etc/network# 

----------------------------------------------------------

etc hosts

  
root@sree-Satellite-L650:/etc# cat hosts.allow
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(and rpc.mountd(
# for further information.
#

root@sree-Satellite-L650:/etc# 
------------------------------------------------

etc deny


 root@sree-Satellite-L650:/etc# cat hosts.deny
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.
#
# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

root@sree-Satellite-L650:/etc# cat hosts.deny

----------------------------------------------------

root@sree-Satellite-L650:/etc# cat hosts
117.196.141.188   sree-Satellite-L650     # Added by NetworkManager
127.0.0.1   localhost.localdomain   localhost
::1   sree-Satellite-L650     localhost6.localdomain6 localhost6
127.0.1.1   sree-Satellite-L650

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
root@sree-Satellite-L650:/etc# 

----------------------------------------------------------------------





[FONT=&quot]No address associated with hostname  ? what is that[/FONT]


[FONT=&quot]pls help  ? this is very important to me . pls help anyone ?:cry:[/FONT]

---

