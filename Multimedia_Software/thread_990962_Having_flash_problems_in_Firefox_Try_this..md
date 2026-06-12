---
title: "Having flash problems in Firefox? Try this."
date: 2008-11-23
forum: Multimedia Software
---

### Post by BastardNamban on 2008-11-23
I'm new to Ubuntu & linux in general, but I think I finally found a way to fix something that a lot of people seem to have problems with- I know I did. Since so many of these posts with flash problems go unanswered, I was really getting frustrated. I thought posting this might help some people!
___________________________________________________________________________

This fix worked for me using Ubuntu 8.04, after installing from the live CD.

I could get everything working in Ubuntu EXCEPT flash. Now, searching the forums, there are many posts on people with the same problem, and the same answers- install the restricted extras package after enabling multiverse, download flash 10 from adobe's site (never works), and all kinds of similar advice.

None of that advice worked for me. I was fuming mad, and I couldn't take it anymore! ](*,)

So in what you could say was "user rage", I went to Synaptic Package Manager under System/administration from the panel bar. I decided to try completely ripping firefox out of my computer, and reinstalling it. I did a search for firefox, and marked the main file for complete removal. Hit apply. Rebooting, firefox was indeed gone- I had downloaded the .tar for a new firefox 3.1 install before removing it, and exported my bookmarks too.

Once I realized I didn't know how to install from the .tar, as it would only open in archive manager, I got even angrier. Enraged, I went back to Synaptic Package Manager- searched for firefox, and it shows up- I don't know how it would install it if it wasn't connected to the internet, but I marked it for install.

This is key.

Hitting apply, I then rebooted- firefox shows up under internet! Ok, but what will happen? It didn't seem to have used the .tar on my desktop. 

Firefox opened, and somehow, less a LOT of the previous plugins that came with it natively on installing ubuntu, it had left my bookmarks and add-ons unchanged. Puzzled, as I tried to figure out how it could selectively remember what I wanted, and forgetting extentions, I tried youtube.

Youtube worked.

I still have no idea what *exactly* happened, but with the new leftover set of extentions, firefox works normally, and youtube/flash everything does too!

Here are the 4 plugins left in firefox that leave everything working nice:

1. Default Plugin 2. Demo Print Plugin for Unix/Linux
3. iTunes Application detector (disabled) 4. Shockwave Flash 10.0 r12


What can I say? Sometimes rage & stupidity payoff! To any linux pros out there, maybe you can shed light on what happened/might have been screwing things up, and why this worked.

I hope this might help some of you newbies like me who were having problems with flash in Firefox. :biggrin:

P.S.- sorry bout the super wide posting. Not sure how I fix that (yes, I am an idiot, but today, a lucky idiot!)

---

