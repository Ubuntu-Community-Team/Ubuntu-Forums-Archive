---
title: "Accessing smb shares off windows"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by fungihead on 2009-04-24
now i know i can mount filesystems but it would be nice to just click places > network > WORKGROUP and be able to see all the shared computers with the folders and files inside them.

but for the life of me i cant, and i never ever have been able to with linux, its probably the only keeping me on windows.

i open places, click "windows network" and it opens and shows "WORKGROUP". i click that and all i get is "unable to mount location, failed to recieve share list from server"

when googling i see other people with this problem, but no solutions

Ubuntu 9.04 Gnome on Asus EEE PC 901

---

### Post by fungihead on 2009-04-25
bump

---

### Post by Iowan on 2009-04-25
Seems like it _did_ work that way back before Hardy (when gvfs came to play). This Gutsy machine would do what you describe... until I replaced my dial-up modem/firewall/dns-server with a DSL modem.

---

### Post by inobe on 2009-04-25
> **fungihead said:**
> bump

hi

lets assume we are starting from scratch as i haven't the foggiest idea what changes you made !

follow steps 1 to 11 under **"Sharing folders via the Shared Folders application"**

then steps 1 to 6 under **"Accessing shared folders via Windows"**

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

the steps maybe specific for 8.10 but shouldn't matter much in 9.04.

if your fast enough and don't make mistakes you should have an accessible network both ways in ten minutes.

enjoy

---

### Post by DenysT on 2009-04-25
> **fungihead said:**
> now i know i can mount filesystems but it would be nice to just click places > network > WORKGROUP and be able to see all the shared computers with the folders and files inside them.

but for the life of me i cant, and i never ever have been able to with linux, its probably the only keeping me on windows.

i open places, click "windows network" and it opens and shows "WORKGROUP". i click that and all i get is "unable to mount location, failed to recieve share list from server"

when googling i see other people with this problem, but no solutions

Ubuntu 9.04 Gnome on Asus EEE PC 901


Having struggled through this in 8.10 I finally decided to start over in 9.04 and this is how I got everything to work without the dreaded "failed to retrieve" error.

Open a terminal window.
Applications -> Accessories -> Terminal

