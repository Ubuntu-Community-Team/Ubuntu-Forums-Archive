---
title: "Rhythmbox freezes while indexing mp3 files"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by Farenji on 2007-01-30
For a week or two I've been having troubles with rhythmbox under edgy. When I start rhythmbox, it starts scanning for (new) mp3 files but it doesn't finish. The app uses 100% cpu and rhythmbox just hangs, it is not responsive. I waited long (hours) but the only way to stop it is is to kill it. The program is totally unusable now as I can't import my music without a total freeze.

Here's what I tried to solve it, without any success:
- deleting the .gnome2/rhythmbox folder;
- reinstalling rhythmbox from the repos, including a purge of all config files;

I have the feeling that it is one or more files in the mp3 folder that's causing the freeze. When I exclude some dirs in the mp3 folder (by using chmod) rhythmbox works ok. The strange thing is that it only freezes when I include a dir that hasn't been changed in months. RB used to index this dir without problems.

The mp3's are in a mp3 folder in my home folder which is on a local (S-ATA) drive. I did a fsck of the HDD but no problems are reported. It is quite big (about 75GB) but this hasn't been any problem before. Also there is enough space left on the drive.

I can't find out which file is giving the problem or even confirm that's really the case. There are tens of thousands of mp3's in the folder. I tried to find out more using "lsof -n | grep mp3" while indexing, and that only shows me that (as far as I can see) all files are indexed from A to Z and then rhythmbox hangs. No mp3 file is open by the rhythmbox process at that moment. Maybe rhythmbox gets in some sort of eternal loop but I don't know where or how to find out.

There are no error messages when I start rhythmbox from the terminal.

Anyone has an idea where to look next? I ran out of ideas... please help!

---

### Post by Farenji on 2007-01-31
Anyone? :(

---

### Post by Farenji on 2007-01-31
I just built rhythmbox from source to see if that makes a difference - it doesn't, same problem.

:confused:

---

### Post by Farenji on 2007-02-01
Looks like I'm the only one with this problem??

I noticed that the indexing and 100% cpu consumption does stop after I let it run for a long, long time (ie the whole day, not just a few hours). Then RB works OK. However, *every* time I restart RB the problem returns: the app freezes for a long long long time. This sucks!!! It's not the speed of my processor or my memory or my disk. It's some kind of bug in RB.

Problem is, it seems I'm the only one with this problem and as I don't know the cause, it's not easy to file a usable bug report. Hell I'm gonna try anyway as obviously here's no one who can help me.

Did I already say that this sucks?

---

### Post by tears.of.angels on 2007-02-13
hey Farenji - i've been having a similar problem lately but haven't looked into it until now; i don't know if it's the same problem as yours or if it's different.

RB for me will lock up when i open it and it's scanning my mp3's, however since i have fewer mp3's than you (i've got about 10gb's) it takes 5-10 mins to fix the problem. at that point i can use it, but when i try to search through my songs, it locks up, uses 100% again, and takes anoth 5 minutes to search.
keep in mind this is ~5 mins per letter i type!

let me know if you've figured anything out (anyone): it's getting to be frustrating

---

### Post by RomeReactor on 2007-02-13
Sorry. Double post.

---

### Post by RomeReactor on 2007-02-13
Hi. I used to have that problem when using Rhythmbox in Dapper; the only workaround i found was to manually drag and drop around 200-250 songs at a time and wait until it indexed them, then drop another batch in, and so on. At the time, my computer was a Duron 700 MHZ with 256 MB pc100 RAM and a Nvidia TNT Riva with 32 MB RAM. Since then i've upgraded my machine to a 1.6 GHZ Sempron with 1GB ddr2 RAM and a Nvidia Gforce 6200 and haven't had that problem. Now, i'm not saying it's necessary to upgrade your machine; just that now that i'm using Edgy, haven't had that problem: Could be Rhythmbox in Edgy, or my newer hardware...

---

### Post by Farenji on 2007-02-14
> **RomeReactor said:**
> Hi. I used to have that problem when using Rhythmbox in Dapper; the only workaround i found was to manually drag and drop around 200-250 songs at a time and wait until it indexed them, then drop another batch in, and so on. At the time, my computer was a Duron 700 MHZ with 256 MB pc100 RAM and a Nvidia TNT Riva with 32 MB RAM. Since then i've upgraded my machine to a 1.6 GHZ Sempron with 1GB ddr2 RAM and a Nvidia Gforce 6200 and haven't had that problem. Now, i'm not saying it's necessary to upgrade your machine; just that now that i'm using Edgy, haven't had that problem: Could be Rhythmbox in Edgy, or my newer hardware...

My pc is a 3800+ AMD64 with 1GB ram and I'm using Edgy as well (32bit) so I guess there must be another reason. Even when the indexing is complete, RB hangs each time I start it rendering it useless.
I haven't been able to find out anything new about the problem so I'm kinda stuck.

---

### Post by RomeReactor on 2007-02-14
Have you installed the Gstreamer Ugly plugins? If not, then make sure the Universe and Multiverse repositories are enabled: In Synaptic, go to "Settings-->Repositories" and on the first tab (Edgy 6.10) check all the cases; then press the "Reload" button. Then look for Rhythmbox in Synaptic, rightclick on the package, and select **Mark Recommended for installation**-->**gstreamer0.10-plugins-ugly**; you might also need the Multiverse variant of those plugins, so search for **gstreamer0.10-plugins-ugly-multiverse**.

---

### Post by mikelo on 2007-02-15
i'm just wondering ... i have the same problem... and i have an AMD-64bit but i have edgy 32-bit installed... could it be that if we had edgy-64bit the problem would be contained?

---

### Post by RomeReactor on 2007-02-15
I'm using Edgy 32-bit as well, so i don't think it's related to that. Did you install the plugins?

---

