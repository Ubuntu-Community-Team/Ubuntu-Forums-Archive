---
title: "Blacklist IP Address by country of origin script"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by themanwithaplan on 2012-11-06
Im getting hacking attacks from Russian and Brazilian IP addresses, so Ive made a dark greylist and light greylist. Submitting this to help others that wish to do the same
 
Run this firewall rule permanently:
iptables -I INPUT -p tcp --dport 21:22 --syn -m limit --limit 1/m --limit-burst 5 -j LOG --log-prefix "sshftp hammering: " --log-level 1
 
 
Run script as root daemon:
#Script by Avishek Chaudhuri
while [ 1 -eq 1 ]
do
sleep 30
tail -n 1 /var/log/syslog | grep -o sshftp\ hammering.* | awk '{print $6;}' | grep -o [0-9]*[.][0-9]*[.][0-9]*[.][0-9]
HAMMERING=$?
if [ $HAMMERING -eq 0 ]
then
echo 'sshftp hammering detected'
tail -n 1 /var/log/syslog | grep -o sshftp\ hammering.* | awk '{print $6;}' | grep -o [0-9]*[.][0-9]*[.][0-9]*[.][0-9] | grep -o 192[.]168.*
FRIEND=$?
if [ $FRIEND -ne 0 ]
then
echo 'sshftp is being hammered by adversary, checking if in blacklist'
iptables -L > /tmp/badlistcheckiptablesdump.txt
tail -n 1 /var/log/syslog | grep -o sshftp\ hammering.* | awk '{print $6;}' | grep -o [0-9]*[.][0-9]*[.][0-9]*[.][0-9] > /tmp/badlistcheckbadip.txt
grep -f /tmp/badlistcheckbadip.txt /tmp/badlistcheckiptablesdump.txt
ALREADYBLACKLISTED=$?
if [ $ALREADBLACKLISTED -ne 0 ]
then
echo 'not blacklisted yet, lets add him to blacklist'
for BADIP in `cat /tmp/badlistcheckbadip.txt`
do
whois $BADIP | grep country[:].*'\|'.*JPNIC.* | grep .*GB.*'\|'.*AU.*'\|'.*US.*'\|'.*JPNIC.*'\|'.*SG.*'\|'.*IE.*'\|'.*FR.*'\|'.*BE.*'\|'.*IN.*'\|'*.DE.*
FRIENDLYCOUNTRY=$?
if [ $FRIENDLYCOUNTRY -eq 0 ]
then
echo 'Attack from friendly country put moderate shields in place'
iptables -I INPUT -p tcp --syn -m iprange --src-range $BADIP -j DROP -m comment --comment "Friendly blacklist"
iptables -I INPUT -p tcp --dport 21:22 --syn -m iprange --src-range $BADIP -m limit --limit 5/d --limit-burst 5 -j ACCEPT -m comment --comment "Friendly blacklist"
fi
if [ $FRIENDLYCOUNTRY -ne 0 ]
then
echo 'Attack from unfriendly country maximum shields'
iptables -I INPUT -p tcp --syn -m iprange --src-range $BADIP-$BADIP -j DROP -m comment --comment "Unfriendly blacklist"
iptables -I INPUT -p tcp --dport 21:22 --syn -m iprange --src-range $BADIP-$BADIP -m limit --limit 2/d --limit-burst 2 -j ACCEPT -m comment --comment "Unfriendly blacklist"
fi
done
fi
fi
fi
done;

---

