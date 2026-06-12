---
title: "Unable to install libdvd-pkg. Broken packages."
date: 2021-06-09
forum: Multimedia Software
---

### Post by Tadaen_Sylvermane on 2021-06-09
```
$ sudo apt install libdvd-pkg
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libdvd-pkg : Depends: build-essential but it is not going to be installed
              Depends: debhelper (>= 9) but it is not going to be installed
              Depends: dh-autoreconf but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

```
$ apt policy libdvd-pkg
libdvd-pkg:
  Installed: (none)
  Candidate: 1.4.2-1-1
  Version table:
     1.4.2-1-1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages
```

This is my desktop that is used for Kodi via the offical Kodi ppa, the Makemkv ppa, and pci pass through where I run a Windows VM that I game on. I rip dvd's occasionally via the Makemkv and compress with Handbrake. I wanted to install the above package so I could run vlc on a dvd and be able to tell which title was which in a given dvd.

---

### Post by Bashing-om on 2021-06-09
Tadaen_Sylvermane; Hummm ...

Right now is a head scratcher for what is not going on.

Let's see what we can do to get some additional info.

```

sudo apt update
sudo apt upgrade
sudo apt -f install

```
all return clean ?

See then where we go from here.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Tadaen_Sylvermane on 2021-06-10
```
$ sudo apt update
Hit:1 http://ppa.launchpad.net/heyarje/makemkv-beta/ubuntu focal InRelease
Hit:2 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu focal InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu focal InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:6 http://us.archive.ubuntu.com/ubuntu focal-security InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
```

This is it. If it's not in these repos then I don't have it. No custom compilations.

```
$ sudo apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

full-upgrade also returns the same result.

```
$ sudo apt install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by &amp;KyT$0P# on 2021-06-10
Can you please post the output of
```
apt-get -s install build-essential
```

---

### Post by ajgreeny on 2021-06-10
I wonder if the two launchpad repos you are using
```
Hit:1 http://ppa.launchpad.net/heyarje/makemkv-beta/ubuntu focal InRelease
Hit:2 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu focal InRelease
```
have introduced different versions of some packages and upset the dependency requirements of something else as those three packages mentioned in your original post are available in the normal repos as versions that are above the minimum versions shown in that post so should be OK for your installation.

Have you tried installing **build-essential, debhelper** and **dh-autoreconf** separately or are they perhaps already installed?  If they are not installed already try doing so as a separate action; that may give us more clues in the output you get, so run command
```
sudo apt install debhelper build-essential dh-autoreconf
```
and copy back here the output you get.

---

### Post by Tadaen_Sylvermane on 2021-06-10
```
$ sudo apt-get -s install build-essentialReading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 build-essential : Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:9.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

```
$ apt policy libc6-devlibc6-dev:
  Installed: (none)
  Candidate: 2.31-0ubuntu9.2
  Version table:
     2.31-0ubuntu9.2 500
        500 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
     2.31-0ubuntu9 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
```

```
$ sudo apt install libc6-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.31-0ubuntu9.2) but 2.31-0ubuntu9.3 is to be installed
E: Unable to correct problems, you have held broken packages.
```


```
$ apt policy libc6libc6:
  Installed: 2.31-0ubuntu9.3
  Candidate: 2.31-0ubuntu9.3
  Version table:
 *** 2.31-0ubuntu9.3 100
        100 /var/lib/dpkg/status
     2.31-0ubuntu9.2 500
        500 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
     2.31-0ubuntu9 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages
```

I did a bunch of chasing with apt policy and trying to install. Ultimately the libc6 seems to be the issue. It is version 9.3 but stuff wants 9.2.

I tried eliminating both PPA's as well as dumping the packages themselves. No dice.

---

### Post by Bashing-om on 2021-06-10
Tadaen_Sylvermane; Yukkie

Something here is not adding up;
There is
> 
apt list libc6 >> libc6/now 2.31-0ubuntu9.3 amd64 


However
> 
apt show libc6-dev >> Depends: libc6 (= 2.31-0ubuntu9.2)


Are we looking at a packaging error ?

[INDENT][INDENT]south side of right ?[/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2021-06-10
Thanks for the outputs, that shows what's going on.  I had to fix this on another computer recently.

To help us determine the exact terminal command to suggest for you, can you please post the output from running the script from [this post]("https://ubuntuforums.org/showthread.php?t=2399096&p=13794515&viewfull=1#post13794515")?

(If it gives an error make sure you have [FONT=Courier New]python3-apt[/FONT] installed.)

---

### Post by Tadaen_Sylvermane on 2021-06-10
I don't know. This has been out since April of last year? I have doubts I'm the first person to hit it, unless there was an update recently. It's really odd. I am inching toward just putting Windows back on this machine for my games but I like being able to snapshot the file system with LVM. Makes backups 100x easier to deal with and I can just sync them to my server. Done twice a week currently.

---

### Post by Tadaen_Sylvermane on 2021-06-10
```
:~$ ./pyapt.py
libc-bin        2.31-0ubuntu9.3
libc6   2.31-0ubuntu9.3
libc6-dbg       2.31-0ubuntu9.3
locales 2.31-0ubuntu9.3
```


That's what it gave me.

---

### Post by &amp;KyT$0P# on 2021-06-10
Try
```
sudo apt-get install libc-bin/focal libc6/focal libc6-dbg/focal locales/focal
```

Can you now install [FONT=Courier New]libdvd-pkg[/FONT] ?

---

### Post by Tadaen_Sylvermane on 2021-06-11
That seems to have done it. It installed just fine right now.

Leaves the question though. Why did it need to be done in the first place? Where did it get the higher/wrong versions?

---

### Post by &amp;KyT$0P# on 2021-06-11
> **Tadaen_Sylvermane said:**
> Where did it get the higher/wrong versions?

Not sure but I'd guess this was probably a phased update that caused some people such severe issues that it got outright pulled from the repositories.*  The computer here that had this issue has automatic updates enabled and I have to do this sort of thing to it every so often.

* Confirmed [here]("https://launchpad.net/ubuntu/+source/glibc/+publishinghistory") -
> 2021-05-03 12:10:08 UTC 	Deleted 	Focal 	updates 	main 	libs 	2.31-0ubuntu9.3

    Removed from disk on 2021-05-03.
    Removal requested on 2021-04-27.
    Deleted on 2021-04-27 by &#321;ukasz Zemczak

    Update might be causing regressions in snaps and the core20 snap (LP: #1926355)


---

### Post by ajgreeny on 2021-06-11
Great news! 

Please mark as **SOLVED** from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by Tadaen_Sylvermane on 2021-06-11
Thank you much. Solved.

---

