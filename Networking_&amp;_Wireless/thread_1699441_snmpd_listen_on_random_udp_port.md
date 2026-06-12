---
title: "snmpd listen on random udp port"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by ploufplouf on 2011-03-03
hy \\:D/

I am looking for help to understand why my snmpd demon is listenning on a random udp port. 
I am using ubuntu server 10.10.

result of commands:

```

sudo netstat -lupn
Connexions Internet actives (seulement serveurs)
Proto Recv-Q Send-Q Adresse locale          Adresse distante        Etat       PID/Program name
udp        0      0 192.168.X.X:161        0.0.0.0:*                           13178/snmpd     
udp        0      0 127.0.0.1:161           0.0.0.0:*                           13178/snmpd     
udp        0      0 0.0.0.0:1194            0.0.0.0:*                           3297/openvpn    
udp        0      0 0.0.0.0:56121           0.0.0.0:*                           13178/snmpd 

```Then I restart snmpd 

```

sudo netstat -lupn
Connexions Internet actives (seulement serveurs)
Proto Recv-Q Send-Q Adresse locale          Adresse distante        Etat       PID/Program name
udp        0      0 192.168.X.X:161        0.0.0.0:*                           13398/snmpd     
udp        0      0 127.0.0.1:161           0.0.0.0:*                           13398/snmpd     
udp        0      0 0.0.0.0:1194            0.0.0.0:*                           3297/openvpn    
udp        0      0 0.0.0.0:53939           0.0.0.0:*                           13398/snmpd    

```I notice that I configured snmpv3. I think this behaviour is totally illogical. What is the usefulness for snmpd to listen on a random port ? 

Any ideas ?  is it normal ? Should I be worried about this ?

thanks in advance :-({|=

---

