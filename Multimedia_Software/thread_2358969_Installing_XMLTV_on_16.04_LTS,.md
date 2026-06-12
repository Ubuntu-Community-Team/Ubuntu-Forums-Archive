---
title: "Installing XMLTV on 16.04 LTS,"
date: 2017-04-19
forum: Multimedia Software
---

### Post by elsmandino2 on 2017-04-19
Hello,

I have just set up Ubuntu Server 16.04 LTS on my home server.

I have also set up TVHeadend and want to use the [COLOR=#555555][FONT=monospace]tv_grab_zz_sdjson[/FONT][/COLOR] EPG grabber so I can make use of my Schedules Direct account.

The problem is that only XMLTV 0.5.69 supports this particular grabber.

According to this  

[http://packages.ubuntu.com/xenial/all/xmltv/download](http://packages.ubuntu.com/xenial/all/xmltv/download)

the latest version of XMLTV is only 0.5.67.

Is there any way to install the later version on 16.04?

Thank you.

---

### Post by ajgreeny on 2017-04-19
There is a ppa which should allow you to add 0.5.69.2 to a xenial installation.

All info on how to enable and use it are at [https://launchpad.net/~alex-tomlins/+archive/ubuntu/xmltv?field.series_filter=xenial](https://launchpad.net/~alex-tomlins/+archive/ubuntu/xmltv?field.series_filter=xenial) though I have no experience of either this ppa, nor tv-headend, so can not tell you how likely it is to be successful for you.

---

### Post by elsmandino2 on 2017-04-20
Thank you so much for that - all installed now and fully working!

Purely out of interest (and as Linux novice trying to learn as much as I can at the moment):

1.  How did you manage to find that particular site?  I spent days looking for something like this but failed - is this something that comes with experience?
2.  As far as I can make out, backporting seems to be taking a program that was made for a later version of a distro and changing it so it fits the one that you are currently using.  In practice how difficult is this?  Is it something that anyone can do?

---

### Post by ajgreeny on 2017-04-20
> **elsmandino2 said:**
> Thank you so much for that - all installed now and fully working!

Purely out of interest (and as Linux novice trying to learn as much as I can at the moment):

1.  How did you manage to find that particular site?  I spent days looking for something like this but failed - is this something that comes with experience?
2.  As far as I can make out, backporting seems to be taking a program that was made for a later version of a distro and changing it so it fits the one that you are currently using.  In practice how difficult is this?  Is it something that anyone can do?
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum
.
To answer your questions posed in your reply, yes it is partly experience of how to solve problems that leads to my solutions (sometimes but not always).

I have a google custom search site at [https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao) which I set up rather than using the full google engine.  It searches many ubuntu linked sites such as this forum, askubuntu, launchpad, etc etc.
If I am looking for a package or package version not available in the normal repos I search for a ppa repository with search term **xmltv ppa** and this is how I found that ppa link for you.

How difficult it might be to compile or backport something for my own version of ubuntu that is not available in the repos is not something I can speak of with any personal experience as I have never done it; I do however, use several ppa repos and so far have never had any of the potential problems of doing so, ie dependency problems as a result of incorrect versions of other dependency packages that may be installed with a ppa.

---

### Post by elsmandino2 on 2017-04-21
That is really clever thinking - I shall remember that for future searches.

Thanks again - really appreciate the help.

---

