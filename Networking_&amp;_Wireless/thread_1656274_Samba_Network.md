---
title: "Samba Network"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by PaulClarke on 2010-12-30
Hello,

This is my last effort at working this out and then I'm going to admit failure.

I have a home network with Ubuntu (3 PC) Windows (XP 3, 7 1 vista 1) and Lacie networked drive.

I have successfully edited fstab to mount the lacie drive at startup on my main ubuntu PC and it works a treat.

My problem is setting up the Unbutu PCs to browse the workgroup.

This was working but now (since my last update of Unbutu I think) I get prompted for a password and no matter what I do it does not let me browse.

Now I have read a few things on Samba and do not have the time or ability to become a network engineer. All I want to do is is have on my Ubuntu the same browsing ability that seems to come out of the box in Windows.

Thank you in advance

I'm happy to have someone forward me a smb.conf that works

Paul

---

### Post by PatchesTheCaveman on 2010-12-30
Do you have Windows Live Essentials installed on the Windows machine?  The Windows Live Sign-In Assistant changes the way Windows communicates via the SMB protocol such that Samba can't connect to Windows shares.  While the Samba developers have fixed this in the official version of their software, Canonical has not yet released an update with the new version.

To work around this issue, uninstall Windows Live Essentials.  Also note that Microsoft sometimes installs Windows Live Essentials via Windows Update, so you might not be aware you have this software.

As for configuring Samba, you don't have to edit smb.conf manually.  There is a graphical program that makes that much easier.  Go to Applications > Accessories > Terminal in your top panel.  In the black box that appears, type the following two commands, pressing Enter after each one:
```
sudo apt-get update
sudo apt-get install system-config-samba
```

Then, go to System > Administration > Samba to set up shared folders from your Ubuntu machine.

---

### Post by PaulClarke on 2010-12-30
Hello and thank you for your time.

The windows machine I am using is a bog standard XP box with all updates added.

I have set up the Samba shares using that tool and checked with webmin.  The windows box can browse my shares.  My main issue is not being able to browse the machines on the workgroup from Ubuntu.

It keeps asking for a password and will not accept my password from either my login or a SMB password from a Ubuntu SMB user.

Paul

---

### Post by PatchesTheCaveman on 2010-12-30
You need to use a username and password of an account on the Windows machine you are connecting to.  If you don't have a password set up on the Windows machine, enter *guest* as the username and leave the password blank.

If you don't want to require the username and password of a valid user on the Windows XP machine, I can assist you in enabling guest access.

---

### Post by PaulClarke on 2010-12-30
Hello again.

The "guest" in the name and no pass word did not work.  This is where I get lost.  I would think that we are not accessing the XP box as such but are browsing the whole of "workgroup".

We are now where I have gotten to last night.  I would be very happy to set up a "guest" option please.

Regards

Paul

---

### Post by PatchesTheCaveman on 2010-12-30
How are you browsing the workgroup?  I usually just go to Places > Network and I can see all of the 7 or so Linux and Windows machines running on my network.

I'd be glad to set up the guest option but I'm not sure that's your problem just yet.  Have you tried a valid username and password on the XP box?

---

### Post by PaulClarke on 2010-12-31
Hello,

I'm doing the same.  When I click on "workgroup" a window comes up requesting a password.

Nothing put in seems to work.  I have added users to the Samba software and I have added a new user to the XP box and tried that.  It still did not work.

Paul

---

### Post by PatchesTheCaveman on 2010-12-31
If you know the names of the computers you are connecting to, you can access them directly without going through the workgroup screen.

Just click Places > Connect to Server.  Change Service Type to Windows Share.  Enter the name of the computer in the Server box.  Leave everything else blank.  Click Connect.

You might be prompted for a username and password.  Try a valid account on the machine you're connecting to, or guest and and a blank password.  Enter the name of the computer you're connecting to in the Domain box.  You also have the option of having GNOME save your password information.

That should get you the share listing of that computer.  It will also create an icon on your desktop to that computer for future use.

If you get it to work that way, I can also instruct you on how to mount SMB shares so you can access them like they were a folder on that computer's hard drive, if you would like.

---

### Post by PaulClarke on 2010-12-31
Hello again,

Before I go to a NYE BBQ.

Yes I know how to mount external shared drives and I have a Lacie NAS that mounts on each reboot and it works a treat.  The main thing I am trying to do is browse the workgroup.

Thank you for your assistance and if you can think of anything else to allow this please let me know

Happy New Year.

Paul

---

### Post by Morbius1 on 2010-12-31
Just to make sure I'm not misinterpreting things:
> When I click on "workgroup" a window comes up requesting a password.You are being prompted for a password at the Workgroup level?
Or are you being prompted for a password at the host or share level?

If it's at the Workgroup level then this may be an encryption problem. Go into your /etc/samba/smb.conf file and look for the following line:
> encrypt passwords = Noand change No to Yes.

Then restart samba:
```
sudo service smbd restart
```That parameter pertains to both client and server.

---

### Post by supershin on 2010-12-31
Using the Samba gui you have to set the windows account you want to use. So under Administration -> Samba. Preferences -> Samba Users. Add a user and enter your windows machine username and password. When you get the prompt that username and password.

Looks like did that but did you enable sharing on that windows account. In windows control panel look for the option to enable file and printer sharing. You can turn on password protected sharing or the guest account access, enable one. Also ensure the windows firewall isn't blocking anything.

---

### Post by PaulClarke on 2010-12-31
Hello,

It is already "yes"

Here is the file

[global]
	log file = /var/log/samba/samba.log
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	force unknown acl user = yes
	create mask = 0777
	null passwords = yes
	winbind trusted domains only = yes
	encrypt passwords = yes
	winbind use default domain = yes
	public = yes
	dns proxy = no
	netbios name = Paul
	writeable = yes
	server string = Samba file and print server
	workgroup = workgroup
	os level = 20
	printcap name = cups
	security = domain
	max log size = 1000

[homes]
	comment = Home Directories
	path = /home
	read only = no
	available = yes
	browseable = yes
	guest ok = yes
;	printable = no
	locking = no
	strict locking = no

[Music]
	comment = test
	path = /home/paul/Music
	writeable = yes
	browseable = yes
	guest ok = yes

---

### Post by Morbius1 on 2010-12-31
Ah, you should have posted that first.  As I recall with "security = domain" Samba will try to authenticate the remote user by pointing to the Primary Domain Controller. This is beyond my level of expertise I'm afraid.

---

### Post by PatchesTheCaveman on 2010-12-31
Morbius1 is correct.  Try
```
security = user
```
instead.

Also if you still experience your browsing problem after you change that, changing the default
```
workgroup = workgroup
```
to another name other than the defualt "workgroup" in Samba and on your Windows computers to a custom name might help.

---

### Post by PaulClarke on 2011-01-01
Hello and thank you.

You are being prompted for a password at the Workgroup level?

answer yes.

I can mount external shared drives via FSTAB but I cannot browse the workgroup.

Regards

Paul

---

### Post by PatchesTheCaveman on 2011-01-01
Try adding this line to your *[global]* section:
```
wins server = yes
```

Then restart Samba.  From a terminal:
```
sudo service smbd restart
sudo service nmbd restart
```

You might need to reboot the Windows computers for them to respect the new configuration.

---

### Post by PaulClarke on 2011-01-01
Hello,

Sorry those things did not work.  Now it does not ask for a password it just times out.  The shares dealt with byt FSTAB still mount as usual.

Paul

---

