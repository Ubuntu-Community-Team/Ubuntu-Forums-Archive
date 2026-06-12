---
title: "my dvds will just not play"
date: 2009-08-31
forum: Multimedia Software
---

### Post by lilmissdids on 2009-08-31
i just want to say, i've really tried everything i am capable of. i've been an ubuntu user since 2004 and until now, every problem i've ever had, someone else has had before me and i was able to google myself through. however, i've spent HOURS trying to make my dvd player work and it just doesn't.


no matter what i install, uninstall, write into the terminal or try.. i always get 

Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/scd0'. Check the log for details. 

info on cd drive

 *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-875S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready


maybe this is really, really simple, but I am really not that ubuntu-smart, so if someone could help me i would be so thankful.

cheers

---

### Post by mc4man on 2009-08-31
Other than not having libdvdcss2 installed

Sometimes it helps to go into home folder and delete the .dvdcss folder (hidden

Seeing that you have a matshita drive a couple of things specific to them (have the same drive on this laptop

A dvd region must be set on these drives or no playback of encrypted disks will be allowed (authentication will not occur

The region set **must match that of the disk being played**.

This is something that matshita laptop drives are known for, you cannot play disks when there is a region mismatch, period, no workaround

To check run regionset, if not installed go 
```
sudo apt-get install regionset
```

With a **disk in the drive** run regionset, if it shows 5 user controlled changes resets available and type: none, then set the region to where you are or what the majority of your dvd's are.
Don't change regions to play a title from another region, you only have 5 changes in total before drive gets locked

Ex. of my drive, already set to region 1
> doug@doug-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET  [COLOR="Red"]<-[/COLOR]
vendor resets available: 4
user controlled changes resets available: [COLOR="Red"]4[/COLOR]
drive plays discs from region(s): [COLOR="Red"]1[/COLOR], mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n


If not having a region set was the issue, delete the .dvdcss folder before reattempting playback

---

### Post by lilmissdids on 2009-09-01
THANK YOU SO SO SO SO SO MUCH.

I had done everything, I had even installed regionset before starting this thread, but I had not deleted the .dvdcss folder (and would have never done that).

You really just made my day.

THANK YOU!!!!

---

### Post by mc4man on 2009-09-01
Good to hear
Just make sure you only play dvd's from your region with that matshita drive and you'll be ok.

small note on .dvdcss

That is where the decryption keys are stored when you first playback a dvd.
It is a 'prefetch' for players to save time, so most players will look there first for a folder matching the volume label of the disk being played

If a matching folder is found then the player will use it for decryption even if the 'key' files inside are missing, corrupted or incomplete. 
In those cases the player will be unable to playback or playback fully

It's a perfectly safe folder to delete, will be re-created and populated as you playback disc's.

---

