---
title: "Need help configuring connection sharing via UFW."
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by oygle on 2011-02-23
I've been using Firestarter for ages now, and it constantly gives problems.

Can someone please advise what I need to do, to replace Firestarter with UFW ?

I don't think it is a plain uninstall Firestarter, and then install UFW (although I think UFW is installed by default), as Firestarter has pushed 'rules' into iptables.

I guess I need to dump/list/view those 'rules' first, then 'flush' the rules, so iptables is 'bare bones', then uninstall Firestarter, and install UFW (plus the GIU for it).

I probably have it all wrong though ??

Running 2 computers with 10.04, so one connects via mobile broadband, and the other connects through the first one (gateway).

Oygle

---

### Post by cariboo on 2011-02-23
> **oygle said:**
> I've been using Firestarter for ages now, and it constantly gives problems.

Can someone please advise what I need to do, to replace Firestarter with UFW ?

I don't think it is a plain uninstall Firestarter, and then install UFW (although I think UFW is installed by default), as Firestarter has pushed 'rules' into iptables.

I guess I need to dump/list/view those 'rules' first, then 'flush' the rules, so iptables is 'bare bones', then uninstall Firestarter, and install UFW (plus the GIU for it).

I probably have it all wrong though ??

Running 2 computers with 10.04, so one connects via mobile broadband, and the other connects through the first one (gateway).

Oygle

All you have to do is make sure firestarter isn't running, the use the purge option of either apt-get or aptitude. Use the following commands:

```
ps ax | grep firestarter
```

to find the firestarter pid, then

```
sudo kill pid
```

once firestarter is dead

```
sudo apt-get purge firestarter
```

Ufw is installed by default, but you may want to install gufw for a graphical interface.

---

### Post by bodhi.zazen on 2011-02-23
You need to simply remove firestarter with the purge option.

```
sudo apt-get purge firestarter
```

If you wish you can install gufw for a graphical interface.

