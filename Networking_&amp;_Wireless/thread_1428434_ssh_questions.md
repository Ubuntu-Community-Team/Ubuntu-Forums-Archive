---
title: "ssh questions"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by jeezoflip on 2010-03-12
Hey. I need help with ssh. 

I run a counter-strike server on my ubuntu box. When I'm home, I can go downstairs and manually restart the server if needed. However, when I'm at college, I cannot. If I needed to start, or restart the server remotely, I would ssh into my box at home and enter the commands needed to start the server. However, if I close the ssh session, the server stops as well. How can I keep the server running, even after I close my ssh session whether it's through putty on windows, or terminal on mac? 

thank you.

---

### Post by koszta on 2010-03-12
the problem is (as you can guess) that the process of server is tied to its parental process (that being the remote shell login) and when the shell dies it takes all the child processes with it. The solution is nohup command
see 
```
man nohup
```
e.g. nohup script.sh

---

### Post by jeezoflip on 2010-03-12
> **koszta said:**
> the problem is (as you can guess) that the process of server is tied to its parental process (that being the remote shell login) and when the shell dies it takes all the child processes with it. The solution is nohup command
see 
```
man nohup
```e.g. nohup script.sh

I tried it out. I dont know if I'm doing something wrong or if it just didn't work. 

I have a script on my server desktop called cs_server.sh. 

I log in ssh and do...

```
cd /home/michael/Desktop
nohup ./cs_server.sh
 
```the output I get is...

```
nohup: ignoring input and appending output to 'nohup.out' 
```Then a log shows up on my server's desktop with all the output the command would get, however, the server never starts, and ssh just hangs on the command.

---

### Post by cjhabs on 2010-03-12
> **jeezoflip said:**
> I tried it out. I dont know if I'm doing something wrong or if it just didn't work. 

I have a script on my server desktop called cs_server.sh. 

I log in ssh and do...

```
cd /home/michael/Desktop
nohup ./cs_server.sh
 
```the output I get is...

```
nohup: ignoring input and appending output to 'nohup.out' 
```Then a log shows up on my server's desktop with all the output the command would get, however, the server never starts, and ssh just hangs on the command.

Off the top of my head, how about running the script in the background?
./cs_server.sh &

---

### Post by jeezoflip on 2010-03-12
> **cjhabs said:**
> Off the top of my head, how about running the script in the background?
./cs_server.sh &

well will that keep the script running, even after i close the ssh session? i'm sorry, i only ask because i'm not near that computer right now.

---

### Post by cjhabs on 2010-03-13
> **jeezoflip said:**
> well will that keep the script running, even after i close the ssh session? i'm sorry, i only ask because i'm not near that computer right now.

I am not able to test it at the moment, sorry.

---

### Post by jeezoflip on 2010-03-16
> **cjhabs said:**
> I am not able to test it at the moment, sorry.

mmm, jus tried that. didn't work :(.

---

