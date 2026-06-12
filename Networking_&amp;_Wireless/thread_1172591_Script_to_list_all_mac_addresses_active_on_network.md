---
title: "Script to list all mac addresses active on network"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by lavinog on 2009-05-28
I have come across a need to keep track of MAC addresses on my lan. I couldn't find simple ways of doing this other than going to each machine and writing it down.
I made a script to gather all MAC addresses for active machines on the lan.

[php]
#!/bin/bash

# MAC Address Parser - Creates list of MAC addresses of active machines on network
# Created by Greg Lavino
# Last modified 28May09 - 16:06 CST

# Feel free to modify to suit your needs.


# Output to file (true/false)?
fileout=true

# Output filename
fileout_path='./macs'

# Number of address blocks to ping at a time (only if nmap not installed)
ipblocks=51

# make temp file
tmpfile=$(tempfile)

# get local address
ip_addr_str=$(ip route list|grep 'src')

# Get device string
self_ip_dev=$(echo $ip_addr_str|cut -d ' ' -f 3)

# Get ip address
self_ip_addr=$(echo $ip_addr_str|cut -d ' ' -f 9)

# Get self mac address
self_mac_addr=$(ifconfig ${self_ip_dev}|grep 'HWaddr'|cut -c 39-55)

testinstalled()
{
# search path enviroment for file
	IFS=':'
	for p in $PATH
	do
		[[ -f ${p}/${1} ]]&&{
			unset IFS
			return 0
		}
	done
	unset IFS
	return 1
}
pingit()
{
ping -n -c 1 -W 1 ${1}>/dev/null && echo ${1}>>${tmpfile}
}

pingall()
{
# ping all addresses in block
# (much slower than nmap)

ip_prefix=$(echo ${self_ip_addr}|cut -d '.' -f 1-3)

for i in {1..254}
do
	# Ip address to ping
	ip="${ip_prefix}.${i}"

	# ping in background
	pingit ${ip}&
	
	# Wait for all ping blocks to finish
	[[ $(( ${i}%${ipblocks} )) -eq 0 ]]&&{
	echo -n '|'
	wait
	}
done

# wait for last batch of pings
wait

# remove progress line
echo -en '\r'



}

# get online addresses and populate arp cache
if $(testinstalled nmap);then
	nmap -n -sP -oG ${tmpfile} "${self_ip_addr}/24">/dev/null
	ip_list=$(grep 'Status: Up' ${tmpfile}|cut -d ' ' -f 2)

else
# TODO: use ping loop if nmap is missing instead of exiting
	echo "You can speed up discovery by installing nmap:"
	echo "sudo apt-get install nmap"

	# Start ping loops
	pingall
	# List is sorted just in case
	ip_list=$(sort ${tmpfile})

fi


# remove output file
$fileout && [[ -f $fileout_path ]] && rm ${fileout_path}



# find mac address of online machines
for i in $ip_list
do
	if [ ${i} == ${self_ip_addr} ];then
		# Already got mac address for local machine
		mac=$self_mac_addr
	else
		# Use arp cache to get mac address
		arpstr=$(arp -n ${i}|grep ${i})
		mac=${arpstr:33:17}
	fi

	# Output table
	printf "${i}\t${mac}\n"
	$fileout && printf "${i}\t${mac}\n">>$fileout_path

done

# cleanup
rm ${tmpfile}
[/php]

by default it will create a macs file in the current folder that will look something like this:
```

a.b.c.1		00:ff:ff:ff:ff:56
a.b.c.2		00:ee:ee:ee:ee:bd
a.b.c.50	00:dd:dd:dd:dd:b3
a.b.c.112	00:cc:cc:cc:cc:da
a.b.c.115	00:bb:bb:bb:bb:75
a.b.c.122	00:aa:aa:aa:aa:1a

```

It executes quicker with nmap installed, but it is not required.

If you try it out, let me know if there are any issues.

I have a couple of uses for this:
Automatic hosts file generation so that a hosts file can be updated with names for machines using dhcp.

Intrusion detection (find computers stealing your wifi, or unauthorized computers connected to the lan)

MAC addresses are needed to send magic packets to turn on machines using wakeonlan

Asset tracking. The ability to use wakeonlan helps with this also.

---

### Post by santhony on 2010-02-06
Worked Great for me.  THANKS!!

---

### Post by uniomni on 2010-06-18
Worked great for me too. 
This scripts saves the day since my Belkin N wireless router doesn't list all DHCP hosts.

Would it be hard to also get host names too?

Thanks
Ole

---

### Post by lavinog on 2010-06-19
> **uniomni said:**
> 
Would it be hard to also get host names too?


It would depend on the way the network is configured.

This should get the hostname if avahi or bonjore is installed:
```

avahi-resolve -a ipaddress

```

This also might work (It doesn't on my home network though):
```

nmblookup -A ipaddress

```
I think nmblookup will require a windows computer, or winbind installed.

---

