---
title: "tcpdump captured packets store Mysql problem"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by bhaskar_goel on 2009-01-16
we are capturing packets using tcpdump and trying to store them in a mysql database. we are running the following script to do this :-
tcpdump -i eth0 -n -q -e | grep IPv4 | awk -F "[:, >]" {'print $24 " " $27 " " $22'} | awk -F "[. ]" '{

                if ($11 == "")

                print "\""$1"."$2"."$3"."$4"\",\""$5"."$6"."$7"."$8"\","$9

                else

                print "\""$1"."$2"."$3"."$4"\",\""$6"."$7"."$8"."$9"\","$11

               }' > /var/collect-eth1.txt &

 awk '{print"use collections;INSERT INTO packets(source,destination,pack_size) VALUES($1,$3,$8);"}'| mysql -u root -p
while no error is being reported no data is being recorded in the database.

Can someone point the way ?

---

