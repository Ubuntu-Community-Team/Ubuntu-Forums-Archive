---
title: "Garbled text XBMC"
date: 2011-09-02
forum: Multimedia Software
---

### Post by wilber85 on 2011-09-02
Installed XMBC recently on Ubuntu 11.04. 

Everything went smoothly, except when I start up XBMC I get this.  As you can see, all text is garbled.  The rest of the graphics are fine, just text is unreadable.  I dont notice this in any other programs.

Any ideas?

---

### Post by sackerud on 2011-09-03
Ooooh, finally I found someone with the same problem. Been googling my a** off to find a solution for this. I have the exact same issue on an HP Pavilion zt3000 laptop.

My laptop has a ATI graphics card, Radeon RV250 [Mobility FireGL 9000].

I really have no clue on how to solve this but I'll post here if find anything useful.

---

### Post by axelitus on 2011-09-18
I just installed Ubuntu 11.04 Natty Narwhal in an old laptop I had (Vaio VGN-A190F) to use as a Media Center. This laptop has an ATI Mobility Radeon 9200 AGP, ehich uses the integrated driver (No additional/propietary driver is detected).

I have the exact same issue (I used the unstable ppa from team-xbmc, but I tested in another more recent Vaio laptop with a recent ATI card and works just fine). The text is all garbled and unreadable :S

Any fix for this?

Everything else works great. I'm watching my image Full-HD in a Samsung TV without problems, so I'm guessing incompatibility with OpenGL versions?

---

### Post by wilber85 on 2011-09-26
bump? :-\"

---

### Post by sackerud on 2011-09-26
@wilber85 and axelitus:

You guys have screenshots from your garbled XBMC. Have you posted this on the XBMC forums? I believe we have a better chance on getting help over there. Seems more related to the XBMC bits than Ubuntu.

---

### Post by wilber85 on 2011-09-28
Yes I have posted this on XBMC forums.  I got similar results over there...a handful of people with the same issue, no clue why or how to fix.  Continuing to troubleshoot on my end.  ATI seems to be a common factor.

---

### Post by axelitus on 2011-09-28
Could you give the post reference so we can look at it and make some noise about it?

---

### Post by axelitus on 2011-09-30
I just tried XBMC Live Dharma 10.1 (which runs on Ubuntu 10.04LTS) and it worked like a charm... I'll try XBMCFreak later to see if it's a problem with Ubuntu or the unstable builds of XBMC...

---

### Post by marlar on 2011-10-17
I have the same problem with Linux Mint 11 LXDE edition. And yes, I have an ATI card.

Have you guys found any solutions?

---

### Post by axelitus on 2011-10-19
I haven't solved it yet... I did not try again as a matter of fact... I just installed the XBMC 10.1 live CD (which worked great)

