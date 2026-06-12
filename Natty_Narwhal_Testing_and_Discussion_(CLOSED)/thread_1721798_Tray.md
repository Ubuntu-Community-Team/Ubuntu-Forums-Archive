---
title: "Tray"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nothingspecial on 2011-04-05
Is there some way to use the "tray"?

If I can't use thunderbird with firetray to notify me of emails and especially radiotray then unity is pretty much useless as far as I'm concerned.

---

### Post by mc4man on 2011-04-05
Well, I don't and have never used thunderbird/firetray other than the last 10 min, it can be added to the unity systray and does seem to work ok (keeping in mind I never used

One of the things you look for when adding something to the systray whitelist is does it work and does it mess anything else up. In this case it seems to work and does mess at least one thing up. (you'd need to do extended testing to see if anything else goes south _which is possible_

In this case it 'seems' that if using firetray that the thunderbird global menu will stop working after opening from the tray icon. It may be one or the other
2 screen show - it does show up and work and auto-notify of an email

There may be other options for this other than the systray in unity
If you wish to try I'll or someone can show how to add to whitelist if need be

Edit: didn't try radiotray - same deal, you add it and see what happens, if it works out you keep, if not you don't

---

### Post by nothingspecial on 2011-04-05
Couldn't get radiotray to work :(

It could be me though.

---

### Post by mc4man on 2011-04-05
> Couldn't get radiotray to work
It does work, (plus notifications and mouseover),  pay attention to how added if using dconf-editor or I'll post you a gsetting command

(used the 0.6.3 deb from the site

---

### Post by castrojo on 2011-04-05
Thunderbird is getting native indicator integration, which is probably what you want to use since it's being done by Mozilla:

[http://mikeconley.ca/blog/2011/03/15/my-campaign-to-get-thunderbird-integrated-into-ubuntu-natty-narwhal-continues/](http://mikeconley.ca/blog/2011/03/15/my-campaign-to-get-thunderbird-integrated-into-ubuntu-natty-narwhal-continues/)

---

### Post by tjeremiah on 2011-04-05
> **mc4man said:**
> Well, I don't and have never used thunderbird/firetray other than the last 10 min, it can be added to the unity systray and does seem to work ok (keeping in mind I never used

One of the things you look for when adding something to the systray whitelist is does it work and does it mess anything else up. In this case it seems to work and does mess at least one thing up. (you'd need to do extended testing to see if anything else goes south _which is possible_

In this case it 'seems' that if using firetray that the thunderbird global menu will stop working after opening from the tray icon. It may be one or the other
2 screen show - it does show up and work and auto-notify of an email

There may be other options for this other than the systray in unity
If you wish to try I'll or someone can show how to add to whitelist if need be

Edit: didn't try radiotray - same deal, you add it and see what happens, if it works out you keep, if not you don't
Oh wow, thanks :o . I never knew you could do this.

---

