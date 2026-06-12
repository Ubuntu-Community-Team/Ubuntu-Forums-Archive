---
title: "Ok I Really Need Help Here, Heellpppp"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by tribeone on 2007-06-11
OK, I loaded the libdvdcss and nothing is working now at least before I could see thedvd now all I get is this error messege:

[PHP]The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?[/PHP]

and when I try to update i get this:

[PHP]It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/PHP]

Can anyone please help? This is everything I have done so far:

[PHP]sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
Password:
Reading package lists... Done
Building dependency tree... Done
totem-xine is already the newest version.
Package libxine1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine-main1
E: Package libxine1 has no installation candidate
faruq@faruq-desktop:~$  

Reading package lists... Done
Building dependency tree... Done
libxine-main1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  [/PHP]

and when I run  sudo apt-get -f i get back this:
[PHP]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
faruq@faruq-desktop:~$[/PHP]

---

### Post by tgm4883 on 2007-06-11
you need libdvdcss2

---

### Post by kevinlyfellow on 2007-06-11
What happens when you just run synaptic?

The last command you issued seemed to think you had another package manager running.  When you issue the command "sudo apt-get -f" you can't have any other package manager running (including your updater).

---

### Post by tribeone on 2007-06-12
Ok I did what you said kevin and made sure nothing else was running when I issued the sudo command and this is what I got back

> faruq@faruq-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  libdvdcss2 libdvdcss2-dev
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 397kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 105276 files and directories currently installed.)
Removing libdvdcss2-dev ...
Removing libdvdcss2 ...
faruq@faruq-desktop:~$

---

### Post by kevinlyfellow on 2007-06-12
Ok, there seems like there was an issue with dependencies.  This will not solve the problem, but will give us a better idea on what the problem is.

```

sudo apt-get install -s libdvdcss2

```

What this will do is simulate what would happen if you try to install libdvdcss2.

Let us know how it responds

---

### Post by tribeone on 2007-06-12
Ok I used the command and got back this
> 
faruq@faruq-desktop:~$ sudo apt-get install -s libdvdcss2
Password:
Reading package lists... Done
Building dependency tree... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
faruq@faruq-desktop:~$

---

### Post by kevinlyfellow on 2007-06-12
That's kinda funny, since it seemed like it just removed libdvdcss2... well as long as it's there.

now just issue these commands
```

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

```

---

### Post by tribeone on 2007-06-12
ok this seems crazy to me but this is what I got back

> faruq@faruq-desktop:~$ sudo apt-get install libdvdread3
Reading package lists... Done
Building dependency tree... Done
libdvdread3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
faruq@faruq-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found
faruq@faruq-desktop:~$ sudo apt-get install totem-xine
Reading package lists... Done
Building dependency tree... Done
totem-xine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
faruq@faruq-desktop:~$


---

### Post by kevinlyfellow on 2007-06-12
Ok, try this
```

sudo apt-get  --reinstall install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

```

---

### Post by tribeone on 2007-06-12
Heres the result
```

faruq@faruq-desktop:~$ sudo apt-get  --reinstall install libdvdread3
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 52.2kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com dapper/main libdvdread3 0.9.4-5.1 [52.2kB]
Fetched 52.2kB in 2s (19.3kB/s)
(Reading database ... 105292 files and directories currently installed.)
Preparing to replace libdvdread3 0.9.4-5.1 (using .../libdvdread3_0.9.4-5.1_i386.deb) ...
Unpacking replacement libdvdread3 ...
Setting up libdvdread3 (0.9.4-5.1) ...

faruq@faruq-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found
faruq@faruq-desktop:~$
```

---

### Post by kevinlyfellow on 2007-06-12
I've attached the script.
Download it to your home directory and then 
```
sudo ~/install-css.sh
```

---

### Post by tribeone on 2007-06-12
how do I find my home directory? I am really new to most of this. When I click the att it opens with text editor

---

### Post by kevinlyfellow on 2007-06-12
:-)
When it opens in the text editor, save it as /home/faruq/install-css.sh

---

### Post by tribeone on 2007-06-12
ok I got this back

> faruq@faruq-desktop:~$ sudo ~/install-css.sh
sudo: /home/faruq/install-css.sh: command not found
faruq@faruq-desktop:~$


---

### Post by kevinlyfellow on 2007-06-12
Ok, this is getting weird.  

Can you give me the output of the following commands?
```

ls /usr/share/doc/libdvdread3/

```
and 
```

ls ~/install-css.sh

```

---

### Post by tribeone on 2007-06-12
Ok here ya go. This is really bugging me out

> faruq@faruq-desktop:~$ ls /usr/share/doc/libdvdread3/
changelog.Debian.gz  changelog.gz  copyright  examples  README.Debian
faruq@faruq-desktop:~$

faruq@faruq-desktop:~$ ls ~/install-css.sh
/home/faruq/install-css.sh

