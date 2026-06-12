---
title: "Odd behavious with firefox and copy/paste"
date: 2010-12-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2010-12-16
Ever since I upgraded to natty scrolling in firefox doesn't work if you click on the scrollbar and drag. It gets bored and decides to throw you to a random extreme of the page and refuses to let you move to where you want unless you click on the arrows at the edge of the scrollbar to move. Also it keeps randomly decided a tab should be closed sometimes if I left click on it. Another bad habit is that it becomes obsessed with some pages sometimes, say, for instance I visit ebay and then later come on here he browse posts. It just suddenly decides to load that ebay page up again with no warning and will do this several times.

Copy and paste seems to decide to randomly past things I have typed into search boxes but never copied. At the moment 'BT Infinity is being pasted into my word document I'm editing whenever I left click on the page!

Is anyone else experiencing these issues and does anyone know why Ubuntu has suddenly got such a bad attitude?

---

### Post by chrismine on 2010-12-16
Natty at the moment is like a child trowing his toy's out of the cot - panels crashing, desktop icons not showing, right clicking works on a whim, and update manger loosing interest...

---

### Post by macroshaft on 2010-12-16
Sounds like we're both babysitting the same child! Do you think we can have it potty trained in time for release?

---

### Post by cariboo on 2010-12-16
I don't use Firefox often, but when I do I don't have any problems with scrolling or anything else. I seem to be have the same sorts of problems with chromium, although it's pretty intermittent.

---

### Post by chrismine on 2010-12-16
> **macroshaft said:**
> Sounds like we're both babysitting the same child! Do you think we can have it potty trained in time for release?

With the help of the Ubuntu Dev's I think so - they seem to perform miracles the nearer it get to release date...

I must say this is the most "unstable" development release IMHO and I started with Hardy!

---

### Post by seeker5528 on 2010-12-16
> **macroshaft said:**
> Ever since I upgraded to natty scrolling in firefox doesn't work if you click on the scrollbar and drag. It gets bored and decides to throw you to a random extreme of the page and refuses to let you move to where you want unless you click on the arrows at the edge of the scrollbar to move.

Firefox 4 seems to have a lot more cases where the UI becomes unresponsive while some other part of Firefox is busy. Seems to be worse if there is a lot of flash stuff in a page, maybe with java script as well.

If what you see is what I see, you could consider it to not be *randomly* throwing you to some extreme of the page. If the page is not loaded and you move the scroll bar when the page is not fully loaded to what would be 75% down the page for example, then there is a big delay processing that action, then a bunch more of the page loads, then the request is processed, 75% down the page may now be much further down than what it appeared it would be when you first tried to move the slider, and potentially if you tried to move the slider multiple times it may be processing multitple actions, and I believe if you page down by clicking below the slide button instead of dragging the slide button you may see something similar. You can get some idea if this is what seems to be the case by noting the size of the slide button before you try to slide it and noting the difference in size at the time you actually get some scrolling action on the page.

Don't know about the rest of the stuff. Except you say they happen when you left click, but sound like things you would expect with a middle click.

Middle clicking the content area of a page can cause something to pop up in a new tab, never understood the logic of what page would open or when this actually worked or didn't work.

If you are getting stuff when you left click that you should only see when you middle click, maybe there is something going on with your mouse?

Later, Seeker

---

### Post by macroshaft on 2010-12-16
> **seeker5528 said:**
> Firefox 4 seems to have a lot more cases where the UI becomes unresponsive while some other part of Firefox is busy. Seems to be worse if there is a lot of flash stuff in a page, maybe with java script as well.

If what you see is what I see, you could consider it to not be *randomly* throwing you to some extreme of the page. If the page is not loaded and you move the scroll bar when the page is not fully loaded to what would be 75% down the page for example, then there is a big delay processing that action, then a bunch more of the page loads, then the request is processed, 75% down the page may now be much further down than what it appeared it would be when you first tried to move the slider, and potentially if you tried to move the slider multiple times it may be processing multitple actions, and I believe if you page down by clicking below the slide button instead of dragging the slide button you may see something similar. You can get some idea if this is what seems to be the case by noting the size of the slide button before you try to slide it and noting the difference in size at the time you actually get some scrolling action on the page.

Don't know about the rest of the stuff. Except you say they happen when you left click, but sound like things you would expect with a middle click.

Middle clicking the content area of a page can cause something to pop up in a new tab, never understood the logic of what page would open or when this actually worked or didn't work.

If you are getting stuff when you left click that you should only see when you middle click, maybe there is something going on with your mouse?

Later, Seeker

My problem with scrolling always seems to take me to the bottom of the page and when I try to scroll back up it starts to go but then jumps back to the bottom again, over and over. As for the left click problems, I don't have a three button mouse, only a two button trackpad, so I CAN'T be middle clicking, lol

I've also noticed when the screensaver activates I often have either the taskbar and unity par on top of it, or the active window i.e. firefox. That's a new one on me!

---

### Post by seeker5528 on 2010-12-16
> **macroshaft said:**
> My problem with scrolling always seems to take me to the bottom of the page and when I try to scroll back up it starts to go but then jumps back to the bottom again, over and over. As for the left click problems, I don't have a three button mouse, only a two button trackpad, so I CAN'T be middle clicking, lol

There is an option to recognize simultaneous clicking of left and right mouse buttons (a mouse chord) as a middle click, which used to be the default, doesn't seem to be working for me at the moment, but maybe if it is recognized that you only have a 2 button mouse when you start X it will enable the mouse chord automatically. Don't know how likely it seems but at least seems possible that it could have something to do with the track pad.

I haven't seen the scrolling/jumping to the bottom thing with web pages, but some times if I click a folder on the bookmarks tool bar that doesn't fit on the screen and start scrolling that it will continue scrolling 'till it hits the bottom and keep jumping back to the bottom if I try to scroll upwards. After seeing this several times I finally figured out it was because the down arrow key on my keyboard sticks some times and tapping the down arrow key to unstick it stops the scrolling.

Later, Seeker

---

### Post by cariboo on 2010-12-16
Seeing as we are talking about odd firefox problems here, has anyone else notice the poor font rendering when creating posts? I've got the default fonts set.

---

### Post by chrismine on 2010-12-17
I am only seeing "funny" fonts when using Minefield, with Firefox 4 beta 7 it is fine and also with Google Chrome.

---

### Post by macroshaft on 2010-12-17
Am I the only person who finds this new firefox somewhat lacking? So far I have instinctively gone to click the reload button and also the little down arrow on the browse back button which displays the last x steps back. I think they should call this one Diet Firefox instead of Firefox 4!

---

