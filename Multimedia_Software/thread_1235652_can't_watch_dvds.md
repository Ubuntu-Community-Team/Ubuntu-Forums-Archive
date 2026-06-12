---
title: "can't watch dvds"
date: 2009-08-09
forum: Multimedia Software
---

### Post by methodtwo on 2009-08-09
Hi there
I'm new to ubuntu.I've just installed edgy-eft because both my gentoo boxes were hacked and edgy was the only copy i had around.
How do i get to a stage where i can watch DVDs in edgy-eft?
I've added the medibuntu repo.I've installed win32codecs and libdvdcss2 but still totem won't play DVDs.Also when i do:
```
$sudo apt-get install vlc
```
i get an error saying that vlc can't be found.
would updating the distro entirely solve the problem?.Oh and yes i did do:
```
$sudo apt-get update
```
before trying to install vlc
Thank you very much for any help

---

### Post by hansdown on 2009-08-09
Hi methodtwo.

I think the repositories for Edgy are closed.

Are you able to download a newer version?

[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by Narada on 2009-08-09
Did you configure your apt sources to use all repositories? VLC is in the multiverse repo (community maintained), which is not enabled by default.
```
sudo nano /etc/apt/sources.list
```
Example with multiverse enabled:```
deb http://us.archive.ubuntu.com/ubuntu/ edgy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates multiverse

```
More info: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If hansdown is correct about the repos then you will need to upgrade. Edgy is no longer supported.

---

### Post by wojox on 2009-08-09
> **hansdown said:**
> Hi methodtwo.

I think the repositories for Edgy are closed.

Are you able to download a newer version?

[http://www.ubuntu.com/](http://www.ubuntu.com/)

+1 repo's closed.

---

