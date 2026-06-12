---
title: "trying to set up x11vnc"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by andrea_bio on 2011-03-05
Hi
 
I am a linux novice with root access to an Ubunutn 10 VM which i connect to via putty. I want to connect to it via a GUI from windows xp so I have tried installing x11vnc on the machine and used realvnc from the xp client
 
I have tried to install x11vnc on the machine as follows
 
sudo apt-get install x11vnc vnc-java"
x11vnc -storepasswd
 
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5900 -j ACCEPT
 
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5900 -j ACCEPT
 
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5900 -j ACCEPT
 
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5900 -j ACCEPT
 
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5900 -j ACCEPT 
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5800 -j ACCEPT 
 
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
 
This seems to load ok but removes the shell prompt. I presume the server has started and is listening on the ports so i used another putty window to reconnect to my machine and ran sockstat -l and xllvnc is listening on the 2 ports.
 
I then downloaded realvnc windows client and entered the hostname to connect
 
If i entered just the hostname or hostname:5900 i get a timeout error but if i enter hostname:5800 i get 'connection refused' error
 
thanks a lot

---

### Post by krunge on 2011-03-05
In the way you have it set up, x11vnc will listen on port 5900 for VNC connections and port 5800 for HTTP connections (to download java viewer applet.)

So something like:
```

http://hostname:5800            (in java enabled web browser)
vncviewer hostname:0            (tell vncviewer to use VNC display 0 which is port 5900)

```
I don't understand your "connection refused" error though... check the iptable logging (and enable logging if need be.)

---

### Post by gradinaruvasile on 2011-03-05
The safest way should be tunneling x11vnc through ssh. So no more ports needed. You start x11vnc (this is the actual example i use on my computers - for some reason it works only if i start it as root/sudo):

x11vnc -auth -forever guess -display :0 -localhost -rfbport 20000 -xkb

-localhost the server listens only on localhost, no outside ports need to be opened;
-rfbport can be anything you want;
-xkb -i had keyboard layout issues without it;

connecting - i use Remmina, it is in the repositories, it supports directly ssh tunneling in an easy and elegant way. Remmina it is the best remote connection utility out there (supports VNC, RDP, NX, XDMCP as remote desktop software as well as SFTP file transfer and SSH shell).
The side "effect" of using ssh tunneling is that Remmina lets file transfer/ ssh console through the ssh connection directly, no more authentication needed. You can tab all connections in a single window.
I personally dont let the x11vnc server running, i start it without the -forever flag usually and start it only when i need it through ssh.

---

### Post by andrea_bio on 2011-03-06
Hi
 
Thanks for your reply but I am too much of a beginner to understand what you mean.
 
 
i started the server as you suggested like this:
 
x11vnc -auth -forever guess -display :0 -localhost -rfbport 20000 -xkb

i got a warning saying i was running the server without a password. 
There does appear to be an encrypted password in ~/.vnc/passwd though so i tried this instead

x11vnc -auth -forever guess -display :0 -localhost -rfbport 20000 -xkb -rfbauth ~/.vnc/passwd

There was some loading messages.
The root prompt returned so i assumed the server must be running in the background so i tried ps -ef | grep vnc to look for it but nothing was listed. How do i stop the vnc servers I have started???

I tried connecting via realvnc but still got the same timeout error
 
 
 
If this mode of connection is tunnelling via SSH then i need to set up port forwarding dont i?
 
I should point out the linux machine is a VM which i connect to via putty. It doesn't use the normal port for SSH if that makes a difference. I am connecting from windows xp client
 
thanks

---

### Post by krunge on 2011-03-06
"-auth -forever guess" is incorrect.  I assume "-auth guess -forever" is what the poster intended to type.

I think you should avoid ssh tunnelling for now and try to get it work directly.  If you are absolutely sure you have SSH working we can switch to telling you how to do that.

To check the direct connection I suggest rebooting to get to a clean state. Apply the iptable adjustments you feel should let these two ports in (n.b. I did not check or verify your iptable cmds, so they may be wrong.) Then start x11vnc with the "-o x1.txt" option to get a log file.  Next, run "netstat -antpe > n1.txt" to capture the output to file n1.txt.  Then on another machine on the same LAN use telnet from windows or unix to connect to the vnc host on port 5900 and then to port 5800 (e.g. telnet hostname 5900)  Then kill x11vnc via "Ctrl-C".  Attach both x1.txt and n1.txt to this thread as file attachments.  Examine /var/log/messages for iptables messages and send any message printed out while you were doing this experiment.

