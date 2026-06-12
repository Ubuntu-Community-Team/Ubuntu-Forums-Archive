---
title: "Auto-connect to strongest network?"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by EuropaCar on 2010-05-10
I am running Ubuntu 10.04, but this problem has occurred since I started using Ubuntu (I believe it was 8.04).  

I use a laptop so I am constantly on the move and switching networks.  I put the laptop in standby and go to a new place and it would be nice if it would automatically connect to the strongest network.  However, what it does is the opposite - it seems to be trying to connect to the network that I last connected to.  When that fails (because I'm miles away from it) it gives up and the status is 'disconnected.'
This is easily solved by connecting manually, but is there an automated function to do this?  Am I missing a setting somewhere?

Thanks in advance

---

### Post by EuropaCar on 2010-05-12
any ideas?

---

### Post by rnerwein on 2010-05-12
hi
be happy that your laptop don't try to connect automatically to the strongest network. i guess
this would be end in a totaly chaos.
have fun
ciao

---

### Post by Zintha on 2010-05-12
> **rnerwein said:**
> hi
be happy that your laptop don't try to connect automatically to the strongest network. i guess
this would be end in a totaly chaos.
have fun
ciao
Yeah, i'd hate for it to be "strongest" network... When I move my laptop in my house there are 7 other wireless signals floating about.

I'd get pissed off to be honest if it kept changing.

---

### Post by EuropaCar on 2010-05-12
If I move from the library to my dorm then I want it to automatically connect to the new location's preferred network.  Right now, it just keeps trying to connect to the old network which doesn't technically exist after I move locations.

**I don't want it to constantly be changing but if the old network that it was connected to is far out of range then I want it to get a new one.**

I literally drive 2 hours from one place to another, open the laptop, and find it trying to connect to the old one.

---

### Post by EuropaCar on 2010-05-23
anyone??

---

### Post by QLee on 2010-05-23
> **EuropaCar said:**
> anyone??

When you suspend your laptop, it thinks it is resuming in the same location (how would it know different, it was asleep during the trip).

If you click the network manager icon and disconnect before you suspend, and if you have the new location set to auto connect, it should work as you want assuming that you have one of the network interfaces which does resume OK.

---

### Post by EuropaCar on 2010-05-23
yes you are correct.  But there should be a step before connecting where it actually detects if the network is still available.  You say "how would it know different," but it *should* know different once it wakes up and sees the network is unavailable.  
I may be nitpicking but even this step of disconnecting before suspending is annoying.  Windows has had this feature since xp as far as I know.

---

### Post by QLee on 2010-05-23
Well, what you find annoying, I see as proper secure behaviour, guess it gets down to personal preference. I don't want my wireless connecting automagically to any access point.

However, if you want to argue that Windows is better then I don't want to take part in that discussion. ...And developers are not likely to see your preference here, consider filing a wishlist bug.

---

### Post by EuropaCar on 2010-05-23
YOU personally may not want it to connect automatically but there is clearly a setting in wireless security for connecting to each network automatically.  THIS should be where 'proper secure behavior' is set.  Mine is currently set to connect automatically.  Yours must be set to not connect automatically.

Now, given that I have told it that I want to connect to this network automatically, it should do so..

I will file a wishlist bug as you suggested.

---

### Post by QLee on 2010-05-23
[QUOTE=EuropaCar]YOU personally may not want it to connect automatically but there is clearly a setting in wireless security for connecting to each network automatically.  THIS should be where 'proper secure behavior' is set.  Mine is currently set to connect automatically.  Yours must be set to not connect automatically.[/QUOTE]

Fair comment, that's why I used the word I.

[QUOTE=EuropaCar]Now, given that I have told it that I want to connect to this network automatically, it should do so.  [/QUOTE]

Interesting thing is that because you brought this up, I decided to try with my system setup for automagic.

I was connected to an AP when I suspended the laptop, then I shut that AP down and turned on another AP. Each had different configurations and ssids. When I resumed, my system did in fact try to connect to that new access point (I set up that connection to be automatic before suspending). The problem is that I only have this laptop with Karmic on it to test with at the moment but it works as you desire in your description.

---

### Post by EuropaCar on 2010-05-23
OK!  So I guess this problem is only my own..
In that case, any suggestions on what might be causing my computer to be doing this?

[QUOTE="QLEE"]I was connected to an AP when I suspended the laptop, then I shut that AP down and turned on another AP. Each had different configurations and ssids. When I resumed, my system did in fact try to connect to that new access point (I set up that connection to be automatic before suspending).[/QUOTE]

By any chance, was the first AP *not* set to automatic and the second was?

---

### Post by QLee on 2010-05-23
[QUOTE=EuropaCar]OK!  So I guess this problem is only my own..
In that case, any suggestions on what might be causing my computer to be doing this?[/QUOTE]

Don't be too quick to assume it's only your problem, remember I can only test with 9.10 and I think I remember you said you are using 10.04.

[QUOTE=EuropaCar]By any chance, was the first AP *not* set to automatic and the second was?[/QUOTE]

Good logical troubleshooting, it's a pleasure to work with someone who thinks.

I just verified that it worked the same if the first AP was connected automatically or manually, the system tried to connect to the automatic (optioned) second connection (2nd AP) when resuming.

We (perhaps I should state you) need someone using Lucid to try. I do find the topic interesting. Maybe we should ask for someone using the same wireless interface as you in case that has an effect.

---

### Post by QLee on 2010-05-23
I see this thread has been around a while and you've had difficulty attracting the help you want.

Perhaps you would consider amending the subject line, what you stated isn't really what you want to accomplish. What you want is successful roaming.

Another thing to consider, if this post sits here and no one else steps up to help, ask a mod to move it to the Networking and Wireless sub forum, there is very likely somebody over there using 10.04 with the exact same interface as you and I doubt your thread would be ignored for long.

---

### Post by EuropaCar on 2010-05-24
Thanks for the response QLee, those are great suggestions.
Yes, if anyone is reading this and has 10.04 and can reproduce this problem - or not - please let me know.

I have asked a mod to move the thread, too.

=edit=
not sure if I can edit the title myself, I guess an admin has to do that
and thanks QLee for adjusting your access points and performing those tests

---

### Post by tseliot on 2010-05-26
Moved

---

### Post by Elfy on 2010-05-26
Is this supposed to be in the archive?

---

### Post by cariboo on 2010-05-26
It looks like it was accidentally moved to the archive instead of Networking & Wireless in the main sub-forum.

---

### Post by Filipek on 2010-06-02
I would "enlarge" the topic a bit asking whether there is some software or it could be scripted to **define network profiles** within Ubuntu.

On my Lenovo notebook, there is very cool piece of software in Windows XP where you can set up the network profile (defining what adapter you'd use, encryption, even IP address and stuff like that) and activate the profile whenever you need to.

While moving among many networks it is very usable (mostly because you don't have to fill in the IP adrress details when there is no DHCP option). But this could "solve" this issue too.

Thank you.

---

### Post by EuropaCar on 2010-06-14
hmm I am not sure how to implement your solution Filipek

well here is one bit of information that might help solve the problem: when I move to a new location and resume the computer from sleep, it attempts to connect to the previous network and that is the ONLY network that appears on the list for a little while.  Or in some cases, all of the networks from the previous location appear on the list of available networks.  

In other words, for a few seconds it does not replace the old list of available networks with new ones.  So maybe if I could get the applet to first detect networks and then connect it would solve the problem?

I suggest this but have no idea how I would actually do it.. maybe a "sleep #" command or something?

---

### Post by EuropaCar on 2010-10-14
It's been a while, but I just thought I'd post:
Ubuntu 10.10 solved this issue for me!!
Additionally, a problem I've been having where my brightness buttons don't work has been solved.
I don't know if these were intentional fixes or if something just ended up being screwed up in my own setup for a while and was updated, but either way I am a happy camper :)

---

### Post by mithunsingh123 on 2010-10-14
This isn't always desirable.  For example, say you're sitting right next  to an access point, but so are 20 other heavy internet users.  You  might do much better connecting to the access point across the hall.  Or  say you get 5 bars from the wifi router powering your 6Mbit home dsl  connection, but you get one bar and a good relationship with the owner  from the business across the street that has a 20mbit synchronous  connection siting largely unused most evenings.

Thanks

---

