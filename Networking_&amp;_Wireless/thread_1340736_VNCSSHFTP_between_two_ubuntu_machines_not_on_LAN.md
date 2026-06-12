---
title: "VNC/SSH/FTP between two ubuntu machines not on LAN?"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by lee.colby on 2009-11-28
I first want to apologize if this has been discussed already, but with so many similar posts and small differences in them, its just easier to start a new thread. Heres my question...I currently run ubuntu 9.10 on my personal laptop, and I just recently converted my parents home computer to ubuntu as well (YAY!). They like the simplicity of ubuntu over windows, but aren't knowledgable enough to do some things. I have been looking into different ways of connecting the two machines to transfer files, keep up with their updates, etc. I live in a different city than my parents, and I am unsure how to remotely connect to their ubuntu machine. When I visit and I am on their LAN, I can use ssh and vnc to connect, but not when I am at my personal home. So, what is the best way to stay connected to their computer when not on their LAN? I have looked into apache, and sftp, but I'm not sure how to go about it? And if I have not even mentioned a better alternative please, enlighten me :D

---

### Post by puppywhacker on 2009-11-29
Create a tunnel like ipip, gre, ipsec or openvpn. Those will allow you to be on the lan remotely. But ofcourse with ssh it's a lot easier to just remotely login, do tunneling and xwindows forwarding. I think vnc, rdp and xdmcp for remote desktop slow over the internet. My point is that you have a lot of options, some will suite you better.

Ah, you cant ssh remotely? Than you will have to setup port 22 forwarding from the router. You might than also be interested in the fail-to-ban package

---

### Post by Lars Noodén on 2009-11-29
If they have one machine then you can set their modem or router to forward port 22 to that machine.

1. Set up openssh-server on their machine.
[indent]
PermitRootLogin no
[/indent]

2. Make an account for yourself on their machine and on your machine make a key pair with a good, strong pass phrase.  Copy the public key to their machine (ends with .pub)

[indent]
ssh-keygen -b 2048 -t rsa -f ~/momnpop_rsa
[/indent]

3. Enable key-based authentication in sshd_config by adding the public key created above into ~/.ssh/authorized_keys.  Keep the key all on one unbroken line.  

[indent]
cat ~/momnpop_rsa.pub >> ~/.ssh/authorized_keys
[/indent]

4. Disable password-based authentication in /etc/sshd_config.  
[indent]
PasswordAuthentication **no**
[/indent]

Then when you want to connect you ssh to their external IP address.  

If you want to use VNC, have them start up vnc sharing, then you tunnel to their machine using ssh.  The default for vnc is 5900 + the display.  So vnc display :1 is on port 5901, vnc display :2 is on 5902, etc.
[indent]
ssh -L 5901:localhost:5901 momnpop.example.org
[/indent]
then use your vnc client connect to your machine -> localhost:1, localhost:2, etc. which in reality is a connection via ssh to their machine.  


To copy files to or from their machine, load your key into the agent, then use an sftp client like Nautilus, Filezilla, Konqueror, or Dolphin.

---

