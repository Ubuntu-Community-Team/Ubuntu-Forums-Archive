---
title: "Samba Problems with Windows 7"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by Canyonero on 2010-07-25
I'm not sure how to go about this problem. I've done many searches both here on the forums and on the web at large and can't seem to solve this problem.

I upgraded my computers (2 of them) from XP and Vista to Windows 7 Professional. One is 32-bit, the other is 64-bit. Both initially had no problems connecting to my Ubuntu machine (Jaunty). I mounted the Ubuntu drives on both and set to always mount on startup. Then my hard drive died on one of the machines (the 64-bit machine)and I had to reinstall Windows on a new drive. Since I did, I can't connect to Ubuntu, let alone mount shares. I've also noticed that while I can access the shares already mounted on the other Win 7 machine, I can no longer see the Ubuntu machine through the network explorer.

I also can no longer see my Ubuntu shares from my Mac, running Leopard, which I just realized. I had been trying to fix this on the windows machines, assuming that it was a Windows problem, not being able to see the machine from OS X suggests to me that something broke on the Ubuntu machine.

One of the two Windows 7 machines sees the share I have on Leopard (OS X), but not the one that had the hard drive die. 

I also have another old box running Debian Lenny. None of my boxes see that machine either.

Any ideas?

---

### Post by Canyonero on 2010-07-25
If this helps: Running 'smbtree' from both Linux machines shows the shared folders on the Mac, but not each other or either of the Windows machines.

---

### Post by Unterseeboot_234 on 2010-07-26
I have Win7 64 / Ubuntu 10.04-64 dual boot on one box, and ubuntu 9.10-64 on another box all wired together with DNS modem for DLS internet access. The only way I can share a printer or copy / write a file is to use the HomeGroup feature of Win7. Use this link

**[Windows 7, 7tutorials]("http://www.7tutorials.com/how-change-workgroup-windows-7")**

Basically, you make sure you have a user on Win7. That user is 'joined' to a Workgroup. Make a note of the name of that Workgroup, it can be named what you like, say: MyWorkgroup.

Edit the Samba config file on your Ubuntu box. There is a line of script you have to edit that says workgroup = "myworkgroup" ( or whatever the name is ). Reboot, or shutdown / restart Samba. Now you have two boxes in the same orbit flying on your network.

