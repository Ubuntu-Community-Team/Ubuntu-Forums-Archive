---
title: "strange audio feedback problem, still"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by eclectic4 on 2007-06-17
Hi, folks,

I posted about this back in January, and have gotten no clues about it, only two posts saying others are having similar problems.

My original post on this site is at:
[http://ubuntuforums.org/showthread.php?t=333478](http://ubuntuforums.org/showthread.php?t=333478)

I also got no response from this post:
[url]http://www.linuxquestions.org/questions/
showthread.php?p=2566439&highlight=strange+feedback#post2566439[/url]

As I said there, there is no microphone attached, the feedback is coming from software.  It doesn't happen in suse which is dual booted on this machine.  

I recently upgraded ubuntu to 7.04 but this problem remains unchanged

A local linux geek i met today says it's probably a problem with the driver modules.

I have compared "lsmod |grep snd" in both suse and ubuntu but i'm not smart enough to see any important difference. 

Can someone please help me with this? I am off work this week and I would love to get this fixed.  I really don't want to consider switching distributions over a little thing like this.

Thanks.

---

### Post by Reugen on 2007-06-17
I have a similar problem if i have the ac97 slider turned up at all.  If i turn it down it goes away.  This is with both a sb live 5.1 and RealTek ALC850.

---

### Post by eclectic4 on 2007-07-09
Disappointed that I have not gotten one useful response about this from all these posts, and lacking the mental and physical energy to take the quest to usenet, and to irc (which I would be a newbie at), I have done a workaround.

I have another computer sitting next to this one with the problem, and the other is running Dapper. It had a vortex 2 8830 sound card. I swapped the sound cards between the two computers. Now Dapper is sounding fine with the sb pci512, and this machine is fine as well with the vortex. I think the pci512 is a better card than the vortex, but I don't know for sure; I would like to have the better card running on my better machine, but oh well.

I hope someone with the knowledge to fix this takes an interest in this problem. Please let me know of any news on this.

I guess I'd be willing switch cards again to reproduce the problem if someone out there seriously wanted my help and info.

---

### Post by eclectic4 on 2008-05-10
This problem reoccured when, after my upgrade to Gutsy, via the update manager, I was using a similar but higher end sound card, the SB Live 5.1.  Now I have installed Gutsy from scratch via cdrom, and the problem disappeared, including after upgrading to Hardy.

---

