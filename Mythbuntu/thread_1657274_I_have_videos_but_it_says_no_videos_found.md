---
title: "I have videos but it says no videos found"
date: 2011-01-01
forum: Mythbuntu
---

### Post by bludshot on 2011-01-01
In mythbuntu by default it creates folders like /home/username/Videos, /home/username/Music.

So I want to store my videos in that Videos folder.

So then in MythTV I set my video folder to /home/myusername/Videos  instead of the default mythtv location.

But then when I go to actually watch the videos in mythtv it says there are none.  [note: There *are* actually several videos in that folder]

plz help

---

### Post by sami8519 on 2011-01-01
Hi,

Press menu from remote control or M from the keyboard and choose scan for changes. It should find your videos now.

Regards
Sam

---

### Post by williammanda on 2011-01-01
Check your storage group setting in myth backend. That where it will look for your videos.

---

### Post by frego on 2011-01-01
also, check and fix ownership and permissions.

sudo chmod 777 /home/username/Videos/* -R

---

### Post by bludshot on 2011-01-01
> **sami8519 said:**
> Press menu from remote control or M from the keyboard and choose scan for changes. It should find your videos now.

Pressing M just brings up a box that says "System Menu" and it has two options: About and Close. About shows a version number. There's no "scan for changes"


> **williammanda said:**
> Check your storage group setting in myth backend. That where it will look for your videos.

I checked the storage group setting in the myth backend and added my folder for videos. But still no videos show up in mythtv under Videos in the media library. (I confirmed there are 3 .avi video files in the folder though.)


> **frego said:**
> also, check and fix ownership and permissions.

sudo chmod 777 /home/username/Videos/* -R

Ok I did this but still it shows no videos :|


What else can I check or do?

thanks!

---

### Post by bludshot on 2011-01-01
Ah, pressing M and scan for changes DOES work, but you have to press it when you're on the videos page. (I was pressing it on the main menu and in the video storage settings pages...)

---

### Post by microtechno on 2011-01-02
Was going to suggest getting the menu in the video folder but beat me to it.
If you have got it working remember to mark solved :D

---

### Post by Michaelknox on 2011-01-04
I got exactly the same issue.... I have 2 other drives with movies and I have tried adding the paths to Mythtv but no success... any help is deeply appreciated...if I place a movie in the default path is fine .. I tried to link but no luck... I placed the paths in Mythtv video storage directory configuration but nope...please help...

---

### Post by SJI on 2011-01-07
If the video directory's contents change do you have to rescan in order to be able to view them?

Is there a way of having myth just show the list dynamically?

---

### Post by thatguruguy on 2011-01-07
> **SJI said:**
> If the video directory's contents change do you have to rescan in order to be able to view them?

Yes. Which may be why the scan function is labeled "Scan for changes."

---

### Post by SJI on 2011-01-07
Shame :(

I was looking for something that wouldn't need to scan everything.

---

### Post by newlinux on 2011-01-07
> **SJI said:**
> Shame :(

I was looking for something that wouldn't need to scan everything.

I think if you enable file browser mode you won't have to scan, but you won't have metadata for files that weren't scanned and saved with metadata.

---

### Post by SJI on 2011-01-10
Thanks for that.

---

### Post by thatguruguy on 2011-01-10
Or, just use thunar (or dolphin, or nautilus, or whichever file browser you use) to browse your files, and open them with vlc. Problem solved!

---

### Post by SJI on 2011-01-10
> **thatguruguy said:**
> Or, just use thunar (or dolphin, or nautilus, or whichever file browser you use) to browse your files, and open them with vlc. Problem solved!

Navigating nautilus with a TV remote isn't my idea of fun :(

---

### Post by thatguruguy on 2011-01-10
Are you adding dozens of videos a day (or more)?

I ask this because: 
A) it's pretty easy to run the scan with your remote and 

B) you only have to run the scan if you really NEED your info updated 
--1) you don't need to run the scan if you haven't added any videos (by downloading or ripping movies, etc.)
--2) you don't need to run the scan for things you've recorded in mythtv
--3) If you don't feel like updating the info, you don't have to. You're not going to break anything by waiting and doing it once a week.

C) Scanning is pretty quick.  At least, it is on my system, but I only have ~500 Gigs of video files. YMMV.

---

### Post by SJI on 2011-01-10
> **thatguruguy said:**
> Are you adding dozens of videos a day (or more)?


I have scripts on a server that grab TV etc as and when it becomes available, so some days there'll be 5 or 6 new files and other days none.


> **thatguruguy said:**
> I ask this because: 
A) it's pretty easy to run the scan with your remote and 


Indeed. But it's something i'd like to avoid.
The player that i'm trying to replace simply views the remote share and lists what's there. Hit play and i'm done. I'd like to get as close as I can to that functionality.

> **thatguruguy said:**
> 
B) you only have to run the scan if you really NEED your info updated 
--1) you don't need to run the scan if you haven't added any videos (by downloading or ripping movies, etc.)
--2) you don't need to run the scan for things you've recorded in mythtv
--3) If you don't feel like updating the info, you don't have to. You're not going to break anything by waiting and doing it once a week.

C) Scanning is pretty quick.  At least, it is on my system, but I only have ~500 Gigs of video files. YMMV.


Scanning took a few minutes to complete on my system here (755GB 2,230 files). Audio took even longer.

---

### Post by thatguruguy on 2011-01-10
Maybe [Jamu]("http://www.mythtv.org/wiki/Jamu") can help.

---

### Post by nickrout on 2011-01-11
> **SJI said:**
> 
The player that i'm trying to replace simply views the remote share and lists what's there. Hit play and i'm done. I'd like to get as close as I can to that functionality.

Then enable browse mode in mythvideo

---

