---
title: "Gnome-nettools can't ping"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by SonicSteve on 2011-01-15
Hello guys,

I've been all over the net on this one and found a lauchpad bug about it but no one seems to have a fix.

Using the gnome-nettools "administration> network tools" I can't ping, but it seems like all the other tools are fine. 

One article seemed to think that the ping command that the tool tries to launch is pointing to the wrong place. Though again no one seems to have a fix. 

Pinging from the command line is fine, networking is fine just in case anyone asks. 

I use the ping command frequently at work and I would really like to use the tool. 

Does anyone care to wade in on this?

---

### Post by dandnsmith on 2011-01-15
I wonder how many people have this problem.
Are you really running 10.04? - I am, and have no problem with the nettools ping.

---

### Post by SonicSteve on 2011-01-15
I guess I should change my avatar, I did change over to 10.10, interestingly though I had this problem with 10.04 also. It was one of the reasons I decided to change to 10.10. 

The install was a clean install though though I keep my home partition. 

I admit it's a strange bug. The live CD doesn't suffer from it. I'm starting to think it has something to do with a carried over setting from the home partition.

---

### Post by SonicSteve on 2011-01-15
Sorry for the double post, the site didn't move on from the reply box and I ended up submitting it twice.

---

### Post by dandnsmith on 2011-01-15
> **SonicSteve said:**
> I guess I should change my avatar, I did change over to 10.10, interestingly though I had this problem with 10.04 also. It was one of the reasons I decided to change to 10.10. 

The install was a clean install though though I keep my home partition. 

I admit it's a strange bug. The live CD doesn't suffer from it. I'm starting to think it has something to do with a carried over setting from the home partition.

That's an interesting bit of info. I wonder just what you could have saved to do that (could it be a path setting?).

I wonder how to find the ping you point to - might get a clue from stuff on how to customise the menues.

---

### Post by SonicSteve on 2011-01-15
I just tried my laptop, it was an accidental fresh install, accidentally wiped out my home partition. 

It has the same problem. All my systems suffer the same fate, 
1. Work PC
2. Home desktop
3. home laptop

None have ever shared a home partition. This likely isn't the reason. 

This thread seems to be correct that the path to the ping command that nettools calls seems to point to the wrong place.

