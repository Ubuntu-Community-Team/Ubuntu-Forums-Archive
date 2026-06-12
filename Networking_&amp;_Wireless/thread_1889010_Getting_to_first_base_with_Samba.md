---
title: "Getting to first base with Samba"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by paul1149 on 2011-11-30
Hi,

I'm about at wit's end trying to get a linux fileserver up here. I installed Ubuntu 10.04 (desktop) on a dedicated older Dell box, with no problems, and it seems to be running well.

I updated the packages, and added things like samba, ssh, apache2 and others. I enabled Personal File Sharing. So far so good.

I can see the ubuntu machine on the local Workgroup, but cannot log in. I don't even know why I have to log in, as I allowed anyone to access the public folders under PFS. Maybe because passwords are turned on in the Vista box?

I have so many small questions, any one of which I know could throw a wrench into the machine, and despite studying this for a long time - weeks, really - I have not gotten even to first base with linux file sharing.

[LIST]
[*]Is there a firewall running under U 10?
[*]How do I know samba is running?
[*]Do I have to restart it every time I change smb.conf? If so, how?
[*]How on earth does one actually accomplish the smb.conf.master -> smb.conf parameter check trick?
[/LIST]

And so many more. This should be so good - being able to set up a free file server, yet it has been a sink hole of weeks of my time and has ended in utter frustration.

Maybe I'm not cut out for this. I'm at the point of shutting down, where I can hardly even assimilate new information. I'm going glassy-eyed.

Is there a straightforward way to do this, or do I give up?

---

### Post by Lisiano on 2011-11-30
1) Not that I know of. By default there shouldn't be any firewall unless you added one yourself.
You might consider iptables a firewall in a way so check there in case.

2) ```
ps aux | grep smb | grep -v grep
```
```
root      1183  0.0  0.0  93764  3160 ?        Ss   Nov29   0:00 smbd -F
root      1201  0.0  0.0  93764  1380 ?        S    Nov29   0:00 smbd -F
```
There might be a better way but this works for me.

3) Not exactly, but you need to reload the configuration file. 2 ways, either reload (Just refresh the config) or restart (Restart smbd)
```
sudo service smbd reload
```
Replace reload with restart, stop, start or whatever you wish to tell smbd to do.
Personally I always restart a service.

4) EDIT: Googled the smb.conf.master file and found this. ```
testparm -s smb.conf.master > smb.conf
``` You are probably looking for that.

For the password thing, Windows always tries to talk to a server and use the SAME username and password the current user is logged in as on the SMB server, so the samba server might be telling the client there is an auth error so the default response by the client is to ask the user what the credentials are. Try to auth to the SMB server as "Guest" or "nobody".

---

### Post by paul1149 on 2011-11-30
Thank you. With that first command I got an output that began 

root 520 0.0 0.1 15316 3984 ? .... smbd -F

then another line in the same format. It's on the other machine, so I haven't copied it here. I have no idea what this means, but apparently smbd is running.

I didn't install a firewall, so I guess that is not a problem here.

The smb.conf.master idea is to copy the default smb.conf to the master file, and then run [COLOR="DarkRed"][FONT="Lucida Console"]root#  testparm -s smb.conf.master > smb.conf[/FONT] [/COLOR]to both test parameters and distill the file into a much cleaner unit.

---

### Post by paul1149 on 2011-11-30
Replying to your edit, thank you, yes, that is exactly what I was referring to with the master smb.conf file.

Using 'guest' I was able to get right in to view the Profile and Printer folders. But that was it. I couldn't get any further without a login query, which again failed.

---

### Post by Lisiano on 2011-11-30
Forgot to mention. To allow guests to view your folders, you also need to put this in your usershare
```
guest_ok=y
```
My usershare is located under /var/lib/samba/usershares
This consists of the filename (The name that will be shown to everyone), the path where the folder is located and any extra arguments you wish to add. Try adding that line there.
NOTE: I have Ubuntu 11.10 so YMMV. If it's not there, then it should be somewhere close to smb.conf, if not. Use this nifty command
```
locate usershare
```

EDIT: To add a SMB password (ONLY applied to SMB) to the currently logged in user, use smbpasswd
For example to edit a password I set for a user named lisiano I would use this as root (sudo)[no need for root if you are editing yourself]
```
sudo smbpasswd lisiano
Type in new password
```
If you enter a non-existant user, it will be created.

