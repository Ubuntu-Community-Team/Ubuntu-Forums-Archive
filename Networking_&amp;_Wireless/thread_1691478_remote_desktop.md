---
title: "remote desktop"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by adver on 2011-02-19
I can't get remote desktop to work.  The computer I am trying to access is on the same local network and I have the top 2 buttons checked under remote desktop in ubuntu 10.10 32bit.  I don't have password checked.  When I try to access the computer from another computer on my network running the 64bit version of 10.10 with username@ip address of server it asks for a password anyway.  I've tried the password of both computers and it doesn't work. I just get a "permission denied".  Not really sure how this works so I also tried the username of both computers with no luck. 

I also added port 22 to port forwarding on my router.  I don't think I have firewall running on either computer

---

### Post by pressko on 2011-02-20
Hi guys, 

I have kinda the same problem 2.

When I enable: 
1.Allow other users to view your desktop
2.Allow other users to control your desktop 

I get : Your desktop is only reachable over the local network. Others can access your computer using the address localhost.

Then i tried 3. Configure network automatically to accept connections. ( yes i have UPnP enabled on my router D-Link 300)
Also i opened router's  forwarding  ports to my pc : 5900 and 22 ... and no firewall on my Ubuntu 10.10 :/
But my pc is still reachable only over the local network ... while i'm able to connect to my fr's pc.

pls Help ? 
10x in advance.

---

### Post by Miguel Tavares on 2011-02-20
Hi guys,
un-check the uPnP box and try again.
Also output from the following:
1 - dpkg-query -l vino
2 -  netstat -antp|grep 5900|awk -F" " '{print $7}'|awk -F"/" '{print $1}'|tail -1|while read line; do ps -ef|grep $line; done
3 - uname -a
4 - how many hops to the remote machine?

Kindest Regards
Miguel Tavares

---

### Post by pressko on 2011-02-20
> **Miguel Tavares said:**
> Hi guys,
un-check the uPnP box and try again.
Also output from the following:
1 - dpkg-query -l vino
2 -  netstat -antp|grep 5900|awk -F" " '{print $7}'|awk -F"/" '{print $1}'|tail -1|while read line; do ps -ef|grep $line; done
3 - uname -a
4 - how many hops to the remote machine?

Kindest Regards
Miguel Tavares

Hi ,

Unmarking UPnP on the router didn't help...

when i use  : dpkg-query -l vino 
I got : 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  vino           2.32.0-0ubuntu VNC server for GNOME

The other steps u wrote about are unclear for me ... what should i do ? 
For that how many hops to the remote machine also unclear ... i have a router and a PC , so it makes one hop to the WLAN.


Best regards,
Presian

---

### Post by Miguel Tavares on 2011-02-20
Ok can you execute the below cmd's with the user that you want to use the remote desktop?

1 - cd ~; find ./ -exec grep -il "vino" {} \;|grep xsession|while read line; do grep vino $line; done
This will cd to your home dir and find vino recursively within your home dir files and based on its output it greps "vino" from the files that contained some log information regarding the vino server eg: xsession...

2 -  netstat -antp|grep 5900|awk -F" " '{print $7}'|awk -F"/" '{print $1}'|tail -1|while read line; do ps -ef|grep $line; done
This will use netstat to check a tcp connection on port 5900 and its PID and exclude all the columns except for the 7th and using a separator "/" echos the PID from the service that the socket is using and while realing the PID do a ps -ef|grep PID. So basically, checking if vino server is up and running with its daemon.

After that could you run this one?

3 - netstat -antp|grep 5900|awk -F" " '{print $7}'|awk -F"/" '{print $1}'|tail -1|while read line; do ps -ef|grep $line; done|grep -v grep|awk -F" " '{print $3}'|xargs sudo strace -p

This will Attach the process to be traced, now with the attached process in the stdout please rerun the remote desktop connection and when finished, CTRL+C and send us the logs.

Thanks 

Miguel Tavares

---

### Post by pressko on 2011-02-20
> **Miguel Tavares said:**
> Ok can you execute the below cmd's with the user that you want to use the remote desktop?

1 - cd ~; find ./ -exec grep -il "vino" {} \;|grep xsession|while read line; do grep vino $line; done


sry but i'm a ******* noob ... just to copy and paste into terminal right ?


if u mean that i got :

presian@presian-Aspire-6920:~$ cd ~; find ./ -exec grep -il "vino" {} \;|grep xsession|while read line; do grep vino $line; done

grep: ./.mozilla/firefox/ww71hrgt.default/lock: No such file or directory

---

### Post by Miguel Tavares on 2011-02-20
Hi thats ok.
also the output from the cmd was normal but was expecting to find the xsession around there and some failed error within the log....
so can u go to your home dir and execute the following command in the terminal 

