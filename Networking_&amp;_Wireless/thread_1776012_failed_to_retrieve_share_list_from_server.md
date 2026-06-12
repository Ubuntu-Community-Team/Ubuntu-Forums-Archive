---
title: "failed to retrieve share list from server"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by Clive McCarthy on 2011-06-05
I'm using multiple Ubuntu 10.10 computers on a peer-to-peer network with a router that handles the DHCP (it isn't the DHCP server because I have this same problem at two locations). I have SMB installed on all machines and they all have a [COLOR="SeaGreen"]**[SIZE="3"]shareddocs[/SIZE]**[/COLOR] folder and they all belong to the same WORKGROUP.

The connection between machines is quite erratic. Sometimes the shared folders are easily found, sometimes not at all.

My current problem is with just two machines with seemingly identical set ups. However, machine A can see machine B's shared folder but B cannot see A's folder.

Nautilus can successfully navigate to the "Windows Network" and then can locate the appropriate WORKGROUP and also the list of machines. But it can't get to the shared folder on the peer computer.

The horrible:
[COLOR="Red"]**[INDENT][SIZE="3"]failed to retrieve share list from server[/SIZE][/INDENT]**[/COLOR]error message is emitted. I've done a bunch of searches for this message but haven't found a satisfactory answer yet. The error message is REALLY bad since it doesn't say which server it was trying? -- the DHCP, the peer, who knows?

I ran smbtree and got this:

```
CLIVEWORKGROUP
	\\VOSTROV13      		VOSTROV13
		\\VOSTROV13\SharedDocs     	
		\\VOSTROV13\IPC$           	Remote IPC
	\\ARTDEMO        		ARTDEMO server (Samba, Ubuntu) 
							cli_start_connection: failed to connect to ARTDEMO<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\ALDERWOOD      		alderwood server (Samba, Ubuntu)
		\\ALDERWOOD\shareddocs     	
		\\ALDERWOOD\IPC$           	IPC Service (alderwood server (Samba, Ubuntu))
		\\ALDERWOOD\print$         	Printer Drivers

```
Which is a little more instructive:
[COLOR="Red"][SIZE="3"]cli_start_connection: failed to connect to ARTDEMO<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME[/SIZE][/COLOR]

I was guessing that somehow there is a trailing space character stuck on the end of the host name "ARTDEMO" that somehow confused things but I have checked /etc/hostname and that isn't it. Of course ***cifs*** is a mess so who knows...

As you can see, a Windows peer computer shows up just fine but it can't locate the shared folder on ARTDEMO either. The shareddocs folder on ARTDEMO has its permissions wide open from:
sudo chmod 777 -R etc.

I'm constantly annoyed at the weak peer-to-peer facilities of Ubuntu :-({|= The client-server model is too ingrained.

Any help or commiseration will be appreciated. ;)

---

### Post by Morbius1 on 2011-06-05
What about the permissions of the entire path to the shared folder?

For example, if /mnt/Data/shared is 777 but /mnt/Data is 700 then the remote user will never see the share.

Both /mnt and /mnt/Data have to be something like 755.

---

### Post by Clive McCarthy on 2011-06-05
I set the shared folder's permissions with:
sudo chmod 777 -R shareddocs *
Moreover, Nautilus shows the properties of the folder as:
[B][COLOR="Blue"]Others Create and delete files
Allow execution of files
Apply Permissions to Enclosed files[/COLOR][/B]
Though I don't entirely trust it. 

I wish Ubuntu supported a really simple shared folder option that was utterly open all the time.

Correction! Looks as if I did the chmod wrongly. The shareddocs folder is now showing up correctly. I guess that there was a file in the folder that didn't have wide open permissions and that prevented the folder from being found. Geez.

Is there some way of permanently causing ALL content of such a folder to have open permissions?

---

### Post by Clive McCarthy on 2011-06-05
So here is what I see as three bugs:

[LIST=1]
[*]The **properties>permissions** dialog [COLOR="Red"][SIZE="3"]falsely indicates that a folder is shareable[/SIZE][/COLOR] when in fact it is not.

[*]Nautilus emits an error message "**failed to retrieve share list from server**" which does not identify the server nor indicate the cause of the failure.

[*]smbtree emits an error message **NT_STATUS_BAD_NETWORK_NAME** when the name is just fine but there is a permission problem.
[/LIST]

My view is that a bug isn't just about 'code' it also includes all messages and documentation.

---

