---
title: "How to allow guest access to samba share in Jaunty using nautilus"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by psypher on 2009-06-07
hi all, i've been having an issue since installing jaunty. From what i can remember I didn't have to make any changes in Intrepid to get this working as expected.

Trying to setup a samba share with complete guest access using the share tool in nautilus, but no matter what the permissions are i cannot open the share in windows (get a permission denied error) and in ubuntu i get unable to mount location. If i setup the share with authentication it works fine.


am i missing something? please don't flame me for not looking around I have looked around. All the howto's talk about setting up the smb.conf file as well as your shares in there. I know how to do that but I don't want to do that anymore I want this share tool to work as it should. 

For interest sake I have tried using smb.conf and still does not work, set security = share and share:

[test]
  comment = test
  path = /home/psypher/Downloads/Cisco
  guest ok = yes
  read only = no
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

permissions on folder and files are 777

Thanks

---

### Post by superprash2003 on 2009-06-08
hope this helps [http://www.prash-babu.com/2008/07/samba-share-folders-or-files-without.html](http://www.prash-babu.com/2008/07/samba-share-folders-or-files-without.html)

---

### Post by swerdna on 2009-06-08
I think by the "share tool" you mean in Nautilus you R-click and select Sharing Options. If so then: The share tool in Nautilus installs the newer style of share called "usershares". These are structurally different from the classical shares we are used to seeing in the Samba config file.

So with both styles of share operating on the same folder you might have a conflict. The configuration file for the "usershare" called "test" is located at /var/lib/samba/usershares/test, not in smb.conf. So removing the spurious entry from smb.conf will allow the "usershare" enabled in Nautilus to operate unhindered. Then it will work.

{the structure you have for the stanza [test] in smb.conf is incorrect for guest access, so you should remove it anyway}

For an explanation of the difference between "usershares" and "classical" Samba shares, have a look here: [Samba: Practical Introduction to Linux Usershares on openSUSE]("http://www.swerdna.net.au/linhowtousershares.html")

---

### Post by psypher on 2009-06-08
I understand the difference between the 2. I didn't have both turned on, on the same folder at the same time. Installed jaunty, installed samba, created guest share, using usershares, does not work, turned off usershare, created config in smb.conf on same share, still does not work. Copied the config from my working config on my intrepid server.

tried that other config, added guest account = nobody and changed the share settings as follows:

[test]
  comment = test
  path = /home/psypher/Downloads/Cisco
  guest ok = yes
  browseable = yes
  read only = no
#  create mask = 0777
#  directory mask = 0777
#  force user = nobody
#  force group = nogroup

still does not work

Found a way to make it work though. removed the security = share line, changed guest account = psypher. guest config in smb.conf works now. removed the config in smb.conf and setup usershare, still works. 

is this the correct way to do it? just confused as i have the same smb.conf file on intrepid but on there the guest line is commented out as follows:

;   guest account = nobody
and guest access works perfectly

thanks

---

### Post by swerdna on 2009-06-08
Ok, let's focus on classical style of shares.

Turn usershares off on the directory /home/psypher/Downloads/Cisco. Don't have both the stanza in smb.conf and the Nautilus sharing tool active on directory "cisco" at the same time. [I think you understand that but I reiterate it in case you didn't get it].

Next, remove the line: guest account = psypher

Then in smb.conf put this:
[LIST=1]
[*]In the [global] stanza put this:
```
map to guest = bad user
security = user
```
[*]In the [test] stanza put this:
```
[test]
comment = test
path = /home/psypher/Downloads/Cisco
guest ok = yes
force user = psypher
```
[/LIST]

chmod the permissions to drwxr-x--- or drwxr-xr-x, either will work. You can use: ```
sudo chmod -R 750 /home/psypher/Downloads/Cisco

or use 755, whichever you prefer
```
And make the files back to the correct Linux owner with this:```
sudo chown -R psypher:users /home/psypher/Downloads/Cisco
```

If you have a firewall running, turn it off pro tem (so as not to have too many things complicating the diagnosis).

Then restart the Samba daemons with this command:
```
sudo /etc/init.d/samba restart
```

Then if it doesn't work, post here the contents of smb.conf.

For many different configs for shares see this reference: [HowTo Configure a Professional File Server on a SOHO LAN]("http://www.swerdna.net.au/linhowtosambaserver.html")
In particular, look at the segment titled: [Part II: Defining and Using File Shares (Services)]("http://www.swerdna.net.au/linhowtosambaserver.html#shares")

---

### Post by swerdna on 2009-06-08
And an afterthought: the "permissions denied" response on a windows machine can come from not having the workgroup names the same in windows and Linux or from having other constraints in the [global] stanza.

But try the above post first.

---

### Post by fa1thful on 2009-12-01
I know i'm resurrecting an old thread but i don't care.

I registered just to say this, I love you swerdna!  <3  Thank you so much for posting this!  This is exactly what I needed and I was getting really frustrated with not being able to figure it out.  So THANK YOU again!!!!!

> **swerdna said:**
> Ok, let's focus on classical style of shares.

Turn usershares off on the directory /home/psypher/Downloads/Cisco. Don't have both the stanza in smb.conf and the Nautilus sharing tool active on directory "cisco" at the same time. [I think you understand that but I reiterate it in case you didn't get it].

Next, remove the line: guest account = psypher

Then in smb.conf put this:
[LIST=1]
[*]In the [global] stanza put this:
```
map to guest = bad user
security = user
```
[*]In the [test] stanza put this:
```
[test]
comment = test
path = /home/psypher/Downloads/Cisco
guest ok = yes
force user = psypher
```
[/LIST]

chmod the permissions to drwxr-x--- or drwxr-xr-x, either will work. You can use: ```
sudo chmod -R 750 /home/psypher/Downloads/Cisco

or use 755, whichever you prefer
```And make the files back to the correct Linux owner with this:```
sudo chown -R psypher:users /home/psypher/Downloads/Cisco
```If you have a firewall running, turn it off pro tem (so as not to have too many things complicating the diagnosis).

Then restart the Samba daemons with this command:
```
sudo /etc/init.d/samba restart
```Then if it doesn't work, post here the contents of smb.conf.

For many different configs for shares see this reference: [HowTo Configure a Professional File Server on a SOHO LAN]("http://www.swerdna.net.au/linhowtosambaserver.html")
In particular, look at the segment titled: [Part II: Defining and Using File Shares (Services)]("http://www.swerdna.net.au/linhowtosambaserver.html#shares")

---

### Post by swerdna on 2009-12-01
I'm delighted by your happiness

---

### Post by tc0nn on 2012-07-12
Works for me too! Using Centos5.8 with hadoop-hdfs and cifs. Thanks swerdna

---

### Post by wildmanne39 on 2012-07-12
Old thread closed.

---

