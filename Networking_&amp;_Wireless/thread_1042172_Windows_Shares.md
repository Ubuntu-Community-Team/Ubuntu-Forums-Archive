---
title: "Windows Shares"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by b747pete on 2009-01-17
I have a network running on a few Windows machines and a Mac. My linux machine is on the same network via an ethernet card and accesses the internet Ok, but when I try to access Windows shares I can only get as far as Places > Network > Network Servers > Windows Network and there I can see both the Workgroups that exist MSHOME and WorkGroup.

When I click on either there is no connection to any of the computers.

From Windows I cannot see the linux machine.

Any help will be appreciated. I have tried lots of threads and none get me where I want to go here!

Thanks.

---

### Post by Iowan on 2009-01-17
The linux machine may not be visible without Samba server installed.

Going the other way - see if this helps:
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by b747pete on 2009-01-17
Thanks for your response, i gives the following:

~$ smb://192.168.1.104
bash: smb://192.168.1.104: No such file or directory
peter@peter-linux-desktop:~$ smb://192.168.1.120
bash: smb://192.168.1.120: No such file or directory

When I link to [http://192.168.1.200](http://192.168.1.200) using Firefox I can access my printer webpage.

I can ping from terminal to the Windows machines.

Again, thanks.

---

### Post by Iowan on 2009-01-17
Looks like you entered the location from a terminal.  **superprash2003**'s How-To recommends:
> Step 1 : Go to Places->Computer.
Step 2 : The nautilus window should now pop up.
Step 3 : Now under "Go to" type smb://x.x.x.x where x.x.x.x is the ip address or the machine name of the windows machine which contains the shared folders and hit ENTER.As said earlier you can find that information by typing ipconfig in the command prompt of windows machine(eg 192.168.1.3)
Step 4 : Now you should be asked for a username and password, enter the appropriate username and password which is typically the windows login username and password.Or any other special account you setup.
Step 5 : Now you should able to see the shared files and folders 
(Illustrations omitted - check the link...)

---

### Post by b747pete on 2009-01-17
Thank you, that has allowed me access to the folders. Is there a simple way, or a way to automate that process in the future.

I do appreciate your reply, I have read dozens of posts without success.

---

### Post by b747pete on 2009-01-17
This is the output of smbtree, all of the computers are on 192.168.1.1xx IP addresses.

Does this mean anything.

Thanks.

Peter

WORKGROUP
	\\VIAODESKTOP    		Terrye's Computer
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Error connecting to 24.28.193.9 (Operation already in progress)
cli_start_connection: failed to connect to VIAODESKTOP<20> (24.28.193.9). Error NT_STATUS_ACCESS_DENIED
	\\MAC_XP         		MacBook_XP
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Error connecting to 24.28.193.9 (Operation already in progress)
cli_start_connection: failed to connect to MAC_XP<20> (24.28.193.9). Error NT_STATUS_ACCESS_DENIED
	\\MAC-BOOK       		Mac Book
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Error connecting to 24.28.193.9 (Operation already in progress)
cli_start_connection: failed to connect to MAC-BOOK<20> (24.28.193.9). Error NT_STATUS_ACCESS_DENIED
	\\HP-A6400       		
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Error connecting to 24.28.193.9 (Operation already in progress)
cli_start_connection: failed to connect to HP-A6400<20> (24.28.193.9). Error NT_STATUS_ACCESS_DENIED
peter@peter-linux-desktop:~$ smbtree
Password: 
WORKGROUP
	\\VIAODESKTOP    		Terrye's Computer
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Error connecting to 24.28.193.9 (Operation already in progress)
cli_start_connection: failed to connect to VIAODESKTOP<20> (24.28.193.9). Error NT_STATUS_ACCESS_DENIED
	\\MAC_XP         		MacBook_XP
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Error connecting to 24.28.193.9 (Operation already in progress)
cli_start_connection: failed to connect to MAC_XP<20> (24.28.193.9). Error NT_STATUS_ACCESS_DENIED
	\\MAC-BOOK       		Mac Book
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Error connecting to 24.28.193.9 (Operation already in progress)
cli_start_connection: failed to connect to MAC-BOOK<20> (24.28.193.9). Error NT_STATUS_ACCESS_DENIED
	\\HP-A6400       		
timeout connecting to 24.28.193.9:445
timeout connecting to 24.28.193.9:139
Error connecting to 24.28.193.9 (Operation already in progress)
cli_start_connection: failed to connect to HP-A6400<20> (24.28.193.9). Error NT_STATUS_ACCESS_DENIED

---

### Post by Roasted on 2009-01-17
Why not just set up a Samba connection? Except with Samba routing to your home directory on your Linux machine.

That would allow you to access all of your music, pictures, etc. 

I personally use Samba to treat my desktop like a file server. My little dinky 30gb iBook G4 taps into my Samba desktop and suddenly has access to 500gb of music and pictures. :) 