### Post by Morbius1 on 2011-06-05
> The **properties>permissions** dialog [COLOR=Red][SIZE=3]falsely indicates that a folder is shareable[/SIZE][/COLOR] when in fact it is not.It most certainly is shareable. 
> Nautilus emits an error message "**failed to retrieve share list from server**" which does not identify the server nor indicate the cause of the failure.If the remote user can't see the share then there is no way to list it.
> smbtree emits an error message **NT_STATUS_BAD_NETWORK_NAME** when the name is just fine but there is a permission problem.The bad network name is the full path to the target share so it is on fact a bad network name.

As a side note never ever do this:
sudo chmod 777 -R shareddocs 
You can do this:
```
sudo chmod -777 shareddocs
```Or you can do this:
```
sudo chmod -R a+rwX shareddocs
```But doing a "-R 777" made all your files executable.

---

### Post by Clive McCarthy on 2011-06-05
We have a difference of philosophy. Slamming 777 gets me where I want to go and the fact that a file might be executable when it isn't, is not an issue for me. There will be _some_ executables in the shared folder and teasing these out is way too much work.

On other matters: a 'name' is a 'name' and a 'permission' is a 'permission' and for me 'permission denied' leads to one kind of intuitive understanding whereas a 'bad name' leads me to another.

If one tool says a folder is shared and another says something has a 'bad name' and yet another says a 'share list' can't be retrieved there is obviously a large inconsistency in terminology. These messages should be intuitively clear, consistent and unambiguous.

Is there way of creating a shareddocs or public folder that implicitly has wide open permissions? It's VERY tedious to use Nautilus to drag and drop files from one machine to another and then have to re-chmod the destination folder.

---

### Post by Morbius1 on 2011-06-05
> **Clive McCarthy said:**
> Is there way of creating a shareddocs or public folder that implicitly has wide open permissions? It's VERY tedious to use Nautilus to drag and drop files from one machine to another and then have to re-chmod the destination folder.
That's 2 different questions.

If you can drag and drop a file from a remote machine to the server then you have fulfilled the first requirement.

The fact that the remote file is not accessible to the server user is another problem entirely. Based on your posts so far It sounds like you are using Nautilus to share the folder. So to fix the second problem:

* Edit smb.conf as root:
```
 gksu gedit /etc/samba/smb.conf
```* Add the following line to the [global] section:
```
force user = your-server-user-login-name
```* Save smb.conf, exit gedit and back in the terminal restart samba:
```
sudo service smbd restart
```Every time you restart samba you have to wait a bit - sometimes minutes - for the network to settle down.

When the remote user gains access he will be converted to you as far as Samba is concerned and all saved files will be owned you you.

If that doesn't fix it or I misunderstood the problem then I need more information. The output of the following commands will indicate what method of samba you are using and how you are using it:
```
testparm -s
net usershare info --long
```As a side note:
> There will be _some_ executables in the shared folder and teasing these out is way too much work.```
sudo chmod -R a+rwX shareddocs
```That's not a little "x" it's a big "X". Every sub-folder will be tagged as executable which you must have. Every file that is not already tagged as executable will not be made executable. And every file that is already executable will remain so. FYI

---

### Post by Clive McCarthy on 2011-06-05
Thanks! I'll take your advice.

These machines all have just one user (me) and I can be sitting at one machine or another so there is no client-server hierarchy it's all peer-to-peer.

---

### Post by Morbius1 on 2011-06-05
You may not want it to be client - server. You may not think of it as client-server but this is Samba so it is client-server.

The only thing I can think of that looks and smells like a peer-to-peer file transfer is Personal FIle Sharing. It doesn't work very well but it looks peer-to-peer. In reality though it sets up a baby Apache file [COLOR=Blue]server[/COLOR] and announces it's presence to the network using avahi so looks can be deceiving.

---

### Post by capscrew on 2011-06-05
> **Morbius1 said:**
> You may not want it to be client - server. You may not think of it as client-server but this is Samba so it is client-server.

The only thing I can think of that looks and smells like a peer-to-peer file transfer is Personal FIle Sharing. It doesn't work very well but it looks peer-to-peer. In reality though it sets up a baby Apache file [COLOR=Blue]server[/COLOR] and announces it's presence to the network using avahi so looks can be deceiving.

Just a quick thought to add to the soup...

It would be helpful for the OP to think of Samba as a client-server *[COLOR="Blue"]application[/COLOR]*.  Peer to peer networking is a [COLOR="Green"]user control issue[/COLOR]; more like local vs domain control of users and computers (hosts).

---

### Post by Clive McCarthy on 2011-06-05
Yes, I understand. 

