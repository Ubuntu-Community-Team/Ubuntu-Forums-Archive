---
title: "Dialup, which is the best solution for the poor?"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by joewski on 2009-07-31
As a strong supporter of Ubuntu, I have to say the dialup support is hopeless. I tested 12 pci modems and Ubuntu was only able to recognise one, and of that I couldn't dial out without using the KDE version of GUI configuration tool.

What the worst part of it is is the realisation that a local club "Melbourne PC users" has over 20% of it members on dialup. I was amazed when I was told this figure. I have been on cable for years and though this was a thing of the past. Also what is interesting these people tend to be running the older operating systems. They also were more willing to give Ubuntu a try.

If you read the documentation, wikis, forums etc, each article assumes that you have an cable or ADSL internet connection, so you can install dialup. While I could sort this out myself my problem is more broad than myself. I need to do it on a larger scale.

This is insane. How can Ubuntu expect people with dialup to install a modem if no connection exists. What are we assuming that there previous OS is going to act as the go between? Dumb I recon. I think the required software needs to be on the Ubuntu disk by default.

I want to fix the dialup problem, but Im no expert on dialup or distros. I need the communities help, so I can help others. I will do what it takes but I would be grateful if people could point me in the right direction and help put something together.

Remember, The objective is connect a dialup modem user, without a network internet connection. Is it possible? Remember, the assumption is that they have installed Ubuntu and are asking the question now what? What tools do I need to give them to make that final connection to the world?

What is the best solution to solve the dialup problem? I really want to support these people and need to solve it quickly. I would prefer they solve it themselves, but they can't unless they have an internet connection. I don't want to use windows to connect because that just looks very bad. (Here I am telling everyone Ubuntu is great and I can't even detect a PCI modem without downloading tools)

Should I 

1. Create a custom distribution called "dialbuntu" with all the driver on it ready to go? (In which case how do I go about this?)

2. Use some distro better than Ubuntu more suited to dial-up? 

3. Is there a way to install a modem using the tools already found in Ubuntu and not depend on a network connection? (What are the instructions?)

4. Would it be better to create a custom how-to disk with all the drivers, instructions etc? (Can anybody point me to some good resources for this task. I am already aware of our local docs's but there may be others.)

5. Should Mark Shuttleworth get involved? Does he realise how important dial-up is to so many people?

Thanks in advance to all helping solve bug number 1.

---

### Post by some1_genius on 2009-09-18
Hi bro.
Just switch to puppy its the some kind of lonely distro that supports pci dialup modems well, I didn't tried it my self and don't know much about it.
Its very small and you can download it from softpedia.
By the way, I don't think that any body (I mean distro makers) cares about pci dialup modems exept for Puppy, go for it and I will be gratefull if you told me about what will you experience with it.
Good luck

---

### Post by sir_cheats_a_lot on 2009-10-14
Dialbuntu.. that's hilarious...what's not is the amount of work involved with building a new distro.  i feel your pain though, i'm stuck on dialup myself, and i don't have any other internet options either.  if you feel up to the task of doing it, i'd say go for it.  that ONE modem that did get picked up was probably a REAL modem, and not some cheap softmodem.  If you want to go the remastery route i'm sure many here would be willing to lend a hand, but the biggest obsticle will be getting all the dependancies needed and then transferring them all to your test PC.
  From personal experience.. kppp blows something fierce, that's why i don't like using Kubuntu instead of regular Ubuntu.  always had to edit some config file just to get it so i wouldn't have to constantly run it as root or get it to connect at all.  if you can get somewhere and snatch the sl-daemon(smart link) package out of the repository, you could probably get half of the other pci modems you have working.  i assume you already have a provider for your dialup connection....right?  naturally the key tool you need is to punch in lspci at the terminal, and then run down the info about each modem's chipsets;this is key in determining if you need the smart-link driver, or lucent/rockwell(some of which work with the sl driver).  Dial-up support is horribly lacking it's true.  there is a good deal many threads in the forum that explain different methodes of identifying and setting up different dial-up modems.(i.e. scan modem script).  sadly the last i knew these missing drivers/packages couldn't be shipped with ubuntu under their license.  If that weren't the case i'm sure everything would be included...i think.

---

