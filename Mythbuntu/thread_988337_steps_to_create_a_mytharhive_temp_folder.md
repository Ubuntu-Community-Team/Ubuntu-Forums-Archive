---
title: "steps to create a mytharhive temp folder"
date: 2008-11-20
forum: Mythbuntu
---

### Post by zf3636 on 2008-11-20
Hello i have a combined myth backend and frontend myth 8.04 0.21 instal and i want add a mytharchive temp folder so i can burn to dvd,can anyone tell me the steps needed to create this in the home directory or mythtv directory.

---

### Post by klc5555 on 2008-11-20
> **zf3636 said:**
> Hello i have a combined myth backend and frontend myth 8.04 0.21 instal and i want add a mytharchive temp folder so i can burn to dvd,can anyone tell me the steps needed to create this in the home directory or mythtv directory.

If you've got the space in the partition/disk your home directory is in, it's just easier. Mytharchive runs as a user job with your home user's credentials, so if it's in your home directory you get fewer bizarre mytharchive terminations that end up being tied to permissions/groups issues. Mytharchive has enough other bizarre problems without your needing to bother with these.

If you wish to physically create such a directory prior to setting up mytharchive, simply open a terminal as your ordinary user and type:  mkdir mytharchivetemp       (or whatever you want to call it)

You will now have a directory whose full path is /home/<your-user-name>/mytharchivetemp

Set this path and directory as your temp working directory in the mytharchive setup in the frontend, and you're good to go.

Or, if you prefer, you can just set the path and directory in the mytharchive setup as above without bothering to actually create the physical directory with mkdir. Mytharchive blows away the temporary directory and recreates it every time it runs; it doesn't really care whether the directory is physically already present or not.

This solution assumes that only one user account is using mytharchive and burning DVDs. If other users have logins on this machine and will burn DVDs on their logins, then you will need to make a temp working directory that everybody can write to. Usually somewhere in the /var directory. That would have to be done as the superuser: sudo mkdir /var/mytharchivetemp

and then to make the directory universally read/writeable:
 sudo chmod 777 /var/mytharchivetemp
And finally to make the directory owned by mythtv and part of the mythtv group:  sudo chown mythtv /var/mytharchivetemp
sudo chgrp mythtv /var/mytharchivetemp

And then set this directory as the temp working directory in the mytharchive frontend setup.

I personally prefer the simple home directory solution, so that's what I use myself. Nobody else uses mytharchive on my machines.

Cheers! :)

---

### Post by zf3636 on 2008-11-20
Great i will try this info thx, curently these are my setting in utilities/setup setup/ media settings/ archive settings /-Mytharchive Temp Directory- /var/lib/mytharchive/temp/ and Mytharchive Share Directory- /usr/share/mythtv/mytharchive so if swap the following info to Mytharchive Temp Directory-to-mytharchivetemp and Mytharchive Share Directory-to-/home/user name/mytharchive temp will this work thx.

---

### Post by klc5555 on 2008-11-21
> **zf3636 said:**
> Great i will try this info thx, curently these are my setting in utilities/setup setup/ media settings/ archive settings /-Mytharchive Temp Directory- /var/lib/mytharchive/temp/ and Mytharchive Share Directory- /usr/share/mythtv/mytharchive so if swap the following info to Mytharchive Temp Directory-to-mytharchivetemp and Mytharchive Share Directory-to-/home/user name/mytharchive temp will this work thx.

You shouldn't need to mess with the Share Directory --best leave it alone where it is. Moving it will likely break scripts, including mythburn.py that is the master script for mytharchive.

Just set up the temp working directory in your home space, and you  should be ready for a first trial run.

There are a number of glitchy problems that you may later run into while trying to use mytharchive, depending on the source of the recording(s) and the way you wish to have it/them encoded onto DVD. But there are solutions or fairly reasonable workarounds for most of the problems, so they can be addressed individually if you encounter them.

Cheers!:)

---

### Post by zf3636 on 2008-11-21
Hello thx i have created the mytharchive temp directory that was missing and know i have started to archive recording(s),with no suprise i have source recording issues which are mentioned in the above post thx.

---

