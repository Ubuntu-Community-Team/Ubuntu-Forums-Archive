---
title: "Best way to do a WOL every 20 seconds?"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by Diskdoc on 2008-12-21
I have a Buffalo Linkstation Mini and want it to wake up from sleep with a Wake-on-LAN call (drive used in "auto" mode) as revealed on the Buffalo forums here:

[http://forums.buffalotech.com/buffalo/board/message?board.id=0101&message.id=2893#M2893](http://forums.buffalotech.com/buffalo/board/message?board.id=0101&message.id=2893#M2893)

Since I just barely manage making scripts let alone programs I dug around a little and found Etherwake (that uses wakeonlan, a Perl script) in the repositories. My problem is putting it in some kind of scripted loop that keeps sending WOL:s to the Linkstation keeping it awake.

---

### Post by Diskdoc on 2009-01-15
I haven't put in much time on fixing this yet but I put together a (ugly, probably) script which seems to keep the Linkstation Mini awake. Maybe it will help someone going down the same path.

 

 #!/bin/bash
while [  6 -lt 9 ]; do
        wakeonlan -i 192.168.1.255 aa:bb:cc:dd:ee:ff

        sleep 20
done

---

### Post by jonobr on 2009-01-15
stupid suggestion,
if its a script that runs, would you not just execute it when you want using a cron job?

Crontab is used to execute procedures at certain times/dates/periods etc and is good for executing tasks at certain times.
Heres a good link.

[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

---

### Post by Diskdoc on 2009-01-16
Hi Jonobr! Thanks for commenting on my musings! :) Yes, I'm thinking to do something of the sort. My Linkstation would mainly be used for doing scheduled backups using SBackup. I think SBackup puts stuff in crontab for its scheduling so I was thinking to add the WOL-scripting there.

However, I do store other files on the Linkstation and need to wake it up when I want to access them. For this I was thinking an on/off button in the Gnome-panel would be great. Seems a simple project to learn programming with and potentially useful to other people needing to keep something awake with WOL:ing. Knowing myself, I'll probably never get around to doing it :-p

---

### Post by jonobr on 2009-01-16
My "Keep away from the darkl art of scripting" brain was thinking of some other way of doing this.
However, Im pretty sure if you put this post in programming the guys over there would probably put together a fancy php script that will wakup and also stick on the bacon, brew a strong quad shot of Ubuntu and then do turn down service at night.

On what you are doing, Im curios what happens when you just execute the script. is that working itself?
DOes it give errors?

When you run the command on its own, 
wakeonlan -i 192.168.1.255 aa:bb:cc:dd:ee:ff
What does that do?
Does that work?

(Again, way out of my league here, but just curious how far you have gotten)

---

### Post by Diskdoc on 2009-01-19
Yes, the script works! It puts the WOL-sending in an infinite loop so that the WOL is sent every 20 seconds. Colin at Buffalo explained the Linkstation shuts itself down unless it gets a WOL every now and then to keep it awake. Sending one WOL would wake it up but then it will go to sleep again after a few minutes.

Wouldn't you need a webserver and browser for running a PHP script? Seems a "heavier" solution than shellscripting, plus I'm not sure you could integrate it with other programs (starting before etc.)

---

### Post by jonobr on 2009-01-19
Yep,
I was only being a smart a@#

I get the idea of 6 lt 9 now.....

Thanks

---

### Post by Diskdoc on 2009-02-03
I've fooled around with making a Cron-script for me. The script does the following:

1) Wake up the Linkstation
2) Mount my network drive (defined in /etc/fstab)
3) Start SBackup as a separate thread
4) Keep WOL:ing the Linkstation (indefinately, could be made to check for running sbackupd I suppose)

It seems to work but I'll chuck it into /etc/cron.daily and see how it goes..

[I]#!/bin/bash
#
# Sbackup Service file used by anacron

i=0
if [ -x /usr/sbin/sbackupd ]
then
while [ $i -lt 5 ]; do
        wakeonlan -i 192.168.1.255 00:1d:73:4c:22:03
        sleep 20
        let "i += 1" 
done
umount /media/Backup
mount /media/Backup
/usr/sbin/sbackupd &
while [ 6 -lt 9 ]; do
        wakeonlan -i 192.168.1.255 00:1d:73:4c:22:03
        sleep 20
done
fi
[/I]

---

### Post by Diskdoc on 2009-02-12
Worked on the script some more. If anyone uses it and improves it, I'd be happy to see your changes so I can incorporate them :)

[SIZE="1"][I]#!/bin/bash
#
# Buffalo Linkstation Mini+Sbackup Service file used by anacron
# Version 0.1 by Olof Englund, 02.2009 

interface=ra0
mountpoint=/media/Backup
ipshouldbe=192.168.1.2
ethernet=aa:bb:cc:dd:ee:ff
subnet=192.168.1.255
ip=`ifconfig $interface | gawk '/inet addr/{sub(".*:", "", $2);print $2}'`

