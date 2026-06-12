---
title: "Bash Script using nslookup and nmap"
date: 2013-08-31
forum: Networking &amp; Wireless
---

### Post by fred14 on 2013-08-31
Hello 
I'm trying to create a script in bash that i only enter the domain name and it will search that domain fo the Ip address and scan that host for only the IPv4 and save in a text file only those IPv4 results and using and nmap scan call that file and scan those IPv4, i have try many options but nothing work.

i will appreciated your help guys or point me in the right direction.

thanks

This is the script I am working

#!/bin/bash
read -p "Domain to Scan: " domain
read -p "File to Save: " file
dig +nocmd $domain any +multiline +noall +answer | grep '5' | awk '{print $5}' > $file
cat $file
for hostname in (cat $file);do
host $hostname
done

---

### Post by prodigy_ on 2013-08-31
So what exactly doesn't work?

Anyway (if I correctly understand what you're trying to achieve):
```
#!/bin/bash

read -p "Domain to Scan: " domain_name
read -p "File to Save: " file_name

ip_list=$(dig +nocmd "$domain_name" any +multiline +noall +answer | \
	grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}' | tee "$file_name")

for ip_addr in $ip_list; do
	nmap -v "$ip_addr"
done
```

---

### Post by SeijiSensei on 2013-08-31
You have to run nmap as the root user to have it scan ports; an ordinary user can only do things like ping scans.  Try running the whole script with sudo and see if that helps.

---

### Post by fred14 on 2013-09-01
Thank you guys for the information, I was working I was unable to reply but I will try now.

---