---

### Post by kevinlyfellow on 2007-06-12
#-o
Linux security requires us to make sure that the file is allowed to be executed.

```

chmod 700 /home/faruq/install-css.sh
sudo /home/faruq/install-css.sh

```

---

### Post by tribeone on 2007-06-12
OK did that now what](*,)
```

faruq@faruq-desktop:~$ chmod 700 /home/faruq/install-css.sh
faruq@faruq-desktop:~$ sudo /home/faruq/install-css.sh
Password:
--02:03:38--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb
           => `/tmp/dvdcss-45giuj/libdvdcss.deb'
Resolving www.dtek.chalmers.se... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        22.52K/s

02:03:39 (22.46 KB/s) - `/tmp/dvdcss-45giuj/libdvdcss.deb' saved [25178/25178]

dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu2 to 1.2.5-1.
(Reading database ... 105292 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu2 (using .../dvdcss-45giuj/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

faruq@faruq-desktop:~$

```

---

### Post by kevinlyfellow on 2007-06-12
try playing a dvd in totem! (Its in Applications -> Sound and Video -> Movie Player)

---

### Post by tribeone on 2007-06-12
I got this
> The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

I am going nuts

---

### Post by kevinlyfellow on 2007-06-12
> I am going nuts
I would be too!

ok, how about this.  Let's start from the begining.
```
sudo apt-get autoremove libdvdread3 libdvdcss2
sudo apt-get install totem
```

