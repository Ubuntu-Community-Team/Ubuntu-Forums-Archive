---
title: "Folder Sharing"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by yofat on 2012-05-18
Hi, Thank you everyone in advance for whatever advice you can give me :)

I'm trying to set up a network in Ubuntu 12.04 LTS. However, when I try to share a folder I get an error 

I've searched and I cant find a way to fix this. I cant share the folder either. at first I tried to use system-config-samba as a GUI tool to set up samba, but I wasnt able to connect. From the first moment I opened this tool I got an error stating "Some lines couldn't be understood while reading the configuration file /etc/samba/smb.conf. THese may be unknown configuration directives for Samba plugins but could also be configuration errors." If I hit "shor_details" it doesnt show anything. Well, since the GUI tool didnt help me to share a folder I tried to do this from Nautilus, that's when I got the error:

'net usershare' returned error 255: Ignoring unknown parameter "SO_SNDBUF"
Ignoring unknown parameter "update encrypted"
net usershare add: cannot convert name "Everyone" to a SID. Unexpected information received.

Like I said, I searched online, tried to edit /etc/samba/smb.conf but got no results.

I'm just a newbie, dont know quite much of Ubuntu 'under the hood', but I'm trying to get there =D Hope someone can help me!!! pls :s

---

### Post by yofat on 2012-05-18
In case someone asks, this is my smb.conf file

> [global]
	netbios name = Samba24
	server string = Samba file and print server
	workgroup = workgroup
	security = user
	hosts allow = 127.192.168.0.
	interfaces = 127.0.0.1/8 192.168.0.0/24
	bind interfaces only = yes
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	printcap name = cups
	cups options = raw
	guest account = avahi
	log file = /var/log/samba/samba.log
	max log size = 1000
	username level = 6
	password level = 6
	encrypt passwords = no
	unix password sync = yes
	socket options = TCP_NODELAY SO_RCVBUF=8192
SO_SNDBUF=8192
	local master = no
	domain master = no
	os level = 33
	logon drive = m:
	logon home = \\%L\homes\%u
	logon path = \\%L\profiles\%u
	logon script = %G.bat
	name resolve order = wins lmhosts bcast
	dns proxy = no
	client use spnego = no
	client signing = no
	client schannel = no
	server schannel = no
	allow trusted domains = no
	obey pam restrictions = yes
	enable spoolss = yes
	follow symlinks = no
	update encrypted = yes
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete user script = /usr/sbin/userdel '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	machine password timeout = 120
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind use default domain = yes
	winbind separator = @
	winbind cache time = 360
	winbind trusted domains only = yes
	winbind nested groups = no
	winbind nss info = no
	guest ok = yes

[homes]
	comment = Home Directories
	path = /home
	valid users = %U
	read only = no
	locking = no
	strict locking = no

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = yes
	locking = no
	strict locking = no

[SambaShare]
	path = /home/yofat/SambaShare
	writeable = yes
	guest ok = yes

Really dont know what am I doing :( If someone can give any lead, please. Thanks :)

---

### Post by markbl on 2012-05-18
You are making it more complicated than it needs to be. If you search google you will find heaps of guides about editing smb.conf etc but that is not needed for simple folder sharing in modern ubuntu.

Try and back out all the manual changes you have done. Perhaps do a "apt-get purge samba"? Then just right click on the folder you want to share and select "Sharing Options". That will automatically install any packages it needs etc (e.g. samba) and will set the configuration settings for you.

---

### Post by yofat on 2012-05-19
:s Thank you for the quick answer :)

I tried and backed out all the changes I made to smb.conf and I still got the same error.