See also:

	[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
	[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
	[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by oygle on 2011-02-23
Thanks cariboo907 and bodhi.zazen for your replies. I have dumped the iptables 'rules' to a .txt file, just in case there is something I may miss.

Will purge firestarter and install gufw.

Thanks,

Oygle

---

### Post by oygle on 2011-02-24
Have purged firestarter and enabled firewall via GUFW, but gufw doesn't show the iptables rules.

I think that is because the rules were added by firestarter ?? That is why I asked if the iptables should be flushed prior to this, or whatever the command is, to clean out everything from iptables.  That way I know that only ufw (via gufw) has added any rules that are needed.

---

### Post by doas777 on 2011-02-24
well first, run
```

sudo ufw status

```to list the status and rules in play. 

if all you see is 'status: active' then you don't have any rules at present.

one bit of advice on gufw vs firestarter: I always had the urge to run firestarter all the time and keep it in the task tray. don't do that with gufw. just open it when you want to edit your rules. otherwise you don't need it running to have your firewall active (and be sure to run it with gksu).

you can run this to dump the rules in iptables to a file in your home for your review:
```
sudo iptables -L > chains.txt
```

---

### Post by oygle on 2011-02-24
> **doas777 said:**
> if all you see is 'status: active' then you don't have any rules at present.

Yes, all I see is 'active'. **BUT** I know from an iptables 'list', there are many rules ??

> **doas777 said:**
> one bit of advice on gufw vs firestarter: I always had the urge to run firestarter all the time and keep it in the task tray. don't do that with gufw. just open it when you want to edit your rules. otherwise you don't need it running to have your firewall active (and be sure to run it with gksu).

Yes, okay thanks, I don't have gufw running all the time. It's run from the menu 'System | Admin | Firewall Configuration', but it seems I should be doing ..

```

gksu gufw

```

is that correct ?

> **doas777 said:**
> 
you can run this to dump the rules in iptables to a file in your home for your review:
```
sudo iptables -L > chains.txt
```

Many rules, like the file has 268 lines in it, including empty lines for formatting, but there are a lot of rules there.

Thanks,

Oygle

---

### Post by oygle on 2011-02-24
There are 2 computers, one is the gateway, and the other uses the gateway.

The gateway computer has ufw/gufw installed and firestarter removed. It all worked fine until I rebooted the gateway computer, then internet on the gateway was okay, but on the client, I lost the internet connection.

The syslogs on the client told me nothing. I could ping either computer either direction, but could not get 'outside' to the net, from the client.

The syslogs on the gateway were filling up fast, as follows ..

> 
Feb 24 19:21:29 computername kernel: [ 3960.871991] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.100 DST=192.168.1.255 LEN=185 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=165 
Feb 24 19:21:29 computername kernel: [ 3960.872040] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.100 DST=192.168.1.255 LEN=185 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=165 
Feb 24 19:21:33 computername kernel: [ 3964.536043] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=66.102.11.100 LEN=804 TOS=0x00 PREC=0x00 TTL=64 ID=18723 DF PROTO=TCP SPT=46369 DPT=80 WINDOW=116 RES=0x00 ACK PSH URGP=0 
Feb 24 19:21:34 computername kernel: [ 3965.272003] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=66.102.11.100 LEN=804 TOS=0x00 PREC=0x00 TTL=64 ID=18724 DF PROTO=TCP SPT=46369 DPT=80 WINDOW=116 RES=0x00 ACK PSH URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.197293] [UFW AUDIT] IN=ppp0 OUT= MAC= SRC=66.102.11.100 DST=220.233.***.*** LEN=52 TOS=0x00 PREC=0x00 TTL=58 ID=64509 PROTO=TCP SPT=80 DPT=46369 WINDOW=136 RES=0x00 ACK URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.224087] [UFW AUDIT] IN=ppp0 OUT= MAC= SRC=66.102.11.100 DST=220.233.***.*** LEN=1470 TOS=0x00 PREC=0x00 TTL=58 ID=64510 PROTO=TCP SPT=80 DPT=46369 WINDOW=136 RES=0x00 ACK URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.224134] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=66.102.11.100 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=18725 DF PROTO=TCP SPT=46369 DPT=80 WINDOW=162 RES=0x00 ACK URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.224189] [UFW AUDIT] IN=ppp0 OUT= MAC= SRC=66.102.11.100 DST=220.233.***.*** LEN=222 TOS=0x00 PREC=0x00 TTL=58 ID=64512 PROTO=TCP SPT=80 DPT=46369 WINDOW=136 RES=0x00 ACK PSH URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.224221] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=66.102.11.100 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=18726 DF PROTO=TCP SPT=46369 DPT=80 WINDOW=162 RES=0x00 ACK URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.232085] [UFW AUDIT] IN=ppp0 OUT= MAC= SRC=66.102.11.100 DST=220.233.***.*** LEN=1470 TOS=0x00 PREC=0x00 TTL=58 ID=64511 PROTO=TCP SPT=80 DPT=46369 WINDOW=136 RES=0x00 ACK URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.232133] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=66.102.11.100 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=18727 DF PROTO=TCP SPT=46369 DPT=80 WINDOW=207 RES=0x00 ACK URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.316066] [UFW AUDIT] IN=ppp0 OUT= MAC= SRC=66.102.11.100 DST=220.233.***.*** LEN=64 TOS=0x00 PREC=0x00 TTL=58 ID=64513 PROTO=TCP SPT=80 DPT=46369 WINDOW=136 RES=0x00 ACK URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.719176] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=66.102.11.100 LEN=780 TOS=0x00 PREC=0x00 TTL=64 ID=18728 DF PROTO=TCP SPT=46369 DPT=80 WINDOW=207 RES=0x00 ACK PSH URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.900587] [UFW AUDIT] IN=ppp0 OUT= MAC= SRC=66.102.11.100 DST=220.233.***.*** LEN=52 TOS=0x00 PREC=0x00 TTL=58 ID=64514 PROTO=TCP SPT=80 DPT=46369 WINDOW=159 RES=0x00 ACK URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.900633] [UFW AUDIT] IN=ppp0 OUT= MAC= SRC=66.102.11.100 DST=220.233.***.*** LEN=357 TOS=0x00 PREC=0x00 TTL=58 ID=64515 PROTO=TCP SPT=80 DPT=46369 WINDOW=159 RES=0x00 ACK PSH URGP=0 
Feb 24 19:21:35 computername kernel: [ 3966.900684] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=66.102.11.100 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=18729 DF PROTO=TCP SPT=46369 DPT=80 WINDOW=251 RES=0x00 ACK URGP=0 
Feb 24 19:21:36 computername kernel: [ 3966.938749] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=66.102.11.100 LEN=790 TOS=0x00 PREC=0x00 TTL=64 ID=18730 DF PROTO=TCP SPT=46369 DPT=80 WINDOW=251 RES=0x00 ACK PSH URGP=0 
Feb 24 19:21:36 computername kernel: [ 3967.140092] [UFW AUDIT] IN=ppp0 OUT= MAC= SRC=66.102.11.100 DST=220.233.***.*** LEN=1409 TOS=0x00 PREC=0x00 TTL=58 ID=64516 PROTO=TCP SPT=80 DPT=46369 WINDOW=183 RES=0x00 ACK PSH URGP=0 
Feb 24 19:21:36 computername kernel: [ 3967.140161] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=66.102.11.100 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=18731 DF PROTO=TCP SPT=46369 DPT=80 WINDOW=296 RES=0x00 ACK URGP=0 
Feb 24 19:22:00 computername kernel: [ 3991.872275] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.100 DST=192.168.1.255 LEN=185 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=165 
Feb 24 19:22:00 computername kernel: [ 3991.872299] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.100 DST=192.168.1.255 LEN=185 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=165 
Feb 24 19:22:00 computername kernel: [ 3991.872333] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.100 DST=192.168.1.255 LEN=185 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=165 
Feb 24 19:22:31 computername kernel: [ 4022.872124] [UFW AUDIT] IN= OUT=eth0 SRC=192.168.1.100 DST=192.168.1.255 LEN=185 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=165 
Feb 24 19:22:31 computername kernel: [ 4022.872142] [UFW ALLOW] IN= OUT=eth0 SRC=192.168.1.100 DST=192.168.1.255 LEN=185 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=165 
Feb 24 19:22:31 computername kernel: [ 4022.872167] [UFW AUDIT] IN=eth0 OUT= MAC= SRC=192.168.1.100 DST=192.168.1.255 LEN=185 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=165 
Feb 24 19:22:34 computername kernel: [ 4025.849092] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=74.125.237.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=65425 DF PROTO=TCP SPT=56524 DPT=80 WINDOW=121 RES=0x00 ACK FIN URGP=0 
Feb 24 19:22:35 computername kernel: [ 4026.440039] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=74.125.237.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=65426 DF PROTO=TCP SPT=56524 DPT=80 WINDOW=121 RES=0x00 ACK FIN URGP=0 
Feb 24 19:22:36 computername kernel: [ 4027.420086] [UFW AUDIT] IN=ppp0 OUT= MAC= SRC=74.125.237.12 DST=220.233.***.*** LEN=64 TOS=0x08 PREC=0x00 TTL=58 ID=58541 PROTO=TCP SPT=80 DPT=56524 WINDOW=120 RES=0x00 ACK URGP=0 
Feb 24 19:22:36 computername kernel: [ 4027.420135] [UFW AUDIT] IN=ppp0 OUT= MAC= SRC=74.125.237.12 DST=220.233.***.*** LEN=52 TOS=0x08 PREC=0x00 TTL=58 ID=58542 PROTO=TCP SPT=80 DPT=56524 WINDOW=120 RES=0x00 ACK FIN URGP=0 
Feb 24 19:22:36 computername kernel: [ 4027.420174] [UFW AUDIT] IN= OUT=ppp0 SRC=220.233.***.*** DST=74.125.237.12 LEN=52 TOS=0x08 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=56524 DPT=80 WINDOW=121 RES=0x00 ACK URGP=0 


