---
title: "Installing Medibuntu"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by Incarnadine on 2007-06-11
I found out about this Medibuntu respiratory and was hoping someone could give me a step by step guide on how to install this thing. I found the official documentation on it, but still couldn't figure out how to add Medibuntu to my respiratory. I'm too new to all this. They tell me some sudo commands, but what is this sudo? I don't even know where to start with it. If anyone could point me out to the right direction that would be great. Thanks.

---

### Post by LaRoza on 2007-06-11
when you have a sudo command, it means type it in the terminal.

for example, 
```

sudo aptitude install kubuntu-desktop

```
would install all the Kubuntu aspects of Ubuntu on an existing Ubuntu OS.

I imagine the command you were given was similar. Type it in and see if it works, or you can post it here and someone or myself will explain what it means.

-edit 

sudo means to run the command as root, you will be asked for the password, type it in. Don't worry when you can't see what you are typing, it doesn't show up on the screen.

---

### Post by taurus on 2007-06-11
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and add these two lines to the end of it.

```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
Save the changes and close down gedit window.  Then run

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by scott_g on 2007-06-11
Or you could do it the user friendly way;

System>Administration>Software Sources (root password needed).
Then: 3rd party software, click add, enter :

```

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free

``` 
into the box, then click ok, then repeat with:
```

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free

```
Click close, then the reload button that appears.

You could then go into the update manager (System>Adminsitration>Update Manager) to see if there is anything new.  Other than that, you can search for new software using the Synaptic Package Manager, or the Add Remove software (may need to include all available software).

Hope if helps,
Scott

---

### Post by Incarnadine on 2007-06-11
Perfect. Thanks guys:p

---

### Post by stchman on 2007-06-11
> **Incarnadine said:**
> I found out about this Medibuntu respiratory and was hoping someone could give me a step by step guide on how to install this thing. I found the official documentation on it, but still couldn't figure out how to add Medibuntu to my respiratory. I'm too new to all this. They tell me some sudo commands, but what is this sudo? I don't even know where to start with it. If anyone could point me out to the right direction that would be great. Thanks.

I have a procedure to install Medibuntu:

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

I use Medibuntu to enable the CSS decryption for DVD playback but you will then have access to the repositories of Medibuntu.

---

### Post by Bablefish on 2007-06-11
If that still don't works for you search for the Medibuntu site and look for the straight terminal install. I found it a hell of a lot easier.

---

### Post by Incarnadine on 2007-06-11
This is what I get when I use  sudo apt-get install libdvdcss2

Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

What the heck does this mean? The package isn't available anymore? I'm clueless:(

---

### Post by taurus on 2007-06-11
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Incarnadine on 2007-06-11
Sure thing.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

Am I missing a respiratory?

---

