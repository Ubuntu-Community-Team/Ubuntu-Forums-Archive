---
title: "ubuntu laptop needs to map a windows network drive"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by rvchari on 2011-01-05
hi,
i ve been a thorough user of ubuntu and one reason for me using windows is that office uses a windows based software. i ve been lucky to install the same on my laptop and executing it using wine.
the hitch is that whatever i work on the laptop doesnt get updated in the server. is there a mapping needed or some extra configuration ?
the documents i post on my laptop is visible within the software but its not shown up on server database....

a help in this region will help me stop using windows !!!

---

### Post by fabricator4 on 2011-01-05
I'm going through the same thing, but since it's fairly simple to move the files to and from the network share manually I haven't really had much incentive to work out how to do it properly.

Basically, all windows shares are handled via Samba, which should already be installed on your system.  The tricky bit is to mount the samba network drive share into the file system.  I've never been able to figure out what it's called as I always get errors.  Perhaps I'm just doing wrong, but I don't seem to get it.

Once you know how to mount the Samba share the next step would be to put it correctly in the /etc/fstab file so it gets mounted automagically at boot time.

There's some information on the Ubuntu wiki on doing it, but it appears to be out of date, misleading, and rather hard to work through:

Link: [Mount Windows Shares Permanently]("http://wiki.ubuntu.com/MountWindowsSharesPermanently")


Chris.

---

### Post by rvchari on 2011-01-05
copying and sharing is perfect using samba. i am also able to connect to windows server and execute the software to run my office apps. the irony is when i save my data, its saved on my laptop and not on the server.
i cant copy the file from my machine to server coz it might affect the data base of other fellow staff who are working on the same software !!! hope u got my point.

---

### Post by dandnsmith on 2011-01-05
> **rvchari said:**
> hi,
i ve been a thorough user of ubuntu and one reason for me using windows is that office uses a windows based software. i ve been lucky to install the same on my laptop and executing it using wine.
the hitch is that whatever i work on the laptop doesnt get updated in the server. is there a mapping needed or some extra configuration ?
the documents i post on my laptop is visible within the software but its not shown up on server database....

a help in this region will help me stop using windows !!!

Are we talking about Msoft Office (and which version)?
Do you operate on 'documents' on the server, or pick up a local copy to use?
How does a Windows based user save any updates? - details may condition approach.

---

### Post by rvchari on 2011-01-05
the software is totally windows bsed and its using backend to store multiple data. its not ms office (i stopped using msoffice the day i started using openoffice in ubuntu).

i need to know if there is a way how we do it in windows by clicking on my computer icon and mapping a network drive. we get a drive letter assigned (say z or y or whatever we allot) now this file system heirarchy is not there in linux and when i execute the win based software executed thru wine, software loads perfectly, i can even access the data but whatever i add on, its saved by default in the .wine/software/data and not saved in the server. this is the problem. sounds simple but i just need the correct syntax ! to assign the path.

smb:// doesnt serve the purpose and c:\program files\etc doesnt seem to be recognised by wine !

---

### Post by dandnsmith on 2011-01-05
OK, finally got to where you're working from.
You need the equivalent of the *net use Z: \\server\sharename ...*

I've never tangled with Wine to try this kind of thing, so don't know if it will do that.

---