EDIT 2: The "ps aux" command lists all programs you have running in this table
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
```
It didn't appear since it didn't contain the word "smb" in it so that might have confused you.
User - Under who the process is running
PID - Process ID
%CPU - Current CPU usage
%MEM - Current Memory (RAM) usage
VSZ - Virtual memory size of the process in KiB (1024-byte units)
RSS - Resident set size, the non-swapped physical memory that a task has used (in kiloBytes)
TTY - Controlling tty (Terminal)
STAT - Multi-character process state. Basically what the process is doing.
START - Time the process started at.
TIME - Cumulative CPU-time the process had. For example a process running at 50% for 24 hours will have 12 hrs of CPU time.
COMMAND - What command string was used to start the process
(Taken from the ps man page, section STANDARD FORMAT SPECIFIERS)

---

### Post by Morbius1 on 2011-11-30
* Personal File Sharing is not Samba. It's bit's and pieces of an Apache server that uses avahi to broadcast it's only share located in the Public folder in your home directory.

* You need to determine if the following services are running:
```
sudo service smbd status
sudo service nmbd status
```If not then start them:
```
sudo service smbd start
sudo service nmbd start
```* You didn't say how you created the Samba shares - there are 2 methods so if you post the output of the following commands we can figure it out:
```
testparm -s
net usershare info --long
```Last but not least please post the output of the following commands:
```
hostname
smbtree
```To answer some of the smaller questions:
> Do I have to restart it every time I change smb.conf? If so, how?Yes:
```
sudo service smbd restart
```> How on earth does one actually accomplish the smb.conf.master -> smb.conf parameter check trick?Don't bother. Any PC built in the last 10 years will not benefit from the alleged performance improvement.

---

### Post by paul1149 on 2011-11-30
> **Lisiano said:**
> To allow guests to view your folders, you also need to put this in your usershare
```
guest_ok=y
```

EDIT: To add a SMB password (ONLY applied to SMB) to the currently logged in user, use smbpasswd
For example to edit a password I set for a user named lisiano I would use this as root (sudo)[no need for root if you are editing yourself]
```
sudo smbpasswd lisiano
Type in new password
```
If you enter a non-existant user, it will be created.

EDIT 2: The "ps aux" command lists all programs you have running in this table
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
```

Thanks again for all this information, Lisiano.

I looked at the .conf again and noticed that under [homes] browseable was turned off. I corrected that, and immediately saw homes from Vista. However I still couldn't log in.

I just set a smb password for my ubuntu user name, and was hopeful its lack had been the problem. But when I went back to Vista 1) now I couldn't see homes any longer (not related, I trust), and b) I still couldn't log in.


> **Morbius1 said:**
> * Personal File Sharing is not Samba. It's bit's and pieces of an Apache server that uses avahi to broadcast it's only share located in the Public folder in your home directory.

* You need to determine if the following services are running:
```
sudo service smbd status
sudo service nmbd status
```If not then start them:
```
sudo service smbd start
sudo service nmbd start
```* You didn't say how you created the Samba shares - there are 2 methods so if you post the output of the following commands we can figure it out:
```
testparm -s
net usershare info --long
```Last but not least please post the output of the following commands:
```
hostname
smbtree
```To answer some of the smaller questions:
Yes:
```
sudo service smbd restart
```Don't bother. Any PC built in the last 10 years will not benefit from the alleged performance improvement.

Ok, thanks for those commands. I'm copying everything useful to a Word file. Both services are and were up and running here.

I haven't created any shares yet. I just want to get into the machine. One step at a time. I do have **public **enabled, but that was under PFS, and I don't see it from Vista.

I realize that the file size of .conf doesn't matter. I was actually more concerned with being able to parse it myself without all the confusing text.

The output of those two commands follows. Thanks much for your input.


[PHP]paul@ubuntu:~$ testparm -s

Load smb config files from /etc/samba/smb.conf

rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)

WARNING: Ignoring invalid value 'guest' for parameter 'security'

Processing section "[homes]"

Unknown parameter encountered: "guest_ok"

Ignoring unknown parameter "guest_ok"

Processing section "[printers]"

Processing section "[print$]"

Processing section "[profiles]"

params.c:Parameter() - Ignoring badly formed line in configuration file: http://www.linuxhomenetworking.com/w...nux,_and_Samba

Loaded services file OK.

Server role: ROLE_STANDALONE

[global]

        map to guest = Bad User

        obey pam restrictions = Yes

        pam password change = Yes

        passwd program = /usr/bin/passwd %u

        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

        unix password sync = Yes

        usershare allow guests = Yes

 

[homes]

        comment = Users profiles

        path = /home/samba/profiles

        create mask = 0600

        directory mask = 0700

        guest ok = Yes

        browseable = No

        browsable = No

 

[printers]

        comment = All Printers

        path = /var/spool/samba

        create mask = 0700

        printable = Yes

        browseable = No

        browsable = No

 