Go back to the Win box, logged in as the user. The user grants access privileges to folders, and also file types. (It's fuzzy why this is).

Back on the Ubuntu box, [Menu] Places --> Network.

View my attached screen capture. You want the Windows Network (that's SAMBA). Open, you see the name of your Workgroup. Open, you see the members of the workgroup. Open the Win box icon. Open the folder Users. Open the defined user from Win7. Inside that User Profile folder is where you have the definitions of the assets you can use.

You may NOT use Volume level hard drive access from Win7, eg. > \C:

Hope that helps. This workgoup metaphor is still fuzzy to me. I have googled and found other, weird HowTos via hacking the Windows Registry, or Administrator privileges ... I guarantee you that you don't want to do those sort of hacks.

It is a lot easier to set up a share account on the Ubuntu box that Win7 can see. Use the 7tutorials link I show you to try that feature.

Good luck.

---

### Post by Canyonero on 2010-07-26
Thanks so much for your help, but there are a few issues. First, I'm trying to go in the other direction. I use the Linux boxes as file servers. Right now I have a lot of stuff on them I want copied to the new install of Windows and have to use Filezilla.

Another issue I have is that I had a recent disaster in my home (basement flooded). As a result, the computers were untouched, but had to be moved upstairs. The Linux box in question is shoved into a corner and is "headless" (both are actually). I don't have access to a monitor for it (long story), so I can only do things via ssh/command line.

It's frustrating because everything worked fine until about a week or two ago. Nothing on either Linux box has changed, unless doing a regular software upgrade (aptitude safe-upgrade) changed something. 

I've even been looking into trying to get the computers on the network talking to the Linux boxes with NFS, as it appears they can still see each other that way. No luck yet. It appears Windows has NFS services, but only for the Ultimate and Enterprise editions, I have professional.

---

### Post by Morbius1 on 2010-07-26
> I also can no longer see my Ubuntu shares from my Mac, running Leopard,  which I just realized. I had been trying to fix this on the windows  machines, assuming that it was a Windows problem, not being able to see  the machine from OS X suggests to me that something broke on the Ubuntu  machine.Let's focus on this aspect a bit and see if anything is configured "funny" on your ubuntu machine. Please post the output of the following commands:
```
net usershare info
sudo net usershare info
testparm -s

```

---

### Post by Canyonero on 2010-07-26
Also to clarify, it was a little difficult to find at first, but I did get the workgroup names changed on the Windows machine to match what they had always been. Having workgroups of different names doesn't appear to be the problem.

---

### Post by Morbius1 on 2010-07-26
> **Canyonero said:**
> Also to clarify, it was a little difficult to find at first, but I did get the workgroup names changed on the Windows machine to match what they had always been. Having workgroups of different names doesn't appear to be the problem.
That's because having the same workgroup name on all machines is a Samba myth. Bless you for posting your last post ;)

---

### Post by Canyonero on 2010-07-26
net usershare info  returns nothing, just goes back to the command line.

sudo net usershare info does the same

testparm -s   (a few names changed for privacy, {Wife's Backup} is actually my wife's name - "user" is my name)
> user@dolphin:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[files on dolphin]"
Processing section "[{Wife's Backup}]"
Processing section "[web]"
Processing section "[backup on dolphin]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
        workgroup = WORKGROUP
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = lmhosts wins bcast host
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[files on dolphin]
        path = /files
        read only = No
        guest ok = Yes

[{Wife's Backup}]
        path = /files/{Wife's Backup}
        read only = No
        guest ok = Yes

[web]
        path = /var/www
        read only = No
        guest ok = Yes

[backup on dolphin]
        path = /backup
        read only = No
        guest ok = Yes
user@dolphin:~$
I KNOW this is insecure. We can worry about that later, if at all.

---

### Post by Morbius1 on 2010-07-26
So many people are using "security = SHARE" in this forum I'm going to have to look at my old SuSE 6.3 notes to see if I can remember all the rules.

Ignoring that for the moment, you have something missing. You don't have any way of creating a guest user. There should be a line in the [global] section that looks like this:
```
map to guest = Bad User
```Despite it's name, what it does is convert an un-authenticated remote user to the default guest account in samba and this allows guest access. Maybe it's not needed when "security = SHARE" is used, I simply don't remember.

The other thing is what you're sharing:
> path = /files
path = /files/{Wife's Backup}
path = /var/www
path = /backupThe way you set up these share is for guest access. Samba is allowing guest access but what are the Linux permissions on those directories. They have to match. The samba "guest" correlates to having "other" set to rwx.

So for example, do the following command:
```
ls -dl /backup
```It should come back with something like this:
> drwxrwxrwx 4 root root

---

### Post by Canyonero on 2010-07-26
Hey Morbius1, I really appreciate your help!

I have always set all permissions for shared folders to 777 or drwxrwxrwx.

Adding "map to guest = Bad User" appears not to have done anything

---

### Post by Morbius1 on 2010-07-26
You did restart samba after making the change?
```
sudo service smbd restart
```While I think of it, are all the samba related services running:
```
sudo service smbd status
sudo service nmbd status

```[COLOR=Blue]EDIT: Didn't read your original post carefully enough. You're using Jaunty:[/COLOR]
```
 sudo service samba restart
```
That's the only command you need for jaunty.

---

### Post by Canyonero on 2010-07-26
I did run ```
sudo /etc/init.d/samba restart
```which appears to do the same thing :D

---

### Post by Morbius1 on 2010-07-26
How about some other obvious things:

(1) Firewall. If you've done anything with the firewall on the Ubuntu machine - disable it. If you haven't touched it should be OK.

(2) Host name. By default samba will use the host name to broadcast it's presence to the network but the name has to be 15 characters or less.

---

### Post by Canyonero on 2010-07-26
I don't think there's a firewall. There hasn't been anyway. If an upgrade ended up putting one on, I didn't notice.

As for host name, I'm not sure about that one. Where would that be set?

---

### Post by Canyonero on 2010-07-26
Found it, the host name is "dolphin", which it has always been.

---

### Post by Canyonero on 2010-07-26
Also, I don't think this matters much, but everything on my network has a static local IP address.

---

### Post by Morbius1 on 2010-07-26
From the Debian box,

Post the output from this command:
```
smbtree
```

Also from the debian box, can it access the Ubuntu box directly:

In a terminal run:
> nautilus smb://192.168.0.100
[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the Ubuntu box.*[/COLOR]

---

### Post by Canyonero on 2010-07-26
smbtree from Debian:
> user@frog:~$ smbtree
Password:
WORKGROUP
        \\LEOPARD                       Leopard
                \\LEOPARD\(wife)'s public folder       (Wife)'s Public Folder
                \\LEOPARD\guest's public folder guest's Public Folder
                \\LEOPARD\(user)'s public folder  (User)'s Public Folder
                \\LEOPARD\IPC$                  IPC Service (Leopard)
user@frog:~$
LEOPARD is the Mac

nautilus:
> user@frog:~$ nautilus smb://192.168.1.4
cannot open display:
Run 'nautilus --help' to see a full list of available command line options.
user@frog:~$
It looks to me like this requires the gui, which I don't have at the moment. Both boxes are headless for about another 2-3 weeks until my basement gets fixed up.

---

### Post by Morbius1 on 2010-07-26
Sorry, not paying attention again.
Can the debian machine access the ubuntu machine by ip address is what I'm after.

[COLOR=Blue]EDIT: Or can you use the "Connect to Server" in Finder to access the ubuntu machine by ip address from the MAC.[/COLOR]

---

### Post by Canyonero on 2010-07-26
Strangely enough, going that way, I can connect to both via smb, but not nfs. I can't remember how to specify username and password via nfs and it isn't giving me a dialogue asking.

I can get there using both IP and host name, which I've also specified in the hosts file on the mac.

Now I feel like we're getting somewhere! :D

---

### Post by Canyonero on 2010-07-26
Still nothing on Windows though.

---

### Post by Canyonero on 2010-07-27
After even further digging, it appears that activating Windows 7 Homegroups breaks or deactivates the old-school workgroup system. Deactivating Homegroups allowed me to go into Explorer and enter \\[IP Address] or \\[computer name] and find my drives.

It's not ideal, but it works well enough.

Just thought I'd post this for the archives in case anyone else has similar problems.

---

