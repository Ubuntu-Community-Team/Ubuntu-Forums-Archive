---
title: "firefox 4"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-04-01
firefox wont work in middle search bar this is not on beta just daily build upgrade

---

### Post by mc4man on 2011-04-01
I see this on an install of 03/31 iso, are you saying it doesn't happen w/ the beta, or you're not using the beta?
Had filed bug on, if it's fine in the beta 1 iso then I'll mark the bug as invalid

[https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/745829](https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/745829)

---

### Post by rbrick49 on 2011-04-01
no I am not using beta just upgrade 1/4/2011

---

### Post by mc4man on 2011-04-01
> **rbrick49 said:**
> no I am not using beta just upgrade 1/4/2011

Well I'll leave the bug up then, there is something amiss with that version of the about:startpage

---

### Post by rbrick49 on 2011-04-01
yes its something in the about:start pge

---

### Post by bikeboy on 2011-04-01
Yeah I ran into that while running the i386 desktop beta live today. Tried it with the Firefox web console open but no errors or warnings appeared.

---

### Post by meanpt on 2011-04-01
I came here for the same: was going to update until I saw "Version 4.0~rc2+build3+nobinonly-0ubuntu2: " ... what the hell of a joke is this?:confused: ... better update the system tomorrow

---

### Post by rajeev1204 on 2011-04-01
true.does not search.Though i never use the home page.Just tried it once to check.


edit: just entered different words and it goes to launchpad.

---

### Post by mc4man on 2011-04-02
I think this is some kind of 'in between' deal, only see (saw) on recent 03/30 iso.

If you look closely you'll see  the search box is not the normal, it's more like the search box you'd see AFTER doing a search from about:startpage
(narrower and has that little google icon business

Anyway  - probably a bit more than needed but works fine here to fix - All your present firefox settings ect. will remain as is

```
sudo apt-get purge firefox*
```
Do read before saying yes
A _restart_, then 
```
sudo apt-get install firefox
```

(if you want to take a bit 'easier' then purge and re-install xul-ext-ubufox, see what that does
I did a restart between purging and re-installing just because..

---

### Post by andrewabc on 2011-04-02
I ran liveusb of firefox4 and I can't figure out where main menu is to change settings/addons etc.

---

### Post by rbrick49 on 2011-04-02
> **mc4man said:**
> I think this is some kind of 'in between' deal, only see (saw) on recent 03/30 iso.

If you look closely you'll see  the search box is not the normal, it's more like the search box you'd see AFTER doing a search from about:startpage
(narrower and has that little google icon business

Anyway  - probably a bit more than needed but works fine here to fix - All your present firefox settings ect. will remain as is

```
sudo apt-get purge firefox*
```
Do read before saying yes
A _restart_, then 
```
sudo apt-get install firefox
```

(if you want to take a bit 'easier' then purge and re-install 
xul-ext-ubufox, see what that does
I did a restart between purging and re-installing just because..
yes I did that  and the same thing happened my server repos might be behind i am using a singapore repo as it is faster than the Thailand ones I just did an update its ok now but now my terminal is only half there on unity I guess it will get better soon

---

### Post by Muskegman on 2011-04-02
Im currently running natty AMD64 beta1 on my laptop and the problem with the middle search bar not searching is not only a problem in natty, but also ive found it does the same thing in my kubuntu lucid and also in ubuntu meerkat. I resolved the issue by typing "start.ubuntu.com" in the upper right google text box and then going into firefox /preferences and selecting "use current page"

This has brought me back to a working middle text box in ubuntu start page again on all 3 of my OS's

---

### Post by mc4man on 2011-04-16
Seems to be a new variation w/ fresh beta2 updated install. This time the search works from default  'about:startpage' but the scrollbar disappears on the results page. (arrow key works

---