[print$]

        comment = Printer Drivers

        path = /var/lib/samba/printers

 

[profiles]

        path = /home/samba/profiles

        read only = No

        create mask = 0600

        directory mask = 0700

 

paul@ubuntu:~$ net usershare info --long

[2011/11/30 13:50:57,  0] param/loadparm.c:7388(lp_set_enum_parm)

  WARNING: Ignoring invalid value 'guest' for parameter 'security'

 [/PHP]

---

### Post by Morbius1 on 2011-11-30
You're not going to like my suggestion. Now don't panic it's not as bad as it first sounds. Start over. Do not uninstall everything and reinstall it again. There is a factory fresh copy of smb.conf already on your system that needs one modification:

**(1) Make sure the following file exists: **
/usr/share/samba/smb.conf

**(2) Make a backup of your current smb.conf**
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.confMOD
```[B]
(3) Start with a fresh one:[/B]
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```**(4) Correct one mistake in the new one:**
Find the line:
> encrypt passwords = falseand change it to:
> encrypt passwords = true**(5) Restart samba**
```
sudo service smbd restart
```[B]
(6) Use Samba Nautilus-share to create a guest share:[/B]

Open Nautilus
Right click on /home/your_user_name/Documents
Select "Sharing Options"
Select "Share this Folder", "Allow others to create and delete..", and "Guest access"
Select "Create Share"

It will ask you if you want it to modify permissions - you do.

**(7) Now run the following command to find out if the samba client on your box can see the samba server on your box:**
```
smbtree
```[COLOR=Blue]**Note:**[/COLOR] to post the output of commands to the forum just copy and paste from the terminal to the forum. It makes it easier to read. Just a suggestion.

---

### Post by Lisiano on 2011-11-30
> **Morbius1 said:**
> [COLOR=Blue]**Note:**[/COLOR] to post the output of commands to the forum just copy and paste from the terminal to the forum. It makes it easier to read. Just a suggestion.

Tinsy correction, instead of just plainly copy-pasting, use the **#** button on the formatting tools when you post a reply. 2nd button left of the PHP button the OP used.

---

### Post by paul1149 on 2011-11-30
Ok, that wasn't hard. A couple of notes.

First, the parameter said **encrypt passwords = no**, and I changed it to yes.

Second, I changed the Workgroup to the name of my workgroup and restarted samba, and yet the new name is not reflected in the smbtree output.

Third, this brings up another point: ubuntu cannot connect to Vista, or even to the workgroup.

Here's the output of smbtree (using the Code button).


```
paul@ubuntu:~$ smbtree
Enter paul's password: 
WORKGROUP
	\\UBUNTU         		Samba 3.4.7
		\\UBUNTU\print$         	Printer Drivers
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
		\\UBUNTU\documents      	paul's account
MYNET
	\\VISTA          		
cli_start_connection: failed to connect to VISTA<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
```


And now for the acid test. I actually saw and got right into Documents, wit no log in necessary. So it seems to have worked flawlessly.

I still can't get into MYNET workgroup, but here's a clue maybe: Looking at the network from ubuntu, under Windows Network there are two workgroups, and ubuntu is listed under WORKGROUP. So maybe ubuntu doesn't know that samba is set up for MYNET?

It seems we're very close. What I'm actually trying to do is implement user-based permissions on various shares. But as I said earlier, I'm trying to go a step at a time, which is confusing enough.

Thanks much so far.
p.

---

### Post by Morbius1 on 2011-11-30
Open up smb.conf again and add one more line - I would place it right under the worgroup = line:
```
name resolve order = bcast host lmhosts wins
```Save it and restart samba:
```
sudo service smbd restart
```You probably know this already but every time you restart samba you have to wait a bit for the network to settle down before you can connect to a share.

[COLOR=Blue]**EDIT:**[/COLOR] I have to leave for about 30 minutes but I promise I'll be back.

---

### Post by paul1149 on 2011-11-30
Ok. That seems to have taken ubuntu out of WORKGROUP, but I still am unable to mount MYNET. BTW, when I click on Network I see two items: ubuntu and Windows Network. I'm not clear on why ubuntu is standing by itself, or if it matters.

Also, I just tested opening a file in Documents, but was unable to save changes. I'm sure there is a permission thing that needs adjustment. Or is it that I'm in as a non-passworded Guest?

---

