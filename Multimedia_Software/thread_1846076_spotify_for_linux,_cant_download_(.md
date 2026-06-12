---
title: "spotify for linux, cant download :("
date: 2011-09-18
forum: Multimedia Software
---

### Post by s3l3ct on 2011-09-18
I installed ubuntu 11.04 64 bit on my new asus 1215B, works like a charm, only one major problem so far: Im failing to install spotify!

I have a premium spotify account, so when it wouldnt let me install it on wine I thought Id just get the Spotify for linux, but running the code in terminal (deb [http://repository.spotify.com](http://repository.spotify.com)) just tells me "deb command not found"... Is there anywhere I can download it without using terminal, or am I missing something? 

And if I install Spotify on wine it crashes on start...

Please help me, Im missing my music sooo much! :( 

And if this is posted in the wrong place Im really sorry about that ;)

---

### Post by .... on 2011-09-18
You'll have more luck with these commands: 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
sudo add-apt-repository "deb http://repository.spotify.com/ stable non-free"
sudo apt-get update
sudo apt-get install spotify-client-gnome-support
```

---

### Post by s3l3ct on 2011-09-18
Tried it, and got as far as sudo apt-get update, after which I got:

W: Failed to fetch [http://repository.spotify.com/dists/stable/InRelease](http://repository.spotify.com/dists/stable/InRelease)  Unable to find expected entry 'non-free/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.



And after trying the last line got:

E: Unable to locate package spotify-client-gnome-support


Seriously, is my ubuntu install faulty?

---

### Post by howefield on 2011-09-18
Can you post the output of


```
cat /etc/apt/sources.list
```

---

### Post by s3l3ct on 2011-09-19
The output i get is:


# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) natty universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb [http://repository.spotify.com/](http://repository.spotify.com/) stable non-free
deb-src [http://repository.spotify.com/](http://repository.spotify.com/) stable non-free
deb [http://repository.spotify.com/](http://repository.spotify.com/) stable non-free
deb-src [http://repository.spotify.com/](http://repository.spotify.com/) stable non-free

As I said, any help with this is sooo appreciated, im getting slightly frustrated ;)

This is my third ubuntu computer, and i must say ive never experienced this much difficulty getting everything compliant...

---

### Post by masterdam79 on 2012-03-10
Following [http://www.spotify.com/nl/download/previews/](http://www.spotify.com/nl/download/previews/) I had the same problem but commenting out the previously present deb-src line worked for me!

#deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free

So for Spotify there is (in my case) only one line needed in my /etc/apt/sources.list:

deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

Then
# apt-get update
# apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
# apt-get install spotify-client-qt

I didn't install spotify-client-gnome-support as this had a unresolved dependency.

Ubuntu 11.10
Gnome 3

---

### Post by shantiq on 2012-03-10
ok s3l3ct   i am going to explain this line by line since i sense you are not familiar with terminal



if i am wrong **apologies  **:KS   OPEN TERMINAL


```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
```      and press enter


**then**


**1**   ```
 sudo gedit /etc/apt/sources.list
```

**2**    add those two lines one under the other right at the bottom of the page WHICH IT OPENS on your desktop and **save**

```
deb http://repository.spotify.com/ stable non-free
deb-src http://repository.spotify.com/ stable non-free
``` 


Back to terminal

**3**    ```
sudo apt-get update
```


**4**   finally  ```
sudo apt-get install spotify-client-qt
```

---

