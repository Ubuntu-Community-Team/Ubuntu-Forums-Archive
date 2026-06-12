---
title: "file server becomes unreachable"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by deanwilliams on 2010-01-15
I have a ubuntu desktop 9.10 that is used as a file server and occasionally as a desktop. My problem is after about 15 min of idle the server can not be accessed by other computers. I attempted to disable power management but Im not sure if i did that correctly. Where should i look for problems?

---

### Post by deanwilliams on 2010-01-15
problem seems to go away if i disable the screen saver, but I would rather not leave it disabled. Is there a fix for this?

---

### Post by SlugSlug on 2010-01-15
Not sure of the prob but how is it used as a fileserver? ftp/ ssh / samba?

---

### Post by deanwilliams on 2010-01-15
it is a samba server.

---

### Post by SlugSlug on 2010-01-15
Struggle to believe its a screen saver prob, 

could you post the output of

```
cat /etc/samba/smb.conf
```

---

### Post by deanwilliams on 2010-01-15
I attached a file that has the output from that command.

---

### Post by SlugSlug on 2010-01-15
have you doctored that to cover what your sharing?

I've attached mine you can change that to meet your needs and test it?

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```&& if mine fails you can restore yours by 
```
sudo cp /etc/samba/smb.conf.bak /etc/samba/smb.conf
```edit the below with your needs at the bottom of the file

save it to your desktop as smb.conf and 
```
sudo cp ~/Desktop/smb.conf /etc/samba/smb.conf
``````
[global]
; General server settings
server string = 
workgroup = WORKGROUP
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;interfaces = 127.0.0.1, 192.168.2.1/24
interfaces = lo, eth0
bind interfaces only = true

hosts allow =
hosts deny = 0.0.0.0/0

passdb backend = tdbsam
security = user
encrypt passwords = true
username map = /etc/samba/smbusers
obey pam restrictions = yes
invalid users = root

name resolve order = hosts wins bcast

wins support = no

; printing = CUPS
; printcap name = CUPS

syslog = 1
syslog only = yes

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0700
;browseable = no
;read only = yes
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = yes

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = no
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
;[print$]
;path = /var/lib/samba/printers
;browseable = no
;guest ok = no
;read only = yes
;write list = root
;create mask = 0644
;directory mask = 0755

;[printers]
;path = /tmp
;printable = no
;guest ok = no
;browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = no
;read only = yes
;guest ok = no

[Shared]
path = /home/shared/
browseable = no
read only = yes
guest ok = no
create mask = 0600
directory mask = 0770
force user =   ##[insert username for samba] (or delete whole line)
force group = shared



