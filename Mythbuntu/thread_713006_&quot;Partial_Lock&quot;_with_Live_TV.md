---
title: "&quot;Partial Lock&quot; with Live TV"
date: 2008-03-02
forum: Mythbuntu
---

### Post by RichardA on 2008-03-02
I'm watching live TV, I see a message about a recording about to start, I choose 'record it and go back to the main menu', and I can't watch live TV -- I get a partial lock and a message about how I 'should have gotten a channel lock by now'.

If only one or two tuners out of four are recording, surely I should be able to use one of the others to watch live TV? Have I missed something in the backend setup?

I also get some 0 size recordings. Is this related?

---

### Post by foxbuntu on 2008-03-02
This usually happens because the channel is setup inncorrectly for you HD data, was the channel automaticly added/discoverd by the channel scanner or did you have to modify it to make it work?

---

### Post by RichardA on 2008-03-04
I didn't modify any channels, you mentioning scanning channels made me wonder if I'd done that for each tuner. So I ran the back-end setup 24 hours ago, and I haven't seen any missing files since...

---

### Post by RichardA on 2008-03-06
I'm still getting "You should havev gotten a channel lock by now". When it happens it's for all the channels. If I wait a while and try the Live TV option again, it works.
Oh, and I've just seen a 0 byte file, so that's still happening :-(

---

### Post by RobJohnston on 2008-03-11
I'm getting a very similar problem with a nova-t-500 card, it looks like one of the tuners is disconnecting.

People have varying degrees of success disabling the remote and the EIT.

Right now I'm still searching for a solution.

Rob

---

### Post by RichardA on 2008-03-11
This is annoying. I bought Nova-T 500s because I read that they were 'fully supported'.
I suppose I could use the web-based method of getting program info. What about the remote? Buy a USB IR dongle?

I'm going to increase the channel tuning timeouts to see if that helps.

---

### Post by RobJohnston on 2008-03-12
I bought the card as I thought they were OK too.

I'm trying a script from [http://ubuntuforums.org/showthread.php?t=618546](http://ubuntuforums.org/showthread.php?t=618546)

We'll see how it goes.

---

### Post by RichardA on 2008-03-13
Looking at that thread, it seems that the tuner can disconnect without leaving a message in the logs, so the script will only be a partial fix.

Someone else says they're not using broadcast program data or the supplied IR receiver, and their tuners are stable.

I can work out how to change to web-based program data, but how do I change IR receivers? I've got a USB one (SigmaTel something) lying around. Can I just plug it in, edit something in /etc/lirc and still use the same remote?

---

### Post by RobJohnston on 2008-03-13
Not sure about the remote, you can disable the nova t 500 one with the work around here:
[http://www.linuxtv.org/pipermail/linux-dvb/2008-February/024079.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-February/024079.html)

Are you following a guide to get the other guides working?

---