[http://www.linuxquestions.org/questions/linux-software-2/gnome-nettools-doesnt-ping-i-figured-out-the-problem-how-do-i-fix-it-843085/](http://www.linuxquestions.org/questions/linux-software-2/gnome-nettools-doesnt-ping-i-figured-out-the-problem-how-do-i-fix-it-843085/)

The interesting thing is that if you paste the /bin/ping command into the terminal is that it calls the ping command, but the command doesn't really seem to ping.

---

### Post by SonicSteve on 2011-01-15
I just tried my laptop, it was an accidental fresh install, accidentally wiped out my home partition. 

It has the same problem. All my systems suffer the same fate, 
1. Work PC
2. Home desktop
3. home laptop

None have ever shared a home partition. This likely isn't the reason. 

This thread seems to be correct that the path to the ping command that nettools calls seems to point to the wrong place.

[http://www.linuxquestions.org/questions/linux-software-2/gnome-nettools-doesnt-ping-i-figured-out-the-problem-how-do-i-fix-it-843085/](http://www.linuxquestions.org/questions/linux-software-2/gnome-nettools-doesnt-ping-i-figured-out-the-problem-how-do-i-fix-it-843085/)

The interesting thing is that if you paste the /bin/ping command into the terminal is that it calls the ping command, but the command doesn't really seem to ping.

---

### Post by SonicSteve on 2011-01-15
Could someone remove this post and post #7. I'm having trouble posting today.

---

### Post by dandnsmith on 2011-01-15
At the very end of the thread is a hint that there may be a new version of nettools. Could be worth a try

---

### Post by SonicSteve on 2011-01-15
Yeah I saw that, here's the crapper though. The "new version" it points to is v2.30.xx the version in Ubuntu is 2.31.6 which is already a latter version. I don't know where the trouble lies but it's cross distro and seemingly not affecting many people, or we all just use the command line as the workaround hoping that some day they'll fix it. I'd be willing to be it's not a very difficult fix, but if not that many are affected it's probably a low priority. 

What I find most strange is that all 3 installs I have running are affected. Two have home partitions that have been around for quite some time. I believe the 3rd was wiped out but perhaps not entirely. What I mean is this; when I installed I chose not format the home partition, but after the install was done all my files were gone from the home partition on my laptop (must be a bug in the installer). If not all the home partition was wiped out perhaps some of the gnome settings were left behind.

---

### Post by SonicSteve on 2011-01-15
OK so here's something interesting. 

I just booted up 10.10 in a virtualbox vm and used network tools to ping 127.0.0.1 (localhost) and the same problem occured. The ping worked from the command line and not from the gui tool.

How can I be the only one having this problem. The live CD of 10.10 didn't work.

EDIT.

I just tried booting up a 10.04 live CD in VM. The ping tool in network tools worked properly.

Something happened in 10.10, I'll check my CD's for defects etc. but I didn't install my computers using the same media or even the same download.

---

### Post by Twyztyd on 2011-01-15
I have the same problem on 10.10 clean install.

Kind of aggravating but at least theres terminal

---

### Post by SonicSteve on 2011-01-15
> **Twyztyd said:**
> I have the same problem on 10.10 clean install.

Kind of aggravating but at least theres terminal

Hey I welcome a brother in arms gladly. I just wish I had some kind of lead to investigate. I'm stumped at the moment.

Take a look at this,

[https://bugs.launchpad.net/ubuntu/+source/gnome-nettool](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool)

It seems that many are having problems with the nettool. The bugs are exactly being fixed quickly though.

Edit,
I just found this;
[http://linux.softpedia.com/progDownload/gnome-nettool-Download-12192.html](http://linux.softpedia.com/progDownload/gnome-nettool-Download-12192.html)
I'm not sure I trust the source just yet, but it looks interesting.

---

### Post by dandnsmith on 2011-01-16
```
"gnome-nettool" versions published in Ubuntu
Maverick (2.31.6-0ubuntu1): main/gnome
Lucid (2.30.0-0ubuntu1): main/gnome
Karmic (2.28.0-0ubuntu1): main/gnome 
```

From the page referred to in the last post (1st link)

One of the posts where a version was found to fix the ping problem was (IIRC) 2.30.0-3: wonder if it works in 11.04?

---

### Post by SonicSteve on 2011-01-16
> **dandnsmith said:**
> ```
"gnome-nettool" versions published in Ubuntu
Maverick (2.31.6-0ubuntu1): main/gnome
Lucid (2.30.0-0ubuntu1): main/gnome
Karmic (2.28.0-0ubuntu1): main/gnome 
```From the page referred to in the last post (1st link)

One of the posts where a version was found to fix the ping problem was (IIRC) 2.30.0-3: wonder if it works in 11.04?

You know I find it odd that a smaller project like gnome-nettools would release it's code with a bug as glaring as this one.  I wonder more if it perhaps not enough attention is given by the various distros when they build the distro, thusly overlooking a smaller usually reliable component. I may be wrong but it I have trouble believing that the issue isn't something rather small and easy to fix.


EDIT,

I should preface this next comment by saying that I'm not a programmer. However...

I looked at the bug [https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/555546](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/555546)

It looks like ping command is running, but the output from the command isn't being processed into the nettool gui properly.

---

### Post by SonicSteve on 2011-01-16
OK so here's the problem,

[https://bugzilla.gnome.org/show_bug.cgi?id=634749](https://bugzilla.gnome.org/show_bug.cgi?id=634749)

nettools handles icmp_seq and icmp_req differently. It's looking for one and ignores the other. It's likely the the icmp ping command in Ubuntu was changed from seq to req a while back, that would break the nettools ping function. I wonder if there is an easy way to switch from one type of ping back to the icmp_seq without breaking other things.


EDIT;
Just to confirm,
I loaded up a freshly installed VM of both 10.04 and 10.10
10.04 pinged properly, using icmp_sec
10.10 did not using icmp_req

---

### Post by trundlenut on 2011-03-24
I have just come across this problem on a fresh install of 10.10, it didn't happen with 10.04, slightly annoying.

---

