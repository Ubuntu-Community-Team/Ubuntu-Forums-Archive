---
title: "New scrollbars?"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2011-04-18
New mouseover scrollbars seem to have been added to applications now.Move mouse over to the right and they appear.

I hate them, what do you people think about it?

---

### Post by lucazade on 2011-04-18
> **rajeev1204 said:**
> New mouseover scrollbars seem to have been added to applications now.Move mouse over to the right and they appear.

I hate them, what do you people think about it?

I like them, very well coded and designed.
Only issues I see at the moment are the lack of support in qt and hydrid gtk apps like ff and chrome and middle clicking feature.

---

### Post by rajeev1204 on 2011-04-18
> **lucazade said:**
> I like them, very well coded and designed.
Only issues I see at the moment are the lack of support in qt and hydrid gtk apps like ff and chrome and middle clicking feature.


How can i disable them?

---

### Post by Hogashi on 2011-04-18
You can try this:
[http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html](http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html)

---

### Post by rajeev1204 on 2011-04-18
> **Hogashi said:**
> You can try this:
[http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html](http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html)


I tried this but its still the same.

---

### Post by lucazade on 2011-04-18
> **rajeev1204 said:**
> I tried this but its still the same.

sudo apt-get remove overlay-scrollbar

---

### Post by rajeev1204 on 2011-04-18
> **lucazade said:**
> sudo apt-get remove overlay-scrollbar


ah thanks, that was easy. I had to log out and back in again to see the change.

---

### Post by SevenMachines on 2011-04-18
with all the talk about unity and gnome3, i think the new scrollbars are the thing i've noticed most, strange though it seems! eclipse is a riot of scrollbars at any time and it now looks a lot more sleek and less 'cramped', the small things can make a big difference :)

---

### Post by TragicWarrior on 2011-04-26
Thanks to whoever posted this fix.  I HATE THESE STUPID OVERLAY SCROLLBARS !!!  Obviously the person who designed them didn't have to sort through hundreds of emails in Evolution.  UGH!!!

---

### Post by teachop on 2011-04-26
They don't work in my programming editor of choice, Code Blocks.  Artifacts are left in the text area when scrolling vertically.  The artifacts are remnants of the horizontal scroll bar that don't get properly erased.  I had no choice but to disable them.

---

### Post by MacUntu on 2011-04-26
> **teachop said:**
> They don't work in my programming editor of choice, Code Blocks.  Artifacts are left in the text area when scrolling vertically.  The artifacts are remnants of the horizontal scroll bar that don't get properly erased.
Have you filed a bug report?

---

### Post by mafitzpatrick on 2011-04-26
Since they were first implemented they have been intermittently broken for me - they appear when the mouse goes to the edge of the window, but once I try and move the mouse actually onto the scroller they disappear... infuriating. Thankfully I've got a scroll wheel on the mouse! Each update  break, fix, break, fix so filing a bug report seemed a little futile. On the upside, testing today they're working! Hope they don't update too much for the final release ;)

In a usability sense I'm not convinced. When scrolling small distances I use the scroll wheel - the scroll bar is for moving a long way down the document. On a standard scroll bar you can move the mouse down to the bottom-right window and just click-click-click to the general area, and adjust with the scroll wheel. With the new overlays you have to look for the small orange bar, move the mouse to that exact spot, then click and drag all the way down.

Try moving through a long folder (/etc as an example) ...it's slower no question. Admittedly part of this is probably years of habit meaning that by default I go to the wrong place on the bar, but in general it requires more precise targeting - the exact opposite of the reasoning behind the global menu etc. Seems inconsistent, unless I'm missing something.

It is pretty though.

---

### Post by teachop on 2011-04-26
> **MacUntu said:**
> Have you filed a bug report?
No I just punted on that one at the time.  I will re-enable them and if it isn't fixed already or reported already, collect data and start a bug report.

---

### Post by aaaantoine on 2011-04-26
I like them so far, at least in theory.  I practically never drag the scrollbar manually, but at the same time I like the fact that they come with a fade-in grab handle.

One little nitpick I've noticed is that they can interfere a bit with the right-edge resize area.

Another is that, though perhaps not related, the corner grab handle looks terrible.  I think it might need a bit of alpha-mapping to blend in better.  Though even then, it doesn't fix the issue of the grab handle occasionally overlapping an application control.

---

