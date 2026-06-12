---
title: "pop hack blocking script"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by Vishal Agarwal on 2012-05-31
Hi,

I have created the below shell script to check hacking attack to my dovecote server that i am facing everyday from different IP's. Can it be more better then my one ?

> 
#!/bin/bash
TotalData=$(grep dove /var/log/auth.log | grep "authentication failure" | awk '// {print $13 "," $14}' | replace "ruser=" "" | replace "rhost=" "")
for i in $TotalData
do
        UserName=$(echo $i | cut -d"," -f 1)
        UserIp=$(echo $i | cut -d"," -f 2)
#        echo "UserName = $UserName , UserIp = $UserIp "

        if [ -d "/home/$UserName" ]; then
                {
                (echo "User $UserName Exist")
                }
        else
                {
                (echo "User $UserName does not Exist")
                if [ !  $(iptables -L -vn | grep $UserIp) ]; then
                        {
                        (echo "iptables -A input-pop-hack-blocked  -i eth1 -s $UserIp -p tcp --dport 110 -j DROP")
                        $(iptables -A input-pop-hack-blocked  -i eth1 -s $UserIp -p tcp --dport 110 -j DROP)
                        }
                else
                        {
                        (echo " IP Address $UserIp aleeady added to firewall ")
                        }

                fi
                }
        fi



done


any modifications welcome.

---

