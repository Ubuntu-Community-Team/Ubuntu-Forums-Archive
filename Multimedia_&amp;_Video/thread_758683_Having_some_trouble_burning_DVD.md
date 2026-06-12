---
title: "Having some trouble burning DVD"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by mowque on 2008-04-18
(first post, nice forums btw)

Ubntu is being troublesome in burning videos onto DVD+R or DVD-R, I managed to put 223mb on a 4.3 gig DVD but now it won't take anymore. IS their a way to clear the old info off and start again? 

Also, on another DVD, after attempted to put some of the same type of vids, flv. format, Ubuntu 'cannot mount disc'......I'm a new user, and i'm not using any speaical burning programs, any help?

---

### Post by xc3RnbFO8P on 2008-04-18
In Synaptic Package Manager (Gusty): 
Settings> Repositories> Ubuntu Software check all, uncheck cd
Settings> Repositories> Updates  check all  (close settings window and reload)

Then use this to install:
[http://ubuntuforums.org/showpost.php?p=4736469&postcount=2]("http://ubuntuforums.org/showpost.php?p=4736469&postcount=2")

---

### Post by mowque on 2008-04-18
thanks for the speedy response.....for getting the Termial stuff right in your linked post, after many of the commands it said "Failure or Error", and for the last one it said that it was expertimantal....Is this normal?

---

### Post by xc3RnbFO8P on 2008-04-18
And you did this first?
In Synaptic Package Manager (Gusty):
Settings> Repositories> Ubuntu Software check all, uncheck cd
Settings> Repositories> Updates check all (close settings window and reload)
Check the **Server** you download from: **Settings> Repositories> Ubuntu Software**
Try change Server.

---

### Post by mowque on 2008-04-18
Sorry to ask again, but what cd do you mean? the only place where Cd is mentioned on "Settings> Repositories> Ubuntu Software check all, uncheck cd" is at the bottom,"CD-rom with Ubuntu 7.10, Gusty Gibbon", it is checked....should i uncheck it? Also i cannot check a box called 'Source Code".....?

---

### Post by xc3RnbFO8P on 2008-04-18
> CD-rom with Ubuntu 7.10, Gusty Gibbon", it is checked....should i uncheck it? Also i cannot check a box called 'Source Code".....?
Yes, and source is ok with -

---

### Post by mowque on 2008-04-18
ok, i did all that stuff, changed server but this is the type of thing i am getting after the terminal commands,

Connecting to packages.medibuntu.org|213.186.45.139|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:36:09 ERROR 404: Not Found.

I assume that is bad?

---

### Post by xc3RnbFO8P on 2008-04-18
**Copy and paste **did you do that?

---

### Post by mowque on 2008-04-18
i copied and pasted the termial commands, yes....is that bad?

matthew@matthew-laptop:~$  wget -c [http://packages.medibuntu.org/pool/n...untu1_i386.deb](http://packages.medibuntu.org/pool/n...untu1_i386.deb)
--10:36:09--  [http://packages.medibuntu.org/pool/n...untu1_i386.deb](http://packages.medibuntu.org/pool/n...untu1_i386.deb)
           => `n...untu1_i386.deb'
Resolving packages.medibuntu.org... 213.186.45.139, 87.98.242.10, 88.191.30.43, ...
Connecting to packages.medibuntu.org|213.186.45.139|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:36:09 ERROR 404: Not Found.

That is the whole thing, copied and pasted out of Terminal

---

### Post by xc3RnbFO8P on 2008-04-18
try:
> wget -c [http://packages.medibuntu.org/pool/n...untu1_i386.deb](http://packages.medibuntu.org/pool/n...untu1_i386.deb)

---

### Post by mowque on 2008-04-18
it worked! Should all the rest of them work now? (thanks alot for spending your time, this is why Linux is better then Windows, at least the main one)

---

### Post by xc3RnbFO8P on 2008-04-18
yes just copy paste all away down

---

### Post by mowque on 2008-04-18
dpkg: error processing w32codecs_20071007-0medibuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20071007-0medibuntu1_i386.deb

I got this from the next one...what is the problem?

---

### Post by xc3RnbFO8P on 2008-04-18
You did:
wget -c......... <return>
sudo dpkg..... <return>

did you do this in right order?

If not start again :)

---

### Post by xc3RnbFO8P on 2008-04-18
In SynapticPackage Manager search and install:
Win32 codec 
libdvdcss2
But this in Terminal:
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
> sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by mowque on 2008-04-18
still isn't working, eve in the right order,lol. What do you mean search and install in Synaptic manager? (i'm a newbie Linux user)

---

### Post by xc3RnbFO8P on 2008-04-18
Can you see search button in Synaptic P ..?
In search window write  **Win32 codec**

---

### Post by mowque on 2008-04-18
ah, i did that, but it said that the three different pieces won't install...i thought i was trying the wrong thing. I do this before all the terminal stuff?

---

### Post by xc3RnbFO8P on 2008-04-18
Yes, if it works then you only have to do:
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
> sudo /usr/share/doc/libdvdread3/install-css.sh
in terminal

---

### Post by mowque on 2008-04-18
the middle on worked but for the other two i get this- 

mplayer-nogui:
 Depends: libfaac0 (>=1.24clean) but it is not installable
 Depends: libggi2 (>=1:2.2.1) but it is not installable
 Depends: libjack0 (>=0.103.0) but it is not installable

and so on.... any way i can get around this?

---

### Post by xc3RnbFO8P on 2008-04-18
You are geting there, now you search and install:
libfaac0 
libggi2 
libjack0

---

### Post by mowque on 2008-04-18
I got no hits on those searchs

---

### Post by xc3RnbFO8P on 2008-04-18
In Terminal:
> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by mowque on 2008-04-18
First one worked, the second one did alot of stuff put ended with this-

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by xc3RnbFO8P on 2008-04-18
You need to **turn off** Synaptic, and try again

---

### Post by mowque on 2008-04-18
Wow, i'm a complete idiot......well, it worked that time...now what?

---

### Post by xc3RnbFO8P on 2008-04-18
Now back to [post #15]("http://ubuntuforums.org/showpost.php?p=4740761&postcount=15")

---

### Post by mowque on 2008-04-18
is that it? it worked.....thanks for all that

---

### Post by xc3RnbFO8P on 2008-04-18
Now try to play Dvd and post it, does work.

---

### Post by mowque on 2008-04-18
i can watch DVD's...but it still won't let me edit the DVD's with my info on them

---

### Post by xc3RnbFO8P on 2008-04-18
Try to burn dvd with K3B in Application> Sound&Video

---

### Post by mowque on 2008-04-18
it wasn't thier, i went to install it, and i got this!- 

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by mowque on 2008-04-18
bah, ok...it is all fixed. I'm installing K3B right now, should that work?

---

### Post by xc3RnbFO8P on 2008-04-18
Hopefully :)

---

### Post by mowque on 2008-04-18
Ok, K3B is working, looks cool...but my DVd gives me this- Malformed URL
media://dev/hda

---

### Post by xc3RnbFO8P on 2008-04-18
> **mowque said:**
> Ok, K3B is working, looks cool...but my DVd gives me this- Malformed URL
media://dev/hda

Can you send a sceenshot.

---

### Post by mowque on 2008-04-18
ok, this is what comes up when i first put it in

---

### Post by xc3RnbFO8P on 2008-04-18
In /home/your folder/**.kde** 
Rename .kde to .kde.back
Restart the computer
Start K3b again

---