The problem seems to be with the combination Ubuntu 11.04 + XBMC unstable (develop branch) + ATI graphic card (older models which aren't supported anymore).

With the release of Ubuntu 11.10 it's just a matter of trying again, just not have time with right now :S maybe the unstable branch has gotten updated as well thus making this work...

---

### Post by AMSlider on 2011-10-19
Dudes, upgrading to 11.10 fixed it for me.  I think it was something in the xorg files, since xbmc and boxee were both garbled for me.  Also, I'm still on the unstable branch and same boxee version after the 11.10 upgrade and all works great!  At least on lubuntu....

Cheers

---

### Post by axelitus on 2011-10-25
Well I just updated my XBMC Live 10.1 installation to Ubuntu 11.10 (running the command 'sudo do-release-upgrade' in the terminal). I then updated the ppa to ppa:team.xbmc/unstable (and then changed the release to maverick as there are no repositories for oneiric) and ran 'sudo apt-get update' to update the repositories.

I reinstalled xbmc and xbmc-live (I ran sudo apt-get upgrade but it didn't like the updates so I forced the install of the new versions, you are encouraged to try 'sudo apt-get upgrade' first).

After all this and a reboot, the new version of XBMC runs really nice :D no more garbled text. So I can only support the theory of AMSlider about the xorg files + drivers. So: update to Ubuntu Oneiric :D

---

### Post by dondada on 2011-11-11
I've been noticing this same problem for about a year now on my Ubuntu box hooked up to my Samsung TV. I tend to upgrade my Ubuntu when the new versions come out and, contrary to the above, Oneiric seems to garble text more for me than Natty. However, it's not only XBMC for me, it also happens in Ubuntu. Right now, the top third of my desktop background is garbled too. When I mouse over my Unity menu, the flyover text is garbled. 

Rebooting fixes it every time, so I've never really bothered looking for a fix until today. Just now, my desktop background changed and the new image is fine.

My graphics card is integrated: Intel 945G x86/MMX/SSE2

I'm using the team-xbmc/ppa/ubuntu maverick repository for XBMC.

I'd rather not reinstall everything until I have to, probably when 12.04 comes out, so I'm looking for an easier fix.

---

### Post by AMSlider on 2011-11-20
> **dondada said:**
> I've been noticing this same problem for about a year now on my Ubuntu box hooked up to my Samsung TV. I tend to upgrade my Ubuntu when the new versions come out and, contrary to the above, Oneiric seems to garble text more for me than Natty. However, it's not only XBMC for me, it also happens in Ubuntu. Right now, the top third of my desktop background is garbled too. When I mouse over my Unity menu, the flyover text is garbled. 

Rebooting fixes it every time, so I've never really bothered looking for a fix until today. Just now, my desktop background changed and the new image is fine.

My graphics card is integrated: Intel 945G x86/MMX/SSE2

I'm using the team-xbmc/ppa/ubuntu maverick repository for XBMC.

I'd rather not reinstall everything until I have to, probably when 12.04 comes out, so I'm looking for an easier fix.


That is strange... Have you tried the ubuntu classic or gnome environments?

Probably a long shot, but if it's connected to the TV via HDMI, maybe try a new cable?

---

### Post by axelitus on 2011-11-21
> **dondada said:**
> I've been noticing this same problem for about a year now on my Ubuntu box hooked up to my Samsung TV. I tend to upgrade my Ubuntu when the new versions come out and, contrary to the above, Oneiric seems to garble text more for me than Natty. However, it's not only XBMC for me, it also happens in Ubuntu. Right now, the top third of my desktop background is garbled too. When I mouse over my Unity menu, the flyover text is garbled. 

Rebooting fixes it every time, so I've never really bothered looking for a fix until today. Just now, my desktop background changed and the new image is fine.

My graphics card is integrated: Intel 945G x86/MMX/SSE2

I'm using the team-xbmc/ppa/ubuntu maverick repository for XBMC.

I'd rather not reinstall everything until I have to, probably when 12.04 comes out, so I'm looking for an easier fix.

Well, one thing that was common to all of us that had the problem is that the graphic cards where all ATI (and I think most of them, if not all where old ones that are no longer supported by ATI). Your problem could be anon-related issue also because as of now the problem was only with XBMC, no the whole OS (it seems to me yours is a driver issue) but I would suggest to try a couple of things and see if one solves it:
1. Try upgrading to Oneiric (I've been using it since it came out and is working very nice, have it installed in three different machines and it works fine on all).
2. Install the latest drivers for your card. (Look for the additional drivers notification in Ubuntu. If it does not pop, try searching on Intel's website for a supported Linux driver.
3. For XBMC try using the development (unstable) PPA. It's currently marked as unstable but as of now I'm happy running it. It hasn't given me any trouble at all once I got it working with Oneiric.
4. ¿Does this problem only occur with your TV connected or does it happen also only with the monitor attached to it? (Maybe is the cable as AMSlider suggested).
5. As AMSlide suggested try different environments (try classic or unity2d which are the lightest one).

Hopefully one of this points will help you fix the issue with garbled text.

---