As I do all my email, and other apps from the client, I have had to reboot the gateway computer into Win XP, at least it allows connect to the net for the client.

---

### Post by marquinos on 2011-02-24
Well... ufw+gufw and firestarter are frotends for iptables ;)

The rules are incompatibles between them, then you have the firestarter rules in your iptables, but ufw will not see it ;) OK?

My advance: 

[LIST]
[*]Reset all iptables rules > [http://acurti.es/leo](http://acurti.es/leo) (I think first result is fine).
[*]Restore by hand all rules in gufw from your text file.
[/LIST]
Best regards.

> 
gksu gufw
is that correct ?Yes, it's correct, you can try only: gufw, because gufw will call to the desktop file and autoinclude the "gksu" ;)

---

### Post by oygle on 2011-02-24
Hi marquinos, thanks for the tips. I will do a 'flush' on iptables, and see if that fixes it.  :)

...later: Have seen a post [here]("http://ubuntuforums.org/showpost.php?p=8668856&postcount=3"), on how to flush everything.

---

### Post by bodhi.zazen on 2011-02-24
> **marquinos said:**
> Well... ufw+gufw and firestarter are frotends for iptables ;)

The rules are incompatibles between them, then you have the firestarter rules in your iptables, but ufw will not see it ;) OK?

My advance: 

