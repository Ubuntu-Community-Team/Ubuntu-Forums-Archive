---
title: "SSH Troubleshooting"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by Eureka89 on 2009-02-06
Hello,
For some reason, SSH stopped working for me. I've tried Googling and tried all I can for this crap to work.

So from the time of my last successful SSH, this is all I did: (minus all the things I just tried recently)

I removed a few things so they are not publicly viewable. I will denote edits to the file with #edited.
> 
vim .bashrc
clear
ssh [email]user@domain.com[/email]  #edited
ps aux | grep sshd
ping domain.com  #edited
ssh [email]user@domain.com[/email]  #edited
sudo /etc/inid.d/ssh restart
dpkg -l | grep ssh
ps aux | grep sshd
sudo iptables -L
sudo netstat -nap | grep :22
sudo netstat -nap | grep :21
sudo netstat -nap | grep :80
sudo netstat -nap | grep :88
sudo netstat -nap
sudo shutdown -r now
ssh [email]user@domain.net[/email]  #edited, new domain
vim /etc/ssh/ssh_config 
ssh [email]user@domain.net[/email]  #edited
sudo /etc/host.allow
ssh help
ssh --help
ssh [email]user@domain.net[/email] -p 21  #edited
ssh -p 21 [email]user@domain.net[/email]  #edited
ssh -p 512 [email]user@domain.net[/email]  #edited
scp /home/user/.vim/colors/colors.vim [email]user@domain.com[/email]:  #edited
scp /etc/vim/vimrc [email]user@domain.com[/email]:  #edited
# my sound was not working as well at the time
# and SSH was upsetting me
sudo also force-reload
sudo alsa force-reload
killall pulseaudio
sudo apt-get build essential
sudo apt-get install build-essential
sudo module-assistant
sudo apt-get install gnome-audio
alsamixer
alsa reload
sudo also reload
sudo alsa reload
aplay -l
gstreamer-properties
lspci | grep Audio
find /lib/modules/`uname -r` | grep snd
alsamixer
clear
ssh [email]user@domain.com[/email]   #edited
ssh [email]user@domain.net[/email]   #edited
ssh localhost
sudo apt-get remove --purge build-essential
sudo apt-get remove --purge build-essentials
sudo apt-get clean
ssh localhost
ssh [email]user@domain.com[/email]   #edited
ssh localhost
ssh -p 00 localhost
ssh -p 21 localhost
ssh -p 5317 localhost
man ssh
ssh [email]user@domain.net[/email]   #edited
sudo shutdown -h now


That's the whole thing with a few comments in place. At first, I thought build-essentials was causing it so I tried removing it. Right now, I'm thinking apt-get clean may have caused it. But I think it stopped working before I ran that command. I don't really know. At the time of the log above, ssh localhost fails as well. The error was a connection denied on port 22. I tried other ports, none of which works.

The netstat -napt does show that I have tcp6 on port 22 with status LISTEN. Every connection test I've tried seemed to pass just fine. I'm absolutely out of ideas now.

I also found this when I Googled and I ran it:
```
sudo apt-get --reinstall install `ls *.list | sed s/\.list$//`
```

That didn't fix my SSH problem. It may have fixed SSH localhost to work since it works now but I'm not sure because I also tried re-installing SSH. One of them fixed ssh localhost but I think that's it.

If anyone know the problem or have any troubleshooting tips and are willing to share, please list them.

Edit: on the logs above, those vim commands to files you see, I didn't modify anything. I just took a look. I exited them all with :q! to ensure I didn't save any changes.

Lastly, I am currently running Ubuntu 8.04.

Thanks a lot,
Eureka89

---

### Post by wirelessmonkey on 2009-02-06
```
cat /var/log/auth.log 
```

Should report authentication attemps, and in many cases will tell you why it failed.

---

### Post by superprash2003 on 2009-02-07
do you get a connection refused error when connecting from another machine??

---

### Post by Eureka89 on 2009-02-08
Okay so this is a bit weird. SSH was just working again and now it's off.

@wirelessmonkey: when it's off, I get no authentication attempts so it doesn't log it. When I type: "ssh [email]user@domain.com[/email]" the cursor just blinks on the next line until it either times out or I kill it with Ctrl + C. It doesn't even prompt me for the password.

@superprash2003: I don't. It's just this one. It worked all day today except it stops working now.

Thanks for the replies and efforts though. I do appreciate them. :)

---

### Post by jimv on 2009-02-08
Could try reinstalling it:

sudo apt-get remove --purge openssh-server
sudo mv /etc/ssh/sshd_config /etc/ssh/sshd_config.old
sudo apt-get install openssh-server

---

### Post by Eureka89 on 2009-02-08
> **jimv said:**
> Could try reinstalling it:

sudo apt-get remove --purge openssh-server
sudo mv /etc/ssh/sshd_config /etc/ssh/sshd_config.old
sudo apt-get install openssh-server
There is no more sshd_config file after you removed it with line one. Regardless, I re-installed it and it still doesn't work. :(

And this time, I didn't even touch apt-get or modify any files relating to SSH. The only files I touched are the ones for my site. And the only sudo command I ran was to restart my computer once (hoping that would solve SSH) and a shutdown. Those are it.

Thanks for your effort though. :)

---

### Post by Eureka89 on 2009-02-14
Okay so I got SSH to connect now, but I can't seem to prevent it from timing out. I have:

> 
TCPKeepAlive yes
ClientAliveInterval 300


I read that those work, but I still get time outs after not doing anything on the Terminal for a while. Is this a server thing or are there more sshd_config lines that need to be added?

Thanks!
Eureka89

---

