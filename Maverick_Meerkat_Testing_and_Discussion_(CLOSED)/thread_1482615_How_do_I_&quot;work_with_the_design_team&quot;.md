---
title: "How do I &quot;work with the design team&quot;?"
date: 2010-05-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-05-13
No, this is not a joke :)

Even typing that I think my own first answer would jokingly be, "if you need to ask, you can't do it".

***Sort of a new take on "how much does that cost" .............. "if you need to ask, you can't afford it"*** :P

But I am serious. During Lucid Beta1 iso-testing I posted this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

[B]Lucid Live CD fails to display boot options w/o user action
CancelOk
[/B]

Which resulted in a mention in the Release Notes:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs)

Anyway, I'm still subscribed to that bug and I'd noticed another recent comment there that caused me to post this:

> 

Well, if Colin is still reading this and I'd bet so ;^) All we've really done is move the "interactive" part further down the line. You still end up having to select whether to just run Ubuntu or install Ubuntu. Sadly you're too far into the boot cycle by then to edit the boot parameters.

I've otherwise found Lucid to be totally worthy of a Live USB, that is quite stable, but I'm considering a remaster beginning with an Lubuntu image to avoid this "new feature".

Even once you know about the new behavior the option to press any key passes so quickly that an incoming phone call or some other untimely distraction can result in an otherwise unnecessary reboot.


Steve Langasek's response was (I highlighted the part that matters):

> Erick, it's true that the first prompt happens when it's too late to edit the boot parameters. However, it's important to recognize that editing boot options is *not* the common case: for the vast majority of users, install vs. try is the first selection they should need to make, and they normally won't even *know* if other boot options are needed until they've first tried to boot with the default options. So while I'm personally rather dissatisfied with the solution that's been implemented to hide the language selector by default, I think the comments here significantly exaggerate the severity of the problems that result, and I don't think it's necessary or appropriate to revisit this in 10.04. **[COLOR="Red"]Please work with the design team instead to improve our live CD's boot behavior for maverick.[/COLOR]**

Oh, and prior to that I'd posted a question at Ayatana:

[https://answers.launchpad.net/ayatana-ubuntu/+question/110648](https://answers.launchpad.net/ayatana-ubuntu/+question/110648)

> As I found out iso-testing prior to Lucid Beta 1 the Live CD now requires user interaction to display menu options:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

At first this seemed fine but having used this more and more I find it to be only annoying. Consider the following:

1) It creates confusion for those who are new to Ubuntu. I've seen this a lot at the forums.

2) We've only moved the interactive part to a later point in the boot cycle because you still must choose whether to just "run" Ubuntu or install Ubuntu, so this really did not result in a faster boot.

3) With that "move" all we've done is "remove" the options to check CD for defects, adjust boot parameters, etc. without an otherwise unnecessary reboot which only results in frustration.

4) Even after learning of the new "boot behavior" the option to press any key passes so quickly that even an unplanned phone call or some other interruption can cause me miss the opportunity, and increasing that "time out" would only increase the boot time.

I'm curious what others think about this. We can certainly plan changes for the first "point release" of Lucid and also for Maverick, and no time like the present ;^)


Thus my silly question :)

Now, I've tried to use IRC and being visually impaired it simply doesn't work for me. I need something slow and consistent, something I can spend my time focusing on!

That in itself is a huge problem with some web pages that have "stuff" stuck all over the place. I can easily overlook the obvious sometimes.

Anyhoo there it is, Don't laugh too hard.

I just figure we can either be complainers or we can at least try to shape things in a manner we deem sensible.

Edit: I forgot to add that I'm fully aware of UDS so maybe I'm being impatient, but in the past I've put things off too long so I want to get this "out there" ASAP.

---

### Post by cariboo on 2010-05-13
I believe the **[Canonical User Experience and Design Team]("https://launchpad.net/~canonical-ux")** is what you are looking for. There is a link o contact the team owner on the top right.

---

### Post by kansasnoob on 2010-05-13
> **cariboo907 said:**
> I believe the **[Canonical User Experience and Design Team]("https://launchpad.net/~canonical-ux")** is what you are looking for. There is a link o contact the team owner on the top right.

So you think it would be OK to just send Ivanka a very brief PM?

I don't like being a nuisance.

---

### Post by cariboo on 2010-05-13
You've more or less been asked to work with the design team, so I don't she'll mind. I've have good dealings with the Canonical people so far.