then (source: [http://www.cs.cornell.edu/~djm/ubuntu/#multimedia](http://www.cs.cornell.edu/~djm/ubuntu/#multimedia))
```

wget -c -P /tmp/ http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
wget -c -P /tmp/ http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb
sudo dpkg -i /tmp/w32codecs_20061022-0.0_i386.deb /tmp/libdvdcss2_1.2.9-0.0_i386.deb
sudo apt-get install totem-xine libxine-extracodecs

```

---

### Post by kevinlyfellow on 2007-06-12
I'm also kinda curious about what would happen if you tried another media player.

I've always had good luck with xine-ui
```

sudo apt-get install xine-ui

```

It seems like you had everything working fine, I'm wondering if its not just totem not working correctly

---

### Post by tribeone on 2007-06-12
> **kevinlyfellow said:**
> I would be too!

ok, how about this.  Let's start from the begining.
```
sudo apt-get autoremove libdvdread3 libdvdcss2
sudo apt-get install totem
```

then (source: [http://www.cs.cornell.edu/~djm/ubuntu/#multimedia](http://www.cs.cornell.edu/~djm/ubuntu/#multimedia))
```

wget -c -P /tmp/ http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
wget -c -P /tmp/ http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb
sudo dpkg -i /tmp/w32codecs_20061022-0.0_i386.deb /tmp/libdvdcss2_1.2.9-0.0_i386.deb
sudo apt-get install totem-xine libxine-extracodecs

```

ok with the first 2 codes  I get this

```
faruq@faruq-desktop:~$ sudo apt-get autoremove libdvdread3 libdvdcss2
E: Invalid operation autoremove
faruq@faruq-desktop:~$
faruq@faruq-desktop:~$ sudo apt-get install totem
Reading package lists... Done
Building dependency tree... Done
totem is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdvdcss2-dev: Depends: libdvdcss2 (= 1.2.9-2medibuntu2) but 1.2.5-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I get the same error codes with all the players. With the second set of wget codes I get this:
> 
faruq@faruq-desktop:~$ wget -c -P /tmp/ [http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb)
--10:21:13--  [http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb)
           => `/tmp/libdvdcss2_1.2.9-0.0_i386.deb'
Resolving [www.debian-multimedia.org](www.debian-multimedia.org)... 213.186.33.17
Connecting to www.debian-multimedia.org|213.186.33.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb) [following]
--10:21:13--  [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb)
           => `/tmp/libdvdcss2_1.2.9-0.0_i386.deb'
Resolving ftp.sunet.se... 194.71.11.69, 2001:6b0:19::64
Connecting to ftp.sunet.se|194.71.11.69|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32,680 (32K) [application/x-debian-package]

100%[====================================>] 32,680        21.04K/s

10:21:15 (20.97 KB/s) - `/tmp/libdvdcss2_1.2.9-0.0_i386.deb' saved [32680/32680]
faruq@faruq-desktop:~$ sudo dpkg -i /tmp/w32codecs_20061022-0.0_i386.deb /tmp/libdvdcss2_1.2.9-0.0_i386.deb
(Reading database ... 105292 files and directories currently installed.)
Preparing to replace w32codecs 20061022-0medibuntu1 (using .../w32codecs_20061022-0.0_i386.deb) ...
Unpacking replacement w32codecs ...
Preparing to replace libdvdcss2 1.2.5-1 (using .../libdvdcss2_1.2.9-0.0_i386.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up w32codecs (20061022-0.0) ...
Setting up libdvdcss2 (1.2.9-0.0) ...

faruq@faruq-desktop:~$ sudo apt-get install totem-xine libxine-extracodecs
Reading package lists... Done
Building dependency tree... Done
totem-xine is already the newest version.
libxine-extracodecs is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdvdcss2-dev: Depends: libdvdcss2 (= 1.2.9-2medibuntu2) but 1.2.9-0.0 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
faruq@faruq-desktop:~$


and with the sudo apt-get install xine-ui I get this:
> faruq@faruq-desktop:~$ sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdvdcss2-dev: Depends: libdvdcss2 (= 1.2.9-2medibuntu2) but 1.2.9-0.0 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
faruq@faruq-desktop:~$
 
What the heck is going on here. To me it looks like everything is thee but not working "argghhhhhhh"

---

### Post by kevinlyfellow on 2007-06-13
Well, I think that dvds were not playing because totem-xine didn't install for some reason (only the standard totem was available).  apt-get is acting really crazy for you for some reason.  

BTW, which version are you running?  The autoremove feature for apt-get is for feisty, sorry I just kinda assumed...

You do not need libdvdcss2-dev, so...
```

sudo apt-get remove libdvdcss2-dev
sudo apt-get -f install
sudo apt-get install xine-ui

```

Another thing you can do, post the result of
```

cat /etc/apt/sources.list

```

And finally, look around the in synaptic.  There should be a place that shows you what files were not installed via your repositories.  I'd give better directions, but I don't think your using the same version as me.  On mine, I press the origins button and it I choose "Local/main" in the side bar.  If you can find that, please post what packages are listed.  This all should work without resorting to downloading stuff from other places!

Sorry this is such a mess.  Something weird happened somewhere along the line and it its playing tricks with apt.

---

### Post by tribeone on 2007-06-13
HEy Kevin how are you thanks a lot for your help. I am using 6.06 dapper i think. Funny thing dvd played with mplayer by using  gmplayer in terminal. but still none of the players work through app-sound and video. I will try doing what you said above

---

### Post by tribeone on 2007-06-13
Ok this is what iI got following the apt-get remove

> faruq@faruq-desktop:~$ sudo apt-get remove libdvdcss2-dev
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libdvdcss2-dev
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 291kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 105227 files and directories currently installed.)
Removing libdvdcss2-dev ...

and these are the result to the cat command

> faruq@faruq-desktop:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
#AUTOMATIX REPOS END
faruq@faruq-desktop:~$



Fuuny thing now the dvd plays but you cant hear the voice diaolog. I mean you can hear the music some of the background noise ( people walking etc) but no voice.

---

### Post by kevinlyfellow on 2007-06-13
I think that your problem may have been with automatix... lots of people have complained about it screwing up their system.

> Fuuny thing now the dvd plays but you cant hear the voice diaolog. I mean you can hear the music some of the background noise ( people walking etc) but no voice.

Excellent... so what are you using to play the dvds?  My guess why you aren't getting sound to work is because its not playing the language track.  Not sure why this would be the case, but if I know the player I may be able to figure out how to fix it.

---

### Post by tribeone on 2007-06-13
Ok here it goes. If I open a terminal and type in gmplayer the mplayer will open and play the dvd fine ( I was surprised), but if I open mplayer  or totem movie player or any other player it will play but all you get is the video and the music in the movie and maybe a little bit of people moving sound but no diaolog at all. Now if I go to the sound menu for the player and choose let say french I get voice sound  and if I choose one of the 2 english settings I get the voice of the commentary but no movie diaolog at all. The players I have are totem movie player xine, mplayer, kaffeine, and gxine. same response on all of them except when i load mplayer from terminal. Hope that helps

---

### Post by kevinlyfellow on 2007-06-13
Another weird thing...

In xine, try changing the audio channel from auto to something else.  See the attached pic.

---

### Post by tribeone on 2007-06-13
my gxine doesnt look like that i dont see a lang setting

---

### Post by tribeone on 2007-06-13
Ok it now seems as though only the totem xine player wont work

---

### Post by kevinlyfellow on 2007-06-13
sorry, that is xine-ui, I thought you had it listed.

in gxine, there is a number on the bottom right (again we may have different versions).  By default it is set to -1 (which means automatic).  Try changing it and see if you can find an appropriate audio channel.  Just out of curiosity, have you tried it on more than one dvd?

---

### Post by kevinlyfellow on 2007-06-13
> **tribeone said:**
> Ok it now seems as though only the totem xine player wont work

Well, totem is a bit annoying because it comes in two versions, totem-gstreamer and totem-xine.  totem-gstreamer has a bug that it won't play dvds, which is why everyone always says "sudo apt-get install totem-xine"

---

