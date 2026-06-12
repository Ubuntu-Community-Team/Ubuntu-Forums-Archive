---
title: "Connecting to a computer through SSH"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by nl4m on 2011-02-13
I have 2 computers in my house, on my network. I want to connect to one computer to the other using SSH. On one I installed "OpenSSH-server". "OpenSSH-client" was already installed. I go to the other computer to try to connect to the "server" computer and I enter in the terminal:
```
ssh username@192.168.0.33
```
It never connects. The text input "bar" keeps blinking, it never connects and I get the "Connection timed out" message. 

Any tips on how I can connect to the "server" computer? What am I doing wrong? And if I edit my "/etc/ssh/sshd_config" file to listen to port "12345" how do I get the other machine to connect to that port? Thanks.

---

### Post by dmizer on 2011-02-13
For this command ...
ssh [COLOR="Red"]username[/COLOR]@[COLOR="Blue"]192.168.0.33[/COLOR]

The [COLOR="Red"]username[/COLOR] needs to be an active account on the ssh server computer, and [COLOR="Blue"]192.168.0.33[/COLOR] should be the ssh server's IP address.

If both of those are correct, do you have a firewall installed on the SSH server?

Also to connect to an alternate port, you can use the -p switch like so:
```
ssh username@192.168.0.33 -p 12345
```

---

### Post by nl4m on 2011-02-13
I've turned both of the computers into servers. I can't connect to neither of them. The "username" is an active name. Is it a problem that they are the same names? I'll go create an account with a different name to see what happens. I got my I.P. by typing in the terminal:
```
ifconfig
```

When I enter "ssh this-computers-user-name@this-computers-ip". I connect to the very same computer I'm on. If I enter the username@IP of the other one I get the blinking "bar".

---

### Post by dmizer on 2011-02-13
Do you have firewalls in place on the machines?

Edit:
No, it's not a problem if both machines are using the same username.

---

### Post by nl4m on 2011-02-13
I have "FireStarter" and UFW as a firewalls... 


_____________________________________________

I solved this problem. I am going to write down what I did just in case people out there encounter the same problem. 

The Problem:
Now I have a now problem. On both machines I've entered: 
```
sudo apt-get purge openssh-client && sudo apt-get purge ssh
```Reinstalled them both, and now I get this error message:

"@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
9d:60:40:46:32:d9:e3:56:2a:g7:93:87:2e:96:c7:09.
Please contact your system administrator.
Add correct host key in /home/linux/.ssh/known_hosts to get rid of this message.
Offending key in /home/linux/.ssh/known_hosts:1
RSA host key for 192.168.0.33 has changed and you have requested strict checking.
Host key verification failed."


The solution: 
```
cd /home/username/.ssh
```
```
rm $(ls)
```
```
sudo apt-get purge openssh-client && sudo apt-get purge ssh
```
```
sudo apt-get remove openssh-client && sudo apt-get remove ssh
```
```
sudo apt-get install openssh-client && sudo apt-get install ssh
```

---

### Post by dmizer on 2011-02-13
This is to be expected because the host generated a new key when you reinstalled. Remove the known_hosts file with this command:
```
rm /home/linux/.ssh/known_hosts
```

Also, please post the output of this command:
```
sudo iptables -L
```

Your problem is not with the servers, so reinstalling SSH did nothing. You know that the servers are working correctly because you can connect to the same machine. The problem is the route to the server is being blocked. The block could be a result of a couple of things:
1) There is a firewall in the way.
2) Both machines are not actually on the same LAN (Wireless connected to a neighbor for example).

---

### Post by dmizer on 2011-02-13
Firestarter is your problem. I suggest removing it.

Do you have a specific need for a firewall? Is your local network untrusted (as with an open wireless access point)? Do you have a router (with a firewall) between your computers and your modem?

If you have a router and your LAN is trusted, then you don't need software firewalls on your LAN computers.

---

### Post by nl4m on 2011-02-13
^You are a Genius times 10 :) You fixed the problem. It was Firestarter :) and thanks for the "rm /home/linux/.ssh/known_hosts" tip, too!!! Everything works like a dream...

To change the port I edit the /etc/ssh/sshd.config file and add port "12345", and on the other computer I enter "ssh user@192.168.0.33 -p 12345", right ? And if I want to copy one file from one computer to the other? I used the commend
```
ssh user@192.168.0.33 "cp abcd.txt" abcd.txt
```
But it didn't copy the file to the computer I was on.

---

### Post by dmizer on 2011-02-14
> **nl4m said:**
> To change the port I edit the /etc/ssh/sshd.config file and add port "12345", and on the other computer I enter "ssh user@192.168.0.33 -p 12345", right ?
Yes, except the file is /etc/ssh/sshd_config

To copy a file via SSH, you actually have to use a completely different command like so:
From local machine to remote machine:
```
scp -r /local/file/path.txt username@remote.ip.address:/path/to/target/directory/
```
From remote machine to local machine:
```
scp -r username@remote.ip.address:/remote/file/path.txt /path/to/local/directory/
```

---

