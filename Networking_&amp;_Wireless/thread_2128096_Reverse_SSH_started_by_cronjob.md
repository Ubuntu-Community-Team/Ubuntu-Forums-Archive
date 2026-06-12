---
title: "Reverse SSH started by cronjob"
date: 2013-03-22
forum: Networking &amp; Wireless
---

### Post by ontheair on 2013-03-22
Hello everybody,

I would like to create a reverse SSH on a remote machine and most things are working fine, there is just one last, little problem. Maybe you can give me a hint. Xubuntu 12.10 is used in this case.

For your information, the background story: I am going to donate some computers to a NGO project far away. The people there dont have much computer skills, so I have to get SSH connection to maintain and update the systems. Also I can not tell them to do port forwardings on their router due to the lack of skills. Teamviewer or other, bandwidth-hungry variants are not possible due to a slow internet connection at the NGO-side.

That's why I prepared the computers for reverse SSH. Almost everything is working fine:
I created keys and the NGO-computers are connecting without any interaction to my linux machine at home when *reversessh.sh* is executed, which holds this line and is executable:
```
ssh -i /path/to/secret/key -R 5000:localhost:22 UserOnMyHomeMachine@MyHomeMachine
```

At home on my machine I can access the NGO-machine by typing:
```
ssh -p 5000 UserAtNGO@localhost
```

So everything works well, BUT: I want the *reversessh.sh* on the NGO-machine to be started automatically by a cronjob every 30 Minutes (in case the connection gets lost). When I add it to crontab, the reversessh.sh is executed, the connection is established, the keys are shared and *then the connection is disconnected automatically*. And that's the problem.

So, how can I start the reverse SSH automatically on the remote machine by cronjob? Or maybe: How can I add a script, which is checking if the connection is established and just if disconnected, to connect again?

Again, thank you for any ideas and help!

---

### Post by jonobr on 2013-03-22
Hello

I reckon you need autossh (should be in the repos.

I searched "autossh reverse ssh" and found [http://akntechblog.wordpress.com/2010/09/11/autossh-for-persistent-reverse-ssh-tunnels/]("http://akntechblog.wordpress.com/2010/09/11/autossh-for-persistent-reverse-ssh-tunnels/") , I think that may be exactly what you need

---

### Post by Hadaka on 2013-03-22
Hi, read your post and decided to do some scripting
its crude,simple...and actually works..;)

```
hadaka@the-beach:~$ cat rssh_status
#!/bin/bash
echo "`ping -c5 192.168.1.4 > ping_test`" #my wlan0 ip - replace with your host ip

 case `grep "packets" ping_test | awk '{print$6}' | cut -c1` in
[0-15]) echo "$(date) All is well" >> daily_ssh.log;;
$NULL) echo "$(date) *Link down*" >> daily_ssh.log && echo "`ls -al`";;
 esac
########################################################
#case $NULL ..."`ls -al`" tested to insure "hands off" command worked.
#replace with your ssh command below....be aware of the ` ` backticks.

#ssh -i /path/to/secret/key -R 5000:localhost:22 UserOnMyHomeMachine@MyHomeMachine

# $ cat daily_ssh.log
# Fri Mar 22 21:09:04 EDT 2013 All is well     wlan0 up - ip test
# Fri Mar 22 21:10:46 EDT 2013 All is well
# Fri Mar 22 21:11:32 EDT 2013 *Link down*
# Fri Mar 22 21:12:05 EDT 2013 All is well
# Fri Mar 22 21:12:26 EDT 2013 All is well
# Fri Mar 22 21:13:04 EDT 2013 *Link down*     wlan0 down - ip test
# Fri Mar 22 21:13:44 EDT 2013 All is well
# Fri Mar 22 21:15:25 EDT 2013 *Link down*
# Fri Mar 22 21:15:53 EDT 2013 All is well
#Note you will most likely have to add PATH= at the top of the script
#Handy crontab links
# http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/

# http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work
 
```

---

### Post by ontheair on 2013-03-23
Thank you very much for your suggestions and ideas! I will try it later after work and tell you if it works ;-) Thank you!

---

### Post by ontheair on 2013-03-23
Hello, I tried your suggestions.

@Hadaka: In general your script works fine. But there is a basic problem: Which IP adress should I ping in my case? I can ping the WAN IP of my home machine, but there will be always an answer as the system is running 24/7 - no matter if the ssh connection is actually active or not. The script will always get an answer and never start the ssh connection. So, in my case it is not working, but for other purposes the script can be very useful!

@Jonobr: Thank you for suggesting autossh! I finally got everything working by:
- Installing autossh
- Putting the command in rc.local (with "autossh" instead of "ssh")
-> The connection is starting and autossh is checking every ten minutes if the connection is still alive.

First I failed on two things (maybe useful for others):
- The key for ssh authentification was stored in an encrypted directory and the system was not able to access the key on boot. So I had to relocate the key, of course.
- autossh was started *before* the network interface was coming up (and made autossh crashing completely). A simple "sleep 60" in rc.local did the trick.

Thank you very much for your kind help and have a nice weekend!

---

