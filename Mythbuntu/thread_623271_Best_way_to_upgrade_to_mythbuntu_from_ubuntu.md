---
title: "Best way to upgrade to mythbuntu from ubuntu"
date: 2007-11-25
forum: Mythbuntu
---

### Post by trubblemaker on 2007-11-25
I want to upgrade to mythbuntu and would download the cd and use that two install but, I have a unique setup.  

I can only access my box by wireless/ssh.  It's currently a frontend/backend that displays to a tv via pvr-350 tv out.  It use madwifi, which needs to be complied from source 'cause I'm using a ubunut server which doesn't come with restricted drivers.

I want to know if it's possible to upgrade to mythbuntu by adding the correct repositories via souces.list?

Should I upgrade to Gutsy first?  (I'm on Fiesty)

If this is printed in a wiki somewhere point me to it and I'll read the manual, I've been searching but can't find it.

---

### Post by trubblemaker on 2007-11-25
What I really want is how to upgrade to mythbuntu from commandline.... that's basically what I want to do, I also need to know the kernel that's being used prior to upgrading... and if there are any special steps involved when you upgrade from using a server

---

### Post by superm1 on 2007-11-25
Ive got several comments here.

First off regelatsong wireless you can switch to a standard ubuntu kernel and start using linux restricted modules again.

As for upgrading, follow the standard sever upgrade process. There is a server upgrade tool that can be done via command line over ssh.

Pvr350 our has some troubles. You will need to activate gutsy proposed after your upgrade to get a patched mythtv that will be entering gutsy updates in a week or so. Also you need to grab a package from a ppa that includes the x server module. Search these forums and you will find it.

As for migrating to mythbuntu you will just need to install mythbuntu-desktop after you upgrade.

Hopefully that covers it all

---

