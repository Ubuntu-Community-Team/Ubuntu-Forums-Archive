---
title: "Durr I stoopid how connect 2 windoes sharez"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Aped on 2009-04-15
Yeah, I have some shared files on a windows machine that I want to xfer over the network to one of my lunix machines. 

just using the file browser, I get a seriously pensive delay on the computer's part (attempting to connect to windows share) and then the following error: 

Opening win-desktop
You can stop this at any time by pressing cancel

and then

Unable to mount location
Failed to retrieve share list from server.


Would using something like samba be of benefit to me here? This IS a wireless G/N network, if that makes any difference whatsoever.

---

### Post by Svensk023 on 2009-04-15
As a suggestion, use proper English in your thread's title, otherwise most people will just ignore it.

---

### Post by Aped on 2009-04-15
> **Svensk023 said:**
> As a suggestion, use proper English in your thread's title, otherwise most people will just ignore it.

Your pardon, good sir, and dually so for the inconvenience it must have caused you to click on my thread solely to post a (purely justified) remonstration. That I should be so crass! The imposition! Lord have mercy on my soul.

.... So: Repost w/ proper english title, d'ya think? I just meant it as a little self-deprecation; I don't think anyone seriously types like that.

---

### Post by DJonsson2008 on 2009-04-15
Some tips...

I found KDE konqueror a very handy tool in sorting out windows shares, for some reason it seemed to give more leverage with shares and attached NTFS drives.

On hardy 8.4 the GUI's network browsers were iffy in terms of telling
the full story of what machines were available and what drives. Sometimes
I could see the machines but not the shared drives, so I did not rely
on this.

Instead the Ubuntu Places>Connect to Server interface was my main tool for making the connection... then I rock and rolled between Nautilus and KDE Konqueror to get a firm handle on the drives. Remember to bookmark your shares in konqueror once you have them active, I've found these bookmarks stick better there than in Nautilus.

On the windows side there seems to be different behaviour if you are attaching to a domain or a workgroup. If you don't have a workgroup happening on your windows install you may find it best to work out how
that works with another windows machine on the same lan first.
A caveat here though XP to W2K and different distros of
NT all have their nuances with peer to peer sharing, I did
not find Ubuntu any harder, but it was a similar process.

Browsing on the GUIs for shared resources does not always mean they
are not available...you may get lucky though and find that works for you,
it was not the case with me on any of the 3 Ubuntu Hardy installs I've made yet.

---

### Post by Svensk023 on 2009-04-15
was just saying, so you would get the help you needed man

EDIT:

or should I say, increase your chances of getting the help you needed.

---

### Post by DJonsson2008 on 2009-04-15
If I remember right having samba IS essential to getting windows shares to work. Also it really helps to have the exact same username/password on 
both machines in the initial attempts of getting the machines to talk with each other. Here is where XP/W2K is knarly, unless you are confident with your Windows LAN skills you will save yourself much time and hassle by
having the exact username/password for both machines at first to get started.

Anyhow as a noobie who has yet read the book on Linux and Ubuntu that's
what I discovered, I don't know enough to detail the process to you
otherwise.

---

### Post by DJonsson2008 on 2009-04-15
For a new thread...(another humbling noobie Ubuntu initiation.)

Go to [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)

Click on the support category you wish to make 
a new thread to in the list of forum categories.

Then at the top right hand corner you will see
the [NEW Thread] button

---

### Post by Svensk023 on 2009-04-15
> **Aped said:**
> Your pardon, good sir, and dually so for the inconvenience it must have caused you to click on my thread solely to post a (purely justified) remonstration. That I should be so crass! The imposition! Lord have mercy on my soul.

.... So: Repost w/ proper english title, d'ya think? I just meant it as a little self-deprecation; I don't think anyone seriously types like that.

I do enjoy your enthusiastic martyrdom!

and my mistake for not catching the humor at first glance.

---

### Post by Aped on 2009-04-15
> **DJonsson2008 said:**
> Some tips...

I found KDE konqueror a very handy tool in sorting out windows shares, for some reason it seemed to give more leverage with shares and attached NTFS drives.

On hardy 8.4 the GUI's network browsers were iffy in terms of telling
the full story of what machines were available and what drives. Sometimes
I could see the machines but not the shared drives, so I did not rely
on this.

Instead the Ubuntu Places>Connect to Server interface was my main tool for making the connection... then I rock and rolled between Nautilus and KDE Konqueror to get a firm handle on the drives. Remember to bookmark your shares in konqueror once you have them active, I've found these bookmarks stick better there than in Nautilus.

On the windows side there seems to be different behaviour if you are attaching to a domain or a workgroup. If you don't have a workgroup happening on your windows install you may find it best to work out how
that works with another windows machine on the same lan first.
A caveat here though XP to W2K and different distros of
NT all have their nuances with peer to peer sharing, I did
not find Ubuntu any harder, but it was a similar process.

Browsing on the GUIs for shared resources does not always mean they
are not available...you may get lucky though and find that works for you,
it was not the case with me on any of the 3 Ubuntu Hardy installs I've made yet.

Wow, thanks for taking the time to write all of that. I am playing with the Connect To Server... option as I type this. I have no experience with Nautilus and have just recently aptitude'd samba, though again I have no experience with it. Any chance you might know of a retard-friendly example page for either? 

For now, I'm making a share on the linux machine and attempting to access from the windows end. If this fails, I'll burn 3 dvds and be done with it :D

Seriously though, thanks again for the well-thought out response. I appreciate it.

---

### Post by DJonsson2008 on 2009-04-15
Folks have been helping me out here so that's what civilization is supposed to be about, including a bit of humour...

I do though have to get back to work...

for now can say these items helped

you may need to use gksu to call these.

shares-admin
systems-config-admin

also xfce4-appfinder you need to install this one
but it makes finding applications a breeze...

my experience was getting folders on my Ubuntu username.Desktop
shared was the easiest connect between my Windows/Ubuntu
worlds.

gotta go now...

---

