---
title: "Mplayer - unmet dependencies"
date: 2008-06-02
forum: Multimedia Software
---

### Post by miickEe on 2008-06-02
Hey

Can't install mplayer/ogle because of "unmet dependencies". Thought with apt-get dependencies were taken care of? Obviously not.

```
miickee@miickee-gutsy:~$ sudo apt-get install mplayer
[sudo] password for miickee:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libamrnb3 but it is not going to be installed
           Depends: libamrwb3 but it is not going to be installed
           Depends: libc6 (>= 2.7) but 2.6.1-1ubuntu10 is to be installed
           Depends: libcaca0 (>= 0.99.beta13b-1) but 0.99.beta11.debian-3 is to be installed
           Depends: libcairo2 (>= 1.6.0) but 1.4.10-1ubuntu4.4 is to be installed
           Depends: libcucul0 (>= 0.99.beta13b-1) but 0.99.beta11.debian-3 is to be installed
           Depends: libfaac0 (>= 1.26) but it is not going to be installed
           Depends: libfribidi0 (>= 0.10.9) but 0.10.7-4build1 is to be installed
           Depends: libgif4 (>= 4.1.6) but it is not going to be installed
           Depends: libjack0 (>= 0.109.2) but 0.103.0-6ubuntu1 is to be installed
           Depends: libncurses5 (>= 5.6+20071006-3) but 5.6+20070716-1ubuntu3 is to be installed
           Depends: libpango1.0-0 (>= 1.20.1) but 1.18.3-0ubuntu1 is to be installed
           Depends: libpulse0 (>= 0.9.8) but it is not going to be installed
           Depends: libx264-57 (>= 1:0.svn20071224) but it is not installable
E: Broken packages
```

I tried installing these dependencies but it would not work. For example
```

miickee@miickee-gutsy:~$ sudo apt-get install libamrnb3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libamrnb3: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
E: Broken packages

```

Tried using sudo aptitude install mplayer, no use at all.

Oh, for those who are about to ask what I'm using it's ubuntu 7.10
```

miickee@miickee-gutsy:~$ uname -a
Linux miickee-gutsy 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

```

A prompt and complete reply would be much appreciated.

Thanks in advance

miickEe

---

### Post by mc4man on 2008-06-02
Your trying to install an mplayer package meant for hardy. check your sources for hardy listings
gksudo gedit /etc/apt/sources.list

---

### Post by Kevbert on 2008-06-02
I see you have some broken packages, repair with
```
sudo apt-get install -f
```
Next, you want to install ogle.  You can install this with Synaptic Package Manager.  You may need to enable backports in your software sources first.  Synaptic will look after all dependences.  The software is quite old (2005).  It may be a better bet to get the Xine media player (totem-xine in Synaptic) and then use [Quickstart]("http://quickstart.phpbb.net/viewtopic.php?f=8&t=11") to install codecs.

---

### Post by Bubba64 on 2008-06-02
Isn't Mplayer in add remove.

---

### Post by miickEe on 2008-06-02
> Your trying to install an mplayer package meant for hardy. check your sources for hardy listings
gksudo gedit /etc/apt/sources.list
Ok, yes I do know what my sources list is. Although exactly what to enter to enable hardy repository listings is somewhat of a mystery to me, please explain.

> I see you have some broken packages, repair with
Code:

sudo apt-get install -f

Next, you want to install ogle. You can install this with Synaptic Package Manager. You may need to enable backports in your software sources first. Synaptic will look after all dependences. The software is quite old (2005). It may be a better bet to get the Xine media player (totem-xine in Synaptic) and then use Quickstart to install codecs.
Yes I have done this.

Now what do I do?

---

### Post by Bubba64 on 2008-06-02
> **miickEe said:**
> Ok, yes I do know what my sources list is. Although exactly what to enter to enable hardy repository listings is somewhat of a mystery to me, please explain.


Yes I have done this.

Now what do I do?

This link will tell you how to add medibuntu from the terminal, also if you go to software sources in system-administration or synaptic you can also add 3rd party urls there and enable other support repositories. Personally I have every one clicked except source code and have never had a problem, but others have very few I suspect. You can also choose a the main repository or choose the one the computer finds to be the fastest for you.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
You can also install Mplayer from add remove in applications.

---

### Post by Kevbert on 2008-06-02
You could run
```
sudo apt-get update
```
and then install ogle or xine player as detailed above.

---

### Post by miickEe on 2008-06-02
I think I've run apt-get update toooooo many times.

---

### Post by miickEe on 2008-06-02
Alright mplayer is installing, thanks guys.

---

### Post by Bubba64 on 2008-06-02
> **miickEe said:**
> I think I've run apt-get update toooooo many times.

Whats the problem?

---

### Post by mc4man on 2008-06-02
> Although exactly what to enter to enable hardy repository listings
I was thinking the opposite, -removing any hardy references
based on this
> miickee@miickee-gutsy:~$ sudo apt-get install mplayer
Yet it's _trying to install_ a hardy package
If your so inclined to force that you may end up with libc6 2.7-1 which will cause you no end of problems in gutsy and will be very hard to undo

---

