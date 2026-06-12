---
title: "Firefox wont re-open previous session"
date: 2011-02-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Jonny87 on 2011-02-25
I'm one for having lots of tabs open and I usually close firefox and save all tabs so that they open next time. However since upgrading, ff 4.0 always opens a new session and I have to go History-> Restore Previous session, every time I open firefox. this is getting really annoying and frustrating. Does anyone have any solutions?

---

### Post by seeker5528 on 2011-02-25
If you save the tabs, then should I take it that you didn't go to....

Edit --> Preferences --> General --> Startup --> When Firefox starts:

.... and select 'Show my windows and tabs from last time' in the drop down box?

Later, Seeker

---

### Post by sgage on 2011-02-25
> **Jonny87 said:**
> I'm one for having lots of tabs open and I usually close firefox and save all tabs so that they open next time. However since upgrading, ff 4.0 always opens a new session and I have to go History-> Restore Previous session, every time I open firefox. this is getting really annoying and frustrating. Does anyone have any solutions?

You need to go to about:config and set the following booleans to true:

browser.tabs.warnOnClose

browser.warnOnQuit

browser.warnOnRestart

For some reason, they decided on different defaults with the last beta.

I'm now trying to figure out how to fix the find function. As soon as you switch tabs or reload the page, it goes away, though at least it remembers the search term. But I like it to stay there. I will mess around with about:config settings until I get it figured out.

---

### Post by zika on 2011-02-25
> **sgage said:**
> But I like it to stay there.
I do not. But, nevertheless, I wish You a good hunt...

---

### Post by sgage on 2011-02-25
> **zika said:**
> I do not. But, nevertheless, I wish You a good hunt...

It's mostly for one site that I spend a lot of time on. New posts are marked with a [new] tag, and I like to be able to work with my other tabs, go periodically go back to the site and reload, and scan for [new] without having to bring up the find bar again. I probably wouldn't care other than that.

---

### Post by Jonny87 on 2011-02-25
> **seeker5528 said:**
> If you save the tabs, then should I take it that you didn't go to....

Edit --> Preferences --> General --> Startup --> When Firefox starts:

.... and select 'Show my windows and tabs from last time' in the drop down box?

Later, Seeker

Thanks, I did search through the preferences but I don't know why I didn't notice that.

---

