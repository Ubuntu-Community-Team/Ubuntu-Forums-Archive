---
title: "Connecting to and mapping a windows network drive"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by Prometheus418 on 2012-06-27
Hello-

I'm new to Ubuntu, and while I've been able to figure out most things, I've got one final puzzle piece to get in place.

I use a personal laptop alongside my CAD machine at work, and from time to time, I need to access the network drives (which are on a windows 2003 server.) to pull up specs or customer prints while I am designing components.

I've done what seems like endless searches on how to access a network drive, and in every case, the articles are apparently assuming a level of user-savvy that I don't have with Ubuntu yet.  I have managed to RDP easily, and I have the VPN set up and am able to see the network, just not access our company filesystem.

Ideally, I'd like to map the network drives and set them as folders in the /home file rather than as drive letters.  They don't need to be on all the time, but it couldn't hurt if they were. I think I have read most of the articles on how to do this, but it seems as though the more common issue is configuring a Linux server to accept connections from a Windows system, and I need that to run the opposite direction.  There's little chance of getting the owners to switch to a Linux server, so that is off the table for the time being.  

Currently, when I use this setup in Win7, I connect to the network on the wireless router and then start the VPN to the server to access the shared drives.  This is also the method I use from home.  I am trying to set up my system to dump Windows entirely on my laptop, but this is the one last thing that I must have working to do so- currently, I have to either e-mail files to myself or dual-boot just to grab files off the the network, and then pull them from the Windows file system, which is actually in violation of our QMS (network files are supposed to stay on the network for revision control.)

I have a feeling that someone has already solved this, and if anyone could give me a hand getting it up and running, I would really appreciate it.

---

### Post by mikewhatever on 2012-06-28
To access a Windows share, just open a file browser and click Network in the left panel. An alternative would be to hit Ctrl-l to show the address bar, and type the location, for example, smb://10.10.0.100/share1, or smb://server_name/share2. Once inside the shared folder, you can bookmark the location (Ctrl-d).

---

### Post by Prometheus418 on 2012-06-28
Sounds like I'm almost there, but there's a sticking point.

When I do what you've described above, there is a printers folder and a Windows_Share on the work server.  I can access printers fine- but the Windows_Share prompts for a user name and password.

The defaults that appear in the login box are my Ubuntu username, and the correct work workgroup.  After correcting the username and entering the network password, I get a popup with the error "Unable to mount location -- Failed to mount Windows share."

I am using the default file browser that comes with Ubuntu 12.04- is there some way to configure the file browser itself to force it to use an alternate username for Windows shares?  I have seen a similar situation before caused by logging into a local machine with a username that does not match my network name and pass, and the workaround was to change the username to //<domain>/<username> when mapping the shared drive.  That doesn't seem to work here, but is there a file that stores preferences of some kind where I can set my username and domain for the file browser?  I would be willing to install an alternate browser if required to make this option available.

I am guessing that changing my system name/pass on a global level would break other things locally, and if at all possible, I would prefer to avoid creating a new user profile and reinstalling everything so that my Ubuntu login matches the network one- and I'm not even sure that that method would work, as the Windows server probably would not validate the name and pass correctly cross-platform. 

Thanks for your help- at least now I know that I am pointing the right direction, and not missing an entire software package or something.

---

### Post by mikewhatever on 2012-06-28
Hm..., you shouldn't need to change anything on the system level, not sure why it wouldn't connect. As for remembering the credentials, in the file browser, try File->Connect to Server, and add a bookmark from there.

---

### Post by Prometheus418 on 2012-06-28
Well, still no luck- but I'll keep monkeying with the settings.  If anyone else has any ideas, I'm open to trying just about anything.

Odds are at this point, it's a translation error- I found that with keymapping, when I had no idea what the <primary> and <super> keys were.

---

### Post by bab1 on 2012-06-29
> **Prometheus418 said:**
> Well, still no luck- but I'll keep monkeying with the settings.  If anyone else has any ideas, I'm open to trying just about anything.

Odds are at this point, it's a translation error- I found that with keymapping, when I had no idea what the <primary> and <super> keys were.


