---
title: "Help with PPA's"
date: 2010-06-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by KdotJ on 2010-06-11
Hello all,
Could someone please give me a little info regarding PPA's. When I add them (I did for Gnome-Shell) and then used Update-Manager, I got offered a Partial Upgrade. I have read the sticky which talks about Partial Upgrades, so I didn't continue. How can I update without this happening? Can I update just the packages from the PPA's?

Thanks for any help

---

### Post by wilee-nilee on 2010-06-11
It would be helpful if you give us the ppa you are adding, if there are anymore besides the one mentioned.

---

### Post by taavikko on 2010-06-11
Also cli version of safe-upgrade output would help determing the course of action...

---

### Post by KdotJ on 2010-06-11
Sorry for being brief, the tow PPA's I'm attempting are:

**The Gnome-shell PPA**
By typing the following in the terminal:

```
sudo add-apt-repository ppa:ricotz/testing
```

Which I obtained form [HERE]("http://ubuntu-tweak.com/source/gnome-shell-testing/")


**Unity**
By typing the following in the terminal:

```
ppa:canonical-dx-team/une
```

Which I obtain from [HERE]("https://edge.launchpad.net/~canonical-dx-team/+archive/une")

---

### Post by ranch hand on 2010-06-11
```

sudo apt-get update

```
```

sudo apt-get upgrade

```
Or use "safe-upgrade" with aptitude.

Or use synaptic.

Anything but Update Mangler.

---

### Post by wilee-nilee on 2010-06-11
What I have noticed with maverick and the update manager is that if a update/upgrade is a 3rd part addition that it wont just let you run the upgrade from the gui, even without a partial upgrade option in some circumstances.

Probably the safe-upgrade as suggested will be the best, way of approaching this. 

Personally I am running maverick from a installation on a thumb so I have nothing to lose, and just run a dist-upgrade for the rush of the risk, but thats just me and shouldn't be done with maverick being installed as a dual boot. This is the testing part a new OS so you have to be prepared to be able to fix your system, no matter what and have everything backed up.

I see some people who are new to Ubuntu trying out these, test OS, and probably not really understanding the risks and being set up for failure. Not saying your one of these, but always be prepared is the mantra I roll with. ;)

For me always being prepared is a full backup on a external Hd of important media, rather then a separate home, and the install media at hand in case needed. Along with several partitioning based cd's partmagic, partition wizard, gparted, and several supergrub releases. Since I use MS I have a couple of Hirens discs, which have multiple programs for a whole bunch of different applications, not necessarily for fixing MS but the HD.

---

### Post by KdotJ on 2010-06-11
Thanks for the replies. As for messing things up, I have a backup and try a lot of stuff in a VM, however I cannot obviously test stuff like gnome-shell in a VM as 3D acceleration is not supported. 

So how do I go about safe-upgrade ?

Literally just type that in the terminal? aptitude prefix?

---

### Post by ranch hand on 2010-06-11
There is not much difference between "sudo aptitude safe-upgrade" and "sudo apt-get upgrade".

Either will work, it is really a matter of personal choice as to use apt-get or aptitude.

Both camps are quite fervent.  I use apt-get so I will say nothing about aptitude.

They are both great tools.  Which one fits your hand better is up to you.

Do not forget synaptic which is mighty handy for getting information on packages that are held back.  Some you are safe to do and some are an unmitigated wreck.  It is nice to know which is which.

---

### Post by KdotJ on 2010-06-11
Thank you, I must say I need to get to know synaptic. It looks mighty helpful, just a bit complex at first glance

---

### Post by ranch hand on 2010-06-11
In the lower left there are some buttons (sections, status, etc).  Explore them, they are handy.

For running an update just hit reload (upper left).  If you have the "status" button pushed it will soe you your proposed upgrades.

It is a little safer to do the upgrades in apt-get.  Then go to synaptic and check the ones held by apt.

Apt will hold because something extra is being installed.  Synaptic will tell you this.  Those are usually safe to do.

Apt will also hold because something is going to be removed.  These are dicey and if you wait it will probably clear up.  May take a week or two (or a couple hours).  As they say around here "don't gitcher panties in a bunch."  Just wait, watch this forum and see what happens.

---

### Post by KdotJ on 2010-06-11
Ok so now I have another issue, 
Now when I try to add the PPA's in the terminal, it does some stuff and then ends up stopping on:

```

gpg: requesting key 7AE26941 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```This happens with both of the PPA's that I stated a few posts back. 
Also, when I run apt-get update, it returns with an error about no public key:

```

W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AA2BB78B7AE26941

```Any ideas? Do I need a public key? 



(NOTE: Please notify me if I should blank out the keys from this post)

---

### Post by xebian on 2010-06-11
> **KdotJ said:**
> Thanks for the replies. As for messing things up, I have a backup and try a lot of stuff in a VM, however I cannot obviously test stuff like gnome-shell in a VM as 3D acceleration is not supported. 

So how do I go about safe-upgrade ?

Literally just type that in the terminal? aptitude prefix?

VirtualBox supports 3d accel.

---

### Post by KdotJ on 2010-06-11
> **xebian said:**
> VirtualBox supports 3d accel.

So i've been told. However even when I have followed the instructions to do enable it (from the VB instructions), I still cannot enable desktop effects, nor can I run Gnome-shell

---

