---
title: "Mythbuntu artwork messes with aspect ratio"
date: 2007-11-20
forum: Mythbuntu
---

### Post by Daminator on 2007-11-20
This doesn't seem to make sense to me, but Mythbuntu artwork seems to mess up Myth's aspect ratio.

I have a 16/9 projector but I can only output 4/3 resolutions from my system to my projector (for some reason that I can't fathom). To compensate, I use a DisplaySize line in my xorg.conf file (following instructions I found in Myth documentation). This worked fine before I added Mythbuntu. After Mythbuntu, it stopped working. The Myth frontend looked fine, but as soon as I went into 'Watch TV' (in any user, not just a mythbuntu session) the screen would be squashed and I'd have to select 4/3 for it to display correctly on my 16/9 display. Weird.

Simply unticking the check box next to Mythbuntu artwork fixes the problem.

So, my system is fine again now, but I thought I'd mention the problem for the sake of the developers.

One question I do have .. Now that I've removed Mythbuntu sessions, how can I get rid of the icons (floppy drive etc) that are on the desktop when I select standard Xfce?

Cheers

Damian

---

### Post by foxbuntu on 2007-11-20
> **Daminator said:**
> This doesn't seem to make sense to me, but Mythbuntu artwork seems to mess up Myth's aspect ratio.

I have a 16/9 projector but I can only output 4/3 resolutions from my system to my projector (for some reason that I can't fathom). To compensate, I use a DisplaySize line in my xorg.conf file (following instructions I found in Myth documentation). This worked fine before I added Mythbuntu. After Mythbuntu, it stopped working. The Myth frontend looked fine, but as soon as I went into 'Watch TV' (in any user, not just a mythbuntu session) the screen would be squashed and I'd have to select 4/3 for it to display correctly on my 16/9 display. Weird.

Simply unticking the check box next to Mythbuntu artwork fixes the problem.

So, my system is fine again now, but I thought I'd mention the problem for the sake of the developers.


Could you file a bug against this so we can track it?
[https://bugs.launchpad.net/mythbuntu/+bugs](https://bugs.launchpad.net/mythbuntu/+bugs)

> 
One question I do have .. Now that I've removed Mythbuntu sessions, how can I get rid of the icons (floppy drive etc) that are on the desktop when I select standard Xfce?


You should be able to either delete them as any other icon, or edit the Xfce settings via them menu.

---

### Post by Daminator on 2007-11-20
Bug reported,

Thanks

---

