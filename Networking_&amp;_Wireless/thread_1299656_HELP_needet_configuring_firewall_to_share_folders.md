---
title: "HELP needet configuring firewall to share folders"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by KONEY on 2009-10-24
Hi all!

I run UBUNTU and WINXP in two different rooms. They're networked thru a HAG and this works OK for sharing folder (samba is running etc). The problem is Ubuntu Firewall, if it's running it stops any connection from the other pc! If I stop it then I can access the shared folders from remote. I've configured the IP and port correctly as follow:

[IMG]http://img408.imageshack.us/img408/9408/screenshotfirestarterbe.png[/IMG]

WINXP is 29.244.120.179, Ubuntu .176 and HAG .0. Samba ports are opened

I tryed also opening ALL the ports and ALL the IPs for the domain but no luck!

Anyone can tell me what's wrong??:confused::confused:

---

### Post by uncle-c on 2009-10-24
On the Samba server side the following ports should be open :

[B]udp 137
udp 138
tcp 139
tcp 445[/B]

Looking at your screen shot I think you may have ***tcp 137-139*** open.

---

### Post by KONEY on 2009-10-24
doesn't 137-139 with the "-" means all ports in that range?

I may try putting them all separated from a space, anyway...

thanx

---

### Post by uncle-c on 2009-10-24
Yes but there is a distinct difference between  udp 137 and tcp 137. I'm not sure if your firewall is opening tcp 137-139 or udp 137-139.
What is the output of :

```

$ netstat -atnu

```

---

### Post by KONEY on 2009-10-24
AHH yes you're totally right! But I don't know how to open UDP ports...


```
koney@BEAST2-UBUNTU:~$ netstat -atnu
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:60460           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:56663         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:63863         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:58846         0.0.0.0:*               LISTEN     
tcp        0      0 29.244.120.178:48502    92.122.212.81:80        ESTABLISHED
tcp        0      0 29.244.120.178:52525    95.74.7.113:32337       ESTABLISHED
tcp        0    400 29.244.120.178:51800    93.148.230.77:55416     ESTABLISHED
tcp        0      0 29.244.120.178:44187    212.243.221.247:80      ESTABLISHED
tcp       38      0 29.244.120.178:57680    174.36.30.66:443        CLOSE_WAIT 
tcp        0      1 29.244.120.178:55385    79.240.106.247:40592    SYN_SENT   
tcp        0      0 29.244.120.178:38298    207.46.124.190:1863     CLOSE_WAIT 
tcp        0      0 29.244.120.178:48504    92.122.212.81:80        ESTABLISHED
tcp        0      0 29.244.120.178:51775    87.13.76.162:62834      TIME_WAIT  
tcp        0      0 29.244.120.178:57258    82.50.114.94:22083      TIME_WAIT  
tcp        0      0 29.244.120.178:48505    92.122.212.81:80        ESTABLISHED
tcp        0      0 29.244.120.178:52500    212.243.221.246:80      ESTABLISHED
tcp        0      0 29.244.120.178:47592    69.63.181.12:80         ESTABLISHED
tcp        0      0 29.244.120.178:60225    212.243.152.114:80      ESTABLISHED
tcp        0      1 29.244.120.178:53890    87.6.47.82:41441        SYN_SENT   
tcp        0      0 29.244.120.178:43921    95.74.230.15:42091      ESTABLISHED
tcp        0      0 29.244.120.178:44185    212.243.221.247:80      ESTABLISHED
tcp        0      0 29.244.120.178:47995    93.147.48.147:16598     ESTABLISHED
tcp        0      0 29.244.120.178:52498    212.243.221.246:80      ESTABLISHED
tcp        0      0 29.244.120.178:46829    87.7.16.206:56336       TIME_WAIT  
tcp        0   9958 29.244.120.178:58369    85.129.165.230:45682    ESTABLISHED
tcp        0      0 29.244.120.178:39033    208.43.202.32:80        ESTABLISHED
tcp        0      0 29.244.120.178:60085    79.37.196.157:48466     ESTABLISHED
tcp        0      0 29.244.120.178:47382    91.189.94.12:80         ESTABLISHED
tcp        0      0 29.244.120.178:42192    151.57.249.107:49400    ESTABLISHED
tcp        0      0 29.244.120.178:48501    92.122.212.81:80        ESTABLISHED
tcp        0      0 29.244.120.178:60267    82.52.155.114:52436     ESTABLISHED
tcp       38      0 29.244.120.178:54897    174.36.30.67:443        CLOSE_WAIT 
tcp        0      0 29.244.120.178:48503    92.122.212.81:80        ESTABLISHED
tcp       38      0 29.244.120.178:59331    75.101.131.0:443        CLOSE_WAIT 
tcp        0      0 29.244.120.178:41277    87.19.113.153:30578     ESTABLISHED
tcp        0      0 29.244.120.178:45360    79.117.212.183:11729    ESTABLISHED
tcp        0      0 29.244.120.178:55911    79.18.23.68:29847       ESTABLISHED
tcp        0      0 29.244.120.178:52502    212.243.221.246:80      ESTABLISHED
tcp        0      0 29.244.120.178:54132    193.206.158.232:37411   TIME_WAIT  
tcp        0      0 29.244.120.178:36098    79.2.32.242:6881        ESTABLISHED
tcp        0      0 29.244.120.178:57815    74.125.39.101:80        ESTABLISHED
tcp        0      0 29.244.120.178:36464    64.4.34.52:1863         ESTABLISHED
tcp        0      0 29.244.120.178:42013    87.0.101.119:59947      ESTABLISHED
tcp6       0      0 :::139                  :::*                    LISTEN     
tcp6       0      0 :::60460                :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::445                  :::*                    LISTEN     
udp        0      0 29.244.120.178:137      0.0.0.0:*                          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          
udp        0      0 29.244.120.178:138      0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          
udp        0      0 29.244.120.178:46614    0.0.0.0:*                          
udp        0      0 0.0.0.0:60460           0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:45259           0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:6771            0.0.0.0:*                          
udp        0      0 0.0.0.0:35959           0.0.0.0:*                          
udp6       0      0 :::60460                :::*                               

```

Hey I didn't know this command! very useful :)

---

### Post by uncle-c on 2009-10-24
Looks as if you have all the relevant ports open. However, something is of concern is the **tcp6** in your port 139 and 445 line. I am no expert but it could be an Internet Protocol Version 6 ( IPV6 ) conflict of some sort and you may have to do some reconfiguring of your Samba software. There is another Internet Protocol Version ( 4) and this maybe the correct version that the software supports. Perhaps a more learned person than me could shed more light ! ?

EDIT : I HAVE JUST CHECKED YOUR FIREWALL SCREEN SHOT, YOU SHOULD CHANGE [COLOR="Red"]**29.244.120.179**[/COLOR] TO [COLOR="DarkSlateBlue"]**29.244.120.178**[/COLOR]

---

### Post by carnagex420x on 2009-10-24
```
ufw allow from xxx.xxx.xxx.0/24 to any app Samba
```

This will allow Samba to work with all the PCs in your subnet. NOTE you need to change /24 to the appropriate number if you have more than 1 subnet.

137/udp
138/udp
139/tcp
445/tcp

---

