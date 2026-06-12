---
title: "file sharing: &quot;unable to mount: failed to retrieve share list...&quot;"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by spencerownside on 2011-12-16
Hello - am looking for some help please. 
I am getting an error when trying to pull up my shared folders. The error in full is:
"Unable to mount location. Failed to retrieve share list from server". 
My desktop is ubuntu 11 and is where the files are stored. My laptop is also on ubuntu 11 and is the location that I am using to as the remote. 
When I go into my home folder, click browse network, it does say "Windows Network" (even though the desktop is not windows {i assume this is not the issue but mention none the less}); I open that and it goes to "workgroup". 
Clicking 'workgroup' is where i get my error. I have gotten the 'unable to mount' error from the 'browse network' like before - but in the vast majority of cases it is not until workgroup that i get the error. 
I'm not totally clear as to what samba is and what difference using that would make. 
I am not super new to ubuntu but am quite the terminal novice so be gentle please. 
thank you

---

### Post by N00b-un-2 on 2011-12-16
written for XFCE, but works in other desktops too.

[http://ubuntuforums.org/showthread.php?t=1891590&highlight=nonsense+networking]("http://ubuntuforums.org/showthread.php?t=1891590&highlight=nonsense+networking")

---

### Post by Morbius1 on 2011-12-16
From the laptop please post the output of the following command:
```
smbtree
```[COLOR=Blue]**BTW**[/COLOR], since you stated that both the server and the client are running Ubuntu 11, why are you posting in the Lubuntu sub-forum. If you are running Lubuntu let us know.

---

### Post by spencerownside on 2011-12-16
my best guess for why i posted here is that i moved the cursor by accident. I did go ahead and move the thread and relabel it appropriately under 'uduntu'. 
thanks for pointing out the mistake. 
how do i erase this thread? don't want to have a bunch of random posts floating around.

---

### Post by Morbius1 on 2011-12-16
The moderators will figure it out. The only reason I asked is because not everything you can do in Ubuntu can you do in Lubuntu. For example the HowTo mentioned above disables the ability to create a guest accessible Samba Usershare. It would be a problem for Ubuntu for sure, can be a problem for Xubuntu, but not so much for Lubuntu.

---

### Post by coffeecat on 2011-12-16
> **Morbius1 said:**
> The moderators will figure it out.

They have! :wink:

@spencerownside, I've changed the tag to "Ubuntu" for you. If you want the thread closed for any reason, please click on the report button and send a message to the staff with that.

---

### Post by Morbius1 on 2011-12-16
@coffeecat,
When did you become a moderator! You not going to hold against me all those terrible things I said to you are you?

@spencerownside,

I need to shut down for the day so let me leave you with this. 

92.48% ( I made that number up ) of all the "failed to retrieve.." errors are caused by these 4 problems:

[1] Services on the server (desktop) aren't running.

So start them:
```
sudo service smbd start
sudo service nmbd start
```[2] Firewalls are in the way.
If you haven't done anything to your firewalls then you're fine. If you have done something with it disable them. We can fix it later.

[3] Your hostname is too long.

Run the following command and count the number of characters:
```
hostname
```If it's 15 characters or less then you're good to go. If it's 16 characters or more then here's how to fix it:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```In the [global] section - right under the workgroup line - add the following line:
```
netbios name = something
```[COLOR=Blue]*"something" has to be 15 characters or less in length*[/COLOR]

[4] Rearrange the order of how samba resolves names to ip addresses by putting the on;ly method that works by default first. Again in the [global] section add the follwoing line:
```
name resolve order = bcast host lmhosts wins
```After you do [3] or [4] restart the samba services:
```
sudo service smbd restart
sudo service nmbd restart
```Wait 5 minutes - no kidding - and then see if your client (laptop) can access the server's shares.

You may need to do all of the above on the client as well.

---

### Post by spencerownside on 2011-12-16
Thank you for moving the thread coffeecat: and also thank you morbius for the help with the code stuff. Let me see if i can summarize what i did with the info some. 

I preface that it is entirely possible that I could have screwed some of this up, so its as much cut & paste as i could. 

First, I ran the samba sudo commands and my terminal code goes: 
```
spencer@spencer-media:~$ sudo service smbd start
[sudo] password for spencer: 
start: Job is already running: smbd
spencer@spencer-media:~$ sudo service nmbd start
start: Job is already running: nmbd
```I ran the firewall check code and got: 
```
spencer@spencer-media:~$ sudo ufw status
Status: inactive
```Checked my hostname (which is 13 characters long):
```
spencer@spencer-media:~$ hostname
spencer-media

```Ran the 'resolve' code: 
```
spencer@spencer-media:~$ name resolve order = bcast host lmhosts wins
No command 'name' found, did you mean:
 Command 'named' from package 'bind9' (main)
 Command 'namei' from package 'util-linux' (main)
 Command 'lame' from package 'lame' (universe)
 Command 'uname' from package 'coreutils' (main)
 Command 'nama' from package 'nama' (universe)
 Command 'mame' from package 'mame' (multiverse)
 Command 'nam' from package 'nam' (universe)
name: command not found

```Went ahead and restarted the Samba code:
```
spencer@spencer-media:~$ sudo service smbd restart
smbd start/running, process 8270
spencer@spencer-media:~$ sudo service nmbd restart
nmbd start/running, process 8282
spencer@spencer-media:~$ 
```I waited 5 minutes, tried again but still to no avail. I rebooted both the desktop and the laptop, tried again, this time though the error I am getting is: 

"DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered"

I read a couple different bug reports and am thinking that maybe its relevant that I'm using a partitioned drive. Ubuntu is the only installed OS, though the stored info for the network sharing is on the "storage" partition. I hope i stated that clearly and such. 

I don't know when, or even if, I should mention this, but I have an in-home studio with multiple other pcs around (only 1 has windows [xp at least]), and the eventual goal is to be able to freely swap from location to location. I only mention it in case it simplifies this process. My main focus right now is just 2 already mentioned units.

---

### Post by Morbius1 on 2011-12-17
"name resolve order = bcast host lmhosts wins" is not a command you run from the terminal:
> [4] Rearrange the order of how samba resolves names to ip addresses by  putting the on;ly method that works by default first. [COLOR=Blue]Again in the  [global] section add the following line:[/COLOR]
```
name resolve order = bcast host lmhosts wins 
```Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```And add the following line under the "workgroup" line in the [global] section:
```
name resolve order = bcast host lmhosts wins 
```And then restart samba:
```
sudo service smbd restart
sudo service nmbd restart

```

---

### Post by z06steve on 2011-12-22
This is awesome. 

I installed 11.10 about 2 wks ago and this was my 1 and only issue.  There is ALOT of info out there on this, but this is the only fix that worked for me, THANKS!

---

### Post by Tolossa on 2011-12-23
Morbius1,
After many attempts and many downloads I followed your commands above; you solved my problem.
I appreciate your help.
Keep up the good work, Is people like you that I admire in the Linux Community.
Merry Christmas & Happy New Year.

---

### Post by techknowledge on 2012-01-19
> **Morbius1 said:**
> @coffeecat,
When did you become a moderator! You not going to hold against me all those terrible things I said to you are you?

@spencerownside,

I need to shut down for the day so let me leave you with this. 

92.48% ( I made that number up ) of all the "failed to retrieve.." errors are caused by these 4 problems:

[1] Services on the server (desktop) aren't running.

So start them:
```
sudo service smbd start
sudo service nmbd start
```[2] Firewalls are in the way.
If you haven't done anything to your firewalls then you're fine. If you have done something with it disable them. We can fix it later.

[3] Your hostname is too long.

Run the following command and count the number of characters:
```
hostname
```If it's 15 characters or less then you're good to go. If it's 16 characters or more then here's how to fix it:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```In the [global] section - right under the workgroup line - add the following line:
```
netbios name = something
```[COLOR=Blue]*"something" has to be 15 characters or less in length*[/COLOR]

[4] Rearrange the order of how samba resolves names to ip addresses by putting the on;ly method that works by default first. Again in the [global] section add the follwoing line:
```
name resolve order = bcast host lmhosts wins
```After you do [3] or [4] restart the samba services:
```
sudo service smbd restart
sudo service nmbd restart
```Wait 5 minutes - no kidding - and then see if your client (laptop) can access the server's shares.

You may need to do all of the above on the client as well.

Either Rearranging the name resolve order fixed my issue or adding a netbios name or a combination of both has fixed this new Oneiric Ocelot Sharing issue

---

### Post by jfca283 on 2012-12-08
i'm hsving the same issue described here. My PC with 11.10 using samba can't access to my notebook using 12.04 also using samba. I tried everything here explained and nothing.

---

