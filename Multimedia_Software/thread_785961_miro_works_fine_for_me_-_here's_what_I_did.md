---
title: "miro works fine for me - here's what I did"
date: 2008-05-07
forum: Multimedia Software
---

### Post by goggins on 2008-05-07
There are a lot of posts/threads regarding various miro related problems. I'm a stone cold newbie, so sorry if this isn't protocol, but it seemed the best way to reply to all of them.

I installed miro using add/subtract and doing nothing fancy so I think it came from ubuntu repositories.  It didn't play.  I fixed this (and it now works very well except some screen issues that seem endemic to my system) by following the miro help instructions.

Open miro and click on help in the top menu.  At the miro help page, select the FAQs.  In the FAQ index, select 2.7 - problems with miro using feisty.  The recommendation is "Try following the feisty instructions on this page", and "this page" is a link.  Click that link and there are two instructions you need to follow.  1) Near the top, headed "on Debian/Ubuntu" is a command like 'sudo apt-get install build-essential pkg-config imagemagik subversion' - copy it and paste it into the teminal.  Answer prompts appropriately.  2) Scroll down under "Installing prerequisites" to "*On Hardy" and copy the paragraph long command there and paste it into the terminal.  Again answer prompts appropriately.  Run miro.  

Hope it works for you.

---

### Post by Jimbotronics on 2008-05-10
> **goggins said:**
> There are a lot of posts/threads regarding various miro related problems. I'm a stone cold newbie, so sorry if this isn't protocol, but it seemed the best way to reply to all of them.

I installed miro using add/subtract and doing nothing fancy so I think it came from ubuntu repositories.  It didn't play.  I fixed this (and it now works very well except some screen issues that seem endemic to my system) by following the miro help instructions.

Open miro and click on help in the top menu.  At the miro help page, select the FAQs.  In the FAQ index, select 2.7 - problems with miro using feisty.  The recommendation is "Try following the feisty instructions on this page", and "this page" is a link.  Click that link and there are two instructions you need to follow.  1) Near the top, headed "on Debian/Ubuntu" is a command like 'sudo apt-get install build-essential pkg-config imagemagik subversion' - copy it and paste it into the teminal.  Answer prompts appropriately.  2) Scroll down under "Installing prerequisites" to "*On Hardy" and copy the paragraph long command there and paste it into the terminal.  Again answer prompts appropriately.  Run miro.  

Hope it works for you.

This worked like a charm, and Miro playbacks finally works perfectly on my system (ATI Radeon Xpress series integrated graphics).  Following good directions can be an amazing thing!

Megathanks, goggins!

---

### Post by goggins on 2008-05-11
Strangely enough, after I wrote that I installed Stellarium whihc was very, very clunky, so I broke down and installed the 3rd party nvidia driver for my machine.  Stellarium now runs much better, but miro shuts down the second I try to play something.  I guess I need to fing a way to toggle that driver or else give up on stellarium.

Sure enough, I killed the nvidia driver and miro now works fine, but Stellarium is pretty much too clunky to use.  Time to look for a different planetarium program, I guess, because miro is just too wonderful of an app to lose.

---

### Post by Redptc on 2008-05-14
I'm glad you have it working for you. I get it running but really not very well. Sound out of sync and erratic while the video often stutters along.

I may follow your instructions but would like to ask what version of Ubuntu are you running?

---

### Post by goggins on 2008-05-18
> **Redptc said:**
> I'm glad you have it working for you. I get it running but really not very well. Sound out of sync and erratic while the video often stutters along.

I may follow your instructions but would like to ask what version of Ubuntu are you running?

I'm running Hardy.

---

### Post by slugicide on 2008-06-24
Miro has never worked for me.  I try and try, every release, every new dist upgrade...  I give up now.  I'm erasing it from my mind.

---

### Post by abbot on 2008-10-06
does anyone have that code you're supposed to paste?  looks like the link in the faq is broken.

[http://www.getmiro.com/documentation/index.php/The_FAQ#I.27m_having_problems_with_Miro_on_Ubuntu_Feisty](http://www.getmiro.com/documentation/index.php/The_FAQ#I.27m_having_problems_with_Miro_on_Ubuntu_Feisty).

why can't they just make their program work.  i've tried using miro on every version of ubuntu since warty and it's never really worked right.

---

### Post by qns8dn3 on 2008-10-11
i had the problem that miro crashes immediately after starting playback.

This [ubuntu miro playback issue solution]("http://orobos.wordpress.com/2008/08/27/miro-playback-issue-solution/") worked in my case.

---

### Post by xcusmwah on 2008-10-11
Wow, this solved my problem.  Thank you very much.

---

