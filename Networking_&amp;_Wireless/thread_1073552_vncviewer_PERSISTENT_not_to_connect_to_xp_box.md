---
title: "vncviewer PERSISTENT not to connect to xp box"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Claus7 on 2009-02-18
Hello,

I feel completely disappointed to find out that via kde someone with krdc program was able to connect to a windows xp machine almost in less than 1', while me troubling more than 2 days to connect via vncviewer without success.

The windows xp machine was in a different suburb of my city, and I'm saying that because I was able to connect with vncviewer in the same building to an xp box with my ubuntu machine.

I do not try to find out a solution to this. Just to inform people that if vncviewer fails, then try krdc.

Both xp machines had tightvnc program up and running.

Regards!

---

### Post by Excedio on 2009-02-18
I am able to connect to my work computer (XP) using my personal computer (Ubuntu).

type in this:

```
vncviewer ipaddress::port
```

Make sure that you have two colons ::

Note: This is a picture of me using my work station and using VNC to get into my Ubuntu box at home AND THEN using the Ubuntu box to get into the XP work station in my lab.

[IMG]http://i71.photobucket.com/albums/i136/Excedio/vnc.png[/IMG]

---

### Post by Claus7 on 2009-02-18
Hello,

so I didn't put all the story...

First thing first :thank's for the reply.

Now, I was able to connect to an xp box.
How? It depends on the number of port someone chooses:
```
vncviewer ipaddress:port
```
```
vncviewer ipaddress::port
```

So sometimes the two columns where needed, sometimes not. And all these on a computer close to the ubuntu box I had. I do not know whether this made any difference or not.

On the machine that was far away I was getting most of the time :
connection reset by peer (104)
after the message :
cconn :connected on server ... in port ...

If I typed:
vncviewer ipaddress:1 

then it prompted for password, yet to no avail. No matter what, the connection couldn't be established. At least setting the display number (here 1), it allowed me to type a password, yet I couln't set the port. It said that it connected to port 5901. Also I was changing the ports from tightvnc in order to comply with what vncviewer seemed to want. 

I tried to see whether I was able to set both display (what this setting means?) and port via command line to no avail.

So krdc I think that is a good choise. It doesn't even need tightvnc. 

Regards!

---