As a user that has migrated from Windows XP to Ubuntu the strong client-server background of Linux is more evidently present than Windows. I suspect, at least from the posts that I have read, that a lot of desktop/GUI Ubuntu users are working with a peer-to-peer environment and not a client-server one. If one enables a shared folder on a machine and is in _physical possession_ of the HDD then not having permission to use the content is a bit silly. It's a _personal_ computer after all.

This is of course not true for the non-GUI, CLI server version. A server might well be locked away in a physically secured location. An impersonal computer...

I have found it a bit odd that SMB server isn't installed by default. In fact with a new installation of 10.10 the process of setting up a shared folder is quite ugly: create the folder; begin changing the properties to shared and ... whoops SMB server needs to be installed, including a reboot :( ... and then updated; to make things work.

I'd recommend that, for the GUI version, both SMB client and server should be installed and that:
**force user = your-user-login-name**
is set when a shared folder is first created.

---

### Post by capscrew on 2011-06-05
> **Clive McCarthy said:**
> Yes, I understand. 

As a user that has migrated from Windows XP to Ubuntu the strong client-server background of Linux is more evidently present than Windows. I suspect, at least from the posts that I have read, that a lot of desktop/GUI Ubuntu users are working with a peer-to-peer environment and not a client-server one.
If you really drill down you will find that any time you communicate via TCP/IP, and are requesting resources you are a client.  Conversely, any time you are running a process that provides resources via TCP/IP (i.e. SMB, DHCP, DNS, HTTP, SSH,etc.) you are functioning as a server.  Even a simple iTunes application has a server for streaming music built in (DAAP).  Peer to peer has nothing to do with providing/requesting the service.  Peer to peer vs domain has everything to do with authentication, authorization and auditing users and resources.  Client/Server and Peer to Peer are not mutually exclusive.  They can and do co-exist in the network.  In short they are 2 different aspects of computing in a network.> 
If one enables a shared folder on a machine and is in _physical possession_ of the HDD then not having permission to use the content is a bit silly. It's a _personal_ computer after all.
A name like *_personal computer_* is  marketing speak.  It has little to do with a description of  with how the hardware/software is used.  I used a Windows server as a workstation for awhile years ago.  Not the best situation but do-able. > 

This is of course not true for the non-GUI, CLI server version. A server might well be locked away in a physically secured location. An impersonal computer...

I have found it a bit odd that SMB server isn't installed by default. In fact with a new installation of 10.10 the process of setting up a shared folder is quite ugly: create the folder; begin changing the properties to shared and ... whoops SMB server needs to be installed, including a reboot :( ... and then updated; to make things work.
This has not been my experience with Samba at all.  It takes me about 5 minutes to install and configure Samba.> 

I'd recommend that, for the GUI version, both SMB client and server should be installed and that:
**force user = your-user-login-name**
is set when a shared folder is first created.
You might do that...

But to whom would you recommend it to?  The developers at Samba have little to nothing to do with the developers at Gnome (Nautilus) or KDE (Dolphin).  In addition Samba has minimal contact with the package maintainers of the binary packages that you install.  Microsoft controls all of this in their world.  In the FOSS world there are many independent developers.

On the other hand you can always compile the source yourself...

---

### Post by Clive McCarthy on 2011-06-05
Just so you know, I'm working on a program that uses TCP/IP IPC sockets. My servers are three Ubuntu machines that each control part of an art work. Eventually one of the servers will also be the 'master' client (IPC works both intra-computer as well as inter-computer). So I'm quite familiar with what lies under the hood.

It still strikes me that Ubuntu is the integrator of all the software components and that, though these components come from different sources, Ubuntu is responsible for the default configuration and integration.

---

### Post by capscrew on 2011-06-05
> **Clive McCarthy said:**
> Just so you know, I'm working on a program that uses TCP/IP IPC sockets. My servers are three Ubuntu machines that each control part of an art work. Eventually one of the servers will also be the 'master' client (IPC works both intra-computer as well as inter-computer). So I'm quite familiar with what lies under the hood.

We've talked before.  :-)> 

It still strikes me that Ubuntu is the integrator of all the software components and that, though these components come from different sources, Ubuntu is responsible for the default configuration and integration.
Ubuntu is not the *integrator* more like the *aggregator* of the packages. Samba, Apache, OpenSSH, OpenLDAP...just about all that is in Synaptics are independent (of Ubuntu) projects.  Some are sponsored by Redhat or Debian, but most are truly independent.  As long as you meet certain packaging mandates you can package source to binary.  There is very little to no crossover.