If you need help in the direction of Samba, I can at least let you know what I did. I'll check back here soon enough.

---

### Post by theozzlives on 2009-01-17
in a terminal type:
```
gksudo gedit /etc/samba/smb.conf
```
under the global section you'll see a line that says workgroup=WORKGROUP, change the one in caps to MSHOME. Exit, and type:
```
sudo /etc/init.d/samba restart
```

---

### Post by b747pete on 2009-01-17
workgroup was set to WORKGROUP and the second line of code returned

sudo /etc/init.d/samba restart
sudo: /etc/init.d/samba: command not found

I thought I had Samba installed?

---

### Post by maciu on 2009-01-17
looks like you have only smbclient installed, install samba with

sudo apt-get install samba

check the config and try again.

---

### Post by theozzlives on 2009-01-17
I'm sorry, since you saw your Windows workgroup, I thought you had samba installed.

---

### Post by b747pete on 2009-01-17
I have installed Samba, resstarted it, this is the "global" section of the conf file.

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

Is there something wrong in there, I can see "Workgroup" when I go Places > network Servers > Windows Network , but cannot see any computers, they are on Workgroup

---

### Post by b747pete on 2009-01-17
Now I can see the "linux-desktop" from all the other computers on the network, 1 x XP, 1 x Vista and 1 x Mac OSX, but still cannot see them from the Linux machine.

I guess I need to enalble sharing to be able to see the floders on the linux machine from Windows.

Thanks fr all the help!

---

### Post by sergueik on 2009-01-18
I had that exact problem I think. I have Winxdows XP Home laptoip, Windows XP Pro tower, and Mac OSX computer. They all can share files and a printer attached to WInXPPro machine. Recently I got me Lenovo Ideapad S10e which came with preinstalled XP Home. It is pretty-weak computer, so Ubuntu was a logical choice to make it into a better computer. However, once that was done, I could not share files between it and the rest of the computers I have. Pretty much the same symptoms: can not ping it or ping from by network names (can ping from by IP). Can also ping by name.local.
I was determined not to mod anything in my windows, mac, firewall, or monkey with DNS and DHSP settings. I knew the problem was with ubuntu and I stick to looking for it.

At the end I have commented some lines in smb.conf file and now evrything works great. Her eis the snippet from my smb.conf. This is just top few lines. I have added "#" in front of 4 lines, reboot.. and it works fine, I can see and ping back and forth no problem.


> 
netbios name = Lenovo S10e
server string =
workgroup = Workgroup
security = user
#hosts allow = 127. 192.168.0.
#interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
#remote announce = 192.168.0.255
#remote browse sync = 192.168.0.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = yes
username level = 2
password level = 2
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = lmhosts bcast wins host
wins support = no
wins proxy = no
dns proxy = no
...


At this stage I have not changed anything bellow this.

---

### Post by b747pete on 2009-01-18
Thanks for the input.

My smb.conf does not look anything like yours, mine looks very generic actually with no input from me to change it.

I have lots of log files in var/log/samba but they don't mean anything to me, but a common them seems to be "failed to create users or failed to create administrator".

Does this mean anything?

Thanks.

---

### Post by b747pete on 2009-01-24
I don't really know how I fixed this, but it now works.

I think one of the most important comments I can add to this is that one should REBOOT after a lot of these changes.

My success came after a reboot, following some changes here and there.

smb://xxx.xxx.xx.xxx is Ok and you can bookmark too, but if the IP address of the target changes, you have to redo it. I guess you could go with fixed IPs.

My short bit.

Peter

---

