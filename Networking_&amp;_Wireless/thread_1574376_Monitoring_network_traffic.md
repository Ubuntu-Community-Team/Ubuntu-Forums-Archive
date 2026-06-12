---
title: "Monitoring network traffic"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by s.v.z on 2010-09-14
Hi everyone. I am connected to a network with free traffic inside it and post-paid outer traffic. So I need a way to be able to separately monitor the download traffic from inside and outside the network. All the solutions I`ve found for now offer monitoring of ALL up/down traffic.

So, I want to get separate statistics on these:

1 &#8212; 81.89.188.0/23, 217.197.9.0/24
2. &#8212; 81.89.186.0/23
3. &#8212; 81.89.178.0/23
4. &#8212; 81.89.176.0/23
5. &#8212; 81.89.180.0/24
9. &#8212; 217.197.12.0/24
10. &#8212; 92.42.30.0/24
12. &#8212; 92.42.28.0/24
13. &#8212; 92.42.31.0/24
14. &#8212; 92.42.26.0/23, 217.197.10.0/24
15. &#8212; 217.197.0.0/23, 217.197.7.0/24
16. &#8212; 217.197.6.0/23
17. &#8212; 81.89.181.0/24
18. &#8212; 195.70.216.0/24
20. &#8212; 217.197.11.0/24
21. &#8212; 217.197.2.0/23
22. &#8212; 217.197.4.0/23
23. &#8212; 217.197.8.0/24
1) &#8212; 81.89.185.0/24

and another on all the rest.

UPD: I`m connected to the internet through the network`s gate, so all the traffic comes through eth0. I wish to separate traffic incoming from the IPs on top from all other traffic

---

### Post by BkkBonanza on 2010-09-14
If you don't find a better solution I can show you how to do it with iptables. It's a bit raw as far as data but it does have the info.

---

### Post by elico on 2010-09-14
well there is nothing wrong with monitoring all the up and down traffic if it per ip+\session
you just need to analyze the log somehow with a script on what so ever.

the other option of iptables sounds fantastic but you first need to master a bit IPTABLES.

just to understand the topology:
you have one computer with internet access but some interconnection\strait connection to these networks?

---

### Post by BkkBonanza on 2010-09-14
I know there's another tool for this because I needed it once and found it. But all I can find at the moment is this,

[http://ipband.sourceforge.net/](http://ipband.sourceforge.net/)

You might have a look and see if it does what you need. If I can recall the other one I used then I'll post back later.

Edit: ah, yes now I have it. IPAudit will record all connections and how much traffic it used. This would be too much info for just a total so the output data would have to be run through a script to merge IPs in your networks. Maybe too much work. But anyway, this tool certainly collects all the information needed but would need additional steps to summarize.

[http://ipaudit.sourceforge.net/documentation/manpages/ipaudit.html](http://ipaudit.sourceforge.net/documentation/manpages/ipaudit.html)

The iptables method is fairly simple and will give a running total per network.

---

### Post by annoyingrob on 2010-09-14
What are you using to route traffic?

For example, I have an Ubuntu server which does all my internet routing, which I've installed bandwidthd on. I can see how much traffic the server is passing in and out of the cable modem, as well as all of the traffic it's passing inside the network.

---

### Post by s.v.z on 2010-09-14
> **BkkBonaza said:**
> If you don't find a better solution I can show you how to do it with iptables. It's a bit raw as far as data but it does have the info.

well, I`ve been adviced to use iptables just before, but this is fairly the first day I`ve heard of such a thing, so it was not of much use..

> **elico said:**
>  ...just to understand the topology:
you have one computer with internet access but some interconnection\strait connection to these networks?

I am connected to the internet through this network`s gate.

> **BkkBonaza said:**
> I know there's another tool for this because I needed it once and found it. But all I can find at the moment is this,

