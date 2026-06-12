---
title: "Accessing a NAS often fails before several trials"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by calande on 2010-09-27
Hello,

I have a NAS on my network. It is password-protected. When I access it using smb://my-nas/public, it fails. I have to try it several times until I get the password prompt to bet granted access. Why doesn't it work right away? I have a gigabit connection between my PC and my NAS. Please let me know how to sort it out. Thanks,

---

### Post by gordintoronto on 2010-09-27
What brand and model of NAS is it? Have you tried Googling that information to see if your experience is typical?

---

### Post by calande on 2010-09-28
My NAS is a Synology DS110+
I haven't found related information on the web.
Any idea? Thanks.

---

### Post by calande on 2010-09-28
Is it a common problem? (It's not the first time it happens to me)

---

### Post by gordintoronto on 2010-09-28
What I know about NASes you could stick in a gnat's eye. I had a look at Google, but it appears to be a rare beast. However, I found:
[http://forum.synology.com/enu/](http://forum.synology.com/enu/) 
which might be a better place to find your answer. (I'm assuming that Windows users will also have the same problem you have...)

What hard drive do you have installed? Does it go offline if it isn't used for a little while? Oh, does the whole NAS shut down, and then "wake on LAN"? I always like to turn off any power-saving features (of anything) for testing purposes.

---

### Post by calande on 2010-09-29
Thanks. No, the Windows computer doesn't have this problem, it mounts the NAS right away&#8230;

---

### Post by calande on 2010-10-03
I noticed that if I access using the IP address, it shows up right away, while it doesn't as easily when using the name of NAS.

---

### Post by Morbius1 on 2010-10-03
If the NAS has a fixed ip address then Bookmark it:

Nautilus > smb://ip-address > Bookmarks > Add Bookmark

It will then show up under Places in Nautilus.

---

### Post by luvshines on 2010-10-03
Are you able to ping the NAS server by it's hostname ??

---

### Post by calande on 2010-10-03
@Morbius1: This is what I do, but I'd like to use the name instead...


@luvshines: Yes

Thanks.

---

### Post by Morbius1 on 2010-10-03
Then create a lookup table to connect the two:

Open /etc/hosts as root and add a line in this format:
```
192.168.0.101  my-nas
```

Where "192.168.0.101" is the ip address of the nas and "my-nas" is the name of the nas device.

---

### Post by calande on 2010-10-03
Thanks, is this the only way? I'm asking because there are new people connecting to the NAS every now and then, and this is not very convenient to add a line in a configuration file...

---

### Post by Morbius1 on 2010-10-03
If your network problem prohibited a netbios name to ip address conversion then it would be another matter. But as you stated in your original post it does work only slowly:
> When I access it using smb://my-nas/public, it fails. I have to try it  several times until I get the password prompt to bet granted access.Besides for occasional use I don't see what the difference is between:
>  smb://my-nas
and 
>  smb://192.168.0.101
Well it is 7 keystokes different :wink:

---

### Post by calande on 2010-10-03
:) Ok, Ok...

---

### Post by luvshines on 2010-10-04
Did you try accessing it with command line.

To list the shares:
smbclient -L <server-name> -U<valid-user>%<passwd>

To access them:
smbclient //<server-name>/ -U<valid-user>%<passwd>

You can also try the smbtree command

---

### Post by calande on 2010-10-04
Do you mean for a test or to access on a regular basis?
Thanks.

---

### Post by calande on 2010-10-05
Hi again, I actually have the same problem when accessing the NAS with its IP address :(

---

### Post by luvshines on 2010-10-05
> **calande said:**
> Do you mean for a test or to access on a regular basis?
Thanks.

I meant for the testing purpose

---

### Post by Morbius1 on 2010-10-05
If you can't access that device by netbios name or ip address then there's something more fundamentally wrong here. Perhaps a firewall is in the way. Run the following command to find out if the samba ports are open:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Run it once with the ip address of the NAS.
Then again with the ip address of the Ubuntu box

You should get something like this:
> Interesting ports on 192.168.0.100:
Not shown: 1992 closed ports
PORT     STATE         SERVICE
[COLOR=Blue]139/tcp  open          netbios-ssn[/COLOR]
[COLOR=Blue]445/tcp  open          microsoft-ds[/COLOR]
631/tcp  open          ipp
68/udp   open|filtered dhcpc
[COLOR=Blue]137/udp  open|filtered netbios-ns[/COLOR]
[COLOR=Blue]138/udp  open|filtered netbios-dgm[/COLOR]
631/udp  open|filtered ipp
5353/udp open|filtered zeroconfThe ones in [COLOR=Blue]blue[/COLOR] have to be open

*[COLOR=Blue]EDIT: Sorry , I keep forgetting that nmap isn't installed by default:[/COLOR]*
```
 sudo apt-get install nmap
```

---

### Post by calande on 2010-11-27
Thanks, Morbius1, I tried but it didn't work as expected:
```
$ sudo nmap -sS -sU -T4 192.168.0.13

Starting Nmap 5.21 ( http://nmap.org ) at 2010-11-27 13:41 CET
Warning: 192.168.0.13 giving up on port because retransmission cap hit (6).
```

---

