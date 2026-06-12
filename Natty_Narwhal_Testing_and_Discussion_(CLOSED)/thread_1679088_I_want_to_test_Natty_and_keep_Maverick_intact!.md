---
title: "I want to test Natty and keep Maverick intact!"
date: 2011-01-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by [Snc] on 2011-01-31
yes yes ... i know, Natty is still Alpha, ... but if it can boot in my downsized VM in roughly 3s (I'm not kidding!), then I *want* to test drive it on a *real* machine

This is my situation:

I have two drives, Maverick and swap installed on the first (60GB)
and 80GB of unallocated space + a data partition on the second. (1TB)

I would like to know if it is okay to just normally install to the second drive (where the 80GB of free space is)

...and everything should work "out of the box" ????

Or should I be cautious about anything???? 
Anyone here with personal experience about such a situation?

---

### Post by drewsus on 2011-01-31
I don't know how Ubuntu will handle booting from a secondary drive, but it should work fine. 
Also, some notes on partitioning to save you trouble when you reinstall the OS:
Seperate your system partition for Ubuntu into 3 parts:
1) /
2) /home
3) swap

1 (/) should be at the front and be about 10GB. 
3 (swap) should be at the end and be 2x your RAM if you want to successfully suspend/hibernate
2 (/home) should be in the middle (the remaining space)

That way, when/if you reinstall Ubuntu, you should be able to maintain your home partition and just reinstall your system files on part 1. Then you will maintain your settings and documents that you once had in your home folder. 

Here is my partition table (note that I have a tri-boot with OS X, Windows 7 and Ubuntu - my Ubuntu partition is the extended partition at /dev/sda3)
[IMG]http://i.imgur.com/8GwCp.png[/IMG]

---

### Post by donniezazen on 2011-01-31
Use two different usernames and thy shall not have any problems. I deleted all the data folders in maverick added bookmarks of natty folders and made links for maverick home. It works just fine.

---

### Post by drewsus on 2011-01-31
> **soham_1207 said:**
> Use two different usernames and thy shall not have any problems. I deleted all the data folders in maverick added bookmarks of natty folders and made links for maverick home. It works just fine.

you can use Ubuntu Tweak to change the path to default folders as well:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

Then spark it up and go to Personal -> Default Folder Locations

---

### Post by [Snc] on 2011-01-31
Cool :) thank you for the tips ;)

Any additional opinions will be greatly appreciated!

I Want to make sure, before I start doing stuff, that will make my head hurt ;)

---

### Post by drewsus on 2011-01-31
If a head free of pain is what you seek, I don't think installing the next version of Ubuntu that just entered Alpha 2 is the route for you! 
I think you should wait until it is at least at RC. But, then again, if you just want to learn and don't *really* care about the headaches, go for it!

---

### Post by kansasnoob on 2011-01-31
What's the problem:

[ATTACH]182438[/ATTACH]

I multi-boot a lot and the only time I run into trouble is when I break it trying stupid things.

If I break one OS really bad i can just use another :p

---

### Post by [Snc] on 2011-02-01
> **kansasnoob said:**
> What's the problem:

[ATTACH]182438[/ATTACH]

I multi-boot a lot and the only time I run into trouble is when I break it trying stupid things.

If I break one OS really bad i can just use another :p

That's what i want :) the "test" Natty is going to be "test" only until RC, then i am moving 100% to Natty.

---

### Post by [Snc] on 2011-02-01
> **kansasnoob said:**
> What's the problem:

[ATTACH]182438[/ATTACH]

I multi-boot a lot and the only time I run into trouble is when I break it trying stupid things.

If I break one OS really bad i can just use another :p

Wow :) that picture is **awesome** !!!!!

It made me feel like a *minor* nerd :) I'm gonna try that!

---

### Post by donniezazen on 2011-02-01
> **drewsus said:**
> you can use Ubuntu Tweak to change the path to default folders as well:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

Then spark it up and go to Personal -> Default Folder Locations

How does it work? Chromium downloads file in maverick default folder same with Banshee which looks for files in maverick home music folder.

---

### Post by drewsus on 2011-02-01
You'll have to try it out, but I think it does it behind the scenes. Like... symbolic links or something.

---

