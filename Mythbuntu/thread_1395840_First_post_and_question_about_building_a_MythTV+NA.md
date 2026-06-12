---
title: "First post and question about building a MythTV+NAS box"
date: 2010-02-01
forum: Mythbuntu
---

### Post by devinfriday on 2010-02-01
Hi,
i was searching for a solution that provides PVR/DVB-T and divx/mp3 organizer and i found MythTV :)
My main concern is: is it possible to build a backend/frontend on a single machine that supports also basic NAS functionality (takes a folder and share it with Samba on the whole local network)????
I have an old Celeron/P4 1.8Ghz on a SiS 651 mobo + Maxtor PATA 200 for OS + Asus My Hybrid 7173. Need to buy 2 SATA disks and 2Gb of ram.
Do you think it can bear the load?
TIA.

---

### Post by jayg1169 on 2010-02-01
Looking at the system requirements for mythbuntu i cant see any problems with that PC.

If your only wanting to record and playback SD content.

My only doubt would be the TV card.

Are you sure your card isnt called an Asus My Cinema P7131?

If it is then that card IS supported in Linux [Link]("http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#ASUS")

---

### Post by devinfriday on 2010-02-02
Hi,
yes, the model seems to be "My Cinema.." here's a photo of the box.
[[IMG]http://img524.imageshack.us/img524/6580/130801157358202cw6.jpg[/IMG]](http://img524.imageshack.us/i/130801157358202cw6.jpg/)
The content will be only SD in recording (in my country there's a poor offering of HD contents), maybe some H264 files in playback.
Many thanks! The project "Frankestein" starts, i will update the thread with any news.

---

### Post by jayman8547 on 2010-02-02
I tend to stay away from celeron cpu's in any config because they lack L2 cache space that inhibits secondary processing power.  I.e they run great in a straight line but as soon as you try and turn they stumble....

As for the myth BE / FE / NAS setup it will easily work.  I have dedicated backend that also acts as a file / print server for my home network.  I also share my "multimedia" drive in Samba so I can see all the files when I boot into Windoze.

---

### Post by devinfriday on 2010-07-26
Good day,

i have finished my project and i wish 2 share some toughts about it:

1) mythtv is definitely not for newbie. The lacks of GUI-based tools for hw configuration is bad. My Tv card was recognized but there's no firmware loaded. In fact, /lib/firmware is not fully populated, probably due to licensing problems. Again, that's no good for first users;
2) Paradigm. MythTV has a way-of-life that's not so easy to understand: BackEnd, FrontEnd and all that comes with'em (configuration is splitted between the 2, and sometimes is hard 2 understand the meaning of some parameters);
3) Optional functions (Samba, SSH acccess, NFS) has no configuration tool enabled, that's brings 2 the first point: u need a Medium/high skill in unix administration 2 make them work/configure/customize.

At the end, i have spent the last WE 2 install, make the tv card work, make the wi-fi card connects WITHOUT a graphical tool/NetwokManager, change some configuration, fix the mysql server after an apt-get upgrade and still there is something that doesn't work properly:

- Videos are not recognized, i have changed the directory in which the FE is supposed 2 watch, put some files in it, no videos at all, sad :(
- Samba does not work, parameters seems ok but i cannot access the shares, shame on me it's supposed that i should be able to make it work (i'm an sysadmin), but what if i was a simple user???

When things works out-of-the-box you're in heaven, but when you loose 2 days for workin' out something that should be user-friendly and, most of all, for your entertainment, it's not worth, IMHO.

---

