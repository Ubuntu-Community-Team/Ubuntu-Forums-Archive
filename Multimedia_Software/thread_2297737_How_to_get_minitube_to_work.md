---
title: "How to get minitube to work"
date: 2015-10-06
forum: Multimedia Software
---

### Post by rdh61 on 2015-10-06
Hi,

I installed minitube from the respositories but it does not work. It won't play videos, I just get a black screen. So I found this:

[http://askubuntu.com/questions/672501/why-is-minitube-not-working-on-ubuntu-15-04](http://askubuntu.com/questions/672501/why-is-minitube-not-working-on-ubuntu-15-04)

As advised I obtained my API key, and first tried Method 2. This produced no change in behaviour.

I next tried Method 1. This proceeded until I got a message saying "Now heading over to Google" on which a browser opened with my Google projects page open. No instructions on what I am meant to do. No further progress on terminal, even after 20 minute wait.

Lastly, I tried Method 3 and got a qt error. I saw then that minitube requires qt5, while I had qt4. I installed qt5 from the repos, tried again, same result. I notice I still have qt4 installed as well as qt5. Could that be a problem? How can I remove qt4?

Has anybody here successfully got minitube working on 14.04? If so, what method did you use? Any ideas about what might be my problem?

Many thanks.

---

### Post by warp07 on 2015-11-05
Try Minitube 2.4

---

### Post by rdh61 on 2015-11-05
Thanks for the interest. I've tried 2.4 and 2.5. No luck. The problem has gone through various incarnations, none of them good. The current state of play is described [here]("http://flavio.tordini.org/forums/topic/minitube-2-5-does-not-open-on-lubuntu-14-04-lts-32-bit").

---

### Post by v3.xx on 2015-11-05
My setup is a bit different from yours, I'm running 16.04/64bit.  So here's what happen.

I loaded minitube from the software center and it was broke out of the box.

So I went to the minitube site and loaded the same version and it worked out of the box.

If you want to try this, first remove the current install and then download from the site.

[http://flavio.tordini.org/minitube](http://flavio.tordini.org/minitube)

I used gdebi to install it.  This can be installed with the terminal command:

```
sudo apt-get install gdebi
```

---

### Post by andrew.46 on 2015-11-05
Newer versions of SMTube work well enough, perhaps try this?

---

### Post by rdh61 on 2015-11-06
Thanks, I had tried that and it didn't work. I am aware that minitube works with other versions of Ubuntu. But has anybody got it working with 14.04?

> **v3.xx said:**
> My setup is a bit different from yours, I'm running 16.04/64bit.  So here's what happen.

I loaded minitube from the software center and it was broke out of the box.

So I went to the minitube site and loaded the same version and it worked out of the box.

If you want to try this, first remove the current install and then download from the site.

[http://flavio.tordini.org/minitube](http://flavio.tordini.org/minitube)

I used gdebi to install it.  This can be installed with the terminal command:

```
sudo apt-get install gdebi
```

---

### Post by rdh61 on 2015-11-06
Thanks, I'll look into it.

> **andrew.46 said:**
> Newer versions of SMTube work well enough, perhaps try this?

---

### Post by mc4man on 2015-11-08
> **rdh61 said:**
> Thanks, I had tried that and it didn't work. I am aware that minitube works with other versions of Ubuntu. But has anybody got it working with 14.04?

installs & works ok here on 14.04, see screen. Just use software-center or gdebi to install it & whatever dep packages it needs.

---

### Post by rdh61 on 2015-11-09
Four weeks ago, as per my original message, the version installed with Synaptic did not work. But now it does. They must have upgraded it. Thanks for stimulating me to try again. I'm marking the thread solved.

> **mc4man said:**
> installs & works ok here on 14.04, see screen. Just use software-center or gdebi to install it & whatever dep packages it needs.

---

