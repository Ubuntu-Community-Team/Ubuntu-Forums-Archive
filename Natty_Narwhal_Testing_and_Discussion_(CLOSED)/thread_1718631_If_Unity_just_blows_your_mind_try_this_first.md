---
title: "If Unity just blows your mind try this first"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-03-31
Many people new to Natty may initially freak out at the new Unity UI. Not to worry!

Ubuntu has your back, haven't they always?

If you find yourself simply overwhelmed with the Unity interface you can still use either the Classic Desktop or Classic w/o effects. Just log-out using the power button in the upper right-hand corner of the screen or press Alt>SysReq>K and after clicking on your username you'll be able to select from the menu at the bottom of the login screen.

NOTE: If using the Live CD/USB you can do likewise, just accept the default username and enter no password.

If you prefer something other than the Unity desktop as your default you can change that in Login Screen Settings.

If you find that the global menu messes with your head look here in post #2 if you're using the classic desktop:

[http://ubuntuforums.org/showthread.php?p=10613605#post10613605](http://ubuntuforums.org/showthread.php?p=10613605#post10613605)

If you want to lose the global menu in Unity look at post #8 in the same thread, but I personally think it's unwise to remove packages at this point in development.

Ubuntu still has your back :D

Aside from the bugs you'd expect to find in a Beta you can test with a familiar UI and easily try Unity when you're feeling adventurous!

**Note**: As mentioned above, "I personally think it's unwise to remove packages at this point in development". Another thing I happened to think of is button placement. If you want the buttons on the right using the classic desktop I very highly recommend you choose another desktop theme, such as clearlooks, rather than editing gconf.

I added a bit about overlay scrollbars in post #2.

---

### Post by kansasnoob on 2011-04-07
**NOTE:** This is just something I began for those who upgrade to 11.04 and totally freak out over Unity, no doubt it needs a lot of work.

First of all I know that was a horrible title :(

My true goal was to accomplish a totally "retro" gnome experience so people didn't just jump ship and go distro-hopping :)

So, if you read through that first post, you'll see that I'm trying very hard to find ways of getting there w/o the need to remove or install any packages. 

You'll notice I even included a bit about choosing a different theme rather than editing gconf to move the buttons :)

Today came the addition of 'overlay-scrollbar' and I realize many people will love them but with my poor eyesight it was simply an obstacle to overcome.

For the moment I just removed the package but I'd prefer to find a way to avoid that if possible, any thoughts?

I use classic w/o effects so making adjustments to compiz is not an option.

I appears ATM that if the overlay scrollbars mess with your mind you must remove two packages:

overlay-scrollbar
liboverlay-scrollbar-0.1-0

---

### Post by davepoth on 2011-04-07
I also removed notify-osd as I don't like the way it looks. The only difference between my current and 8.04 desktop is that it's not brown any more...

---

### Post by mc4man on 2011-04-07
> For the moment I just removed the package but I'd prefer to find a way to avoid that if possible, any thoughts?

Don't see a way otherwise atm, if none is forthcoming then file a bug for requesting a gsetting, gconf, or gui config option
(likelihood of seeing such in natty if not currently present - slim to none

---

### Post by kansasnoob on 2011-04-07
> **davepoth said:**
> I also removed notify-osd as I don't like the way it looks. The only difference between my current and 8.04 desktop is that it's not brown any more...

Did you then install 'notification-daemon'?

I haven't bothered with that aspect of Natty yet :)

In another thread I mentioned that 'notify-osd' has never worked well for me. I can't see well, I need notifications to wait for me to respond, however long that may take ;)

---

### Post by kansasnoob on 2011-04-07
> **mc4man said:**
> Don't see a way otherwise atm, if none is forthcoming then file a bug for requesting a gsetting, gconf, or gui config option
(likelihood of seeing such in natty if not currently present - slim to none

No doubt once gnome3 rolls out the challenge of obtaining a retro gnome-based desktop will be even worse. I guess they've already added a "gnome-panel" option back in Fedora 15 but I lack the time and desire to look into what Fedora is doing ATM :)

I suppose for those in my boat just removing that one package won't break unity too awful bad. My thought is that I want to be able to keep testing unity, but revert almost flawlessly to classic (with or without effects) to actually get work done.

I'm hardly worried, in fact Lubuntu is becoming a truly viable alternative :guitar:

---

### Post by mc4man on 2011-04-07
the overlay scrollbar isn't unity specific or even 'effects' related
(haven't bothered to look at the source to see how it's implemented.

Slightly ot, it would not surprise me to see some things about unity, (features, options),  cut back by release to gain some stability
Hopefully one thing that has been missing for a bit - the nautilus appmenu on desktop focus, will be returned, it can be very handy when not using maxed windows

---

### Post by rbrick49 on 2011-04-08
very good kansasnoob

---

