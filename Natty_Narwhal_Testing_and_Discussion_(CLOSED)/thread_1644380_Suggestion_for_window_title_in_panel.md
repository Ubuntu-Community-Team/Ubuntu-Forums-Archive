---
title: "Suggestion for window title in panel"
date: 2010-12-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2010-12-13
I commented on a suggestion for improving the implementing of window titles in the panel.

[https://bugs.launchpad.net/unity/+bug/657449/comments/3](https://bugs.launchpad.net/unity/+bug/657449/comments/3)

And suggestion? Usability pitfalls I'm missing?

Since my panel is for now totally borked could somebody give me a screenshot of the panel (with the menu and indicators) so I can make a mockup? Another thing that would be nice if you could use an app that has lots of menu items + start every app that has an indicator (that you have installed) so that I can see how it would look in the extreme case. Thanks!

---

### Post by kaldor on 2010-12-13
Basically, you want it like it is on OS X? I agree fully, since it can be frustrating when you aren't shown which window is displayed.

Screenshot is from OS X, I think it's what you're talking about anyway.

Edit: And [here's]("http://i.imgur.com/ffirV.png") a random screenshot from omgubuntu. My Unity is also borked at the moment, so I cannot get a good example.

---

### Post by zekopeko on 2010-12-13
> **kaldor said:**
> Basically, you want it like it is on OS X? I agree fully, since it can be frustrating when you aren't shown which window is displayed.

Screenshot is from OS X, I think it's what you're talking about anyway.

Not exactly although your suggestion to display app name is a good one.

I'm talking about the window title. That's the text that shows in the title bar (the part of the window where close,minimize,maximize controls live).

Since you are on a Mac now you can open Firefox or a folder and you should see the name of the page you are on or a folder you opened. That's what I'm talking about. In your example Chromium doesn't have it since tabs are taking the space of the window title so in essence tabs are the window title.

EDIT: BTW the fade effect tabs have in your Chromium is exactly what I think of when I talk about fade effect in my bug comment.

---

### Post by kaldor on 2010-12-13
So you'd basically want to have in the panel the fade effect the Chromium tabs have going on? It'd be useful, but if that's what you mean I can see it getting very cluttered.

---

### Post by zekopeko on 2010-12-13
> **kaldor said:**
> So you'd basically want to have in the panel the fade effect the Chromium tabs have going on? It'd be useful, but if that's what you mean I can see it getting very cluttered.

For now they want to have the window controls and the window title in the panel. When you mouse over the panel you get the menu. The problem as I see it is that it's not obvious there is a menu there until you mouse over it. My solution would only display 1.5 or 2.5 menu entries then have a fade effect, and then the window title (that would be shortened if it's too big for the panel) and then the indicators. When you mouse over my version of the panel (since you saw the first 1.5-2.5 menu items) the fade effect would simply "eat" the window title and display all the menu items. You move the mouse out of the panel and the fade effect "eats" the menu items again and the window title returns to it's fullness.

I think I'm just going to do a mockup to better explain myself.

---

### Post by kaldor on 2010-12-13
Ahh, right. I'm slow in the mornings ;)

Yeah, that could be a decent idea. It might cause a bit of confusion at first, but I don't see anything wrong overall.

---

### Post by zekopeko on 2010-12-13
Ok here is what I had in mind but prettier:

[http://i.imgur.com/T6tV7.png](http://i.imgur.com/T6tV7.png)

---

### Post by knarf on 2010-12-15
> **zekopeko said:**
> I commented on a suggestion for improving the implementing of window titles in the panel.

[https://bugs.launchpad.net/unity/+bug/657449/comments/3](https://bugs.launchpad.net/unity/+bug/657449/comments/3)

And suggestion? Usability pitfalls I'm missing?

Since my panel is for now totally borked could somebody give me a screenshot of the panel (with the menu and indicators) so I can make a mockup? Another thing that would be nice if you could use an app that has lots of menu items + start every app that has an indicator (that you have installed) so that I can see how it would look in the extreme case. Thanks!
I guess you mean something like [this image]("http://ubuntuforums.org/showpost.php?p=10157038&postcount=30")? You get that for free when using a tiling window manager like Xmonad. It does make sense in a tiling context where it is generally clear which window is in focus, especially when using full-screen windows :-). As to its utility in an overlapping window context I am not really convinced as there is no fixed relation between the windows and the panel.

---

### Post by ronacc on 2010-12-15
One of the things I find annoying about the OSX interface is that the window title and menus are in the panel rather than in the border where they "should" be . Having the window title and menus in the panel only makes any sense with a full screen window . The title and menus should always maintain the same position relative to the window in question not the screen as a whole If I have say 4 small window open on my DT and am moving between them i t makes less sense to go to the top of the screen for a menu than the top of the window itself .see screenshot .

---

### Post by zekopeko on 2010-12-15
> **knarf said:**
> I guess you mean something like [this image]("http://ubuntuforums.org/showpost.php?p=10157038&postcount=30")? You get that for free when using a tiling window manager like Xmonad. It does make sense in a tiling context where it is generally clear which window is in focus, especially when using full-screen windows :-). As to its utility in an overlapping window context I am not really convinced as there is no fixed relation between the windows and the panel.

No, I'm not talking about that. Here is a revised version in the attachment. I'm trying to address the issue of when an app is maximized its title bar is in the panel but since there is already the menu there the bug I linked to proposes that only the title of the window is present and menu only when you mouse over it. My solution makes the title visible and part of the menu so you can see there is one and you don't need to wonder where did the menu go.

---

### Post by ronacc on 2010-12-15
where would the title and menus be in a situation like in my screenshot with multiple small windows ?

---

### Post by zekopeko on 2010-12-15
> **ronacc said:**
> where would the title and menus be in a situation like in my screenshot with multiple small windows ?

This is about maximized windows so it's out of scope of what I'm addressing.

---

### Post by ronacc on 2010-12-15
sorry I thought you meant windows in general .

---

### Post by kyleabaker on 2010-12-15
> **zekopeko said:**
> This is about maximized windows so it's out of scope of what I'm addressing.

I get what you're suggesting, but I think it will only clutter the panel. I think the current plan is to add the app name to the left of the menu in the panel exactly like in OS X. I've seen plenty of bugs regarding the design of this on launchpad. I'm not sure when it will show up in Natty, but it will likely be before alpha 2.

Currently, I have dual screens and the top panel spans both screens. I love this since it makes the window position consistent and would allow for plenty of room for your idea, but on smaller screens there won't be much extra space for the window title and it will only be ugly clutter.

---

