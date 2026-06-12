---
title: "Samba and Windows Networking Guide"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by bferd on 2011-04-26
**[SIZE="4"]All[/SIZE] props to [Stormbringer]("http://ubuntuforums.org/member.php?u=56737")** who back in 2006 made a [killer tutorial]("http://ubuntuforums.org/showthread.php?t=202605") for this. It helped me a lot. All I did is update his hard work for the latest versions.

**1. Prerequisites**

- Your main Linux box should have an static ip-address. (eg: my home server)
In case you're getting your ip from a router/server via DHCP make sure it's configured to provide a fixed dhcp-lease. If that's no valid option you cannot use WINS ... more on this way down.

- You need to have samba installed.
If you haven't done so already open a terminal and type:

```
sudo apt-get install samba
```

Don't close the terminal upon installation - we still need the commandline to get several tasks done!


**2. Getting samba configured**

First, let us make sure samba isn't running:

```
sudo stop smbd
```

As a starting point I included an smb.conf below, and there are only a few simple things you may need to tweak.

Since the installation of samba just installed a rather useless template file we're going to rename it - we keep the file just in case.

```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.template
```

Next we create a new empty file

```
sudo touch /etc/samba/smb.conf
```

And finally we need to open the file inside an editor

```
sudo gedit /etc/samba/smb.conf
```

[COLOR="Red"]NOTE:[/COLOR] If you're on KDE replace "gedit" with "kate"

Copy / Paste the contents of the code-section below into your editor. Make a note of the [COLOR="Red"]red highlighted[/COLOR] text as these are things that you will need to edit as per your system.

```
[global]
    ; General server settings
    netbios name = [COLOR="Red"]YOUR_HOSTNAME[/COLOR]
    workgroup = [COLOR="Red"]YOUR_WORKGROUP[/COLOR]
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = wins lmhosts hosts bcast

# WINS SETTING
# NEVER set "wins support = yes" on more than one machine in your network
# "wins support = yes" and the "wins server xxx.xxx.xxx.xxx" option are mutually exclusive; you cannot simultaneously offer Samba as the WINS server and point to another system as the server

    [COLOR="Red"]wins support = no[/COLOR]
# or (not both)
#   [COLOR="Red"]wins server xxx.xxx.xxx.xxx[/COLOR]

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

[COLOR="Red"][SHARED_FOLDER][/COLOR]
    path = [COLOR="Red"]/home/USER/SHARED_FOLDER[/COLOR]
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]YOUR_USERNAME[/COLOR]
    force group = [COLOR="Red"]YOUR_USERGROUP[/COLOR]
```

Ok, I already mentioned that there are a few things you will need to change (in red); so here they are:


[INDENT]netbios name = YOUR_HOSTNAME[/INDENT]