1 - cd ~; ls -la|grep .xsession-errors
2 - grep vino .xsession*

and get us the output from these 2 commands please.

Alternatively to the absence of vino-server logs, we can do the following:

3- Stop all vino-server services as root user:
     $killall vino-server

4 - Check if they are down:
root@ubuntu:/# nmap localhost|grep 5900|wc -l
0

 5- Go to root home and create a script for the vino-server logs upon startup as follows:

root@ubuntu:/# vi vino-server.sh

#!/bin/sh
killall vino-server
exec /usr/lib/vino/vino-server > $HOME/vino.log 2>&1

6 - Permissions to execute:
root@ubuntu:/# chmod 755 vino-server.sh 

7- Run the Script and %bg it:
root@ubuntu:/# ./vino-server.sh &
[1] 16355

8- Check that the file exists:
root@ubuntu:~# ls -la|grep vino
-rw-r--r--  1 root root    422 2011-02-20 07:58 vino.log

9- Check the created log in real time while trying to connect to the remote machine. This will provide us a mean to Root Cause your issue in a more logical approach. So after trying to connect attach the log to your reply.
 
root@ubuntu:~# tail -f vino.log 
20/02/2011 07:58:11 Autoprobing TCP port in (all) network interface
20/02/2011 07:58:11 Listening IPv6://[::]:5900
20/02/2011 07:58:11 Listening IPv4://0.0.0.0:5900
20/02/2011 07:58:11 Autoprobing selected port 5900
20/02/2011 07:58:11 Advertising security type: 'TLS' (18)
20/02/2011 07:58:11 Advertising authentication type: 'No Authentication' (1)
20/02/2011 07:58:11 Advertising security type: 'No Authentication' (1)


Regards
Miguel Tavares

---

### Post by pressko on 2011-02-20
> **Miguel Tavares said:**
> Hi thats ok.
also the output from the cmd was normal but was expecting to find the xsession around there and some failed error within the log....
so can u go to your home dir and execute the following command in the terminal 

1 - cd ~; ls -la|grep .xsession-errors
2 - grep vino .xsession*

and get us the output from these 2 commands please

Regards
Miguel Tavares


Hi ,


resian@presian-Aspire-6920:/$ cd ~; ls -la|grep .xsession-errors
-rw-------  1 presian presian    8250 2011-02-20 09:48 .xsession-errors
-rw-------  1 presian presian    3507 2011-02-20 09:43 .xsession-errors.old

presian@presian-Aspire-6920:/$ grep vino .xsession*
grep: .xsession*: No such file or directory


also: 

presian@presian-Aspire-6920:~$ nc -zv localhost 5900
nc: connect to localhost port 5900 (tcp) failed: Connection refused
nc: connect to localhost port 5900 (tcp) failed: Connection refused


finnaly it's running ... i don't know how i did it but it's OK now :)) 
10x to [Miguel Tavares]("http://ubuntuforums.org/member.php?u=1247565")

---

### Post by Miguel Tavares on 2011-02-20
Well cool to see that you managed it...
Also, my approach to the absence of vino-server logs, you can do the following for yours future reference on wtf is going on with vino....

1- Stop all vino-server services as root user:
     $killall vino-server

2- Check if they are down:
root@ubuntu:/# nmap localhost|grep 5900|wc -l
0

 3- Go to root home and create a script for the vino-server logs upon startup as follows:

root@ubuntu:/# vi vino-server.sh

#!/bin/sh
killall vino-server
exec /usr/lib/vino/vino-server > $HOME/vino.log 2>&1

4- Permissions to execute:
root@ubuntu:/# chmod 755 vino-server.sh 

5- Run the Script and %bg it:
root@ubuntu:/# ./vino-server.sh &
[1] 16355

6- Check that the file exists:
root@ubuntu:~# ls -la|grep vino
-rw-r--r--  1 root root    422 2011-02-20 07:58 vino.log

7- Check the created log in real time. This will provide us a mean to  Root Cause your issue in a  more logical approach since by default  vino-server doesnt have any logs.
 
