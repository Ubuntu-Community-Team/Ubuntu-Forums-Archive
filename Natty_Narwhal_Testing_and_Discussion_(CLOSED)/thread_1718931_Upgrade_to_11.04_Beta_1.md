---
title: "Upgrade to 11.04 Beta 1"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by StephanG on 2011-04-01
I recently installed Kubuntu 11.04 Alpha 3 on my computer, but now that Beta 1 is out, I want to upgrade to it.  But I haven't received any notable updates.
And I tried to add the kubuntu repository with:

```
sudo add-apt-repository ppa:kubuntu-ppa/ppa
```

and

```
sudo add-apt-repository ppa:kubuntu-ppa
```

but with both there's a problem when I try to update.  What repository to I need to upgrade to beta 1?

---

### Post by mörgæs on 2011-04-01
Just use Update Manager as normal, and you will get to Beta.

---

### Post by StephanG on 2011-04-01
The update manager is telling me that there are no new updates.  Even with backports, universe, etc. enabled.

But it doesn't matter any more, I just installed the beta onto the alpha 3 partition.  My home directory is on another partition, so I haven't lost any settings or data.  I just have to reinstall the few apps that I was using.

Thanks anyways.

---

### Post by mörgæs on 2011-04-01
If you don't see anything new in Update Manager, either you are already on Beta or the mirror is delayed. In the latter case you can just wait a day and repeat.

---

### Post by tribalboy on 2011-04-03
Hi Guys,

 Still cant see an update for Ubuntu 11.04 beta on my Alpha 3 install. Is this a bug...? I have also tried to do this from the command line

```
sudo do-release-upgrade
```

it says No new release found

Also checked the release version to see if it had already upgraded it to beta 
```
lsb_release -a
```

Description : Ubuntu Natty (development branch)
Release : 11.04
Codename : natty

But it doesnt seem to distinguish between Alpha & Beta. Any ideas anyone.

Many thanks

---

### Post by Dutch70 on 2011-04-03
> **tribalboy said:**
> Hi Guys,

 Still cant see an update for Ubuntu 11.04 beta on my Alpha 3 install. Is this a bug...? I have also tried to do this from the command line

```
sudo do-release-upgrade
```

it says No new release found

Also checked the release version to see if it had already upgraded it to beta 
```
lsb_release -a
```

Description : Ubuntu Natty (development branch)
Release : 11.04
Codename : natty

But it doesnt seem to distinguish between Alpha & Beta. Any ideas anyone.

Many thanks

As mentioned above, if you don't see any upgrades, then you already have the beta version by now. 

Also, if you have questions about Natty, please start your own thread in the Natty testing forum.

---

### Post by ikt on 2011-04-03
> **tribalboy said:**
> But it doesnt seem to distinguish between Alpha & Beta. Any ideas anyone.

Change your software sources to the main server and update/upgrade using that.

If the main server has no new updates, you are running the latest software.

---

### Post by Dutch70 on 2011-04-03
I didn't think you could use anything but the main server. I haven't been able to on mine anyway.

---

### Post by ikt on 2011-04-03
> **Dutch70 said:**
> I didn't think you could use anything but the main server. I haven't been able to on mine anyway.

Why wouldn't you?

Why aren't you able to?

My ISP is internode and I use them for updates for 11.04.(as it is not counted against my usage and comes down at full speed)

---

### Post by Dutch70 on 2011-04-03
> **ikt said:**
> Why wouldn't you?

Why aren't you able to?

My ISP is internode and I use them for updates for 11.04.(as it is not counted against my usage and comes down at full speed)

I don't know why. I have tried with both Ubuntu & Kubuntu development releases and the only server that it lets me choose is the main server. I'm new to running dev releases, so I thought that it was the only place you could get downloads until they are officially released.

---

### Post by drazelian on 2011-04-05
to see the 11.04 upgrade option
press alt +f2 and type
```
update-manager -d
```

---

