---
title: "how to get past this error while installing xbmc?"
date: 2010-08-01
forum: Multimedia Software
---

### Post by stephanecharette on 2010-08-01
I'm trying to install XBMC for the first time.  Machine is an ION 330HT running fresh install of Ubuntu 10.04 64bit.

The steps I found are for 9.10, not 10.04, and they don't seem to work correctly on 10.04.

Here is what I've done:
[FONT="Courier New"]sudo add-apt-repository ppa:team-xbmc-svn/ppa
sudo apt-get update
sudo apt-get install xbmc xbmc-standalone[/FONT]

This results in the following message:
[FONT="Courier New"]The following packages have unmet dependencies:
  xbmc-data: Depends: xbmc-bin (< 1:10.08~svn32246-lucid1.1~) but 1:10.08~svn32375-lucid1 is to be installed
E: Broken packages[/FONT]

I understand what this message would mean (xbmc-bin is too new according to what xbmc-data knows) but I have no idea how to fix it.

Any help would be greatly appreciated!

---

### Post by stephanecharette on 2010-08-02
There is so much confusing information and variations when it comes to xbmc...!  But I finally got it installed.  I'm not 100% certain which step finally got things running, but here are the ones I think are key to getting xbmc installed:

- sudo gedit /etc/apt/sources.list
- remove all references to xbmc that you may have
- look at all the files in /etc/apt/souces.list.d/
- remove all files that have to do with xbmc
- run the command:  sudo add-apt-repository ppa:team-xbmc/ppa
- run the command:  sudo apt-get --install-recommends install xbmc

Hope this helps someone.

---

