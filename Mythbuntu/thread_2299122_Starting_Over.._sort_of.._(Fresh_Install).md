---
title: "Starting Over.. sort of.. (Fresh Install)"
date: 2015-10-15
forum: Mythbuntu
---

### Post by elliott6 on 2015-10-15
Hi all,

Looking at a fresh start (install). Currently on 12.04LTS with 0.25. This is a system that started with 8.10 (maybe), and upgraded over the years.

- I hosed up my storage when I set my fstab wrong (mounted my xfs as ext4.. stupid me). I was almost there too with my overall system refresh, and silly me. Unable to get my main media array back (tried xfsrepair, as well as using testdisk and photorec without success), I have most of the important stuff backed up (minus about 800 pictures - wifey will not be happy; hope I can find them somewhere!) since I had been moving things around to make room for a new array. So the pictures, and probably half or more of the recordings are gone, along with some downloads and other documents and items. My thought is this:

Fresh install of 14.04.3 with 0.27. I have 40GB SSD for system install, and then media (videos/movies) on RAID10 (6TB), recordings on RAID5 (4.5TB), pictures and music each on their own 1TB drives. Using FiOS with HDHomeRun Prime (cable card) and HDHomeRun (regular), but planning on dropping FiOS for OTA shortly. Previously had all media on one RAID5, but "updated" my PERC 5i to H700 and now running RAID10. This is my main "server" in the house that I run 2 frontends off, as well as pull media for two laptops and one desktop, but would also like to eventually use our tablets and mobiles more efficient, and perhaps VPN into later on once everything is stored properly.

My concern is losing Megaraid Storage Manager (manage my PERC5i, now H700) that was a bear to install on 12.04. To this day, I am not sure what series of commands/installs/configs got it to work properly. But, I figure I will try it out on the fresh system, and worst case scenario, go back to my old config/backup.

Also, should I bother importing my database? Or would it be better to start anew?! As mentioned, I have some of the recordings (not sure I care about them), but don't know what is good/bad due to the naming convention. Additionally, I did have a lot of blank recordings where the file was lost, or didn't record/transcode because I was out of space.

I don't mind the setup, as I can make it right (eventually). But thoughts? Would you start fresh, or save what you could? Not sure if config files (like fstab, samba, etc) would benefit from a "clean" install.

Thanks for reading!

elliott

---

### Post by elliott6 on 2015-10-19
Fresh install complete. To import backed up database or not, that is the question..

I've been updating a bunch of my settings (update static IP, fstab, samba, etc.), adding programs, etc. 

Good:
- went smooth for the most part
- found install instructions for Megaraid Storage Manager 14 (used 15), and after converting with alien, seemed to be easier than the last time

Bad:
- LiveTV not working; can write to livetv directory and schedule recording and watch said recording fine, so more troubleshooting to come
- may be related to livetv not working, but initially in exiting backend setup, got an error about a videos directory and test file error (I switch "media" storage to /media/... from /user/mythtv/... or whatever it is); changed those permissions and cleared that error. However, I then received an invalid starting channel for my tuner(s) when exiting that I could not clear. Guess my next step is to remove the tuners and readd; tried reassigning sources.
- Megaraid installed fine, can launch and see program, proper storage address and login, but can't actually login (using root or mythuser); not sure if it is related to too weak a password, or some settings. More to come I guess..

Still to do:
- Do I import my old database?! I have some of the recordings I can copy back, but as mentioned, not all. I guess I can try, and if it works as I want, great, otherwise redo.
- Move media to appropriate place (folder)
- Last ditch attempt at recovering data? This is the main array for videos and movies (not recordings), so I haven't moved files in hopes I can figure something out.
- More tweaks
- Setting up the rest of the house - 2 frontends, possible VPN, access from outside the home
- Binge record FiOS (mainly for the kids' shows), then dump FiOS for OTA

Thanks for reading!

elliott

---