---

### Post by dino99 on 2010-05-14
from Matthew Helmke, on Planet:

There is a new initiative from the Canonical/Ubuntu Design Team to do a much better job communicating their thoughts, ideas and plans to the wider community. They have started a blog at [http://design.canonical.com/](http://design.canonical.com/) that I believe is worth reading regularly. Fire up your RSS feed reader and subscribe after taking a look at the wonderful foundation they have created to kick things off.

---

### Post by VeeDubb on 2010-05-14
> **kansasnoob said:**
> So you think it would be OK to just send Ivanka a very brief PM?

I don't like being a nuisance.

This is something a lot of people feel a little wierd about the first time, but it's really a good thing.

Unless the dev you're trying to talk to is an egotistical jerk, which I admit there are a few out there, they will be happy to hear from you.  This is how the open source community works.

I have ended up speaking directly the the developers of many projects over the last couple of years, and the response has always been the same.  They've been happy to hear from a user, helped me fix my immediate problem, and gotten useful feedback that helped them to improve their applications.  With at least one, I ended up doing in depth alpha testing for a smart phone app that was too unstable for public testing.  Even though I lack the skill to write useful software, I was able to contribute.

When  developer invites you to work with the design team, you should take them up on it without hesitation if you feel you have something of value to contribute.

---

### Post by castrojo on 2010-05-14
The design team's main hub is the ayatana mailing list, I recommend posting there:

[https://launchpad.net/~ayatana](https://launchpad.net/~ayatana)

---

### Post by cariboo on 2010-05-14
Thanks whiprush, I looked for that but couldn't remember the name.

---

### Post by Merk42 on 2010-05-14
> **whiprush said:**
> The design team's main hub is the ayatana mailing list, I recommend posting there:

[https://launchpad.net/~ayatana](https://launchpad.net/~ayatana)

Is there some special anti spam filter or something?
 I sent an email to [email]ayatana@lists.launchpad.net[/email] but it didn't show up in the mailing list as a topic

---

### Post by 23meg on 2010-05-14
> **Merk42 said:**
> Is there some special anti spam filter or something?
 I sent an email to [email]ayatana@lists.launchpad.net[/email] but it didn't show up in the mailing list as a topic

Have you subscribed?

---

### Post by Merk42 on 2010-05-14
> **23meg said:**
> Have you subscribed?

Yes, I'm getting email notifications from other people making threads and my name appears in the members list

---

### Post by kansasnoob on 2010-05-14
> **whiprush said:**
> The design team's main hub is the ayatana mailing list, I recommend posting there:

[https://launchpad.net/~ayatana](https://launchpad.net/~ayatana)

Thanks Whiprush. I had mentioned in my original post that I posted a question at Ayatana:

[https://answers.launchpad.net/ayatana-ubuntu/+question/110648](https://answers.launchpad.net/ayatana-ubuntu/+question/110648)

BTW, I'm Erick Brunzell on Launchpad and Lance at iso-testing.

I do receive Ayatana notices (dozens a day recently), but clearly I should have done that in a different way. Maybe from the team page I should have done something different:

[https://launchpad.net/~ayatana](https://launchpad.net/~ayatana) 

Due to my visual impairment I can easily overlook things :(

I personally try to avoid sending folks a PM unless I feel it's my last option. To me it's sort of like knocking on someones door unexpectedly.

---

### Post by kansasnoob on 2010-05-14
> **Merk42 said:**
> Yes, I'm getting email notifications from other people making threads and my name appears in the members list

Maybe we can both learn something here :confused:

I figure the only dumb question is the one that goes unasked :)

---

### Post by kansasnoob on 2010-05-15
I went ahead and basically copied my Ayatana question:

[https://answers.launchpad.net/ayatana-ubuntu/+question/110648](https://answers.launchpad.net/ayatana-ubuntu/+question/110648)

into an email to "ayatana at lists dot launchpad dot net"

We'll see what happens :)

---

### Post by kansasnoob on 2010-05-16
Well, that worked, at least to the degree that Mark Shuttleworth posted this reply:

> Michael Forrest, cc'd, is the right person to chat with about the install CD experience. Michael, could you reply on-list for everyone's benefit?


Anyone interested and not already a member might benefit by starting here:

[https://help.launchpad.net/ListHelp](https://help.launchpad.net/ListHelp)

---