It would help if we could see your *smb.conf* file.  Post the output of ```
cat /etc/samba/smb.conf
```...and what Ubuntu users you have added to the Samba user database.  Please post the output of ```
sudo pdbedit -L
```Does this match your Ubuntu login (username)?  Does your Windows user match your Ubuntu and Samba user names?  Its *very* helpful that all 3 be the same.

---

### Post by Prometheus418 on 2012-07-04
[global]
    ; General server settings
    netbios name = [www.xxxxx-xxxxx.com](www.xxxxx-xxxxx.com)
    workgroup = XXXXXXXXXX
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = wins lmhosts hosts bcast

# WINS SETTING
# NEVER set "wins support = yes" on more than one machine in your network
# "wins support = yes" and the "wins server xxx.xxx.xxx.xxx" option are mutually exclusive; you cannot simultaneously offer Samba as the WINS server and point to another system as the server

#   wins support = no
# or (not both)
    wins server XX.XXX.XXX.XXX (Our server IP)

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[SHARED_FOLDER]
    path = \\XXXXXXXX\XXXXXXXXX
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = XXXXXXXXXXXXXX	
    force group = XXXXXXXXXXXX

Sorry about the XXXXXXXs- we do have some files on the work network that are private enough that I'd rather not reveal the server location or file structure- I'm sure you can understand.

Force group is set to the same name as the workgroup

All usernames are not the same, unfortunately.  While I don't really worry about it too much on a forum like this, part of the point of making this Windows to Ubuntu switch is to protect at least some of my privacy.  My employer assigns usernames with our names, but I have a more anonymous username on the Linux machine.

Force user is set to the login name assigned by work, which is what I use to login to the system I am trying to access.

I do have a workaround that is operating ok for now, using the work FTP rather than mapped drives, but it would be nice to make this happen.

---

### Post by cipherboy_loc on 2012-07-04
If ftp works, you can look into curlftpfs, which should give you the ability to mount a FTP server like a SMB drive.


Cipherboy

---

### Post by bab1 on 2012-07-04
> **Prometheus418 said:**
> [global]
    ; General server settings
    netbios name = [www.xxxxx-xxxxx.com](www.xxxxx-xxxxx.com)
[COLOR="Blue"]...^^^ The should not be a FQDN nor more than 15 characters
You are working with a name for this host only[/COLOR]> 
    workgroup = XXXXXXXXXX
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
[COLOR="Blue"]... ^^^ This is the file you use to map Samba users to Windows users.[/COLOR]> 
    name resolve order = wins lmhosts hosts bcast

# WINS SETTING
# NEVER set "wins support = yes" on more than one machine in your network
# "wins support = yes" and the "wins server xxx.xxx.xxx.xxx" option are mutually exclusive; you cannot simultaneously offer Samba as the WINS server and point to another system as the server

#   wins support = no
# or (not both)
    wins server XX.XXX.XXX.XXX (Our server IP)
You have a working WINS server (not this host)?> 

 ...

[SHARED_FOLDER]
    path = \\XXXXXXXX\XXXXXXXXX
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = XXXXXXXXXXXXXX	
    force group = XXXXXXXXXXXX

Sorry about the XXXXXXXs- we do have some files on the work network that are private enough that I'd rather not reveal the server location or file structure- I'm sure you can understand.
Not really, but it's your system.  Even in my least secure installations I never use hostnames or share names that can positively ID my network or the shares that are available in it.  > 

Force group is set to the same name as the workgroup
Why do that?  The term WORKGROUP has nothing to do with the group you are forcing.> 

All usernames are not the same, unfortunately.  While I don't really worry about it too much on a forum like this, part of the point of making this Windows to Ubuntu switch is to protect at least some of my privacy.  My employer assigns usernames with our names, but I have a more anonymous username on the Linux machine.

Then you need to map them in /etc/samba/smbusers> 

Force user is set to the login name assigned by work, which is what I use to login to the system I am trying to access.
And this gets you ...?> 

I do have a workaround that is operating ok for now, using the work FTP rather than mapped drives, but it would be nice to make this happen.
Good deal.  If you want the transparency of mapped drives from on host to another then you will have to work out the permissions of users and groups along with the authentication of those entities.

I'm being general in my comments as this is all I have to work with.  You will have to work out the details.

---

### Post by Prometheus418 on 2012-07-05
Sounds like you know your stuff...

