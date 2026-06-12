---
title: "Dual-monitor: Mouse position jumps when moving off-screen"
date: 2010-11-04
forum: Multimedia Software
---

### Post by 1awesomeguy on 2010-11-04
I have a dual-screen set-up with Ubuntu 10.10. I have an ATI Mobility Radeon HD 5650 video card. I use my lower-resolution laptop screen on the left and a larger monitor on the right. The monitor is also physically higher than the monitor. See attachment for a screenshot.

I have correctly set up my displays so that if the mouse is in the middle of the screen it can move from one screen to the other without jumping. The jumping happens when moving off of one screen in an area where the other screen is not directly next to it (some people call this 'the void').

Example: (See the attachment for a visual example of this.) My mouse is in the external monitor (right monitor). As I move the mouse to the top-left of the monitor (position 1), I by mistake go a little too far and instead of hitting the Ubuntu applications menu, I ended up at the top-right of the laptop monitor (left monitor; position 2). I quickly realize my mistake and move the mouse back to the right monitor, but now the mouse is at the middle-left position (position 3).

This same error occurs by moving the mouse on the laptop monitor (left monitor) passed the bottom-right position. This is a big problem when scrolling vertical scroll bars on the laptop monitor (left monitor).

I am looking for a fix that if the mouse is at position 1 in the attachment and I move the mouse left, it stays at position 1 and does not go to position 2.

Any help would be very helpful! Thank you!!

---

### Post by P4man on 2010-11-04
I dont think you have control over that behavior as it seems to be the drivers. Reason for thinking that is that the behavior is different with an nvidia card where the pointer goes in to the "void". To be honest, that is more annoying IMHO, certainly if you have dissimilar size monitors; if you have panels on the monitor with the least height, because you keep overshooting the edge of the screen To go from 1 to 2 on your examples also means you have to cross the void with nvidia drivers, moving the cursor without seeing it.

If I were you, I would just align the 2 monitors and cope with the "jump" going from one monitor to another. I suspect you adjust to that fairly quickly. Alternatively, unmaximize the panels so the top one doesnt stretch across the entire width or install an alternative panel like docky.

---

### Post by 1awesomeguy on 2010-11-04
> **P4man said:**
> I dont think you have control over that behavior as it seems to be the drivers. Reason for thinking that is that the behavior is different with an nvidia card where the pointer goes in to the "void". To be honest, that is more annoying IMHO, certainly if you have dissimilar size monitors; if you have panels on the monitor with the least height, because you keep overshooting the edge of the screen To go from 1 to 2 on your examples also means you have to cross the void with nvidia drivers, moving the cursor without seeing it.

If I were you, I would just align the 2 monitors and cope with the "jump" going from one monitor to another. I suspect you adjust to that fairly quickly. Alternatively, unmaximize the panels so the top one doesnt stretch across the entire width or install an alternative panel like docky.

P4man, thanks for the detailed response! The reason I posted the question is that this behavior is different in Win 7, where the same dual-screen set-up does exactly what I want it to (i.e., no mouse jumping through the void).

I agree that having the mouse move into the void would be more annoying. But neither problem is really optimal. I wish video card manufacturers thought of us Linux users more often...

The problem is that even if I set both monitors at similar heights their varying resolutions will still cause this error to occur (though it would only occur in one of the two positions). I did not think of making the top panel non-expanding. If I cannot find a way to make the mouse stop jumping, I will raise the left monitor so that the bottom of both monitors match (both psychically and in the settings) and will make the top panel non-expanding.

I would still love to find a solution to the mouse-jumping problem if anybody knows of a way to do that. Thank you!

---

