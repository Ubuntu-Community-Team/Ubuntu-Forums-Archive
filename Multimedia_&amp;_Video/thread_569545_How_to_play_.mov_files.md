---
title: "How to play .mov files?"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by network.burner on 2007-10-07
Hello,
I have some videos with .mov extension
since this extension is played with quicktime, i downloaded and installed "quicktime-utils" and "quicktime-x11utils" from Synaptic Package Manager
Yet when i open those files, they open in totem player (wich is not able to play them)
i selected to open with other application..but there i cudnt find quicktime...
please help me

---

### Post by pay on 2007-10-07
I think that you need w32codecs installed. Assuming you have the right repositories (universe?) it should install with ```
sudo aptitude install w32codecs
```or ```
sudo aptitude install ubuntu-restricted-extras
```Here's [https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096) a little guide on howto add the repositories.

---

### Post by Cannaregio on 2007-10-07
Also use VLC instead of totem or quicktime or whatever.
Waay better results.

---

### Post by network.burner on 2007-10-07
> **Cannaregio said:**
> Also use VLC instead of totem or quicktime or whatever.
Waay better results.

ya i already hv installed VLC
but vlc also failed to play this..
it just shows a black screen (that is widout ne sound or video) and the buffer keeps moving

---

### Post by network.burner on 2007-10-07
> **pay said:**
> I think that you need w32codecs installed. Assuming you have the right repositories (universe?) it should install with ```
sudo aptitude install w32codecs
```or ```
sudo aptitude install ubuntu-restricted-extras
```Here's [https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096) a little guide on howto add the repositories.

i tried your way..
the last messege that arrived in terminal was :
0 packages upgraded, 0 newly installed, 0 to remove and 168 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

means nothing got downloaded.... is this reposatory problem?

---

### Post by texadactyl on 2007-10-07
The ubuntu-restricted-extras package in Feisty (2.2) seems to be empty except for a changelog file and forcing the user to switch repositories for the Sun Java 6 package.

I think that network.burner should try using `mplayer` with the w32codecs.  Here is a forum page that seems to be a well-documented guide:
[https://help.ubuntu.com/community/MPlayer?highlight=%28mplayer%29]("https://help.ubuntu.com/community/MPlayer?highlight=%28mplayer%29")

I find that the mplayer tool plays Quicktime, WMP,and Real files the best of the Linux tools, even when compared to VLC.  Of course, that could be related to my specific motherboard and graphics adapter:
[LIST]
[*]Shuttle Sb61V40 Mini-ITX kit PC (x86)
[*]Graphics: Intel 82865G (Northbridge)
[*]X.org information
82865G Integrated Graphics Device
PCI vendor:device = 8086:2572
Driver = i810
[/LIST]

-Richard

---

### Post by texadactyl on 2007-10-07
A balanced starting page for information about multimedia and Ubuntu is here:
[https://help.ubuntu.com/community/MultimediaApplications]("https://help.ubuntu.com/community/MultimediaApplications")

People frequently want to play DVD movies so go look here as well (linked to from first URL):
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Unfortunately, in 2007, Linux does not have the same success rate at minimum-effort playing of a wide variety of media on a wide variety of hardware.  Growing pains.  End users are forced to become system administrators (sympathies).  Mac (=D>) and Windoze (](*,)) are still ahead in this category.  I am also frustrated by this, at times, especially when a cousin comes over with a DVD from Asia and we get a grainy picture on all of my media players even though we get great sound :sad: .  

Anyhow, I am a busy developer on several platforms and a believer in the open source movement.  No complaints from me.

-Richard

---

### Post by pay on 2007-10-07
> **network.burner said:**
> i tried your way..
the last messege that arrived in terminal was :
0 packages upgraded, 0 newly installed, 0 to remove and 168 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

means nothing got downloaded.... is this reposatory problem?Open Add/Remove... from the menu and click on preferences and make sure there is a tick next to main universe restricted and multiverse. After that try ```
sudo aptitude update #probvably not nessasary as synaptic should do it for you
sudo apttude install w32codecs
```and see if it works this time.

---

### Post by myke on 2007-10-10
I have the unrestricted extras and w32 codecs installed properly but can never get any .mov file to work.  I have totem, mplayer, vlc, and kaffeine installed and all will play any video vile I try including .wmv but not .mov.   

I prefer kaffeine (I admittedly prefer a lot of KDE based programs though I prefer Gnome as my desktop -- choice is a wondrous thing) but would be ok using one of the other programs for just .mov files if I could get them to work.  Most will not open at all but some will open and have the sound running with no video.  Others will open with sound and a streaky video like an old tv you're trying to tune with the old rabbit ears. 

All of the other codecs work fine.  Why do .mov present such problems?   I've read several threads where this is the only file that will not play properly when the others will.

---

