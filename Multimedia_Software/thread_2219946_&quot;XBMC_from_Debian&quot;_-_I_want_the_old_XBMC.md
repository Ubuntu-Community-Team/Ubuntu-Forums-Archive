---
title: "&quot;XBMC from Debian&quot; - I want the old XBMC back.  Please just tell me how to get it."
date: 2014-04-26
forum: Multimedia Software
---

### Post by CelticWhisper on 2014-04-26
tl;dr: Please provide easy-to-understand instructions on how to install a **non-Debian-approved** version of XBMC via the team-xbmc PPA without having to compile from source.


Trying to rebuild my HTPC environment and the latest snag I'm running into is getting XBMC back the way I had it before.  I added the team-xbmc PPA but every time I try to install XBMC, I get the "XBMC from Debian" version.

***_I do not want this._***  I've read a few discussions regarding a schism between the FFmpeg and libav projects and from what I gather, the change to libav for the "From Debian" version is not for the best.  Some people are having problems with libav playing back everything FFmpeg could, and it seems that the old tried-and-true XBMC used FFmpeg.

I really don't have any inclination to change away from what I was running before the 14.04 upgrade.  I had it working just fine, autolaunching just fine, and shutting down via Android, iOS and web remote interfaces just fine.  I've already had problems with XBMC freezing up my system when trying to use its inbuilt "Exit" command while sitting at a console, no remote anything.  That was on an experimental clean install of Lubuntu 14.04 earlier this evening.  It seems that I've had very good luck in the past with "XBMC" and very bad luck since 14.04's release with "XBMC from Debian."

I really am not concerned with any Debian philosophical aims in embedded libraries or whatever.  I know it sounds cold but I don't care what any Debian dev team wants - it's not my problem and I don't want to help them fight this fight.  I don't care what they want, I want my old, reliable software back.  I'd posted a few threads in ABS about other problems I've been having and this is adding up to a lot of frustration, unhappiness, and an overall very negative experience with Trusty Tahr.

It's getting to the point where I'm seriously considering switching this system to Windows and I really don't want to have to resort to that.  Ubuntu is supposed to be "Linux for human beings" and this human being has too much stress and frustration in his life to be fighting with every last step of trying to get his HTPC (which he uses for relaxation and to reduce that stress) working the way he's used to and comfortable with.  One thing is for sure: once I get this working and stable, I am permanently disabling all software updates.  Security?  I'll pull the LAN cable and load movies onto this thing with flash drives if I have to, I don't care.

Sorry for the rant(s).  I do appreciate any help you can give me.

---

### Post by QIII on 2014-04-26
If you are using the XBMC team PPA and you are not satisfied with it, the people to ask about it is the XBMC team.

You can find them at xbmc.org.  PPAs are not official Canonical resources.

You might see if they still offer older packages.

---

### Post by CelticWhisper on 2014-04-26
Fair enough, I'll ask on the xbmc forums.

Thanks for the quick response.

---

### Post by CelticWhisper on 2014-04-26
[Posted on XBMC forums.]("http://forum.xbmc.org/showthread.php?tid=193245")

One minor point of clarification - I'm not convinced it's a team-xbmc PPA issue.  I installed XBMC via ```
sudo apt-get install xbmc
``` before ever adding the PPA and I got "XBMC from Debian".  I purged xbmc via ```
sudo apt-get purge xbmc
``` added the PPA ```
sudo add-apt-repository ppa:team-xbmc/ppa
``` and tried installing again```
sudo apt-get update

sudo apt-get install xbmc
``` but still got the Debian version.  Doesn't that mean that it wasn't installing from the PPA, but rather still from the official 14.04 repository instead?

Thanks.

---

### Post by QIII on 2014-04-26
If you purged it, added the PPA and installed it again, you were installing what is in the PPA.

If you are installing it from the repo, what you are getting is what xbmc.org makes available and simply packaged by a Canonical maintainer or a MOTU, depending on which section of the repo it's in.   In this case, it's in the Universe repo, meaning it's from somewhere else and a MOTU just packaged it and made sure it worked.

It is still what is made available by xbmc.org.

EDIT:  I just looked at mine, which is from the PPA, and it is the "from debian" version.  I don't think there is any way around this, since xbmc.org produces it.  If you want something with ffmpeg, it may be that you will have to compile it on your own.

---

### Post by CelticWhisper on 2014-04-26
*nod*

Good to know.  Thank you again.  I'll see what they say on the XBMC forum, but I might be stuck with this.

That said, have you noticed any of the problems I read about with performance or file compatibility/decoding?  Does libav seem as competent as FFmpeg with handling all the formats I could expect to run into?

---

### Post by Yellow Pasque on 2014-04-26
The PPA you point to does not (yet?) package xbmc for Trusty: [https://launchpad.net/~team-xbmc/+archive/ppa/+index?field.series_filter=trusty](https://launchpad.net/~team-xbmc/+archive/ppa/+index?field.series_filter=trusty)

Your options:
1. Find another PPA
2. Ask the team-xbmc if they're going to package
3. Build it yourself

> I really am not concerned with any Debian philosophical aims in embedded libraries or whatever. I know it sounds cold but I don't care what any Debian dev team wants - it's not my problem and I don't want to help them fight this fight. I don't care what they want

Then run Debian sid with the debmultimedia repo where everything's rebuilt for ffmpeg and the packages are built with all of the options (regardless of draconian U.S. Copyright laws). It's the best way I've found to work around the libav nonsense.

---

### Post by The Spectre on 2014-05-04
The stable release of XBMC 13.0 is now out...
[http://xbmc.org/xbmc-13-0-gotham-rises/](http://xbmc.org/xbmc-13-0-gotham-rises/)

And using the Official PPA will now install the normal non Debian version...
[https://launchpad.net/~team-xbmc/+archive/ppa]("https://launchpad.net/%7Eteam-xbmc/+archive/ppa")[URL="https://launchpad.net/%7Eteam-xbmc/+archive/ppa"]

[IMG]http://xbmc.org/wp-content/uploads/xbmc-gotham-13_0-splash-600x336.png[/IMG] [/URL]

---

### Post by CelticWhisper on 2014-05-21
That is good news indeed.

Question: How do I go about replacing what I have on here already with the official v13 without hosing my library and settings?  I'm happy to post any apt output you need to verify what I have installed.

Thanks.

---

### Post by The Spectre on 2014-05-22
> **CelticWhisper said:**
> That is good news indeed.

Question: How do I go about replacing what I have on here already with the official v13 without hosing my library and settings?  I'm happy to post any apt output you need to verify what I have installed.

Thanks.
Once you add the XBMC PPA it should just upgrade the XBMC from Debian version to the official XBMC version.

That is what it did for me.

And the XBMC PPA will also automatically update you to version 13.1 when it is released, which is currently at the Beta 2 stage.

---

