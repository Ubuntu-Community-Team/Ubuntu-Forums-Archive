---
title: "Stdout ifconfig conversion to JSON?"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-01-31
I'm trying to find a way to pipe the output of ifconfig to a json file.  I can use: 
     ifconfig > statsfile.txt

which will give me the text like so.

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:320172 (320.1 KB)  TX bytes:320172 (320.1 KB)

Essentially I want the RX and TX but may decide to use the packets as well.  Doing it this way (with Json) just allows me to grab things extremely easy and quickly without having to use regex.  So is there anything that would convert this to json?  I had a python script that did something like pretty print to json output but its at the office and I'm at home.  Thanks for the help.

---

### Post by jonobr on 2013-01-31
Not sure about Json


but if you redirect to output and then use a simple grep, would that not work?


cat testfile | grep 'RX\|TX'


```
         RX packets:9641181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2630257 errors:0 dropped:0 overruns:0 carrier:0
          RX bytes:1268282716 (1.2 GB)  TX bytes:257370470 (257.3 MB)
          RX packets:44608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44608 errors:0 dropped:0 overruns:0 carrier:0
          RX bytes:16620995 (16.6 MB)  TX bytes:
```


Note that gets all RX tx 
if you want bytes

cat testfile | grep 'RX bytes\|TX bytes'

```

          RX bytes:1268282716 (1.2 GB)  TX bytes:257370470 (257.3 MB)
          RX bytes:16620995 (16.6 MB)  TX bytes:16620995 (16.6 MB)

```


Note that this has two sets of results as I did not specify the eth0 , so I am getting eth0 and lo

---

### Post by jonobr on 2013-01-31
Is should have stated that the \ in the grep is a logical OR function

---

### Post by psyllex on 2013-02-01
> **jonobr said:**
> Not sure about Json


but if you redirect to output and then use a simple grep, would that not work?


cat testfile | grep 'RX\|TX'


```
         RX packets:9641181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2630257 errors:0 dropped:0 overruns:0 carrier:0
          RX bytes:1268282716 (1.2 GB)  TX bytes:257370470 (257.3 MB)
          RX packets:44608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44608 errors:0 dropped:0 overruns:0 carrier:0
          RX bytes:16620995 (16.6 MB)  TX bytes:
```


Note that gets all RX tx 
if you want bytes

cat testfile | grep 'RX bytes\|TX bytes'

```

          RX bytes:1268282716 (1.2 GB)  TX bytes:257370470 (257.3 MB)
          RX bytes:16620995 (16.6 MB)  TX bytes:16620995 (16.6 MB)

```


Note that this has two sets of results as I did not specify the eth0 , so I am getting eth0 and lo

Yeah that works...I used:

       cat testfile | grep 'RX\|TX' > logfile2

Is there a way to specify eth0?  As that's the only one I need in this case.  

And where does a person learn all this?  Just go buy a bash book or is there a secret place to get all this downloaded into my head like in the Matrix?

---

### Post by steeldriver on 2013-02-01
You can specify a particular interface on the ifconfig command line, i.e

```
ifconfig eth0
```Alternatively, if you already have the output in a text file and need to parse out the eth0 records you could do a little awk script,

```
ifconfig | awk 'BEGIN {RS=""} ; $1 ~ /eth0/ { print; }'
```

You could do the Tx/Rx match in awk as well

---