I suspect that there are two things working against me here- first, I come from a Windows background, and am probably not getting the translation right- for instance, when there is a field that says "force group"  my inclination is to assume that that is allowing me to change the name of the workgroup or domain that the system is using to connect- for instance, my local login might be delld630/user123 and I need to login to the work network as workserver/jjsmith.

Is there some source material you could direct me to where I could study what the networking terms in Linux mean?  That might be all I need to figure it out on my own.  I'm usually fairly sharp with this stuff, but there's a lot to learn here.

The other problem is that the company owner is also the sysadmin, so any arguments about security are... uncomfortable at best.  He's not unreasonable, but it sometimes takes longer than than it otherwise would to get things changed.  Generally speaking, the engineering department just needs to do whatever we can in the framework he's established, and leave it at that.  I'm sure I could take control of the server in about 15 min and change things to my liking, but it's not really my job, and definitely not worth getting canned over.

It sounds like he's going to let me take over FTP server admin, though, so the other solution proposed (curlftpfs) might be the way to go anyway- I always prefer to use things that I can control.

Thanks for taking the time to help- and if you do have a direction you could point me in for a primer in Linux networking, I'll be sure to study up a bit.  Right now it's still kind of like wandering around in a foreign country where I don't know the local language, but I'm starting to get the hang of it a little.

---

