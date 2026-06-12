---
title: "File sharing in Natty is beyond me :("
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by Amused2Death on 2011-09-02
Ok here is the scenario:

1st computer, desktop dual boot winxp and ubuntu 11.04
2nd computer, laptop dual boot win7 and ubuntu 11.04

Boot up both machines in Ubuntu, no firewalls going (in any OS on either machine) and i get "Unable to mount location : Failed to retrieve list from the server"

I have googled myself to death, followed many pieces of advice and still am stuck with the same result.
There is one other PC on the LAN,  and in the workgroup running win xp but its not required to share anything at this point in time.

Samba is running, and the gui is installed in system/admin/samba and everything looks right.

Surely it should be simple to get 2 ubuntu machines running the same version, to share 1 folder. I cant understand why some of the advice is to turn off firewalls in the windows OS's as they are not in use.

I have edited the smb.conf, all pc's are in the same workgroup.. i am at a loss.

Does anyone have any ideas before i am forced to boot into windows and share/transfer.

I should point out all 3 machines are visible under network, and also visible under windows network/workgroup name.

Is there a way i can share between ubuntu machines without the windows workgroup???

Thanx in advance

---

### Post by kerry_s on 2011-09-02
sounds like you did it the hard way.
all you have to do is right click the folder you want & select share, that's it. no editing files, no messing with samba, nothing.

---

### Post by Amused2Death on 2011-09-03
yup, did all that..

my question is how do i navigate to the shared folder on the other computer.
quite obviously network isn't doing it for me :(

I apologize for my windows upbringing, i am trying to change :)

---

### Post by spiky001 on 2011-09-03
If both machines are running linux try installing ssh server on both machines, to acsess my windows xp from ubuntu i just went to network in nautilus then windows network and I could get the files from shared folders

---

### Post by kerry_s on 2011-09-03
> **Amused2Death said:**
> yup, did all that..

my question is how do i navigate to the shared folder on the other computer.
quite obviously network isn't doing it for me :(

I apologize for my windows upbringing, i am trying to change :)

just go to network places in nautilus, it show whats on your network, then just click on it like any other folder.

here's what it looks like on mine, i'm using lubuntu which has pcmanfm, so it's different than nautilus.

---

### Post by headvampyre@hotmail.co.uk on 2011-09-03
This is kind of confusing :/ Are you looking to share both of the Ubuntu machines with each other(Only Ubuntu can be done via NFS), or with Windows as well(Samba can do this, but smbclient can be buggy)

---

### Post by Morbius1 on 2011-09-03
This is just a suggestion but it would be good if we can see some facts to go along with your description of your setup. Please post the output of the following commands:
```
testparm -s
net usershare info --long
smbtree
hostname

```[I]Note: in case you are wondering why I'm asking for hostname it has to do with an oversight in the Ubuntu installer. Unless you are quick enough to spot it the installer will by default create a machine name that other memebers of the lan cannot see. For example, by default the installer will make this my machine name:
> morbius1-desktop That's 16 characters long. It can only be up to 15 characters long. It's a Samba requirement not a Linux requirement. Easy enough to fix in smb.conf itself but ....[/I]

---

### Post by kherring7383 on 2011-09-03
I can certainly understand your frustration. I too have had this issue trying to share my XP box that I access through Terminal Client so that I can move files back and forth between the two. I did come across this like that you might want to take a look at. I hope it helps.
[http://www.liberiangeek.net/2010/11/enable-file-sharing-windows-xp-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/11/enable-file-sharing-windows-xp-ubuntu-10-10-maverick-meerkat/)

---

### Post by Amused2Death on 2011-09-04
Originally i had 1x Ubuntu and 1x Winxp (wifes) computers networked. Downside was i could only transfer files from her pc.

So i then bought a laptop with Win7, immediately installed Ubuntu and all i wish to do is transfer files between the 2 Ubuntu machines. I have no need to bother networking the winxp machine anymore, i can simply use a flash drive for the "once in a blue moon" need to share files.

Results:

1...testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Movies]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MYSTICS
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	encrypt passwords = No
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Movies]
	path = /media/The Cave/Movies
	read only = No
	guest ok = Yes

2..net usershare info --long
info_fn: file /var/lib/samba/usershares/movies is not a well formed usershare file.
info_fn: Error was Path is not a directory.

