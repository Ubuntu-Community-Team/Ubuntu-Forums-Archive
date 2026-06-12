---
title: "Firewall Ports for smb printer sharing"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by llawwehttam on 2010-02-06
In my firewall I have these ports open:

21
143
110
25
631
2049
23
139
138
137
445

I thought that the bottom 4 were for smb printer sharing but with the firewall enabled my print jobs still don't leave my laptop. It works fine when I disable the firewall. Are there any other ports I should be adding?

---

### Post by llawwehttam on 2010-02-06
I have just noticed when I try to print I get the message 
"could not connect to cifs printer, will retry in 60 seconds"
when the firewall is up.

I have added ports 135 and 136 to the list but still no joy.

EDIT: with the firewall up I cannot browse to the windows share with this problem is fixed if I enable port 53960. (I have no idea why)
I'm guessing I just need to open another port.

---

### Post by CharlesA on 2010-02-06
Might try disabling the firewall and running something like nmap on the machine to see what ports are open when the firewall is disabled.

That might give some clues.

---

### Post by llawwehttam on 2010-02-06
Is there a simpler way to show open ports?
I can't stand nmap even though zenmap is quite nice.

---

### Post by CharlesA on 2010-02-06
Could also try netstat -nap

---

### Post by llawwehttam on 2010-02-06
> **CharlesA said:**
> Could also try netstat -nap

That looks great but I get results into the 10000s so it cuts off. Any ideas how to cut it down a bit, grep maybe?

---

### Post by CharlesA on 2010-02-06
Could try using grep, but I'm not sure what you would search for.

Maybe try "netstat -vatn" ?

That only displays the ports that are open when I ran it on my server.

---

### Post by llawwehttam on 2010-02-06
-vatn worked great:

```
llawwehttam@Joe-Pineapples:~$ netstat -vatn
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.21:52049      205.188.159.114:143     ESTABLISHED
tcp        0      0 192.168.1.21:45905      205.188.159.119:143     ESTABLISHED
tcp        0      0 127.0.1.1:139           127.0.1.1:41788         ESTABLISHED
tcp       64      0 127.0.1.1:41788         127.0.1.1:139           ESTABLISHED
tcp        0      0 127.0.1.1:139           127.0.1.1:41755         ESTABLISHED
tcp        8      0 127.0.1.1:41755         127.0.1.1:139           ESTABLISHED
tcp        0      0 192.168.1.21:139        192.168.1.21:49796      ESTABLISHED
tcp        8      0 192.168.1.21:49796      192.168.1.21:139        ESTABLISHED
tcp        0      0 192.168.1.21:34884      66.102.13.101:80        ESTABLISHED
tcp        0      0 192.168.1.21:60416      192.168.1.3:139         ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
llawwehttam@Joe-Pineapples:~$ 

```

so I should enable all listed ports?

looks like I need to add
49796
41755
41788

---

### Post by CharlesA on 2010-02-06
What's the IP of the machine?

If you can, close all browser windows and then run netstat again, that should clear some enties.

---

### Post by llawwehttam on 2010-02-06
With browser windows closed:

```
llawwehttam@Joe-Pineapples:~$ netstat -vatn
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.21:52049      205.188.159.114:143     ESTABLISHED
tcp        0      0 192.168.1.21:45905      205.188.159.119:143     ESTABLISHED
tcp        0      0 127.0.1.1:139           127.0.1.1:41788         ESTABLISHED
tcp       68      0 127.0.1.1:41788         127.0.1.1:139           ESTABLISHED
tcp        0      0 127.0.1.1:139           127.0.1.1:41755         ESTABLISHED
tcp       16      0 127.0.1.1:41755         127.0.1.1:139           ESTABLISHED
tcp        0      0 192.168.1.21:139        192.168.1.21:49796      ESTABLISHED
tcp       16      0 192.168.1.21:49796      192.168.1.21:139        ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN 
```so pretty much the same.

My IP is 192.168.1.21

---

### Post by llawwehttam on 2010-02-06
Just a little update. On 'allow' in the firewall I can print. On reject of deny I can't so It must be an incoming connection.
Any ideas?

---

### Post by CharlesA on 2010-02-06
> **llawwehttam said:**
> With browser windows closed:

