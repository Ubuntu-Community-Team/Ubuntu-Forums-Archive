---
title: "Karmic cant play region 1 DVDs?"
date: 2010-01-11
forum: Multimedia Software
---

### Post by Naphrys on 2010-01-11
my laptop is having issues with DVD's.
I can play region free DVD's (they were gifts), but I can't play any of my legit Region 1 DVD's? 
I downloaded the codecs from the software center but for whatever reason, They don't work, both Mplayer and Movie player just give me error messages when I load the disks. I know the disks are being read, their name pops up and everything, but I guess it just cant read the files.

Any ideas?

---

### Post by ron999 on 2010-01-11
Hi
Try running **regionset**.
It will tell you which region it's set to, and how many lives you've got left.

> Regionset is a small utility which displays and sets
the region/zone setting of a DVD drive, allowing it to decrypt
the DVD's sold in this geographical zone. Hardware vendors
often limit the number of such modifications, but it is
necessary to set it at least once with a brand new drive.


Get it through Synaptic or use:-
```
sudo apt-get install regionset

```
:cool:

---

### Post by Naphrys on 2010-01-11
OK that didn't seem to help, Keeps giving me the same error messages as before. 

When I ran the install it said something like [region 0.1-3] no clue what that means though.

---

### Post by SuperSonic4 on 2010-01-11
It could be because the region 1 dvds have special protection?

Is libdvdcss installed?

---

### Post by Naphrys on 2010-01-11
tried to install libdvdcss, this is what I got back

"Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

---

### Post by benerivo on 2010-01-11
> **Naphrys said:**
> OK that didn't seem to help, Keeps giving me the same error messages as before. 

When I ran the install it said something like [region 0.1-3] no clue what that means though.

I think 0.1-3 was just the version of regionset (see[http://packages.ubuntu.com/karmic/regionset](http://packages.ubuntu.com/karmic/regionset)). You need to run regionset to set your DVD drive to be at region 1 (presumably it's not at that now). It may also be a problem if you don't have the libdvdcss package installed.

---

### Post by mc4man on 2010-01-11
Either add medibuntu to your sources and then try to install libdvdcss2 again Copy and paste complete command into terminal
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Or run this (again c & p complete command

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly \
&& sudo /usr/share/doc/libdvdread4/install-css.sh
```

Then if need be address region setting

---

### Post by Naphrys on 2010-01-11
> **mc4man said:**
> Either add medibuntu to your sources and then try to install libdvdcss2 again Copy and paste complete command into terminal
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Or run this (again c & p complete command

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly \
&& sudo /usr/share/doc/libdvdread4/install-css.sh
```Then if need be address region setting


This fixed it, thank you!

---

### Post by anco on 2010-01-17
I was just playing with regionset today too, and found this interesting. I could change my drive to region 0 ( so it plays all regions now..) see what i tried at the commandline. I searched a bit and it seems nobody else reported this, so I hope it is worth reporting it here.

This is how I started and accidently I had a region 0 dvd in the dvd drive

[I]anco@anco-HP-Desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 3
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:0
New mask: 0x00, correct? [y/n]:y
Region code set successfully!
[/I]

Totally surprising it accepted my stubborn 0 while it was asking for 1..8 [http://ubuntuforums.org/images/smilies/icon_surprised.gif](http://ubuntuforums.org/images/smilies/icon_surprised.gif)
This I had to check

[I]anco@anco-HP-Desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 2
drive plays discs from region(s): 1 2 3 4 5 6 7 8, mask=0x00
[/I]
[I]Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:2
New mask: 0xFFFFFFFD, correct? [y/n]:y
ERROR: Region code could not be set!
[/I]

What it did not set region 2 ? 
Okay other test I picked up a region 1 dvd and inserted it.

[I]anco@anco-HP-Desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 2
drive plays discs from region(s): 1 2 3 4 5 6 7 8, mask=0x00

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:1
New mask: 0xFFFFFFFE, correct? [y/n]:y
Region code set successfully!
[/I]

So with a DVD in the player from that region I could set it to that region

[I]anco@anco-HP-Desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: LAST CHANCE
vendor resets available: 4
user controlled changes resets available: 1
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n
[/I]

With only one last change to change it, there was no room to play anymore, so I wanted to change it back to region 0

[I]anco@anco-HP-Desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: LAST CHANCE
vendor resets available: 4
user controlled changes resets available: 1
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:0
New mask: 0x00, correct? [y/n]:y
ERROR: Region code could not be set!
[/I]
What the heck, now I got a little sweaty....I want my region 0 back!!! 
Mmm let's give it another try. Put back a region 0 dvd in my drive.

[I]anco@anco-HP-Desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
[/I]
Oops too anxious to get it quickly going, wait for the dvddrive to recognise the disc.....

[I]anco@anco-HP-Desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: LAST CHANCE
vendor resets available: 4
user controlled changes resets available: 1
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:0
New mask: 0x00, correct? [y/n]:y
Region code set successfully!
[/I]
Pfew luckily it worked!!! Let's check one more time.

[I]anco@anco-HP-Desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: PERMANENT
vendor resets available: 4
user controlled changes resets available: 0
drive plays discs from region(s): 1 2 3 4 5 6 7 8, mask=0x00

Would you like to change the region setting of your drive? [y/n]:n
anco@anco-HP-Desktop:~$ 
[/I]
You can see no more changes left and it is permanently region 0 now.. And yes I can indeed copy my region 0, 1, 2 dvd's I have no other dvd's than these 3 regions.

Thank you regionset programmers.. In the past I had to reflash the dvd drives with rpc1 or rpc2 firmwares. This time I was lucky on this liteon drive.

---

### Post by ron999 on 2010-01-17
This is very interesting.
Strange that nobody else has tried it.

Kudos
:D:D

But it didn't work for me!
> regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:0
New mask: 0x00, correct? [y/n]:y
ERROR: Region code could not be set!

---