### Post by Morbius1 on 2011-11-30
When you run smbtree do you still get:
>  failed to connect to VISTA<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL> BTW, when I click on Network I see two items: ubuntu and Windows  Network. I'm not clear on why ubuntu is standing by itself, or if it  matters.Same thing happens to me. I've learned to live with it which for me is a slightly bigger issue since I have multiple hosts with multiple workgroups.
> Also, I just tested opening a file in Documents, but was unable to save  changes. I'm sure there is a permission thing that needs adjustment. Or  is it that I'm in as a non-passworded Guest?     From the client or from the server?

If you added a file from the client it will save with owner = nobody so the server user will have a problem. You can fix that with yet another addition to smb.conf. 

But you should have full write access to anything in documents from the client. Run the following command again:
```
net usershare info --long
```and make sure it looks like this:
> [documents]
path=/home/user-name/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by paul1149 on 2011-11-30
Hmmm. I did nothing but come back 45 minutes later, and now the smbttree is giving me a Vista readout. It's picking up my own share, and the printer and some default share stuff I was unaware existed. Evidently some configuration changes are polled on interval, but why didn't a restart accomplish the same?

IAC, when I go back to nautilus, I still can't mount MYNET. So terminal sees into Vista but nautilus doesn't. This reminds me of Windows' behavior...

BTW, I see now how the output to smbtree is organize by workgroup. ubuntu is listed under the WORKGROUP workgroup, and Vista is listed under the MYNET workgroup. Which doesn't strike me as good.

Also, sorry for the ambiguity: that file save problem was with a file created in ubuntu and opened in Vista. Strangely, I just accessed it again from Vista, and I was able to rename it, but not to change its contents.

That **usershare info **command reads out exactly as you wrote.

So I seem to have three basic problems: ubuntu is not listed in the correct workgroup, I can't access Vista from ubuntu, and the permissions on the ubuntu share aren't what I would like.

Thanks,
p.

---

### Post by Morbius1 on 2011-11-30
> So terminal sees into Vista but nautilus doesn't. From a terminal type:
```
nautilus smb://vista/share-name
```[COLOR=Blue]*You may have to play with the capitalization of vista and change share-name to a known share on vista. Does it show you the contents of the share?*[/COLOR]
> BTW, I see now how the output to smbtree is organize by workgroup.  ubuntu is listed under the WORKGROUP workgroup, and Vista is listed  under the MYNET workgroup. Which doesn't strike me as good.
All hosts do not have to be members of the same workgroup as long as they are in the same network - everyone is connected to the same router. What's puzzling here is that you said you changed the workgroup in smb.conf and it still doesn't show up as such. Run "testparm -s" again and see if it lists your new workgroup name. Maybe it's something simple like you forgot to save smb.conf after you changed it.

[COLOR=Blue]**EDIT:**[/COLOR] While you're in "testparm -s" make sure you don't have any reference to the [documents] share. You can only use one method of samba sharing at a time on the same folder.

> Also, sorry for the ambiguity: that file save problem was with a file  created in ubuntu and opened in Vista. Strangely, I just accessed it  again from Vista, and I was able to rename it, but not to change its  contents.That one I don't understand. What are the permissions of that particular file? Or does it happen with any file?

---

### Post by paul1149 on 2011-11-30
Wow. Progress, but this is deep.

After an absence from the machine, I checked again and everything was behaving the same.

Then I tried the terminal nautilus command, and instantly got into the Vista share, using the Vista user login. This, despite using lower case "vista" in the terminal command, when the machine's name is in Title case.

After getting in through the terminal nautilus command, I tried again through the nautilus GUI, and still was unable to get into the workgroup. Nothing had changed. Man, this does remind me of Windows...

Yes, I've noticed with windows that workgroup boundaries are not respected. It seems the designation is only there for classification purposes, not functionality. They offer no privacy.

I ran testparm -s again, and to my eye one error arose: rlimit max (1024) below minimum windows limit (16384).

When I created that [Documents] share a dialog came up and offered to create the permissions automatically. There was no other choice but cancel, so I accepted. Evidently that's where the problem lay, because my user name was the only one with write permissions on the test file. (But then why was Vista permitted to change the file name? And I did check those two sharing options - allow others to change; allow guest access - when creating the share.) As soon as I changed the file Access permissions for Others to write, Vista was able to amend the file.

I then went into the container (Documents) properties and opened its access, which was the same as it had been for the file, for others to write. I even clicked ~change included objects to these permissions~, though that seemed to be a retrospective-only command. Then I created another test file, but it too had the restrictive permissions. So the question is how to create an automatically inherited permissions scenario, which to my mind should be the default. There must be a control somewhere that I'm missing.

I'm also confused that [Documents] does not appear in smb.conf.

