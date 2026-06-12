---
title: "Scripting iPod Sync"
date: 2009-10-06
forum: Multimedia Software
---

### Post by mastermindg on 2009-10-06
I need a method of automatically syncing my iPod Touch thru a script. GtkPod doesn't seem to have many command-line options; either does Amarok.

I'm running a jailbroken iTouch 2.2.1. ipod-touch-mount/umount work fine passwordless. Does anybody know of a method of updating the 2.2.1 db via script?

To Clarify: I'm connecting by using sshfs thru the ipod-touch-mount/umount comands. This is how I am connecting and this is how I would like to remain connecting.

---

### Post by mastermindg on 2009-10-06
I've been trying to use gnupod scripts to accomplish my task....However, it looks like the mktunes script is searching the ipod via sysfs which would work if it was mounted via USB. I know that gtkpod uses a similar script and it seems to work fine. 

Does anybody know a way around this, a way to update the iTunesDB thru a script while mounted via sshfs?

---

### Post by mastermindg on 2009-10-06
Nevermind, figured it out!!

Create a file: ~/.gnupodrc and put the following line in it:

```

mktunes.fwguid = 000ba3100310abcf
mount = /media/ipod

```

where 000b.... is the fwguid for the ipod. I got mine from the sysinfo file placed by gtkpod. Adding the mount path in the config will simplify the process as well.

once this file is saved you can run mktunes and it will work!!

This is great news. Now I can automatically sync my ipod without any user-interaction. I'm amazed nobody's thought of this before.

---

### Post by mastermindg on 2009-10-07
The following is the finished product of an iPod Touch sync script that will automatically sync if any files are located in a directory. I've got another script that automates ripping streams but I figure there's more than enough of those out there.

To get this to work two packages need to be installed

ipod-convenience
gnupod

I've also configured gnupod as mentioned above:

```
#!/bin/sh

#Load configurable items
. /etc/default/ipod-convenience

BACKUP="/share/music/ripped/"
FILES="*.mp3"

#Ping ipod until there is a response
while true
do
if eval "ping -c 1 $IPADDRESS"; then
		#Look for new mp3 files and grab filenames
		for f in "$FILES"
		do
			#Check to see if there are any files present
                        if [ -e $f ]; then
                        #Begin Sync
			ipod-touch-mount			
			gnupod_addsong $f
			mv $f $BACKUP
			mktunes
			ipod-touch-umount
			fi
		done
		sleep 60
	else
		echo "iPod is not responding to pings at $IPADDRESS."
		sleep 60
fi
done
```

---