### Post by msammels on 2012-07-05
Try [this](http://www.ee.surrey.ac.uk/Teaching/Unix/) and [this](http://www.linux4beginners.info/node/linuxnetworking) :)

And never be afraid to ask, we're all here to help.

---

### Post by bab1 on 2012-07-05
First let me say that as a network admin, I think of networking as *connectivity *(IP addressing, DNS, routing protocols, etc.).    Linux (user, group and others file and directory permissions) or Samba (WORKGROUP or domain) are a different topic.  They may use the same words but the meaning is completely different.

We need to make sure we are both talking about the same thing. 

> **Prometheus418 said:**
> Sounds like you know your stuff...

I suspect that there are two things working against me here- first, I come from a Windows background, and am probably not getting the translation right- for instance, when there is a field that says "force group"  my inclination is to assume that that is allowing me to change the name of the workgroup or domain that the system is using to connect- for instance, my local login might be delld630/user123 and I need to login to the work network as workserver/jjsmith.
This is incorrect in the context of Samba or Linux permissions.  The reference is to the group ownership of the file or directory created, not the domain.  FYI the WORKGROUP in samba (or Windows sharing is only for visual association (how they are grouped in "Network Neighborhood). > 

Is there some source material you could direct me to where I could study what the networking terms in Linux mean?  That might be all I need to figure it out on my own.  I'm usually fairly sharp with this stuff, but there's a lot to learn here.
Start [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.samba.org/samba/docs/") for Samba doc's.  [**_[COLOR="Blue"]Here[/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") is the man page for the smb.conf file (look for "force group")> 

The other problem is that the company owner is also the sysadmin, so any arguments about security are... uncomfortable at best.  He's not unreasonable, but it sometimes takes longer than than it otherwise would to get things changed.  Generally speaking, the engineering department just needs to do whatever we can in the framework he's established, and leave it at that.  I'm sure I could take control of the server in about 15 min and change things to my liking, but it's not really my job, and definitely not worth getting canned over.
Right now that sounds like a scary thought.  :-)  You don't know what you "don't know".> 

It sounds like he's going to let me take over FTP server admin, though, so the other solution proposed (curlftpfs) might be the way to go anyway- I always prefer to use things that I can control.

Thanks for taking the time to help- and if you do have a direction you could point me in for a primer in Linux networking, I'll be sure to study up a bit.  Right now it's still kind of like wandering around in a foreign country where I don't know the local language, but I'm starting to get the hang of it a little.
...^^^  Not networking -- it's Linux System Admin.  Networking is either connectivity of hosts, or Facebook.  I'll choose the former over the latter.  I think the previous post provided network connectivity for you.  If you want Linux System Admin you can start [**_[COLOR="Blue"]here[/COLOR]_**]("https://www.google.com/search?q=Linux+System+Admin&btnG=Go!").

---

### Post by Morbius1 on 2012-07-05
I'm getting a little confused here and I really should stay out of this since I'm strictly a home lan kind of guy but we are trying to access someone else's share correct?

If you run a command that looks something like this:
```
nautilus smb://DOMAIN-NAME;user-name:password@ip_address/Share
```Is this where you are getting the "Unable to mount location -- Failed to mount Windows share." error?

---

### Post by bab1 on 2012-07-05
> **Morbius1 said:**
> I'm getting a little confused here and I really should stay out of this since I'm strictly a home lan kind of guy but we are trying to access someone else's share correct?

If you run a command that looks something like this:
```
nautilus smb://DOMAIN-NAME;user-name:password@ip_address/Share
```Is this where you are getting the "Unable to mount location -- Failed to mount Windows share." error?

All are welcome to pile on.  :D

It's a LAN situation (maybe).  See here```
security = user
```
...no domain, no AD.

The OP is confusing Windows terms with Linux terms.

---

### Post by Morbius1 on 2012-07-05
THe thing that confued me was this:
> [SHARED_FOLDER]
    path = \\XXXXXXXX\XXXXXXXXX
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = XXXXXXXXXXXXXX    
    force group = XXXXXXXXXXXXAnd this:
> Force user is set to the login name assigned by work, which is what I use to login to the system I am trying to access.It almost looks like an attempt to create a share on the client of someone else's share ( the double backslashes in the path implied a network address ) and you know how easily confused I get :D

[COLOR=Blue]**EDIT**[/COLOR]: So can I assume he's running the equivalent of this and getting a permissions error:
```
nautilus smb://WORKGROUP;user-name:password@ip_address/Share
```And he's using the user name and password expected of him from the Windows server?

---

### Post by bab1 on 2012-07-05
> **Morbius1 said:**
> THe thing that confued me was this:
And this:
It almost looks like an attempt to create a share on the client of someone else's share ( the double backslashes in the path implied a network address ) and you know how easily confused I get :D

Nope.  He doesn't understand the "force user" or "force group" parameters in the smb.conf file.  He thought you could map the Windows user and the domain with those.  ;-)

It's his local network (admin'd by his boss, the owner).

---

### Post by Morbius1 on 2012-07-06
The reason I wanted clarification is because of this error message:
> After correcting the username and entering the network password, I get a  popup with the error "[COLOR=Blue]Unable to mount location -- Failed to mount  Windows share[/COLOR]."That's not the server rejecting the passed credentials or he would have received an access denied type of error and the client would be in an infinite loop of being prompted for user name and password.

An "unable to mount location" usually means the path to the folder being shared doesn't exist ( a mistake easily accomplished on a Linux Samba server ) or at least doesn't exist to that user ( on a Linux server it would be because the Linux file permissions on the shared folder or the path to that folder does not allow that user any access ). 

Is it possible that on the Windows server the remote user and his password are legitimate but the NTFS permissions on the Windows directory itself is not allowing any access to that user?

---

### Post by bab1 on 2012-07-06
> **Morbius1 said:**
> The reason I wanted clarification is because of this error message:
That's not the server rejecting the passed credentials or he would have received an access denied type of error and the client would be in an infinite loop of being prompted for user name and password.

An "unable to mount location" usually means the path to the folder being shared doesn't exist ( a mistake easily accomplished on a Linux Samba server ) or at least doesn't exist to that user ( on a Linux server it would be because the Linux file permissions on the shared folder or the path to that folder does not allow that user any access ). 

Is it possible that on the Windows server the remote user and his password are legitimate but the NTFS permissions on the Windows directory itself is not allowing any access to that user?

I don't think any of that matters as long as the OP is misnaming the SMB share.  Earlier he was using this format```
//<domain>/<username> 
```... and that's clearly wrong.  The Samba server is clearly not configured correctly either.

I think the Samba server is not responding and therefore the client pops up the message.  In any event when server is configured and the correct login is tried it all should work.

---

### Post by cipherboy_loc on 2012-07-06
Why doesn't he just use fstab? 

```

//<ip or hostname>/<directory> /path/to/share cifs users,user=user,password=password,uid=1000,gid=1000,noauto

```Then to mount, just run: 
```

mount //<ip or hostname>/<directory>

```And you are set.


Cipherboy

---

### Post by Prometheus418 on 2012-07-08
> **msammels said:**
> Try [this](http://www.ee.surrey.ac.uk/Teaching/Unix/) and [this](http://www.linux4beginners.info/node/linuxnetworking) :)

And never be afraid to ask, we're all here to help.

Excellent- that's right along the lines of what I was looking for.  I've got better than 20 years in on Windows, and more like 20 days with Linux.  Sometimes that stuff that seems easy to a person who has been using it for a while doesn't get communicated (though for the most part, I have to give you folks a lot of credit- the whole system, including support, has really improved since the last time I checked it out in 1997.)

---

### Post by Prometheus418 on 2012-07-08
> **bab1 said:**
> First let me say that as a network admin, I think of networking as *connectivity *(IP addressing, DNS, routing protocols, etc.).    Linux (user, group and others file and directory permissions) or Samba (WORKGROUP or domain) are a different topic.  They may use the same words but the meaning is completely different.

We need to make sure we are both talking about the same thing. 


This is incorrect in the context of Samba or Linux permissions.  The reference is to the group ownership of the file or directory created, not the domain.  FYI the WORKGROUP in samba (or Windows sharing is only for visual association (how they are grouped in "Network Neighborhood). Start [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.samba.org/samba/docs/") for Samba doc's.  [**_[COLOR="Blue"]Here[/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") is the man page for the smb.conf file (look for "force group")Right now that sounds like a scary thought.  :-)  You don't know what you "don't know".
...^^^  Not networking -- it's Linux System Admin.  Networking is either connectivity of hosts, or Facebook.  I'll choose the former over the latter.  I think the previous post provided network connectivity for you.  If you want Linux System Admin you can start [**_[COLOR="Blue"]here[/COLOR]_**]("https://www.google.com/search?q=Linux+System+Admin&btnG=Go!").

Lots to dig through here, and that's just fine by me.  It'll take some time before I can really make a sensible reply to what you've got above, but I am reading through it with the links, and it looks as though everything I'm trying to configure is there, so now it's just a matter of sifting and tweaking with the manuals open in another monitor.

That's ok, though- overall, this has been more interesting than frustrating, and I am still able to move files in the interim.

---

### Post by Prometheus418 on 2012-07-08
> **Morbius1 said:**
> I'm getting a little confused here and I really should stay out of this since I'm strictly a home lan kind of guy but we are trying to access someone else's share correct?

If you run a command that looks something like this:
```
nautilus smb://DOMAIN-NAME;user-name:password@ip_address/Share
```Is this where you are getting the "Unable to mount location -- Failed to mount Windows share." error?


Not exactly, but very similar.  I am using the GUI more.  Going off what I found on my own, the initial process was quite a bit more convoluted, and my lack of familiarity with linux generally makes it harder to remember each step.

What you've got there looks very promising, though- when it comes right down to it, even though I'll eventually want to be able to do linux sysadmin stuff, for the time being what I am trying to achieve is just mapping (mounting?) a Windows drive located on a Windows2003 server so that it is easy to access the server drive, and either open documents directly or cut and paste onto my linux laptop.  Generally speaking, this just means opening .pdf files from the server because our CAD software (Solidworks) does not support Linux (and even if it did, I'm not inclined to run it on an underpowered laptop with a smaller screen when I've got nice CAD systems at both work and home.)

When I'm at work, I am connected to the local network via wireless, and connect to the work server using VPN prior to mapping the drive.  The wireless network and the hardwired networks do not behave the same- each desktop that is hardwired has it's own account on the server and a fixed IP.  It used to be configured so that any machine on the local wireless could access the network folders, but I did demonstrate to the boss why that was a bad idea, by logging into the system folders from an account without a password from the parking lot, so that hole has been closed.  I could bypass the use of VPN while at work, but it would involve setting up my personal machine so that it authenticated off the work server, and I don't want to do that- it's my computer, not theirs.

VPN runs off my username and password- I have an account on the server that is authorized for remote access, and it doesn't matter what machine that access is used from.  I do already have VPN set up on the linux machine, and it seems to be working fine- I can access the server in Nautilus, by selecting browse network and then accessing the server, but it only allows me to browse into the printer$ folder.  While I don't (legitimately) have full access to the system, I do have a lot of read/write access permissions, so I should be able to get further than that.

When I try to access "Shared folder," it prompts me for a username and password.  The username that autofills is incorrect, but the Domain is correct.  I am operating under the assumption that this works in a manner similar to windows, where domain is the location where the user is stored, so the full login is actually domain/username.  

After correcting the username and entering the password, a dialog box pops up that says "unable to mount location- Failed to mount windows share."  If I type in the wrong password, it simply returns me to the login window, so I have been assuming that it is accepting my username and password.

I have a feeling that at this point, it's close enough that it's probably some single command-line that I'm missing, but as another poster said, the problem is that I don't know what I "don't know."

So rather than filling in with XXXXXXX... perhaps it would make sense to fill in the file structure I'm trying to access with bogus IP and names, and you could tell me how you would tackle this.

Server side:

Username: bobsmith
Password: 12345
Server IP address: 234.232.222.12
HTTP Domain: [www.bobs-work.com](www.bobs-work.com)
NT domain: bobswork
File structure:
/bobswork
.../locationone
...../serverone
......./customers
......./engineering
......./specs
.../locationtwo
...../servertwo
......./customers
......./engineering
......./specs

Local side:

Linux login: linux
Linux pass:  ubuntu

When using VPN from my windows machine, the server does not show up in my network locations.  To access the shared drives on the server, I have always used Map Network drive, and then entered the address I am accessing manually.  For example, if I wanted to access "engineering" I would enter //locationtwo/servertwo/engineering directly, set the drive letter and save the location.  Trying to browse the network has never worked, unless the machine is directly connected to the system.

And maybe that is where it is falling down- it sounds as though it may be possible to do something similar in nautilus.  How would I enter the location as noted above, and assign it a mount point somewhere like the home folder?  I see you've got some code, but it did not work in terminal, and I have no idea where I would enter it in Nautilus.

---

### Post by Prometheus418 on 2012-07-08
> **Morbius1 said:**
> The reason I wanted clarification is because of this error message:
That's not the server rejecting the passed credentials or he would have received an access denied type of error and the client would be in an infinite loop of being prompted for user name and password.

An "unable to mount location" usually means the path to the folder being shared doesn't exist ( a mistake easily accomplished on a Linux Samba server ) or at least doesn't exist to that user ( on a Linux server it would be because the Linux file permissions on the shared folder or the path to that folder does not allow that user any access ). 

Is it possible that on the Windows server the remote user and his password are legitimate but the NTFS permissions on the Windows directory itself is not allowing any access to that user?

It works through windows, but as noted in my much longer post just above, it's never been a situation where you could browse the entire server.  There is a point where I am allowed to access, and can browse anything downstream from that.  The easiest way to do that has always been to map a drive to my highest level folder, and browse to location from there.

---

### Post by Morbius1 on 2012-07-08
> When I try to access "**Shared folder**," it prompts me for a username and  password.  The username that autofills is incorrect, but the Domain is  correct.  I am operating under the assumption that this works in a  manner similar to windows, where domain is the location where the user  is stored, so the full login is actually domain/username.Let's make something clear. Trying to access this share will not work:
> [SHARED_FOLDER]
    path = \\XXXXXXXX\XXXXXXXXX
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = XXXXXXXXXXXXXX    
    force group = XXXXXXXXXXXXIf that's where you are getting the "Failed to mount Windows share" then that makes sense.

The path should point to a local directory on your Linux machine because that is the one you want to share to someone else not a network path to the Windows Server. 

You don't map network shares through smb.conf. You create shares in smb.conf for someone else to access.

---

### Post by Prometheus418 on 2012-07-08
> **cipherboy_loc said:**
> Why doesn't he just use fstab? 

```

//<ip or hostname>/<directory> /path/to/share cifs users,user=user,password=password,uid=1000,gid=1000,noauto

```Then to mount, just run: 
```

mount //<ip or hostname>/<directory>

```And you are set.


Cipherboy

I have a very good reason for not doing that... simply put, I don't know how.  

I did try it in the terminal, and got this:

bash: //(IP)/path/path: No such file or directory.

I tried a few different variations, but all had the same result- I did verify that the paths and ip addresses I used were correct, it's just not finding it.

---

### Post by cipherboy_loc on 2012-07-09
First line has to be put in /etc/fstab as the last line. 

Cipherboy

---

### Post by alcapone-g on 2013-03-04
Your windows share is not set up for the folder you try to access.

---

