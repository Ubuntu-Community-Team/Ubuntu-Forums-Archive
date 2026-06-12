---
title: "Is there an easier backup solution for me? Or do I have a good concept of it?"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-04-12
I'm just going to type what I have going on in my system and you folks can just critique it best you can to give me pointers or advice as to anything I should change.

This is how I have my system set up. Four SATA drives. 

A - 500gb - Vista/Ubuntu dual boot. (My Stuff)
B - 500gb - Backup of drive A. (My Stuff)

C - 250gb - Network Storage (Samba).
D - 250gb - Network Storage Backup.

I have an rsync script which copies A to B, and C to D. So that way I have 2 copies of my stuff and 2 copies of network storage.

There are 3 other XP computers on the network, to which I have free XP software to automatically synchronize their data in their My Documents folder to get pushed to my computer in their shares accordingly.

Within the smb.conf, which I actually used a gui to manage most of my samba stuff (system-config-samba, it's in the repos). It at least helped me with most of the basic stuff with users and setting up shares. I still edited the smb.conf manually to enable 775 group and directory masks, which was easy in itself since the directions were listed there but just commented out. 

After I set up the shares and users, I edited the smb.conf to enable 775 masks as I mentioned above. I also added "force group = sambashare" to each entry of user shares. That way, when user "Tyler" auto-synchronizes, it comes through with the ownership being tyler:sambashare instead of tyler:tyler. That way if I need to I can manage his files on my computer. Plus, coupled with the masks I spoke about above, all of the data comes through with 775 octal permissions, therefore tyler (owner) is 7, group (sambashare, which I'm a part of) is 7, and everybody else simply has standard access - 5.

So within drive C, my network drive, I have the following directories.

Pam - Backup Share.
Curt - Backup Share.
Tyler - Backup Share.
Public - What I use if I want to dump a folder in here for the others to access. Like if my buddy comes over and wants a folder of pictures I have, I'll copy them to that directory and he can log in to my guest samba account I set up, then he can copy them down accordingly to his laptop.

Along with that, I noticed something. In order for a samba user to exist, that user must exist on the system. So, let's expand on that a little bit. If I log in as guest and create a file, it comes through as guest:sambashare with 775 permissions, due to the forcegroup = sambashare tag along with the 775 masks I set within the smb.conf. Okay, fine. So even though guest owns that file, I still have full reign over it since I am part of the sambashare group. BUT, for the instance where I ever want to retain ownership of that file, I set up a bin bash script to adjust the owner to jason:sambashare recursively to all samba shares (pam, tyler, curt, public). But the trick is, pam/tyler/curt are members of sambashare, so by doing this I essentially change nothing EXCEPT root ownership, even though the group has full blown reign over those files to begin with.

And just note, with the users being in 1 group and that 1 group having full reign over every person's files, that doesn't mean that tyler can get into curt's stuff and mess around with it. Each share is password protected accordingly, so even though the individual permissions are there to one user COULD alter another's documents, the actual paths are different and protected via password.

So basically, I used the Samba gui to get the base model set up, then edited the smb.conf to adjust the mask setting to what I wanted (775) and added a force group tag to each share. Then I set up the users on my system in Ubuntu, set up the users and permissions in Samba, and bam. Done. Tacked in an rsync script there and now I have two copies of network files. Coupled with the usage of a free windows program (Syncback Free Edition) and suddenly all users can auto-sync their stuff to my computer at any time, or on a scheduled basis - which I set it to 3:00 AM.

How's that for a backup system/file server? Is there a way I could have done this easier? Or was this pretty straightforward and the best route to take when taking into consideration I have Windows machines to deal with an Ubuntu backup/file server computer?

---