[LIST]
[*]Reset all iptables rules > [http://acurti.es/leo](http://acurti.es/leo) (I think first result is fine).
[*]Restore by hand all rules in gufw from your text file.
[/LIST]
Best regards.

Yes, it's correct, you can try only: gufw, because gufw will call to the desktop file and autoinclude the "gksu" ;)

That advice is good if you are configuring iptables manually, but poor in this case as ufw is configuring iptables, and those changes either will not be maintained when the OP reboots or worse will conflict with gufw.

gufw / ufw / firestarter are all front ends for iptables which is in turn a front end for netfilter.

You should **NOT** mix and match configuration tools, use firestarter - ufw/gufw - **OR** iptables but **do not mix and match these configuration tools**.

What you need to do is first purge firestarter. ufw / gufw will then manage iptables and you manage the rules with either the command line (ufw) or the graphical interface (gufw).

See the links I gave you.

To see your rules, on the command line,

```
sudo iptables -L -v -n
```

---

### Post by oygle on 2011-02-25
> **bodhi.zazen said:**
> What you need to do is first purge firestarter.

Gateway computer is 192.168.1.100
Client computer is 192.168.1.101

I did this on both computers ..

```

$ sudo apt-get purge firestarter

```

and both stated it wasn't installed.

> **bodhi.zazen said:**
> 
ufw / gufw will then manage iptables and you manage the rules with either the command line (ufw) or the graphical interface (gufw).


I have ufw / gufw istalled on both computers, but can still only connect to the internet via the gateway computer.

> **bodhi.zazen said:**
> 
See the links I gave you.


Thanks, I read up on gufw , the latest version has an incoming and outgoing 'accept/deny' now, so things are a little bit different.

> **bodhi.zazen said:**
> 
To see your rules, on the command line,

```
sudo iptables -L -v -n
```

Thanks, I ran that on both computers, and then compared the output. The only 'real' differences were the packets and number of bytes, so both computers have exactly the same setup. Here is the output from the gateway computer.

```

$ sudo iptables -L -v -n
Chain INPUT (policy DROP 6 packets, 328 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1917 1934K ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1917 1934K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   87 14392 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    6   328 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    6   328 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    6   328 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 2 packets, 80 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1547  182K ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1547  182K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  314 31159 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  314 31159 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  314 31159 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  314 31159 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    1    78 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:137 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
    2    96 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
    4   200 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:68 
   74 13690 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    6   328 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  314 31159 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   30  2068 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 1746 1908K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
    2    89 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
  139 23728 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       224.0.0.0/4          0.0.0.0/0           
   52  9336 ACCEPT     all  --  *      *       0.0.0.0/0            224.0.0.0/4         
   87 14392 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 1917 1934K LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 1547  182K LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   30  2068 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
 1203  149K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
  314 31159 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   13   702 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
   52  9336 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
   74 13690 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
   81 14064 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   49  2940 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
  263 28139 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
$
```

I have no idea what could be stopping the client from getting out to the internet.

Oygle

---

### Post by oygle on 2011-02-25
Tried to add a rule (GUFW) on the gateway computer, to allow all access from the client (192.168.1.101), and got a message ..

> 
Error performing operation


Yet I can add a rule via GUFW on the client ??

Oygle

---

### Post by marquinos on 2011-02-25
Yes, the gufw messages could be better ;)
Go to gufw menu > File / Log and copy the command.
Open a Terminal and paste the command (with sudo ufw......).
ufw will give you a better message about the problem ;)
Please, report here.
Best regards.

---

### Post by oygle on 2011-02-25
I was actually able to add the rule by UFW, no worries, ...**BUT** the only way I could get the client to have access to the internet, was to reboot the gateway computer into Windows XP, .. works fine.

I have checked and checked the syslogs on both computers, and there is nothing showing that would indicate the gateway blocking the client.

It has to be the gateway setup, because the client stayed booted up when I went into XP, which then became the 'new' gateway, and ...whoosh, the client had internet access.

Whether it is network related as well, I don't know.  I can't even ping to each computer, when I have gateway/clent booted as both Ubuntu.

Oygle

**PS**  With Firestarter, to 'enable' ICS, there was a checkbox. GUFW has nothing like that, so I'm thinking that the networking options for sharing the connection with the client may be the problem, ..maybe ??

---

### Post by marquinos on 2011-02-25
Uhm... Try the next:

[LIST]
[*]Disable Gufw (all will be open).
[*]Or purge Gufw (exists a bug, in a very few computers the Gufw installation blocks the outgoing traffic > no reasons found to this behavior).
[/LIST]
Good luck!

---

