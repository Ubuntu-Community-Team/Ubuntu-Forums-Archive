---
title: "lost recordings and backend not starting"
date: 2014-01-29
forum: Mythbuntu
---

### Post by randal2 on 2014-01-29
It has been a bad week for home IT with the phone line out with a root breaking the phone and ADSL, but I am back up.

The updates for the mythbuntu box were old so I updated everything.
Running ubuntu 12.04.

Got a bunch of errors for one of the http:/ URLs which was no longer there and depricated.
So I removed that specific path from the update manager list and did:
sudo apt-??? clean 
sudo apt-?? repository 
[COLOR=#222222]sudo apt-get update[/COLOR]
Then I installed mythbuntu-repos and set the version I wanted to 0.25
The backend would not start and I did a backend-setup, which looked like the answers from before...
and it said it needed an update, to which I said "yes".

same for the front end and it needed an update == "yes"

The front end would not see the backend, and removed the old mysql.txt files.
after checking that I could ping 127.0.0.1 , and checking that I could log into the mysql server, I checked and no backend was running.
I had to start the backend using ssh -X ...@myurl , which seemed to go OK.
(I rebooted a few times)
Then the front end was launched from the mythtv box and the TV worked again.

Q1> How do I get the back end to launch at startup?
Is it just going into something like .login or .cshrc file and saying (adding) mythbackend ?
I see nothing that looks halfway close other than some files in .lirc

----------

All the recording were 'lost' back in Dec-'13 just after the last update attempt.
I can see in "manage recordings" / "previously recorded" that the recording are known, but finding them is not easy on the mythtv box.
I recorded 2 shows today and they are NOT to be found on the GUI on the mythtv box.
when I launch the <IP>/mythweb from the mac, I can actually ASX watch it and download it... Just not on the mythtv directly.

Q2> How do I get the old recording located?
I stumbled around and see fresh files in 
/store/recordings
but how do I get them to be known by the system? so that they show up on the mythtv GUI?

---

### Post by blm-ubunet on 2014-02-01
In *buntu based systems..
mythbackend is launch by upstart job /etc/init/mythtv-backend.conf

There is a very good example on the mythtv wiki..
0.25 is very old so beware the cmd line options (logging) have changed..
You can get 0.27+fixes on 12.04LTS..

Mythbuntu uses some screwball auto-respawning frontend launching script, tho I think the backend is safe..

Old recording (entries still in DB):
MythTV uses storage groups..just add all/any number of folders in storage groups setup in "mythtv-setup".
Maybe you have just left one folder off the list..

New recordings missing:
Have you changed recordings screen view filter to "deleted" group?
<m> change group filter back to "default"

If you have other HDD mounted (for storage) be careful to never use the root of any disk as a storage group target.
For example if HDD2 mounted in /mnt/extra then create a folder on HDD2 root (recordings) & then use /mnt/extra/recordings/ as the storage group..
Doing this means an unmounted disk (failure) causes the storage folder to not exist (good) rather than write into filesystem in / (root).
Some storage groups can be read-only etc..

---