### Post by mc4man on 2011-04-26
> **teachop said:**
> No I just punted on that one at the time.  I will re-enable them and if it isn't fixed already or reported already, collect data and start a bug report.
as far as code blocks and related, likely here
[https://bugs.launchpad.net/ayatana-scrollbar/+bug/769232](https://bugs.launchpad.net/ayatana-scrollbar/+bug/769232)

---

### Post by Merk42 on 2011-04-26
> **TragicWarrior said:**
> Thanks to whoever posted this fix.  I HATE THESE STUPID OVERLAY SCROLLBARS !!!  Obviously the person who designed them didn't have to sort through hundreds of emails in Evolution.  UGH!!!How do the overlay scrollbars make sorting emails in Evolution (presumably) difficult/impossible?

---

### Post by areteichi on 2011-04-26
The only issue I have with it is that I can't hold down the arrows to scroll by small increments. I either have to click or drag the scrollbar itself. If they fix this, I will very much be satisfied.

---

### Post by tekstr1der on 2011-04-26
I enjoy having the scrollbars take up less real estate on my small(ish) laptop screen. I rarely scroll by grabbing a scrollbar with my pointer, so the new overlay scrollbars are nicely out of the way.

With maximized windows, one issue I've noticed is that if I do try to grab a scrollbar with the pointer, the pointer needs to be moved 1 or 2 pixels inward from the edge of the screen in order for the scrollbar to be grabbed. This is another Fitts' Law issue and a usability problem.

This could present real difficulty for users without a scrollwheel, touchpad or other means of mechanical scrolling.

---

### Post by aaaantoine on 2011-04-26
> **tekstr1der said:**
> With maximized windows, one issue I've noticed is that if I do try to grab a scrollbar with the pointer, the pointer needs to be moved 1 or 2 pixels inward from the edge of the screen in order for the scrollbar to be grabbed. This is another Fitts' Law issue and a usability problem.
Maybe true, but...

> **tekstr1der said:**
> This could present real difficulty for users without a scrollwheel, touchpad or other means of mechanical scrolling.
If you have neither of those things at your disposal and are using anything remotely resembling a modern computer, you are sorely deprived.  A USB mouse with scroll wheel costs 10 bucks.  Get one.

And if you're on one of those laptops that only has the nub pointer, well... A USB mouse with scroll wheel costs 10 bucks. :P

---

### Post by mc4man on 2011-04-26
> **areteichi said:**
> The only issue I have with it is that I can't hold down the arrows to scroll by small increments. I either have to click or drag the scrollbar itself. If they fix this, I will very much be satisfied.
For line  you may just need to do w/ a scroll (scroll area or scrollwheel) or w/ an arrow key.
Atm I believe the arrows on the thumb are doing a page up/page dn, maybe based on list of priorities?
> To have a solution which would embrace touch input devices, some of the functionalities available on cursor driven solutions might have to go. For this reason we prioritized the scrolling functionalities (from the more important to the least):

    Scrolling via mouse wheel (or dragging content on touch devices)
    Scrolling via thumb
    Page up/down
    Jump to position via bar
    Line up/down


---

### Post by teachop on 2011-04-26
I tend to click inside the scrollbar, but not on the thumb.  Example, if I want to page up, I hit the big target and click above the thumb, I don't drag it.  These new scrollbars are not set up really well for that.

---

### Post by sgage on 2011-04-26
> **teachop said:**
> I tend to click inside the scrollbar, but not on the thumb.  Example, if I want to page up, I hit the big target and click above the thumb, I don't drag it.  These new scrollbars are not set up really well for that.

Ditto.

---

### Post by pauljwells on 2011-04-26
> **areteichi said:**
> The only issue I have with it is that I can't hold down the arrows to scroll by small increments. I either have to click or drag the scrollbar itself. If they fix this, I will very much be satisfied.

My thoughts exactly, although I *can* just hit the pagedown key on my keyboard and it does exactly that...

To start with I thought they were stupid. Now I've got used to them I feel disappointed when 'old-style' scroll bars show up in an application.

---

### Post by mc4man on 2011-04-26
> **pauljwells said:**
> My thoughts exactly, although I *can* just hit the pagedown key on my keyboard and it does exactly that...

The little arrows on the thumb currently do page up/down , the OP wants them to do line up/down (maybe), probably not going to happen (and one can use the keyboard arrows for that

One could try filing a bug that a click and hold on the arrows should keep advancing rather than repeated clicks

---

### Post by areteichi on 2011-04-26
> **mc4man said:**
> One could try filing a bug that a click and hold on the arrows should keep advancing rather than repeated clicks

Such a request has already been reported (with many duplicates :P):
[https://bugs.launchpad.net/ayatana-scrollbar/+bug/736592](https://bugs.launchpad.net/ayatana-scrollbar/+bug/736592)

---

### Post by mc4man on 2011-04-26
> **areteichi said:**
> Such a request has already been reported (with many duplicates :P):

I was just reading that bug a few min. ago - so it's not in the design plan. ( and doesn't sound like will be

---

### Post by DogMatix on 2011-04-26
Personally I like it. Works well on a 10" screen netbook with touchpad or a Wacom Bamboo.

---

### Post by seeker5528 on 2011-04-27
> **mc4man said:**
> The little arrows on the thumb currently do page up/down , the OP wants them to do line up/down (maybe), probably not going to happen (and one can use the keyboard arrows for that

One could try filing a bug that a click and hold on the arrows should keep advancing rather than repeated clicks

If the little arrows were actually separate zones that could be acted on differently that the other parts of of the thumb I could see making it so holding the mouse button down would scroll the page.

But as it is now, clicking one half pages one direction, clicking the other half pages the opposite direction, scrolling when you hold down the mouse button doesn't make sense to me.

Personally I would rather have two larger targets without scroll zones to hit than four small ones with.

Are people really finding it that difficult to grab and drag?

Later, Seeker

---

### Post by areteichi on 2011-04-27
> **seeker5528 said:**
> Are people really finding it that difficult to grab and drag?

Imagine reading a PDF file (in evince) that is more than 300 pages long. A short drag will easily scroll multiple pages at once and thus makes the dragging utterly useless.

---