echo "IP address is $ip"

if [ "$ip" != "$ipshouldbe" ]; then 
	echo "IP address for interface $interface is not $ipshouldbe. Exiting."
	exit
fi

i=0
if [ -x /usr/sbin/sbackupd ]; then
	while [ $i -lt 5 ]; do
		wakeonlan -i $subnet $ethernet
        	sleep 20
		let "i += 1" 
	done

	check=`cat /etc/mtab | grep -c $mountpoint`

	if [ "$check" = "0" ]; then 
		echo "check = $check. $mountpoint not mounted. Mounting."
		mount $mountpoint
	fi

	/usr/sbin/sbackupd &

	sbcheck=2
	while [ $sbcheck = 2 ]; do
		wakeonlan -i $subnet $ethernet
        	sleep 20
		sbcheck=`ps a | grep -c sbackupd`
		echo "Sbcheck is $sbcheck"
	done
	echo "SBackup complete. Unmounting $mountpoint"
	umount $mountpoint
fi[/I][/SIZE]

---

### Post by wcpeabody on 2009-08-26
Hmm, I am trying to do the same thing for the linkstation pro duo.

When I try to run the simple version of your script, I get -
[I]
wakeonlan: command not found.

[/I]Any ideas?
Thanks,
Bill

---

### Post by jonobr on 2009-08-26
Some threads just refuse to die :P

Welcome to the forums,

Sounds as if you dont have it installed

if you type 

which wakeonlan

in a terminal screen, 
it will probably show you dont have it installed,

You can try installing from synaptic.

I would also recommend you open a new thread if you have futher issues

Good luck and welcome to the forums

---

### Post by wcpeabody on 2009-08-26
Thanks for the quick reply.  That pointed me in the right direction.

Thanks again,
Bill

---

### Post by dmizer on 2009-08-26
It has been a while since this problem was discovered. I strongly suggest checking for a firmware update. running a WOL script every 20 seconds is less than ideal to say the least.

---

### Post by jmauld on 2009-09-17
Buffalo hasn't released anything to fix this.

To the OP, can you post the line from your fstab file?  I've got your original short script working (Thank you!), and want to make the script mount the drive so that it can be used as a standard network drive, and print server.

Is there anyway to make this script run when I try to access either the filesystem or the print server?

---

### Post by oscar69 on 2009-09-30
I made this 2 script on my Ubuntu.

The first one (Startup_Nas.sh) is to start up the NAS, the second one is to keep it running while the user have the share connected. When the user dismount the share, the script does not send WOL anymore, and after a while, the NAS shutdown.

I'd like to link the first script to the Place-Bookmark link, but I don't know how....
 
So, the user must call the first script, wait the NAS is up&running, before trying to access the share.

The second script can be started at user logon, and must be executed with users's permissions and settings: seems that nobody else can access the $HOME/.gvfs to see if the share is alive.

In test, I started it as 

nohup su - user_name -c /usr/local/sbin/KeepUp_NAS.sh  > /dev/null &

one for every user_name.

Both scripts send 3 WOL at a time, just because the "original" windows services from Buffalo do that :confused:

Any suggestion is appreciated! :)

Oscar

 
Startup_Nas.sh
#!/bin/bash

  for (( i=0; i<3; i++ )) ;
   do
      /usr/bin/wakeonlan -i ip_address  mac_address
   done

exit

 

----------

KeepUp_NAS.sh
#!/bin/bash

while (/bin/true) ;
 do
   if [[ -d "/home/$LOGNAME/.gvfs/NAME_OF_SHARE" ]] ; then

     for (( i=0; i<3; i++ )) ;
       do
         /usr/bin/wakeonlan -i ip_address  mac_address
       done

   else
       echo "Nothing to do!";
   fi

  sleep 30

done
exit

---

### Post by mister_p_1998 on 2009-09-30
Could I use this to turn on my Freenas server?

Steve

---

### Post by oscar69 on 2009-09-30
Essentially it send a wake-on-lan packet. 

I don't know the freenas, but if it can be started up that way, the scritps can be used...

---

### Post by oscar69 on 2009-10-01
A Self Reply: I read something about Freenas. It is software, and WOL is more hardware related. If your NIC is Wake-On-Lan capable, you can restart the freenas box with these scripts.
If your NIC is embedded in motherboard, look in Bios settings, or mobo manual.

---

### Post by oscar69 on 2010-02-18
I opened a [new thread]("http://ubuntuforums.org/showthread.php?t=1410353") on this.

Any comment is appreciated!

Giulio

---

### Post by MetapostAddict on 2010-06-10
> **wcpeabody said:**
> Hmm, I am trying to do the same thing for the linkstation pro duo.

When I try to run the simple version of your script, I get -
[I]
wakeonlan: command not found.

[/I]Any ideas?
Thanks,
Bill

Not sure if you're still interested, but I was having the same problem until I installed wakeonlan.

Now it seems to be working great.

---

