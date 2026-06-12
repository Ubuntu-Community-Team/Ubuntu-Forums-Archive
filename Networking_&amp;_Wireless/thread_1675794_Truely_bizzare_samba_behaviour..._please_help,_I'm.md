---
title: "Truely bizzare samba behaviour... please help, I'm losing hair..."
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by ProZac83 on 2011-01-26
I dont remember samba being this much trouble last time i played with it....

The situation is this: Ive got a small home network going, 2 laptops, a ps3, 2 WDTV Live media players, and a file server / dlna server/ torrent downloader / general dogs body ubuntu machine

Ive followed some guides on setting up samba so i can access files on the ubuntu machine from the laptops.

I installed samba:

sudo apt-get install samba-common
sudo apt-get install system-config-samba

That all went swimmingly.

Following the guide once more I loaded up the samba server configuration, and created some samba shares, specifically directories on HDD's attached to my ubuntu machine, for example:

/media/TV \ SERIES/tv

which is where the collection of downloaded TV series is... Also shared a directory of useful windows programs its nice to have at hand, and another directory of movies. All these shares are checked as writeable, visible, and to allow access from everybody.

Consulting the guide once more, i set the shares up identically in the nautilus sharing options screen. Checked "Share this folder', and to allow creation and deletion of files, and guest access.

Bob's your mothers brother, right? Hell no. Windows can see my server computer, and can even see the share names, but it cannot gain access. Right, I've seen this before, its down to permissions!

I added;

"force user = USERNAME"
"force group = USERNAME"

into smb.conf, ofcourse with USERNAME changed to my ubuntu machines' primary username.

This let me access the shares from the windows machine. HOORAY i thought, EUREKA! Problem solved, everything is hunky dorey...

Alas.

After mucking around out in the garage for a bit, came back inside to the laptop, and went to access the ubuntu machine... Hello, once again I'm refused access. Now, at the moment the ubuntu machine is right next to my laptop, so i played with  few things... unshared the folder in nautilus, and reshared. No dice... Changed some permissions manually, no dice... I browsed through the folder on the ubuntu machine, then tried one last time to access it from the windows machine, and what do you know it? Bingo, I'm in.

This sort of weird behaviour has continued for a couple of days now... I can;t work out any patttern. While writing this out I've tried accessing the ubuntu shares from my windows PC various times.

Initially i could access the TV folder, and the PROGRAMS folder, but not the MOVIES.

Then, probably 3-4 minutes later, without touching the ubuntu machine at all (I'm busy typig this post...) I give it another try. Now i can access the PROGRAMS folder, the MOVIES folder, but not the TV...

Just now i tried once more... Again, i can access the PROGRAMS, the TV, but now not the MOVIES again... grrrr! I went into the movies folder, selected everything, went to the permissions tab and CHANGED NOTHING... Then tried accessing the share again from the windows machine, and now I can get in.

After a fresh reboot of both machines I can't access any shares for the first couple of minutes. Then, sometimes i can get one, sometimes, two, and if I'm very lucky, all three.

seriously, WTF? Someone please tell me I'm doing something outrageously stupid and wrong... That way we can all have a good laugh at my expense, and get this damn thing sorted!

For shits and giggles I rebooted the ubuntu machine again... Now, after a few minutes i can access all three shared folders (lucky!), but according to nautilus, the movies folder isnt even shared anymore... Enabling the sharing options, hah, you guessed it, now i can't access it anymore... Please help...

Cheers.

---

