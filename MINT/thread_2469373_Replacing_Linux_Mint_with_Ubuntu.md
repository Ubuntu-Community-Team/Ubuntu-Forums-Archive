---
title: "Replacing Linux Mint with Ubuntu"
date: 2021-11-26
forum: MINT
---

### Post by gsparky2004 on 2021-11-26
Afternoon, all! I'm currently using Linux Mint, but considering switching (back) to Ubuntu. My current installation is the OS on one drive, and /home on a different drive. 

Quick question: What folders / files would you recommend I remove from my /home directory beforehand because they are Mint-specific? For example, I'm assuming anything related to graphics settings would be specific to Ubuntu, and anything Mint did would probably screw things up. Should I just "nuke from orbit" all configuration files that appear to be used by the OS? The files I'd like to keep are all of my Thunderbird e-mail files, my Firefox profile, my Rhythmbox files, and a few others. The rest I'm happy to either remove or rebuild later.

Thanks!

---

### Post by oldfred on 2021-11-26
I would make sure I had a good backup of everything, including list of installed apps (may be different in Ubuntu), /home, some settings in /etc and anything else like if you installed any server applications in /. The just install using same /home. It should overwrite any duplicate settings and not use some others. The only disadvantage is you may leave some cruft from old install. 

I prefer to have a separate data partition for Documents, Downloads, Music, etc folders and also include some normally hidden folders like the Firefox & Thunderbird profiles. Then /home is tiny, just about only hidden files & folders and easy to back up. But I do not always just restore a /home with new install, just relink my data partitions. And I script 80 to 90% of my configuration settings, to make a new install easy. But I did that as I use LTS versions as main working installs, but also install every release, often more than once. After manually redoing settings several times, I said is that not what computer should be doing?

---

### Post by guiverc on 2021-11-27
> **gsparky2004 said:**
> What folders / files would you recommend I remove from my /home directory beforehand because they are Mint-specific? For example, I'm assuming anything related to graphics settings would be specific to Ubuntu, and anything Mint did would probably screw things up. Should I just "nuke from orbit" all configuration files that appear to be used by the OS? The files I'd like to keep are all of my Thunderbird e-mail files, my Firefox profile, my Rhythmbox files, and a few others. The rest I'm happy to either remove or rebuild later.

Thanks!

I'm a love of re-installing (*without format*) whatever I want to use; so my session settings etc continue from my prior OSes to whatever I'm using now.

My old box was dual boot & contained Fedora & OpenSuSE; now since replaced with different Lubuntu/Ubuntu versions... 

This *replacement *box is likewise dual boot & I initially installed a BSD & Linux Mint; the BSD required me to reformat for the Ubuntu install; Linux Mint did not.  I didn't really use Linux Mint - I was using it to really test this box was reliable before I trusted it (*it was a second hand/refurbished box*) and have a look around at Linux Mint whilst I tested the box :P   There must have been some theme or something I liked on Linux Mint that made me *not format* it when I installed the Ubuntu that's on it now (*it was 2017 so I've since forgotten*).  Either way the two installs were initially populated with the contents of my prior to Fedora & OpenSuSE systems (*one being used by Linux Mint*).  The box today has Ubuntu *jammy* on it (ie. on *development* cycle) & the other as Ubuntu 20.04 LTS. One of them was the prior non-formatted Linux Mint install.

No ill effects; but once in a *blue moon* I get to discover which one used to be Linux Mint, because something *Linux Mint* appears in a web browser that reminds me that I used Linux Mint to *test* the box before I really installed my OS on it. Otherwise I'd not know, ie. no adverse effects.  I cannot tell which install was Fedora, and which was OpenSuSE on this box (*I can still on my prior box though as I never changed the wallpapers, initially just in case I needed something off it but they remained that way*)

The install I use is re-use existing partitions without format, causes
- package installed to be noted
- system directories are wiped (*this will cause the Linux Mint adjustments system folders to be erased anyway*)
- new system is installed
- additional *manually installed* apps are re-install*ed *(*as I knew this, I manually cleaned out any Linux Mint packages myself; destroyed the sources so at least they'd be clean prior to the Ubuntu install; ie. I did some preparation). A format of / will achieve the same thing anyway*.
- no user file is touched (*unless format is used*) & you're asked to reboot

Fedora & OpenSUSE packaging is too different; so that install type doesn't return packages for either - but I didn't want that anyway; it was the /home data that I really wanted.

 Your app choices will of course vary to mine, so your results may differ, but I've noticed no ill effects in changing OSes.  I don't use either of thunderbird of rhythmbox so have no* real * experience with them. I ensured I had many backups of my evolution data [being my chosen email/MUA] but didn't touch the mail during my Linux Mint play.

---

### Post by gsparky2004 on 2021-11-27
> I would make sure I had a good backup of everything
Thanks for the reply. No worries there. I do a full, daily backup to a second hard drive. Then, every week, I do a full backup to an external backup unit. Might be overkill, but I lost six months of valuable data several years ago to a hard drive dying. I don't want it to happen again. "Cron" is your friend here.
> I prefer to have a separate data partition
I actually have a separate hard drive for my data. Up til now, when I've upgraded Linux Mint, I've done a complete re-install and simply pointed Mint to my old /home directory (on the separate hard drive). From start to finish has been 20 minutes or less before I'm back in business.
Only issue is that, after one re-install, my video went... wonky. It turned out that Mint needed to redo some video settings. I wound up having to remove several configuration files to get it working again. I just wanted to try to avoid such a hurdle.

---

### Post by gsparky2004 on 2021-11-27
> **guiverc said:**
> I'm a love of re-installing (*without format*) whatever I want to use; so my session settings etc continue from my prior OSes to whatever I'm using now.

As do I. The only issue (as I pointed out above) was that I once had a re-install go... wonky... due to some leftover video settings. I was hoping to avoid that. Long story short, I wound up removing most of my system configuration files from my /home directory, then re-installing the newest version of Mint. Everything was back to normal after that.

Based on your post, it sounds as if that's an exception, not the rule. So, I'll leave things as they are for my Ubuntu install, and if the old settings cause a problem, I'll remove the config files and start again. Given I can reload Linux Mint in 20 minutes or less, not something to worry about.

Thanks for the reply!

---

