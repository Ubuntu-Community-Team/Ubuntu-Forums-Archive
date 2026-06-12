---
title: "Can't access Ubuntu computer from Windows 7!!!"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by xdominex on 2010-10-23
Hello,
I recently decided to install Samba in Ubuntu as a home file-sharing server. However, when I try to access this computer from another (using Windows 7), an error messages comes up. It says:
"You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The specified domain either does not exist or could not be contacted."

Please help me. :(

---

### Post by d3v1150m471c on 2010-10-23
use gedit to modify your smb.conf file. 
```

gksudo gedit /etc/samba/smb.conf

```here is an example of my samba configuration file. **these are lines i've added to the smb.conf file:**

```

####################################################################
# My own junk I added to this file.
[Music]
comment = Shared Music
path = /home/d3v11/Music
read only = yes
available = yes
browseable = yes
public = yes
writable = no
guest ok = yes


[Downloads]
comment = Shared Downloads
path = /home/d3v11/Downloads
read only = yes
available = yes
browseable = yes
public = yes
writable = no
guest ok = yes

```make something similar with the correct paths and titles. these settings will allow anyone to access your samba shares on your local network. you can further tighten security by adding specific rules to your firewall like allowing 192.168.1.0/24. this samba config file is also capable of it's own security rules, example:

```

[Downloads]
comment = Shared Downloads
path = /home/d3v11/Downloads
read only = yes
available = yes
browseable = yes
writable = no
guest ok = yes
hosts deny = ALL
hosts allow = 192.168.1.4 127.0.0.1

```something like that will allow more tight security narrowing it down to a single ip.

just as a side note you may also want to right click the folder you're sharing in samba in nautilus and picking the right sharing options. also go into properties of the folder(s) like this and select the proper permissions and check the "apply permissions to enclosed files".

restart samba after editing the smb.conf file like so:
```

sudo /etc/init.d/samba restart

```

your windows machine should now be able to access your shares.

---

### Post by d3v1150m471c on 2010-10-23
you'll probably be interested in this link, too.
[URL="http://www.faqs.org/docs/securing/chap29sec284.html"]
http://www.faqs.org/docs/securing/chap29sec284.html[/URL]

---

### Post by xdominex on 2010-10-24
Thank you for your responses. No matter what I try with Samba (have used example settings such as the ones you posted, though I like yours better than most), it continues to have problems. I am running 10.10 and theorize that perhaps 10.10 is simply too new to have things such as compatibility with Samba worked out. Last night I tried the simple instructions for getting folders shared with Windows according to Ubuntu Help and Support, but Samba did not install correctly, so sharing with Windows was not an option as Ubuntu Help and Support claimed it would be. What I am going to try now is to revert to 10.04 and see if that makes a difference. If it works, would you mind answering a question or two if they come up and I can't easily find an answer via Google?

---

### Post by d3v1150m471c on 2010-10-24
i'll do what i can. i still use karmic koala ( 9.10 ) and it works like a charm. it may be a problem with w7 so you may want to direct you google search there. there are 3 pc's on my end and only 2 can access my samba shares. the 3rd computer simply can't but it's not mine so i don't want to go poking in it to find the solution. all three run vista and sometimes vista can have issues with samba. w7 may also.

btw can you post the output of this command:
```

cat /etc/samba/smb.conf

```

have you installed nautilus-share?
```

sudo apt-get nautilus-share

```

---

### Post by xdominex on 2010-10-25
Ok, I got rid of 10.10 in favor of 10.04, and now my Windows 7 computer sees my server computer just fine. I just have a couple of simple questions now that I can't seem to find any help for via Google.

What basic settings do you use in your smb.conf file to allow Windows users to read and execute files on the server?

Also, is there a way to get a login screen to pop up on my Windows computer that will automatically assign me to Guest if the login fails?

Thanks again for taking the time to address my issues. I very much appreciate it.

---

### Post by d3v1150m471c on 2010-10-25
if you scroll back up you'll see how i've established my samba shares. as far as executing them they'll need to be marked as executable. I don't believe samba has a means of executing them so in order to do this you'll probably have to resort to using vnc or ssh to remote into your ubuntu machine to launch them "server side".

The login guest question. I believe you can either choose guest or allowing a specific user. you could probably get away with allowing both but it sounds redundant to me to do so. I'd simply just allow a guest login if that's the case.

---

