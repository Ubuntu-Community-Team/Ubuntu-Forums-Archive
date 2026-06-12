---
title: "Link to control center in session indicator?"
date: 2011-03-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-03-12
[IMG]http://img.xrmb2.net/images/608490.png[/IMG]

Why is this placed there?

```
Lock Session     -> change of system state
Guest Session    -> change of system state
Switch From User -> change of system state
Log Out          -> change of system state
Suspend          -> change of system state
Hibernate        -> change of system state
Restart          -> change of system state
Shut Down        -> change of system state
Control Center   -> change of system configuration <- WTF???
```

---

### Post by Sashin on 2011-03-12
Maybe it does make sense, since everything changes the system in that menu. However, in any case it shouldn't be at the bottom, maybe the top. Its somehow feels harder to get to shutdown now...

---

### Post by lucazade on 2011-03-12
Really strange :/
I hope control center will be included in Unity dash (like apps and folder/files)

---

### Post by macroshaft on 2011-03-12
We really do need all the admin and preference applications grouping together in one place like this, it makes no sense to just heap them in with everything else. I'm not so sure on the placement of it mind you.

---

### Post by anders_c_ on 2011-03-12
I actually really like shuffling them in with the other applications. For example if I want to change my mouse sensitivity I just hit the unity key and type "mouse", no need to go through the control center.
And I strongly dislike having it in the indicator-session, thats not where i would look for it and doesn't feel intuitive at all:(

---

### Post by garvinrick4 on 2011-03-12
Ok with me if have another way to get to control center. Using docky right now to make
sure I can get places if having problems during Alpha's. Can stay where it's at forever
for myself.

---

### Post by macroshaft on 2011-03-12
> **anders_c_ said:**
> I actually really like shuffling them in with the other applications. For example if I want to change my mouse sensitivity I just hit the unity key and type "mouse", no need to go through the control center.
And I strongly dislike having it in the indicator-session, thats not where i would look for it and doesn't feel intuitive at all:(

I didn't say we should un-tangle them from the unity menu, it's great that you can just go for the app you want but what if you don't know what options you can choose from? You still need a place where you can browse the system apps and only the system apps.

---

### Post by scradock on 2011-03-12
I have a brilliant idea! Why doesn't someone create a device called a "menu" that can be accessed by clicking in the (currently completely non-functional) top panel, containing items like "system", "Preferences" and "Administration"?

Wouldn't that be cool?

---

### Post by MacUntu on 2011-03-12
> **scradock said:**
> Wouldn't that be cool?

Log out, log in to the classic session, and leave the cool people alone. ):P

---

### Post by ktp on 2011-03-12
> **MacUntu said:**
> Log out, log in to the classic session, and leave the cool people alone. ):P

:lolflag:

---

### Post by KrazyPenguin on 2011-03-12
> **scradock said:**
> I have a brilliant idea! Why doesn't someone create a device called a "menu" that can be accessed by clicking in the (currently completely non-functional) top panel, containing items like "system", "Preferences" and "Administration"?

Wouldn't that be cool?

Or if your using Natty <superkey><a> and choose from the "drop-down list on the right of the dash", in case you DO NOT know what you were looking for!!!!

Otherwise type in one to two letters of the app and click it to open.

Or if you use the app all the time you can add it to the "Rocket" Launcher on the left, or you can click on the "Re: Link to control center in session indicator?" (if you remember it is there?)  

Or you can open a terminal and use that

Or you can log out and back into classic desktop

Or you can you Lucid/Maverick

Or even another distro

Lots O choices, I don't see the problem!!!


;-)

---

### Post by mc4man on 2011-03-12
[https://bugs.launchpad.net/ayatana-design/+bug/727823](https://bugs.launchpad.net/ayatana-design/+bug/727823)

---

### Post by MacUntu on 2011-03-12
Thanks a lot for that link. At least now I know where to look to remove that entry. :P

[https://bugs.launchpad.net/ayatana-design/+bug/727823/comments/16](https://bugs.launchpad.net/ayatana-design/+bug/727823/comments/16)

Finding that chat is the next task! :D

---

### Post by cariboo on 2011-03-12
The original intent was to but the control center option in the Me menu, The discussion is still ongoing in the Ayatana mailing list, so the location may change yet. I haven't used gnome-shell in a few weeks, but the control center was in the session menu there too.

---

### Post by macroshaft on 2011-03-12
> **cariboo907 said:**
> The original intent was to but the control center option in the Me menu, The discussion is still ongoing in the Ayatana mailing list, so the location may change yet. I haven't used gnome-shell in a few weeks, but the control center was in the session menu there too.

It would make sense for this to be in the same location in both gnome shell and unity. At least then new adopters would easily be able to find it regardless of which distros they are using.

---

### Post by scradock on 2011-03-12
> **KrazyPenguin said:**
> Or if your using Natty <superkey><a> and choose from the "drop-down list on the right of the dash", in case you DO NOT know what you were looking for!!!!



;-)

Thanks for that hint - hadn't noticed that one. I've been doin' all the other suggestions, but it did begin to seem that adding a WORKING MENU somewhere would be a step forward......

---

### Post by mc4man on 2011-03-12
> **MacUntu said:**
>  At least now I know where to look to remove that entry. :P
:D
After taking a look at the .diffs - so simplistic. Now that the mechanism has been added  it may prove  be of some value down the road
(for the heck of it added a few entries to the indicator  to test - interesting...

---

### Post by ktp on 2011-03-12
> **mc4man said:**
> [https://bugs.launchpad.net/ayatana-design/+bug/727823](https://bugs.launchpad.net/ayatana-design/+bug/727823)

yep thanks for the link...when I saw this, it really looked out of place and I really wanted to remove it.  Now it can be. =)

---

### Post by PaulW2U on 2011-03-14
And with the latest update the menu entry is now called "System Settings".

To me it still seems to be in the wrong place though. Would be it better at the top of the menu I wonder?. :confused:

---

### Post by KrazyPenguin on 2011-03-14
> **PaulW2U said:**
> And with the latest update the menu entry is now called "System Settings".

To me it still seems to be in the wrong place though. Would be it better at the top of the menu I wonder?. :confused:

I agree!!!

The bottom should be "Shut Down", it was put there for a reason previously.

I really think this "System Settings" should be put in the launcher of on the dash, anywhere but where they decided to put it.

---

### Post by KrazyPenguin on 2011-03-14
OK the thing that really doesn't make sense is you click on "System Settings" and the "Control Panel" comes up.

Shouldn't these two things have the same name???

Or am I missing something??

lol

---

### Post by mc4man on 2011-03-14
> **KrazyPenguin said:**
> OK the thing that really doesn't make sense is you click on "System Settings" and the "Control Panel" comes up.

Shouldn't these two things have the same name???

Or am I missing something??

lol

Well they just made a change to the display name of the .desktop - I guess it wasn't considered too important to change the window display name - though quite simple - screen

---