Ubuntu indeed contributes in upstream ideas (to Debian) and has it's own variations on packaging but that is all. In reality there is nothing *wrong* with the default configuration or integration other than you don't like it.

Of course in FOSS if you don't like it, *YOU*, can change it.

---

### Post by Morbius1 on 2011-06-05
> I have found it a bit odd that SMB server isn't installed by default. In  fact with a new installation of 10.10 the process of setting up a  shared folder is quite ugly: create the folder; begin changing the  properties to shared and ... whoops SMB server needs to be installed,  including a reboot :sad: ... and then updated; to make things work.That's because you approached this as though you were running Linux. You should have approached it as though you were running Windows XP:

Open Nautilus
Right click a file you own ... say /home/$USER/Documents
Select Sharing Options
Select Share this folder
[COLOR=Blue]*Now at this point if you don't have Samba installed it will ask you if you want it to install it.*[/COLOR]
Select other options that you desire and then click on Create Share.
Now it will ask you if you want it to modify permissions automatically - you do.

You just created a Samba share ( A Samba Usershare to be specific ). Eliminating the download time of the Samba package itself that took what ... 8 seconds?

No reboot.
No restarting services.
No modification of permissions.

You would still have to do the force user though :wink:

---

### Post by Clive McCarthy on 2011-06-05
I configured several machines with 10.10 one after another directly from a live CD -- I can't recall exactly but in each case there was a distinct download and installation of the SMB server and then the need for an upgrade. It's all solved now: I bought a HDD duplicator so I now just clone HDDs when I set up a new machine.

