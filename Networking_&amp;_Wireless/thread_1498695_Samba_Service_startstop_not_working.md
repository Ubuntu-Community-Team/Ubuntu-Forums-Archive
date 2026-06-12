---
title: "Samba Service start/stop not working"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Mgamerz on 2010-06-01
Hi, 
I just recently installed Ubuntu Server Edtion Lucid Lynx onto a spare machine I have to use as a media server for my home. I was following this guide:
[http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/](http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/)
I'm assuming it's probably pretty close to lucid's structure so I just followed it (I used the latest .deb for webmin) However, I am currently using SSH with no desktop installed onto it... I cannot access my shares that I have set up. Webmin states that the shares exist (I first manually coded them and then used the webmin wizard when they didn't work). So I clicked 'Restart Samba Service' and BAM! It says /etc/init.d/samba start failed (It uses stop/start not reload). So I decided to go into SSH and try that command as sudo to see if it just didn't use sudo... 
and I get '/etc/init.d/samba command not found. I just typed in sudo apt-get install samba and it says samba is already at the latest version. 
So I typed in Samba, and it says i need samba4. I typed that in... and it's still not working. 
I did an ls of /etc/init.d/ and I see samba4 but not samba. I'm not sure as to what is going on here...
Anyone else have any idea? I want to be able to have this as a file share so I can easily add music and stuff to my share folder over SSH/SCP.
Thanks,
Mgamerz

---

### Post by wahyabiantara on 2010-06-01
I also have the same problem with you when i update form 9.10 to 10.04.

And i try to use this command

```
sudo service nmbd restart 
```

or 

```
sudo service smbd restart
```

and it work fine

---

### Post by Mgamerz on 2010-06-01
Oh I see... thanks. I wasn't aware that it had changed. Thanks!

---

### Post by christophevr on 2010-06-01
Hello All,

I used samba for very long time. A couple of years .... ago I started using linux on that time debian. Now since 1 year ubuntu. Yes I spended months in finding out on how to use samba perfectly and save . Finnally I had my own optimum smb.conf file.

LIKE MANY OTHERS UPGRADING TO 10.04 CAUSED MY samba not to not run anymore.

But samba is installed using synaptic. of course i always replaced the smb.conf by my own adapted one

WELL it's quit stupid but there is just missing the file samba into /etc/init.d which was the samba start stop file script

and the link to samba /etc/init.d/samba named S20samba into rc2.d rc3.d rc4.d and rc5.d which causes samba to start on boot. (on ubuntu it was on all of them by 9.10. I do not now which is default run level from ubuntu gues it's 2)

I'll appent here the samba start stop script from ubuntu 9.10 which has to be extracted and copied into /etc/init.d and then just make the link to it into folder /etc/rc2 to rc5.d folder using sudo ln -s command example

open console

Youruser@Yourpcname:~$ cd /etc/rc2.d
Youruser@Yourpcname:/etc/rc2.d$ sudo ln -s /etc/init.d/samba S20samba
do the same for rc3.d till rc5.d

Soon I gues the way how samba is started will change. But for now it didn't

---

