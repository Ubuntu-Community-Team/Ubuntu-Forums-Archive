---
title: "Unable to Update in Ubuntu 10.10 Meerkat Alpha"
date: 2010-06-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by SteamInc on 2010-06-04
I have been using Ubuntu for one month already (Ubuntu 10.04) and I wanted to help Ubuntu so I decided to test the new versions of Ubuntu in a Virtual Box. I install the 10.10 Alpha (Meerkat) to test, but I am unable to update Ubuntu 10.10 Meerkat Alpha because of some error when I try to do so. 

Here's the error...


Could not initalize package information

An unresolvable problem has occured while initalizing the package information.

Please report this bug against the 'update manager' package and include the following error message:

'E:Encountered a section with no package: header,
E:Problem with the MergeList /var/lib/dpkg/status,
E:The package lists or status files could not be parsed or opened.'


Can somebody tell me how to fix this. And can somebody also tell if there is a bug report program so I can report this.

---

### Post by ranch hand on 2010-06-04
The very first thing you should do is go to the top of every index page for this forum and read ALL the stickies.

Then you will quit using Update Mangler because it is, too risky and too hard.

Pull up your terminal and run;
```

sudo dpkg --configure -a

```
This should do one of three things;
1>nothing, you just get another prompt
2>fix the problem
3>give error messages

Any of those three will be fine.

If 1 or 3 report back here with any out put from the terminal in the case of 3.

If 2 run;
```

sudo apt-get update

```
Follow that with;
```

sudo apt-get upgrade

```

---

### Post by seeker5528 on 2010-06-04
This sticky post provides some information and links.....

[http://ubuntuforums.org/showthread.php?t=1500648](http://ubuntuforums.org/showthread.php?t=1500648)

Not sure this is a type of thing that is useful to report, probably just some random glitch as opposed to something the software is doing wrong.

Theoretcially, the fix should be easy enough just clear out the list of available stuff......

Open a terminal window and type:

```
sudo dpkg --clear-avail
```

If a more extreme fix is needed then look in '/var/lib/dpkg/' for a file name status-old, if that exists you can rename the status file to something else and rename status-old to status.

```
cd /var/lib/dpkg
ls status*
sudo mv status status-bad
sudo cp status-old status
```

If it still doesn't work, then you would probably have to open '/var/lib/dpkg/status' in a text editor and look for the bad entry and delete it. Unless you have some indicator of what to look for in the status file, like a line number or name or something, it would probably be quicker at that point to re-install. Unless some script guru has a solution for this?

If you want to look at it, the package entries begin with something like:

```
Package: xserver-xorg-input-vmmouse
Status: install ok installed
Priority: optional
```

So you could use the search function in the text editor to search for 'Status:' and keep going to the next until you find an entry that is missing the 'Package:' line, which from the error message in your post, seems to be what is missing.

```
gksudo gedit /var/lib/dpkg/status
```

On my system gedit is showing the words matching the search highlighted in yellow, making it pretty easy to scroll through looking for an entry where 'Package:' is missing so it might be as bad as I was thinking to look for that, if you had to.

Later, Seeker

---

### Post by SteamInc on 2010-06-04
Ok thanks guys.

---

### Post by ranch hand on 2010-06-04
Just remember that it is going to break.  Do not rush anything.  Remember to breath.  Have FUN.

---

### Post by SteamInc on 2010-06-04
What do you mean by break? You mean the OS?

If it is i honestly got use to it when i was using windows so no problems.

---

### Post by SteamInc on 2010-06-04
Didn't work.

I got # 3.

Heres the error-

dpkg: parse error, in file '/var/lib/dpkg/status' near line 0: E0F after field name `'

---

### Post by ronacc on 2010-06-04
try seeker5528's fix for the status file , a couple of posts above .

---

### Post by SteamInc on 2010-06-05
Ok

---

### Post by SteamInc on 2010-06-06
Alright apparently seeker was right. My whole status file is empty.

---

### Post by SteamInc on 2010-06-06
Thank you very much Seeker. I had to use the extreme fix to make it work I can finally continue testing 10.10.

---

### Post by SteamInc on 2010-06-06
Lol now I cant get to the Desktop Enviorment. When i boot up the computer it just goes to terminal.

---

### Post by ranch hand on 2010-06-06
This should really be a separate thread.

Log in at the text login prompt.  Then;
```

sudo apt-get install ubuntu-desktop

```

---

### Post by SteamInc on 2010-06-06
thanks

---

### Post by indigoblue on 2010-06-24
I got a similar message, and I tried using ranch hand and seeker's solutions, but I still can't update.

Here's the error I get:

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 1 (the only line) in source list /etc/apt/sources.list.d/ubuntu-tweak-stable.list (dist parse), E:The list of sources could not be read.'
```

I had Ubuntu-tweak, but I got an error with that as well, so I uninstalled it.

This is Line 1 in the source list /etc/apt/sources.list.d/ubuntu-tweak-stable.list ```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu main #Ubuntu Tweak Stable Source
```.
I can open it in gedit, but I can't delete it?

What should I do?

Thanks!
(And sorry, I'm new. Please don't bite.)

---

### Post by indigoblue on 2010-06-24
EDIT:

I solved the problem, in case anyone else runs into this as well -
I right clicked on the Update Manager and went into Preferences > Software Sources, and unchecked the Ubuntu-Tweak source. It closed out, then I reopened Update Manager, and it worked :D

I'm thinking it's because Ubuntu-tweak isn't supported for Meerkat?

---

### Post by ranch hand on 2010-06-24
Try;
```

gksudo gedit /etc/apt/sources.list.d

```
and just a ## to the start of that line (comment it out).

---

### Post by seeker5528 on 2010-06-24
> **indigoblue said:**
> EDIT:
I'm thinking it's because Ubuntu-tweak isn't supported for Meerkat?

Don't know what is going on with ubuntu-tweek at the moment, but the message you were getting was about the source line being wrong:

```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu main #Ubuntu Tweak Stable Source
```

If you go to [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) and look at the dists directory you see lucid is the newest distribution supported and in the pool directory you see main is the only pool. So what you should have is:
```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu lucid main #Ubuntu Tweak Stable Source
```

In the software sources utility you should be able to select the entry, choose edit, then just put lucid in the distribution box.

One of the advantages to having these things in separate files, aside from not messing up '/etc/apt/sources.list' is that often you can quickly see from the command line with in ls command:

```
ls /etc/apt/sources.list.d
```

then quicly enable/disable by renaming the relavant file so it ends with .list or doesn't:

```
sudo mv /etc/apt/sources.list.d/ubuntu-tweak-stable.list /etc/apt/sources.list.d/ubuntu-tweak-stable.list.old

sudo mv /etc/apt/sources.list.d/ubuntu-tweak-stable.list.old /etc/apt/sources.list.d/ubuntu-tweak-stable.list
```

Later, Seeker

---

### Post by indigoblue on 2010-06-25
Thanks for the responses ^__^
I'm still new to Ubuntu and the terminal, so thanks for the help!

---

