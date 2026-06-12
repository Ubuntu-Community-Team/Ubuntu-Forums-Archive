---
title: "Cannot connect to SSH-Server outside network"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by owena1337 on 2013-06-07
Hello all,

I have a problem which is quite weird but annoying. I have a server which is running Ubuntu 10.04 LTS, it has a static ip address and has been put into the DMZ. All services work on there outside the network BUT SSH. I can connect locally to the server via SSH but not when i'm outside the network. I've already ran this command [FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]"[/FONT]iptables -I INPUT -i eth0 -p tcp --dport 22 -j ACCEPT[FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]" [/FONT]Nothing changed. I can change the port to 23 and I can SSH into the server on that port fine from inside/outside the network. I'm really confused and I'd appreciate any help.

- Owen

---

### Post by Doug S on 2013-06-07
Are SSH (port 22) packets being blocked from even getting to your server? For example, if your "inside" network is at your company, many companies block port 22. You could run tcpdump (or wireshark, if you prefer) to observe port 22 traffic at the packet level:```
sudo tcpdump -n -nn -tttt -i eth0 port 22
```

---

### Post by owen777 on 2013-06-08
Not sure if i'm meant to run that on the server it self or through SSH locally?

---

### Post by SeijiSensei on 2013-06-08
Install a copy of **nmap** on the machine from which you are trying to connect.  Then run "sudo nmap -sT ip.addr.of.remote" to see all the open ports on the remote machine.  Is 22 among them?

---

### Post by owen777 on 2013-06-08
Disregard that, I realised port 22 was port forwarded to my raspberry pi. 

Thanks.

---