---

### Post by andrea_bio on 2011-03-07
I'm not allowed to access any other ports directly :(
 I'm remote from the site and can't access another machine on the same LAN either
I cant reboot either as other people are on the machine
 
 
I got the server started and checked it was listening on port 5900. This is what i did in putty
 
Setup the Client PC:
Launch PuTTY.
Under session:
Host Name: your Unix box FQDN or IP
Click SSH
Give the session a name
Under: Connection / SSH / Tunnels
Enter a port forward for Local
Source Port: 5901
Destination: localhost:5900
Click Add
Click on session again and save it.
Now launch (Open) your PuTTY session and logon to your Linux box's SSH
server.
Then launch your VNC Viewer and enter localhost:1 as the VNC Server.
 
Using realvnc i got the error: unable to connect to host connectionrefused 10061

---

### Post by andrea_bio on 2011-03-07
can't you be sure that ssh is working because someone else set it up and i connect to the machine via putty all the time :)
 
If it makes i difference i am on a virtual machine but i can connect to it via ssh no problem so i presume tunneling over ssh should be possible?

---

### Post by krunge on 2011-03-07
> 
Enter a port forward for Local
Source Port: 5901
Destination: localhost:5900
Click Add
Click on session again and save it.
Now launch (Open) your PuTTY session and logon to your Linux box's SSH server.
Then launch your VNC Viewer and enter localhost:1 as the VNC Server.

So you really did enter "localhost:1" into the RealVNC Viewer?  (I'm pretty sure you did, but really need to make sure since if you put something else 'connection refused' would be a likely outcome.)

And BEFORE you launched the Real VNC Viewer you had x11vnc already running on the other side and listening to port 5900?

Please attach the full x11vnc output ("-o x1.txt" I mentioned before) that results from doing the above setup steps and connection attempt to this thread or send it to me in PM.

---

### Post by andrea_bio on 2011-03-07
Hi
 
I set up the tunnel in putty as described. Then i connected to my VM. Then i changed to root and started the server. The output is below. Then i open realvnc and connecting using localhost:1 and got the error
 
There is nothing in the log other than the start up messages and a ctrl-c from me to stop the server (how should i stop it?)

---

### Post by andrea_bio on 2011-03-07
this is what the terminal displayed
 
:~# x11vnc -forever  -display :0 -localhost -xkb -rfbauth ~/.vnc/passwd -o x1.txt
PORT=5900

---

### Post by krunge on 2011-03-07
> I set up the tunnel in putty as described. Then i connected to my VM. Then i changed to root and started the server. The output is below. Then i open realvnc and connecting using localhost:1 and got the error
 
There is nothing in the log other than the start up messages and a ctrl-c from me to stop the server (how should i stop it?)
Ctrl-C is a fine way to stop x11vnc.

Well, since x11vnc didn't print anything out when you tried to connect to him that proves your SSH tunnel is not reaching his port 5900. x11vnc will print out logging messages whenever a viewer connects.

You said "Then I connected to my VM".  What do you mean by "VM"?  I assume you run Putty and "Realvnc viewer to localhost:1" on a Windows machine and the Putty connects to a Linux Machine running x11vnc.  Not sure what "VM" implies here..

---

### Post by andrea_bio on 2011-03-07
Hi
 
The linux machine I am connecting to is actually a virtual machine on the remote server. I've never actually seen the machine itself to know if it is linux or windows. I'm guessing linux. My VM is Ubuntu 10.04. I connect to that via putty and realvnc. I connect to that via putty and realvnc
 
Hopefully the problem is inside the VM as I have control of that. Otherwise its hard for me to get anything else sorted

---

### Post by andrea_bio on 2011-03-07
Is there anyway I can tell if the ssh tunnel has made it to the VM?

---

### Post by krunge on 2011-03-07
Ah, so there are 3 hosts involved... that may be the reason for the problem.

---

### Post by krunge on 2011-03-07
What I would do on the windows side is not use Putty but use cygwin ssh and run something like this on windows with cygwin:
```

ssh -v -L 5901:localhost:5900 IP-OF-REMOTE-SSH-SERVER

```
Then connect via VNC viewer to "localhost:1".  The "-v" in ssh means verbose debugging messages. Then read that ssh output for any useful info.

BTW: You might find your ssh server has disabled port forwarding.  Look for AllowTcpForwarding=no in /etc/ssh/sshd_config (or whereever the sshd config file is located.)

---

