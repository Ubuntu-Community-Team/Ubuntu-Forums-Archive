---
title: "Connecting to a network attached storage device"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by dowgoldratio7 on 2011-09-04
I'm a noob to linux networking and I'm trying to connect to a network attached storage device (NAS). This is that NAS (a Cirago NUS1000 -- <rant> I called their tech support and they wouldn't give me *ANY* indication of how to connect under linux -- the CSR said something about there being "too many kinds" to support them all -- OK then support ONE! Moreover, I think the NAS runs linux! </rant>):

[http://cirago.com/wordpress/products/networking/ciragolink/](http://cirago.com/wordpress/products/networking/ciragolink/)
[http://www.pcmag.com/article2/0,2817,2358685,00.asp](http://www.pcmag.com/article2/0,2817,2358685,00.asp)

I think I can theoretically connect to it via smbfs, but I'm not familiar enough with that to have explored and there were too many steps and warnings from more experienced people for me to head down this path:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

I suspect there's a simple way to connect, but I'm not having success with the simplest approach (just finding the network devices in nautilus and double-clicking), and I'm paralyzed by choice on the more involved approaches... Some links I've found are here:

[http://ubuntuforums.org/showthread.php?t=1726800&highlight=network+attached+storage](http://ubuntuforums.org/showthread.php?t=1726800&highlight=network+attached+storage)
[http://ubuntuforums.org/showthread.php?t=1795551&highlight=network+attached+storage](http://ubuntuforums.org/showthread.php?t=1795551&highlight=network+attached+storage)
[http://tkramar.blogspot.com/2009/06/mounting-samba-shares-from-firefox.html](http://tkramar.blogspot.com/2009/06/mounting-samba-shares-from-firefox.html)
[http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html)

Some of the things that scare me in what I've found are editing fstab by hand and putting passwords in plaintext, but if that's what I need to do to test temporarily, I'd love to do that to know I *CAN* connect to it, but I'd like to find a simpler test to start.

On my windows XP box, if I type in \\nus1000 in an explorer window, it sees it and connects fine after asking for username and password.

When I open "Computer" -> "Network", I see an icon with the "NUS1000" twice. When I click on one of them and try "Open with other application", I see the title of the window is: "Open smb-server-NUS1000 with:"

If I double-click, I get another linux filesystem browser that has a link: "Windows shares on NUS1000", but it's an empty folder. I suspect it's trying to authenticate me as the user I am (not giving me the username and password dialog boxes), but I don't know if that's really what's going on. I did add a user with my same username to the NAS, but no joy.

If someone could please help with some simplifying guidance, I'd appreciate it. Even better, if someone out there has this device and has successfully connected in ubuntu or some other linux flavor, I'd love to hear how. But I suspect my question is about as general as a simple way to connect to a windows share.

If there's some other thread that has some straightforward approach, I'd love to get a link, too.

---

### Post by dowgoldratio7 on 2011-09-04
To give some sense of my noobness and frustration, here's the outcome of trying to follow the directions at:

[http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html)

This is what I did:

LinuxMachine ~ # mkdir -p /mnt/ntserver
LinuxMachine ~ # cd /mnt/ntserver/
LinuxMachine ntserver # ls
LinuxMachine ntserver # cd ~

Here are my attempts at mounting (all appear to fail):

LinuxMachine ~ # mount -t cifs //nus1000 -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount error: could not resolve address for nus1000: No address associated with hostname
LinuxMachine ~ # mount -t cifs \\nus1000 -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount.cifs: bad UNC (\nus1000)
LinuxMachine ~ # mount -t cifs 192.168.1.15 -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount.cifs: bad UNC (192.168.1.15)
LinuxMachine ~ # mount -t cifs //192.168.1.15 -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
LinuxMachine ~ # mount -t cifs \\192.168.1.15 -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount.cifs: bad UNC (\192.168.1.15)
LinuxMachine ~ # mount -t cifs [http://192.168.1.15](http://192.168.1.15) -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount error: could not resolve address for http: No address associated with hostname
LinuxMachine ~ # mount -t cifs [ftp://192.168.1.15](ftp://192.168.1.15) -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount error: could not resolve address for ftp: No address associated with hostname
LinuxMachine ~ # mount -t cifs smb://192.168.1.15 -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
Mounting cifs URL not implemented yet. Attempt to mount smb://192.168.1.15

LinuxMachine ~ #  mount -t smbfs -o username=XXXXXXXX,password=XXXXXXXX //nus1000 /mnt/ntserver
mount error: could not resolve address for nus1000: No address associated with hostname
LinuxMachine ~ #  mount -t smbfs -o username=XXXXXXXX,password=XXXXXXXX \\nus1000 /mnt/ntserver
mount.cifs: bad UNC (\nus1000)
LinuxMachine ~ #  mount -t smbfs -o username=XXXXXXXX,password=XXXXXXXX 192.168.1.15 /mnt/ntserver
mount.cifs: bad UNC (192.168.1.15)
LinuxMachine ~ #  mount -t smbfs -o username=XXXXXXXX,password=XXXXXXXX //192.168.1.15 /mnt/ntserver
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
LinuxMachine ~ #  mount -t smbfs -o username=XXXXXXXX,password=XXXXXXXX \\192.168.1.15 /mnt/ntserver
mount.cifs: bad UNC (\192.168.1.15)
LinuxMachine ~ #  mount -t smbfs -o username=XXXXXXXX,password=XXXXXXXX [http://192.168.1.15](http://192.168.1.15) /mnt/ntserver
mount error: could not resolve address for http: No address associated with hostname
LinuxMachine ~ #  mount -t smbfs -o username=XXXXXXXX,password=XXXXXXXX [ftp://192.168.1.15](ftp://192.168.1.15) /mnt/ntserver
mount error: could not resolve address for ftp: No address associated with hostname
LinuxMachine ~ #  mount -t smbfs -o username=XXXXXXXX,password=XXXXXXXX smb://192.168.1.15 /mnt/ntserver
Mounting cifs URL not implemented yet. Attempt to mount smb://192.168.1.15

In firefox on the same machine, I go to [http://192.168.1.15](http://192.168.1.15) and it talks to it, so that machine knows that address is alive.

Also,

LinuxMachine ~ # ping 192.168.1.15
PING 192.168.1.15 (192.168.1.15) 56(84) bytes of data.
64 bytes from 192.168.1.15: icmp_req=1 ttl=64 time=2.02 ms
64 bytes from 192.168.1.15: icmp_req=2 ttl=64 time=1.94 ms
64 bytes from 192.168.1.15: icmp_req=3 ttl=64 time=5.98 ms
64 bytes from 192.168.1.15: icmp_req=4 ttl=64 time=1.70 ms
^C
--- 192.168.1.15 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 1.707/2.913/5.980/1.775 ms

I'm sure I'm doing something stupid, just can't see what I'm missing.

---

### Post by Morbius1 on 2011-09-04
The one that comes closest to being the correct syntax in this one:
> mount -t cifs //192.168.1.15 -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserverThe only problem with it is one doesn't mount an entire remote machine ( 192.168.1.15 ). One mount a specific shared resource on that machine:
```
mount -t cifs //192.168.1.15/share-name -o username ............
```ANd remember Ubuntu doesn't do this sort of thing by default you needed to install the following package first:
```
sudo apt-get install cifs-utils
```If you are running an older version of Ubuntu the package is this:
```
sudo apt-get install smbfs
```

---

### Post by dowgoldratio7 on 2011-09-04
Also, samba appears to be running:

LinuxMachine ~ # ps -ef | grep mbd
root       702     1  0 Sep03 ?        00:00:00 smbd -F
root       754   702  0 Sep03 ?        00:00:00 smbd -F
root      1826     1  0 Sep03 ?        00:00:03 nmbd -D

---

### Post by dowgoldratio7 on 2011-09-04
And it seems to know there are samba shares out there with the NUS1000 or 192.168.1.15 address:

LinuxMachine ~ # findsmb

*=DMB
+=LMB
IP ADDR NETBIOS NAME WORKGROUP/OS/VERSION
---------------------------------------------------------------------
192.168.1.14 LinuxMachine [WORKGROUP] [Unix] [Samba 3.5.8]
192.168.1.15 NUS1000 +[WORKGROUP] [Unix] [Samba 3.0.24]

LinuxMachine ~ # smbtree
Enter root's password:
WORKGROUP
\\LinuxMachine LinuxMachine server ...
\\NUS1000 Network USB Storage Link
\\NUS1000\IPC$ IPC Service (Network USB Storage Link)

So it knows there's a samba drive out there...

---

### Post by dowgoldratio7 on 2011-09-04
I also noticed from findsmb it was NUS1000 and not nus1000, so I tried some case-sensitive changes all with the same errors as above:

mount -t cifs "//NUS1000" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "\\NUS1000" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "//NUS1000/IPC$" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "\\NUS1000\IPC$" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "//nus1000/IPC$" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "\\nus1000\IPC$" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "192.168.1.15/IPC$" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "//192.168.1.15/IPC$" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "\\192.168.1.15\IPC$" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "http://192.168.1.15" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "ftp://192.168.1.15" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver
mount -t cifs "smb://192.168.1.15" -o username=XXXXXXXX,password=XXXXXXXX /mnt/ntserver

---

### Post by dowgoldratio7 on 2011-09-04
Morbius, thank you so much for telling me what's closest to correct. Much appreciated. This is my first day with CIFS.

> **Morbius1 said:**
> The one that comes closest to being the correct syntax in this one:
The only problem with it is one doesn't mount an entire remote machine ( 192.168.1.15 ). One mount a specific shared resource on that machine:
```
mount -t cifs //192.168.1.15/share-name -o username ............
```ANd remember Ubuntu doesn't do this sort of thing by default you needed to install the following package first:
```
sudo apt-get install cifs-utils
```If you are running an older version of Ubuntu the package is this:
```
sudo apt-get install smbfs
```

Thanks for the post. I think I have both smbfs and cifs-utils:

LinuxMachine ~ $ sudo apt-get install cifs-utils 
[sudo] password for XXX: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cifs-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 93 not upgraded.
LinuxMachine ~ $ sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 93 not upgraded.

And is the more specific share name IPC$ ? I tried to mount a more specific part of the NUS1000 and IP address in a post (using that IPC$ subdir), but I got similar errors as before. Should I do that differently? Is there a way I can know what I should call the part of the share I'm trying to mount? On windows, it looks like this in the explorer bar:

\\nus1000\XXXXXXXX

Thank you for trying to help.

---

### Post by Morbius1 on 2011-09-04
If this is the extent of smbtree for your NAS:
> \\NUS1000 Network USB Storage Link
\\NUS1000\IPC$ IPC Service (Network USB Storage Link)
You have no shared resources so there is nothing to mount. IPC$ isn't a mountable share.

---

### Post by dowgoldratio7 on 2011-09-04
> **Morbius1 said:**
> If this is the extent of smbtree for your NAS:
You have no shared resources so there is nothing to mount. IPC$ isn't a mountable share.

Morbius, thanks for the guidance on this--helps me focus on trying to create a mountable share I can see in smbtree.

In the meantime, as a workaround, since I can see it in WinXP, is there a way I could run explorer.exe in wine or some other emulator (VM?) and use that to connect to it the same way WinXP does? Or is that nonsense/undoable/harder?

---

### Post by Morbius1 on 2011-09-04
Don't use Wine so I can't help you there.

---

### Post by Morbius1 on 2011-09-04
This may be of no use to you whatsoever but .....

I downloaded the user manual for this device and unfortunately the screen shots ( in pdf ) are nearly unreadable but it seems there may be a couple of explanations for what's happening. 

It's possible that they set the samba share to not be browseable. Can't imagine why they would do that but it can be done. Or they are setting up all these devices per user in what samba calls a [homes] share which coincidentally would be visible to the Windows user if that user name matches a user on the NAS but would not be visible to a Linux Samba user because it's not built that way. You wouldn't see it from "Network" and you wouldn't see it from smbtree.

Now from what I can tell ( again I really can't make out the detail in the screenshots ) the shares look something like this:

/usb1-disk1, usb1-disk2, usb2-disk1, etc ...

If that's true and that's the way you see it from Windows then run the following command and see if it brings up nautilus to that share:
```
 nautilus smb://192.168.1.15/usb1-disk1
```

---

### Post by dowgoldratio7 on 2011-09-04
Morbius,

Thanks for the tip! I just got it to talk with your suggestion! Woot!

Cirago should really be able to tell this to users themselves. They'd sell a lot more to linux users. Their customer service gets an F. You get an A.

Details:

As background, I'd previously created a user (with username YYYYYYYY, password ZZZZZZZZ) and share (XXXXXXXX) from the web interface to the NAS (available at 192.168.1.15:1010). That created share was what I'd previously successfully connected to on WindowsXP.

After that, this was all I needed:

nautilus smb://192.168.1.15/XXXXXXXX

That gives you a nautilus window prompt that lets you enter the username, workgroup, and password inputs. It looks like this:

Password required for share XXXXXXXX on 192.168.1.15

Username: YYYYYYYY
Domain: WORKGROUP
Password: ZZZZZZZZ

 and below that a set of three checkboxes like this:

_ Forget password immediately

X Remember password until you logout

_ Remember forever

With the default option to remember password picked--and the username (YYYYYYYY) and password (ZZZZZZZZ) I created for the user from the web interface to the NAS (keeping domain WORKGROUP).

And voila! I'm talking to XXXXXXXX on my linux box! I can read and write to it.

The trick was like you said... Since the share isn't browsable, you just have to be Zen about it and type in the sharename you created (in my case, XXXXXXXX) as if you knew it'd be there.

Thanks again! Problem solved.

---

