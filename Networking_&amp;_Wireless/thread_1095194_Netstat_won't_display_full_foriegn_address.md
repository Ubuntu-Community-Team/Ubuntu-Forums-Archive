---
title: "Netstat won't display full foriegn address"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by PatchMonster on 2009-03-13
I need to get the full foreign URL in a TCP connection, and netstat only displays an abridged version of it.

Example:
```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        1      1 PatchMonster.loca:44726 musicservices.myspa:www LAST_ACK   
tcp        0      0 PatchMonster.loca:44731 musicservices.myspa:www ESTABLISHED
tcp        1      1 PatchMonster.loca:44625 google.navigation.o:www LAST_ACK   
tcp        0      0 PatchMonster.loca:59033 a204-245-162-33.dep:www ESTABLISHED
tcp        1      1 PatchMonster.loca:46407 216.178.33.50:www       LAST_ACK   
tcp        0      0 PatchMonster.loca:44730 musicservices.myspa:www ESTABLISHED
tcp        0      0 PatchMonster.loca:44725 musicservices.myspa:www ESTABLISHED
tcp        1      1 PatchMonster.loca:56488 208.71.122.23:www       LAST_ACK   
tcp        0      0 PatchMonster.loca:44724 musicservices.myspa:www ESTABLISHED
tcp        1      1 PatchMonster.loca:56488 208.71.122.23:www       LAST_ACK   
tcp        0      0 PatchMonster.loca:44724 musicservices.myspa:www ESTABLISHED


```

I've read the manual on netstat, but I couldn't manage to find an option to display the full foreign URL.  Is there any other way you might suggest getting this URL?  Or is there something I missed in the man?

Thanks in advance :P

---

