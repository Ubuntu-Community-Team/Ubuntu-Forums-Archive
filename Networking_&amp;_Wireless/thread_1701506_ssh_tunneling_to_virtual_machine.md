---
title: "ssh tunneling to virtual machine"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by andrea_bio on 2011-03-06
Hi
 
I am a linux beginner and dont know that much about networks!
 
I have access to a linux VM. The machine is remote and i access via putty.
 
If i can access this machine via SSH and putty, is there any reason why i should not be able to use ssh tunnelling to connect to a vnc server?
 
I don't know the details of the server and what firewall is set up but  i believe that tunnelling uses port forwarding over the ssh connection that is already set up. Where does the port forwarding actually occur? At the actual linux VM or on the router the VM is connected to?
 
thanks

---

### Post by Mickser_52 on 2011-03-10
Hi,

3 days and no reply? Can't answer your query specifically but maybe move it back to top of posts for someone who can.

I recently set up ssh to a remote imac which runs on Darwin Linux so somewhat relevant. 

You should be able to set up tunneling to vnc server. I managed to do it from various googlings. (Is that a new word?) but I found it quite slow. What I do now is connect via ssh, turn on the remote vnc from the terminal then connect via my vnc client (Xtightvnc) when I want and then quit remote vnc when finished to avoid unwanted login attempts. It is a lot faster.

Setting up ssh required making changes to the sshd configuration file on the imac and also opening a port on the remote router to use a non standard (port 22) port which was recommended on various sites. 

Hope some of this helps if only to refresh your original query

---