[http://ipband.sourceforge.net/](http://ipband.sourceforge.net/)

You might have a look and see if it does what you need. If I can recall the other one I used then I'll post back later.

Edit: ah, yes now I have it. IPAudit will record all connections and how much traffic it used. This would be too much info for just a total so the output data would have to be run through a script to merge IPs in your networks. Maybe too much work. But anyway, this tool certainly collects all the information needed but would need additional steps to summarize.

[http://ipaudit.sourceforge.net/documentation/manpages/ipaudit.html](http://ipaudit.sourceforge.net/documentation/manpages/ipaudit.html)

The iptables method is fairly simple and will give a running total per network.

Thanks, I`ll take a look at these.

> **annoyingrob said:**
> What are you using to route traffic?

For example, I have an Ubuntu server which does all my internet routing, which I've installed bandwidthd on. I can see how much traffic the server is passing in and out of the cable modem, as well as all of the traffic it's passing inside the network.

I`m just using a laptop. And I`m connected to the internet through the network`s gate, so I get all the traffic through eth0

---

### Post by elico on 2010-09-14
so you want to now how much traffic your laptop is consuming and this laptop is using ubuntu desktop.
am i right?


if so.. and also you have never heard of this before then it depends how much effort you want to put into it.

iptables is a firewall for linux and it's pretty simple to use for your needs.
you will need to dirt your hands a bit but if English is natural language for you and a little reading is ok then you are good to go.

the steps for your needs are:
1. installing iptables
2. activating iptables with default "accept" policy.
3. turn the firewall on and make sure everything is running.
4. add a "table" that will store the statistics for the specific subnets.
5. run a small test to get hold of iptables functions.
6. create (not from scratch) a script to log the statistics to files in background.
7. test and save and make it start at boot or on demand.
(iptables suppose to be integrated in ubuntu so you probably wont need to install it)


to install iptables
in terminal enter
sudo apt-get install iptables

to remove iptables 
sudo apt-get remove iptables


if you are willing to sit your *** a bit i can write full instructions for you.
just to get hold of what it will take you can look at

[http://www.linux.com/learn/tutorials/305767-bandwidth-monitoring-with-iptables](http://www.linux.com/learn/tutorials/305767-bandwidth-monitoring-with-iptables)

---

### Post by s.v.z on 2010-09-14
Well, I`ve got a time to waste, so if you do write some instructions I`ll be very thankful. I`ve read the man iptables, but this didn`t make things much clearer.
And yes, it`s Ubuntu desktop.

---

### Post by BkkBonanza on 2010-09-14
I'll show you the iptables method here in case you want to use it. iptables isn't usually used for tracking usage but it can do it as a side effect of rules added.

You create a rule for each network you want to separately track, like this,

sudo iptables -A INPUT -s 81.89.188.0/23 -j ACCEPT
...

For each rule iptables will keep a running count of bytes transferred. But it will lose the count upon shutdown so you need to add commands to your /etc/network/interfaces file so that counts are saved/restored when the interface is brought up and down.
eg.

```
auto eth0
iface eth0 inet dhcp
... other lines maybe...
    up iptables-restore -c < /var/run/traffic-counts
    down iptables-save -c > /var/run/traffic-counts
```
(If you are using Network Manager and there is no eth0 listed in interfaces then you will want to add a one line script to if-up.d and if-down.d directories instead.)

It would also be a good idea to add a similar line to your crontab for about every 5 minutes so if the system crashes or powers off unexpectedly then you will have saved the count recently.

sudo crontab -e

add same save command,

*/5 * * * *  /sbin/iptables-save -c >/var/run/traffic-counts

You can view the traffic counts at any time in the file or by typing,

sudo iptables -vnL

For totals you would need a script or add them manually. 

That's the general idea though, not too much work to set up.

---

### Post by elico on 2010-09-14
im now sitting  waiting for the doctor so i have some time.
im using ubuntu server as home file server , router and central download station.
so i was trying it now just to make sure how it looks like.

i will do it in parts:
this is a tutorial that contains the base script.

[http://wiki.openvz.org/Traffic_accounting_with_iptables](http://wiki.openvz.org/Traffic_accounting_with_iptables)

so wait for me.

edit:
well so i waited 4 hours for the doctor and the battery ran out so i couldnt write it but i almost done.

so tomorrow i will post it.

---

### Post by s.v.z on 2010-09-15
ok, I`ve got nowhere to hurry.

---

### Post by elico on 2010-09-16
almost done with the scripts and everything.
and i must say i was the big benefit from all of it..
i need to monitor my network activity and im using this concept.

---

### Post by elico on 2010-09-21
it took me awhile and let see if it's understandable:

iptables comes default with any distribution of ubuntu and dont bother to understand it cause it just works and you will need to add some rules to understand it but just basic and you will see how it will react.

so get into terminal and run

sudo /sbin/iptables -L -v -n

you will get a list of the current rules and it should list you with 3 accept (something like that)
> 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

then we will add a "table" or what so called  "chain" that will contain the list of ip classes you want to monitor/isolate from others

we will call the new chain "free"

sudo iptables -N free

sudo iptables -A INPUT -s 81.89.188.0/23 -j free
sudo iptables -A OUTPUT -d 81.89.188.0/23 -j free

you can add any subnet or ip you would like using these two commands to the "free" list.

starting now iptables is making statistics.

next step is to save the settings to file.

sudo iptables-save >/etc/network/stat.rules

if you want to see the raw rules you can enter

> sudo iptables-save the next step is to see the raw statistic information

sudo iptables -nvx -L INPUT |grep "free"

this will give you something like that.

> 
   35  4533            all  --  venet0 *       0.0.0.0/0            192.168.0.117

if you want to get statistics for download and upload seperetly you should make specific rules one for upload and the other for download in the "free" chain.

something like


> 
sudo iptables -A free -i eth0
sudo iptables -A free -o eth0
this will make rules that counts one the amount of input data and the other the amount of output data.


and then to get the list of statistics you can use:
> 
sudo iptables -nvx -L free
the counters reset on reboot and\OR using the command
> 
sudo iptables -Z
the next step is to collect the statistics and store them a file with log.
after you will have the file you can do with it what ever you want, you can store it on database and\or get a visual log.

im taking the approach that you just want to collect the ammount of traffic you are using on these "free" networks.
based on  [http://wiki.openvz.org/Traffic_accounting_with_iptables](http://wiki.openvz.org/Traffic_accounting_with_iptables)
this is a script to log the current traffic.

we will create a file  with the list of subnets for the log script.
it will contain text only each subnet on seperate line
the file name is:
/etc/var/log/freenets
> 
81.89.188.0/23
81.89.186.0/23
81.89.178.0/23
81.89.176.0/23
81.89.180.0/24
81.89.181.0/24
81.89.185.0/24
92.42.30.0/24
92.42.28.0/24
92.42.31.0/24
92.42.26.0/23
195.70.216.0/24
217.197.12.0/24
217.197.9.0/24
217.197.10.0/24
217.197.0.0/23
217.197.7.0/24
217.197.6.0/23
217.197.11.0/24
217.197.2.0/23
217.197.4.0/23
217.197.8.0/24
the script:

> 

trafficlog="/var/log/freenet-stat.log"
for i in `/etc/var/log/freenets` ;
 do
  echo -n `date "+%Y-%m-%d %H:%M:%S"` >> $trafficlog
  echo -n " $i " >> $trafficlog
  echo -n " IN " >> $trafficlog
  echo `iptables -nvx -L INPUT | grep " $i " | tr -s [:blank:] |cut -d' ' -f3| awk '{sum+=$1} END {print sum;}'` >> $trafficlog
  echo -n " OUT " >> $trafficlog
  echo `iptables -nvx -L OUTPUT | grep " $i " | tr -s [:blank:] |cut -d' ' -f3| awk '{sum+=$1} END {print sum;}'` >> $trafficlog
 done
 # reset the counter
 iptables -Z
to make this log effective you need to schedule it using cron every hour and also every time your network adapter is going down.
(it's a matter of adding lines into some files)

if you get the point then im here and i can write a complete tutorial how to do it from scratch.

IF YOU NEED A REMAKE or even more im here.
(i didnt have much time to explain and complete it)

---

### Post by s.v.z on 2010-09-22
elico, thanks for your help. I`ve done as you wrote and most of this seems to work right. Here is where I have some trouble:

```
svz@svz-laptop:~$ sudo iptables-save>/etc/network/stat.rules
bash: /etc/network/stat.rules: Access denied
```

I`ve saved the file in ~/stat.rules for now.

The same happens when I run the script. I`ve also changed the paths to my homefolder, but it says:

```
svz@svz-laptop:~$ sudo ~/getNetStat  <-This is the script file
/home/svz/getNetStat: line 2: /home/svz/freenet-stat.log: Access denied
/home/svz/getNetStat: line 11: /home/svz/freenets: Access denied
```



Some more things I`d like to ask: 
1. If I wish to get separate stats on all the networks EXCEPT the ones in the "free" table, should I just get the total download and subtract the "free" result or can I make a rule to count everything except "free"?

2. I`d be very thankful if you cold advise some good literature on bash scripts. All I`ve found for now seems either much like "man %name%" or too simple, covering only cd, cp and so on..

---

### Post by elico on 2010-09-28
i started writing the main script for you...
my replay before was the basics so i will try in the next week or two to make it.

first with scripts is to try using saving and do anything with them in the /tmp directory cause it's not restricted.

all the "Access denied" errors you are getting is caused by the files permissions.

to make it simple you can just need to change the owner and group for the files you are using for and in the script.

the linux permission methodology is that every file or object in the file system has 3 access levels.
1. owner
2. group
3. others

you can assign 3 permissions read write and execute.

for simple trials of scripts logs and every other usage you can assign "allow to all anything"
using the command

>  sudo chmod 777 /home/svz/freenet-stat.logor what ever file or folder you want.

this will give full access to all users in the system to do anything with these files and folders.

and for 1.
dont forget that the main objective of iptables is to be a firewall.
you are just using the side effects of this marvelous application to count network usage.
so if you want to get different stats for other networks other then you will need to see how the iptables works with chains.
the concepts you will need for this task is:
subnet 0.0.0.0/0 is "everything"
and every other subnet then that is more specific.
the chains system is "first rule wins"

so i will do it with a list of rules that will transfer the subnets to another chain.
in this chain you will have one rule for 0.0.0.0/0
this rule will count every traffic that gets to it (the "first win" rules for the free subnes)
and then a second rule to move every traffic to another chain that will count everything.
(in it a rule for counter)
so you will get two new chains with counters but one for all the traffic and the other one to the free networks.

that's works as your concept :)

and then... subtract the free from all the traffic.

for the 2. 
the real thing with bash is that it fairly simple.
it has "if" loop
also "while" loop
"for" loop
variables
and the pipe "|"

the main thing with bash is that most of linux tools are build for a "bash" like interacting which means you can do so much with the tools that comes with most of the linux OS using only bash scripts.

just think about that you can do this specific thing of counting traffic usage by the built in tools of bash.

i really dont now that much of bash but until now i'v used it for a long time for specific usage at work and i just like it!

just 2 month ago a friend from work was asked to do some IT task for the windows network and he wrote a "batch" file (dos script) but from a reason it didnt work for him so i sat and in 2 seconds i fixed the script for him to do the specific thing he needed using "old dos" scripting i used to do so much :)

---

