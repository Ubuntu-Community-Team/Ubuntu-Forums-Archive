---
title: "Permanently Mounting cifs Shares with Wireless"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Colie on 2009-01-01
After searching Google and these forums for information regarding permanently mounting samba network shares, I came across information concerning adding the shares to /etc/fstab.  This works fine for a wired network, but runs into problems on a laptop (or wireless in general, I would imagine).  The best I can figure is that when Ubuntu shuts down, the rcX.d scripts turn off the wireless prior to unmounting those drives.  When trying to shut down, the standard ubuntu flash shows, but then I got a CIFS error...something about "no response from cmd 50".  The shutdown/reboot would hang at that point.

After some searching, I came across /etc/gdm/PostSession/Default.  This file is called every time a user logs out of a gnome session.  I created a shell script in my home directory to unmount the drives, set the suid bit, chown'd it to root, and made it executable.

The script (which I called .unmountdrives.sh) looks like this:
```
#!/bin/sh
sudo umount /media/computer1/Share1
sudo umount /media/computerx/Sharex
...
```

And the permission mods looks like so:
```
sudo chown root ./.unmountdrives.sh
sudo chmod +s ./.unmountdrives.sh
sudo chmod +x ./.unmountdrives.sh
```

I then added a line in /etc/gdm/PostSession/Default, right above the "exit 0" line that called that script.    Unfortunately, this was only a partial fix.  If I mounted the drives manually, then this fixed the cmd 50 errors.  If I left the drives mapped by /etc/fstab, then this fix DIDN'T work.  

I first tried to write a shell script to map the drives, giving it the same settings as the unmount script, and putting it in System : Preferences : Sessions.  The script looked like this:
```
#!/bin/sh

sudo mount -t cifs //yourfirstserver/yourshare /media/mountlocation -o credentials=/path/to/.smbcredentials
sudo mount -t cifs //yournextserver/yourshare /media/mountlocation2 -o credentials=/path/to/.smbcredentials
sudo mount -t cifs //yourotherserver/"your share with spaces" /media/mountlocation3 -o credentials=/path/to/.smbcredentials
...
```

This didn't work, though, because it ran before the wireless connection was established.

NOTE: For this script to work, all of the /media/mountlocations must exist--create them with *sudo mkdir*.  Additionally, you must have created a .smbcredentials file as per the smb documentation.

After some more searching, I found /etc/NetworkManager/dispatcher.d/.  This is a magic folder for Network Manager, similar to the rcx.d folders are for runlevels.  I created a script in here called 02mapdrives, because by default there was only 1 file in that directory: 01ipupdown, and these files run in the order they are numbered. I put the following code in it:

```
#!/bin/bash
if [ $1 == "eth1" ] && [ $2 == "up" ]; then
        /home/yourusernamehere/.mountdrives.sh
fi

if [ $1 == "eth1" ] && [ $2 == "down" ]; then
        /home/yourusernamehere/.unmountdrives.sh
fi
```

I then made that file executable like so:
```
sudo chmod +x 02mapdrives
```

Note that my laptop has a wired NIC as eth0, so eth1 is my wireless card.

This fixed the problems!  The first part maps the network drives when the wireless connection is established.  The second part unmounts them if your connection is terminated but you haven't logged out.  You still need to call the .unmountdrives.sh in /etc/gdm/PostSession/Default for when you log out.

So, to summarize:

1) Create a 2 shell scripts--1 to mount and 1 to unmount your drives--in you home directory, and set the ownership/permissions as indicated above.  Make sure you have a .smbcredentials file if you don't want to put your username/passwords in plaintext in the scripts.  see man mount.cifs for more information about that.

2) Create a file in /etc/NetworkManager/dispatcher.d as indicated above to call the mount and unmount scripts when the network is up/down respectively

3) Add a call to the unmountdrives script in /etc/gdm/PostSession/Default to avoid the CIFS cmd 50 errors.

You're done!

I haven't seen anything documenting this process yet, which is why I decided to post, but its definitely possible that there could be a problem with the methodology.  If anyone sees problems with it, make sure to let me know.

EDIT:  Well, I almost had it.  After using this setup for a while, I found a slight problem with it--it doesn't handle suspend/hibernate elegantly.  Apparently when you suspend, it doesn't unmap the drives before it turns off networking, thereby hanging the suspend if you have drives mapped.  To resolve this, we need to cause your unmount script to run when you suspend.  The directory for this is /etc/pm/sleep.d.  In that folder, create a file called **02UnmountCIFSDrives** by typing:
```
sudo gedit /etc/pm/sleep.d/02UnmountCIFSDrives
```
The contents of that file are:
```

#!/bin/sh
# Unmount the CIFS shares that are automatically mounted

. "${PM_FUNCTIONS}"

case "$1" in
        hibernate|suspend)
                /home/yourusernamehere/.unmountdrives.sh
                ;;
        *) exit $NA
                ;;
esac
```
Save that file, then change it's permissions like so:
```

sudo chmod 0755 /etc/pm/sleep.d/02UnmountCIFSDrives

```
That causes the unmount script to run when you suspend or hibernate your computer.  There's no need to cause your "mount" script to run on resume, because it will automatically be run when networking is re-established.

That about sums it up!

---

### Post by jrb114 on 2009-06-25
Hi, 

Thanks for this walkthrough, it's excellent. 

The only thing I'm having trouble with is the dispatches.d folder. I can't seem to get either command running to unmap or map the drives. 

My scripts both work fine on their own, and the drive *is* unmapped on suspend. 

Does anybody have any other ideas?

Many thanks,

J

---

### Post by dmizer on 2009-06-25
Yup, Ubuntu kills the internet connection before unmounting network shares. There's already an unmount script in /etc/init.d/umountnfs.sh

All you had to do was add it to the top of /etc/gdm/PostSession/Default like this:
```
#!/bin/sh
/etc/init.d/umountnfs.sh

PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS
  echo "$OUTPUT"
}

exit 0
```

More information in the 2nd link in my sig.

---

### Post by jrb114 on 2009-06-25
Thanks dmizer, that worked perfectly. I guess I assumed fstab only worked for mounting devices on boot.

J

---

### Post by arturusch on 2011-12-03
Great!
Doesnt work at all on Ubuntu 11.1 :(

I cant map netword drives at all. Allthough my maping should be mounted on OpenVpn connection.
So I changed the 02mapdrives to tun0 instead of eth1. Dont work either.
I cannot locate the /etc/gdm/PostSession folder either in Ubuntu 11.1

Can someone rewrite this for 11.1,  its very usefull :)
Thank you.

Regards
Artur

---

### Post by Colie on 2011-12-03
To be honest, I haven't had to use this technique for a couple of evolutions of Ubuntu now...  I HAVE had some trouble mounting network drives, but it always had to do with being in the appropriate workgroup for smb...

I'm deployed right now, and don't have access to any shared windows drives that I can take a look at right now...tag, Ubuntu community, you're in...

---

### Post by arturusch on 2011-12-04
I came across gigolo.
A little handy although miss the automount when vpn is up.

---

