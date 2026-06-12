---
title: "Count of connections"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by liranv on 2010-03-17
Hey All
 
1) I Would like to know how can i tell what is the count of tcp sessions currently active , also , i would like to know what kind of tcp sessions are they. for example , in windows there is a "established" session , Listening and close_wait sessions . 
 
I Just need to understand what command should i use (Netstat i know , but what syntax) so i can see all connections ?
 
2) I Need information regarding the Disks I/O . What command should i use to see the disk I/O ?
 
Thank you very much
 
Liran

---

### Post by gombadi on 2010-03-17
> 
1) I Would like to know how can i tell what is the count of tcp sessions currently active , also , i would like to know what kind of tcp sessions are they. for example , in windows there is a "established" session , Listening and close_wait sessions .

I Just need to understand what command should i use (Netstat i know , but what syntax) so i can see all connections ?


netstat -an will list all the active connections. You can then pipe that into other programs to provide output like -
```

human@server:~$ netstat -an | awk '/^tcp/ {print $NF}' | sort | uniq -c | sort -rn
   6937 ESTABLISHED
    360 TIME_WAIT
     17 FIN_WAIT1
     15 LISTEN
      5 SYN_SENT
      3 LAST_ACK
      1 SYN_RECV
      1 CLOSE_WAIT

```


> 
2) I Need information regarding the Disks I/O . What command should i use to see the disk I/O ?


Install the sysstat package and then run this command

```

iostat -xtk 2

```

Change the number at the end to change the number of seconds between output.

---

### Post by liranv on 2010-03-18
I Would really like to thank you for your Comment. it was a great help and it gives me exactly what i needed .
 
 I would like to ask another question please.
 
I Am using Munin , as a monitoring system. I have attached a print screen of one of the monitoring windows .It is the netstat command . can you tell me what is what there comparing the command itself in Ubuntu ?
 
Thank you for your help.

---

### Post by gombadi on 2010-03-18
> 
I Am using Munin , as a monitoring system. I have attached a print screen of one of the monitoring windows .It is the netstat command . can you tell me what is what there comparing the command itself in Ubuntu ?


It is showing that you have about 23,000 established connection (the other types are too small to show on the graph) - Does that match with the output of the commands above?
Pipe the basic netstat command through less to see what all the connections are.

---

