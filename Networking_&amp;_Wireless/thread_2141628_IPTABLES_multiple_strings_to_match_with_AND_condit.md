---
title: "IPTABLES multiple strings to match with AND condition"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by docteur on 2013-05-03
Hello,

I need to apply an iptables rules using --string option.

I need to match on --hex or ascii 2 strings that are never localized on the same area.

Each samples I tried DROP only one of my two strings, so i have false positive.
I need to DROP the 2 STRINGS, but when i have only 1 string or the other, i don't want to DROP.

So, the rule what i am looking for is a AND rule around iptables.

So, I tried :

a. [FONT=Verdana]iptables -I INPUT -j DROP -p udp -m string --string "TEST1" --algo bm -m string --string "TEST2" --algo bm
--> Not working, it is look like i have 2 different rules, so it is blockind or TEST1 or TEST2, but not TEST1 AND TEST2 : so False Positive

b. [/FONT][COLOR=#000000][FONT=Arial]iptables -N my_chain
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]iptables -A my_chain -j DROP
iptables -A my_chain -j QUEUE ! -f -m string --string "TEST2" --algo bm
iptables -A INPUT -j my_chain ! -f -m string --string "TEST1" --algo bm
[FONT=Verdana]--> Not working, it is look like i have 2 different rules, so it is blockind or TEST1 or TEST2, but not TEST1 AND TEST2 : so False Positive
[/FONT]
Any idea ?

Thanks for your precious help[/FONT][/COLOR]

---

### Post by Doug S on 2013-05-03
Hi, and welcome to Ubuntu forums.

First, please be aware that use that use of the iptables string module can be somewhat CPU intensive. There was a time, years ago, where one had to compile the kernel to be able use the iptables string function, as the default didn't have it.

I don't understand the order of things done in your example b, and I suspect the order might be all that is wrong. I was thinking of something like:```
sudo iptables -A INPUT -m string --algo bm --string "TEST1" -j check_for_2
... other INPUT rules ...
sudo iptables -N check_for_2
sudo iptables -A check_for_2 -m string --algo bm --string "TEST2" -j DROP
```

---

### Post by docteur on 2013-05-06
Hello Doug, Thanks for your answer, but iptables doesn't accept rules in this order. I have errors. So I'm obligate to write as I wrote, but the 2 conditions are not working. If you some other ideas, I'm open to test ;-) Hope to read you soon, Doc

---

### Post by Doug S on 2013-05-06
The rules work fine for me. However, please note that I was just writting them to convey the concept, but the user table needs to be defined before trying to use it. So the order in my example should have been:```
sudo iptables -N check_for_2
sudo iptables -A INPUT -m string --algo bm --string "TEST1" -j check_for_2
... other INPUT rules ...
sudo iptables -A check_for_2 -m string --algo bm --string "TEST2" -j DROP
```And here are some examples, checking that it works:```
doug@doug-64:~/test2$ [COLOR=#ff0000]wget http://test-smy.smythies.com/Test1blablablaTest2[/COLOR]
--2013-05-06 08:01:55--  http://test-smy.smythies.com/Test1blablablaTest2
Resolving test-smy.smythies.com (test-smy.smythies.com)... 192.168.111.140
Connecting to test-smy.smythies.com (test-smy.smythies.com)|192.168.111.140|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-05-06 08:01:55 ERROR 404: Not Found.doug@doug-64:~/test2$ [COLOR=#ff0000]wget http://test-smy.smythies.com/TEST1blablablaTEST2[/COLOR]
--2013-05-06 08:02:44--  http://test-smy.smythies.com/TEST1blablablaTEST2
Resolving test-smy.smythies.com (test-smy.smythies.com)... 192.168.111.140
Connecting to test-smy.smythies.com (test-smy.smythies.com)|192.168.111.140|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.
--2013-05-06 08:03:06--  (try: 2)  http://test-smy.smythies.com/TEST1blablablaTEST2
Connecting to test-smy.smythies.com (test-smy.smythies.com)|192.168.111.140|:80... connected.
HTTP request sent, awaiting response... ^C
doug@doug-64:~/test2$ [COLOR=#ff0000]wget http://test-smy.smythies.com/TEST2blablablaTEST1[/COLOR]
--2013-05-06 08:03:18--  http://test-smy.smythies.com/TEST2blablablaTEST1
Resolving test-smy.smythies.com (test-smy.smythies.com)... 192.168.111.140
Connecting to test-smy.smythies.com (test-smy.smythies.com)|192.168.111.140|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.
``````
doug@test-smy:~$ sudo iptables -v -x -n -L
[sudo] password for doug:
Chain INPUT (policy [COLOR=#ff0000]ACCEPT 309 packets, 22614 bytes[/COLOR])
    pkts      bytes target     prot opt in     out     source               destination
      [COLOR=#ff0000]25 [/COLOR]    4800 [COLOR=#ff0000]check_for_2 [/COLOR] all  --  *      *       0.0.0.0/0            0.0.0.0/0            STRING match  "TEST1" ALGO name bm TO 65535
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
Chain OUTPUT (policy [COLOR=#ff0000]ACCEPT 282 packets, 35072 bytes[/COLOR])
    pkts      bytes target     prot opt in     out     source               destination
Chain check_for_2 (1 references)
    pkts      bytes target     prot opt in     out     source               destination
      [COLOR=#ff0000]25[/COLOR]     4800 [COLOR=#ff0000]DROP[/COLOR]       all  --  *      *       0.0.0.0/0            0.0.0.0/0            STRING match  "TEST2" ALGO name bm TO 65535
```

---

### Post by docteur on 2013-05-06
Thanks Doug, I took your sample and it is working well now. Thanks sincerly for your help. Best Regards Marc

---