### Post by PatchesTheCaveman on 2011-01-05
"Drives" as shown to Windows programs run with *wine* are stored as directories or symlinks in *~/.wine/dosdevices/*.

So to map a drive to a Samba share, go to Applications > Accessories > Terminal, and type each of the following commands in the black box, pressing Enter each time:
```
mkdir ~/.wine/dosdevices/**[drive]**
sudo smbmount -o username=**[username]** //**[server]**/**[share]**/ ~/.wine/dosdevices/**[drive]**:
```

You will be prompted for your local password and the password for the provided username on the server.

As an example, to mount Z: to //fileserver/docs and login as bob:
```
mkdir ~/.wine/dosdevices/z:
sudo smbmount -o username=bob //fileserver/docs ~/.wine/dosdevices/z:
```

---

### Post by rvchari on 2011-01-06
in my .wine directory, it displays c: and z: in dosdevices. z: displays the root file system. now whenever i am in office i connect to my office server through ethernet. 

usually when we use windows, the mapped drive displays z:. in my particular case, shall i allot y: ? or the server address directly ?

---

### Post by PatchesTheCaveman on 2011-01-06
You can map it to whatever you want.  Y: is fine.

If you absolutely must use Z: you can rename the existing Z: drive to something else.

---

### Post by thefix0r on 2011-01-06
"copying and sharing is perfect using samba"

LOL,. mounting is easy, but sharing, bah, easy my rump, nothing easy about that

---

### Post by rvchari on 2011-01-06
i ve created and tested samba shares and tested from a window machine. i could get it done then... then after that instance i upgraded and removed all shares (assuming i ll do that when i needed) so i said it was easy for me !!! reading ur comment i think i ll have to try once more..

nyways talking of the main topic, i ll have to connect it from my office server later in the day and see how it performs. will comment on that after i do it

---

### Post by rvchari on 2011-01-07
i am unable to issue smbmount command. termal gives output as smbmount command not found !!! i tried apt-get install, still no smbmount command. is there something i have to download ?

---

### Post by rvchari on 2011-01-07
attention : patchesthe caveman,
i am at home now and was surfing for the smbmount options as even man smbmount did not give me any help. i came across this article

smbmount mounts a Linux SMB filesystem. It is usually invoked as mount.smbfs by the mount(8) command when using the "-t smbfs" option. This command only works in Linux, and the kernel must support the smbfs filesystem.

WARNING: smbmount is deprecated and not maintained any longer. mount.cifs (mount -t cifs) should be used instead of smbmount

from the link => [http://linux.die.net/man/8/smbmount](http://linux.die.net/man/8/smbmount)

it will be appreciable if you kindly throw some light on this and guide me. i ll be doing this exercise tomorrow !!!

---

### Post by PatchesTheCaveman on 2011-01-07
On Ubuntu *smbmount* is an alias for *mount.cifs* (meaning they are now the same command).  I use it because it's two characters shorter.

To use it, you need the *cifs-utils* package (which ought to be installed by default).  To install it, run:
```
sudo apt-get install cifs-utils
```

---

### Post by rvchari on 2011-01-07
thanks buddy, i had all the utils related when i quieried but no cifs-utils, just issued the sudo command and installed. will check it out in office once i connect to my office lan.

by the way, just another doubt, do i have to issue the smbmount command every time i connect to my lan and use this particular software ? and that it will umount on disconnecting from lan ?

nyways i ll check that out by disconnecting and reconnecting !!!

---

### Post by PatchesTheCaveman on 2011-01-07
You could configure it to mount on startup, but I'm assuming your not connected to the LAN every time you boot so that wouldn't work.  So, I'm attaching a couple of helper scripts so you can make icons on your desktop to just double-click to map them.

Extract the attachment to your home directory.  Then, edit both files and fill in the information about the drive you want mapped and the network share your connecting to in both the *mapdrive* and *unmapdrive* files.

Then, right click on your desktop and click *Create Launcher*.  Set the name to something like *Map Y: Drive* and the command to *gksudo ~/bin/mapdrive*.  Then create another launcher for unmapping and set the command to *~/bin/unmap*.

Now, you'll be able to double-click those icons to map and unmap those drive whenever you need to.

It should be okay for you to pull the plug, but if something's still writing to the shared drive, your files could get corrupted.  So, you'll probably want to unmount the drive before disconnecting from the LAN.  To do that, you can run this command:
```
sudo umount ~/.wine/dosdevices/y:
```
Replacing *y:* with the drive you've mounted.  I also included a helper script for this too.

---

### Post by rvchari on 2011-01-08
gee... that was really sweet of you to give the scripts.
i did it !!!

one hitch... 
the damn software i have to install throough wine which is executable. i have to edit the data path from c: to y: (here c: mentions local c: in dosdevices and the exact path is c: in server ! so after the mapping is done i have to replace drive letter c: with y:
the funny part is the software gives a reply as data not found !!! but when i browse thru y: using nautilus i find it !!!

any permissions still left ? i am also working on my side..

---

### Post by PatchesTheCaveman on 2011-01-08
Map your drive and open the WINE file manager by running:
```
winefile
```

Click on your Y: drive.  Does everything appear there alright?

---

### Post by rvchari on 2011-01-08
it appeared right, but will check again after i connect to lan in office.

i tried `/.wine/dosdevices/y: after mounting / mapping and i could check the files from nautilus.

same was the way for wine explorer. will check that again today.

i honestly feel that it must be the problem with the software.
that behaves funny...

will definitely update to you. never the less, i could map the drive with ease...

help was valuable buddy...

---

### Post by rvchari on 2011-01-09
i tried what you said by issuing winefile command from terminal. it shows z:/ as root and /home under z:/. so in this i could not locate y: as it was in .wine/dosdevices folder.

then i umounted y:, reconfigured fstab so y: was mounted on /mnt.
this way, y: was noticable from winefile. means everything is in place !!!

the irony is the data folder under the c:/ on server can be explored thru winefile as well as nautilus but when i call for the data thru the software that i installed to run thru wone, it says data not found !!! nyways that must b the software problem that refuses to work under linux environment !!!


finally i installed the same on my virtual machine and tried out by mapping the drive as we usually do in wiondows, everything is working fine !!! may be i need to run that only thru virtual box and not executable directly thru wine...

nevertheless, this exercise and your valuable support has enlightened me more on this wine executables....
can we mark this thread as SOLVED ? coz the main purpose of starting this thread is cleared...
thanks buddy...

---

