---
title: "cant install flash, maybe broke synaptic?"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by lunaz on 2007-02-24
i tried to do sudo apt-get install flashplugin-nonfree
and it kept timing out, so i exit terminal, open synaptic to see if anything's in there & i got this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

then i ran dpkg --configure -a & it kept timing out too.. so i found that flash tutorial at [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

and i got stuck at

wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

cuz it timed out lol....did i break something? far as i know the uni/multi repos are on.

oh, i can now get into synaptic, but by now i have no idea what's going on.

---

### Post by r4ik on 2007-02-24
Try that first link again.
Works like a charm for me,just checked.

---

### Post by lunaz on 2007-02-24
well synaptic just timed out too.

---

### Post by r4ik on 2007-02-24
Now i get timed out in attempt to get to link you to a page with
a possible solution.
Somebody is making waves...
Give it some time.

---

### Post by lunaz on 2007-02-24
haha damn o_o

i did try sudo aptitude update && sudo aptitude install flashplugin-nonfree & i dunno if it worked or not; i got no errors but i still can't see youtube movies. before i tried psychocats 2nd method.

how do u see what plugins are installed?

---

### Post by r4ik on 2007-02-24
about:plugins in the firefox bar (what is that called again ?)
Just a second got this stupid editor running

---

### Post by r4ik on 2007-02-24
Cant loose the stupid smiley.

Look at this as one written behind each other

about
:
config

:) I am making a complete idiot of myself.

---

### Post by lunaz on 2007-02-24
still not working :( and whats that error about dpkg mean?

```

gail@gail-oldpos:~$ sudo aptitude update && sudo aptitude install flashplugin-nonfree
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_CA             
Get:2 http://archive.ubuntu.com edgy Release.gpg [191B]
Ign http://archive.ubuntu.com edgy/universe Translation-en_CA
Ign http://security.ubuntu.com edgy-security/universe Translation-en_CA
Hit http://security.ubuntu.com edgy-security Release
Ign http://archive.ubuntu.com edgy/main Translation-en_CA
Ign http://archive.ubuntu.com edgy/restricted Translation-en_CA
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_CA
Get:3 http://archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_CA
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_CA
Hit http://security.ubuntu.com edgy-security/main Packages
Get:4 http://archive.ubuntu.com edgy-backports Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_CA
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_CA
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_CA
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_CA
Hit http://archive.ubuntu.com edgy Release     
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/universe Sources
Hit http://archive.ubuntu.com edgy-updates Release
Hit http://archive.ubuntu.com edgy-backports Release
Hit http://archive.ubuntu.com edgy/main Sources
Hit http://archive.ubuntu.com edgy/restricted Sources
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://archive.ubuntu.com edgy/universe Sources
Hit http://archive.ubuntu.com edgy-updates/main Packages                        
Hit http://archive.ubuntu.com edgy-updates/restricted Packages                  
Hit http://archive.ubuntu.com edgy-updates/main Sources                         
Hit http://archive.ubuntu.com edgy-updates/restricted Sources                   
Hit http://archive.ubuntu.com edgy-backports/main Packages                      
Hit http://archive.ubuntu.com edgy-backports/restricted Packages                
Hit http://archive.ubuntu.com edgy-backports/universe Packages                  
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages                
Hit http://archive.ubuntu.com edgy-backports/main Sources                       
Hit http://archive.ubuntu.com edgy-backports/restricted Sources                 
Hit http://archive.ubuntu.com edgy-backports/universe Sources                   
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources                 
Fetched 4B in 6s (1B/s)                                                         
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
gail@gail-oldpos:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
gail@gail-oldpos:~$ sudo dkpg --configure -a
sudo: dkpg: command not found
gail@gail-oldpos:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.31.0.1ubuntu1~edgy1) ...
Downloading...
--18:36:36--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 1.0.0.0
Connecting to fpdownload.macromedia.com|1.0.0.0|:80... 

```

from there it just says time out then tries again. then times out ..etc

edit: psychocat method2 & synaptic both time out at the same step.

---

### Post by countervail on 2007-11-19
Same thing happened to me...It&#347; driving me crazy :confused:

```

cvail@mynbox:/$ sudo dpkg --configure -a && sudo apt-get -f install
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--21:14:57--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 84.53.170.70
Connecting to fpdownload.macromedia.com|84.53.170.70|:80... 
failed: Connection timed out.
Retrying.

--21:18:08--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
  (try: 2) => `./install_flash_player_9_linux.tar.gz'
Connecting to fpdownload.macromedia.com|84.53.170.70|:80...

```

Any ideas?

---

### Post by lunaz on 2007-11-19
Last time I installed flash was just thru the firefox plugin thingy... worked good!

---

### Post by ghaz on 2007-11-20
The difference between the flash plugin and the other packages is that the actual flash plugin is downloaded from adobe.com and not from the ubuntu repos.

Do you access the internet through a proxy? You might need to set the http_proxy variable to point to your proxy. Take a look at this old thread [http://ubuntuforums.org/showthread.php?t=96802]("http://ubuntuforums.org/showthread.php?t=96802")

I hope this helps.

---

### Post by countervail on 2007-11-20
> **ghaz said:**
> The difference between the flash plugin and the other packages is that the actual flash plugin is downloaded from adobe.com and not from the ubuntu repos.

Do you access the internet through a proxy? You might need to set the http_proxy variable to point to your proxy. Take a look at this old thread [http://ubuntuforums.org/showthread.php?t=96802]("http://ubuntuforums.org/showthread.php?t=96802")

I hope this helps.

Worked like a charm, much appreciated your help, ghaz

What I did is:

```

export http_proxy=http://myproxy:myport

then

sudo dpkg --configure -a

```

Thanks again people :D

---

### Post by Bablefish on 2007-11-20
Flash is also located in Add/Remove you can install it from there.

---