Type in "sudo gedit /etc/samba/smb.conf" without the quotes (you'll have to enter your password)

In the conf file find the line *workgroup = WORKGROUP*

If your Windows workgroup (My Computer (right click) -> Properties - Computer Name tab has this info) is different change the line to read workgroup = YOURWORKGROUPNAME

Next scroll down a few lines until you find the line *name resolver order = lmhosts hosts wins bcast *and delete the semicolon at the beginning of the line.

Save the changes and exit. Reboot. I don't know that rebooting is necessary but I'm still having to unlearn Windows and learn a real OS again. :P When you next go to Places - > Network you should see the network workgroup and computers attached to it. From there you can open/connect to a computer and see it's shares. It's not like XP where you just have a list of all shares in My Network Places but at least you can see them. This worked for me on 2 clean installs of 9.04, hope it works for you.

---

### Post by Grimmy on 2009-04-26
> **DenysT said:**
> Having struggled through this in 8.10 I finally decided to start over in 9.04 and this is how I got everything to work without the dreaded "failed to retrieve" error.

Open a terminal window.
Applications -> Accessories -> Terminal

Type in "sudo gedit /etc/samba/smb.conf" without the quotes (you'll have to enter your password)

In the conf file find the line *workgroup = WORKGROUP*

If your Windows workgroup (My Computer (right click) -> Properties - Computer Name tab has this info) is different change the line to read workgroup = YOURWORKGROUPNAME

Next scroll down a few lines until you find the line *name resolver order = lmhosts hosts wins bcast *and delete the semicolon at the beginning of the line.

Save the changes and exit. Reboot. I don't know that rebooting is necessary but I'm still having to unlearn Windows and learn a real OS again. :P When you next go to Places - > Network you should see the network workgroup and computers attached to it. From there you can open/connect to a computer and see it's shares. It's not like XP where you just have a list of all shares in My Network Places but at least you can see them. This worked for me on 2 clean installs of 9.04, hope it works for you.

I am having a similar issue with my Eee 701 4G with 9.04.   

I have a 9.04 server which I have my media files on.  (It was on 8.10 but I did a dist-upgrade).  

My Windows 7 and XBMC can both see the share fine.  The Eee hasn't been able to access it since I upgraded the server (on both 8.10 and 9.04).

I checked the smb.config on the server and it was already uncommented, but it didn't have lmhosts, just the rest.   I added it and restarted samba

```

sudo /etc/init.d/samba restart

```

(To save rebooting the whole machine :) )

Now I can see the machines under the network without getting the failed to retreive list error, but I get it when I click on the machine.

However, it does work if I type smb://192.168.0.3 in the location bar

(that is the IP of the server).

I did notice that the smb.conf on the server had a line which was

```

Failed to retrieve share list from serverFailed to retrieve share list from server

```

So I removed that, and restarted, but it didn't make any difference.

Anyone got any ideas what could be wrong?

---

### Post by Another Monkey on 2009-04-26
There's a few things that can be wrong, and it usually results in that lovely, generic and thoroughly unhelpful error message.

I found this thread really helpful
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Post #2 here explained a firewall problem I was having [http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access](http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access)

I also added "smb ports = 139" to to an annoying error in one of my logs based on the advice here [http://kbase.redhat.com/faq/docs/DOC-2339;jsessionid=B3427A500A9C9E95BFCF8054D027B7C7.ab46478d](http://kbase.redhat.com/faq/docs/DOC-2339;jsessionid=B3427A500A9C9E95BFCF8054D027B7C7.ab46478d)

If you look at my posts here [http://ubuntuforums.org/showthread.php?t=1134928](http://ubuntuforums.org/showthread.php?t=1134928) you'll see what I had to do to get Samba fully working again in Jaunty.

I am no expert, but here goes (most of this is the first post in my own words, with some extras):

First thing, switch off any firewalls (Windows too).  (You can bring them back on later, when you do, make sure that the correct ports are open [137, 138 TCP; 189 and 445 UDP].  See the post I mentioned above about the firewall as well.)

Now try the share again.  If it works, you know it's a firewall messing things up and your Samba configuration is fine.

Next is to configure Samba and this is pretty easy, it's just  matter of taking it one step at a time (the first post walks you through this).  My smb.conf looks like this (and this works with Windows):
```

[global]
	workgroup = WORKGROUP

	security = user
	username map = /etc/samba/smbusers

	smb ports = 139

#An example share
[Pictures]
	path = /home/monkey/Pictures
	valid users = samba_username
	writeable = yes

```
I've skipped a lot out as I had them just at default, you should be able to leave them too.

Now, I am using "user" security, so I had to set up a Samba (network) user and map that to a Linux user.  You can use other security settings and possibly ignore this.

Create the Samba user.
```

sudo smbpasswd -L -a samba_username
sudo smbpasswd -L -e samba_username

```

Now associate that Samba user with an Ubuntu user account.
```

sudo gedit /etc/samba/smbusers

```

Add an entry like this (you can add as many as you need):
```

ubuntu_username = samba_username

```
Save the file.

Now restart Samba
```

sudo /ect/init.d/samba restart

```

A lot of the above you can do using the GUI tool and you might find that easier.  You need to install "system-config-samba" and it can be found under System/Administration/Samba once installed.

When Samba comes back up, give it a minute or two and try the shares again.  If you get any problems, check the logs in "/var/logs/samba", they will probably show you what's wrong.

The command "testparm" is good for checking "smb.conf" and "smbtree" is a simple way of checking what Samba really sees without having to use Nautilus or similar.

If you use a firewall in Ubuntu; well, more correctly, if you use an iptools configuration utility - I found that Firestarter was pretty good.  Watching for events in it can be a big help.

---

### Post by dionblundell on 2009-04-26
I have had similar problems, and it normally comes down to passwords...
By default, Samba knows no passwords, not even your linux/unix one, so you have to add it.
My Linux logon passwords are:
_username_: **dion**
_password_: **lions4freedom**
Now you need to let Samba know this, open a terminal (Ubuntu Menu / Accessories / Terminal )```
sudo smbpasswd -a dion
```you will be prompted for your _password_ to allow **sudo** to elevate smbpasswd, give it to it, it's likely to be your unix one (**lions4freedom** is my linux/samba password)
Now that _smbpasswd_ is running, it will ask you for the password of the user **dion **who you have just tried to add (the _**-a**_ switch tells you you are adding a user to the samba/SMB password file/database). I have found that once this is done 3 other things need to be changed to make it work

[LIST=1]
[*]make sure the workgroup names match - I think you said yours was WORKGROUP
[*]set security to user, so passwords are used
[*]turn mapt-to-guest OFF, otherwise passwords are not used
[/LIST]
To do this you need to edit the Samba config file, sigh...
```
sudo gedit /etc/samba/smb.conf
```find the [global] section, this is the top section, search for the following options and put this in the file, right under [global]
```
[global]
workgroup = WORKGROUP
security = user
map to guest = never
```find any other entries for security, map to guest, workgroup
and add a # (hash) to the front of the line, ie:
# workgroup = MSHOME
# security = guest

You need to know that _samba_ when it reads the config file _goes with the last option_, so...
[COLOR=Indigo]security = server
secuirty = user
security = guest[/COLOR]
would be **interpreted as** _security = guest_
Because it is the last option, hence it is important to comment out (with a hash) any other duplicate options.

_**In summary**_ to get samba to play with windows your need to

[LIST=1]
[*]add your linux **username** to the samba password database
[*]make sure **security** is set to user - so it uses passwords
[*]turn **_map to guest_** off
[*]matching **workgroup** names makes it easier to find shares, but is not necessary to make it work
[/LIST]
Now restart samba, or reboot your computer:
```
sudo /etc/init.d/samba restart
```
This should make things work. Hope it helps.
Peace.

---

### Post by fungihead on 2009-04-26
so, tried everything above and still not working, only thing i havnt been able to try is opening ports on my network since im not the admin.

would this cause problems? since in windows it doesnt need open ports

im pretty much stuck now. i dont think its anything on my end, must be the network

---

### Post by jonandrews on 2009-04-27
I recently came across the following info on the forum which solved a very similar problem for the originator of that post. 
(I have not tried it myself, as I have never been able to duplicate the problem - I have done dozens of network setups between various versions of Ubuntu & Windows, and they have always browsed the Windows network fine - see my networking guides [www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/) ) However, I have read so many posts reporting this problem , I kept a copy this apparent solution:



Re: Cannot mount XP network shares
________________________________________
Step 1:
Edit /etc/nsswitch.conf. To do this, open a terminal (programs > accessories > terminal) and copy/paste this command:
Code:
gksudo gedit /etc/nsswitch.conf
Find the line that looks like this:
Code:
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
And just in front of "dns" add "wins" so it looks like this:
Code:
hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4
Save the file, and close gedit.

Step 2:
Install winbind by copying and pasting the following command:
Code:
sudo aptitude install winbind
See if that fixes your problem.

If that still doesn't work, try this: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)


### >> The writer of the solution later explained what it did as follows:

Quote:
Originally Posted by inobe
"i would like to know how winbind came up short if you followed the steps correctly "

Are you sure that wins is placed before dns? Order DOES matter in this file. If you place wins at the end of the line, then dns requests get queried before wins. Some hosts dns servers respond with a search page if dns queries are not successful. This counts as a resolution, so wins is never queried.



I hope this stuff gives you a solution...

---

### Post by lisati on 2009-04-27
Be careful about sharing your system's passwords on these forums! They have been known to be spidered.......

---

### Post by dmizer on 2009-04-27
There are three parts to this problem.

1) All of your Windows computers need to be in the same workgroup.
[INDENT]To check/remedy this, take a look at this Microsoft document: [http://support.microsoft.com/kb/295017](http://support.microsoft.com/kb/295017)[/INDENT]
2) Ubuntu needs to be in the same workgroup as your Windows computers.
[INDENT]To remedy this, follow the steps outlined in [post 5](http://ubuntuforums.org/showpost.php?p=7148118&postcount=5).[/INDENT]
3) Ubuntu is unable to resolve Windows hostnames by default.
[INDENT]To remedy this, follow these steps: [http://ubuntuforums.org/showpost.php?p=7075850&postcount=4](http://ubuntuforums.org/showpost.php?p=7075850&postcount=4)[/INDENT]

---

### Post by Grimmy on 2009-04-27
> **jonandrews said:**
> 
Step 2:
Install winbind by copying and pasting the following command:
Code:
sudo aptitude install winbind
See if that fixes your problem.

If that still doesn't work, try this: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)


Thanks,  I followed the steps in the "pre-work" section of that thread.  This fixed my problem and I can now also browse my Windows 7 share, which I was never previously able to do on my Eee.

---

### Post by RichTJ99 on 2009-05-10
> **DenysT said:**
> Having struggled through this in 8.10 I finally decided to start over in 9.04 and this is how I got everything to work without the dreaded "failed to retrieve" error.

Open a terminal window.
Applications -> Accessories -> Terminal

Type in "sudo gedit /etc/samba/smb.conf" without the quotes (you'll have to enter your password)

In the conf file find the line *workgroup = WORKGROUP*

If your Windows workgroup (My Computer (right click) -> Properties - Computer Name tab has this info) is different change the line to read workgroup = YOURWORKGROUPNAME

Next scroll down a few lines until you find the line *name resolver order = lmhosts hosts wins bcast *and delete the semicolon at the beginning of the line.

Save the changes and exit. Reboot. I don't know that rebooting is necessary but I'm still having to unlearn Windows and learn a real OS again. :P When you next go to Places - > Network you should see the network workgroup and computers attached to it. From there you can open/connect to a computer and see it's shares. It's not like XP where you just have a list of all shares in My Network Places but at least you can see them. This worked for me on 2 clean installs of 9.04, hope it works for you.


I just tried this in a clean install of 9.04 & I cant get it working.  Are you connecting via wired or wireless?  I know it shouldnt make a difference but I figured I would ask.

---

### Post by adonet on 2009-05-11
> **DenysT said:**
> Having struggled through this in 8.10 I finally decided to start over in 9.04 and this is how I got everything to work without the dreaded "failed to retrieve" error.

Open a terminal window.
Applications -> Accessories -> Terminal

Type in "sudo gedit /etc/samba/smb.conf" without the quotes (you'll have to enter your password)

In the conf file find the line *workgroup = WORKGROUP*

If your Windows workgroup (My Computer (right click) -> Properties - Computer Name tab has this info) is different change the line to read workgroup = YOURWORKGROUPNAME

Next scroll down a few lines until you find the line *name resolver order = lmhosts hosts wins bcast *and delete the semicolon at the beginning of the line.

Save the changes and exit. Reboot. I don't know that rebooting is necessary but I'm still having to unlearn Windows and learn a real OS again. :P When you next go to Places - > Network you should see the network workgroup and computers attached to it. From there you can open/connect to a computer and see it's shares. It's not like XP where you just have a list of all shares in My Network Places but at least you can see them. This worked for me on 2 clean installs of 9.04, hope it works for you.

I'm sorry but it doesn't work for me on a clean 9.04 install while 8.10 on the same system (other partition) works fine.

what shall I do?

---

### Post by dmizer on 2009-05-11
> **adonet said:**
> I'm sorry but it doesn't work for me on a clean 9.04 install while 8.10 on the same system (other partition) works fine.

what shall I do?

Try the suggestions I've made in the 6th link in my sig.

---

### Post by rocket777 on 2009-06-03
I just **finally **fixed my windows file sharing problem, perhaps this might help.

Here's the bottom line for what ailed my system. I needed to setup static IP's (192.168.1.xxx for my router) instead of dhcp.

Next, I had to add these entries to my /etc/hosts file.

I have a small home local lan and so there's no nameserver running anywhere. This means that hostname vs. ip addresses were not available to the ubuntu system from the network - which would silently fail. I found nothing in any logs either (but might have missed something).

The sad thing is that it fooled me because the network gui would find all the computer names, but only one would work.

My windows boxes all seem to find each other easily, but my 9.04 Ubuntu would only see one of my windows computers. And I am still puzzled how it found that one - somewhere along the line something (not me, I swear) did actually add my first and only windows ip address and name to the hosts file. When I added the rest, it all worked. I must have added these to the windows hosts files long ago and forgot this was needed on my network.

It's a shame that ubuntu network gui shows these computer and knows their names - it figures out they are there but can't open them w/o the ip address and it can't translate the windows host name it sees somehow into the ip address.

Anyway, maybe this is your problem. 

I hope in the future that ubuntu will be more forthcoming about network failures and at least log what the failure is. I had to figure it out by staring at sniffer dumps for days until I saw where it was not getting the info it wanted.

UPDATE:

I did finally figure out what was occurring that requires the hosts table entries.

My ubuntu system would issue a netbios broadcast (6 times) and it would get no response. So, after that, it would contact my first dns server (I use the open one at 208.67.222.222) which did respond. In this case, I provide a single host name, e.g. "myhost" which it would turn into [www.myhost.com](www.myhost.com) and then return an IP address. Next, ubuntu would think, oh this is good, let's try to do a netbios tcp connection here, which would fail - since this is some system somewhere on the public internet. It tries this 3 times then finally gives up. Anyway, that's what I saw using a hub and a sniffer.

By putting these into the hosts file, ubuntu then did the same things, except it did not go to the public nameserver, but rather immediately sent the netbios connection to my local computer (the right one) and got a response.

---

