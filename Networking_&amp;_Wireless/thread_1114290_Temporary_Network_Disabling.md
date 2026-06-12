---
title: "Temporary Network Disabling"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by jonathansizz on 2009-04-02
There's a program that blocks all internet access for a user-specified period of time, so people like me who have no self-control can get on with their work without being distracted:

[http://www.ibiblio.org/fred/freedom/](http://www.ibiblio.org/fred/freedom/)

Unfortunately it's only available for Macs. Does anyone know of any program with the same functionality that's available for Linux?

---

### Post by Dr Small on 2009-04-02
You would do better to learn and master self-control.

---

### Post by jonathansizz on 2009-04-03
Can anyone actually answer my question, please?

---

### Post by oobe-feisty on 2009-04-03
make a cronjob

sudo crontab -e 

example of cron entry 

```
#shutdown internet at 6:30 pm 
18 30 * * * ifconfig eth0 down

#turn internet on at 9:33 am
09 33 * * * ifconfig eth0 up

```


this a assumes you connect to the internet on your lan using device named eth0 it also assumes you have no other use for it like connecting to a network printer or shares.

if you do need to access you local network then it will be easy to make a script that just messes up your DNS info then restores it at a later time get back to me with the out put of ifconfig and your type of network connection and internet and i will make you up somthing

**OR**

if you dont have a particular time set in mind you can have a script handy to cut of your internet of a set amount of time 

```
#!/bin/bash
/etc/init.d/networking stop

sleep 10800

/etc/init.d/networking start

```

this would stop your network for 3 hours

you can save the above script as whatever name you want in /usr/local/bin

e.g type from console "sudo gedit /usr/local/bin/stopnet" then paste in the above code then save

then from console type sudo chmod a+x /usr/local/bin/stopnet now you can just type stopnet and your internet will be down for 3 hours


heh 

> **Dr Small said:**
> You would do better to learn and master self-control.

this is the second time you have posted today without answering a question or making a constuctive comment instead sharing your opinion which is not relevant to any solution 

when i need help with somthing the last thing i want is people saying why do you want to do that etc. all i want is an answer without explaining every unnecessary detail

---

### Post by jonathansizz on 2009-04-06
Thanks, oobe-feisty. Works well.

---