I found this[SIZE="3"][COLOR="Lime"] [http://www.samba.org/samba/docs/using_samba/ch08.html]("http://www.samba.org/samba/docs/using_samba/ch08.html")[/COLOR][/SIZE]
Which suggests to me that I should try:
[COLOR="Blue"][SIZE="3"]create mask[/SIZE][/COLOR]
 -or-
[COLOR="blue"][SIZE="3"]force create mask[/SIZE][/COLOR]

because
[COLOR="blue"][SIZE="3"]force user = user_name[/SIZE][/COLOR]

will then, I think, exclude the client from subsequently overwriting the files? 

I really want my shareddocs files and directories to have entirely open permissions so that the user on the server (me) and the client of the server (me) can do whatever (me) wants! :P

I find the explanations from the link difficult. I'll have to read it carefully.

---

### Post by capscrew on 2011-06-05
> **Clive McCarthy said:**
> I configured several machines with 10.10 one after another directly from a live CD -- I can't recall exactly but in each case there was a distinct download and installation of the SMB server and then the need for an upgrade. It's all solved now: I bought a HDD duplicator so I now just clone HDDs when I set up a new machine.

I found this[SIZE="3"][COLOR="Lime"] [http://www.samba.org/samba/docs/using_samba/ch08.html]("http://www.samba.org/samba/docs/using_samba/ch08.html")[/COLOR][/SIZE]
Which suggests to me that I should try:
[COLOR="Blue"][SIZE="3"]create mask[/SIZE][/COLOR]
 -or-
[COLOR="blue"][SIZE="3"]force create mask[/SIZE][/COLOR]

because
[COLOR="blue"][SIZE="3"]force user = user_name[/SIZE][/COLOR]

will then, I think, exclude the client from subsequently overwriting the files? 

I really want my shareddocs files and directories to have entirely open permissions so that the user on the server (me) and the client of the server (me) can do whatever (me) wants! :P

I find the explanations from the link difficult. I'll have to read it carefully.

[SIZE="3"][COLOR="RoyalBlue"]I would [COLOR="Purple"]NOT[/COLOR] use that link at all.  It is for Samba v2.[/COLOR][/SIZE]  You are (I hope) using Samba v3.something.

If you want a description of all the parameters of the /etc/samba/smb.conf file you should look [**_[COLOR="Blue"]here[/COLOR]_**.]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")

---

### Post by Clive McCarthy on 2011-06-05
Thanks. The documentation isn't as 'nice' as for V2 but V3 is clearer. Looks like I will use **force create mode** and **force directory mode**  to get what I want.

---

### Post by athenroy on 2011-06-05
While everyone is arguing about desktops and Gnome 3, here is one of the problems that keeps Linux out of the hands of the masses!  Things like setting up a home network, especially if you have Windows machines on it, problems with certain drivers, especially for WiFi, etc.  It's things like that that keep most people on Windoze or OS X.  I'd be really POed if I had reformatted my drive, lost Windows, thinking Linux would work, only to find out when I ran the live CD I forgot to check this or that and now it doesn't work.  This is what Linux really needs to work on!

---

### Post by Morbius1 on 2011-06-06
> **Clive McCarthy said:**
> I found this [http://www.samba.org/samba/docs/using_samba/ch08.html](http://www.samba.org/samba/docs/using_samba/ch08.html)
Which suggests to me that I should try:
create mask
-or-
force create mask

because
force user = user_name

will then, I think, exclude the client from subsequently overwriting the files?

I really want my shareddocs files and directories to have entirely open permissions so that the user on the server (me) and the client of the server (me) can do whatever (me) wants! 

That won't work.
[COLOR=Blue]EDIT: I really should refrain from making absolute statements in the forum so let me rephrase that:[/COLOR]
I'm fairly certain that won't work ;)

First off, this would be a whole lot easier if we knew how Samba is set up on your server and that can be achieved by providing the output of the following commands:
```
testparm -s
net usershare info --long
```Second, I think the root of the problem here is a misunderstanding of Samba vs Linux file permissions. Most of the HowTo authors get this wrong as well so ... At a very basic level Samba determines what a remote user may do but Linux file permissions determines what a remote user can do.  The two have to be in sync. 

Consider the following scenario:

You created a share accessible by guests ( no authentication ). By default when the remote user adds a file it will save as follows:
[COLOR=Blue]owner = nobody
group = nogroup
mode = 644[/COLOR]

All remote users will be "nobody" so all remote users can read and write to that file. But the server user is not nobody so he will have read only access. If you use "force create" and "force directory" you will be able to modify the permissions on a new file such that it will save as:
[COLOR=Blue]owner = nobody
group = nogroup
mode = 666[/COLOR]

Now the server user has access to the file saved by the remote user. Things are looking good until the server user adds a file to the directory locally. When serveruser adds a file it will by default save as:
[COLOR=Blue]owner = serveruser
group = serveruser
mode = 644[/COLOR]

The remote user ( nobody ) is not "serveruser" so he will have read access but not write access to the file. There are ways to fix this using internal Linux permissions alone but if you want to use samba to fix this you have a number of options:

(1) "force user = serveruser"
After Samba lets them in all remote users will be converted from whoever they are into serveruser. All remote users and the serveruser will be seen as the same user.

(2) "guest account = serveruser"
By default Samba sets "guest account = nobody" but you can explicitly change that to have it point to serveruser. This one always gives me the willies but from a practical standpoint in this context ( guest shares ) there's really no difference between this and a global "force user".

(3) Create a samba password for serveruser, disable guest access, and have the remote user authenticate himself as you.

One sign of a bad Samba HowTo is that they insist that the server user create a samba password for themselves and access the share that way. This will take care of the problem but it does add an inconvience factor since you will have to authenticate yourself on the client.

[COLOR=Blue]Speaking of bad HowTo's [/COLOR]there has been a fundamental change in how Samba is initially configured in Ubuntu when you use Nautilus to create the share which I completely forgot about in my previous post. I use the LTS versions as my main OS but have post LTS versions on test machines and this change to nautilus sharing started in 10.10. Back in the good old days when you first use Nautilus-share it will install the samba package if it's not there already. But now it installs 2 packages - samba and:
> libpam-smbpassIn order for libpam-smbpass to do it;s thing it does require a reboot ( actually I think all it needs is a logoff / logon but... ).

This is what libpam-smbpass does: At every boot it forces the smbpasswd to match the local login password for all server users. It took me an embarrassingly long time to realize this and thought that dementia was beginning to set in until I discovered it.

If you set the smbpasswd during a session it will stay in force until you reboot and then it gets reset to the login password for that user. I think this is an incredibly bad idea and I'm not sure why someone thought  that's what nautilus-share users should have but it does go part of the way towards what you want.

Create a share with nautilus without selecting guest access, samba and libpam-smbpass will be installed, and when you reboot the remote user can authenticate himself as you without any further adjustments to Linux file permissions. Spooky. I do not believe they ( whoever they are ) though this one through since in a typical home lan environment the remote user ( like, down the hall ) is now using the same username and password that the server user uses to log into his own physical machine.

The first thing I do with a new install after using nautilus-share is the following:
```
 sudo apt-get remove libpam-smbpass
```But to each his own. :wink:

---

### Post by Clive McCarthy on 2011-06-06
Yikes! Libpam-smbpass sounds horrible. Morbius1 I wonder if it is part of Samba or an Ubuntu fix-up? Samba has a rather rich set of options albeit somewhat confusing but adding another mechanism is VERY messy.

I have to confess that I am planning to slam things hard by brutally setting: 
**force create mode = 0777**
      and 
**force directory mode = 0777**
And to hell with it!

I'll post my current configuration after breakfast...

---

### Post by Clive McCarthy on 2011-06-06
Morbius1,
Here's the configuration status:

```
clive@alderwood:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = CLIVEWORKGROUP
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	force create mode = 0755
	force directory mode = 0755

    ...

```

and

```

clive@alderwood:~$ net usershare info --long
[shareddocs]
path=/home/clive/Desktop/shareddocs
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

Clive.

---

### Post by Clive McCarthy on 2011-06-06
> **Clive McCarthy said:**
> Yikes! Libpam-smbpass sounds horrible. Morbius1 I wonder if it is part of Samba or an Ubuntu fix-up? Samba has a rather rich set of options albeit somewhat confusing but adding another mechanism is VERY messy.

I have to confess that I am planning to slam things hard by brutally setting: 
**force create mode = 0777**
      and 
**force directory mode = 0777**
And to hell with it!

I'll post my current configuration after breakfast...

Incidentally, I think (haven't tried yet) Gnome/Nautilus will handle finding the execution bit set for a non-executable, just fine. Whenever I double click a Bash file it politely asks if I want to _display_ or _run_ the file. I'm guessing it takes a peek at the extension and or the first few bytes of the file. I'm guessing the loader will do a similar thing. If it doesn't, then loading and executing some arbitrary bytes will likely do no harm since it most will likely crash with a GP fault. Further it's my own damn fault for trying to run it...

The difference between a Personal Computer and other machines isn't just "marketing". A Personal Computer is one you can _lift_. Some people _only_ trust computers you can lift, others only trust those you can't. :(

[IMG]http://www.fourteenthstreetstudio.com/web_1st%20program%201.jpg[/IMG]

---

### Post by Morbius1 on 2011-06-06
> **Clive McCarthy said:**
> Yikes! Libpam-smbpass sounds horrible. 
It's all a matter of perspective. If the client is running Windows and certain conditions exist it will be magic.

* You create a non-guest share on Linux - it installs libpam-smbpass.

* You reboot and without the user doing anything a samba password is created using that users login password.

If the remote user is running Windows AND the Windows login username and password matches the Linux users login name and password exactly then the Windows user is allowed access to the share without being prompted for authentication. This is made possible by how Windows passes those things without being asked.

The Linux client doesn't do this so it will always be prompted for authentication.

As far as create mode thing I'm really pretty sure that will work fine until you add a file from clive within the server itself. The shared directory probably has permissions of 777 already because that's what nautilus-share does. So oddly enough the remote user will be able to delete the file but not edit the file.

---

### Post by Clive McCarthy on 2011-06-06
When I get back to my studio I'll do some experimenting with Samba options.

In my case I'm working with a group of peer-to-peer Ubuntu machines (yes, I know there really is only client-server). I have some Windows XP machines on the network but these are quite unimportant.

At times I have as many as a dozen or more Ubuntu machines running but I am the ONLY user and they are configured identically as far as networking is concerned. I want to be able to relatively freely deploy files (both data and executables) from one machine to another.

I'm hoping that if I set the permissions of all my **shareddocs** directories with **sudo chmod -R a+rwX shareddocs** and configure Samba with **force create mode = 0777** and f**orce directory mode = 0777** then the files will have identical and full permissions as seen from either the client side or server side of things?

---

### Post by capscrew on 2011-06-06
> **Morbius1 said:**
> It's all a matter of perspective. If the client is running Windows and certain conditions exist it will be magic.

* You create a non-guest share on Linux - it installs libpam-smbpass.

* You reboot and without the user doing anything a samba password is created using that users login password.

If the remote user is running Windows AND the Windows login username and password matches the Linux users login name and password exactly then the Windows user is allowed access to the share without being prompted for authentication. This is made possible by how Windows passes those things without being asked.

The Linux client doesn't do this so it will always be prompted for authentication.

...

This is a problem due to the free form nature of peer to peer networks.  Samba assumes that all users with the same login are the same beings (human).  In a domain instance this would be impossible as you can't have duplicate users.

Have you posted a bug report with Gnome/Samba or Ubuntu?

---

### Post by Clive McCarthy on 2011-06-06
> **Clive McCarthy said:**
> 
I'm hoping that if I set the permissions of all my **shareddocs** directories with **sudo chmod -R a+rwX shareddocs** and configure Samba with **force create mode = 0777** and f**orce directory mode = 0777** then the files will have identical and full permissions as seen from either the client side or server side of things?

I'm getting "Unknown parameter encountered" from **force create mode = 0777** when I run testparms -s
This is weird...

---

### Post by Morbius1 on 2011-06-06
Then don't use it. Use "force user = clieve" instead.
EDIT: Sorry misspelled your name:
```
 force user = clive
```

---

### Post by capscrew on 2011-06-06
> **Clive McCarthy said:**
> I'm getting "Unknown parameter encountered" from **force create mode = 0777** when I run testparms -s
This is weird...

Although one might think that you could apply create modes globally, testparm sees it otherwise.  Remember create modes are a share parameter (e.g the (S) in the description) not a global one.

---

### Post by Morbius1 on 2011-06-06
@capscrew

Not sure what part of that you consider a bug.

* The fact that libpam-smbpass is installed and sets up samba passwords by itself?

* The way Windows sends the login user's username and password automatically?
[COLOR=Blue]*It's been that way since WinNT 3.5. I think Microsoft considers that a feature :)*[/COLOR]

* Or the fact that if the samba username and password on the server match the Windows _login_ username and password that the samba server accepts them?

---

### Post by Clive McCarthy on 2011-06-06
Is this Samba we have or Shamba? 

The documentation is clear:
[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")

```
force create mode (S)
This parameter specifies a set of UNIX mode bit permissions that will always be set on a file created by Samba. This is done by bitwise 'OR'ing these bits onto the mode bits of a file that is being created. The default for this parameter is (in octal) 000. The modes in this parameter are bitwise 'OR'ed onto the file mode after the mask set in the create mask parameter is applied.

The example below would force all newly created files to have read and execute permissions set for 'group' and 'other' as well as the read/write/execute bits set for the 'user'.

Default: force create mode = 000

Example: force create mode = 0755
```

And just to compound things testparm -s even reports on the status of **force create mode** !!!

---

### Post by capscrew on 2011-06-06
> **Clive McCarthy said:**
> Is this Samba we have or Shamba? 

The documentation is clear:
[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")

```
force create mode **[SIZE="3"][COLOR="Red"](S)[/COLOR][/SIZE]**
This parameter specifies a set of UNIX mode bit permissions that will always be set on a file created by Samba. This is done by bitwise 'OR'ing these bits onto the mode bits of a file that is being created. The default for this parameter is (in octal) 000. The modes in this parameter are bitwise 'OR'ed onto the file mode after the mask set in the create mask parameter is applied.

The example below would force all newly created files to have read and execute permissions set for 'group' and 'other' as well as the read/write/execute bits set for the 'user'.

Default: force create mode = 000

Example: force create mode = 0755
```

And just to compound things testparm -s even reports on the status of **force create mode** !!!

See the red above.

Square peg in a round hole -- keep on pounding!  :-)

---

### Post by Clive McCarthy on 2011-06-06
Hold that. User spelling error! creat and create..

---

### Post by Morbius1 on 2011-06-06
> **capscrew said:**
> Square peg in a round hole -- keep on pounding!  :-)
I do believe that is the very first time you told a joke on this forum :P

---

### Post by capscrew on 2011-06-06
> **Morbius1 said:**
> @capscrew

Not sure what part of that you consider a bug.

* The fact that libpam-smbpass is installed and sets up samba passwords by itself?

* The way Windows sends the login user's username and password automatically?
[COLOR=Blue]*It's been that way since WinNT 3.5. I think Microsoft considers that a feature :)*[/COLOR]

* Or the fact that if the samba username and password on the server match the Windows _login_ username and password that the samba server accepts them?

I think the you will find that Gnome is the culprit in this case.  This sounds like  libpam-smbpass is installed quietly when creating the share via GUI. This is triggered by Gnome.  Gnome should at least have a pop-up the describes what is being done.  The PAM module itself is a useful tool for domain wide use as it is.

---

### Post by capscrew on 2011-06-06
> **Morbius1 said:**
> I do believe that is the very first time you told a joke on this forum :P

Who me?  ;-)

BTW -- Sys admins have NO humor.  :D

---

### Post by Clive McCarthy on 2011-06-06
> **capscrew said:**
> Gnome should at least have a pop-up the describes what is being done.

My feelings are that the Samba installation needs more and clearer installation options via the GUI. The current set-up _appears_ to make things straightforward and a naive user, who is familiar with Windows, (86% of computers currently use one flavor or another of Windows) might readily imagine that Samba is going to enable a simple peer-to-peer network to function as they would expect.

Moreover, the notion of a user being logged on to a domain only once is obsolete. A contemporary user might have an Android phone, Android tablet, a laptop and whatever else, all using network resources at the same time and all logged on with just one name.

I'm waiting for my network to settle down before I can conduct my forcing experiments.

---

### Post by capscrew on 2011-06-06
> **Clive McCarthy said:**
> My feelings are that the Samba installation needs more and clearer installation options via the GUI. The current set-up _appears_ to make things straightforward and a naive user, who is familiar with Windows, (86% of computers currently use one flavor or another of Windows) might readily imagine that Samba is going to enable a simple peer-to-peer network to function as they would expect.
Edit: Windows does not use peer to peer for sharing files.  There is a server on each host that shares files and client software on every host that can request files.  If you look at the services running on Windows you will see the service (I believe it's called "server"). Sharing is a Client/Server process no matter who creates the code.> 
Moreover, the notion of a user being logged on to a domain only once is obsolete. A contemporary user might have an Android phone, Android tablet, a laptop and whatever else, all using network resources at the same time and all logged on with just one name.

No one said *"logged on to a domain only once"*.  Only that that user (no matter how many times they are logged in) will have a unique name (e.g two people can't have the same login).> 

I'm waiting for my network to settle down before I can conduct my forcing experiments.

---

### Post by Clive McCarthy on 2011-06-06
All I'm saying is that Windows creates the illusion that it provides a peer-to-peer networking environment. Linux with Samba doesn't provide the same illusion, however, it is that illusion that most people (86%) expect.

---

### Post by capscrew on 2011-06-06
> **Clive McCarthy said:**
> All I'm saying is that Windows creates the illusion that it provides a peer-to-peer networking environment. Linux with Samba doesn't provide the same illusion, however, it is that illusion that most people (86%) expect.

I guess that 86% should read [**_[SIZE="3"][COLOR="Blue"]this[/COLOR][/SIZE]_**]("http://linux.oneandoneis2.org/LNW.htm") before using Linux then.



Edit: I personally don't care whether Windows users adopt Linux or not.  i just don't like them whining about how it's not like Windows after complaining about "the evil empire" and WinBloz etc.  Get over it.  Use it, modify it to your liking and stop comparing it to something you have stopped using (for what ever reason that is).

---

### Post by Clive McCarthy on 2011-06-06
Perhaps, but expectations are expectations and a good user interface needs to be intuitive. Samba running on Ubuntu declares unambiguously that it has a "Windows Network" not a sorta-kinda-maybe-windows-network.

---

### Post by capscrew on 2011-06-06
> **Clive McCarthy said:**
> Perhaps, but expectations are expectations and a good user interface needs to be intuitive. Samba running on Ubuntu declares unambiguously that it has a "Windows Network" not a sorta-kinda-maybe-windows-network.

The user interface is not Samba at all.  Gnome/Nautilus is the front end you see (the GUI).  Samba is the back end.  Samba provides the daemons (smbd and nmbd) plus some tools for the client and housekeeping.  Gnome is responsible for what you see.  

The Samba and Gnome developers are upstream of the distros (Debian, Redhat, Gentoo, etc) and on different paths.  By and large the distros accept what Gnome has done with some exceptions.  For the most part the projects are in their own world.  Then again if you don't like what Gnome has done and you want to rename the "Windows Network" to "Kinda a Windows Network" you can grab the source code and modify and compile it    

Samba is a viable (reverse engineered) SMB system.  Your use is the kinda sorta type. My system interacts with all sorts of Windows users from *guests* to  specific sensitive data that only I can see.  It can be a XP or Vista or Win7 host or Linux(Debian or Redhat).  

I have stayed away from your discussion of specific configuration for a good reason.  I can't satisfy your unreasonable expectations.

---

### Post by Clive McCarthy on 2011-06-06
Capscrew, 
As Hal said: this conversation can serve no purpose anymore. Goodbye.
Clive.

---

### Post by Clive McCarthy on 2011-06-06
I just completed a test from one Ubuntu machine to a shared directory on another Ubuntu machine with Samba conf settings of:
**force create mode = 0777** 
   and 
**force directory mode = 0777**

I dragged and dropped a small file that had 
permissions  [SIZE="2"][COLOR="Red"]**-rw-r--r--**[/COLOR][/SIZE]
and it arrived on the Samba destination with 
permissions [SIZE="2"][COLOR="red"]**-rwxrwxrwx**[/COLOR][/SIZE]

It's a little brutal but it will get the job done. :guitar:

---

