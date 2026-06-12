---
title: "storing tcpdump captured data in mysql database"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by bhaskar_goel on 2009-01-15
i am working on a project regarding network monitoring, as a first step i need to store the info collected from tcpdump into a mysql database, i am using the following script for this
#! /bin/sh
# mysql-collect.sh
# Store to text file then to MySQL Database
ifconfig eth0 up
sudo tcpdump -i eth0 -n -q -e | grep IPv4 | awk -F "[:, >]" {'print $24 " " $27 " " $22'} | awk -F "[. ]" '{
                if ($11 == "")
                print "\""$1"."$2"."$3"."$4"\",\""$5"."$6"."$7"."$8"\","$9
                else
                print "\""$1"."$2"."$3"."$4"\",\""$6"."$7"."$8"."$9"\","$11
               }' > /var/collect-eth0.txt &
tail -f /var/collect-eth0.txt | awk '{print "USE collections ; INSERT INTO packets (source, destination, pack_size) VALUES ("$1");"}' | mysql -u root -p
~                                                                      

i  get  an unkown database error,even though the database name is correct. can someone point the way????????

---

