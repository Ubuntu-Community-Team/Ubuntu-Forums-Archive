---
title: "lost my data, or have i?"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by puccaso on 2011-04-06
so i made a usb key from the new beta1,
and i did an UPGRADE CURRENT DISTRO option when the liveusb desktop came up...


now, i thought it was going to just upgrade my data and i that i wouldnt lose anything
but i've lost everything


but have i?


my home directory is a sepereate partition, and it shows about 30mb are being used in nautilus..
but, 

when i do a "df --si"

i get this..


/dev/sda5               47G    28G    17G  62% /home


and when i do a mount i get this 


/dev/sda5 on /home type btrfs (rw,subvol=@home)


what is that about, subvol?

it seems like my data is still there? but where..

any ideas?

---

### Post by Harry33 on 2011-04-06
Well if you only upgraded and not reinstalled formatting partitions, you do still have the same separate partition for your /home/ directory.
And you should also be able to automatically see all the files and data there with Nautilus.
However, the /home directory is automounted on boot, otherwise the whole boot and login procedure fails.
Check the file /ect/fstab for partitions that are automounted on boot.

---

### Post by puccaso on 2011-04-06
well &#305; f&#305;xed the problem
&#305; d&#305;dnt know th&#305;s was poss&#305;ble

&#305; have a part&#305;t&#305;on

/dev/sda5
and in that partition i have several folders

skillful and @home

i found out that the @home in the /dev/sda5 partition is being mounted as an actual partition itself (or something similar to that)


when booting into the newly installed system,
only the contents of @home show up as /home
but when i log into console, unmount /home
and mount /dev/sda5 elsewhere, i can see two different folders.


so technically,
i havent lost my data.
im very happy
and its a nice find.

is this something specific to btrfs? or could we do this before,
cos its the first time ive ever seen this, and ive been using 'nix for about 6 years.

---

### Post by puccaso on 2011-04-06
well &#305; f&#305;xed the problem
&#305; d&#305;dnt know th&#305;s was poss&#305;ble

&#305; have a part&#305;t&#305;on

/dev/sda5
and in that partition i have several folders

skillful and @home

i found out that the @home in the /dev/sda5 partition is being mounted  as an actual partition itself (or something similar to that)


when booting into the newly installed system,
only the contents of @home show up as /home
but when i log into console, unmount /home
and mount /dev/sda5 elsewhere, i can see two different folders.


so technically,
i havent lost my data.
im very happy
and its a nice find.

is this something specific to btrfs? or could we do this before,
cos its the first time ive ever seen this, and ive been using 'nix for about 6 years.

---

### Post by cariboo on 2011-04-06
I would call btrfs stable, but I don't think it was the problem. The upgrade option is new for Natty. There was this email on the ubuntu-devel:

> In 11.04 and later versions, the desktop CD installer (ubiquity)
presents an option to upgrade Ubuntu if it finds a single copy on the
system.  This functionality is not exactly equal in operation to
upgrade-manager, nor does it share much code with that application.

Such an upgrade will first make a backup of apt's state, including
repacked debs (using dpkg-repack) for any packages that it cannot find
a source for.  Following this, it will delete all non-user and
non-local files on the existing partitions.  This is roughly
everything but /usr/local, /var/local, /usr/src, and /home. It will
then install Ubuntu over top of the partially-cleared directory
structure and install the packages referenced in the apt state backup.

When triaging upgrade bugs, please make sure they're targeted to and
have logs for the correct package.  If the user upgrades via the
option in the desktop CD installer, change the package to ubiquity and
have the user run `sudo apport-collect $bug_number`.

Thanks,
Evan


---

