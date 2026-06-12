---
title: "Samba ubuntu to windows!"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2009-09-03
Ok so i have a slight problem kinda.... so i set up samba to share from windows 7 to ubuntu 9.04. when i access the ubuntu side it works fast and flawless. But when i access windows share from linux side it works but its alot slower and it displays some directories that arent shared.... example.

my windows shares are
Music
Videos
Public

but ubuntu shows these and...
ADMIN$
C$
D$

why are these appearing.... im guessin that C$ and D& are hard drives but why are they showing up?

Thanks

---

### Post by df6269 on 2009-09-03
It should be permission problem, please check you have the same user account in windows 7 and Ubuntu first.

---

### Post by ductiletoaster on 2009-09-03
what do u mean same user account! Both are set up to ask for username and password. and i can access the folders both read and write on either side.

---

### Post by falconindy on 2009-09-03
Any share with a $ after it is typically hidden in Windows, but they do exist. They're used for administrative purposes. From your own Windows machine, you can run the command `\\localhost\c$` and it'll open up an Explorer window to your c drive.

There's nothing wrong with the setup as long as the other shares (Musics, Videos, etc) are appearing as well.

---

### Post by Suiname on 2009-09-03
ADMIN$
C$
D$

These shares are created by default on Windows boxes, however, they are usually not visible.  You can manage and see them in windows by right-clicking on my computer and selecting the "manage..." option.  Then click on "shared folders" and under that "shares"  You can edit options and stuff from in there.  I would advise against using windows in general though.  Networking in vista sucked so hard, hopefully it'll be improved in windows 7, but not guaranteed.

---

### Post by ductiletoaster on 2009-09-03
Yeah vista networking was horrible but windows 7 is a huge improvement (though not perfect) i would say windows 7 is to vista as windows xp was to windows ME. But anyway i would avoid windows all together but i need it for alot of the apps i use like Adobe Master collection and of course games that arent supported by wine. 

i will look into the windows side and see if my sharing settings are correct

---

### Post by ductiletoaster on 2009-09-03
Ok so i dont know why they are showing up because the used to not, before i reinstalled ubuntu. I know it will work fine but im kinda a "neat freak" so to speak and i dont want them there! any suggestions 

O also both PC have gigabit NIC and they are hooked to a linksys router WRT54G does any one know what speeds i should expect for file transfers. im sure the router is goin to be a bottle neck but i dunno.

---

### Post by falconindy on 2009-09-03
As per the suggestion on [this site]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/1017452.html"), make the follow registry additions/changes on the windows box:
> Hive: HKEY_LOCAL_MACHINE
Key: SYSTEM\CurrentControlSet\Services\LanManServer\Parameters
Name: AutoShareServer (for servers)
Name: AutoShareWks (for workstations)
Type: REG_DWORD
Value: 0
It should hide the administrative shares when you browse from the Ubuntu side.

---

### Post by ductiletoaster on 2009-09-03
I appreciate the suggestion but i would rather not mess with the reg. Besides as i said before it used to not be like this. like three days ago i had ubuntu 9.04 and windows with samba and had no problem. but i reinstalled ubuntu 9.04 and now i have this thing

---

### Post by ductiletoaster on 2009-09-03
Ok so i decided to check the reg and am i supposed to add those or are thes supposed to be there?

---

### Post by falconindy on 2009-09-04
You'll need to add them if they're not there. Mind my typo -- it should be 'Parameters' without a space. Messing with the LanManServer isn't usually a big deal and the likelihood of anything exploding is low provided you create the keys in the right place.

---

### Post by ductiletoaster on 2009-09-05
Thank you! So if i ever decided i wanted them visible agian then i could just delete the reg keys correct?

---

### Post by falconindy on 2009-09-05
> **ductiletoaster said:**
> Thank you! So if i ever decided i wanted them visible agian then i could just delete the reg keys correct?
Correct. Or change it to a 1 if you wanted to keep the keys.

---

### Post by falconindy on 2009-09-05
oops, dbl post.

---

### Post by jobst on 2009-09-06
> **ductiletoaster said:**
> Ok so i have a slight problem kinda.... so i set up samba to share from windows 7 to ubuntu 9.04. when i access the ubuntu side it works fast and flawless. But when i access windows share from linux side it works but its alot slower and it displays some directories that arent shared.... example.

my windows shares are
Music
Videos
Public

but ubuntu shows these and...
ADMIN$
C$
D$

why are these appearing.... im guessin that C$ and D& are hard drives but why are they showing up?

Thanks

Those are standard admin shares, you can turn that of using group policy.
You can share them on your ubuntu box:

  mkdir /mnt/disk
  /bin/mount -t cifs //MACHINE/c\$ /mnt/disk -o lfs,username=MACHINE\administrator


jobst

---

### Post by ductiletoaster on 2009-09-08
Ok how do i turn them off in group policy.... Keep in mind im runnin windows 7! im sure it might be similar to windows Vista.

---