So, I did 'apt-get purge samba' as you advised. Once purged, I went to the folder I wanted to share > right click > sharing options > share this folder. It asked me to install samba, I did. It installed it without any problems. Then asked me to restart session. I did. I was happy at this point because I was sure it was going to work :) but then again, after I tried to share the folder I got the same error listed above :(

Have no idea what to do next

---

### Post by Morbius1 on 2012-05-19
[1] Do not ever use gadmin-samba again for as long as you live.

[2] Purging the "samba" package will not resolve your discombobulated smb.conf file since that file doesn't come from the "samba" package. 

[3] Restore a factory fresh copy of smb.conf:

**(**) Make sure the following file exists: **/usr/share/samba/smb.conf

**(**) Make a backup of your current smb.conf**
```
  sudo cp /etc/samba/smb.conf /etc/samba/smb.confMOD 
```**(**) Start with a fresh one:**
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/ 
```**(**) Correct one mistake in the new one:**
Find the line:
>  encrypt passwords = false and change it to:
> encrypt passwords = true**(**) Restart samba**
```
sudo service smbd restart
```

---

### Post by yofat on 2012-05-19
HOLLY *****!!!!!!

Dear Morbius1!!! I owe you!!!!!! thank you so much, now its shared!!!!!! Wow, that was really simple.... I'm really, really thankfull... And  I guess your right about gadmin-samba. Before upgrading to 12.04, in 11.10 I was able to share the folder but I didnt use any folder... I really dont know why did I got the genius idea of try and use that tool....

Now, like I said, I'm kind of new to this forum... Is there anything I have to do to close this thread, or to put it as solved?

And again, THANK YOU!!! It worked!!!! :)

---

### Post by yofat on 2012-05-19
jajajajajaja sorry for the previous dumb question xp....
Marked it solved XD
Thanks

---

### Post by Malac on 2012-10-08
thanks Morbius1 Worked for me too.

---

### Post by Rezliw on 2012-10-27
I promise never to even think about Gadmin-samba (but it looked so good)  Vile treachery:mad:

---

### Post by mcvries on 2012-11-29
Thanks a lot, fixed my sharing issues within 15 seconds. After i've spent about 30 minutes figuring it out myself.

---

### Post by dodjob on 2013-01-11
Thanks mate :) worked flawlessly :popcorn:
*edit: I had "no" instead of "false" though :)

---

### Post by Morbius1 on 2013-01-11
> **dodjob said:**
> Thanks mate :) worked flawlessly :popcorn:
*edit: I had "no" instead of "false" though :)
Despite claims to the contrary Samba is remarkably flexible allowing yes/true and no/false. It also allows for misspelled words: writeable / writable. 
[B]
[/B]

---

### Post by pgradone on 2013-06-19
> **Morbius1 said:**
> [1] Do not ever use gadmin-samba again for as long as you live.

[2] Purging the "samba" package will not resolve your discombobulated smb.conf file since that file doesn't come from the "samba" package. 

[3] Restore a factory fresh copy of smb.conf:

**(**) Make sure the following file exists: **/usr/share/samba/smb.conf

**(**) Make a backup of your current smb.conf**
```
  sudo cp /etc/samba/smb.conf /etc/samba/smb.confMOD 
```**(**) Start with a fresh one:**
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/ 
```**(**) Correct one mistake in the new one:**
Find the line:
and change it to:
**(**) Restart samba**
```
sudo service smbd restart
```


Thanks very very very much for this man - I was trying this file sharing feature for days, and finally today it works!! :D
Next question would be: why did Canonical allow to leave "encrypt passwords = no" as default in the smb.conf file, and this even up until the days of raring ringtail? :o
I know it's just a default, but do you have an idea of how many noobs (like me :°) you might have lost?

---

### Post by Morbius1 on 2013-06-20
> **pgradone said:**
> Thanks very very very much for this man - I was trying this file sharing feature for days, and finally today it works!! :D
Next question would be: why did Canonical allow to leave "encrypt passwords = no" as default in the smb.conf file, and this even up until the days of raring ringtail? :o
I know it's just a default, but do you have an idea of how many noobs (like me :°) you might have lost?
I'm going to let you in on a secret that confounds even long time users of Samba. The file at /etc/samba/smb.conf [COLOR=#0000cd]**is not**[/COLOR] the samba configuration file. It's a file that the local administrator of the box ( you ! ) uses to add to or override the default settings of samba. There is no "file" that contains the default settings there is only a way to see the defaults by running a command.  Let's take "encrypt passwords" as an example.

By running the following command you can see that the default setting of Samba has that parameter set to Yes:
```
testparm -sv /dev/null | grep "encrypt passwords"
```
Unless you have encountered a bug somewhere during the install the standard smb.conf file has no affect on this state of this parameter. This command will show you the affect of the default smb.conf on that default setting
```
testparm -s | grep "encrypt passwords"
```
You will notice that there isn't even a mention of "encrypt passwords" in the output. You can even add it to the file ( set to yes ) and testparm will still show it missing since adding it has no affect on the default settings.

The file at /usr/share/samba/smb.conf is another matter and comes from the samba-common package. It doesn't come from Ubuntu it comes from the Samba factory. Why it has encrypt passwords set to No is a mystery but it's not Ubuntu's doing it's Samba's.

---

