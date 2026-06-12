---
title: "This package is of bad quality - skype and a few others"
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2011-03-25
So i was trying to install skype today from the website because i could not find it in the repositories.

And it says the package is of bad quality .Was trying to install a few other 3rd party packages today and it said the same.

---

### Post by cariboo on 2011-03-25
Skype is in the partner repositories, make sure you have then enabled.

---

### Post by rajeev1204 on 2011-03-25
> **cariboo907 said:**
> Skype is in the partner repositories, make sure you have then enabled.


It is enabled. Do you have it installed?





edit: nvm, i installed it from terminal with dpkg -i

---

### Post by beew on 2011-03-25
Does it work? Can't test it because I only have webcam on my main laptop and Maverick is going to stay there for a long time.

(Natty is installed in  an external and it doesn't work in my main laptop because of Nvidia card problem)

---

### Post by rajeev1204 on 2011-03-25
> **beew said:**
> Does it work? Can't test it because I only have webcam on my main laptop and Maverick is going to stay there for a long time.

(Natty is installed in  an external and it doesn't work in my main laptop because of Nvidia card problem)


Yes, skype works fine but webcam wont work on 64 bit without a hack,that is why i prefer skype from the ubuntu repos for 64 bit, it works fine with webcam .

Now i need to google for the command line way to start skype on 64 bit, some LD_PRELOAD nonsense.

I think they held back skype to get global menu working with it.

---

### Post by mc4man on 2011-03-25
> **rajeev1204 said:**
> So i was trying to install skype today from the website because i could not find it in the repositories.

And it says the package is of bad quality .Was trying to install a few other 3rd party packages today and it said the same.

Software Center (aptdaemon), now includes a lintian check on ,debs. Atm it can refuse to install many .debs that are actually fine due to this
It will fail on any checkinstall created .deb

Using dpkg or gdebi is a workaround till the check is adjusted (or just remove lintian, it is only a recommend and aptdaemon will work without it

bug here
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/712377](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/712377)

---

