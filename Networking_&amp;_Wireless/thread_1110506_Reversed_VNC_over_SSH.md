---
title: "Reversed VNC over SSH?"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by JohnLM_the_Ghost on 2009-03-29
I want to know if it is possible to access a VNC Server who's running SSH Client from SSH server side.

The thing is I need to access an VNC server behind completely firewalled (actually a NAT with no forwarded ports) PC.

VNC doesn't support this by itself. But I thought if I set up an SSH tunell, then it would be plausible.

The thing that makes me doubt though is that VNC Server is listening, so it probably has a open socket already, preventing SSH client to forward that particular port.

So I doubt if it is possible, but maybe anyone has some ideas of how this could be done?

---

### Post by issih on 2009-03-29
I think I'm right in saying you need to set up a reverse tunnel from the pc with the vncserver on it (i.e. the one behind the nat).

[http://www.brandonhutchinson.com/ssh_tunnelling.html](http://www.brandonhutchinson.com/ssh_tunnelling.html)

You need to set up the reverse tunnel to forward the vncserver's port onto the pc you are logging in from, then connect the vncclient to localhost at that port.

Hope that helps

---

### Post by BkkBonanza on 2009-03-29
Yes. Reverse tunnel should work. This causes the vnc server to connect out to another machine and wait for a connection there (listen). So the machine you forward to has to have sshd running. 

I've done this with Remote Dekstop and it worked fine. It's not quite as reliable though because if the connection outward drops then you need something to cause a re-connect otherwise you cannot get back in. Also it doesn't have to go to your local machine (localhost). I had mine go to a vps server I run so that wherever I am with my notebook (which could be off sometimes) I can can connect with a forward tunnel to my vps server (at port matching the endpoint of my other reverse tunnel) and be connect via that server to my (rdp/vnc) server behind the firewall. This worked because the vps server's sshd keeps the tunnel open for me.

---

### Post by JohnLM_the_Ghost on 2009-03-29
I guess I will try both forward and reverse tunnels and see which one works for me.

Theoretically if I set up a tunnel before I set up VNC server the listening port's socket will be free for SSH and VNC then should listen on the remote host... although I think it is more likely it will try to grab socket SSH already owns... and fail therefore.

Well if it does fail, I will try that reverse tunnel (the double tunnel). That is more likely to work, but it will be a bit pain to set it up!

Thanks for the info!

---

### Post by BkkBonanza on 2009-03-30
The ports shoudln't have conflicts at all. It's not hard to set up. One command on the server. eg.

vnc server:
ssh -f user@my_home_ip -R 5900:my_home_ip:5900 -N
(and set your home vnc client to connect to localhost:5900)

If you want a double tunnel then my_home_ip should be your intermediary server and add this command on the client,

ssh -f user@intermediary_ip -L 5900:localhost:5900 -N
(and set your vnc client to connect to localhost:5900,
or skip this tunnel and connect direct to intermediary_ip:5900)

A couple notes. You can use names instead of ips just as well. Nothing will work if the firewall is blocking the ports on your home machine or the intermediary machine. The commands can be tailored a little to suit but as it is with -N the tunnel will be opened permanently until dropped by network failure. You can use "sleep 600" instead of -N to autoclose after 10 minutes.

Google will find you lots of tutorials on this. It's not hard and works well. For more info here is one helpful link,

[http://www.g-loaded.eu/2006/11/24/auto-closing-ssh-tunnels/](http://www.g-loaded.eu/2006/11/24/auto-closing-ssh-tunnels/)

---