```

---

### Post by superprash2003 on 2010-01-15
under the powermanagement window , make sure that "put computer to sleep when inactive for" is set to "never"

---

### Post by Iowan on 2010-01-16
> **deanwilliams said:**
>  I attempted to disable power management but Im not sure if i did that correctly. What settings did you apply (change)?

---

### Post by deanwilliams on 2010-01-19
I disabled the power management program from the boot up manager. It turns out the turning off the screen saver didn't solve anything. 

I have installed apache recently and it also becomes unreachable. Its not just samba. It uses a static ip on the network. 

I wrote a script that pings the server every 60 sec and it seems to keep the server alive for me but other users on the network cant access it via samba or the web after 30 min or so. If i restart the server they can see it again. I am kinda at a loss of what to try next.

---

### Post by SlugSlug on 2010-01-19
onboard network card? check out BIOS power managment

---

### Post by deanwilliams on 2010-01-19
i disabled what i could in bios power management. It uses a wireless connection which I am not sure if its onboard. it is a dell zino hd with the 1.5ghz dual core amd.

---

### Post by deanwilliams on 2010-01-19
it looks like it may be an issue with the wireless. I switched it to be hard wired and can still access it after 4 hours. Any ideas on what to change to get wireless working? I was using the broadcom sta driver.

---

### Post by ephestione on 2011-01-14
I am having a very similar problem, only while connected via wire.
Server is 10.04, static IP with computer name let's say "XXX".
I have zoneminder under [http://XXX/zm](http://XXX/zm) and deluge at [http://XXX:8112](http://XXX:8112), also telnet responds at XXX:23

None of them is reachable, not even using the static IP in place of XXX.
It's like the server "loses" its computer name on the network, I can browse the internet when physically using the server, but the Netgear router reports UNKNOWN under computer name from the "attached devices" pages, while it would normally report XXX instead.

I cannot access zoneminder nor deluge webserver interfaces not even from the server itslef using localhost as address.

After reboot everything seems to go finre for about a day or so; it all started randomly some time ago, since it wasn't like this before, and I cannot point it to anything in particular that I changed or did in the past.

I may just wipe it all and reinstall Maverick from scratch, but I tend to get pissed at wasting time like this, especially on a linux server that is supposed to just work.

---

### Post by betaj on 2011-08-17
I have the exact same problem on my Ubuntu box. I'm using a PCI wireless card and the server is reachable through SSH, FTP, SMB and HTTP (on port 8080).

However every few minutes or so (and it seems that it cvoincides with perioods when there has not been any network activity), the server becomes completely unreachable from all protocols....I can't even ping to it!

If i run something on the server that causes it to access the network (such as ping to google.com) the connections are re-established almost instantly!

this problem doesn't seem to crop-up when conencted through the LAN interface.

has anyone had any luck solving this to date?

---

### Post by 5oak on 2011-11-08
Hi all,

I have been experiencing a similar (and related?) connectivity issue on my home network the past few weeks and I can't seem to get rid of it. Here it goes (pardon my lingo if it's not 100% correct).

My setup: LMDE server ('tower') and LMDE client ('thinkpad'). I use tower mainly as a music server (mpd/gmpc) and bittorrent server (rtorrent), not that it really matters. In between there's a linksys router, which is running a dhcp server (ip addresses are bound to mac-addresses). tower has 192.168.1.101, thinkpad has 192.168.1.102. The network configuration is the same on both machines. Subnetmask is 255.255.255.0, gateway (linksys router) is 192.168.1.1 and DNS ip addresses are also the same (can't remember those). There's no firewall involved, both are clean LMDE installs. So there's nothing too fancy, I think...

Now usually everyting's fine (which means I can reach and access tower from thinkpad without any problems). However, when I suspend thinkpad (for a longer time, at least an hour or so), tower becomes unreachable, which means I can't even ping tower from thinkpad (I get 'host unreachable'). ssh gives 'no route to host'. I can ping the gateway and otherwise the connection on both machines is perfectly fine (I can browse the interwebs, etc.). The curious part is though, that as soon as I ping thinkpad from tower everything is OK again (! yes, I've tried this multiple times). Now I don't want to get up every time I want to access tower to ping thinkpad first after a suspended period, so any help would be greatly appreciated. Of course, I've done my share of googling but this one's obviously out of my reach.

I honestly don't know if this issue is wireless specific. Unfortunately, I can't use cables where I live.

Naturally, in case more (specific) information is needed, I'd be more than willing tot provide that.

Best regards,

Stijn

---

### Post by betaj on 2011-11-08
> **5oak said:**
> Hi all,

I have been experiencing a similar (and related?) connectivity issue on my home network the past few weeks and I can't seem to get rid of it. Here it goes (pardon my lingo if it's not 100% correct).

My setup: LMDE server ('tower') and LMDE client ('thinkpad'). I use tower mainly as a music server (mpd/gmpc) and bittorrent server (rtorrent), not that it really matters. In between there's a linksys router, which is running a dhcp server (ip addresses are bound to mac-addresses). tower has 192.168.1.101, thinkpad has 192.168.1.102. The network configuration is the same on both machines. Subnetmask is 255.255.255.0, gateway (linksys router) is 192.168.1.1 and DNS ip addresses are also the same (can't remember those). There's no firewall involved, both are clean LMDE installs. So there's nothing too fancy, I think...

Now usually everyting's fine (which means I can reach and access tower from thinkpad without any problems). However, when I suspend thinkpad (for a longer time, at least an hour or so), tower becomes unreachable, which means I can't even ping tower from thinkpad (I get 'host unreachable'). ssh gives 'no route to host'. I can ping the gateway and otherwise the connection on both machines is perfectly fine (I can browse the interwebs, etc.). The curious part is though, that as soon as I ping thinkpad from tower everything is OK again (! yes, I've tried this multiple times). Now I don't want to get up every time I want to access tower to ping thinkpad first after a suspended period, so any help would be greatly appreciated. Of course, I've done my share of googling but this one's obviously out of my reach.

I honestly don't know if this issue is wireless specific. Unfortunately, I can't use cables where I live.

Naturally, in case more (specific) information is needed, I'd be more than willing tot provide that.

Best regards,

Stijn


I think I've finally found a solution to this problem.  After asking around for a while about what might be causing this, I was told of a rather rare occurance where two hosts are conencted to a single WiFi router but one host cannot reach the other.

Apparently under some rare circumstances this might be caused by poor wifi signal.  Even if the hosts connect to the wifi router without any problems - and both hosts would be reachable from the router, the two hosts would not be able to reach each other. Strangely some IP activity on one of the hosts (such as when the computer starts up or receives pings, etc..) seems to re-enable connectivity between hosts for a period of time.

Believe it or not, I solved this problem simply by moving the WiFi router closer to the server tower.  I believe there's a technical name for this problem but I can't remember it.

Hope this works for you too.

---

### Post by 5oak on 2011-11-08
> **betaj said:**
> I think I've finally found a solution to this problem.  After asking around for a while about what might be causing this, I was told of a rather rare occurance where two hosts are conencted to a single WiFi router but one host cannot reach the other.

Apparently under some rare circumstances this might be caused by poor wifi signal.  Even if the hosts connect to the wifi router without any problems - and both hosts would be reachable from the router, the two hosts would not be able to reach each other. Strangely some IP activity on one of the hosts (such as when the computer starts up or receives pings, etc..) seems to re-enable connectivity between hosts for a period of time.

Believe it or not, I solved this problem simply by moving the WiFi router closer to the server tower.  I believe there's a technical name for this problem but I can't remember it.

Hope this works for you too.

Thank you for your response. I'm having serious doubts about this, though. Maybe I should've made more clear that all I have to do is ping the client and the server becomes reachable again. Could this really have anything  to do with a weak signal? Also, in my case the signal isn't that weak (about 80% on the server and even more on the client)...

---

### Post by betaj on 2011-11-08
> **5oak said:**
> Thank you for your response. I'm having serious doubts about this, though. Maybe I should've made more clear that all I have to do is ping the client and the server becomes reachable again. Could this really have anything  to do with a weak signal? Also, in my case the signal isn't that weak (about 80% on the server and even more on the client)...

I understand your scepticism - I found it hard to believe myself and my wifi signal was always 60%+ on both hosts so I was quite convinced that it wasn't the issue.  But still, I decided I had nothing to lose - and I was very pleasantly surprised.

I live in Malta and our houses here are made of limestone and concrete which can cause WiFi signals to act quite funny.  On the other hand it might just be some kind of flaw in the way the wifi modem handles the signals.

---

### Post by 5oak on 2011-11-08
Thanks again betaj. I'm gonna try and move the router to see if this helps.

Best regards,

Stijn

---