3..smbtree
Enter *******'s password: 
Server requested plaintext password but 'client plaintext auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested plaintext password but 'client plaintext auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

4...hostname
gave the correct name of this computer.

I do have Samba installed on both machines, i would be happy to get rid of the windows network and simply do whatever to get the laptop and desktop machines to play nicely.

btw the files i want to transfer from the desktop pc are on a separate partition/hard drive. There is 1x windows, 1x Ubuntu and 2x shared

Thanks again for your assistance

---

### Post by kerry_s on 2011-09-04
> btw the files i want to transfer from the desktop pc are on a separate partition/hard drive. There is 1x windows, 1x Ubuntu and 2x shared

then it needs to be mounted using fstab & you need to create the folder "The Cave" in /media for it to mount to.

mine looks like this.

---

### Post by spiky001 on 2011-09-04
To transfer between to ubuntu machines install ssh server, that will allow you to transfer between them, You can even use Nautilus, Thats how mine works

---

### Post by nothingspecial on 2011-09-04
You really don't need samba

On both machines

```
sudo apt-get install openssh-server
```

On an empty workspace go to the menubar and choose file > connect to server


[ATTACH]201441[/ATTACH]

Fill in the details like so

[ATTACH]201442[/ATTACH]

You can find the ipaddress of the other computer by right clicking the network icon (on the other computer) and choosing connection information.

You can choose any folder, I have chosen / to give me access to the whole filesystem.

The user and password are the user and password on the other machine.

After you click connect (it might give you a warning, just choose to connect), a file browser window will open and the connection should be visible in the sidepane - stfp//blahblahetc. Right click it and choose add bookmark.

[ATTACH]201443[/ATTACH]


The other computer will now be available for ever more from a bookmark from your browser window. Just repeat the process on the other machine and voila :guitar:

---

### Post by spiky001 on 2011-09-04
Also you can open extra pane and have the server folder in there client folder in the other pane for drag and droping, With ssh at a later date you can access from outside your lan with a few mods

---

### Post by Morbius1 on 2011-09-04
[1] You have a number of things wrong with your smb.conf so I would suggest you make the following changes:
 
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Change these lines:
> security = SHARE
encrypt passwords = No
To this:
> security = user
encrypt passwords = Yes
Then restart samba:
```
sudo service smbd restart
```[2] To reiterate what [COLOR=Blue]**kerry_s**[/COLOR] said there may be a problem with the permissions on the target folder: /media/The Cave/Movies.

If it's sitting there with permissions of 0700 and you allowed guest access then the remote user will not even know that share exists. You will need to change permissions or since you only have a guest share you can add one more line to the [global] section of smb.conf:
```
force user = whatever-your-ubuntu-login-user-name-is
```Then restart samba ( see above )

[3] Is "The Cave" mounted?
This would indicate that it is not:
> 2..net usershare info --long
info_fn: file /var/lib/samba/usershares/movies is not a well formed usershare file.
info_fn: Error was Path is not a directory.Always make sure the partition is mounted before trying to access the share remotely. Or have it mounted at boot as suggested by kerry_s.

[4] Still don't know how long your hostname is. This doesn't answer my question:
> 4...hostname
gave the correct name of this computer.If it's more than 15 characters long then you can change it to something less for networking purposes by adding another line to the [global] section ( under workgroup ) :
```
netbios name = some-name-15-character-or-less-in-length
```Then restart samba ( see above ).

---

### Post by kerry_s on 2011-09-04
i would also change "The Cave" to one word, like "The-Cave" or "The_Cave".

i didn't touch smb.conf at all. just did fstab then added it to "shared folders" in lubuntu.

---

### Post by Amused2Death on 2011-09-06
Thanks,

the learning curve can be a little steep when i am time poor.

I appreciate your time spent assisting me.

Morbius1, the host name is The Witcher, I use Ubuntu 11.04 classic and when i click on The Cave or The Vault its automatically mounted on my desktop. Well thats my assumption when the icon appears and if i right click i have the option to unmount.

As stated unfortunately at the moment i am doing some very long hours at work, leaving me with little time to read up, which is what i normally try to do if i have a problem.

I will make the changes to smb.conf and see how i go. I will also try the ssh server option as i try to get a better handle on Linux.

---

