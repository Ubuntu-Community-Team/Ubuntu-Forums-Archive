---
title: "407 Proxy Authentication Required"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by oguzy on 2008-12-24
In a ISA server network, i am able to use Internet after i set the network proxy and the required username and password. The username is set as domain\username. So when i set the proxy setting from Network Proxy at Hardy i am able to use Firefox to surf. 

When i made the same settings for the Synaptic it gave me the below error message:
407 Proxy Authentication Required ( The ISA Server requires
authorization to fulfill the request. Access to the Web Proxy filter
is denied.  )

Do i need to install ntlmaps or is there any other solution to make apt work?

---

### Post by dagamant on 2009-01-14
> **oguzy said:**
> In a ISA server network, i am able to use Internet after i set the network proxy and the required username and password. The username is set as domain\username. So when i set the proxy setting from Network Proxy at Hardy i am able to use Firefox to surf. 

When i made the same settings for the Synaptic it gave me the below error message:
407 Proxy Authentication Required ( The ISA Server requires
authorization to fulfill the request. Access to the Web Proxy filter
is denied.  )

Do i need to install ntlmaps or is there any other solution to make apt work?

[http://cntlm.wiki.sourceforge.net/](http://cntlm.wiki.sourceforge.net/) works nicely, i recently configured it on a open suse system and it works great. you have to manually edit /etc/cntlm.conf to match your proxy server info. here is the default conf:
###start cntlm.conf
#
# Cntlm Authentication Proxy Configuration
#
# NOTE: all values are parsed literally, do NOT escape spaces,
# do not quote. Use 0600 perms if you use plaintext password.
#


Username	<your username>
Domain		<yourdomain.com>
#Password	<your password>		# Use hashes instead (-H)
#Workstation	netbios_hostname	# Should be auto-guessed

Proxy		10.217.112.42:8080

#
# This is the port number where Cntlm will listen
#
Listen		3128

#
# Use -M first to detect the best NTLM settings for your proxy.
# Default is to use the only secure hash, NTLMv2, but it is not
# as available as the older stuff.
#
# This example is the most universal setup known to man, but it
# uses the weakest hash ever. I won't have it's usage on my
# conscience. :) Really, try -M first.
#
Auth		LM
#Flags		0x06820000

#
# Enable to allow access from other computers
#
#Gateway	yes

#
# Useful in Gateway mode to allow/restrict certain IPs
#
#Allow		127.0.0.1
#Deny		0/0

#
# GFI WebMonitor-handling plugin parameters, disabled by default
#
#ISAScannerSize	1024
#ISAScannerAgent	Wget/
#ISAScannerAgent	APT-HTTP/
#ISAScannerAgent	Yum/

#
# Headers which should be replaced if present in the request
#
#Header		User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows 98)

#
# Tunnels mapping local port to a machine behind the proxy
# 
#Tunnel		1122:awk.cz:443
##end cntlm.conf


the only things i changed were:

Username	<your username>
Domain		<yourdomain.com>
Password	<your password>		# Use hashes instead (-H)

Proxy		10.217.112.42:8080

Listen		3128

once this is set you can point your proxy to localhost:3128 and it should work.

---

### Post by oguzy on 2009-01-15
I tried ntlmaps and is working quite fine. I am able to use apt from terminal and also via package manager. Seems fat also. Thanx for your alternative solution.

---

