---
title: "port 80 (http) open on ShieldsUp"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by rng on 2011-07-25
I tried shieldsUp at grc.com and it reported that my system failed the test since port 80 (http) is open. All other ports are closed. Please advise what should I do?

---

### Post by Dangertux on 2011-07-25
Do you have a webserver running?

---

### Post by rng on 2011-07-26
> **Dangertux said:**
> Do you have a webserver running?

No. Its a regular home desktop pc with ubuntu 10.04LTS installation. I did not install any further firewall or other networking tools.

---

### Post by haqking on 2011-07-26
> **rng said:**
> No. Its a regular home desktop pc with ubuntu 10.04LTS installation. I did not install any further firewall or other networking tools.


have you installed something recently that could have a built in webserver ?

you canuse netstat or fuser to see what ports are being used by what.

you can also close a port with

sudo ufw enable

to close port 80

sudo ufw deny 80

---

### Post by rng on 2011-07-26
I have installed some additional programs but not any webserver that I know of. 


I have tried 'sudo ufw deny 80' but it does not help.

---

### Post by rng on 2011-07-26
Following is the netstat -a output. What does this mean?

home@home-desktop:~$ sudo netstat -a | more
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *: x11                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 home-desktop.loca:50880 74.125.236.64:www       ESTABLISHED
tcp        0      0 home-desktop.loca:37328 74.125.236.77:www       ESTABLISHED
tcp        0      0 home-desktop.loca:34400 nx-in-f138.1e100.ne:www ESTABLISHED
tcp6       0      0 [::]: x11                [::]:*                  LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN     
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:60054                 *:*                                
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     7227     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     7081     /tmp/orbit-home/linc-582-0-cdbaa486e4c7
unix  2      [ ACC ]     STREAM     LISTENING     7083     /tmp/orbit-home/linc-57d-0-2d07c0f26e5bc
unix  2      [ ACC ]     STREAM     LISTENING     4868     /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     7230     /home/home/.pulse/3c19a7734bf3126d9d36076d4d10f03d-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     7279     /tmp/orbit-home/linc-5af-0-289dcfcc370af
unix  2      [ ACC ]     STREAM     LISTENING     7847     /tmp/orbit-home/linc-5d1-0-10c10200b5f26
unix  2      [ ACC ]     STREAM     LISTENING     7938     /tmp/orbit-home/linc-5f7-0-506f2498d3422
unix  2      [ ACC ]     STREAM     LISTENING     14089    /tmp/orbit-home/linc-7be-0-49de0376a89cd
unix  2      [ ACC ]     STREAM     LISTENING     7976     /tmp/orbit-home/linc-5f6-0-1bb8d630dcf3c
unix  2      [ ACC ]     STREAM     LISTENING     8221     /tmp/orbit-home/linc-60b-0-74e4d24d91c0c
unix  2      [ ACC ]     STREAM     LISTENING     8243     /tmp/orbit-home/linc-60d-0-3900fcb79a4fa
unix  2      [ ACC ]     STREAM     LISTENING     8264     /tmp/orbit-home/linc-609-0-7505bfc6a266d
unix  2      [ ACC ]     STREAM     LISTENING     8279     /tmp/orbit-home/linc-60e-0-6e6604efa5637
unix  2      [ ACC ]     STREAM     LISTENING     8416     /tmp/orbit-home/linc-622-0-56d1318c20b11
unix  2      [ ACC ]     STREAM     LISTENING     14193    /tmp/orbit-home/linc-7c2-0-62a97eb794508
unix  2      [ ACC ]     STREAM     LISTENING     9409     /tmp/.com.google.chrome.4SBG6s/SingletonSocket
unix  2      [ ACC ]     STREAM     LISTENING     2657     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     8882     /tmp/orbit-home/linc
.....
.....


since many of above are from /tmp folder, I checked its contents. It contains following folders. Are these normal?

keyring-wvObdg  orbit-home  orbit-root  pulse-xA28GTYyyXzs  ssh-dWQXkn1328  virtual-home.OJPQOL

---

### Post by rng on 2011-09-27
I came to know from another forum that x11 listening on network is not good at all and should not occur with default ubuntu installation. I have to reinstall linux, if I do not find a remedy for this. 

I think I will have to regularly check the system with following command:

   sudo netstat -aput         

(a=all, p=program-names, u=udp, t=tcp)

to find what programs have "Active internet connections". The command shows brief output of relevant connections only. The program names are displayed in rightmost column. 

-------------------------

PS: x11 listening disappeared with proper graphics configuration.

---