Replace "YOUR_HOSTNAME" with your desired hostname (don't use spaces!). Best practice would be to use the same name you configured upon installation.

Example:

netbios name = fileserver


[INDENT]workgroup = YOUR_WORKGROUP[/INDENT]


Replace "YOUR_WORKGROUP" with the name of your workgroup, but make sure you're using the same as configured in Windows.

To find out the Workgroup name in Windows follow these steps:

- Click "START"
- Click "Control Panel"
- Click "System"
- Click the 2nd Tab entitled "Computer Name" and find the name of the Workgroup there.

Example:

workgroup = SCHROTHNET
(yes I know that's geeky)


[INDENT]wins support = no [/INDENT]

If your not setting up some sort of server that runs all the time leave as default
If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, leave as default.

In this case you cannot use the benefits of WINS.


[INDENT]# wins server xxx.xxx.xxx.xxx[/INDENT]


If you have another linux box set up as a wins server uncomment this line and enter the ip of your wins server.

See dmizer's post below and follow the link to learn more about wins and samba


[INDENT][MyFiles][/INDENT]


This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!


[INDENT]path = /home/USER/SHARED_FOLDER[/INDENT]


What I did is shared individually my Music folder, Pictures folder etc.

eg. path = /home/brad/Music

If you have more folders to share add to your smb.conf file using the SHARED_FOLDER format.

Remember that this is just an example - you are free to put things wherever you like.

[INDENT]force user = YOUR_USERNAME
force group = YOUR_USERNAME[/INDENT]

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

eg:

force user = brad
force group = brad

Now we completed the part of editing smb.conf

Save the file and close gedit.

If you are going to have a shared folder with other users we should now make sure that the permissions are set. Type:

sudo chmod 0777 /home/USER/SHARED_FOLDER

[COLOR="Red"]NOTE 1:[/COLOR] 0777 gives everybody on you home network read and write permissions.

[COLOR="Red"]NOTE 2:[/COLOR] Don't forget to correct the path to the location you chose above!

That's it - now we need to start samba ...


**1.1 Starting samba and setting up user accounts**

Let us fire up samba for the first time. Type:

```
sudo start smbd
```


Time to add yourself as an samba user.

[COLOR="Red"]NOTE:[/COLOR] You will be asked for a password - make sure you use the same as you use for login!

Code:

sudo smbpasswd -L -a YOUR_USERNAME
sudo smbpasswd -L -e YOUR_USERNAME

In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

[COLOR="Red"]NOTE:[/COLOR] Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!

In the following example we will add an user called "brad" ...

Example:

Code:

sudo useradd -s /bin/true brad
sudo smbpasswd -L -a brad
sudo smbpasswd -L -e brad

The "-s /bin/true" in the first line prevents the users from being able to access the commandline of your linux box ("-s" stands for "shell"). I strongly advise you to follow this recommendation! Don't change that setting to a valid login-shell unless you really know what you are doing!

Repeat this step until you configured all user accounts!

Now that we configured samba and created the user accounts we are done with the Linux-part - there's one more thing to do in Windows.


**2. Changing network settings in Windows 7 **

Now we should let Windows know that there's a WINS server active in the network.

**If you left "wins support = no" above, skip this step!**

- Click "START"
- Click "Control Panel"
- Click "Network and Internet" from there open "Network and Sharing Center"
- On the left side, click the link "Change adapter settings"
- Right click on your Local Area Connection icon and select "Properties" from the list.
- Double click on "Internet Protocol Version 4 (TCP/IPv4)"
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in the ip-address of your Linux box
- Click "Add"
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot Windows

Upon reboot you may now map the network drive within Windows.

With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Browse to folder, or type \\NAMEOFSERVER\MyFiles (eg. //FILESERVER/Documents)

[COLOR="Red"]NOTE:[/COLOR] Adjust this to the hostname and sharename you chose above!
- Click "Finish"

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address-of-ubuntu-machine>\MyFiles (eg. //192.168.0.101/Documents)

[COLOR="Red"]NOTE:[/COLOR] To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.
- Click "Finish"

That's it - samba is up and running now.


**3. Security consideration**

This is the right time to think about security right away.

In case your computer has more than one network connection (i.e. wired and wireless Ethernet) you may want to restrict access to samba.

If not especially configured samba will bind its service to all available network interfaces.

So, let us assume you only want your wired network to have access and that the network card is called eth0.

Add the following lines to the [general] section of your smb.conf to achieve that goal:

```
interfaces = lo, eth0
bind interfaces only = true
```

If you did it correctly it should look similar to this:

```
[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true
```

Now only the local loopback interface (dubbed "lo") and eth0 are able to access samba - there's no need to fear that someone might break into your system by wireless as the interface isn't bound to the service.


**4. Final words**

If you happen to have any questions feel free to ask - I'll try to help as soon as possible.

If you find any mistakes in this howto please let me know so that I can fix them.

Feel free to contribute and suggest - help to make this howto a better guide.

---

### Post by not_a_phd on 2011-04-26
Thank you! Exceedingly helpful and timely.

---

### Post by bferd on 2011-05-18
Not a problem, I use this as a Ubuntu to Windows networking guide every time I install Ubuntu. It works well even on Ubuntu 11.04 Natty.

---

### Post by roma0607 on 2011-05-18
I did all of the instructions above, but in can't connect the network disk. Windows write me that "Windows can't access the \\Ubuntu\workspace" . I think that I taped the wrong ip (there are two in ifconfig / eth1). Both didn't work; please, tell me the possible mistakes.

Thanks for your help.

---

### Post by bferd on 2011-06-30
This guide assumes you already have you Ethernet connections set up (eth0, eth1, etc.), or left default after installing Ubuntu. If you have been making changes to your networking connections your best bet is to reset them back to default.

open Network connections "System > Preferences > Network Connections"

edit _each_ of your network connections (eth0, eth1)

in the "IPv4" tab select Method > "Automatic (DHCP)"

click "Save"


On your windows 7 machine open your control panel and click "Network and Internet" from there open "Network and Sharing Center"

On the left side, click the link "Change adapter settings"

Right click on your Local Area Connection icon and select "Properties" from the list.

Double click on "Internet Protocol Version 4 (TCP/IPv4)"

make sure both radio buttons are on "Obtain IP Automatically" and "Obtain DNS Automatically"


If you did set up your Ubuntu machine to be a WINS server click the "Advanced" button.

Click the WINS tab

Add the IP of your Ubuntu machine

---

### Post by ImTheBatman on 2011-08-01
Hi,

Sorry for bumping this old thread, but I have a problem with sharing. I have a windows 7 machine and a linux machine connected in LAN via an ethernet switch. I have configured windows 7's share on the workgroup "WORKGROUP" (it works with other windows 7 machines, tested) and configured linux exactly as you said on the same workgroup (wins is off). I see the workgroup on both machines but each of them only sees itself.

I noticed windows 7 has a very weird sharing mechanism (a global password is required to connect a new computer to the workgroup, but then no passwords are required to access shares whatsoever). Is it possible that this mechanism requires special configuration on linux?

Regards,
The Batman

---

### Post by doru001 on 2011-08-02
Thank you[COLOR=Black] **bferd**, you saved me. 

The default config does not work because of encrypt passwords = no. 

If you want to give access to [/COLOR][COLOR=Red]YOUR_USERNAME[/COLOR] only, remove the two "force" lines. 

Most options in your /etc/samba/smb.conf example file are not required because they correspond with the default values or are even useless in the given context. smbusers, for example, is not there. 

This works for me: 
> 
[global]
    netbios name = [COLOR=Red]YOUR_HOSTNAME[/COLOR]
    workgroup = [COLOR=Red]YOUR_WORKGROUP[/COLOR]
    server string = [COLOR=Red]YOUR_DESCRIPTION[/COLOR]
[shared]
    path = /home/[COLOR=Red]YOUR_HOSTNAME[/COLOR]/[COLOR=Red]YOUR_SHARED_FOLDER[/COLOR]
    writeable = yes
#   comment = [COLOR=Red]YOUR_FOLDER_DESCRIPTION[/COLOR]
[COLOR=Red]YOUR_USERNAME[COLOR=Black] is the [/COLOR][/COLOR]only user who has access, with a password, to [COLOR=Red]YOUR_SHARED_FOLDER[COLOR=Black]. 

The samba user must be created as you said. 

I am not sure whether the wins address needs to be added in the Windows client. 
[/COLOR][/COLOR]

---

### Post by bferd on 2011-08-23
> **ImTheBatman said:**
> Hi,

 Is it possible that this mechanism requires special configuration on linux?



The windows 7 pc will not show up in Ubuntu unless there is a shared folder.
To share a folder in Win7 there is a 2 step process.

(Do not try to share library folders ie Documents, Music, etc. If you want to share these files navigate to C:\Users\Brad and then share Documents, Music etc.)

Step one sharing the folder
first right click on the folder you want to share.
click properties
click sharing tab
click share
Add the people you want to share with (make sure your user name is there)
click the share button.

Think your done right? Wrong.


Back on the properties window click "Advanced Sharing"
put a check in the "Share this folder" check box
Click the "Permissions" button
Default is to Everyone is fine or if you think you need to add your user name.
click the full control Allow check box.
click OK

Now your Win7 machine will be visible in Ubuntu

---

### Post by dmizer on 2011-08-24
A few comments:

The "server string =" option is left blank. Why include it in the smb.conf file at all? I suggest either removing it or giving directions on how to fill the option properly.

The "announce version = 5.0" Should not be manually set. From samba man pages:
> **Do not change this parameter unless you have a specific need to set a Samba server to be a downlevel server**.

The "wins support" option is largely misunderstood. Wins support does not mean that wins is enabled. It means the following:
```
       wins support (G)

           This boolean controls if the nmbd(8) process in Samba will act as a
           WINS server. [B]You should not set this to yes unless you have a
           multi-subnetted network and you wish a particular nmbd to be your
           WINS server[/B]. Note that you should NEVER set this to yes on more
           than one machine in your network.

           Default: wins support = no
```
This option should be left as the default. Stormbringer did not leave it as default as he originally had plans for explaining its proper use in detail. For more information on how to configure Ubuntu as a wins server, please see this samba help document: [http://oreilly.com/openbook/samba/book/ch07_03.html](http://oreilly.com/openbook/samba/book/ch07_03.html) 

Note here:
> The wins support=yes and the wins server option are mutually exclusive; you cannot simultaneously offer Samba as the WINS server and point to another system as the server.

---

### Post by bferd on 2011-08-25
Changes made, thank you for your suggestions.

I understand you concern with the wins server settings but I left it in the example smb.conf so people understand their options.

---

### Post by slotdoctor on 2011-09-01
> **bferd said:**
> **[SIZE="4"]All[/SIZE] props to [Stormbringer]("http://ubuntuforums.org/member.php?u=56737")** who back in 2006 made a [killer tutorial]("http://ubuntuforums.org/showthread.php?t=202605") for this. It helped me a lot. All I did is update his hard work for the latest versions.

[INDENT][MyFiles][/INDENT]


This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!


[INDENT]path = /home/USER/SHARED_FOLDER[/INDENT]


What I did is shared individually my Music folder, Pictures folder etc.

eg. path = /home/brad/Music

If you have more folders to share add to your smb.conf file using the SHARED_FOLDER format.

Remember that this is just an example - you are free to put things wherever you like.

[INDENT]force user = YOUR_USERNAME
force group = YOUR_USERNAME[/INDENT]

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

eg:

force user = brad
force group = brad

Now we completed the part of editing smb.conf

Save the file and close gedit.

If you are going to have a shared folder with other users we should now make sure that the permissions are set. Type:

sudo chmod 0777 /home/USER/SHARED_FOLDER

[COLOR="Red"]NOTE 1:[/COLOR] 0777 gives everybody on you home network read and write permissions.

[COLOR="Red"]NOTE 2:[/COLOR] Don't forget to correct the path to the location you chose above!

That's it - now we need to start samba ...

**4. Final words**

If you happen to have any questions feel free to ask - I'll try to help as soon as possible.

If you find any mistakes in this howto please let me know so that I can fix them.

Feel free to contribute and suggest - help to make this howto a better guide.

Thank you for a most easy to understand know how. I am grateful. I only need some clarification, pardon my stupedity.

For each folder; Data, Music, Pictures, Work etc. 

1. Do I need a share, the name of the share is the same as the name of the file?

2. Do I create and give permission to each file individualy or as a group?

3. The Netbios/Hostname is the same as the computer(server)?

Many thank you's for all your help.

---

### Post by bferd on 2011-09-03
To answer your questions

1 Your Share name does not have to be the same as the folder name.

2 You might be able to give permissions to multiple folders at the same time but I don't know how to do it. I just do it one at a time.

3 Yes the Netbios/Hostname is the name you want to give that computer to distinguish it from the other computers on your network.

---

### Post by bferd on 2011-09-03
> **doru001 said:**
> 

If you want to give access to [/COLOR][COLOR=Red]YOUR_USERNAME[/COLOR] only, remove the two "force" lines. 



[SIZE="4"]People take note.[/SIZE] If you have multiple users shares on your file server and only want each user to access their own share, doru001 suggests removing the [COLOR=Red]force user =[/COLOR] and [COLOR=Red]force group[/COLOR] = lines.

I leave them in because I have multiple users, some accessing the same shares and some accessing different ones.

you can achieve this by adding some or all of the following tags to the Share section of your smb.conf file

```

	valid users = 
	invalid users = 
	user = 
	read list = 
	write list = 
```

For example here is the share Videos section of my smb.conf

```

[Videos]
	path = /home/brad/Videos
	writeable = yes
	valid users = brad,julie,@brad,@julie
	invalid users = talitha,emily,maggie,@talitha,@emily,@maggie
	user = brad,julie,@brad,@julie
	read list = julie,@julie
	write list = brad,@brad
	force group = brad
	force user = brad
	create mask = 0644
	directory mask = 0755
```

Here me and my wife have access to the folder, but only I can make changes. Our three daughters do not have access to the folder.

---

### Post by celiapgt on 2012-01-28
THANK YOU very much!!!
It was of much, much help. Thanks.

---

### Post by GaryRixon on 2012-10-19
Thank you so much! Been trying to sort out my samba server for days.

I've saved this whole tutorial so I can look at it whenever I need to :D

THANKS AGAIN!

---