### Post by oygle on 2011-02-26
Thanks, but changing anything on GUFW seems to have no effect.  :(

---

### Post by oygle on 2011-02-27
Seems from a bit of Googling, that UFW/GUFW can't do ICS, is that correct ?

---

### Post by oygle on 2011-02-27
From the [Internet Connection Sharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing") community page, it states that with network manager, to make sure that dnsmasq-base is installed.

That was already installed on the gateway computer though.

Is it "safe" to do this ...

> 
After connecting the router, to enable masquerading, type: sudo iptables -t nat -A POSTROUTING -j MASQUERADE


Oygle

---

### Post by oygle on 2011-02-27
The Community [Firewall]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") guide has a section called "ufw Masquerading", which explains how to do the masquerading via UFW.

Considering 'bodhi.zazen's comments about **NOT** to mix and match, it would seem wiser to use UFW to do the masquerading, rather than write a rule directly to iptables.

Oygle

---

### Post by oygle on 2011-02-27
I still can't access the internet from the client computer.  :(

Also if I try

```

$ service iptables status

```

it gives the message "iptables: unrecognized service"

---

### Post by cariboo on 2011-02-27
try:

```
sudo ufw status
```

and to view the rules:

```
sudo ufw -L
```

---

### Post by oygle on 2011-02-27
> **cariboo907 said:**
> try:

```
sudo ufw status
```

Okay, here it is from the gateway (the obvious problem, as XP booted up 'lets' the client get out to the net.

> 
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW       192.168.1.0/24

53/udp                     ALLOW OUT   Anywhere


> **cariboo907 said:**
> 
and to view the rules:

```
sudo ufw -L
```

I guees you mean iptables ...

> 
$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             10.42.43.0/24       state RELATED,ESTABLISHED 
ACCEPT     all  --  10.42.43.0/24        anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  192.168.1.0/24       anywhere            

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 


and ..

> 
$ ifconfig -v
eth0      Link encap:Ethernet  HWaddr ************** 
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ***************** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14959 (14.9 KB)  TX bytes:13246 (13.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2488 (2.4 KB)  TX bytes:2488 (2.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:220.***.***.***  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1353172 (1.3 MB)  TX bytes:153484 (153.4 KB)


The syslogs on both computers are 'okay', in that the only traffic being blocked is intrusion attempts from 'out'. No (block) messages between the gateway and client computers.

The gateway still has full access, the client can only ping to itself and the gateway, either by the gateways IP address (192.168.1.100) or to the IP address assigned by the ISP (220.***.***.***)

Oygle

---

### Post by dmizer on 2011-02-28
If you just need to configure connection sharing, you should do so via the network-manager applet in the system notification area.

It's quite simple. Just right click on the network configuration icon and select "edit connections". Then select the wirless adapter that connects to your second computer and click "edit". Select the "IPv4 Settings" tab. Change the "method" to "Shared to other computers." It might help to make sure that there is a checkmark in "Available to all users". Then click "Apply".

You will now have internet sharing. No need to fiddle with UFW or Firestarter. Though make sure that UFW is correctly configured to limit incoming traffic since you have an external interface.

---

### Post by oygle on 2011-02-28
> **dmizer said:**
> If you just need to configure connection sharing, you should do so via the network-manager applet in the system notification area.

Yes, I have been using NM, to no avail though.   :(

> **dmizer said:**
> 
It's quite simple. Just right click on the network configuration icon and select "edit connections". Then select the wirless adapter that connects to your second computer and click "edit". Select the "IPv4 Settings" tab. Change the "method" to "Shared to other computers." It might help to make sure that there is a checkmark in "Available to all users". Then click "Apply".

You will now have internet sharing.

Yes, I had already done that, several times, but it did not work.  :(

Also, when using that method with NM, upon reboot, I had to set the IP address each time as follows

```

sudo ifconfig eth0 192.168.1.100

```

Surely there must be a method to set the IP address of eth0 , on the gateway permanently.

> **dmizer said:**
> 
No need to fiddle with UFW or Firestarter. Though make sure that UFW is correctly configured to limit incoming traffic since you have an external interface.

Firestarter used to do the (whole) ICS side of things before, and from the [Internet Connection Sharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing") community page, it states that with network manager, to make sure that dnsmasq-base is installed. I can easily uninstall dnsmasq-base, if that is not required.

Also fhe Community [Firewall]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") guide has a section called "ufw Masquerading", which explains how to do the masquerading via UFW. This has been applied, and those 3 files have been modified. If that is definitely _NOT_ required, then I have backups of the files, so easy to restore.

There does seem a lot of _conflicting_ information about how to do ICS with UFW. Those last few modifications I had done, in 'desperation' I suppose, as after 4 days, following advice on forums, ICS was still not working.

The setup is very simple, as follows ..

Internet <<==>> ppp0 <> Ubuntu gateway <> eth0 <<==>> Client PC

Oygle

---

### Post by oygle on 2011-02-28
Anyone please ??:confused:

---

### Post by bodhi.zazen on 2011-02-28
Does the connection work with ufw disabled ?

If not, get the connection working first with iptables, then convert the iptables rules to ufw or write a script to configure iptables (iptables-save / iptables-apply or iptables-restore for example).

I can not really tell from your post what you are doing, what you have configured, or where your problem is, but, no ufw / gufw will not configure iptables to do this, you will need to either know the iptables rules and then configure ufw or use an alternate tool.

You probably want to look at the documentation for NAT / Masquerade

---

### Post by oygle on 2011-02-28
Seems there are some bugs in Network Manager.

[NetworkManager Internet Connection Sharing fails to route DNS]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/389006")

[NetworkManager connection sharing broken]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/725041")

---

### Post by oygle on 2011-02-28
> **bodhi.zazen said:**
> Does the connection work with ufw disabled ?

No, no difference.

> **bodhi.zazen said:**
> If not, get the connection working first with iptables, then convert the iptables rules to ufw or write a script to configure iptables (iptables-save / iptables-apply or iptables-restore for example).

How do I (completely) clear iptables ??

There is a post [here]("http://ubuntuforums.org/showpost.php?p=8668856&postcount=3") of how to do it, is that correct ?

> **bodhi.zazen said:**
> I can not really tell from your post what you are doing, what you have configured, or where your problem is

The setup is as follows ..

Internet <<==>> ppp0 <> Ubuntu gateway <> eth0 <<==>> Client PC

The gateway computer has the 'share' option enabled, and the client computer has the gateway IP address set in NM. I use NM for both computers.

Gateway computer 192.168.1.100
Client computer 192.168.1.101

Problem - can connect to the internet okay with gateway, but **NOT** client.

Both computers worked perfectly when I used Firestarter, as it has an option to share the connection. When I purged Firestarter and replaced it with UFW/GUFW, that is when the problems started. So, it seems the issue is UFW/GUFW interfacing with Network Manager. In effect, it does not work.

I dropped Firestarter because it is no longer supported, and it was stopping the internet connection nearly every day, until I went into 'prefs' and just said 'ok' and all was well.

> **bodhi.zazen said:**
> , but, no ufw / gufw will not configure iptables to do this, you will need to either know the iptables rules and then configure ufw or use an alternate tool.

This thread started on the security forums, and moved to networking, and now we are looking at a possible security problem again ??  :confused:

> **bodhi.zazen said:**
> You probably want to look at the documentation for NAT / Masquerade

Arr, now there lies a big problem. There does not exist, and clear and precise documentation about how to setup ICS with UFW/GUFW. There is some conflicting documentation, especially in the area of whether or not to use dnsmasq, or just dnsmasq-base.

Also, there are those NM bugs, .... clearly a mess.  :(

Oygle

---

### Post by bodhi.zazen on 2011-02-28
You need to understand your firewall is called iptables.

You were configuring iptables with Firestarter.

ufw / gufw will NOT configure NAT for you, you will need to either do it manually or use an alternate tool.

See:

[http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

[http://www.billauer.co.il/ipmasq-html.html](http://www.billauer.co.il/ipmasq-html.html)

[http://www.akadia.com/services/pppoe_iptables.html](http://www.akadia.com/services/pppoe_iptables.html)

---

### Post by oygle on 2011-02-28
> **bodhi.zazen said:**
> You need to understand your firewall is called iptables.

Okay.  :)

> **bodhi.zazen said:**
> 
You were configuring iptables with Firestarter.


Yes, just as ufw / gufw can do.

> **bodhi.zazen said:**
> 
ufw / gufw will NOT configure NAT for you, you will need to either do it manually or use an alternate tool.

I would need to be sure about how to completely clear/flush iptables, so that I can start afresh, so to speak.

Thanks for the links; I will read up on it. IPCop has been suggested to me; it would certainly solve the firewall issues. That said, I would hope that Network manager would 'co-operate'.

Thanks,

Oygle

---

### Post by bodhi.zazen on 2011-02-28
NAT is trivial to set up, it is 4 lines of code.

IPCop will work, but is almost certainly over kill and no easier (IMO) then using iptables directly.

---

### Post by dmizer on 2011-02-28
> **oygle said:**
> Firestarter used to do the (whole) ICS side of things before, and from the [Internet Connection Sharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing") community page, it states that with network manager, to make sure that dnsmasq-base is installed. I can easily uninstall dnsmasq-base, if that is not required.
That community page is mostly dedicated to configuring connection sharing via the command line. It's tricky and you'll have to understand a lot about networking and IPtables. Using network-manager to configure your connection sharing will be much easier.

> **oygle said:**
> Also fhe Community [Firewall]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") guide has a section called "ufw Masquerading", which explains how to do the masquerading via UFW. This has been applied, and those 3 files have been modified. If that is definitely _NOT_ required, then I have backups of the files, so easy to restore.
This will work as long as you replaced the example interfaces and IP addresses with what you need to use on your own network. You cannot simply copy/paste what is on that page and have it work for you.

> **oygle said:**
> There does seem a lot of conflicting information about how to do ICS with UFW. Those last few modifications I had done, in 'desperation' I suppose, as after 4 days, following advice on forums, ICS was still not working.


You're reading a lot of information about a lot of ways to do the same thing. And, it seems as though you are confused as well as the people that are helping you.

From what I see, you simply want to configure one computer for internet connection sharing. Also, the computer you want to use for sharing internet has a WAN facing PPPoE connection, and as a result you need a firewall on your PPPoE interface.

You can use network-manager to handle the connection sharing part, and UFW to handle the necessary firewall on your ppp0 interface.

> **oygle said:**
> Seems there are some bugs in Network Manager.

[NetworkManager Internet Connection Sharing fails to route DNS]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/389006")

[NetworkManager connection sharing broken]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/725041")

Are you using Natty? If so, those bugs have been fixed and the fix has been released, so there should be a fix for this very soon (like within days), and your connection sharing should work fine via Network manager.

> **oygle said:**
> when using that method with NM, upon reboot, I had to set the IP address each time as follows

```

sudo ifconfig eth0 192.168.1.100

```

Surely there must be a method to set the IP address of eth0 , on the gateway permanently.

Once network manager has been fixed for connection sharing, you shouldn't have to do anything with IP addresses. It should take place automatically.

---

### Post by dmizer on 2011-02-28
> **oygle said:**
> The IP address I want for the gateway computer is 192.168.1.100

As I have 'sharing' enabled in Network manager, there is no provision there to specify the IP address for eth0. That is, cannot manually set it there.

Every time I boot up, the IP address changes to 

```

eth0      Link encap:Ethernet  HWaddr *******************  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: ********************* Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6025 (6.0 KB)
          Interrupt:17

```

and so I have to do this

```

$ sudo ifconfig eth0 192.168.1.100

```

to make it the correct IP address again.

Why is having an IP of 10.42.43.1 a problem? It works just as well as 192.168.100.

When using ICS, network manager automatically picks a free IP range for sharing. It should work fine without you having to do anything at all.

---

### Post by oygle on 2011-03-01
> **bodhi.zazen said:**
> NAT is trivial to set up, it is 4 lines of code.

I assume I need NAT the, for ICS ?

> **bodhi.zazen said:**
> IPCop will work, but is almost certainly over kill and no easier (IMO) then using iptables directly.

It may be an overkill, but I have used it before, and considering the problems I'm having using NM and ufw, I'm prepared to run a computer for IPCop, if necessary (or go back to windooze).

What I can't understand is that an outdated firewall like Firestarter (despite it's problems) had ICS going just fine. I change over to UFW / GUFW and now have to do ICS via NM, and it doesn't work. :(

---

### Post by oygle on 2011-03-01
> **dmizer said:**
> Using network-manager to configure your connection sharing will be much easier.

Yes, if it would work, it would be easier.

> **dmizer said:**
> 
This will work as long as you replaced the example interfaces and IP addresses with what you need to use on your own network. You cannot simply copy/paste what is on that page and have it work for you.

I followed the instructions, and used my own IP addresses.

> **dmizer said:**
> You're reading a lot of information about a lot of ways to do the same thing. And, it seems as though you are confused as well as the people that are helping you.

Possibly if Ubuntu worked 'out of the box' with ICS, I wouldn't have to read so much.

> **dmizer said:**
> From what I see, you simply want to configure one computer for internet connection sharing. Also, the computer you want to use for sharing internet has a WAN facing PPPoE connection, and as a result you need a firewall on your PPPoE interface.

That's correct. I need a firewall on the PPPoE interface, as it is just a USB dongle, I don't have it plugged into a router, but directly into the USB port of the computer.

> **dmizer said:**
> You can use network-manager to handle the connection sharing part, and UFW to handle the necessary firewall on your ppp0 interface.

Yes, I only wish I could do that.

> **dmizer said:**
> Are you using Natty? If so, those bugs have been fixed and the fix has been released, so there should be a fix for this very soon (like within days), and your connection sharing should work fine via Network manager.

I have just gone through an upgrade today, it had initial problems as I see other people had, had to do a few things, but now the gateway computer is on Natty.

btw, I didn't appreciate you closing the thread on [How to set a permanent IP address for eth0 ?]("http://ubuntuforums.org/showthread.php?t=1697359"), as I still do not know how to do it, and neither do other people. By closing the thread, it means people cannot answer my question.  :(

Despite that, I appreciate your help.  :)

Oygle

---

### Post by oygle on 2011-03-01
> **dmizer said:**
> Why is having an IP of 10.42.43.1 a problem? It works just as well as 192.168.100.

There are several computers (not just the gateway and one client). They are all setup in the hosts file, with IP addresses for various reasons. The IP 'range' on the LAN is 192.168.1.0/24 , so I see no reason to change that, simply because Network Manager cannot assign an IP address, or I do not know how to set it _permanently_ via the terminal.

---

### Post by oygle on 2011-03-01
Have talked to a friend who uses Debian, and he has advised that I get a 3G router, so then (I assume) the internet connection sharing will be done from the router, and not NM.

Also the router can do all the firewall side of things (NAT).

Oygle

---

### Post by dmizer on 2011-03-01
> **oygle said:**
> btw, I didn't appreciate you closing the thread on [How to set a permanent IP address for eth0 ?]("http://ubuntuforums.org/showthread.php?t=1697359"), as I still do not know how to do it, and neither do other people. By closing the thread, it means people cannot answer my question.  :(

Sorry, but your problem with being unable to assign an IP address in Network-manager is directly related to your attempt to configure ICS, so it's better to keep you question here. As you can see, I quoted and answered your question here, so the discussion can continue.

It looks like you will not be able to change the IP address range when attempting to share the connection via Nework-manager according to this the IP is hard coded: [http://www.mail-archive.com/networkmanager-list@gnome.org/msg13790.html](http://www.mail-archive.com/networkmanager-list@gnome.org/msg13790.html)

> **oygle said:**
> There are several computers (not just the gateway and one client). They are all setup in the hosts file, with IP addresses for various reasons. The IP 'range' on the LAN is 192.168.1.0/24 , so I see no reason to change that, simply because Network Manager cannot assign an IP address, or I do not know how to set it _permanently_ via the terminal.
If you simply must have static IP addresses and do not want to change the /etc/hosts files, then you'll be unable to use network-manager for connection sharing.

Because of this, you have a different problem now. The default network configuration tool (network-manager) interferes with the CLI configuration tools. So if you still want to do ICS and insist on using your own IP range, then you'll have to dump network-manager and essentially configure things manually.

Since this is the case, your Debian friend may be right in suggesting that your best solution will be to purchase a router.

---

### Post by oygle on 2011-03-02
> **dmizer said:**
> It looks like you will not be able to change the IP address range when attempting to share the connection via Nework-manager according to this the IP is hard coded: [http://www.mail-archive.com/networkmanager-list@gnome.org/msg13790.html](http://www.mail-archive.com/networkmanager-list@gnome.org/msg13790.html)

Yes. the reply was ..

> Nope, it's currently hardcoded for user-created "shared" networks.
Didn't really see a great need to change it at the time I did connection
sharing last year.  Mind sharing your use-case here?  I'm curious.

Dan

Pity that one persons "[COLOR="Red"]**Didn't really see a great need**[/COLOR]" makes Network manager _inflexible_ (still), some 17 months later. The use of NM by one person has dictated, _for all other users_, that when using NM and sharing, you can't have a static IP on the gateway. :rolleyes:

> **dmizer said:**
> If you simply must have static IP addresses and do not want to change the /etc/hosts files, then you'll be unable to use network-manager for connection sharing.

It's not a matter of changing the hosts file. It simply makes sense for computers on _any_ LAN to have static IP addresses. I have used Ubuntu for many years now, and have the same IP addresses for the same computers. Using IPCop or a router, you get to specify the IP's for each computer. However, Network manager **can't do it**, when sharing the network.

> **dmizer said:**
> Because of this, you have a different problem now. The default network configuration tool (network-manager) interferes with the CLI configuration tools. So if you still want to do ICS and insist on using your own IP range, then you'll have to dump network-manager and essentially configure things manually.

That perception is incorrect. It is not a matter of wanting to do ICS and insisting on specifying an IP range. That "functionality" was there when using Firestarter. That is ..

Firestarter (with ICS enabled) + NM = ICS and static IP's

and is NOT there with ufw / gufw. That is ..

ufw / gufw  + NM (with ICS enabled) **does NOT equal** ICS and static IP's

Firestarter, despite it's faults, and no longer being supported, integrated well with Network manager. Firestarter was able to do it with masquerading I assume, which raises the question, ..'Why can't ufw do the same ?' (Which is why I originally started the thread in the security forum).

> **dmizer said:**
> your Debian friend may be right in suggesting that your best solution will be to purchase a router.

Yes, it is the best workaround for the inadequacies of Network Manager. :lolflag:

Oygle

---

### Post by dmizer on 2011-03-02
> **oygle said:**
> ufw / gufw  + NM (with ICS enabled) **does NOT equal** ICS and static IP's

Well, part of the problem with that is that NM does ICS by itself. UFW is another way of doing ICS, they are not intertwined. I have never personally tried to configure ICS via UFW, but if you were to do so you would probably not involve NM in any way.

Let's see if we can get it working with UFW.

What is your /etc/ufw/before.rules?

---

### Post by oygle on 2011-03-03
> **dmizer said:**
> What is your /etc/ufw/before.rules?

I had modified that file, as per some instructions (will have to read through this thread and maybe others to see what it was ..

> 
#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

[B][COLOR="Magenta"]# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT[/COLOR][/B]

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines


# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT

# quickly process packets for which we already have a connection
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m state --state INVALID -j ufw-logging-deny
-A ufw-before-input -m state --state INVALID -j DROP

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local

# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP

# allow MULTICAST, be sure the MULTICAST line above is uncommented
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT


# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT


The part in **[COLOR="Magenta"]Magenta[/COLOR]** are the lines I added.

These are the files that were backed up prior to the changes

/etc/default/ufw.backup
/etc/ufw/before.rules.backup
/etc/ufw/sysctl.conf.backup

so, remove the suffix 'backup', and they are the files I modified, and are still modified. This was documented under [under the section ufw Masquerading - Firewall docs]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html")

I don't have dnsmasq or dnsmasq-base installed on the gateway though. (From memory Firestarter had ipmasq or some name like that installed, to make it 'work').

---

### Post by oygle on 2011-03-03
The eth0 was connecting and disconnecting all the time. In the syslogs, Network Manager was inserting into iptables, then some failure with eth0, and then NM deleted rules from iptables. This happened constantly, just like a loop.

So I stopped networking, restored those 3 files, restarted networking, and at least now, the gateway is not going crazy and filling up syslogs.

Have had a few updates of late, and possibly when I upgraded to 10.10  (Maverick Meerkat), it has some Network manager mods.

I did set the gateway to 10.42.43.1 on the client, but still no go.

Have ordered the router, but it would be nice to get this up and running, just for others who want to do it.

Oygle

---

