---
title: "Wireless drivers in Ubuntu 10.04"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by phadaphado on 2012-12-19
Hello all,

I'm pretty inexperienced when it comes to linux, so please bare with me.  I recently purchased a new laptop (Lenovo ThinkPad T530) and I wanted to install the same version of Ubuntu that I am running on my old laptop (10.04).  The installation went fine, but, unsurprisingly, the wireless card was not recognized.  I have been trying to find the appropriate drivers online using my old computer and transferring them via flash drive to the new computer, but so far I have been unsuccessful.  

I downloaded "iwlwifi-2000-ucode-18.168.6.1.tgz" from the intel website, which when extracted yields "iwlwifi-2000-6.ucode" but I don't know how to update to this driver or if that is even the appropriate thing to do. 

I can try to give you a little more info about my computer, but since I don't know exactly what is going to be important, and since I can't copy and paste, there may be come important details missing:

iwconfig yields "no wireless extensions"
lsb_release -d yields "Ubuntu 10.04 LTS"
uname -mr yields "2.6.32-21-generic i686"
lspci -nn yields "...03:00.0 Network controller [0280]: Intel Corporation Device [8086:0891] (rev c4)
sudo lshw -C network shows that both of my networks are "UNCLAIMED"

Let me know if I can provide any more info.  I'm happy to type it all out if I know that it is going to be useful.

Thanks for any advice that you can provide.

phadaphado

---

### Post by mörgæs on 2012-12-19
An old operative system on new hardware is seldom a good idea, especially because of hardware recognition. 

Before proceeding, have you thought of installing 12.10?

---

### Post by phadaphado on 2012-12-19
Yes, I have considered upgrading, but I really hope that I don't have to, if at all possible.

---

### Post by chili555 on 2012-12-19
> I downloaded "iwlwifi-2000-ucode-18.168.6.1.tgz" from the intel website, which when extracted yields "iwlwifi-2000-6.ucode" but I don't know how to update to this driver or if that is even the appropriate thing to do.It's not. Your device ID 8086:0891, a pretty new device, is not covered by iwlagn, the driver in 10.04. You can throw all the firmware files you want at it and it still won't work.

Now, if you are in love with old things and drive a 1958 Ford and *must* get 10.04 working, we can, with a few hard days of teeth gnashing. Or you could, as my esteemed colleague mörgæs suggests, install 12.10 in 20 minutes and your wireless will work perfectly. We don't know about your ethernet, since we don't see the details, but assume the same. My Lenovo T410's ethernet and Intel wireless work perfectly in 12.10 with no extra steps.

Whichever you decide, we will be happy to help.

---

### Post by phadaphado on 2012-12-19
Hmmm...