```
llawwehttam@Joe-Pineapples:~$ netstat -vatn
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
**tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN     **
tcp        0      0 0.0.0.0:22              [COLOR="Green"]0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631    [/COLOR]       [COLOR="Red"]0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN    [/COLOR] 
tcp        0      0 192.168.1.21:52049      205.188.159.114:143     ESTABLISHED
tcp        0      0 192.168.1.21:45905      205.188.159.119:143     ESTABLISHED
[COLOR="Red"]tcp        0      0 127.0.1.1:139           127.0.1.1:41788         ESTABLISHED
tcp       68      0 127.0.1.1:41788         127.0.1.1:139           ESTABLISHED
tcp        0      0 127.0.1.1:139           127.0.1.1:41755         ESTABLISHED
tcp       16      0 127.0.1.1:41755         127.0.1.1:139           ESTABLISHED
tcp        0      0 192.168.1.21:139        192.168.1.21:49796      ESTABLISHED
tcp       16      0 192.168.1.21:49796      192.168.1.21:139        ESTABLISHED[/COLOR]
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN 
```

so pretty much the same.

My IP is 192.168.1.21

Red ones are File Sharing: Port 139 and 445.
Green is CUPS: Port 631.

I'm not sure what the other ones are, especially the one in bold.

You could try adding this rule to iptables:

iptables -A INPUT -i lo -j ACCEPT 

To see if it'll print with the firewall enabled.

---

### Post by llawwehttam on 2010-02-06
Added that to iptables and still no joy.

Just for more info here are my firewall exceptions:

```
21
143
110
25
631
2049
23
139
138
137
445
135
136
53960
49796
41755
41788
7634
52049
45905
34884
60416
43751
46131
36759
```I know long list.....

EDIT: I have to go out for 30 mins so If anybody has any ideas I won't be able to reply till I get back.

---

### Post by CharlesA on 2010-02-06
I am pretty much out of ideas. Is the printer on a remote machine, or is it attached to the local machine?

---

### Post by llawwehttam on 2010-02-06
The printer is attached to a windows xp computer which is on the same router as my ubuntu machine. I have enabled sharing of it from the windows end and can connect to it fine when the firewall is down. Is only when the ubuntu firewall is up that I have problems.

Bit weird really.

EDIT: now if I browse to the computer the printer is attached to in the file browser (with the firewall enabled) I get the error 'unable to mount location' and 'failed to retrieve share list from server'.
Its fine with the firewall disabled.

I have had this before on another machine but simply adding a port to the exceptions solved it that time.

Any ideas?

EDIT: restarted the ufw service and now I can browse to the share again but still can't print. Bit strange.....

---

### Post by pirateghost on 2010-02-06
> **CharlesA said:**
> Red ones are File Sharing: Port 139 and 445.
Green is CUPS: Port 631.

I'm not sure what the other ones are, especially the one in bold.

You could try adding this rule to iptables:

iptables -A INPUT -i lo -j ACCEPT 

To see if it'll print with the firewall enabled.
7634 is hddtemp

---

### Post by llawwehttam on 2010-02-06
> **pirateghost said:**
> 7634 is hddtemp

Thanks. I do have conky running with hddtemp and lmsensors.

---

### Post by CharlesA on 2010-02-06
Wonder what the deal is.

EDIT: Thanks for the info about port 7634.

---

### Post by llawwehttam on 2010-02-06
Well for now I will be setting my laptop firewall to 'allow' when in the house and 'deny' when out.

I would like to get it fixed though.

---

### Post by llawwehttam on 2010-02-08
This is just wierd, I think it may be a firewall bug but I'm not sure.
Any other firewalls I could use? ( I hate firestarter and am currently using gufw)

---

### Post by grisedale on 2010-02-18
I sympathise, having recently struggled with this myself.

The problem is that the firewall requirements in this context are quite different for servers and clients, and the advice generally given is for servers. You, like me, are trying to print to a remote printer from a client.

When your client PC initiates an SMB exchange with the server, it randomly selects a high number port, in the range 1024 to 65535, on which to receive responses. The client doesn't receive on ports 137, 138 etc at all as far as I can see. This means that for UDP exchanges you need to have the high numbered ports open.

What I find on my setup (Karmic to Windows 7 print server on a private network) is that to define a new remote shared printer in Ubuntu I need to do
ufw allow proto udp from 192.168.1.0/24 to any port 1024:65535
or the equivalent in gufw. This is because the exchanges for setting up a printer share use UDP.

Subsequently I find I can delete the firewall rule and close the ports, and still happily use the printer from the Ubuntu system. I believe that this is because printing uses TCP (to 445 on the server), and the responses, again to a high-numbered ports on the client, are allowed through by the firewall since they do not constitute new connections.

---

### Post by snobskidoo on 2011-11-01
Please ignore me!

---

