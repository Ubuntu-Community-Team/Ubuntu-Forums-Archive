---
title: "VIDEO CONVERSION section probem?"
date: 2009-04-17
forum: Multimedia Software
---

### Post by musky on 2009-04-17
G'day folks,

Got 8.08 setup by wubi on this compaq sr2020nx & doing some final (flash & stuff) setups.

Got the nvidia driver loaded & started to go through the [[COLOR="Blue"]*Comprehensive Multimedia & Video Howto*[/COLOR]](http://ubuntuforums.org/showthread.php?t=766683) sticky here & all went well 'till (--PART 3/5, AUDIO & VIDEO CONVERSION--)
 
Not sure if this is a prob but here is the output.

After this 1st part: ([COLOR="Red"]in audio setup[/COLOR])
**echo "deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list**
[COLOR="Red"](EDIT-wrong: should have wrote)[/COLOR] [COLOR="Red"][SIZE="3"]**sudo apt-get install soundconverter audacity oggconvert**[/SIZE][/COLOR]
for below output.

-ended up with
```
Setting up audacity (1.3.5-2) ...

Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'

Setting up soundconverter (1.3.2-0ubuntu1) ...
Setting up oggconvert (0.3.1-3ubuntu1) ...

Processing triggers for libc6 ...

ldconfig deferred processing now taking place
```
=========================================================

after trying this next part: ([COLOR="Red"]video setup[/COLOR])
[COLOR="Red"]EDIT - wrong: -disregard->[/COLOR]**wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add - && sudo apt-get update**

-ended up with..
```
~**$ echo "deb http://winff.org/ubuntu intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list**

deb http://winff.org/ubuntu intrepid universe

yo@ubuntu:~[B]$ wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add - && sudo apt-get update
[/B]
gpg: no valid OpenPGP data found.
```

so stopped there. Something not right here or going on?
[COLOR="Red"][SIZE="4"]EDIT - I'm thinking this part--> gpg: no valid OpenPGP data found & the unknown media type stuff above[/SIZE][/COLOR] 

tia.

---

### Post by paul.gevers on 2009-04-17
> **musky said:**
> 
```
Setting up audacity (1.3.5-2) ...

Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'

Setting up soundconverter (1.3.2-0ubuntu1) ...
Setting up oggconvert (0.3.1-3ubuntu1) ...

Processing triggers for libc6 ...

ldconfig deferred processing now taking place
```

I don't believe this has anything to do with winff...

> ```
~$ echo "deb http://winff.org/ubuntu intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list

deb http://winff.org/ubuntu intrepid universe

yo@ubuntu:~$ wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add - && sudo apt-get update

gpg: no valid OpenPGP data found.
```

so stopped there. Something not right here or going on? tia.

What do you get if you only do the first part? Or something like:
```
wget --quiet --output-document=/tmp/winff.key
sudo apt-key add /tmp/winff.key
sudo apt-get update
```

---

### Post by musky on 2009-04-17
Had a look at the whole thing & turns out the info in my first post is incorrect as to what I did. Just spent an hour+ on it & writing a response..

Was just about all set to respond when .. got up to eat & when I came back, had a clean desktop & everything was gone.. browsers, docs konsoles.. etc

Have no idea how everything was shut down.. musta bumped the mouse ..or something.. wasn't a reboot, i know that for sure.

Will get back..

EDIT - just clicked on the bottom left button & got it all back..

---

### Post by musky on 2009-04-17
Ok.. edited my first post (in red) & here's the output that I didn't include from: sudo apt-get install soundconverter audacity oggconvert
```
sudo apt-get install soundconverter audacity oggconvert
[sudo] password for yo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtwolame0 libxine1-x libmodplug0c2 libxine1-gnome libxcb-xv0
  libboost-date-time1.34.1 libdca0 libiso9660-5 libdvbpsi4
  libboost-thread1.34.1 libmatroska0 libxine1-console libxine1-misc-plugins
  liblua5.1-0 vlc-data libxcb-shape0 libxcb-shm0 libvcdinfo0 libebml0
  libxine1-bin libxine1-ffmpeg libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libflac++6
Suggested packages:
  ladspa-plugin
The following NEW packages will be installed:
  audacity libflac++6 oggconvert soundconverter
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 3503kB of archives.
After this operation, 11.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com intrepid/main libflac++6 1.2.1-1.2 [38.7kB]
Get:2 http://ca.archive.ubuntu.com intrepid/universe audacity 1.3.5-2 [3330kB]
Get:3 http://ca.archive.ubuntu.com intrepid/universe soundconverter 1.3.2-0ubuntu1 [93.3kB]
Get:4 http://ca.archive.ubuntu.com intrepid/universe oggconvert 0.3.1-3ubuntu1 [40.5kB]
Fetched 3503kB in 1min19s (44.0kB/s)                                           
Selecting previously deselected package libflac++6.
(Reading database ... 137748 files and directories currently installed.)
Unpacking libflac++6 (from .../libflac++6_1.2.1-1.2_amd64.deb) ...
Selecting previously deselected package audacity.
Unpacking audacity (from .../audacity_1.3.5-2_amd64.deb) ...
Selecting previously deselected package soundconverter.
Unpacking soundconverter (from .../soundconverter_1.3.2-0ubuntu1_all.deb) ...
Selecting previously deselected package oggconvert.
Unpacking oggconvert (from .../oggconvert_0.3.1-3ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up libflac++6 (1.2.1-1.2) ...

Setting up audacity (1.3.5-2) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

& the rest is already posted above

```

So I'm wondering if anything is funny with -->gpg: no valid OpenPGP data found & the unknown media type stuff

Haven't done this part yet **sudo apt-get install avidemux ffmpeg winff**

---

### Post by musky on 2009-04-17
> **paul.gevers said:**
> What do you get if you only do the first part? Or something like:
```
wget --quiet --output-document=/tmp/winff.key
sudo apt-key add /tmp/winff.key
sudo apt-get update
```

Not sure what first part you mean? Afaik, everything went fine until possibly section 3 & the audio output (which may be no big deal ..dunno) & all the 'Unknown media type in type' outputs

& then not sure about the first 2 parts of the vid setup (below

~$ echo "deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list

deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid universe

yo@ubuntu:~$ wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add - && sudo apt-get update

gpg: no valid OpenPGP data found.

---

