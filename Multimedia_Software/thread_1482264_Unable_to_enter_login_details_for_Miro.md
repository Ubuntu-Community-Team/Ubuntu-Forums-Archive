---
title: "Unable to enter login details for Miro"
date: 2010-05-13
forum: Multimedia Software
---

### Post by Midnighter on 2010-05-13
Please excuse if this is incorrect section, not entirely sure where it would belong. I rarely find myself posting as i rarely have any issues. But this is persistently annoying, tho not a deal-breaker.

 Currently running latest Ubuntu 10.04, fully updated. Everything works fine, even better than any previous releases. No problems worth mentioning. But this is annoying, so anyway, here I am. 

 Installed Miro, loads up and runs fine, can download no probs. The section at the top where it says "account", and you sit over it and it drops down a window for your login details (username, password) so as to recall your personal settings, preferences, etc, but it's not working. By this, I mean the drop-down appears, but clicking the mouse in the window on the lines does not seem to register with it, you can't enter anything. Annoying, slightly frustrating. Has anyone had any experience with this, and can someone please explain how to resolve it? Many thanks in advance.

---

### Post by Midnighter on 2010-05-14
Page 6? It fell to page 6? Not a single attempted reply? C'mon, doesn't anyone have anything to suggest at all? I thought Ubuntu had the biggest and most helpful community, it's what keeps being repeated all round the place.

---

### Post by praxis on 2010-06-11
I'm getting the same problem you're reporting.  Do you know if a launchpad bug has been filed for this problem?

---

### Post by Linux Lurker on 2010-06-16
Similar issue.
I can enter the log-in info... it just doesn't seem to "accept" it and proceed to log-in.
It doesn't bother me as much as it seems to you.  But, I just installed it and haven't "used" it much.  I'm sure that if I decide to regularly use it, this could be an issue.
They have a forum, don't they?  Since you're the OP, you've been knighted to check it out.
I'll check back soon to see what you've found.
Welcome to Ubuntu... (the) "biggest and most helpful community".  I look forward to you helping me with this issue.

Thanks ever so much. :-)

---

### Post by Linux Lurker on 2010-06-16
Ok... had to tease you a little bit for your 2nd post.
Not to be a jerk... but you kinda sounded "entitled" to an answer.  I doubt that's how you wanted to come across, and I've been where you are... WANTING A SOLUTION... ASAP.

Anyway... I started clicking around the "account" drop down button (right next to language button).  As previously mentioned, while I could enter my log in info in the drop down box... it wasn't "accepting" the info and actually logging in.

So, anyway... this is what works.  Click on "account" button TWO TIMES.  It will then display an actual log-in page.  Enter your info there, and you'll see that the former "account" button is replaced by your log in name.

Good enough for me.  Hope it works for you.
More importantly... hopefully this Miro will live up to its potential.

Happy Ubuntuing.
Miro v3.0.2

---

### Post by Midnighter on 2010-06-17
No, I sounded annoyed that not one single, solitary person even attempted to offer a suggestion, nor even ask for more details so's they could assist. It's always being pushed how helpful the Ubuntu Community is, but frankly I've found virtually every other forum more helpful than this one. I've assisted here and solved several issues, but the one time I ask for help, not a damn thing. Not even a weak attempt. Pretty ****-poor effort. I don't "want a solution ASAP", I just want someone to at least try, or offer to help. Nothing. Not a damn thing. Except now I have a wise guy, being a smart-****. 

As I already explained I get the drop down, but typing does nothing, nothing happens. Can't type password or login name. At all. Tried repeatedly. 

 Meh, I give up here, clearly no one gives a damn. I have better places to waste my time, places where people actually help one another.

edit: Jesus christ, it edits out weak words as swear words? Frak me dead! How PC can a place get?

---

### Post by wojox on 2010-06-17
I guess there's not a lot of Miro users. Did you download it from the repo's or from the Miro site?

---

### Post by josephpmh on 2010-08-10
OK, I think I found your solution.  I was having the same problems and came here for a solution.  When I didn't find one, I looked elsewhere and this is what I found:

[http://www.webupd8.org/2010/04/install-miro-30x-in-ubuntu.html]("http://www.webupd8.org/2010/04/install-miro-30x-in-ubuntu.html")

What I did was add the miro update repository.  From your terminal, run:

```
sudo add-apt-repository ppa:pcf/miro-releases
```

Then, also from terminal, run 

```
sudo apt-get update 
sudo apt-get upgrade
```

That worked for me (altho I needed to run apt-get update twice).

Hope this worx for you.


> **Midnighter said:**
> Please excuse if this is incorrect section, not entirely sure where it would belong. I rarely find myself posting as i rarely have any issues. But this is persistently annoying, tho not a deal-breaker.

 Currently running latest Ubuntu 10.04, fully updated. Everything works fine, even better than any previous releases. No problems worth mentioning. But this is annoying, so anyway, here I am. 

 Installed Miro, loads up and runs fine, can download no probs. The section at the top where it says "account", and you sit over it and it drops down a window for your login details (username, password) so as to recall your personal settings, preferences, etc, but it's not working. By this, I mean the drop-down appears, but clicking the mouse in the window on the lines does not seem to register with it, you can't enter anything. Annoying, slightly frustrating. Has anyone had any experience with this, and can someone please explain how to resolve it? Many thanks in advance.

---

### Post by mdgill on 2010-08-13
I had the same problem.  The solution by josephpmh to add the PPA and update to this new Miro version fixed the problem for me.

Midnighter: check it out and if it works come back and mark the problem solved.  That will help others.

---

### Post by tmsbrdrs on 2010-08-30
As a workaround for this problem, I've found that just tabbing over works for entering text in fields on Miro.
Sorry for the late response, just found the thread.
This problem actually effects more than just login, it's a general inability to enter text into fields by clicking them.

---

