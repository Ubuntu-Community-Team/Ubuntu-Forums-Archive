---
title: "Help on Internet Connection Sharing ICS"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2009-11-30
Hello

My problem is that I.C.S. does not start unless I start the Firestarter GUI interface to iptables. This means that i have to log in to the PC in order to start Firestarter 

before i start Firestarter

$ sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
$


After starting Firestarter the iptables are configurered and ICS is working
and remains so even if I quit from Firestarter. 

How can i ensure that the PC boots to this state and I do not have to manually log in?






Solved via alteration shown in 

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/59647](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/59647) 


Henry, I assume you're kinda new to linux, so I'll keep this simple. First, configure your firewall -- that is, you just have to start it the first time, that'll be ok. After you've done that, open a terminal window, and paste the following in it (without the quotes): "gksudo gedit /etc/firestarter/firestarter.sh". That will open you an editor window. Now, seek in there the following lines (probably line 33 in the file):
------
 echo "External network device $IF is not ready. Aborting.."
 exit 2
------
edit the second line so it becomes:
------
 echo "External network device $IF is not ready. Aborting.."
#	exit 2
------
Now seek these two lines (line 39 I think):
------
  echo "Internal network device $INIF is not ready. Aborting.."
  exit 3
------
edit the second one so that it becomes:
------
  echo "Internal network device $INIF is not ready. Aborting.."
#		exit 3
------
 This will probably fix your problem and you'll have a running firewall. After doing this, you'll probably have to restart your computer. If you want to check whether your firewall is running, just do "sudo iptables -L -n" in a terminal.
 If it doesn't give you this (see below), and it returns many many lines of text, then it means the firewall is active.
------
      Chain INPUT (policy ACCEPT)
      target prot opt source destination
       Chain FORWARD (policy ACCEPT)
      target prot opt source destination
      Chain INPUT (policy ACCEPT)
      target prot opt source destination
       Chain FORWARD (policy ACCEPT)
      target prot opt source destination
       Chain OUTPUT (policy ACCEPT)
      target prot opt source destination
      Chain OUTPUT (policy ACCEPT)
      target prot opt source destination

---

### Post by Neill_R on 2009-12-01
Bump

---

