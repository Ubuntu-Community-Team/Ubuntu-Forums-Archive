---
title: "Mouse weirdness"
date: 2011-01-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-01-21
Has anyone else noticed that when clicking something is the area the dash opens up in that at times mouse clicks don't work? If I move the app out of that area then  the click, whether regular or right click works. I have tis behavior two different systems so far.

---

### Post by Quackers on 2011-01-21
I'm getting a similar kind of thing in some instances.
In synaptic I can only highlight the top or bottom option in upgradeable (for instance) and then need to use the up down arrows to get to one in the middle.
In Firefox one or two of my bookmarks toolbar are only clickable after a few tries, and usually only in one or two areas of the tab.

---

### Post by mc4man on 2011-01-21
> Has anyone else noticed that when clicking something is the area the dash opens up in that at times mouse clicks don't work? 

Very interesting observation, that accounts for a lot of odd behavior inc. if one used the r. click "Organize Desktop..."  - items placed in that area become non addressable
(will have to edit bug on

if you manually try to drag and drop to that area, you can't..

---

### Post by Quackers on 2011-01-21
This started happening for me after yesterdays updates. Occasionally the first 2 of my Firefox bookmark toolbar items are completely unclickable. They don't even get the shadow around them when I mouse over them. It's as if they aren't there at all.
At other times they are clickable, but only in specific areas of the tab.
Sometimes I can't open a new tab at all. The green plus sign is unclickable.
Also, sometimes when clicking and dragging (to highlight contents of a file for pasting somewhere else) the highlighted area starts much later than where I held down the left click, and I need to do it again. This also started yesterday iirc.

---

### Post by mc4man on 2011-01-21
> Occasionally the first 2 of my Firefox bookmark ....
try maximizing firefox (or any mis-behaving window) or if screen is large enough moving to the right and down a bit.
(also note that mouse grab on unmaximized windows can be a bit buggy atm

---

### Post by Quackers on 2011-01-21
My problems arise when FF windows are maximised. I almost never use them any other way tbh.

---

### Post by ronacc on 2011-01-21
I've had strange behavior with the mouse in the panel on the classic desktop for several days , to get the menus to drop down the cursor has to be carefully centered on the word, eg: system you have to hit the second s or the t , once the dropdown menus are there they work normally, also program menus are normal .

---

### Post by MacUntu on 2011-01-21
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/705672](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/705672)

---

### Post by Quackers on 2011-01-21
Interesting! Thanks. How on earth does that happen?

---

### Post by cariboo on 2011-01-21
Thanks MacUntu, I added my me too, and subscribed.

---

### Post by ratcheer on 2011-01-21
I think I just encountered the same thing. I was in another web forum on a page with a bunch of links to posts. The link at the top would not accept a click, nor would the mouse pointer change when hovered over it. All the posts that were lower on the page worked just fine. I thought something was wrong with the web page, but I bet it is the same as your problem.

I will add myself to the bug report.

Tim

---

### Post by Quackers on 2011-01-21
I am having that too, but my main sticking point is in something like synaptic, where I can't click on anything other than the top or bottom item in any list. Then I can move the highlighted item with the up/down arrow keys. It doesn't allow a click on any of the items in the middle of any list at all.

---

### Post by cariboo on 2011-01-21
@Quackers, I can click near the center, towards the end of the line in synaptic to get it highlighted, see screen shot.

---

### Post by Quackers on 2011-01-21
> **cariboo907 said:**
> @Quackers, I can click near the center, towards the end of the line in synaptic to get it highlighted, see screen shot.

Curiously, I can't do that. The only items I can click on and highlight are the top one and the bottom one in any list. :confused:

Wow, that's weird!  Now I can click on anything in synaptic window and it highlights ok - but can't click on the red x to close the window :-)  It's there, but I can't click on it!

---

### Post by Quackers on 2011-01-21
An update!
It's definitely something to do with that dead zone, top left. If I move an unmaximised window down and right, I can click on anything in the window. If I move the window high and left I have problems again.
Looks like part of the bug already logged then. At least for mine.

---

### Post by kaehny on 2011-01-21
Seconded. I had to quit Firefox twice to actually use any menu drop down. The problem has not recurred lately though.

---

### Post by jerrylamos on 2011-01-21
With today's updates, Jan 21, I opened Firefox O.K.  Ran O.K. until I tried to mouse select anything example File Edit View History Bookmarks ... you name it.  Then even the items in the top bar wouldn't select, example the power switch.  And Ctrl-Alt-Del didn't either.

Oh, well, it's an "Alpha" so I did power off/on and logged in with classic desktop no effects.  It's ati radeon xpress 200 which does have the hardware.

Anyone have any idea how I could "wake up" Unity to mouse selections?

Thanks, Jerry

---

### Post by cariboo on 2011-01-21
@jerrylamos, I've found that when I run into something similar to your problem, a right click on the the desktop seems to solve the problem. It was very  intermittent, but with updates I don't seem to have that problem any more.

---

### Post by MacUntu on 2011-01-22
What I currently do after the boot is to restart compiz (via an icon on the desktop) and then open the dash - that seems to get rid of all the weird problems (launcher bar hiding on right-click, menus/dropdown lists not opening, etc.).

---

### Post by terry_gardener on 2011-01-22
this happening to me it is really annoying

---

### Post by VMC on 2011-01-22
After todays  zsync install, when I played solitaire, which I normally play as a  check, there were/are slots on the upper card holder that the mouse  wouldn't recognize. Never had that before. Usually what happens is I  can't check statics, unless I touch something on the desktop, but this  one was/is weird. I somehow think its strangely related to this topic.
 		                   		  		  		 		 			 				__________________

---

### Post by Funnnny on 2011-01-22
I found a solution for this, just click on the dash and click again to close it :) Problem solved

---

### Post by garvinrick4 on 2011-01-23
#2 installs and have to open nautilus /usr/share/applications
to make mouse behave with right click function and applets.
As of 1-22-11 11:30 pm using mirror.anl-gov United States.

---

### Post by castrojo on 2011-01-24
[https://launchpad.net/ubuntu/natty/+source/unity/3.2.14-0ubuntu2](https://launchpad.net/ubuntu/natty/+source/unity/3.2.14-0ubuntu2)

Yay! Fix was uploaded.

---

### Post by mc4man on 2011-01-24
>  Fix was uploaded.
That's great - while just using the dash once per session didn't represent any significant 'loss' of memory, I'd prefer not to open it at all till that's fixed.

---

### Post by cariboo on 2011-01-24
Thanks, Jorge, I'm looking forward to he update.

---

### Post by mc4man on 2011-01-24
can say the new 0ubuntu2 unity works well and the 'box' issue is gone.

---

### Post by kyleabaker on 2011-01-24
Yea, this bug has been driving my crazy, haha. I have dual screens so I've been working out of the second monitor only for days now. :/

I was about to try a fresh install until I saw this thread. Looking forward to the update!

---