So there is progress, but at the same time I'm wondering if everyone has this level of difficulty. Because if so, then I don't see how this is a practical solution for the ordinary guy. And I haven't touched yet on fine-tuning user-share permissions. I'm far from the sharpest guy on this stuff, but I'm not a dummy either. So philosophically this perplexes me.

Thanks again for your input.

---

### Post by paul1149 on 2011-12-01
Ok, some progress. I see the difference between sharing permissions and file permissions, similar to how Win7 works. This time setting permissions for the folder also set them not only for existing contents, but future as well. It's unnerving that the settings erase themselves in the dialog when doing so, but it does take.

So now I can create a new file, and edit and save it, in the ubuntu share from across the workgroup.

I also understand that that rlimit error is not significant.

Now I'm working on seeing into Vista from nautilus.

Thanks,
p.

---

### Post by bab1 on 2011-12-01
> rlimit max (1024) below minimum windows limit (16384)

That's not an error per se.  It's information showing that Samba is set below the Windows setting.  Read the description [**_[COLOR="Blue"]here[/COLOR]_**]("http://us.generation-nt.com/answer/bug-608624-testparm-samba3-unexplained-warning-rlimit-max-rlimit-max-1024-below-minimum-windows-limit-16384-help-201604202.html").  I believe Christian Perrier (the person answering the question) is the Samba Package Maintainer for Debian.

---

### Post by Morbius1 on 2011-12-01
>  I'm also confused that [Documents] does not appear in smb.conf.There are 2 ways to create a samba share:

_Classic Share_
Share definitions are in /etc/samba/smb.conf.

_Usershares ( sometimes called nautilus-shares )_
Share definitions are in /var/lib/samba/usershares. These share definitions are produced automatically when you create them from nautilus. You can edit those share definitions directly but the syntax is so picky it's best to leave them up to Nautilus. Usershares are still samba and are controlled by all the [global] settings in smb.conf.

It's best to use one method or the other for your shares. It's possible to use both at the same time but it's not recommended. The more complex your needs for that share the more you need the Classic Share method as Usershares have limitations. The only reason I started with Usershares for this topic was that it's the easiest to set up.

>  Now I'm working on seeing into Vista from nautilus.There is a very obscure bug, that for the life of me I can no longer find, that may explain this. When you click on Network, nautilus interprets that as a "nautilus network://" command. The next step when you select "Windows Network" is it issues a "nautilus smb://" command. This gets discombobulated for some reason and I don't remember why.

Try this:

Run from a terminal the command:
```
nautilus smb://
```When Nautilus opens up Bookmark it: Bookmarks > Add Bookmark. You will notice that on the left side panel of Nautilus the "Windows Network" bookmark appears. Use that bookmark to access the hosts.

Of course you could also circumvent this whole process altogether by running:
```
nautilus smb://vista
```Or even:
```
 nautilus smb://vista/share-name
```And then Bookmark that one. It can even be renamed via a right click. Then it will show up just like a "mapped drive" does on Windows.

---

### Post by paul1149 on 2011-12-01
Bab1 - Thanks. That confirms what I had found. I will say, though, that I had not changed the log error level, yet I still got this warning. IAC I'll ignore it.

Morbius1 - thanks once again. I was quite warming up to creating shares via the folder property sheets, which I'm quite used to under Windows, but I would like to pursue more granularity with permissions, so at some point I guess I will have to switch over to the .conf file. Your expertise is much appreciated.

(I will note, though, that I have found the property sheets method to perhaps be buggy. I have had to go through the motions some three times in order for access settings to stick. Perhaps, though, it is necessary to establish ownership, then access, then apply them to contents, each separately and in sequence.)

I'll look into the vista problem a bit later and get back.

Be well,
p.

---

### Post by paul1149 on 2011-12-03
Ok, sorry for the delay. I had to get a box up and running and recover some data.

It appears that I finally have a functioning linux workgroup server up and running reliably. *Praise the Lord!*

I didn't even do the bookmark thing - for some reason it was automatically done for me, both within Nautilus and on the desktop. Someone wrote some pretty smart code. But I have recorded all these commands in a samba file for future reference.

The other thing I did was download ubuntu-tweak. This allowed me "open as root" and also to access advanced properties on the share folder's permissions sheet, both from within Nautilus. I'm not sure I understand the advanced properties interface yet, but they're nice to have readily available. And I'm not sure they are as powerful as smb.conf; I suspect not.

(The other thing tweak allowed me to do is move the application control buttons over to the right. What a relief!)

Next I want to explore finely granulated permissions, per users and groups. But in fairness I need to read the samba documentation first and give it a try before I waste anyone's time here on that.

Many thanks to all for the great guidance, especially Morbius1.

Paul

---