Well my reasons for sticking with 10.04 are mainly that I have set up 5 computers in my computer lab at my university with it and it was hard enough trying to get my students to switch to an unfamiliar (and sometime less friendly) operating system, that I felt that upgrading the OS every 6 months would be too frustrating for them.  So, I have kept my laptop the same as those computers so that when I get frantic e-mails, I can more easily walk them through their problems.  That and I like old things (in particular, I'm not a fan of the gnome 3 (?), iphone like, icon-based interface).

But, I would like to keep an open mind about this.  Would it be too much to ask of you, "what would be the first step for either of these plans?"  How would I upgrade to 12 without an internet connection (seems straight forward with one, but without I feel like I have some of the same issues), and if I was to try to stick with 10.04 what would be the first thing that you would try.  I hate to think that I am backing down from a challenge, but that's just me being stubborn.  I did have a similar issue when I set up the lab computers (almost a year an a half ago), but it was somehow easier to find the network card drivers online and they had a pretty helpful readme file.

I hope that I am not being too much of a pain in the butt.

Thanks for the help, I really appreciate it.

Matty

---

### Post by Pjotr123 on 2012-12-19
I advise to try 12.04.1 LTS first, as that's an LTS version. If you can't get used to the new Unity desktop environment which is the default nowadays, you might be pleasantly surprised by the elegant simplicity of Xubuntu:
[https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)

A clean upgrade is always best, for every operating system under the sun, on this our weary planet. Which can be done easily like this: [https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

Good luck! :)

---

### Post by GordThompson on 2012-12-19
> **phadaphado said:**
> Well my reasons for sticking with 10.04 are mainly that I have set up 5 computers in my computer lab at my university with it and it was hard enough trying to get my students to switch to an unfamiliar (and sometime less friendly) operating system, that I felt that upgrading the OS every 6 months would be too frustrating for them.  So, I have kept my laptop the same as those computers so that when I get frantic e-mails, I can more easily walk them through their problems.  That and I like old things (in particular, I'm not a fan of the gnome 3 (?), iphone like, icon-based interface).
My suggestions:

- Download the ISOs for Ubuntu 12.04 LTS and Xubuntu 12.04 LTS and burn them to CD or DVD, as required.

- Boot each of them using the "Try Ubuntu" option (aka "Live CD").

- When you've decided which one you like better, install that one.

- In 12.04, install VirtualBox, then create a virtual machine and install 10.04 on it. Chances are pretty good that 10.04 will recognize the virtual network adapter and use it. (If VirtualBox didn't work for whatever reason you could always try VMware Player instead.)

Then, when you get a "frantic e-mail" just fire up the 10.04 VM and use that for the support session.

---

### Post by ahallubuntu on 2012-12-19
> **phadaphado said:**
> Well my reasons for sticking with 10.04 are mainly that I have set up 5 computers in my computer lab at my university with it and it was hard enough trying to get my students to switch to an unfamiliar (and sometime less friendly) operating system, that I felt that upgrading the OS every 6 months would be too frustrating for them.

Ubuntu 10.04 LTS (desktop version, the one you are probably using) is supported only until April 30, 2013.  Then you'll either have to upgrade anyway or let your students use an unsupported operating system.

A lot of people don't like Unity (the "iPhone interface" in the newer versions of Ubuntu).  You can easily install Gnome 3 aka "Gnome Shell" which is close to Gnome 2 that you are used to in Ubuntu 10.04 LTS but not exactly the same.  Another options is to use "Mate," a fork of Gnome 2, in Ubuntu 12.04 LTS.  (Or use Linux Mint, which is based on Ubuntu and uses Mate as a standard interface.)  There are disadvantages to Mate, but people use it because they dislike certain things about Gnome 3.  (Long story - google for more info if you're curious about the pros and cons). 

If you want to save yourself time making identical workstations, you can always make one good image of Ubuntu on one workstation, tuned with all the apps and updates you want, etc.  Then...clone that image to the other hard drives on the other computers, so they'll all be exactly the same, instead of re-installing from scratch over and over again.  There's a good chance it will work almost perfectly without changing much of anything (perhaps wireless drivers, if you are using laptops).  The only thing you really MUST do is change the hostname afterward so each computer on the network has a unique name.  (Also, blow away the file "/etc/udev/rules.d/70-persistent-net.rules" on each new installation so eth0 and wlan0 are the default network devices.)

Unlike Windows, Linux is very adaptable to moving the same OS install from one computer to another, even if the hardware is different.  Often you can boot the same installation on very different hardware without changing a thing.

---

### Post by phadaphado on 2012-12-22
Hello everyone,

Thank you for all of your replies.  Sorry that I am a little late getting back, but I have been traveling across coasts for the holidays.

I did have a chance to install Xubuntu 12.04 overtop of my previously installed Ubuntu 10.04.  That worked fairly well.  I don't think I am totally sold on it yet, but I want to play around with it more before passing judgment.  Some things are quite different than I am used to, so I might have some really basic questions about Xubuntu, if you guys are willing to field such questions.  I might also try the VirtualBox suggestion and/or the Gnome 3 suggestion in the next couple/few days.

Thanks again for all of your thoughtful suggestions, and have a happy holiday season.

phadaphado

---

### Post by phadaphado on 2012-12-26
Latest Update:

I did decide that Xubuntu wasn't for me, so I installed Ubuntu 12.04 and then installed Gnome 3 and have been running in classic mode.  So far it seems to work great.  Are there any down sides to running in classic mode?

I hope everyone had a good xmas.

phadaphado

---