root@ubuntu:~# tail -f vino.log 
20/02/2011 07:58:11 Autoprobing TCP port in (all) network interface
20/02/2011 07:58:11 Listening IPv6://[::]:5900
20/02/2011 07:58:11 Listening IPv4://0.0.0.0:5900
20/02/2011 07:58:11 Autoprobing selected port 5900
20/02/2011 07:58:11 Advertising security type: 'TLS' (1:cool:
20/02/2011 07:58:11 Advertising authentication type: 'No Authentication' (1)
20/02/2011 07:58:11 Advertising security type: 'No Authentication' (1)

Now you'll be able to see who gets in or out :grin: 

Quote:
                                                 [COLOR=#cc0000]**How to run commands in a Terminal: **[/COLOR]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter*   again to run the command. Please do not run commands without knowing   what they do. If you do not understand what a command does, ask for   explanations.                      

Kindest Regards

Miguel Tavares
^_^

---

### Post by adver on 2011-02-20
the following is with UPnP disabled on my router and only the top 2 boxes checked in remote desktop

1.  Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  vino           2.32.0-0ubuntu VNC server for GNOME

2.  (Not all processes could be identified, non-owned process info    I tried this with sudo aswell and nothing happened
 will not be shown, you would have to be root to see it all.)

3.  Linux azazel-p6720f 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

4.  Not sure if this is what you mean but, in between the two machines is the router only... so 2 hops I guess one to from the machine to the router, and from the router to the other machine.

---

### Post by pressko on 2011-02-20
> **Miguel Tavares said:**
> Well cool to see that you managed it...
Also, my approach to the absence of vino-server logs, you can do the following for yours future reference on wtf is going on with vino....

1- Stop all vino-server services as root user:
     $killall vino-server

2- Check if they are down:
root@ubuntu:/# nmap localhost|grep 5900|wc -l
0

 3- Go to root home and create a script for the vino-server logs upon startup as follows:

root@ubuntu:/# vi vino-server.sh

#!/bin/sh
killall vino-server
exec /usr/lib/vino/vino-server > $HOME/vino.log 2>&1

4- Permissions to execute:
root@ubuntu:/# chmod 755 vino-server.sh 

5- Run the Script and %bg it:
root@ubuntu:/# ./vino-server.sh &
[1] 16355

6- Check that the file exists:
root@ubuntu:~# ls -la|grep vino
-rw-r--r--  1 root root    422 2011-02-20 07:58 vino.log

7- Check the created log in real time. This will provide us a mean to  Root Cause your issue in a  more logical approach since by default  vino-server doesnt have any logs.
 
root@ubuntu:~# tail -f vino.log 
20/02/2011 07:58:11 Autoprobing TCP port in (all) network interface
20/02/2011 07:58:11 Listening IPv6://[::]:5900
20/02/2011 07:58:11 Listening IPv4://0.0.0.0:5900
20/02/2011 07:58:11 Autoprobing selected port 5900
20/02/2011 07:58:11 Advertising security type: 'TLS' (1:cool:
20/02/2011 07:58:11 Advertising authentication type: 'No Authentication' (1)
20/02/2011 07:58:11 Advertising security type: 'No Authentication' (1)

Now you'll be able to see who gets in or out :grin: 

Quote:
                                                 [COLOR=#cc0000]**How to run commands in a Terminal: **[/COLOR]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter*   again to run the command. Please do not run commands without knowing   what they do. If you do not understand what a command does, ask for   explanations.                      

Kindest Regards

Miguel Tavares
^_^


Awesome work man :)) :guitar:

But now i have new problem my pc is discoverable over the wlan network , but can't connect from a windows pc due some protocol error Oo?  ( are there any settings for windows connections ? ) ?? 

Also about the script ... just copy it into text file right ?

Best regards , 
Presian

---

### Post by Miguel Tavares on 2011-02-20
Well regarding your PC being exposed, buy a Cisco PIX or a Checkpoint which will bring you to another thread and not this one.
Regarding the script just follow the steps provided. Not a txt file but a *.sh file as mentioned.
Doubts regarding vi cmd:
1 - man vi
2 - [http://www.unix-manuals.com/tutorials/vi/vi-in-10-1.html](http://www.unix-manuals.com/tutorials/vi/vi-in-10-1.html)
3 - RTFM

:D

Regards

Miguel Tavares

---

### Post by Miguel Tavares on 2011-02-20
> **adver said:**
> the following is with UPnP disabled on my router and only the top 2 boxes checked in remote desktop

1.  Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  vino           2.32.0-0ubuntu VNC server for GNOME

2.  (Not all processes could be identified, non-owned process info    I tried this with sudo aswell and nothing happened
 will not be shown, you would have to be root to see it all.)

3.  Linux azazel-p6720f 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

4.  Not sure if this is what you mean but, in between the two machines is the router only... so 2 hops I guess one to from the machine to the router, and from the router to the other machine.

Hi,
you realise that you can be root if you issue the "sudo su -" + your password ?

---

### Post by adver on 2011-02-20
I logged in as root with sudo su and re-entered the 2nd command, but it gave no output.  Nothing happened.

---

### Post by mobnovus28 on 2011-02-21
Hi,

I'm new here. Can somebody suggest a classroom management program aside from Italc and Controlalua?

thanks :D

---

