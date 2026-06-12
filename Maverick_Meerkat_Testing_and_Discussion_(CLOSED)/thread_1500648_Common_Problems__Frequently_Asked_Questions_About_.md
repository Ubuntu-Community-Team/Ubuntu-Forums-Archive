---
title: "Common Problems / Frequently Asked Questions About Testing"
date: 2010-06-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-06-03
Here are answers to some commonly asked questions and solutions to common problems when testing pre-release Ubuntu versions. It will be updated during the testing period as necessary. Feel free to post suggestions for things that you think should be included (I won't promise to include them all, since making the document unnecessarily long typically discourages people from reading). 


**I already have a testing installation. Do I have to reinstall the latest alpha / beta / RC when it comes out?**

If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the alpha / beta / RC, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix.

The milestone releases (alphas, betas and the RC) are slightly stabilized snapshots of the package archive at pre-decided dates, so they reflect the latest state of Maverick on those dates. If you're up to date, you already have the latest packages. If you have to reinstall, and have an old disc image, you may want to [use rsync]("https://wiki.ubuntu.com/RsyncCdImage") to avoid having to download the whole image.

**If I install the alpha / beta / RC now, do I need to reinstall the final version when it's released? **

You don't have to (Update Manager will let you upgrade to the final version), but you may want to, if one or more of the below apply:

[list]
[*] You have tweaked your testing installation to a point where you're not aware of its exact components and configuration 


[*] You have replaced essential components of your installation with versions from external repositories / PPAs


[*] You have used package installation scripts or similar tools which are not trusted by the Ubuntu development community


[*] You have applied hacks / workarounds for testing purposes for good reason (prompted during structured testing, bug triage etc.), which may cause problems during daily usage of a stable installation


[*] You're affected by potential corner cases that may require a reinstall to fix (which will be documented in the release notes)
[/list]

**Update Manager offers a "Partial Upgrade". What should I do?**

[Read this]("http://ubuntuforums.org/showthread.php?t=1343434").

**When / at what time will the alpha / beta / RC be released?**

Take a look at [the release schedule]("https://wiki.ubuntu.com/MaverickReleaseSchedule"). There's no specific time of the day for releases; just wait for the official release announcement, which will be mirrored immediately in the forum with a sticky thread as well.
 
**I'm trying to report a bug, but I'm redirected to [this page]("http://help.ubuntu.com/community/ReportingBugs"). What's going on?**

That's intentional; you'll understand what's going on once you read that page :)

**I'm trying to report a bug, but I don't know which package it belongs to. What should I do?**

Take a look at the [Bugs/FindRightPackage page on the wiki]("wiki.ubuntu.com/Bugs/FindRightPackage"), and try invoking Apport's (currently rather primitive) symptom-based reporting mode by issuing ```
ubuntu-bug
``` with no arguments. If those don't help, feel free to start a thread, or join the #ubuntu-bugs channel on [the Freenode IRC network]("help.ubuntu.com/community/InternetRelayChat") to ask for assistance.

**My testing installation is badly broken. Is there a way to roll back to the stable release, or a relatively stable point in the development branch?**

No. You'll have to fix your installation or do a fresh install.

**I haven't been getting updates for a while. Is it that there's nothing new in Maverick, or is there a problem with the servers?**

The archive mirror you're using is probably lagging behind. You can see the status of the mirrors at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors). Also note that there will be relatively few updates during the freeze periods leading to alpha, beta and RC releases.

**I downloaded the daily CD image, but it's oversized and I can't burn it on a CD.**

The daily images get built automatically, and due to the rapid and asynchronous nature of uploads to Maverick, no effort can be made to make them fit on a CD on a daily basis; such an effort is only made for the milestones. Note that you can still use oversized CD images for testing in a virtual machine.

**Is testing Maverick in a virtual machine useful?**

For testing kernels, X, and anything that interacts directly or at a low level with hardware, it's hard to produce useful bug reports. If filing bug reports from virtual machine installs, don't forget that they will be reports about Ubuntu failing to work on that particular virtual machine, and don't forget to indicate that you're testing on a virtual machine in your bug report. While virtual machines are a valid use case, bugs from real hardware are much more useful. If, however, you're only looking to test high-level functionality such as userspace applications, user interfaces, documentation, translations and so on, virtual machines are mostly fine.

---

### Post by ranch hand on 2010-06-03
@23meg
You are a gem.

Now if folks will learn to read.

---

### Post by gekken on 2010-06-03
NO! On behalf of all people that post in/on forums everywhere, I hereby reserve the right to not read a darned thing and to spew forth my ill-formed opinion in any way that may annoy others. 

That being said -  LONG LIVE MASTICATING MANATEE!

---

### Post by dext on 2010-06-06
> **ranch hand said:**
> @23meg
You are a gem.

**Now if folks will learn to read**. or google for that matter

---

### Post by sinurge on 2010-08-16
> **gekken said:**
> NO! On behalf of all people that post in/on forums everywhere, I hereby reserve the right to not read a darned thing and to spew forth my ill-formed opinion in any way that may annoy others. 

That being said -  LONG LIVE MASTICATING MANATEE!
I will not adhere to this sticky lolz :)..... or Google....make more mistakes learn more...

---

### Post by gibbylinks on 2010-09-04
> **ranch hand said:**
> @23meg
You are a gem.

Now if folks will learn to read.

I have two observations on that one. If folks learned to read then

[LIST=1]
[*]What would some people have to moan about ?
[*]How would people fill their day with all their new found spare time ?
[/LIST]
;)

---

### Post by techunit on 2010-09-04
I have a solution to a problem with the current Version of Virutalbox. If you tryed to install Ubuntu 10.10 beta in Virtualbox then you probably ran into some trouble installing the guest additions. This is because Ubuntu 10.10 has an unsupported version of Xorg. You need to revert to the lucid version to alleviate the problem.

Here is how I fixed the problem.

Ok I know how to fix the problem... What you need to do is install the  old xorg drivers. To do this you will have to open the sources list.

```
sudo gedit /etc/apt/sources.list
```then put pound symbols infront of the maverick main restricted lines (4 of them)

Ok then open the software sources app and add the lucid main restricted
```
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
```Ok now reload the packages and make sure that everything is working with apt. 

Now go to the synaptic package manager and go to "status" click  installed and enter "xorg" into the quick search option then go to  xorg-server-core (something like that (second entery after xorg) and  mark it for removal (now everything with xorg in its name should be set  to be removed) apply and reboot.

Now when you reboot you will see a command line interface. Log-in and type

```
sudo apt-get install xorg
```now the old xorg drivers from  lucid are running! next install the Virtualbox Guest Editions (you may  see and error goblygook message) if you see the screen crazy error then  wait 3 minutes and hit enter on the keyboard. Then click close on the vm  and check send shutdown signal and hit enter. after that you should  have access to changing the settings and screen freely!

---

### Post by chilloutmo on 2010-09-08
Seriously you got to be kidding. When will ubuntu stop wasting release cycles make battery life finally its priority. Netbook editions, unity, and so on, only to adapt everything for small screens and to have hip icons. But that somebody would think about adapting ubuntu to fit the main buying argument of netbooks (portability i.e. battery life) that is too much to ask. I mean if you are lucky, an optimized ubuntu gets at about 66% of the battery life of a W7 system. This is a total joke. I mean seriously who buys a 10 hour netbook just to have it slashed down to 5 ? even ubuntu (which I love to use on my desktop) is not worth that. it's just sad to see pages and pages of discussions about the look of this logo or the arrangement of that menu. But today at least 3/4 of all sold computers are portable ones, and I am sorry to say it but it is just pathetic to think that you can compete with other OS if you drain battery life like a vampire. And I know there is powertop and some other tools, but there is still no way that ubuntu can keep up with the power management of MS and Apple. I hope it will be a priority for the next release since I believe that ubuntu cannot seriously want to attract netbook and notebook users with this poor battery life.

---

### Post by MarkieB on 2010-09-09
no longer participating in ubuntuforums.org

---

### Post by k7rata121 on 2010-10-09
now i'm using 10.10 the RC and i'm installing the updates everyday..
how i know that i've the final release now "from the updates"?

---

### Post by ktp on 2010-10-09
if you keep the system updated, then you will have the latest version.  there is also /etc/issue file which tells the version.

---

### Post by sendblink23 on 2010-10-10
> **ktp said:**
> if you keep the system updated, then you will have the latest version.  there is also /etc/issue file which tells the version.

So what words are we looking for in there?

Mine has currently
```
Ubuntu 10.10 \n \l
```
=P

```
sendblink23@sendblink23-MS-7577:~$ uname -a
Linux sendblink23-MS-7577 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
sendblink23@sendblink23-MS-7577:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick
sendblink23@sendblink23-MS-7577:~$ 

```

---

