---
title: "Why the browser speed difference?????"
date: 2006-01-04
forum: Networking &amp; Wireless
---

### Post by dalani on 2006-01-04
I've been using Ubuntu and enjoy very much  the robustness of Linux and the Ubuntu distro. I have Hoary installed in dual boot with my Win98SE. But one thing that keeps me from deleting windows and using only Linux is the HUGE speed difference between the FAST internet page loads in Win98SE (using Mozilla) and the slow response in Ubuntu (with Firefox 1.x). Can anyone explain this how, with a dialup Modem connection that uses the SAME hardware, internet access on Linux sooo slow??????  SYSTEM MONITOR shows the CPU maxxed out at 100% with more than two TABS loading. On Win98se, the I can have three tabs loading and still open heavy apps with littel latency. Is there some resource in Linux I can configure to speed up the webbrowser(changing the priority or some modem setting???)
I already tried Epiphany and there was no speed improvement.

Until I solve this, it is very difficult and bothersome to web browse with Firefox in Linux. Objectivly, Mozilla in Windows is maybe five times faster with more tabs open. Any help (or explaination) would be appreciated....

---

### Post by linuxted on 2006-01-04
[QUOTE=dalani]I've been using Ubuntu and enjoy very much  the robustness of Linux and the Ubuntu distro. I have Hoary installed in dual boot with my Win98SE. But one thing that keeps me from deleting windows and using only Linux is the HUGE speed difference between the FAST internet page loads in Win98SE (using Mozilla) and the slow response in Ubuntu (with Firefox 1.x). Can anyone explain this how, with a dialup Modem connection that uses the SAME hardware, internet access on Linux sooo slow??????  SYSTEM MONITOR shows the CPU maxxed out at 100% with more than two TABS loading. On Win98se, the I can have three tabs loading and still open heavy apps with littel latency. Is there some resource in Linux I can configure to speed up the webbrowser(changing the priority or some modem setting???)
I already tried Epiphany and there was no speed improvement.

Until I solve this, it is very difficult and bothersome to web browse with Firefox in Linux. Objectivly, Mozilla in Windows is maybe five times faster with more tabs open. Any help (or explaination) would be appreciated....[/QUOTE]

That is strange.  I had the opposite experience with Windows XP and Explorer... Ubuntu Firefox was much faster.

---

### Post by dalani on 2006-01-04
> 
That is strange. I had the opposite experience with Windows XP and Explorer... Ubuntu Firefox was much faster.

I notice you are using a 64bit processor. WinXP is still 32bit but Ubuntu is available in 64bit. SO it would be faster in Ubuntu in 64bits for any apps since the OS has been compiled to take advantage of the full 64bits.

---

### Post by viscount on 2006-01-04
I would say that you're having some strange issue and that
its probably not FF's fault. 

However, who knows.. you might want to see what you can
do to tweek FF to speed it up, like turning off ipv6, and other
various settings.

Search this forum for "speed up firefox" and "disable ipv6"
that should help...

---

### Post by linuxted on 2006-01-04
[QUOTE=dalani]I notice you are using a 64bit processor. WinXP is still 32bit but Ubuntu is available in 64bit. SO it would be faster in Ubuntu in 64bits for any apps since the OS has been compiled to take advantage of the full 64bits.[/QUOTE]

Well I had done the test on an older machine that was 32bit.  For this current machine I'm 100% Linux :)

You're right though, 64bit is slightly faster than the 32bit version.  I don't use it because the "support" isn't quite where I want it to be (Java, Flash, etc).

---

### Post by piedamaro on 2006-01-04
Also win98 is times lighter than actual gnome.

---

### Post by az on 2006-01-04
I think the version of firefox in Dapper will be faster.   It is slow to render pages, but I think that aspect has been given some love by the firefox developers lately.

The one in Dapper currently is as fast as any other browser out there, but crashes sporatically.

---

### Post by Stereotypical Rage on 2006-01-04
I noticed that Flash Player 7 eats my CPU and caused me to go horrendously slow on broadband. I just used adblock and blocked that from the page I was viewing. Sucks to be that page owner, right?:-P

---

### Post by dalani on 2006-01-04
thanks fellows
MArk this solved for me. I turned off Ipv6 and presto! a noticable speed improvement. Enough to allow me to use Ubuntu Linux as my web browser. 

Now if I could get  OpenOffice to run as fast as Word2000..another topic for another day

---

### Post by zasf on 2006-01-05
[QUOTE=dalani]why with a dialup Modem connection that uses the SAME hardware, internet access on Linux sooo slow??????[/QUOTE]

Same happens here, when I connect to the internet via ethernet card, speed seems to be equal in WIN and Ubuntu.

When I connect via dial up 56k modem, ubuntu is so much slower. I already turned ipv6 off, there must be something that i miss, I'll follow [this post]("http://ubuntuforums.org/showpost.php?p=423242&postcount=4") very closely when I go home this evening and tell if you I improve speed under ubuntu. 

My feeling is that, at this time ubuntu is slower, but this difference can't be appreciated when connected via ethernet card.

---

