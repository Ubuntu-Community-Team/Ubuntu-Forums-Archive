---
title: "3 Questions"
date: 2008-06-04
forum: Mythbuntu
---

### Post by bergqvistjl on 2008-06-04
Hi, ive just installed mythbuntu and i have 3 questions
I have a sapphire x1650 pro (proprietry drivers) and two monitors: 1440x900 lcd (primary monitor) and 800x600 crt TV. 

1. How can i get mythtv (gui and all) to display on the TV in 800x600, while having my normal desktop on my LCD monitor in a resolution of 1440x900? the 1st time i ran mythtv, there was a screen within the frontend setup options to choose your monitor and its resolution, but it had absolutly no effect, also the menu has now disappeared (it goes onto the next screen) btw that menu was in the Appearance setup options. 

2. Also, when i play dvds using the internal player, the quality (including the pop-up mythtv menus) is bad (slightly distorted and flickery to be exact) (tho it seems ok if i play a dvd that is not copy protected (i have libdvdcss2). However it doesnt do this when i play it through mplayer or xine. is there some options i can put in the dvd player textbox in the options so that it will increase the quality?

3. Also is the tv standard in the UK PAL or PAL-I? in the backend setup i can set it to either of these, but in the part where you configure your tv-out (install) i can only set it to PAL-I. Catalyst Control Centre also tells me it should be PAL-I

---

### Post by Titus A Duxass on 2008-06-04
To use xine instead of internal you need to tell myth to use xine. 
Somewhere in the set up menus under set up video or DVD eplace the command Internal with xine -pfhq --no-splash -r 4:3 dvd/:
Edit: you can find all you need in the Mythtv Wiki.
[http://www.mythtv.org/wiki/index.php/Configuring_Xine](http://www.mythtv.org/wiki/index.php/Configuring_Xine)

---

### Post by bergqvistjl on 2008-06-04
yeah but i dont want to use xine, thats the thing. I want to use the internal player, but at the moment the quality's bad. is there a way i can increase the quality of the internal player?

---

### Post by Titus A Duxass on 2008-06-04
Sorry, I misread your question.

I have used both and find that the quality with xine is better, but the control that the internal player gives you is easier.

---

### Post by bergqvistjl on 2008-06-04
yeh, so are u saying that the quality is not good on your pc with the internal player too? and do you have any answers to my other 2 questions

---

### Post by Titus A Duxass on 2008-06-04
Sorry, I can't really help you with the other questions.

I only ever use pure TV or pure Monitor.

Over here in Germany I set my system to PAL even though it's PAL-B (I think).

When I say bad quality I am being a bit over critical, xine gives better quality.

With the internal player I get random lines of distortion that climb up the screen and sometimes the internal player appears to crop the ends of chapters.

---

### Post by bergqvistjl on 2008-06-05
ive solved the DVD issue, but not the monitor issue. With the internal player, i just have to swictch it to Progressive Scan mode and it works fine. Anybody got any ideas on the monitor problem?

---

