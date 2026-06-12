---
title: "Sharing Ubuntu Files With Vista"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by WannabeFantasma on 2009-10-31
Hi all,

I've been trying to find my Ubuntu laptop on my Vista machine for over a week now and it's no fun anymore :(

Been to lots of sites but still doesn't work, earlier I tried this with my XP and it worked in 2 minutes....

I can see my Vista machine from Ubuntu
but i can't see Ubuntu Laptop in Vista, testing it to maybe make a home server...

it's Vista - Switch - Ubuntu

I'm trying to share the documents using Samba.

Can someone please help me?

---

### Post by ST3ALTHPSYCH0 on 2009-10-31
What version of Ubuntu?
I had full read/write both ways before upgrading to 9.10, now it seems as though all networking has been broken by Karmic. 
One would think that good configuration would be maintained with an upgrade.

---

### Post by WannabeFantasma on 2009-10-31
At the moment still 8.10 

No need to go to 9.10 atm when it's just file sharing? :)
and first wanted to get it to work before going to "next version"..

---

### Post by WannabeFantasma on 2009-11-02
Please Someone? :(

---

### Post by gorg_karlo on 2009-11-02
You might want to have a look at dmizer's excellent [threads]("http://www.backports.ubuntuforums.org/showpost.php?p=7157868&postcount=12") on network file sharing.

If you are using 8.10, I think you'll be fine with the instructions.

I myself is looking for an answer since I moved up to 9.10 (should have waited for the bugs to be ironed out...) - before everything works perfect following the troubleshooting threads I linked above. Now, I have a DBus error org.freedesktop.DBus.Error.NoReply error every time I try to connect to a Windows share.

---

### Post by WannabeFantasma on 2009-11-02
I did it (3) and i still can't see my ubuntu laptop in windows Vista...

going to try the other 2 things again and hope it'll work somehow..

[http://www.freeuploadimages.org/images/6d1tf8i2zzlgy9unqxc3.jpg](http://www.freeuploadimages.org/images/6d1tf8i2zzlgy9unqxc3.jpg) this is on my vista

[http://www.freeuploadimages.org/images/bcsujfl1zdfgqtdi8hs.jpg](http://www.freeuploadimages.org/images/bcsujfl1zdfgqtdi8hs.jpg)  on my ubuntu
PC_van_Kjeld is my pc / servertest is my laptop's name

---

### Post by gorg_karlo on 2009-11-02
Please tell us the result so we can keep track of your progress.

---

### Post by WannabeFantasma on 2009-11-03
still can't see my ubuntu laptop in vista 

and strangely after I installed that winbind(or something)
i couldn't see my pc on my ubuntu...
so kinda messed things up :( might install ubuntu again and hope it'll work...

---

### Post by gorg_karlo on 2009-11-03
Uh, sorry to hear the failure...

Don't lose hope. Try one more link: [http://ubuntu.swerdna.org](http://ubuntu.swerdna.org).

Good luck! :p

---

### Post by WannabeFantasma on 2009-11-03
i did most of that stuff :D

weird thing is my XP can see my Ubuntu but Vista can't, and i can't even connect with the ip so...

I'll try it tomorrow :)

wish i could set myself a static ip (would make connecting easier) but when i do that i don't have internet anymore and that for a guy who studies P2P atm.. (probably because of the switch instead of router...)

ok teacher pulls out the internet connection and stuff :D 
but here at home i need it :(

anyway I'll test it tomorrow and report back 

Hope it'll finally work!! :D   ):P

---

### Post by WannabeFantasma on 2009-11-04
All i need to do is "[homes] Users' Roaming Shares" ??

And still... I can't find my ubuntu machine on _vista_ (not even with :\\Servertest\kjeld or :\\IP\Kjeld
but on my_ XP _everything works as a normal p2p network with icons and stuff and i can stream music from it 

and I can see both my Vista and XP on ubuntu.... 

I can Ping from my Vista to ubuntu and I can tracert from vista to ubuntu.....

i will try some things of this [http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer) again....... hope it'll finally work some people have done it with that guide on vista so it's kinda my last hope :(

---

### Post by mister_doctor on 2009-11-04
- Check your firewall settings on Vista to make sure that File and Print sharing are exempt.

- On the Vista machine, see if Network Discovery is turned on. It's trivial on a home network but you never know, it might help...

Could you elaborate more on your home network setup? Do you have a router where you can access the admin pages? If so, you can assign your Ubuntu machine an IP reservation. It's like having a static IP address, only it's assigned via DHCP.

---

### Post by WannabeFantasma on 2009-11-04
1) yeh it's checked
2) Checked too

I have a router where i can acces admin pages but we mostly just use a switch here... + when we don't need it we remove the power cord 
 for some reason my ubuntu is acting all weird :s

Checking the filesystem....
1075

ah well re-install :lolflag:

mm ok so after reinstall (with 9.10) it's working again but still no Ubuntu on my vista machine...
so still the same :D

but now when I log in it says "some sectors are damaged"... 
(nothing to do with Samba )

---

### Post by Iowan on 2009-11-04
This probably won't help, but... 
if connection is via DHCP, edit */etc/dhcp3/dhclient.conf* and add hostname to the line:```
send host-name "<hostname>";

```

---

### Post by WannabeFantasma on 2009-11-05
kjeld@servertest:~$ /etc/dhcp3/dhclient.conf 
bash: /etc/dhcp3/dhclient.conf: Permission denied


damn..

---

### Post by Iowan on 2009-11-05
Try it with either```
sudo nano /etc/dhcp3/dhclient.conf
``` or ```
gksudo gedit /etc/dhcp3/dhclient.conf
```

---

### Post by WannabeFantasma on 2009-11-06
k will try it when i have time :)

---

### Post by sb73542 on 2009-11-09
> **Iowan said:**
> This probably won't help, but... 
if connection is via DHCP, edit */etc/dhcp3/dhclient.conf* and add hostname to the line:```
send host-name "<hostname>";

```

Hi,

Thanks, sorry for the delay.  Yes, I am running dnsmasq on the dd-wrt router.  I tried the dhclient.conf trick, but to no avail.  It still can't resolve the IP address of COMPUTERNAME.  Any ideas?

Thanks!

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
I was able to get my network in (mostly) working order by installing Samba 4 and the GUI frontend for configuring. Best of luck!!

---

### Post by dmizer on 2009-11-10
Please post your current /etc/samba/smb.conf file.

---

### Post by WannabeFantasma on 2009-11-13
[global]
    ; General server settings
    netbios name = SERVERTEST
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
  

[Documents]
    path = /home/kjeld/Documents
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = Kjeld
    force group = Kjeld

tried alot though :D 
this might be like really really messed up...

---

### Post by dmizer on 2009-11-13
> **WannabeFantasma said:**
> 
this might be like really really messed up...
Uh ... yeah, a bit. ;)

Try this:
```
#======================= Global Settings =======================

[global]
   workgroup = WORKGROUP
   netbios name = SERVERTEST
   server string = %h server (Samba, Ubuntu)
   dns proxy = no

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = share
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

########## Printing ##########

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

[Documents]
        path = /home/kjeld/Documents
        read only = no
        guest only = yes
        guest ok = yes
```

Restart samba or reboot after making the above change.

---

### Post by WannabeFantasma on 2009-11-13
i'll test later ^^ 

Hope Vista finally finds my ubuntu machine :o
--------------------------------------
Yesh It works on Win7 and vista :o

thank you SOOOOOOO much :o

---

